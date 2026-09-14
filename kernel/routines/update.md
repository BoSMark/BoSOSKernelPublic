# Update: keep the kernel current

## Purpose
Before anything else in a session, make sure this OS is running the latest kernel. You check the published kernel repo for a newer version and, if there is one, bring the new and changed routines into `kernel/` and remove retired ones. You only ever write inside `kernel/`. You never touch `OS.md`, its shims, `context/`, `missions/`, `routines/`, `memory/`, or `state.md`.

Do this quietly. If the OS is already current, say nothing and carry on. If you can't reach the network, skip the check and carry on; the OS works offline.

**Split the check from the apply.** Checking whether a newer version exists is a harmless read; applying it writes to `kernel/`. If you can't write `kernel/` (the operator keeps the files, see `OS.md`, *Which host, which mode*), do **not** attempt the apply: check if you can reach the network, and if a newer version exists say so once and point to the manual refresh in `docs/HOSTS.md`. Never fail a write you can't do.

**Frame the check on a brand-new OS.** The first time someone meets the OS, an unexplained call out to GitHub is a surprise. So if this is a brand-new instance (no `context/company.md` yet), say one plain line *before* the check, e.g. *"First I'll check for any kernel updates from `<UPDATE-SOURCE>`. This only reads from that one repo and only ever changes files inside `kernel/`, never your own content."* On later sessions, stay silent unless there's actually an update to report.

## Inputs
- `kernel/KERNEL-VERSION`: the version this instance is on.
- `kernel/UPDATE-SOURCE`: one line, `owner/repo@branch` (the published kernel repo, with `kernel/` at its root).
- `kernel/OS-MODEL-VERSION`: the version of the company model (`OS.md`'s *How the company is modelled*) this kernel expects. Operator-owned `OS.md` carries a matching `OS-model version:` marker. Bumped only when the model itself changes, not on every kernel release.
- `kernel/OS-LAYOUT-VERSION`: the cumulative operator-owned file layout and runtime contract this kernel expects. Operator-owned `OS.md` carries a matching `OS-layout version:` marker. It is independent of release labels and model version.

The update must survive interruption (a power cut or an internet outage mid-way). It does so by three rules: **stage everything before touching the live `kernel/`; apply only if the whole download succeeded; write `KERNEL-VERSION` last.** Because the version is written last and every write is an overwrite, an interrupted update simply leaves you on the old version, and the next load re-runs and completes it. Your `kernel/` is never left half-changed and unaware of it.

## Operating loop
1. **Recover.** If a staging folder `.bos-update-staging/` exists from a previous interrupted run, delete it; you'll re-stage cleanly.
2. Read the local `kernel/KERNEL-VERSION` and parse `kernel/UPDATE-SOURCE` into `owner`, `repo`, `branch`.
3. Fetch the remote version from
   `https://raw.githubusercontent.com/<owner>/<repo>/<branch>/kernel/KERNEL-VERSION`.
   If the fetch fails, **tell the two failures apart before you go quiet**, because they mean different things:
   - **Unreachable** (no network, timeout, DNS): you're offline. Skip silently and carry on; it retries next session. This is the normal quiet case.
   - **Resolved but refused** (404 / not found / private repo / bad path): the source itself is wrong or you can't reach it, and waiting won't fix that. Don't swallow it every session. Note it so the Assistant can say plainly if asked: *"the update source `<UPDATE-SOURCE>` didn't resolve, the repo may be private or the path may be wrong."* On a brand-new instance (the framed first-run check above), surface it once rather than silently.
   Never report success, or imply the OS is current, when the source didn't actually resolve. Either way, hand to the BoS OS Assistant.
4. Compare as dotted integers (`major.minor.patch`). If remote **≤** local, you're current: continue silently.
5. If remote **>** local, upgrade:
   a. Fetch the file list:
      `https://api.github.com/repos/<owner>/<repo>/git/trees/<branch>?recursive=1`.
      Keep every `blob` whose `path` starts with `kernel/`. This is the authoritative kernel file set for the new version.
   b. **Stage.** Fetch each listed file's raw content into `.bos-update-staging/<path>`, creating folders as needed. Also fetch `kernel/CHANGELOG.md` and read the new version's entry and any **migration note**. **If any fetch fails** (e.g. the connection drops), delete `.bos-update-staging/` and **abort**: the live `kernel/` is untouched and you're still on the old version. It will retry next load.
   c. **Verify staging is complete:** the staged `kernel/KERNEL-VERSION` equals the remote version and every listed file is present. If not, delete staging and abort.
   d. **Apply** (local only, no network): copy every staged file **except `KERNEL-VERSION`** over `kernel/`; delete any local file under `kernel/` not in the staged set (retired routines); **then write the staged `KERNEL-VERSION`, last.** Writing the version is the commit point.
   e. Delete `.bos-update-staging/`. Write or delete **nothing** outside `kernel/` and the staging folder.
6. **Tell the user what happened.** If you updated, say the version change, then a short plain-English summary of what is new (take it from the new version's entry in `kernel/CHANGELOG.md`, not from file names), and then list the new / changed / removed routines by name. Close with: *"Ask me about any of these and I'll explain."* If a migration note needs an operator action, surface it here and pause. Then hand to the BoS OS Assistant; it can answer follow-ups by reading the kernel. If nothing changed, say nothing.
7. **Check `OS.md` still matches this kernel's model (read-only; you never write `OS.md`).** This runs every session, not only after an upgrade, because a model migration can be left undone across many sessions. Read `kernel/OS-MODEL-VERSION` (the version the kernel expects) and the `OS-model version:` marker in `OS.md`:
   - **Marker equals the kernel value:** compatible. Say nothing.
   - **Marker missing, or lower than the kernel value:** the operator's `OS.md` predates one or more model changes this kernel depends on, so the model the operator reads and the routines the OS runs can disagree. **Do not assume a single latest change: the operator may have skipped several releases.** Read `kernel/OS-MODEL-MIGRATIONS.md` and collect **every** entry whose version is greater than the operator's marker (treat a missing marker as older than all of them) and no greater than the kernel's expected value. Surface it **once, plainly**, and pause: name the mismatch (`"your OS.md describes the model at version <marker or 'unversioned'>, this kernel is on <kernel value>"`), then present **all** the collected migrations **in order, oldest first**, each as the exact change to make to `OS.md` in plain terms. Say the **Assistant** can make the edits **with their go-ahead** and, **only after all of them are made**, bump the marker straight to the kernel value (this update routine itself writes nothing outside `kernel/`; changing `OS.md` is normal operator-approved work handed to the Assistant, never something the upgrade does silently). **Never bump the marker after applying only some of the migrations**, and never skip an intermediate one just because a later one supersedes it in wording, unless the ledger says so. Do **not** rewrite `OS.md` from here, and do **not** repeat the notice once the marker matches. If `OS.md` has no marker at all, treat it as older than every entry and offer to add the marker (set to the kernel value) as part of the same approved edit, once all changes are made.
   - **In a workspace (several Folders visible, each its own BoS OS):** each Folder has its own `OS.md` marker and its own kernel `OS-MODEL-VERSION`. **Before doing any cross-Folder work, compare them. If they differ across the Folders you can see, surface the incompatibility first and route the operator to reconcile it**, rather than silently reasoning across two Folders on materially different models. You need not update every Folder automatically; make the mismatch visible (`"[execs] is on OS-model 0.22 but [company] is on 0.21, so I'd be mixing two models, let's line them up before I work across them"`) and let the operator fix each in its own session.
8. **Check the operator-owned layout contract too (read-only here; the Assistant applies it only with approval).** This also runs every session. Read `kernel/OS-LAYOUT-VERSION` and the `OS-layout version:` marker in `OS.md`:
   - **Marker equals the kernel value:** compatible. Say nothing.
   - **Marker missing, or lower than the kernel value:** read `kernel/OS-LAYOUT-MIGRATIONS.md` and collect **every** entry after the Folder's marker and no greater than the kernel value, oldest first. Treat a missing marker as older than every entry. Tell the operator the Folder's layout is behind, present the complete cumulative change set, and pause. The **Assistant** may apply those operator-owned changes only with the operator's explicit go-ahead. Preserve operator content, apply every entry in order, verify every required path, link, ignore rule and contract change, then bump the marker straight to the kernel value. Never advance it after a partial migration, and never make these changes silently as part of the kernel update.
   - **In a workspace:** before cross-Folder work, compare both the model and layout markers across every visible Folder. If either differs, name the mismatches and reconcile each Folder before combining their content.

## Stop / ask
- If the new version's changelog carries a **migration note that needs an operator action** (for example, "add a new file under `context/`"), apply the kernel update as above, then **surface the note to the human and pause**. Do not perform the operator action yourself.
- If either compatibility ledger requires operator-owned changes, present all pending entries and wait for one explicit go-ahead. The Assistant performs and verifies them; this routine never silently writes them.
- Never write or delete outside `kernel/`. If an update seems to require changing operator content, that is a migration note for the human, not something you do.
- Only ever upgrade. If the remote version is lower than local, do nothing.

## Outputs
- An up-to-date `kernel/` (new routines added, changed ones overwritten, retired ones removed, `KERNEL-VERSION` bumped), or no change at all.
- When something changed: a plain summary of what is new, drawn from the changelog, with an invitation to ask the Assistant about it. Silence when already current or offline.
- A visible, supervised path for any pending model or layout migration, with neither marker advanced until its full ledger has been applied and verified.

# Update: keep the kernel current

## Purpose
Before anything else in a session, make sure this OS is running the latest kernel. You check the canonical GitHub repo for a newer version and, if there is one, bring the new and changed routines into `kernel/` and remove retired ones. You only ever write inside `kernel/`. You never touch `OS.md`, its shims, `context/`, `missions/`, `routines/`, `memory/`, or `state.md`.

Do this quietly. If the OS is already current, say nothing and carry on. If you can't reach the network, skip the check and carry on; the OS works offline.

**Split the check from the apply.** Checking whether a newer version exists is a harmless read; applying it writes to `kernel/`. If you can't write `kernel/` (the operator keeps the files, see `OS.md`, *Which host, which mode*), do **not** attempt the apply: check if you can reach the network, and if a newer version exists say so once and point to the manual refresh in `HOSTS.md`. Never fail a write you can't do.

**Frame the check on a brand-new OS.** The first time someone meets the OS, an unexplained call out to GitHub is a surprise. So if this is a brand-new instance (no `context/company.md` yet), say one plain line *before* the check, e.g. *"First I'll check for any kernel updates from `<UPDATE-SOURCE>`. This only reads from that one repo and only ever changes files inside `kernel/`, never your own content."* On later sessions, stay silent unless there's actually an update to report.

## Inputs
- `kernel/KERNEL-VERSION`: the version this instance is on.
- `kernel/UPDATE-SOURCE`: one line, `owner/repo@branch` (the published kernel repo, with `kernel/` at its root).

The update must survive interruption (a power cut or an internet outage mid-way). It does so by three rules: **stage everything before touching the live `kernel/`; apply only if the whole download succeeded; write `KERNEL-VERSION` last.** Because the version is written last and every write is an overwrite, an interrupted update simply leaves you on the old version, and the next load re-runs and completes it. Your `kernel/` is never left half-changed and unaware of it.

## Operating loop
1. **Recover.** If a staging folder `.bos-update-staging/` exists from a previous interrupted run, delete it; you'll re-stage cleanly.
2. Read the local `kernel/KERNEL-VERSION` and parse `kernel/UPDATE-SOURCE` into `owner`, `repo`, `branch`.
3. Fetch the remote version from
   `https://raw.githubusercontent.com/<owner>/<repo>/<branch>/kernel/KERNEL-VERSION`.
   If the fetch fails for any reason, **stop silently** and hand to the BoS OS Assistant.
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

## Stop / ask
- If the new version's changelog carries a **migration note that needs an operator action** (for example, "add a new file under `context/`"), apply the kernel update as above, then **surface the note to the human and pause**. Do not perform the operator action yourself.
- Never write or delete outside `kernel/`. If an update seems to require changing operator content, that is a migration note for the human, not something you do.
- Only ever upgrade. If the remote version is lower than local, do nothing.

## Outputs
- An up-to-date `kernel/` (new routines added, changed ones overwritten, retired ones removed, `KERNEL-VERSION` bumped), or no change at all.
- When something changed: a plain summary of what is new, drawn from the changelog, with an invitation to ask the Assistant about it. Silence when already current or offline.

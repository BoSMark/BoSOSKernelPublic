# Install a mission (add a new agent to this OS)

## Purpose

Add a mission the operator does not yet have into this existing BoS OS Folder, from the connector's
catalogue. This is how a second (or later) agent arrives after the first one shipped seeded in the
download. Delivery is the connector's job; writing the files locally is yours.

## When this runs

Load this routine when the operator asks to install, add or "get" a named agent or mission — for
example after seeing an install instruction on the BoS site ("install annual-planning"), or asking
"add the annual planning agent". The name they use is the mission **slug**.

Do not load this to re-open a mission this Folder already has — that is `mission-runner.md`. Installing
is only for a mission not yet present.

## Steps

1. **Connector must be live.** Call `whoami`. If it does not answer, the connector is not added: say so
   in one line and how to add it once (`connector_url` in `.bos/manifest.yaml`; paste the token the
   operator was given, raw). Installing a new mission needs the connector — unlike the seeded first
   mission, its files are not already on disk. Stop here until it answers.
2. **Confirm the slug is available.** Call `list_missions`. If the requested slug is not listed, say
   what is available and stop; do not guess a near-match. If the slug is already `installed`, `active`
   or further along in the ledger, say it is already here and offer to run it (`mission-runner.md`)
   instead of reinstalling over the operator's progress.
3. **Kernel gate.** `get_mission` returns the mission's `min_kernel_version`. If this Folder's
   `kernel/KERNEL-VERSION` is below it, do not write mission files yet — run the kernel update first
   (`update.md`), then continue. A mission must never land against a kernel that cannot run it.
4. **Fetch the package.** Call `get_mission(slug)`. It returns `{slug, version, min_kernel_version, files,
   manifest}` where `files` holds `mission.md` and `guide.md` and `manifest` holds each file's sha256.
   Verify each written file's hash against `manifest`. The `mission.md` you write carries a
   `mission_version` in its header; that becomes this Folder's version marker for the mission, and
   `update-mission.md` uses it later to detect a newer published version. This tool never touches your
   filesystem.
5. **Write the files.** Create `missions/<slug>/` if absent and write each returned file into it
   (`missions/<slug>/mission.md`, `missions/<slug>/guide.md`). If the folder already exists with
   operator edits or progress, do not overwrite silently — this is operator-owned work; name the
   conflict and ask before replacing. Add a `missions/<slug>/work.md` with an empty `Next / In progress
   / Blocked / Done` backlog only if one is not already there.
6. **Record it, by name.** Add the mission to `missions/INDEX.md` using its **title** (from
   `list_missions`, or the mission's own H1, e.g. "Annual Planning"), not the slug, as `status: installed`
   (not active — activation is a separate, explicit act). The slug is only the folder ID and the
   connector key; the title is the canonical name and is how the mission is named to the operator
   everywhere. Call `set_mission_status(slug, "installed")` so the connector ledger matches.
   Best-effort: `register_instance` with this Folder's path if not already recorded.
7. **Offer to run.** Tell the operator the agent is installed, by its title, in one plain line and offer to run it now.
   On yes, activate it (`set_mission_status(slug, "active")`, update INDEX to `active`) and enter
   `mission-runner.md`. Do not auto-run without the offer.

## Guardrails

- Installing writes only inside `missions/<slug>/` and one line in `missions/INDEX.md`. Touch nothing
  else in `context/`, other missions, or the kernel.
- Entitlement is settled on the BoS site before the operator is given the install instruction; the
  connector serves what the operator is cleared for. You do not police purchase here — but you also
  never invent a slug that `list_missions` did not return.
- One install at a time. If the operator names several, install the first, confirm, then the next.

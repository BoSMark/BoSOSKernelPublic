# Update installed missions (keep downloaded agents current)

## Purpose
Keep the instruction files of every mission already installed in this Folder current with the
connector's catalogue. A mission's `mission.md` and `guide.md` are BoS-owned instructions (like the
kernel); the operator's own `work.md`, `outputs/` and any edits are theirs. When BoS refines a mission
and publishes a newer version, this routine brings the new instructions down and overwrites **only**
`mission.md` and `guide.md`, never the operator's work.

Do this quietly. If every installed mission is already current, say nothing and carry on. If the
connector is not live or the network is down, skip and carry on; installed missions still run offline
on the instructions already on disk.

This is the mission-level twin of `update.md` (which keeps `kernel/` current). Same discipline:
compare versions, only ever upgrade, verify before applying, touch only BoS-owned files.

## When this runs
- At **clean session start**, right after the kernel update check, once the connector is confirmed
  live and `list_missions` has been called. Never mid-turn, never mid-mission-step.
- On demand if the operator asks to update or refresh an installed agent.

## Inputs
- The local `missions/<slug>/mission.md` for each installed mission. Its catalogue header carries
  `mission_version=<x.y.z>`; that is the version this Folder is on for that mission. A mission.md with
  no `mission_version` predates versioning: treat it as older than any advertised version.
- `list_missions` from the connector, which advertises each mission's latest `version`.
- `get_mission(slug)`, which returns `{slug, version, min_kernel_version, files, manifest}` where
  `files` holds `mission.md` and `guide.md` and `manifest` holds each file's sha256.

## Operating loop
For each mission folder present under `missions/`:
1. **Read the local version.** Parse `mission_version` from the local `missions/<slug>/mission.md`
   header. If absent, treat as `0.0.0`.
2. **Compare.** Find this slug in the `list_missions` result and read its advertised `version`. Compare
   as dotted integers (`major.minor.patch`). If advertised **≤** local, this mission is current:
   continue silently to the next.
3. **Kernel gate.** If the advertised mission needs a newer kernel than this Folder runs
   (`get_mission`'s `min_kernel_version` above `kernel/KERNEL-VERSION`), do not update it yet: run
   `update.md` first, then retry. A mission must never land against a kernel that cannot run it.
4. **Fetch.** Call `get_mission(slug)`. Keep the returned `files` and `manifest` in memory; do not write
   yet.
5. **Verify.** For each returned file, compute its sha256 and check it equals the value in `manifest`.
   If any file is missing or mismatches, **abort this mission**: leave the local files untouched (still
   on the old version) and note it so the Assistant can mention it if asked. Move to the next mission.
6. **Apply (local only, no further network).** Overwrite `missions/<slug>/mission.md` and
   `missions/<slug>/guide.md` with the verified content. Write **nothing else**: do not touch
   `missions/<slug>/work.md`, `missions/<slug>/outputs/`, `context/`, other missions or the kernel.
   Record `set_mission_status(slug, <its current status>)` is **not** needed; status is unchanged, only
   the instructions moved forward.
7. **Never disturb progress.** Updating the instructions does not re-open or re-run the mission. If the
   operator has progress in `work.md`, it stands; the newer guide informs the remaining steps only.
   Never re-run a step already recorded done.

## Tell the operator (notify, then it is done)
After applying, tell the operator in one plain line per updated mission: the mission title, the version
change, and a short plain-English note of what is new (take it from the mission's own guide/mission
text, not from file names). For example: *"Updated Content Ingest to v1.1: the card schema now asks
for a counterexample."* Close with *"Ask me about it and I'll explain."* If nothing updated, say
nothing. This matches the kernel update's report style; the change is applied, the operator is told,
no permission gate.

## Guardrails
- **Only ever upgrade.** If the advertised version is not strictly greater than the local one, do
  nothing for that mission.
- **BoS-owned files only.** Write only `missions/<slug>/mission.md` and `missions/<slug>/guide.md`.
  The operator's `work.md`, `outputs/` and any edits are never overwritten.
- **Verify before apply.** Every file's sha256 must match the manifest, or the mission is left on its
  old version. Never apply a partial or unverified fetch.
- **Quiet on offline / not-current.** No connector or no network means skip silently; already-current
  means silent. Only speak when something actually changed.
- One mission at a time; a failure on one never blocks the others.

## Outputs
- Each installed mission's `mission.md` / `guide.md` current with the catalogue, or unchanged.
- A one-line notice per mission that was updated, drawn from the mission's own text; silence otherwise.

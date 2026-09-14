# Operator-owned layout migrations

The kernel updates itself. It never silently rewrites the operator-owned files around it. This ledger is the cumulative path for bringing an older Folder's file layout and runtime contract forward when `OS.md` has a missing or lower `OS-layout version:` marker.

Apply every entry after the Folder's marker, oldest first. Present the complete set before asking for approval. Verify every item before advancing the marker. Model wording remains governed separately by `OS-MODEL-MIGRATIONS.md`.

## 1

For an unversioned or pre-layout Folder, bring all operator-owned pieces forward in one supervised migration:

1. Add `archive/README.md` and `archive/state-archive.md` from the current distribution if they are absent. Preserve any existing archive content.
2. Ensure `systems/INDEX.md` and one stub for each of the eleven named Systems exist: Steer; Create Demand, Capture Demand, Win, Offer, Deliver, Keep; Fund, Staff, Run, Protect. Add only missing stubs; never replace a System record that already holds operator content.
3. Ensure the current operator-owned roots exist where applicable: `roles/`, `routines/`, `context/`, `decisions/`, `memory/`, `missions/`, and `local_context/`. Preserve all existing content.
4. Use the current documentation layout: `START-HERE.md` at the root and reference material under `docs/`. If an older root `README.md` or root reference documents contain operator additions, merge those additions before removing or moving anything. Update links to the `docs/` paths.
5. Keep existing mission folder names and IDs. New missions use the current per-Folder `<FF><NN>_name` form; never rename history merely to match the new convention.
6. Bring the operator-owned `OS.md` runtime contract forward: current startup and routine-index paths, `archive/` and `local_context/` ownership, the one-question rule, plain voice, current mission-ID example, current host-document paths, and the two capability-growth channels. Apply company-model wording through `OS-MODEL-MIGRATIONS.md`, not by guessing from this layout ledger.
7. Update `.gitignore` so `local_context/*` is ignored while `local_context/README.md` is explicitly included. Add the current README warning that this is working-copy-only, not a privacy wall, and that payload files have no Git history or OS undo. Never stage an existing payload.
8. Bring `state.md` placeholders and links forward to the current archive, mission-ID, handoff, and blocked-item conventions without overwriting live state.
9. Verify the required paths, links, ignore behaviour, and OS contract. Only then set `OS-layout version: 1` in `OS.md`.

This entry is cumulative. A Folder jumping directly from v0.17 or another unversioned layout does not need to reproduce intermediate release labels.

## 2

Keep growing company records searchable without making them part of every session:

1. Add `decisions/INDEX.md` from the current distribution if absent. Preserve every existing Decision and `decisions/log.md`. The index is a bounded locator, not a replacement for those records.
2. Add `memory/README.md` and `memory/INDEX.md` from the current distribution if absent. Preserve `memory/learnings.md` and any other Memory content. Point the starter index at the existing learning file.
3. Bring `decisions/README.md`, `context/README.md` and `archive/README.md` forward with the bounded-record instructions while preserving any operator additions.
4. Treat 12 KB as the internal backstop for a normally loaded index or baseline summary. Do not split a small existing file merely to finish migration. When the next approved write would cross the backstop, split prospectively using the current README and `kernel/routines/record-retrieval.md`.
5. Keep `archive/state-archive.md` as the bounded intake and route. If it is already above the backstop, preserve every dated item and partition it by year; otherwise leave its existing entries in place until the growth trigger fires.
6. Bring the operator-owned `OS.md` minimum-context contract forward: a specific request starts with its owning source and may return `Not recorded` without a broad scan; bounded indexes locate detailed Decisions, learning and cold history. Preserve company-specific wording elsewhere.
7. Verify the new indexes point to existing records, no operator content was removed, and the Assistant can reach `session-orientation.md` and `record-retrieval.md` from its kernel index. Only then set `OS-layout version: 2` in `OS.md`.

This migration adds filing routes, not a new business object. It requires no database, embeddings, GitHub workflow or bulk history rewrite.

# BoS check (internal, read-only)

## Purpose

Give the operator a plain-language consistency check over the BoS record without changing anything. Run only when asked. This checks declared structure, ownership, references and derived views; it does **not** claim that business facts, strategies or AI outputs are correct.

## Inputs

Read only what each check requires:

- active `missions/*/mission.md` and their `work.md`;
- standing `roles/*.md`;
- materialised System records and `systems/INDEX.md`;
- `state.md`;
- relevant Context source registers;
- `OS.md` model/layout markers and the kernel version markers;
- the `Collaboration:` line in `context/operator-rules.md`, and relevant linked repository evidence only when that Folder is GitHub-managed;
- version history only where the host supports it.

Do not load whole archives, all Decisions, all Memory, or unrelated Context merely to run the check.

## Invariants

Report each by this number and exact plain-language rule:

1. Every active Mission has a progress statement, outcome, named human owner, primary System and functional Roles.
2. Every named owner and approver resolves to `context/people.md`, or is flagged as not yet recorded there.
3. Every standing Role has an outcome, named human owner, Systems served, performance path, Authority and existing Onboarding sources.
4. Each System's Mission and Role lists match the Mission and Role records that own those relationships.
5. State matches active Missions, open handoffs, blocks and findings in Mission worklists.
6. Every new finding carries a supported status plus its source or evidence and date. Legacy `[unverified]` is reported as readable old format, not treated as corruption.
7. Every inline source marker in a record resolves to an entry in that record's Sources register, and every entry is used. A fact known to be superseded is not still presented as current; an unresolved disagreement remains visibly attributed rather than silently collapsed.
8. Every lasting shared change has attribution and version history where the host supports history; `local_context/` is excluded by design. A recorded collaboration mode is one of the three supported values and stable work references are unique within each Mission; in a GitHub-managed Folder, linked status evidence that the operator asks this check to inspect is checked live when accessible and reported `not checkable here` otherwise.
9. OS model, layout and kernel markers are compatible with the current kernel.
10. The Assistant is reading the intended BoS instance; another visible nearby instance is reported before records are combined.

## Method

1. Establish the intended Folder or workspace and its host mode.
2. Run deterministic checks first: required headings, named references, file existence, links, markers and Git history where available.
3. Use judgment only for wording that cannot be checked mechanically, such as whether an outcome is stated as a result. Label these `needs review`, never `failed` merely because phrasing differs.
4. Do not traverse cold `archive/` or unrelated Folder content.
5. Make no edits, commits, promotions or automatic repairs. A repair is a separate proposal after the operator reviews the result.

## Output

```text
BoS check: <n> passed; <n> need attention; <n> need review.

Needs attention
<rule number>. <plain failure> · source: <path>

Needs review
<rule number>. <judgment the operator should inspect> · source: <path>

No repairs were made.
```

Omit empty detail sections, but always include `No repairs were made.` Do not produce a composite health score, percentage, grade or green/amber/red label. A passing check means the files satisfy these declared invariants, not that the business is healthy or the contents are factually correct.

## Stop / ask

- If more than one BoS instance is visible and the intended one is unclear, stop and ask which is live.
- If Folders carry different model or layout markers, report the mismatch and stop before cross-Folder checks.
- If a rule cannot be checked on this host, report `not checkable here`; do not count it as passed.

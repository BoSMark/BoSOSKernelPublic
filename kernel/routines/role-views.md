# Role views (internal, generated)

## Purpose

Answer two plain operator questions from the records already present:

1. **Mission Role Map:** who is responsible for what in this Mission, how is each Role performed, and where does its authority stop?
2. **Role Evolution View:** where could AI safely take on more of the work next?

These are generated views, not company records. Never save or maintain them as separate files. If a view conflicts with a source, the source wins and the view is regenerated.

## Shared rules

- Keep the accountable owner visible and human at every performance level. AI may perform a Role; it never becomes the accountable owner.
- A Mission owns which Roles participate and their Mission-specific outcomes. For a linked standing Role, read both records: owner and performance path should agree; Mission Authority may narrow the standing boundary but may not expand it without a human decision. Read only that linked Role, never all `roles/`, when mapping one Mission.
- Do not infer a missing outcome, owner, mode or authority from a Role name, worklist, tool access or likely practice. Show **Not recorded**.
- If the Mission and linked Role disagree, name both values and their source paths. Do not blend them or silently choose one.
- Cite the path or paths used for every row.
- In a workspace, label every row by Folder. Generate the view only for the current operator; never write private Role details into another Folder.
- Do not turn tasks, tools, prompts or AI personalities into Roles.
- Do not change a Mission, Role, performer, target or authority while producing either view. A later change follows the normal human decision and audit path.

## Mission Role Map

### Use when

- Shape has written a draft `mission.md` and is presenting the Mission for confirmation.
- The operator asks “who does what?”, “show the Mission Roles”, “who is responsible for each part?”, or equivalent for a named or current Mission.

Read the Mission's `mission.md`. For each `Durable:` link, whether a legacy inline marker or a block field, read that one Role record. Do not load `work.md` merely to fill missing Role fields.

Use this exact shape:

```text
Mission Role Map: <Mission name>

| Role | Outcome in this Mission | Human owner | Now | Target | Authority boundary | Source |
|---|---|---|---|---|---|---|
| <Role> | <bounded result> | <person> | <current performance> | <target performance> | May: <...>; needs approval to: <...> | <path(s)> |
```

Show one row per Mission Role, in Mission order. For a missing value write **Not recorded**. Keep Mission-specific limits if they are narrower than a standing Role's Authority; flag any apparent expansion for a human decision. The map replaces a prose Role recap at Shape, so it adds clarity rather than another approval step.

## Role Evolution View

### Use when

Only when the operator asks “where can AI help next?”, “show Role evolution”, “what should we automate?”, or equivalent. Do not add it to every session opening.

Use the named Mission, Role, or System scope. If one active Mission is already in focus, use it. If several scopes are plausible, ask one scope question. For an explicitly company-wide view, include standing Roles and active Mission-local Roles visible in the current Folders; exclude dormant and closed work unless asked. De-duplicate a Mission Role linked to a standing Role, while listing each visible active Mission in which it is currently in scope.

For a Mission-scoped view, read `mission.md`, each linked standing Role, and only the relevant items or findings in that Mission's `work.md` needed to support a next experiment. For a company-wide view, reading the visible Role records and active Mission Role sections is in scope; do not load unrelated Context, Decisions, Memory or archives.

Use this exact shape:

```text
Role evolution: <scope>

| Role | Scope | Human owner | Current mode | Target mode | Authority ceiling | Next safe experiment | Basis / source |
|---|---|---|---|---|---|---|---|
| <Role> | <Mission/System/company> | <person> | <mode> | <mode> | <recorded limit> | <one bounded proposal, or Needs evidence: ...> | <status, date and path> |
```

Apply these rules to each row:

- **One rung at a time.** Human-led may move to an AI-assisted experiment. AI-assisted may test bounded AI-run execution with human sign-off. Do not skip straight to a more autonomous mode.
- **Stay below the ceiling.** The experiment must fit the recorded `May` boundary. Sending, publishing, spending and irreversible action remain human-executed. If Authority is missing, show **Not recorded: no autonomy experiment proposed**.
- **Evidence before confidence.** Name the basis, its status, date and source. When the evidence is insufficient, show **Needs evidence: `<what would settle it>`**. A hypothesis may justify a test, but not a claim that the Role is ready.
- If owner, current mode or target mode is missing, show **Not recorded** and state the specific record decision needed before proposing an experiment.
- If current and target modes are the same, show **No change recorded** unless the operator explicitly asks to reconsider the target.

Do not score, grade, rank or label a Role “ready”. Preserve Mission order for a Mission view. For a company-wide view, group by System and say how many Roles are shown; if the result is long, show the first ten and offer the remainder without hiding the total.

## Stop / ask

- If the Mission or requested scope is unclear, ask one scope question.
- If two records disagree on owner or authority, surface the conflict and stop before proposing increased autonomy for that Role.
- If the operator wants to adopt an experiment or change a target, move back into the Mission work method and use the normal approval boundary. The view itself makes no change.

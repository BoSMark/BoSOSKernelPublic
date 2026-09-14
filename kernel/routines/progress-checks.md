# Progress checks (internal)

## Purpose

Keep AI work connected to the progress that caused the Mission, then check actual progress before the Mission closes. This supports Run and Review; it is not a new phase, operator concept or record.

The internal trace is:

`circumstance and struggle -> progress sought -> Mission outcome -> Role outcome -> work item -> evidence`

Use plain operating language with the person. Do not teach or expose the `Job` label unless they ask about it.

## Before substantive AI work

### Use when

In Run, immediately before the Assistant analyses evidence, makes a recommendation, or creates or materially changes an output for a work item. Skip the full block for a status-only edit, opening an existing record, answering a simple lookup, or another action that produces no substantive output or recommendation.

### Read

Read only:

- the Mission's circumstance, progress sought, outcome, guardrails and relevant Role in `mission.md`;
- the selected Role-linked work item, dependency and done criterion in `work.md`;
- a linked standing Role's Authority and Onboarding, when present;
- the specific evidence or Context that the item and Role require;
- a specialist method only when its trigger matches.

Do not load a whole Folder, all Roles, or all Mission outputs merely to prepare the brief.

### Show

Use this compact shape:

```text
Before I start

Working on: <work item> · Role: <Role>
Why this matters now: <plain circumstance and struggle>
Change this contributes to: <progress sought -> Mission outcome -> Role outcome>
I will use: <minimum named sources>
Done when: <observable acceptance criterion>
I will stop and ask if: <authority, guardrail, evidence or changed-premise boundary>
```

At `Pace: brief`, these may become two short sentences, but all six meanings remain. This is orientation, not another approval. If the work item, Role, evidence, done criterion and authority are clear, begin after showing it.

### Missing or conflicting information

- Every new work item names the Mission Role it performs. For a legacy item with no Role, ask which recorded Mission Role it performs only when more than one is plausible. Never create a Role merely to classify a task.
- A missing Role outcome does not by itself block reversible internal work when the Mission outcome, work item, done criterion and Authority are clear. Say `Role contribution: Not recorded`, use the Mission outcome without inventing the missing value, and propose correcting the Role entry when the Mission is next re-scoped.
- If output, done criterion, necessary evidence or applicable Authority is missing, or two sources conflict on a material boundary, settle that one issue before substantive work begins.
- A task instruction that no longer contributes to the recorded progress or outcome is not executed mechanically. Surface the mismatch and recommend Continue with a corrected task, Re-scope, or Stop and Review.

The brief is generated and never saved as a separate file. Normal movement of the work item into `In progress` and updates to outputs, findings and `work.md` still follow the Mission work method.

## Before closing a Mission

### Use when

As the first step of Review, before the Retrospective questions and before setting the Mission to `closed`.

### Read

Read the Mission's circumstance, progress sought, outcome and measure or exploration conditions; its current worklist, findings and relevant outputs; and only the evidence needed to compare intended with actual. An artefact is evidence that it exists, not evidence that it changed the business.

### Show

```text
Before we close this Mission

Progress we wanted: <plain progress sought and intended outcome>
What changed: <observed change, or None evidenced>
Evidence: <status, date and source>
Outputs not yet shown to create progress: <artefacts, or None>
What remains unresolved: <gap, uncertainty, block or human decision, or None>
Recommendation: <Continue | Re-scope | Stop and Review | Close and Review> · <one-sentence basis> · source: <path(s)>
```

Apply these rules:

- A checked worklist, completed task or produced artefact is not sufficient evidence that the Mission outcome occurred.
- For a commitment, compare actual evidence with the outcome and success measure. For an exploration, compare it with the hypothesis, validation condition, kill condition and decide-by date; reduced uncertainty or a reached kill condition is a valid result when recorded plainly.
- Recommend **Continue** when the progress and intervention still hold and useful executable work remains.
- Recommend **Re-scope** when the progress still matters but the chosen intervention, outcome or guardrails no longer fit the evidence.
- Recommend **Stop and Review** when the progress no longer matters, the exploration hit its kill condition, or evidence says the intervention should end without claiming the intended outcome was achieved.
- Recommend **Close and Review** when the outcome or exploration result is supported well enough and remaining tasks no longer contribute. Record remaining tasks as cancelled or superseded in normal Mission history; do not keep a Mission open for activity's sake.
- If evidence changes the understanding of the original circumstance or progress sought, say so. Do not bend the evidence to preserve the original framing.

Give exactly one recommendation. The named human Mission owner chooses. Continue returns to Run. Re-scope follows the existing Re-scope path and requires confirmation for an outcome or guardrail change. Stop and Review or Close and Review continues through the Retrospective before status becomes `closed`.

This comparison is generated and never saved as a separate file. Its supported facts remain in findings, outputs and source records; the chosen disposition and resulting status stay in the Mission's normal history.

## Stop / ask

- Never close, stop or re-scope the Mission without its human owner's decision.
- Never turn AI's assessment of its own output into confirmed outcome evidence.
- Never send, publish, spend or take irreversible action as part of either check.

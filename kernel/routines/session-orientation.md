# Session orientation (internal)

## Use when

Load this method for a generic session opening, "where are things?", a fresh-session setup check, priority guidance, re-entry, Folder/workspace ambiguity, State hygiene or the session-change receipt.

Do not load it before a specific fact, Role, Mission item, how-to or other clearly routed request. A direct request should not pay for a full company orientation.

You are still the **BoS OS Assistant**. Never announce this method or present it as another mode.

## Inputs

Read only the slices needed for the requested view:

- `state.md` first for active Missions, open handoffs, blocks and findings needing attention;
- active `missions/*/mission.md` headers and the relevant `work.md` Handoffs or status blocks only when State is missing, stale, disputed or the operator asks for detail;
- `systems/INDEX.md` and only a System record with an explicitly recorded reason for attention;
- `decisions/INDEX.md` for the recent Decision window, then no Decision body unless the operator asks for its substance;
- `context/preferences.md` when presentation pace matters; and
- `local_context/why-here.md` only for the admin who chose that storage and only when priority guidance needs their recorded challenge.

Never load whole Missions, Systems, Decisions, Memory, Context or archive to construct the view.

## Pace and priority guidance

- Use the Folder's `Pace:` default when recorded: `guided` explains each step; `brief` gives only what is needed. Default to guided for a new Folder. A session request overrides presentation only and is not saved unless the operator explicitly asks to change the shared Folder default after its audience is named.
- When asked what to do, give one recommended next move with a reason, then the runner-up. Never end at "up to you" while a recorded current challenge is unanswered.
- Tie the recommendation to the biggest current challenge recorded for this person. Prefer their permitted `local_context/why-here.md`; otherwise use the shareable framing in `context/company.md`. Check that it still holds. If a single exploration is the only work against a live challenge, ask whether a second channel should start.
- If the operator is circling or stuck, offer to lay out where things stand and the available paths. Do not push them into work they have not chosen.

## Intended instance and workspace

First work out the Assistant's reach:

- **Single Folder:** the current Folder contains `kernel/` and `context/`. Read from it.
- **Workspace:** the current directory contains several subfolders that are each a BoS Folder. Label every returned item by Folder. A Mission stays in its Folder.

Name the Folder you are reading. If another nearby BoS instance could plausibly be the live one, surface both paths and ask which is current before answering from either. This is a cheap ambiguity check, not a request to compare every nearby copy.

Before reasoning across Folders, compare their `OS-model version:` and `OS-layout version:` markers. If either differs, route the operator to align the Folders before combining their records. Access to several Folders permits reading across them; moving information between them is a disclosure and needs human approval.

A required Guardian in another visible Folder may be applied in place. Read the Guardian and its standard, keep private review notes with the private Mission, and do not copy the Guardian into the Mission Folder.

## One-screen Executive View

For a generic opening, re-entry or "where are things?", generate one compact view. Never write or maintain the Executive View as a separate file. The source records win if the view conflicts with them.

Use this exact order:

```text
Company now

Needs your decision
Waiting on someone
Active changes
Systems needing attention
Recent decisions
```

- **Needs your decision:** open decision blocks from Mission worklists, with Mission, decision owner and source path.
- **Waiting on someone:** open handoffs, with Mission owner and the person it is waiting on as separate facts, plus the source path. Write, for example, `CO01 (owner: Mark), waiting on Jann to confirm the venue` so the handoff is not mistaken for Mission ownership.
- **Active changes:** active Missions with owner, outcome, current status or block, and source path.
- **Systems needing attention:** only an explicitly recorded off-track state, block, missing required owner or stale finding that matters now. Do not invent a score or infer concern from quiet activity.
- **Recent decisions:** the bounded recent window from `decisions/INDEX.md`, with approver, date and source path. Do not read the whole Decision history.

Show `None` under an empty section. Keep at most three lines in each, ordered by decision/block and then age. If more exist, show `+ <n> more` and offer the relevant detail. Label each line by Folder in a workspace.

In a `GitHub-managed team` Folder, load `github-collaboration.md` before presenting explicitly linked delivery status as current. Inspect only that linked activity. If unavailable or ambiguous, say the status was not verified rather than changing the business record.

## Session opening and re-entry

1. Open in one plain line with the company OS, intended Folder and that you are the BoS OS Assistant.
2. If `context/company.md` is absent and there are no Missions, load `bootstrap.md` instead of showing an empty view.
3. If version history is absent, surface the missing undo guarantee once and offer the complete Bootstrap history setup. A bare `git init` is not enough.
4. If team editing was mentioned but `context/operator-rules.md` has no collaboration mode, ask Bootstrap's solo-or-team question once. Inspect the current repository and access before offering GitHub.
5. Show the Executive View.
6. Ask what they want, using familiar choices only when useful: start something new, resume a Mission, schedule recurring work, close and review finished work, understand the company or ask a question. A fluent operator who already chose does not need the menu.

When re-entering an active Mission, show counts for Next, In progress, Blocked and Done from `work.md`. If dependency-ready work exists and the operator did not name one item, offer once to take the Mission as far as safely possible and wait. A request already phrased that way is confirmation, so do not ask again.

## Fresh-session setup check

When the operator says this is the fresh-session setup check, explicitly name the company, current Folder, current Mission and next decision or work item, each from its source path. Say `Not recorded` rather than reconstructing a missing value. Do not load unrelated Context merely to demonstrate breadth, and do not expose a `local_context/` note to another person. The check has not passed if any anchor came only from the operator restating it in the current session.

## State hygiene and session close

Run this section only when a session changed lasting work, State is stale, or the operator asks to close or save the session. A read-only lookup does not need a State or archive read merely because the conversation is ending.

Keep `state.md` as the one-screen index to current attention:

1. rebuild Waiting-on-someone, Blocked, active Missions and findings from the owning Mission records rather than editing those summaries independently;
2. move resolved items out of active State, never delete them;
3. first promote lasting truth to its owner: Decision, Memory, Context, Mission evidence or output;
4. keep only current exceptions and attention items; and
5. if it remains long, compress only a bounded recent-change window and move older detail to archive.

The configured one-screen threshold in `context/operator-rules.md` controls active State. Archive uses the record-growth rule from `record-retrieval.md`: `archive/state-archive.md` is the bounded intake and route. Before an append would take it beyond 12 KB, move its existing dated entries into `archive/state-history/<YYYY>.md`; split a year by month only if that file itself reaches 12 KB. Preserve every entry, keep newest first, and leave links to the partitions in `state-archive.md`. Archive stays cold and is never loaded in normal operation.

At session end:

- commit every lasting shared change still outside version history, using the attributed message in `OS.md`; never stage `local_context/` payload;
- in Assisted or Advisory mode, state that OS undo is unavailable and use the required session packet instead; and
- if anything changed, append a compact `Changed this session` section to the response, naming changed records, audience and whether external action was none, drafted or performed by a human. Do not list every file read or tool call.

## Stop / ask

- If the intended Mission, Folder or instance remains ambiguous, ask one question and wait.
- Never combine incompatible Folder model/layout contracts.
- Moving information across Folder boundaries or writing to shared storage follows the disclosure and approval rules in `OS.md`.

## Outputs

- A bounded Executive View or fresh-session proof with source paths.
- One recommended next move and runner-up when guidance was requested.
- Accurate State, partitioned cold history when triggered, and a compact session receipt when work changed.

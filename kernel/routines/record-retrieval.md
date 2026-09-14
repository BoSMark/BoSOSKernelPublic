# Record retrieval and growth (internal)

## Use when

Load this method when the operator asks about company Context, a System, Role, Decision, learning or history and the Assistant's direct source map is not enough. Also use it when writing a material Decision or learning, correcting a current fact, repairing a repeated context miss, or splitting a growing record.

Do not load it for a direct fact whose owning source already answers the question, or merely to orient a session.

You are still the **BoS OS Assistant**. `Context`, `State`, `Decisions` and `Memory` remain familiar company records; the indexing and size rules below are internal filing behavior, not new operator concepts.

## Bounded working set

The company record may grow without limit. The working context for one piece of work must not grow with it.

Use three layers where a record family grows:

1. **Current route:** a small index or summary that points to current or recent records.
2. **Detailed record:** the authoritative Decision, learning, person, policy or historical item selected for this work.
3. **Partitioned history:** older route files and cold operational history, read only for an explicit historical need.

An index is a locator, not a second source of truth. It may carry an ID, title, scope, date, owner and path so the correct record can be chosen. The detailed record owns the substance. If locator metadata conflicts with the detailed source, use the source and repair the locator only when the current write scope permits it.

Every normally loaded route or baseline-summary file has a 12 KB internal size backstop. Meaning comes first: split when topics or audiences differ even if the file is smaller. Before the next append would cross the backstop, preserve existing content and split prospectively. Do not rewrite old records merely to make the directory look tidy.

Use a known path directly. To find a candidate, search only its owning directory with a narrow filename, stable ID, date or metadata pattern and cap the result set. Never inventory the whole workspace or a whole growing record family: discovery output also consumes context even when file bodies stay closed. Read only the route and selected record. Follow one explicit link at a time. For normal current work, stop when the source answers the question.

## Source-first lookup

1. Identify the source that conventionally owns the requested value or rule.
2. Read it before related evidence or neighbouring files.
3. Answer with its path and recorded status/freshness where material.
4. If it does not record the value, say `Not recorded` and stop.
5. Open one more business source only when the owner links to it, the question requires a distinct second source, a known conflict must be resolved, or the operator explicitly asks for an exhaustive search.

Do not widen a missing-fact search through sibling Missions, all Roles or general Context. Do not infer a recorded value from plausibility or model memory. For an ambiguous request, a bounded route may be the first read used to identify the owner.

## Context

The four Bootstrap files remain the named fallback for shaping early work, not an automatic bundle for every request:

- `context/company.md`: concise company identity, model, North Star, current priority and shareable challenge;
- `context/people.md`: cross-company identity, ownership and approval authority needed to route work;
- `context/values.md`: current working principles; and
- `context/operator-rules.md`: binding Folder-wide rules.

Each remains a concise current summary and route. When one approaches 12 KB:

- move extended person material to `context/people/<person>.md`, leaving cross-company ownership and authority in `people.md`;
- move a System-, Mission- or Role-specific rule to its owner and link it, leaving only global rules in `operator-rules.md`;
- move supporting explanation or evidence to a narrow Context record or Decision, leaving the current company/value statement and link in the baseline.

An additional Context file never joins the fallback set merely because it exists. When a cited record uses inline source markers, check that each marker resolves to its Sources register and each source is used; fix an obvious broken locator while already working there, or flag it.

When a named authority confirms a replacement fact and approves the update, change the owning file so only the replacement reads as current. Where history exists, the prior value stays recoverable. Where it does not, warn before saving that the old value will not be recoverable and include the old → new change in the session account. If sources or responsible people disagree, keep both claims with their status, source and date until the proper owner decides. A disagreement is not supersession.

For facts that can become wrong, use `Effective` or as-of date and an optional `Review when:` trigger. Check it when work is about to rely on the fact, not through blanket calendar review.

## Decisions

Prefer one file per material company-level Decision, using `kernel/templates/decision.md`, a stable `DEC-<YYYY-MM-DD>-<short-name>` ID and descriptive filename. Mission-internal choices remain in the Mission.

Normal retrieval order:

1. follow the direct Decision link from the governing System, Mission, Role, Routine or Context record when present;
2. for an unnamed recent Decision, read `decisions/INDEX.md` and then the selected Decision;
3. for older history, use a year or stable ID named in the request to locate that one time index directly; otherwise read `decisions/INDEX.md`, one linked time index under `decisions/history/`, and the selected Decision; and
4. follow `Supersedes:` only when the operator asks about the earlier reasoning or the current question requires the chain.

Keep at most 20 recent Decision locators in `decisions/INDEX.md`. When adding the twenty-first, move the oldest locator to `decisions/history/<YYYY>.md`. If a yearly locator file would exceed 12 KB, split that year's locators by month. The Decision bodies do not move merely because the index rolls.

When recording a Decision, add its locator to the recent index and link it from every current record it governs. A new Decision names what it supersedes; never edit the old Decision to make history disappear.

An existing `decisions/log.md` remains valid while below 12 KB. Before a new line would cross the backstop, preserve the log and create individual Decision files plus index locators prospectively. Do not bulk-convert the old log.

## Memory

Memory records what work taught, not a transcript of everything that happened. A person decides whether a proposed hypothesis becomes an adopted rule.

Normal retrieval order:

1. use the Mission's primary System and Roles to select a route from `memory/INDEX.md`;
2. read only that System/Role route, or `memory/learnings.md` while the Folder is still below the split threshold;
3. open only the learning selected for this Mission; and
4. read retired or older history only when the question asks for it.

For a lookup asking which learning is routed to a Mission, its `mission.md` owns the primary System and Roles and is sufficient to choose the Memory route. Do not open that Mission's `work.md`, Role Onboarding or operating evidence unless the operator also asks to apply or judge the learning against a current work item.

`memory/INDEX.md` contains links to System/Role learning routes and a short recent-hypothesis window; it does not accumulate every learning. A System/Role route contains locators to current adopted learning records and splits by topic if it reaches 12 KB. A substantive learning uses `kernel/templates/learnings.md` and records a stable `LRN-<YYYY-MM-DD>-<short-name>` ID, type, scope, evidence, date and owner.

The starter `memory/learnings.md` remains valid below 12 KB. Before a new entry would cross the backstop, preserve it, create the relevant route and individual learning records prospectively, and update `memory/INDEX.md`. Retired learning leaves the current route for `memory/history/<YYYY>.md` but retains its evidence and retirement reason.

Mission Shape reads only learning routed to its primary System or Roles. It never loads the complete company Memory merely because learning may exist.

## Systems and Roles

A person understands the company through `systems/INDEX.md`, then the one relevant System record and its current linked Missions, Routines and Roles. A Mission or Routine executes from its own record, then each required Role's Onboarding.

Relationships have one owner: a Mission owns the Systems and Roles it names; a Role owns the Systems it serves. A System's Mission and Roles-and-capabilities lists are derived views. When already crossing one of those links, repair an obvious mismatch from the owning record and flag only what cannot be resolved. Do not run a broad reconciliation pass as part of an ordinary lookup.

Roles and Systems are earned. When recurring work reveals a lasting responsibility outside a Mission, offer to draft one thin Role, never impose it. A Role is a coherent functional responsibility that can evolve from human-led through AI-assisted to AI-run with human sign-off, not a title, task, tool, prompt or AI personality. When a Role is promoted, add it to the derived map of every System it serves. Merge or retire only with a human decision; a quiet System remains recorded as `Dormant`.

## Repeated context misses

If the same fact, authority rule, method or interaction default has to be supplied again in separate work, propose the narrowest useful owner:

- company fact to its Context source;
- authority to `context/people.md` or the relevant Role;
- recurring process to a Routine;
- specialist method to the kernel route;
- shared presentation default to `context/preferences.md`; or
- Mission-only detail to that Mission.

Name the proposed source, audience and effect and wait for a human decision. Never save merely because something was repeated, and never expand the always-loaded company baseline.

## Archive and historical questions

Archive is cold. A current status, fact or recommendation never loads it. When an explicit historical question needs pruned State, start from the links in `archive/state-archive.md`, select one year or month partition, then read only the relevant dated slice. A Retrospective does the same for the Mission's window.

The session-orientation method controls State pruning and archive rollover. No record is deleted to reduce context.

## Write maintenance

When writing a material Decision or adopted learning:

- assign or preserve its stable ID;
- save the authoritative detailed record or valid small starter log entry;
- update the bounded locator route;
- link it from the current record it governs or affects;
- move a superseded or retired locator out of the current route without deleting history;
- roll the route before the next append crosses its backstop; and
- commit the lasting shared change with the attribution required by `OS.md`.

On Git, ordinary merge/conflict behavior protects shared files. In a non-Git shared folder, follow its single-writer rule. Never create a separate master database or status file to mirror the business records.

## Stop / ask

- If two applicable current sources still conflict, name the conflict and ask the recorded authority. Do not average them.
- If an expected owner or locator is absent, say `Not recorded`; do not invent one.
- Ask before moving information between Folders or changing a confirmed current record.

## Outputs

- A source-first answer with the smallest supporting record set.
- A new or updated Decision/learning with its locator and governing link when approved.
- A bounded route or history partition only when its growth trigger fires.

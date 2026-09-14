# OS-model migrations

The ledger of every change to the **operator-facing company model** described in `OS.md` (*How the company
is modelled*, the grounding principle, and the minimum-context law). Each entry is one OS-model version and
the exact change an operator must mirror by hand into their own `OS.md`, because `OS.md` is operator-owned
and a kernel upgrade never rewrites it.

**Newest first.** `kernel/OS-MODEL-VERSION` names the version the current kernel expects. The update routine
(`kernel/routines/update.md`, step 7) reads this ledger to find **every** entry with a version greater than
the operator's `OS-model version:` marker and up to the kernel's expected version, and presents them **in
order (oldest first)** so an operator who skipped releases applies each change. The marker is bumped to the
kernel value only **after all** the required changes are made, never after just one.

Only add an entry here when `OS.md`'s model text actually changes. A kernel release that changes routines but
not the operator-facing model does **not** get an entry (and does not move `OS-MODEL-VERSION`).

---

## 0.23
**Clarify the human operating model, context conflicts and evidence.** Update `OS.md` so that:

1. Systems are enduring business functions; Missions are bounded projects/interventions; Routines are recurring company processes. Every Mission still decomposes into functional Roles. Each Role has a coherent outcome, one named human accountable owner, an authority boundary and a human-led -> AI-assisted -> AI-run performance path. Tasks, tools, prompts and AI personalities are not Roles. Job, Guardian, capability and internal methods appear to the operator only when needed.
2. Grounding keeps **status**, **source** and **freshness** separate. Status is confirmed, reported but not checked, inferred, hypothesis, or simulated. A confirmed claim has a named source and as-of date. Legacy `[unverified]` means reported but not checked and is translated only when its record is next touched.
3. Context conflicts resolve by kind: physical access and capability constrain action; rules and named authority constrain approval; confirmed sources, Decisions, Mission outcomes and Role contracts govern company work; new evidence triggers an explicit correction; current requests propose change through approval; preferences affect presentation only; unresolved conflicts go to the person with authority.
4. `context/preferences.md` is the source for non-sensitive shared Folder interaction defaults, not one person's profile. A session request is not persisted unless the person explicitly asks to make it the Folder default after its audience is named.
5. Material decisions use the compact card in `OS.md`: Decision needed, Recommendation, Basis, Effect if approved, Reversibility, Decision owner. After execution, show what changed, its audience and whether any external action occurred.

Inspect any existing `context/preferences.md` before adopting the new scope. Remove personal or sensitive material from the shared file rather than silently relabelling it. No operator data is bulk-rewritten by this migration.

## 0.22
**Add the source-of-record principle** to `OS.md`, under *Minimum sufficient context (a kernel law)*.
Add a paragraph: *"Read the source of record before you assert a recorded value"* — if a value already has a
source of record (System name → `systems/INDEX.md`; owner/authority → `context/people.md`; a Role → `roles/`;
a Mission's status/outcome → its `mission.md`; a System's state/strategy → its record; a preference →
`context/preferences.md`), read that source before asserting it; never reconstruct a recorded value from
plausibility or model memory. It is the other face of the minimum-context law, not a licence to load
everything.

## 0.21
**The JTBD model.** Rewrite *How the company is modelled* in `OS.md` so that: a **Job** is the progress the
operator seeks in a circumstance, and the OS **diagnoses** a challenge into the Job before choosing work
(bounded: diagnose far enough to choose the next Mission, not to claim a root cause); a **Mission** is the
chosen intervention; **Roles** are the accountable units of execution a human and/or AI is *hired to perform*,
each with **one named human accountable owner at every autonomy level** (not "who, human or AI, is
accountable"); a System's **Roles-&-capabilities map is derived/earned**, not drawn up front. Add the
**grounding principle**: keep supplied fact / retrieved fact / inference / hypothesis distinguishable, and
never invent a company-specific fact. (Also add the `OS-model version:` marker itself if the `OS.md` predates
it.)

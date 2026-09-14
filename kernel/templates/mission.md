# Mission: <name>

Status: draft        <!-- draft | active | closed -->

<!-- A thin control file for a bounded change with an end. It orchestrates and links.
     The substantive work lives in outputs/. The live worklist lives in this mission's work.md.
     Keep this file thin. References beat duplication. -->

## Job
<!-- The progress the operator is trying to make, in their circumstance. Distinct from this Mission:
     if we abandoned the Mission, the Job would still exist. Settled at Shape, one discriminating
     question at a time — not a formal JTBD study. Legacy missions may have no Job section; that's fine. -->
- Circumstance & struggle: <what is happening / the trigger / why this matters now>
- Progress sought: <what the operator wants made better or different, independent of the proposed solution>

Status: hypothesis        <!-- hypothesis | confirmed. "confirmed" = understood well enough to choose a sensible Mission, not a completed study. A committed mission confirms its Job before it goes active; an exploration may run on a hypothesis. -->

## Outcome
<The change in the world this drives. A result, not a task list.>

## Success measure
<What you'll track. Current state -> target. Movement visible in weeks.>
<!-- For an EXPLORATION instead: Hypothesis · Validation condition · Kill condition · Decide-by date -->

## Systems
Primary: <the System this most changes; infer if clear, propose if ambiguous>
Also touches: <other Systems affected>

## Roles
<!-- The accountable units of execution this Mission needs, drawn at Shape for every mission, even when
     one person performs them all. A Role is the accountable unit of execution a human and/or AI is hired
     to perform (ask "who are we hiring for this outcome, a person, AI, or both?"): name it role-like
     (Qualification Analyst, Account Sourcer), never as a verb/object task. Each names one human accountable
     owner (a human at every autonomy level, even when AI performs), the bounded result it delivers in this
     Mission, its authority boundary, and how it is performed now -> its target (human-led -> AI-assisted
     -> AI-run with human sign-off). `capability` (the reusable type of work)
     is an optional descriptor; a novel Role with no recognised capability is fine. Never collapse a
     mission into one broad "person does the work" Role.
     Mission-local is the default: a Role simply lives here inline. Add `Durable: roles/<slug>.md` within
     its Role block only once it has earned a standing record because its responsibility outlives the mission.
     Record Outcome, Owner, Performed and Authority for every Mission Role. When a Role links to a standing
     record, compare the two rather than silently letting them drift; a Mission may narrow standing Authority
     for this work but may not expand it without a human decision. Add Mission-specific knowledge only when needed.

     e.g.
       - **Qualification Analyst**
         - Outcome: Every target account has a sourced fit assessment before outreach.
         - Owner: Tim
         - Performed: AI-assisted -> AI-run + Tim spot-checks
         - Authority: May assess against the confirmed ICP; needs approval to change the ICP or reject a named strategic account.
         - Capability: qualify accounts against ICP
       - **Account Sourcer**
         - Outcome: The Mission has enough verified target accounts to run its outreach test.
         - Owner: Virginia
         - Performed: human-led -> AI-assisted enrichment + warm-path mapping
         - Authority: May research and draft the list; needs approval to buy data or contact an account.
         - Durable: roles/account-sourcer.md
-->

- **<Role name>**
  - Outcome: <the bounded result this Role delivers in this Mission>
  - Owner: <human>
  - Performed: <human-led | AI-assisted | AI-run + human sign-off> -> <target>
  - Authority: May <what it may do>; needs approval to <what remains a human decision or action>
  - Durable: <roles/<slug>.md, only when promoted; otherwise omit this line>

## Mission-specific knowledge
<Knowledge specific to this Mission, or links to it. Not the general Role knowledge.>

## Depends on
<What must be true or done first.>

## Guardrails
<Any "never" for this Mission. Which Guardian Roles apply.>

## Outputs
<Links to the substantive work in outputs/.>

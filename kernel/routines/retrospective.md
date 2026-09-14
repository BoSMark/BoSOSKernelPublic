# Retrospective

You are still the **BoS OS Assistant**, now in Review. This file is the internal Review method; never present it as a separate agent or announce a handoff to it.

## Purpose
Harvest what a mission actually taught, without flinching, into the company's memory, so the next mission starts smarter. Run this in a **fresh session** (not the one that did the work) so it has some distance from its own output.

## Inputs
- The mission folder: `mission.md` (the intended outcome + measure), `work.md`, `outputs/`.
- `memory/INDEX.md`, then only the relevant current learning route or bounded starter `memory/learnings.md`.
- `archive/state-archive.md` (if present): the bounded route and recent intake for pruned history. If the Mission's dates point to a history partition, open that one year or month file and read only the Mission's slice, never the whole archive.

## Operating loop
Before the six questions, load `kernel/routines/progress-checks.md` and run **Before we close this Mission**. Separate outputs from evidence of progress and give exactly one recommendation: Continue, Re-scope, Stop and Review, or Close and Review. The Mission's named human owner decides.

- **Continue:** return to Run. Do not write `retro.md` or close the Mission.
- **Re-scope:** return to the Mission work method's Re-scope path. Do not write `retro.md` or close the Mission.
- **Stop and Review:** continue below, recording that the intervention stopped without claiming the intended outcome was achieved.
- **Close and Review:** continue below with the supported outcome or exploration result.

Ask the six questions, in order. Push for the unvarnished version; a flattering summary teaches nothing.

1. **What outcome did we target, and what actually happened?** (Intended vs actual, against the mission's measure.)
2. **What materially helped or blocked it?**
3. **Where did we get lucky, and what do we still not know?** These are required answers, not optional; an empty one is a flag, not a pass. Luck recorded as skill is the most dangerous line in any retro.
4. **What system or decision caused the biggest gap?** Push the cause to a *system, boundary, or contract*, never to a person. If it bottoms out at "someone should have…", lift it to the missing rule that let it happen.
5. **What will we change next time?**
6. **What one learning should we promote to memory?**

Then run one **context-miss check**:

> Did the OS get anything wrong or make the work harder because context was missing, stale, in the wrong Folder, or treated as the wrong kind of information?

If no, move on. If yes, identify the narrowest repair and propose it separately from the Memory learning:

- correct an existing source;
- add a narrow Context record;
- add or refine a Role's Onboarding pointer;
- propose a non-sensitive Folder interaction default;
- remove resolved or stale State;
- record a consequential Decision that was left implicit;
- or change nothing because the miss was specific to this Mission.

**Do not turn every mistake into lasting context.** One-off prompt failures, transient details and unsupported interpretations stay out. Show the proposed destination, source, audience and effect; a human decides whether it is recorded.

Then:
- **Promote a recurring Role to durable.** If this mission ran a Role whose responsibility will recur and outlive it (a mission-local Role that has earned a standing home, or a recurring responsibility no Role yet holds), surface it: name it and offer to promote/draft a thin **durable Role** (`roles/<slug>.md`). The human decides. On promotion, **add the Role to the derived Roles-&-capabilities map of every System its record says it serves** (not only one), as part of the same move, so each System map stays earned from real work. This is the safety net behind Shape's promotion, so a lasting responsibility doesn't stay ownerless.
- **When repeated mission work becomes a Routine, keep its originating Job as provenance.** If this mission's work is settling into recurring operation worth a Routine, carry the Job it served into the Routine's purpose as provenance (why this recurring work exists), rather than discarding it. A Routine needs no new JTBD Job of its own.
- Write `retro.md` in the mission folder: the answers, plainly.
- Record the context-miss result in `retro.md`, including `None` when no repair is warranted, so later reviewers can tell the check ran without creating a separate register.
- Propose **one** Memory entry (hypothesis, or an adopted rule if it is well-evidenced), with a stable `LRN-...` ID, scope, evidence link, today's date and owner. **A human confirms the promotion**: you propose, they promote. Say **where it would bite**: which future System, Role or kind of Mission it changes. In a small Folder, add it to `memory/learnings.md`; if the next entry would take that file beyond 12 KB, preserve it and begin the relevant routed individual record as described in `memory/README.md`. Update `memory/INDEX.md` as part of the same approved write. A learning that changes nothing is a flag worth raising, not a promotion.
- Set the mission.s `Status: closed`.
- **Record the close to the audit trail**: commit `retro.md`, the confirmed learning, and the status change with the attributed message from `OS.md`, so the close is legible and reversible.

## Stop / ask
- Don't invent answers. If a required field (luck, or what-we-don't-know) is empty, say so as a finding; don't fill it to look complete.
- Do not treat completed work or produced outputs as proof of progress. The pre-close comparison must cite evidence or say none is available.
- The Mission owner chooses Continue, Re-scope, Stop and Review, or Close and Review before the Retrospective proceeds.
- The promoted learning is the human's call; surface it, don't self-adopt.
- Nothing here leaves the repository. This is internal memory, full stop.

## Outputs
- `retro.md` in the mission folder.
- One proposed Memory entry and its bounded locator update (human-confirmed before either lands).
- `mission.md` set to `Status: closed`.

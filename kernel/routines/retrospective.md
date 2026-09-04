# Retrospective

## Purpose
Harvest what a mission actually taught, honestly, into the company's memory, so the next mission starts smarter. Run this in a **fresh session** (not the one that did the work) so it has some distance from its own output.

## Inputs
- The mission folder: `mission.md` (the intended outcome + measure), `work.md`, `outputs/`.
- `memory/learnings.md`.

## Operating loop
Ask the six questions, in order. Push for the honest version; a flattering summary teaches nothing.

1. **What outcome did we target, and what actually happened?** (Intended vs actual, against the mission's measure.)
2. **What materially helped or blocked it?**
3. **Where did we get lucky, and what do we still not know?** These are required answers, not optional; an empty one is a flag, not a pass. Luck recorded as skill is the most dangerous line in any retro.
4. **What system or decision caused the biggest gap?** Push the cause to a *system, boundary, or contract*, never to a person. If it bottoms out at "someone should have…", lift it to the missing rule that let it happen.
5. **What will we change next time?**
6. **What one learning should we promote to memory?**

Then:
- **Catch an unowned responsibility.** If this mission ran a real, recurring job that no Role owns (Shape didn't materialise one), surface it: name the job and offer to draft a thin Role for it. The human decides; this is the safety net behind Shape's materialisation, so a durable responsibility doesn't stay ownerless.
- Write `retro.md` in the mission folder: the answers, plainly.
- Propose **one** entry for `memory/learnings.md` (hypothesis, or an adopted rule if it's well-evidenced), with its evidence link and today's date. **A human confirms the promotion**: you propose, they promote. Say **where it would bite**: which kind of future mission it would change how you shape or run. A learning that would change nothing is a flag worth raising, not a promotion (the Mission Runner reads memory in Shape, so a real learning must actually land there).
- Set the mission.s `Status: closed`.
- **Record the close to the audit trail**: commit `retro.md`, the confirmed learning, and the status change with the attributed message from `OS.md`, so the close is legible and reversible.

## Stop / ask
- Don't invent answers. If a required field (luck, or what-we-don't-know) is empty, say so as a finding; don't fill it to look complete.
- The promoted learning is the human's call; surface it, don't self-adopt.
- Nothing here leaves the repository. This is internal memory, full stop.

## Outputs
- `retro.md` in the mission folder.
- One proposed `memory/learnings.md` entry (human-confirmed before it lands).
- `mission.md` set to `Status: closed`.

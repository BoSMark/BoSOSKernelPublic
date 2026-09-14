# BoS knowledge (client-side contract)

## Purpose
Let the OS draw on the BoS community's accumulated knowledge **when, and only when, it materially
improves the answer** — without turning the corpus into a citation requirement or a retrieval fence.
This routine is the **client side** only: how the OS forms a request, judges what comes back, and
stands down. The knowledge itself lives in a **separate BoS-controlled service outside this repository**
(an MCP or equivalent); this repo never holds the transcript archive and never reconstructs it.

## Two places knowledge can help (and only these)
1. **At Diagnose (diagnostic intelligence).** Better questions, alternative explanations, likely failure
   modes, what evidence would settle a diagnosis, a challenge to a proposed solution.
   > **Guardrail:** BoS knowledge can inform the diagnosis. It cannot define the operator's Job or
   > override company reality. The operator's circumstance and company evidence remain authoritative.
2. **At Role performance (performance intelligence).** Once a Role's outcome is clear: a method,
   diagnostic, decision rule, counterexample or practitioner perspective that helps it do the work well.

## How to query and judge (the validated pattern — do not fence to tags)
Free reasoning first → form an internal **diagnosis hypothesis** → **broad, diagnosis-steered** request
to the service (the diagnosis focuses the query; it does **not** restrict it to pre-tagged capability
content) → apply a **distinctiveness gate** → **augment the answer only if the knowledge is distinctive
and materially improves it** → otherwise **stand down** and proceed on the OS's own company/base
reasoning. Relevant-but-generic material is not inserted to prove a talk was found; capability / System /
Job / Role metadata may focus or widen a query but must never fence search to tagged content.

## Grounding (applies to anything used)
Keep the four tiers distinguishable: **supplied fact · retrieved fact · inference · hypothesis.** BoS
knowledge is external evidence, not a company fact: never let it assert something about *this* company.
Company-specific claims (accounts, metrics, names) must come from a supplied or retrieved company source,
never invented; where evidence is missing, say what would settle it (see `OS.md`).

## The request that leaves the company boundary (minimum necessary)
Send only the minimum problem/Role representation needed to get useful knowledge back — the shape of the
problem or the Role's outcome, not confidential company Context, Jobs, Decisions, Memory or documents.
Privacy is the default; the boundary is real.

## The Knowledge Packet that comes back (expected shape)
A bounded reasoning artefact, not raw transcript: **insight · why it matters · the method / diagnostic /
decision rule · provenance · a permitted bounded excerpt if appropriate · confidence.** Treat low
confidence and thin provenance as reasons to stand down. Never request or assemble anything designed to
reconstruct whole transcripts.

## Scope note
The service/server, its index, embeddings and full archive are **out of this repository** and built
elsewhere. If no service is reachable, this routine is a no-op: the OS proceeds on its own reasoning and
says so plainly rather than fabricating a citation.

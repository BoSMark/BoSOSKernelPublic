# Role: <name>

<!-- A thin operating contract for a durable Role: an accountable unit of execution, promoted to a
     standing record because its responsibility outlives any one Mission. It exists independently of who
     or what performs it. A human, an AI, or both can perform it, but the accountable owner is always a
     person. Keep this file thin: it defines the responsibility and says what to read; it does not hold
     the knowledge itself.
     Detailed methodology, playbooks and examples live in referenced context/ files, retrieved when relevant.
     For a Guardian (a Role that protects a standard across Systems), add two lines near the top:
       Type: Guardian
       Standard: <the one artefact it protects: the positioning doc, brand rules, security policy>
     The standard lives once and is referenced wherever it applies, never copied into another Folder.
     A Guardian is applied in place to work in any Folder the current operator can see; its review notes
     stay with that work. -->

Lifecycle: durable
Capability: <optional — the reusable type of work this Role instances, e.g. "qualify accounts". A novel Role with no recognised capability is fine.>

## Outcome
<The single outcome this Role owns, stated as a result not an activity. Pitch it as something that could be owned and progressively automated, not a person's title or "X does the work". If it reads as a person doing the work, it's at the wrong altitude: decompose it into the real units of work underneath.>

## Systems
<Which of the company's Systems this Role serves. One line each.>

## Accountable owner
<One named person. Always a human, even when execution is delegated to AI.>

## How performed: now → autonomy target
<Where this capability sits on the human-to-AI ladder today, and where it's heading. The rungs: human-led → AI-assisted (AI drafts, the person decides) → AI-run with human sign-off. State both ends plainly, e.g. "manual today → AI scores against the signals, human spot-checks." This trajectory is the point of a Role: a capability that gets more autonomous over time, not a fixed job. The accountable owner stays a person at every rung. Legacy `human-done` records mean `human-led` and remain readable.>

## Authority
May: <what this Role may do on its own>
Needs approval to: <what still needs a person: spend, publish, change what's on record>

## Onboarding

<!-- Progressive disclosure: start simple. A small Role just lists what to read.
     Split into the two tiers below only when the list grows enough that loading it all
     every time wastes context. The two-tier form is a scaling pattern the Role earns,
     not a required shape. -->

Read:
- <what someone reads before substantive work in this Role. Link to specific Context or a relevant Memory route, not the content itself.>

<!-- When the list grows, replace the single "Read:" above with the two tiers:

### Core knowledge
<What to read before substantive work in this Role.>

### Know when relevant
<Retrieve only when the task triggers it. "- <trigger> -> <what to read or which Role>">
-->

### Works closely with
<Descriptive only. Names the Roles this one coordinates with. Loads nothing.>

### Tools and access
<What this Role normally needs. Point to capabilities or context/tools-and-access.md where useful, never secrets or claims about a named user's live connection.>

# System: <name>

<!-- An enduring area the company must keep operating well. It never completes.
     This record is a one-glance operating contract, not a label. Keep it thin: it links to the work,
     it does not absorb it. A System record only exists once real work, ownership or state makes it useful. -->

## Purpose
<Why this area exists / what it must keep working well.>

## Leading outcome
<The small measure that says it is working. Current state -> target.>

## Accountable owner
<Who owns the result.>

## Current strategy
<The route currently chosen to move the outcome.>

## Roles & capabilities (derived)
<The one derived view of the durable Roles that serve this System. Not drawn up front: it accumulates as
Missions that touch this System promote durable Roles into `roles/`. The owner of record is each Role
(which names the Systems it serves); this list is reconciled from those, never asserted here independently,
so the same responsibility is never stated in two places that can drift. One line per durable Role: the
Role (link to `roles/`), its accountable owner (a named human), the reusable capability it instances
(optional), and its now -> autonomy target. Include any **Guardian** Role that constrains this System (it
carries `Type: Guardian`), noting what it gates. Empty is correct for a System no durable Role has been
earned in yet.>

<!-- Populated by Shape / Retrospective / the Assistant when a Role is promoted, for every System the Role's
     record says it serves, e.g.
  - Account Sourcer (roles/account-sourcer.md) · owner: <name> · capability: source accounts + warm path · human -> AI enrichment + warm-path mapping
  - Messaging Authority (roles/messaging-authority.md) · Type: Guardian · owner: <name> · gates: no claim off-positioning
-->

## Active Missions
<Derived view. The owner of record is each Mission (which names the Systems it affects); this list is reconciled from those, not asserted here independently. Links to missions/, not copies.>

## Routines
<Recurring work that keeps it running. Links to routines/.>

## State
<On or off track, with a link to the evidence. When the System has no active work, mark it `Dormant`; the record stays, references stay intact, and it wakes on the next mission that touches it.>

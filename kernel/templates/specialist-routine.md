# Specialist routine: <name>

<!-- A reusable expert prompt the OS reaches for when a step needs depth a core routine doesn't carry.
     BoS-owned, lives in kernel/routines/, listed in INDEX.md. Self-contained and thin: reference
     depth, don't absorb it. Optional and additive; a company runs fine with none. -->

## Use when
<The trigger. The specific step or situation where this earns its place, e.g. "a mission needs a competitive teardown", "a pricing change needs a sensitivity check". If a step doesn't match, don't load it.>

## Do not use when
<The nearest cases this method could be confused with, and the cheaper or safer alternative.>

## Why this method
<One sentence the Assistant can show the operator: why this method fits the current Role and what it cannot settle.>

## Reads
<The minimum records and evidence required. Links, not copied content. Never a whole Folder by default.>

## Produces
<The output and where it goes, usually a Mission's `outputs/`.>

## May change
<The exact records this method may propose or update. `None` is valid.>

## Cannot decide
<The decisions, authority changes, disclosures or external actions that remain with a named human.>

## Evidence standard
<The sources, freshness and claim-status standard required for the output.>

## Human reviewer
<The Role or named authority that reviews the output when review is required.>

## Method
<The expert steps, thin. A long runbook lives in a referenced file, not here.>

## Possible next method
<At most one or two likely follow-ons, each with its trigger. This is not a workflow graph.>

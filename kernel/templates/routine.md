# Routine: <name>

<!-- A thin operating contract for recurring work that keeps a System running.
     Keep it thin: detailed runbooks, reference material and outputs live separately and are retrieved
     when required. Otherwise it becomes a huge SOP that gets loaded every time it runs. -->

## Recurring outcome
<The standing outcome this maintains.>

## Owner
<One named person accountable.>

## Systems
<Which System(s) this serves. Links to systems/.>

## Roles
<The durable Roles this Routine draws on (links to roles/). A Routine has no Job section: it keeps a
System running against a standing outcome; it does not need a newly discovered JTBD Job.>

## Trigger or cadence
<When it runs: "first of the month", "whenever a new signup lands".>

## Required knowledge
<What to read to run it. Links, not the content.>

## Execution instructions
<The current steps, thin. Detailed runbooks live in a referenced file.>

## Scheduled run (optional)
<!-- Add only when this Routine is deployed to a scheduler. Plan the business process above first.
     Never store credentials, tokens, private connection identifiers or a live access snapshot. -->
Cadence and timezone: <business timing or event>
Source ready when: <condition that makes the input safe to process>
Host task: <host and non-secret task reference, or Not configured>
Execution identity: <named user or company/service connection; name its human owner>
May: <bounded reads and safe, reversible internal writes>
Must stop before: <actions requiring a named human>
Run state: <link to run-state.md, or Not needed>
On no new input: <normally no change and no notification>
On failure: <stop behaviour and named owner>

<!-- Query the host before stating live schedule status or latest run time. -->

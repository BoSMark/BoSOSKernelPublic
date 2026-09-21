# Kernel methods

The BoS OS's internal operating procedures. BoS-owned: replaced wholesale on upgrade, never edited in place. The operator works with one Assistant and sees the current phase; these file names are diagnostic, not a menu they must choose from. This index is the source of truth for the method set, so the rest of the OS points here rather than hardcoding a list that goes stale as the set grows.

## Core methods
The five always present, driving every session.

- **Update** (`update.md`): before anything else, check for a newer kernel and pull it in if there is one.
- **Bootstrap** (`bootstrap.md`): first light. Orient, research, draft `context/`, run a first mission.
- **Assistant** (`assistant.md`): the first thing a person meets. Orient, explain, coach, route.
- **Mission Runner** (`mission-runner.md`): take one mission from intent to accepted output (Shape / Plan / Run / Re-scope).
- **Retrospective** (`retrospective.md`): harvest what a closed mission taught into memory.

## Diagnostic methods
Loaded only when the operator asks for the check; never part of every session's context.

- **BoS check** (`health-check.md`): read-only validation of declared ownership, references, derived views, evidence labels and version compatibility. Reports plain failures and makes no repairs.

## Assistant support
Loaded by the small Assistant entry method only when the current request triggers it. Neither file is part of every direct-answer session.

- **Session orientation** (`session-orientation.md`): generic opening, one-screen Executive View, re-entry, priority guidance, workspace ambiguity and session-close State hygiene.
- **Record retrieval and growth** (`record-retrieval.md`): source-first company lookup, Context/Decision/Memory routing, historical retrieval and bounded record maintenance.
- **Install a mission** (`install-mission.md`): add a mission this Folder does not yet have (a second agent) from the connector catalogue — connector check, kernel gate, `get_mission`, local file write, ledger update, offer to run. Triggered when the operator asks to install/add/get a named agent.
- **Update installed missions** (`update-mission.md`): keep the instruction files of already-installed missions current with the catalogue — compare each local `mission_version` against `list_missions`, and for any behind, verify and overwrite only the BoS-owned `mission.md`/`guide.md`, never the operator's `work.md` or `outputs/`. Runs at session start after the kernel check, or on demand. The mission-level twin of `update.md`.

## Generated views
Read-only views produced from records that already own the information. They are never saved or maintained as separate state.

- **Role views** (`role-views.md`): the Mission Role Map shown at Shape or on request, plus the on-request Role Evolution View for bounded human-to-AI experiments.
- **Progress checks** (`progress-checks.md`): an internal JTBD trace shown in plain language before substantive AI work and before Mission closure. Used inside Run and Review, never presented as another feature or phase.

## Run support
Loaded from the Mission Runner only when its trigger matches; never presented as another mode or Assistant.

- **Continue across a Mission** (`mission-full-run.md`): after one explicit operator confirmation, work through every eligible item in the existing Mission worklist, continue past item-level blocks where independent work remains, and finish with status, evidence and one highest-value ask.
- **GitHub-managed team collaboration** (`github-collaboration.md`): when a Folder has several editors and has chosen GitHub, protect accepted file changes and check only explicitly linked live delivery evidence while the Assistant hides routine Git mechanics. `work.md` remains the sole work record.

## Routine support
Loaded when recurring work is being planned for a cadence or event, when its host binding is being managed, or when a scheduled run starts. It remains an ordinary company Routine to the operator.

- **Schedule and run a Routine** (`scheduled-routine.md`): define the business process before choosing a host, bind it to a declared execution identity and bounded standing authority, then run it with duplicate prevention, quiet no-op behaviour and human stop boundaries.

## Specialist methods
Reusable expert prompts the Assistant reaches for when a Role needs depth a core method does not carry: a specific analysis or domain method. Each is self-contained and names its own trigger ("use when ..."), drafted from `kernel/templates/specialist-routine.md`. Optional and additive: a company runs fine with none. They are discovered here, so adding one is: ship the file, add a line below.

- **BoS knowledge** (`bos-knowledge.md`): the client-side contract for drawing on the BoS community corpus at Diagnose and at Role performance — broad diagnosis-steered request, distinctiveness gate, stand down when nothing distinctive helps. The knowledge service itself is a separate BoS-controlled service outside this repo; this routine is client-side only.

## Extending the kernel: two channels that don't collide
New capability reaches an operator three separate ways. Keep them separate.

- **Kernel channel (this folder, via auto-upgrade).** New or changed routines and specialist prompts. BoS-owned, versioned by `KERNEL-VERSION`, delivered by `update.md`, replaced wholesale. Never touches operator content. This is how a capability lands in every deployed instance at once.
- **Mission channel (installed agents, via auto-upgrade).** The instruction files of an installed mission (`mission.md`, `guide.md`). BoS-owned, versioned by each mission's `mission_version`, delivered by `update-mission.md` from the connector catalogue, replaced wholesale after a sha256 verify. Never touches the operator's `work.md`, `outputs/` or edits. This is how a refined agent reaches everyone who already downloaded it.
- **System-package channel (operator space).** A System, for example an annual-planning system, ships with its own Roles, records and routines, installed into the operator's own `systems/`, `roles/`, `routines/`. Operator-owned, never arrives through a kernel upgrade, never overwritten by one.

So an expert prompt everyone should have is a kernel specialist routine; the Roles and records a specific System needs are a System package. Promote a specialist routine into Core only if it becomes something every session depends on; otherwise it stays a specialist entry.

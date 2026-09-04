# Kernel changelog

Newest first. Each entry: version, what changed, and a **Migration** line only when the operator must do something by hand (the auto-update never changes operator-owned files).

## 0.17.0
Every important law now has a lifecycle or a forcing function. The v0.16 model was conceptually right but left the good behaviour to good intentions; a live-system retro found six places where the design was correct but not yet enforced. This release makes them inevitable. The first run is unchanged, and no operator-owned file changes shape on day one.

- **Roles and Systems get a lifecycle.** They were always "earned", but nothing turned earned into materialised. Now the **Mission Runner materialises them at Shape**: when a mission needs a Role with no record and the responsibility is real, it drafts a thin Role inline (Type, a named human owner, a one-line outcome, Authority, an Onboarding read-list), reads it back, and gets one yes before carrying on. First real work in a System with no record offers to open the System record. The rule is **propose, do not silently bureaucratise**. The Assistant does the same outside a mission, and tends what exists (create, change, **merge**, retire); the Retrospective catches a responsibility that ran without an owning Role.
- **Retire is a review signal, not an auto-delete.** Long inactivity prompts the question "does this responsibility still exist?"; a person decides. A quiet System **keeps its record, marked `Dormant`**, and wakes on the next mission that touches it, so references never break.
- **Materialising is audited, not automatically a Decision.** Every materialisation lands in the audit trail; a `decisions/` entry is added only for a genuine organisational choice (a new accountability, a changed owner or authority, standing up a Guardian), so `decisions/` doesn't bloat.
- **State hygiene is now a forcing function, not a hope.** At session end the Assistant prunes **by meaning first**: remove resolved items, promote durable truth to `decisions/` / `memory/` / its source, keep only current exceptions. A **size tripwire is only a backstop**, and its threshold is configurable in `operator-rules.md`, not a fixed number. One-line summaries are bounded to a recent-change window. Where the host keeps no history, hygiene **archives rather than deletes**.
- **Minimum context has a stated fallback.** The principle is always on; only the routing changes with maturity. Before Roles exist, work routes from the Mission's own knowledge, the primary System's strategy and state, and a **bounded company baseline** (the fixed Bootstrap set, never a general read of `context/`). In Advisory mode the OS **names the minimum file set up front** instead of assuming retrieval it doesn't have.
- **Relationship ownership ends cross-link drift.** One relationship has one canonical owner: a Mission owns the Systems and Roles it names; a Role owns the Systems it serves. A System's Missions and Roles lists are **derived views**, reconciled from their owners by the Assistant as it reads, not asserted by hand in both directions.
- **A Guardian and its standard are canonical and live once.** A company-wide Guardian governing private work is **applied in place** across any Folder the current operator can see, never duplicated or shadowed. The standard is referenced, not copied; the Guardian's review notes and gate status stay with the private work, and nothing about it is written back. Permission use case 15 is rewritten to this.
- **Progressive disclosure for Onboarding.** A small Role's Onboarding is a single "Read:" list. The two-tier split (Core knowledge / Know when relevant) is a scaling pattern the Role earns when the list grows, not a required shape. This lowers the day-one concept count.
- **Polished after a real smoke test.** One early mission was run end to end through a fresh instance before release. Three small refinements came out of it: the **company baseline is now a named four-file set** (`company.md`, `people.md`, `values.md`, `operator-rules.md`) so the pre-Role fallback reads a named floor, not a guessed one; Shape now **asks the durability question out loud** before offering to materialise a Role, so a one-off never gets dressed up as a standing job; and State's **Blocked and Waiting-on-someone lines are stated as derived views**, rebuilt from each mission's `work.md` so they cannot drift.
- **Migration:** none. Every change is a kernel routine, template, or model refinement, refreshed for you by the auto-update. No operator-owned file needs a hand edit.

## 0.16.0
The operating model lands in the kernel: the OS now describes a company the way it actually works, and stays light while doing it.

- **Systems are the map.** A company operates the same eleven enduring jobs (Steer; Create Demand, Capture Demand, Win, Offer, Deliver, Keep; Fund, Staff, Run, Protect). You understand the company by starting with its Systems. The map is known from day one (`systems/INDEX.md`); an individual System earns its own record only when real work, ownership or state makes one useful. Ask *"show me the Systems"*, *"how is Create Demand doing?"*, *"who owns Win?"*.
- **Roles are first-class, with Onboarding.** A Role is an enduring job, defined once and independent of who performs it, performed by a human, by AI, or both, always with a person accountable. Each Role carries an **Onboarding** section: what someone needs to know to do the job, which is also what the OS reads to do work under it. `roles/` exists from day one and starts near-empty; a Role record materialises only when a real responsibility exists.
- **Guardian is a type of Role.** A Guardian protects a standard across Systems (messaging, brand, security). It carries `Type: Guardian`. It's not a separate noun and not a separate directory.
- **No Agent primitive.** AI is a way a Role is performed, recorded on the Role, not a second org running alongside the human one. There's no `agents/` folder and no standing agent roster.
- **Minimum-context law.** For every job, load the minimum authoritative context to do it correctly; retrieve deeper only when needed; never load a whole Folder just because it's visible. A Role's Onboarding is the routing mechanism: Core knowledge now, Know-when-relevant on trigger. Visible is not loaded.
- **Thin contracts.** A Role, a Mission and a Routine are each thin operating contracts that link to depth rather than absorbing it; substantive work lives in outputs and referenced context. New templates: `system`, `role`, `mission`, `routine`.
- **`decisions/` is a directory.** Consequential company-level decisions are retrieved by relevance, never loaded as one growing file. `context/decisions.md` is superseded.
- **"Space" is renamed "Folder"** everywhere, keeping the audience-named permission rule (a private Folder is created by the confidentiality test, not the org chart).
- **The first run is unchanged.** Bootstrap still asks three questions, researches with citations, asks for documents, and shapes one real mission. Nothing instantiates eleven Systems or a roster of Roles at bootstrap. The map is knowledge; the structure is earned.
- **Migration (existing installs only):** the operator-owned folders can't be created by the auto-update. Add by hand from this release: a `systems/` folder with `INDEX.md`, a `roles/` folder (with its `README.md`), and a `decisions/` folder (with its `README.md`); move your `context/decisions.md` content into `decisions/` and delete the old file. The model itself lives in the kernel routines, which the auto-update refreshes for you. `context/operating-model.md` and the old `brief.md` template are retired; you can delete `context/operating-model.md`.

## 0.15.0
The same OS now runs on Claude *and* ChatGPT, honestly, with the one real difference named plainly.

- **A neutral entry file, `OS.md`.** All the startup and rules live here now; `CLAUDE.md` and `AGENTS.md` are thin shims that just point to it, so nothing is tied to one tool's filename.
- **`HOSTS.md`:** how each host runs, the three ways it can go (*your assistant keeps the files* / *keeps them but can't undo* / *you keep the files*), a two-minute check to place any host, and how to refresh the kernel by hand where self-update can't write.
- **It tells you which way it's running.** When the assistant can't keep your files (e.g. ChatGPT), it says so in one line and then hands you each change to save, batched, with a save-ready **session packet** at the end of the session so nothing is lost.
- **Self-update degrades cleanly:** where it can't write the kernel, it checks and tells you a new version exists rather than failing.
- **Honest portability.** The FAQ and manual no longer over-promise: the routines run anywhere a model follows them; what varies is who keeps the files and how reliably a given model follows a long chain. Runs best in Claude; fully usable on ChatGPT.
- **Migration (existing installs only):** move your `CLAUDE.md` contents into a new `OS.md`, reduce `CLAUDE.md` to the one-line pointer, and add `AGENTS.md` (copy all three from this release). Nothing else changes.

## 0.14.0
Every part of running the company now has a visible home, and the OS can show you what it does.

- **Recurring work has a home, `routines/`.** A new operator-owned folder for standing procedures (the monthly review, the standing checklist), run the same way each time instead of re-shaped. Build one when settled work keeps recurring; a one-off stays a mission.
- **Where things stand, `state.md`.** One file, the live company-level snapshot (active missions, open handoffs, what's blocked, findings to re-confirm), kept current by the Assistant so tomorrow opens where today left off.
- **See what the OS does, `context/operating-model.md`.** A plain "you are here" map of what the OS does for each part today (decisions, work, state, knowledge, authority, memory) and what a fuller version would add. Ask *"what does the OS do?"*.
- **Learning now compounds.** A kept lesson is read back into shaping the next mission, and a contradicting one is raised as a challenge; the loop that was open (learnings went in, never came out) is closed.
- **Honest about what's structural.** The safety rules now say which protections hold no matter what (no tool = can't act, not-present = can't see, history = can undo) versus which are rules the AI follows. New FAQ: "What actually stops the AI doing something bad?"
- **The Assistant knows the whole surface** and the operator's guide covers it, so both can guide you to any capability.
- **Migration (existing installs only):** the new operator-owned files can't be created by the auto-update. Add by hand: a `routines/` folder, a `state.md`, and `context/operating-model.md` (copy the seeds from this release), plus the small `CLAUDE.md` additions (the operating-model line and the structural-vs-followed note).

## 0.13.0
Clarity and consistency pass, from a mental-model review of the v0.12.0 package. No new capability; this makes the OS describe itself accurately and gives a first-time operator a single map.

- **New `START-HERE.md`:** the whole OS on one screen: the one rule, the folders and who owns each, the five routines and when each fires, a mission's three steps, your first 20 minutes, and a plain note on what isn't built yet.
- **New `A-SESSION-WALKTHROUGH.md`:** one realistic session start to finish, showing where the OS pushes back, blocks, and waits.
- **Undo works from the first session.** The audit trail needs version history; README, the manual, and Bootstrap now make sure the folder has it (a one-time `git init` if you copied from a zip) before relying on undo.
- **Self-consistency fixes:** the README no longer names a stale version or a design-repo file you don't have; the shim no longer references an unbuilt registry; the Dropbox/synced-folder guidance and the disclosure rule now agree (a backup sync only you use isn't a disclosure); one canonical workspace shim instead of two; `context/preferences.md` (your pace setting) is now described where you'd look for it; unbuilt features (Systems) are marked as design, not described as working.
- **Migration (existing installs only):** remove any `operating-model.md` references from your operator-owned `CLAUDE.md` by hand, and run `git init` once if your folder has no version history. A fresh copy needs neither.

## 0.12.0
Two changes, from Mark's first-run feedback.

**Bootstrap is now a cited, document-aware first light.** It asks three opening questions (the two-letter shorthand is dropped from the openers; you can still set one later), and opens by telling you what the whole session will do before the first question. Its research now cites every claim and tags how sure it is (confirmed / reported / inferred), marks gaps as `[NEEDS INPUT]`, then **proactively asks for any internal documents**, mines and cites them, reconciles them against the public draft (a deck keeps its gloss; where internal disagrees with public, both are recorded), and puts the remaining gaps back to you.

**Every durable change is now audited.** Writes still land straight on disk (that's the point), but each durable change (to `context/`, `decisions.md`, `missions/`, `memory/`) is recorded to the version history with provenance (who · routine · mission), the most durable records carry an inline "who changed this" stamp, and you can ask the OS "what changed / who changed X / undo that" in plain language. Trust comes from being able to see and undo, not from approving every write in advance.

**The Assistant is a guide, not a switchboard.** It's now written to coach: guide more for a newcomer or anyone stuck, ease off for the fluent, and never leave you at a dead end. It tells you where you are as you go: the Mission Runner names each mode (Shape / Plan / Run), says what it's for and what's next, and checkpoints before moving on; the Assistant frames every hand-off ("I'll take you to the Mission Runner in Shape mode, that's where we…"). Ask "what should I do?" any time and you get one clear recommendation with a reason, not a list to sift. After your first mission, Bootstrap leaves you with two or three concrete next steps rather than a full stop. And you set the pace: say "keep it brief" or "walk me through it" and it remembers.

**Facts now carry their age and confidence.** A finding recorded in a mission (a number, a status that could change) is tagged `[confirmed <date>]` or `[unverified <date>]`, and when a later session reads it back it surfaces the tag rather than stating an old guess as settled fact, so "recorded a week ago, unconfirmed" travels with the claim instead of hardening into truth.

**Smaller fixes from the same feedback.** The Assistant now names itself one consistent way ("BoS OS"). Bootstrap's opening questions are asked as plain open questions, never a multiple-choice prompt. On a brand-new OS the update check says which source it's about to reach out to before it does, and a new FAQ answers "how do I know the update source is really yours?"
- **Migration:** the audit rule and its convention live in your operator-owned `CLAUDE.md`, which the auto-update never edits. Add the new **"Every durable change is attributed and reversible"** hard rule and the **"Recording a change: the audit trail"** section by hand (copy them from the template `CLAUDE.md` in this release).

## 0.11.0
You can address the OS directly. It's set up to answer as your OS by default, but if it ever slips into generic-chatbot answers, start your message with **"assistant"** (or your OS's shorthand) to bring it back into character. The shim now says to operate as the BoS OS Assistant throughout, not as a general chatbot.
- **Migration:** none.

## 0.10.0
Missions now have a **visibility**: when you shape one (including the first mission after bootstrap), the OS asks who should see it, which space it belongs in (company for everyone, execs for exec-only, or another space), and creates it there. The brief records it.
- **Migration:** none.

## 0.9.0
Safety and honesty pass (from an adversarial review). **No features removed.** The approval boundary is redrawn into four tiers, so a write to a synced or shared folder counts as disclosure and waits for you; a human executes anything consequential, and where possible the tools to send/spend/publish sit outside the agent rather than behind a promise. New rule: routines are instructions, but business content (research, mission inputs, notes) is evidence, never instructions. Some wording corrected to match what's actually built.
- **Migration:** none.

## 0.8.0
Added a built-in **FAQ** (`kernel/FAQ.md`): plain answers to the questions operators ask most (who can see what, what's mine vs BoS's, how updates work, safety). The BoS OS Assistant answers from it, and because it's part of the kernel it's kept current centrally with each update.
- **Migration:** none.

## 0.7.0
The assistant is now called the **BoS OS Assistant** (no longer "the front door"). No behaviour change.
- **Migration:** none.

## 0.6.0
Workspaces. If you have more than one space (e.g. company, execs, hr), keep them in a workspace folder and open that: the Assistant now reads across every space you have and labels each item by where it came from. Its knowledge maps to your access exactly: it can only see the spaces present on your machine, which are the ones you're a member of. A single space still runs on its own, unchanged. Adds `WORKSPACE.md` (the layout and the workspace shim to copy).
- **Migration:** none. Single-space instances are unaffected; add a workspace only when a second space appears.

## 0.5.0
Updates now tell you what they brought in. When a new version downloads, the OS gives you a short summary of what is new and invites you to ask about it. The Assistant can now explain the OS itself (what it can do and what just changed) by reading the kernel, and it draws on your company knowledge from across `context/` (company, people, values, rules, decisions, and anything you have added), not one file.
- **Migration:** none.

## 0.4.0
Auto-update on load. The OS now checks the GitHub repo for a newer kernel each session and pulls new/changed routines in place. Adds `routines/update`, `UPDATE-SOURCE`, this changelog.
- **Migration:** none for the kernel itself. To turn auto-update on in an instance created before 0.4.0, add this line to the top of your session flow in `CLAUDE.md`: *"At the start of every session, first follow `kernel/routines/update.md`, then `kernel/routines/assistant.md`."* New instances already have it.

## 0.3.0
Handoffs block in `work.md`; growable `context/` (+ `context/README.md`); authority boundaries in `people.md`; `context/decisions.md`.
- **Migration:** `context/decisions.md` and `context/README.md` are operator-owned, so an upgrade does not add them. Copy both from the template into an existing instance's `context/` to pick them up.

## 0.2.0
Bootstrap routine added; behaviours moved to `routines/`, shapes to `templates/`.

## 0.1.0
First kernel: Assistant, Mission Runner, Retrospective, templates, upgrade contract.

# FAQ: the questions people actually ask

Plain answers to the things operators ask most. The BoS OS Assistant reads this to help you, and it's part of the kernel, so it keeps itself current. Ask the Assistant to go further on any of them.

## Folders, access, and who sees what

**Why separate Folders instead of one big folder?**
Because access is the point. A Folder (company, execs, hr, finance) is a separate repo with its own members: it decides who can see a body of work. Keeping them separate is what lets HR work stay HR's without a wall of settings to maintain. One big folder means one big permission problem, and those compound.

**Who gets a Folder of their own?**
The confidentiality test decides, not the org chart. Execs, HR and the Board pass: they work on things that need a tighter audience, so each gets a Folder. Growth, Sales and Product fail: there's no reason to hide their work from the company, so they don't get a Folder, they work in the open company Folder tagged to the Systems they own. Add a Folder only when a real boundary appears.

**Can someone in the company Folder see the exec or HR work?**
Not unless they're a member of that Folder. You only get the Folders you belong to. Being in the company Folder tells you nothing about what's in execs or HR.

**I want the execs to see something without opening it to everyone. How?**
Put it in the execs Folder. Everyone in that Folder sees it, nobody else does. If a piece of work needs a tighter room than the ones you have, that's the signal to add a Folder, not to loosen an existing one.

**If I'm not in HR, can the OS show me HR things by accident?**
The OS can only read what's on your machine, and a Folder you're not a member of isn't there. That's the main protection, and it's a real one. It isn't a complete security boundary though: once a single session can see two Folders at once, keeping them apart depends on the session behaving, which is why moving anything between Folders waits for you and why sensitive work belongs in its own session.

**I'm in several Folders. Do I get one view, or hop between them?**
One view. Keep your Folders together in a workspace folder and open that. The Assistant reads across everything you have and tells you which Folder each thing came from. (See docs/WORKSPACE.md.)

**Can the OS take something from one Folder and put it in another?**
Only if you say so. Reading across your own Folders is free. Copying HR content into a company mission is sharing, and sharing waits for you. The OS won't quietly move things across a boundary.

**Can several people work in the same Folder without learning GitHub?**
Yes. During setup the Assistant asks whether the Folder has one editor or several. For a team it inspects the existing setup first and, with approval for any external configuration, can manage GitHub underneath. You say ordinary things such as "I'll take this", "show me what changed", "ready for review" or "accept it". The Assistant handles routine branch, checkpoint, review and merge mechanics. The Mission owner still accepts the work, and `work.md` remains the one backlog and status record.

**Can we use Dropbox or a shared drive instead?**
Yes, but only one person or session edits that shared copy at a time. BoS gives its narrow concurrency assurance only in a GitHub-managed Folder where people use separate working copies. A sync service can copy files and create conflicted copies; it cannot protect the meaning or accepted state of a Mission record.

## What's yours, what's ours

**What can I change, and what's off limits?**
Everything is yours except the kernel folder. Your context, your missions, your memory. The kernel is ours and it looks after itself. You never edit it.

**I don't like how something works. Can I change it?**
Yes. Copy the routine out under a new name into your context and use your version. It's yours from then on and nothing we ship will touch it. Don't edit the kernel copy, or the next update writes over you.

**Where do my files live, and are they backed up?**
In your own folder, as plain text. Keep it inside Dropbox or Drive so it's backed up and you can reach it from another machine. That's backup, not sharing: a folder only you use, so a write there needs no approval. A folder other people can open is different, and a write there waits for you. Nothing lives in an app you can't open.

**Is `local_context/` private?**
It stays out of Git commits and GitHub, apart from the tracked README that explains the rule. That does not make the files machine-private: Dropbox, Drive, backups, mounted workspaces, or anyone with access to the working copy may still copy or read them. They also have no Git history, so the OS cannot undo them. During Bootstrap you can keep a candid answer in the session only instead.

## Keeping it current

**How does it stay up to date?**
Every time you open it, it checks for a newer version and, if there is one, updates its own instructions before you start. It tells you what changed in plain terms, and you can ask about any of it.

**Will an update overwrite my work?**
No. Updates only ever change the kernel. Your context, missions, and memory are never touched. If a new version needs a step from you, it says so and waits.

**What if I'm offline, or the power goes out halfway through an update?**
Offline, it skips the check and carries on with what you have. An interrupted update is designed to be re-run: it stages everything before touching the live kernel, and writes the version stamp last, so the next run can tell it didn't finish and complete it. It's resilient, not bulletproof: a crash partway through applying files can leave a mixed state until the next successful run, which is one reason updates are supervised rather than silent.

**How do I know the update source is really yours, and not something the AI made up?**
It's written down, not invented. The one line in `kernel/UPDATE-SOURCE` names the repo the kernel is published from (`owner/repo@branch`); check it matches what you were given when the OS was set up (it's named in the README too). The update only ever *reads* from that one repo, and only ever changes files inside `kernel/`, never your context, missions, or memory. If you don't recognise the source, don't run the update, and ask whoever set the OS up. On a brand-new OS the update also says out loud which source it's about to check before it reaches out.

**Is this locked to Claude?**
No. Here's the precise version, because it's better than "runs anywhere". The routines are plain text and run on any assistant that will follow them; the shaping, the outcome-vs-activity push, the retro questions, the confidence tags need no special tool. What varies by host is one thing: whether the assistant can **keep your files for you** or only **tell you what to write**. It runs best in Claude (what we use); on ChatGPT you keep the files yourself and it hands you each change to save, and everything still works. `docs/HOSTS.md` names how each host runs. So: portable files, yes; identical behaviour on every model isn't promised, because how reliably a long instruction chain is followed differs between them.

## Getting started

**Why doesn't it build my whole company plan on day one?**
Because that's how you end up with a folder of documents nobody reads. It starts you on one real piece of work and fills in around it. The OS grows from what you actually do, so it stays a picture of the real business rather than a plan for one.

**Do I have to fill in a pile of forms first?**
No. The first session asks your name, company and whether this Folder has one editor or several, one question at a time. It researches the company, then asks what you want help with and the number you steer by. It asks where your candid answer may be stored before writing it, offers to use any documents you'd like to share, and drafts context for you to react to, every line cited. Correcting a draft is easy. Facing a blank page is not. That's the whole reason it works this way.

**How do I know setup will work in the next session?**
At the end of setup, the Assistant offers a fresh-session check. Open a new session and say "Where are things? This is my setup check." It should identify the company, Folder, current Mission and next decision or work item from the saved source paths without you retelling it. It must not claim the check passed from file creation alone or expose a working-copy-only note to another person.

**What happens when a fact in Context changes?**
Once the proper owner confirms and approves the replacement, the Assistant updates the file that owns the fact so only one version reads as current. Version history preserves the old value where the host supports it; without history, the Assistant warns before saving and includes the old → new change in its session account. If evidence or responsible people still disagree, both claims remain visibly sourced and dated until the owner resolves them. Consequential Decisions keep their own explicit supersession trail.

**Won't Decisions and Memory become too large over time?**
The record can grow; the amount opened for one piece of work stays small. A short index points to the relevant Decision or learning, and older locators and State history are filed by date. The Assistant opens the index and selected record, not the whole history. A small company can keep using its starter files; splitting happens only when a live route grows, with old content preserved.

**How do I make sure I'm talking to the OS, and not a generic answer?**
Mostly you don't have to. The project is set up to answer as your OS. If it ever replies like a general chatbot, off the top of its head rather than from your files, start your message with "assistant" (for example *"assistant, where are things?"*), or use your OS's two-letter shorthand. That's the nudge to come back into character.

## The words: Systems, Jobs, Roles, Guardians, Missions, Routines

**What's a System?**
One of the eleven enduring areas your company must keep operating well: Steer; Create Demand, Capture Demand, Win, Offer, Deliver, Keep; Fund, Staff, Run, Protect. A System never finishes. The route you take through it is your strategy. You understand the company by starting with its Systems. The map is known from day one, but a System only gets its own record when real work or ownership makes one useful.

**What's a Job?**
The progress you're trying to make in a particular situation (Jobs to Be Done) — separate from how you do it. You describe a challenge in your own words; the OS diagnoses it into the Job before it locks a Mission. A Job lives inside the Mission that serves it; there's no separate Jobs list to keep. "We need lead scoring" is a proposed solution, not a Job; the Job might be "stop wasting sales effort on prospects that never convert".

**What's a Role?**
A bounded functional responsibility or project workstream, defined independently of who currently performs it. Every Mission decomposes into Roles so you can see the whole machine, its human accountability, and which areas may evolve from human-led to AI-assisted or AI-run. A Role can be performed by a human, AI, or both, but the accountable owner is always one named person. Tasks, tools, prompts and AI personalities are not Roles. A Role starts inside its Mission and earns a standing record only when its responsibility recurs. Each standing Role carries an **Onboarding** section: what someone would need to know to take it on. That's also what the OS reads to perform the Role.

**How do I see who does what on a Mission?**
Ask **"show the Mission Role Map"** or **"who does what?"**. The Assistant generates one row per functional Role with its outcome, human owner, current and target performance, authority boundary and source. Missing information says `Not recorded`; the view never guesses or becomes another file to maintain.

**How do I see where AI could help next?**
Ask **"where can AI help next?"**. The Role Evolution View proposes at most one bounded experiment at the next performance rung, within the Role's recorded authority, and cites the evidence behind it. It assigns no readiness score, changes no Role and leaves sending, publishing, spending and irreversible action with a person.

**What's a Guardian?**
A Role that protects a standard across Systems: your messaging staying on-message, your brand, your security, your privacy. It's a type of Role (it carries `Type: Guardian`), not a separate thing to learn. A Guardian can detect, review, challenge, reject and gate work, but doesn't get to publish or spend just because it can gate those.

**What happened to "agents"? Does AI get its own org?**
No. AI is a way a Role is performed, recorded on the Role itself. There's no separate agent roster and no `agents/` folder running alongside the human org. Define the responsibility once; onboard humans and AI into it.

**What's a mission?**
One bounded piece of work with an end: a goal, a task list, and whatever it produces. It names the System it most changes and the Roles it needs. It's the unit the OS runs on.

**How does the Assistant keep AI work tied to the Mission outcome?**
Before substantive AI work, it says what it is taking on, why it matters now, which Mission and Role result it contributes to, the minimum sources it will use, what counts as done and where it will stop and ask. That explanation is generated from the existing Mission and worklist; it is not another file or concept to maintain.

**Can the Assistant take a whole Mission as far as it can?**
Yes. Once you accept the Plan, the Assistant offers to continue through every ready item it can safely perform instead of making you prompt it one task at a time. It makes the same offer when you return to an active Mission with useful work ready. You choose whether to start. During that run it stays inside the Mission, each Role's current performance and authority, and the existing rule that a person handles consequential action. If one item is blocked, it records the exact reason and continues with independent work.

**Where are the backlog and task statuses?**
In each Mission's existing `work.md`. `Next` is that Mission's committed executable backlog, `In progress` is work under way, `Blocked` is waiting for an exact decision, dependency or access, and `Done` records completed work and what it produced. `Handoffs` records work routed to or waiting on another person. There is no second task system. Potential future Missions and loose ideas do not go into a live Mission's `Next` list.

**How does it know which connected tools I can use?**
The Plan names the capability the work needs first, such as CRM read access. Only then does the Assistant check the relevant company and Role tool pointers and the connections available to you in this session. Immediately before use it checks the service, account or workspace, permission and Role boundary. Another person's connection is never assumed to be yours. A company may keep approved capability and restriction pointers in `context/tools-and-access.md`, but that file contains no secrets or live user-access list and is read only when planned work needs it.

**When is a Mission complete?**
Not merely when its tasks are checked or its documents exist. Before closing, Review compares the evidence with the progress and outcome you wanted. It recommends continuing, re-scoping, stopping or closing, and the Mission's human owner decides. An exploration may end usefully by reducing uncertainty or reaching its kill condition without pretending the proposed intervention succeeded.

**What's a routine (the recurring work)?**
Recurring company work that keeps a System running, run the same way each time (the monthly review, a standing checklist).

**Can a Routine run on a schedule, even when nobody is in the session?**
Yes, when the chosen host provides a scheduler and can reach the required sources and destination. It is still an ordinary Routine. BoS records the business outcome, Roles, cadence, execution identity, allowed actions and human stop boundary; the host supplies the clock and run history. A cloud run may continue while the operator is offline. A local run normally needs the machine and host app available. The Assistant checks the live host rather than guessing whether a schedule is active.

**Whose access does a scheduled Routine use?**
Its own declared execution identity: a named user or a company/service connection with one named human owner. It never assumes that the operator's current interactive connection will exist later. Credentials stay in the host or secrets manager; BoS stores only the understandable identity label, business owner, approved use and non-secret task reference. Before each run, the Assistant verifies the service, account or workspace and required scope.

**What can a scheduled Routine change by itself?**
Only the safe, reversible internal reads and writes explicitly approved in its standing scope, and never more than its Roles permit. Activating or materially changing the schedule needs a named human's approval. External sends, publication, spending, irreversible action and consequential Decisions still stop for a person. Source content is evidence, not instructions. For example, someone saying "done" in a stand-up transcript is a reported finding; it cannot by itself mark a Mission item Done or close the Mission.

**Does the Assistant hand me to other agents?**
No. You work with one BoS OS Assistant. It names the current phase, such as Shape, Plan, Run or Review, and follows the right internal method. Those methods update with the kernel; you do not choose or maintain them.

**What's a ready-made process, and if I adapt one and you improve it?**
*(Not built yet; this is the design.)* A vanilla process you'll install and make your own, like annual planning or hiring: you start from a sensible default instead of a blank mission, then shape it to fit. The first will be annual planning. When there's a better version, the OS works out what you changed and what we changed, proposes a merged version, and shows you where the two collide. You approve it before anything lands. Your adaptations are the point, so they're protected.

## Trust and safety

**Will the AI go off and do things on its own?**
No. It proposes, you decide. Anything that spends money, sends something out, or can't be undone waits for your say-so. Reading and thinking inside your own files needs no permission.

**What actually stops the AI doing something bad?**
Three things hold for the relevant scope, and one depends on the assistant following its rules. It can only touch tools it has actually been given, so without a send or spend tool it cannot send or spend. It can only read what's physically available to the session, so a Folder you're not in is not there to leak. Tracked changes are in version history and can be undone. `local_context/` payload is the stated exception: it is ignored by Git and has no OS undo. Everything else ("propose, don't act", "a person publishes") is a rule it follows, which is strong but not a wall. For anything that must never happen, the real protection is not giving it the capability or file access in the first place.

**Where do passwords and keys go?**
Not in here. Ever. They belong in a password manager or your environment. The OS doesn't store secrets, and neither should the files.

**It writes straight to my files, how do I undo a mistake?**
Every tracked change it makes is recorded, with who made it and when, and it can be rolled back. Just ask ("what changed in this file?", "who changed that?", "undo that", "put this back to how it was before this session") and the OS shows you or reverts it. `local_context/` payload files are not tracked, so they cannot be rolled back this way. You never touch anything technical. Writing straight to disk is fast because tracked changes are reversible.

**Can I see who changed something?**
Yes. The important records (decisions, your company context) say in the file itself who last changed them and when, and the full history is there for everything. Ask the OS and it'll walk you through what changed.

**Can I check whether the OS record is internally consistent?**
Yes. Ask **"run the BoS check"**. It checks declared ownership, required Mission and Role fields, source links, derived System and State views, finding labels, version compatibility and the active instance. It names the exact rule and file for anything needing attention and makes no repairs. A pass means the record satisfies its structural rules, not that the business is healthy or every fact is correct.

**What happens to my information over time, does the OS quietly throw things away?**
No. The OS keeps your working "where things stand" file small so every session opens fast, but small does not mean lossy. When something is resolved or closed, its lasting truth is first promoted to where it belongs (a decision to `decisions/`, a lesson to `memory/`, a piece of work to its output), and the item itself is then moved to `archive/`, not deleted. So the day-to-day view stays light, and the full record of what happened is still there, ready for a retrospective or a "remind me how that went" months later. There's no cut-off and nothing to configure: pruning is just the moment an item moves from the live view into the archive.

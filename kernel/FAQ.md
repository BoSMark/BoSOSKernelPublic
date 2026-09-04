# FAQ: the questions people actually ask

Plain answers to the things operators ask most. The BoS OS Assistant reads this to help you, and it's part of the kernel, so it keeps itself current. Ask the Assistant to go further on any of them.

## Folders, access, and who sees what

**Why separate Folders instead of one big folder?**
Because access is the point. A Folder (company, execs, hr, finance) is a separate repo with its own members: it decides who can see a body of work. Keeping them separate is what lets HR work stay HR's without a wall of settings to maintain. One big folder means one big permission problem, and those compound.

**Who gets a Folder of their own?**
The confidentiality test decides, not the org chart. Execs, HR and the Board pass: they genuinely work on things that need a tighter audience, so each gets a Folder. Growth, Sales and Product fail: there's no reason to hide their work from the company, so they don't get a Folder, they work in the open company Folder tagged to the Systems they own. Add a Folder only when a real boundary appears.

**Can someone in the company Folder see the exec or HR work?**
Not unless they're a member of that Folder. You only get the Folders you belong to. Being in the company Folder tells you nothing about what's in execs or HR.

**I want the execs to see something without opening it to everyone. How?**
Put it in the execs Folder. Everyone in that Folder sees it, nobody else does. If a piece of work needs a tighter room than the ones you have, that's the signal to add a Folder, not to loosen an existing one.

**If I'm not in HR, can the OS show me HR things by accident?**
The OS can only read what's on your machine, and a Folder you're not a member of isn't there. That's the main protection, and it's a real one. It isn't a complete security boundary though: once a single session can see two Folders at once, keeping them apart depends on the session behaving, which is why moving anything between Folders waits for you and why sensitive work belongs in its own session.

**I'm in several Folders. Do I get one view, or hop between them?**
One view. Keep your Folders together in a workspace folder and open that. The Assistant reads across everything you have and tells you which Folder each thing came from. (See WORKSPACE.md.)

**Can the OS take something from one Folder and put it in another?**
Only if you say so. Reading across your own Folders is free. Copying HR content into a company mission is sharing, and sharing waits for you. The OS won't quietly move things across a boundary.

## What's yours, what's ours

**What can I change, and what's off limits?**
Everything is yours except the kernel folder. Your context, your missions, your memory. The kernel is ours and it looks after itself. You never edit it.

**I don't like how something works. Can I change it?**
Yes. Copy the routine out under a new name into your context and use your version. It's yours from then on and nothing we ship will touch it. Don't edit the kernel copy, or the next update writes over you.

**Where do my files live, and are they backed up?**
In your own folder, as plain text. Keep it inside Dropbox or Drive so it's backed up and you can reach it from another machine. That's backup, not sharing: a folder only you use, so a write there needs no approval. A folder other people can open is different, and a write there waits for you. Nothing lives in an app you can't open.

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
No. Here's the precise version, because it's better than "runs anywhere". The routines are plain text and run on any assistant that will follow them; the shaping, the outcome-vs-activity push, the retro questions, the confidence tags need no special tool. What varies by host is one thing: whether the assistant can **keep your files for you** or only **tell you what to write**. It runs best in Claude (what we use); on ChatGPT you keep the files yourself and it hands you each change to save, and everything still works. `HOSTS.md` names how each host runs. So: portable files, yes; identical behaviour on every model isn't promised, because how reliably a long instruction chain is followed differs between them.

## Getting started

**Why doesn't it build my whole company plan on day one?**
Because that's how you end up with a folder of documents nobody reads. It starts you on one real piece of work and fills in around it. The OS grows from what you actually do, so it stays a picture of the real business rather than a plan for one.

**Do I have to fill in a pile of forms first?**
No. The first session asks three short questions, researches your company, asks for any documents you'd like to share, and writes a first draft for you to react to, every line cited. Correcting a draft is easy. Facing a blank page is not. That's the whole reason it works this way.

**How do I make sure I'm talking to the OS, and not a generic answer?**
Mostly you don't have to. The project is set up to answer as your OS. If it ever replies like a general chatbot, off the top of its head rather than from your files, start your message with "assistant" (for example *"assistant, where are things?"*), or use your OS's two-letter shorthand. That's the nudge to come back into character.

## The words: Systems, Roles, Guardians, Missions, Routines

**What's a System?**
One of the eleven enduring jobs your company must keep doing well: Steer; Create Demand, Capture Demand, Win, Offer, Deliver, Keep; Fund, Staff, Run, Protect. A System never finishes. The route you take through it is your strategy. You understand the company by starting with its Systems. The map is known from day one, but a System only gets its own record when real work or ownership makes one useful.

**What's a Role?**
An enduring job someone is responsible for, defined once and independent of who does it. A Role can be performed by a human, by AI, or by both, but the accountable owner is always a person. Each Role carries an **Onboarding** section: what someone would need to know if they joined that job tomorrow. That's also what the OS reads to do work under the Role.

**What's a Guardian?**
A Role whose job is to protect a standard across Systems: your messaging staying on-message, your brand, your security, your privacy. It's a type of Role (it carries `Type: Guardian`), not a separate thing to learn. A Guardian can detect, review, challenge, reject and gate work, but doesn't get to publish or spend just because it can gate those.

**What happened to "agents"? Does AI get its own org?**
No. AI is a way a Role is performed, recorded on the Role itself. There's no separate agent roster and no `agents/` folder running alongside the human org. Define the job once; onboard humans and AI into it.

**What's a mission?**
One bounded piece of work with an end: a goal, a task list, and whatever it produces. It names the System it most changes and the Roles it needs. It's the unit the OS runs on.

**What's a routine (the recurring work)?**
Recurring work that keeps a System running, run the same way each time (the monthly review, a standing checklist). Distinct from the OS's own **kernel routines** below.

**What's a kernel routine?**
One of the OS's own procedures: the Assistant, the Mission Runner, the Retrospective. They're ours and they update themselves. You don't write them.

**What's a ready-made process, and if I adapt one and you improve it?**
*(Not built yet; this is the design.)* A vanilla process you'll install and make your own, like annual planning or hiring: you start from a sensible default instead of a blank mission, then shape it to fit. The first will be annual planning. When there's a better version, the OS works out what you changed and what we changed, proposes a merged version, and shows you where the two collide. You approve it before anything lands. Your adaptations are the point, so they're protected.

## Trust and safety

**Will the AI go off and do things on its own?**
No. It proposes, you decide. Anything that spends money, sends something out, or can't be undone waits for your say-so. Reading and thinking inside your own files needs no permission.

**What actually stops the AI doing something bad?**
Three things that hold no matter what, and one that depends on it behaving. The three that hold: it can only touch tools it's actually been given, so if it has no way to send email or spend money, it *can't*, whatever it's asked; it can only read what's physically on your machine, so a Folder you're not in isn't there to leak; and every change is in version history, so anything can be undone. Everything else ("propose, don't act", "a person publishes") is a rule it follows, which is strong but not a wall. So for anything that must never happen, the real protection is not giving it the capability in the first place, not a line of text asking it not to.

**Where do passwords and keys go?**
Not in here. Ever. They belong in a password manager or your environment. The OS doesn't store secrets, and neither should the files.

**It writes straight to my files, how do I undo a mistake?**
Every change it makes is recorded, with who made it and when, and it can be rolled back. Just ask ("what changed in this file?", "who changed that?", "undo that", "put this back to how it was before this session") and the OS shows you or reverts it. You never touch anything technical. Writing straight to disk is fast *because* every change is tracked and reversible, not despite it.

**Can I see who changed something?**
Yes. The important records (decisions, your company context) say in the file itself who last changed them and when, and the full history is there for everything. Ask the OS and it'll walk you through what changed.

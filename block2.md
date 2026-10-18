## Block 2: Working with an agent

New pairs! This block, both pairs are going to work with an AI agent. An agent is an AI that reads and edits your files by itself, instead of just answering you in a chat window. That changes your job quite a bit: you're no longer writing prompts that produce text, you're giving instructions, reviewing a plan and checking what it changed.

> There's one rule for this block: you don't edit any file by hand. If the agent gets something wrong, you fix it by giving it another instruction. It will feel slower at times, but this is exactly how you find out where agents go wrong.

**This block, you write the prompts yourself.** This morning you got them ready-made. Now we only tell you the goal, what a good prompt for it needs to contain, and what to check afterwards. How you word it is up to you.

> Keep a **prompt log** in your team's shared document (not in the Codespace, remember: no hand edits there). Every time you write a prompt, paste it in and add one line: did it work, or did you have to fix it, and what did you change? This is the start of your team's prompt library.

> Stuck after two tries? Ask your coach for the example prompt for that step. Looking is allowed, just write down what the example does that yours didn't.

> **Watch your tokens.** Agents read your files again on every step, and a long chat gets read again with every message. So name the files in your prompt, and start a **new chat** for each step (keep the plan in your shared document, not in the chat). Your tool says you're out of tokens? Don't wait for it to reset: work on your partner's machine or switch tools, and tell your coach.

---

### Setting up (both pairs, about 10 minutes)

An agent needs real files to work on, so we'll do this block in a GitHub Codespace. That's basically VS Code running in your browser, nothing to install. One laptop per pair is enough.

* Open the Meridian workspace repo (your coach gives you the link) and click **Code** → **Codespaces** → **Create codespace on main**. Sign in with your GitHub account if it asks.
* Open the Copilot chat panel. If Copilot asks you to, enable **GitHub Copilot Free** (no credit card needed). Then switch the chat from **Ask** to **Agent**.
* Paste your team's instructions file from Block 1 into `.github/copilot-instructions.md`. From now on, Copilot reads this file automatically before every request you make in this workspace.

Time for your first agent task, and your first prompt: getting this morning's work into the files.

**Goal:** the backlog ends up in `backlog.md`, the glossary in `glossary.md`, the decisions in `decisions.md`, the open questions in `open-questions.md` and the business rules in a new file `business-rules.md`. The content itself doesn't change, it only moves.

A good prompt for this:
* Names every file the content has to end up in
* Says clearly what the agent is not allowed to do (hint: touch the content)
* Contains your team's shared document, so the agent has something to work with

Now open the **Source Control** panel on the left. Every file the agent touched is listed there, and when you click one, you see exactly what changed. You'll be using this view all block long, because this is how you check what an agent did.

* Pick one story in `backlog.md` and compare it with your shared document. Is it still word for word the same?

> This Codespace is your pair's own scratch space. Please don't push anything back to the repo. At the end of the block, you simply copy your results back into your team's shared document.

---

## Pair AC: filling the gaps in the backlog

Most teams miss the same things: regulatory complaints, extensions and escalations. You're going to let the agent add those. On top of that, a "previous session" left behind three acceptance criteria that aren't quite right, and you'll let the agent fix those too.

* Ask your coach for `flawed-acceptance-criteria.md` and let the agent save it in the workspace.

### Step 1: plan before you act

Never let an agent start changing files before you've seen its plan. That's the habit of this block.

**Goal:** a plan, and no changed files yet, for three things:
1. User stories with acceptance criteria for regulatory complaints (escalation to compliance within 2 working days)
2. Stories for the extension flow (a handler asks for more time with a reason, the team leader approves) and for a missed deadline without an extension
3. The factual error in each of the three flawed acceptance criteria, compared to `meridian-brief.md`, and how to fix it

A good prompt for this:
* Tells the agent which files to read first
* Says in so many words that nothing may be changed yet
* Asks for a plan per part, not one long list
* Asks for the file and the source quote behind every planned change
* Says what to do when the brief doesn't give an answer (hint: flag it, don't decide it)

After you got the plan:
* Read it before you let it do anything. Look at the three flawed criteria: do you agree with the error it found? Check each one in the brief yourself.
* Did it plan the business customer question as a story? It shouldn't, that one is still an open question. Tell the agent.

### Step 2: execute it, one step at a time

**Goal:** the agent carries out the plan, one part at a time, and you check after each part.

A good prompt for this:
* Points to the plan, so you don't have to repeat it
* Says the agent has to stop after each part and list what it changed
* Sets limits: nothing gets removed without asking you, and no invented source quotes

After each part, open the changed files in the Source Control panel.
* Does the regulatory escalation go to compliance within 2 working days? Not 5 days, and not to the team leader?
* Does the missed-deadline flow treat a missed 5-day target differently from a missed 8-week deadline? Only the 8-week one requires a letter to the customer.

### Step 3: did it follow your house rules?

**Goal:** a list of every place where what the agent added breaks the rules in your instructions file.

A good prompt for this:
* Points to the file with the rules
* Asks for every place where a rule wasn't followed, not for a verdict like "looks fine"

> If the agent keeps breaking the same rule, chances are the rule isn't clear enough. Improve your instructions file (that's the one file you may ask the agent to edit for this) and remember what you changed, we'll ask you about it in Retro 2.

---

## Pair BD: restructuring the backlog and drawing the flows

You're going to let the agent clean up the entire backlog in one go, and then turn it into process diagrams.

### Step 1: plan before you act

**Goal:** a restructuring plan, and no changed files yet, for these problems:
1. Stories that don't follow "As a ... I want ... so that ..."
2. Stories without a source quote from `meridian-brief.md`
3. Terms that don't match `glossary.md`
4. Acceptance criteria that can't be tested

A good prompt for this:
* Tells the agent which files to read
* Says that nothing may be changed yet
* Asks for every story that needs to change, with the reason why, per problem

After you got the plan:
* Compare it with what you see in the backlog. Did it flag things that aren't actually a problem? Did it miss things that are?

### Step 2: execute the restructure

**Goal:** the backlog is cleaned up, without losing what it says.

A good prompt for this:
* Says in which order to work (hint: terminology first, testability last) and to stop after each step and list what changed
* Protects the meaning: an acceptance criterion may become clearer, but it can't say something else
* Doesn't allow removing a story without asking you
* Forbids invented source quotes: if a story has no source, the agent flags it

After the restructure:
* Open `backlog.md` in the Source Control panel and go through the changes.
* Pick three stories it changed. Do they still say what they said before?
* Did it invent a source quote anywhere? Search for it in the brief.

### Step 3: draw the flows

**Goal:** two Mermaid diagrams, each in its own file in a `diagrams/` folder, and a reference to the right diagram in every story it covers:
1. `main-flow.md`: the complaint from submission to closure, with every decision point
2. `extension-flow.md`: what happens when a handler needs more time

A good prompt for this:
* Names the files and the folder
* Says what the diagrams have to be based on
* Asks for the references in the stories as part of the same task

After the agent is done:
* Open one of the diagram files and click the preview icon in the top right. Does it render?
* Look at how a complaint gets closed in the main flow. Do you see the two reminders, the 14-day letter and the manual sign-off? Or does the diagram just close it automatically?

### Step 4: reflect

This one isn't a prompt for the agent, it's a conversation with your partner. Write your answers in `decisions.md` (through the agent, of course, so this is one more prompt for your log).

* What did the agent do that you didn't expect?
* At what point did you stop trusting it, and why?
* What would you want to have in place before you let an agent loose on a real client's documents?

---

### The last 5 minutes, both pairs

* Ask the agent to show you the final content of each file and paste it back into your team's shared document.
* Now build your **context pack**: one short document with three parts, each under its own heading: the backlog, the open questions and your prompt log. Leave the rest in your shared document. The smaller the pack, the less your next tool has to read.
* Why? In Block 3 you'll work in a different tool (most of you in Claude.ai), and that tool knows nothing about today. Your work doesn't live in a chat, it lives in files, and the context pack is how it travels with you.
* Pick your **best** and your **worst** prompt from your log. You'll be asked for them in Retro 2.

### Done?

Pair AC:
* Regulatory complaint stories exist, with escalation to compliance within 2 working days
* Extension and missed-deadline stories exist, with the 5 days and the 8 weeks kept apart
* The three flawed criteria are corrected, each one with a source quote
* The business customer question is still an open question

Pair BD:
* The backlog is restructured, without any invented source quotes
* Both diagrams render, and the main flow doesn't close complaints automatically
* Your reflection is in `decisions.md`

Both pairs:
* Your instructions file is better than it was this morning
* Everything is back in your team's shared document
* Your context pack is ready: backlog, open questions and prompt log, nothing else
* Your prompt log has every prompt you wrote, each with a one-line verdict
* You picked your best and your worst prompt

What you learned in this block:
* What the difference is between chatting with AI and letting an agent work on your files
* Why you always let an agent make a plan before it starts changing things
* How to check what an agent really did, by reading the changes instead of its summary
* How an instructions file in the project gives an agent your team's rules
* What a prompt needs to contain to keep an agent on a leash
* Why your work has to live in files you can carry to another tool, and not in one chat

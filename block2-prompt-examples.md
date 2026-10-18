## Block 2: Working with an agent

New pairs! This block, both pairs are going to work with an AI agent. An agent is an AI that reads and edits your files by itself, instead of just answering you in a chat window. That changes your job quite a bit: you're no longer writing prompts that produce text, you're giving instructions, reviewing a plan and checking what it changed.

> There's one rule for this block: you don't edit any file by hand. If the agent gets something wrong, you fix it by giving it another instruction. It will feel slower at times, but this is exactly how you find out where agents go wrong.

---

### Setting up (both pairs, about 10 minutes)

An agent needs real files to work on, so we'll do this block in a GitHub Codespace. That's basically VS Code running in your browser, nothing to install. One laptop per pair is enough.

* Open the Meridian workspace repo (your coach gives you the link) and click **Code** → **Codespaces** → **Create codespace on main**. Sign in with your GitHub account if it asks.
* Open the Copilot chat panel. If Copilot asks you to, enable **GitHub Copilot Free** (no credit card needed). Then switch the chat from **Ask** to **Agent**.
* Paste your team's instructions file from Block 1 into `.github/copilot-instructions.md`. From now on, Copilot reads this file automatically before every request you make in this workspace.
* Time for your first agent task: getting this morning's work into the files.

```
I'm going to paste my team's work from this morning. Put each part in the right file:
the backlog in backlog.md, the glossary in glossary.md, decisions in decisions.md, open
questions in open-questions.md, and the business rules in a new file business-rules.md.
Don't change the content, only put it in place.

[paste your team's shared document]
```

* Now open the **Source Control** panel on the left. Every file the agent touched is listed there, and when you click one, you see exactly what changed. You'll be using this view all block long, because this is how you check what an agent did.

> This Codespace is your pair's own scratch space. Please don't push anything back to the repo. At the end of the block, you simply copy your results back into your team's shared document.

---

## Pair AC: filling the gaps in the backlog

Most teams miss the same things: regulatory complaints, extensions and escalations. You're going to let the agent add those. On top of that, a "previous session" left behind three acceptance criteria that aren't quite right, and you'll let the agent fix those too.

* Ask your coach for `flawed-acceptance-criteria.md` and let the agent save it in the workspace.

### Prompt 1: plan before you act

```
Read backlog.md, glossary.md, business-rules.md and flawed-acceptance-criteria.md.

Make a plan, but don't change any file yet, for:
1. Adding user stories with acceptance criteria for regulatory complaints (escalation to
   compliance within 2 working days)
2. Adding stories for the extension flow (a handler asks for more time with a reason, the
   team leader approves) and for a missed deadline without an extension
3. Finding the factual error in each of the three flawed acceptance criteria, compared to
   meridian-brief.md, and how to fix it

For every planned change, name the file and the source quote it's based on.
```

* Read the plan before you let it do anything. Look at the three flawed criteria: do you agree with the error it found? Check each one in the brief yourself.
* Did it plan the business customer question as a story? It shouldn't, that one is still an open question. Tell the agent.

### Prompt 2: execute it, one step at a time

```
Execute the plan. After each of the three parts, stop and list what you changed before you
continue. Don't remove anything without asking me first, and don't invent source quotes.
```

* After each part, open the changed files in the Source Control panel.
* Does the regulatory escalation go to compliance within 2 working days? Not 5 days, and not to the team leader?
* Does the missed-deadline flow treat a missed 5-day target differently from a missed 8-week deadline? Only the 8-week one requires a letter to the customer.

### Prompt 3: did it follow your house rules?

```
Check every story and acceptance criterion you added against the rules in
.github/copilot-instructions.md. List every place where you didn't follow them.
```

> If the agent keeps breaking the same rule, chances are the rule isn't clear enough. Improve your instructions file (that's the one file you may ask the agent to edit for this) and remember what you changed, we'll ask you about it in Retro 2.

---

## Pair BD: restructuring the backlog and drawing the flows

You're going to let the agent clean up the entire backlog in one go, and then turn it into process diagrams.

### Prompt 1: plan before you act

```
Read backlog.md and glossary.md. Without changing anything yet, make a restructuring plan
for these problems:
1. Stories that don't follow "As a ... I want ... so that ..."
2. Stories without a source quote from meridian-brief.md
3. Terms that don't match glossary.md
4. Acceptance criteria that can't be tested

List every story that needs to change, and why.
```

* Compare the plan with what you see in the backlog. Did it flag things that aren't actually a problem? Did it miss things that are?

### Prompt 2: execute the restructure

```
Execute the plan. Rules:
- Don't change the meaning of any acceptance criterion, only its clarity and testability
- Don't remove a story without asking me
- Never invent a source quote: if a story has no source, flag it instead
Start with terminology, then format, then sources, then testability. Stop after each step
and list what you changed.
```

* Open `backlog.md` in the Source Control panel and go through the changes.
* Pick three stories it changed. Do they still say what they said before?
* Did it invent a source quote anywhere? Search for it in the brief.

### Prompt 3: draw the flows

```
Based on backlog.md and meridian-brief.md, create two Mermaid diagrams, each in its own file
in a diagrams/ folder:
1. main-flow.md: the complaint from submission to closure, with every decision point
2. extension-flow.md: what happens when a handler needs more time

Then add a reference to the right diagram in every story it covers.
```

* Open one of the diagram files and click the preview icon in the top right. Does it render?
* Look at how a complaint gets closed in the main flow. Do you see the two reminders, the 14-day letter and the manual sign-off? Or does the diagram just close it automatically?

### Prompt 4: reflect

This one isn't a prompt, it's a conversation with your partner. Write your answers in `decisions.md` (through the agent, of course).

* What did the agent do that you didn't expect?
* At what point did you stop trusting it, and why?
* What would you want to have in place before you let an agent loose on a real client's documents?

---

### The last 5 minutes, both pairs

* Ask the agent to show you the final content of each file and paste it back into your team's shared document. Your team needs it in Block 3.

### Done?

Before lunch at 12:45:

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

What you learned in this block:
* What the difference is between chatting with AI and letting an agent work on your files
* Why you always let an agent make a plan before it starts changing things
* How to check what an agent really did, by reading the changes instead of its summary
* How an instructions file in the project gives an agent your team's rules

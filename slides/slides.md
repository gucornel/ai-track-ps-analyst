---
theme: default
title: FA Day Theory
info: |
  AI Track, Module 2, Functional Analyst Day.
  The short theory parts for the kick-off, Block 1 to 3 and the wrap-up.
layout: cover
fonts:
  sans: Public Sans
  serif: Rubik
  mono: Fira Code
transition: fade
mdc: true
---

<div class="eyebrow">AI Track · Module 2 · Functional Analyst Day</div>

# Working with AI,<br>carefully and efficiently

A bit of theory for every block of today. Short, so you can get back to work.

<!--
We use this deck in five short parts: the kick-off (slides 2 to 5, about 10 minutes), 15 minutes at the start of Block 1, 2 and 3, and the last three slides during the wrap-up. There's no theory in Block 4. Keep every part short. People learn during the exercises, the theory just gives them the words for what they're about to run into.
-->

---

<div class="eyebrow">Today</div>

# What are we doing today?

<div class="grid grid-cols-3 gap-5 mt-6">
<div class="card">
<div class="label">BLOCK 1 · MORNING</div>
<h3>Chat</h3>
<p>Prompt well, check by hand, write your house rules</p>
</div>
<div class="card">
<div class="label">BLOCK 2 · BEFORE LUNCH</div>
<h3>Agent</h3>
<p>AI that reads and edits your files, under your rules</p>
</div>
<div class="card">
<div class="label">BLOCK 3 · AFTERNOON</div>
<h3>Grounding</h3>
<p>AI that reads the real regulation, and skills you can reuse</p>
</div>
</div>

<div class="footer">Kick-off · Along the way, we store everything that works, so you don't have to type it again</div>

<!--
Explain the shape of the day in about a minute. The thing to stress: this time every pair gets to do chat, agent and grounding. The pairs work on different tasks, but nobody misses out on a technique like in the first edition. Also mention the thread through the day: their prompts become house rules in Block 1, the agent uses those rules in Block 2, and in Block 3 they build a skill. Don't say anything about Block 4.
-->

---

<div class="eyebrow">How AI works with context</div>

# What does an AI actually know about Meridian?

<div class="grid grid-cols-2 gap-5 mt-6">
<div class="card grey">
<h3>Training</h3>
<p>Billions of public texts. General patterns: what complaint processes usually look like. Nothing about Meridian.</p>
</div>
<div class="card accent">
<h3>The context window</h3>
<p>Your prompt, the chat so far, the files you attach. This is the only place Meridian exists for the AI.</p>
</div>
</div>

<div class="footer">Kick-off · If it's not in the context, the AI fills it in with what usually happens</div>

<!--
A quick recap of Module 1, but practical. The AI predicts the most likely next words, based on two things: what it was trained on and what's in its context window. Everything about this client (Sarah, Marc, Priya, the 7-day auto-close) only exists in the context. If it's not in there, the AI answers from general patterns, and those sound very confident. That's why we keep giving it the source today, and not our own summary.
-->

---

<div class="eyebrow">How AI works with context</div>

# What happens when the brief doesn't say?

<div class="grid grid-cols-2 gap-4 mt-5">
<div class="card"><h3>It fills gaps</h3><p>with what's plausible, not with what's true</p></div>
<div class="card"><h3>It picks a side</h3><p>often the first or loudest voice in the source</p></div>
<div class="card"><h3>It rarely says "I don't know"</h3><p>unless you ask it to</p></div>
<div class="card"><h3>Long chats drift</h3><p>old context crowds out what matters now</p></div>
</div>

<div class="footer">Kick-off · The brief you just read contradicts itself, and that's on purpose</div>

<!--
This slide sets up the whole day, so be careful not to give anything away. Don't mention the auto-close contradiction, just say the brief contradicts itself on purpose. The question to keep in mind all day: does the AI tell you it's making a decision, or does it simply decide? The last box is a practical one: when a chat gets long and messy, start a new one and only bring what you need. We come back to that during the wrap-up.
-->

---
layout: center
class: statement
---

<div class="eyebrow">The one rule of the day</div>

# Use AI for every decision today,<br>and check what it tells you

We kept the brief short, so you can always check. Every exercise tells you what to look at.

<!--
This is the rule of the first edition, with something added. The feedback last time was that the brief was too big to check, so people ended up trusting the AI. This time the brief is three short documents, and every prompt has bullets that tell people what to check. Say it out loud: if you skip the check, you're not testing the AI anymore, you're trusting it. Then go straight into Block 1.
-->

---
layout: section
---

<div class="eyebrow">Block 1 · 09:30</div>

# Prompting well

How do you give AI the right context, and how do you make it tell you what it found and what it guessed?

<!--
The Block 1 theory takes about 15 minutes, this slide and the next four. After that, pairs AB and CD start on their prompt ladders. Any chat tool is fine this morning.
-->

---

<div class="eyebrow">Prompting well</div>

# What goes into a good prompt?

| Part | In today's case |
|------|-----------------|
| **Role** | You're a functional analyst on a requirements engagement |
| **Context** | The three Meridian documents, pasted or attached in full |
| **Task** | Propose a user story backlog, organised into epics |
| **Format** | As a … I want … so that …, with a source quote per story |
| **Constraints** | Only use the source. Label inferences. Don't resolve contradictions |

<div class="footer">Block 1 · You might know frameworks like CO-STAR or CRISPE: they're variations on these same parts</div>

<!--
Don't turn this into a lecture about frameworks. The point is that most weak prompts only contain the task. Walk through the table using Prompt 2 of their ladder, which they'll be sending in a few minutes anyway. You can also mention that an example helps: if you want stories written in a certain way, give it one good story first (that's called few-shot prompting). The constraints row is where the quality of today's work is decided.
-->

---

<div class="eyebrow">Prompting well</div>

# Give it the source, and make it show its work

<div class="grid grid-cols-2 gap-5 mt-5">
<div class="card grey">
<div class="label">WEAK</div>
<p>"Sarah wants auto-close after 7 days, compliance is worried about some rules. Write the stories."</p>
<p class="text-sm mt-3">That's your summary, with your assumptions already in it. There's nothing to check it against.</p>
</div>
<div class="card accent">
<div class="label">STRONG</div>
<p>"[the three documents]. For each story, quote the source and who said it. Label anything you inferred. Don't resolve contradictions: list them."</p>
<p class="text-sm mt-3">Every claim comes with a quote you can look up in two minutes.</p>
</div>
</div>

<div class="footer">Block 1 · Can't find the quote in the source? Then you probably found an invented requirement</div>

<!--
Three habits on one slide. First: paste or attach the source, never your own summary, because your summary already contains your interpretation. Second: ask for a quote with every claim, so checking it becomes a search instead of a judgement call. Third: ask it to label what it inferred, otherwise a guess looks exactly like a fact. These three lines should end up in their house rules at the end of the block.
-->

---

<div class="eyebrow">Prompting well</div>

# You can't check everything, so what do you check?

<div class="grid grid-cols-3 gap-5 mt-5">
<div class="card">
<div class="big-number">1</div>
<h3>Spot-check</h3>
<p>Pick two or three claims at random and find their quote in the source</p>
</div>
<div class="card">
<div class="big-number">2</div>
<h3>Risk-check</h3>
<p>Check the one thing that would hurt most if it were wrong: the numbers, the rules</p>
</div>
<div class="card">
<div class="big-number">?</div>
<h3>Ask it back</h3>
<p>"Which contradictions did you find, and how did you resolve them?"</p>
</div>
</div>

<div class="footer">Block 1 · Every prompt in your ladder tells you what to check by hand. Don't skip those.</div>

<!--
This one deals with the feedback from the first edition: "we just assumed AI was right, because we couldn't check it." Nobody can check everything, and that's not what we're asking. We want them to build a habit: spot-check a few claims at random, and always check the thing that would hurt most if it's wrong (timeframes, legal obligations). And ask the AI what it decided for you. Point out that the brief is small enough to do this in a couple of minutes.
-->

---

<div class="eyebrow">Working efficiently</div>

# Tired of typing the same rules? Write them down once

| Tool | Where your house rules go |
|------|---------------------------|
| **M365 Copilot** | Settings → Personalization → Custom instructions, or a Copilot Notebook |
| **Claude.ai** | A Project, with project instructions |
| **GitHub Copilot** | `.github/copilot-instructions.md` in the repo, for the whole team |

In the last 15 minutes of this block, your team writes 10 to 20 lines of house rules, based on the prompts that worked best. The agent will use them in Block 2.

<div class="footer">Block 1 · Cheat sheet: ai-cheat-sheets/working-efficiently.md</div>

<!--
This is where the efficiency thread starts (the fourth piece of feedback from the first edition). By 10:30 they'll have typed "use only the source, quote it, label inferences" about five times. Custom instructions are the easiest fix: rules the AI reads before every request. Remind them to start on their instructions file by 10:45 at the latest, Block 2 needs it. The GitHub Copilot version is the most interesting one for a team, because the rules live in the project, right next to the work.
-->

---
layout: section
---

<div class="eyebrow">Block 2</div>

# Working with an agent

An AI that reads and edits your files by itself. You give the instructions, review the plan and check what it changed.

<!--
The Block 2 theory takes about 15 minutes. Every pair does agent mode this block, in a GitHub Codespace with GitHub Copilot Free. Warn them that the setup takes about 10 minutes, and that you'll walk around while they do it.
-->

---

<div class="eyebrow">Working with an agent</div>

# What's the difference between a chat and an agent?

| | Chat | Agent |
|---|---|---|
| **Input** | What you paste | Your whole workspace: it reads files itself |
| **Output** | Text you copy | Changes to your files |
| **Size of task** | One question | A whole job, in several steps |
| **Your role** | Read the answer | Approve the plan, check the changes |

<div class="footer">Block 2 · Today we use GitHub Copilot in Agent mode, in a Codespace. Rovo and M365 Copilot agents are built on the same idea.</div>

<!--
The main difference: an agent can do an entire job across lots of files. That's what makes it powerful, and it's also why you need to keep an eye on it. When a chat gets it wrong, you get a wrong answer to read. When an agent gets it wrong, it changes your files. Keep it concrete: the BD pair restructures the whole backlog in one go, the AC pair adds regulatory and extension stories across several files.
-->

---

<div class="eyebrow">Working with an agent</div>

# Plan, act, check, with you in between every step

<div class="flex gap-3 mt-6">
<div class="card accent flex-1">
<h3 style="color: var(--blue)">1 · Plan</h3>
<p>"Don't change anything yet. Tell me what you would change and why."</p>
<p class="font-semibold mt-2" style="color: var(--navy)">You: agree or correct</p>
</div>
<div class="arrow">→</div>
<div class="card accent flex-1">
<h3 style="color: var(--blue)">2 · Act</h3>
<p>"Execute it, one part at a time. Stop after each part."</p>
<p class="font-semibold mt-2" style="color: var(--navy)">You: watch, stop it early</p>
</div>
<div class="arrow">→</div>
<div class="card accent flex-1">
<h3 style="color: var(--blue)">3 · Check</h3>
<p>"List everything you changed." Then read the changes yourself.</p>
<p class="font-semibold mt-2" style="color: var(--navy)">You: verify, not trust</p>
</div>
</div>

<div class="footer">Block 2 · Today's rule: don't edit files by hand. Fix mistakes by giving the agent another instruction.</div>

<!--
Every Block 2 prompt ladder follows this structure. The plan is the cheapest place to catch a mistake: fixing a plan takes one sentence, cleaning up a messy edit takes a lot more. Explain why we don't allow editing by hand today: fixing things through the agent is how you find out where agents go wrong, and that's what this block is about. On a real project you'd obviously fix the small stuff yourself.
-->

---

<div class="eyebrow">Working with an agent</div>

# How do you know what the agent really did?

<div class="grid grid-cols-2 gap-8 mt-5">
<div>
<h3>Where to look</h3>
<p>The <b>Source Control</b> panel lists every file the agent touched. Click a file to see exactly what changed: old on the left, new on the right.</p>
<p class="mt-3">Don't rely on the agent's own summary of what it did. That's a claim like any other AI output.</p>
</div>
<div class="card">
<h3>What agents typically get wrong</h3>
<ul>
<li>Merge two stories that weren't the same</li>
<li>Break a reference by renumbering</li>
<li>Invent a source quote to fill a gap</li>
<li>Change meaning while "improving clarity"</li>
</ul>
</div>
</div>

<div class="footer">Block 2 · Put guardrails in your prompt, like "don't remove anything without asking" or "never invent a source"</div>

<!--
If you can, show the Source Control panel live in your own Codespace. It's the most useful thing in this block, and most analysts have never seen a diff before. The list on the right is what the pairs told us in Retro 2 of the first edition. Let them find these things themselves, but do tell them to look for them. Guardrails go in the prompt, and the ones they keep needing go in the instructions file.
-->

---

<div class="eyebrow">Working efficiently</div>

# Let's put the house rules in the project

<div class="grid grid-cols-2 gap-8 mt-5">
<div class="code-box">
<div class="file">.github/copilot-instructions.md</div>
You support a functional analysis team on the Meridian CMS engagement.<br>
Use only meridian-brief.md as source.<br>
Quote the source for every story.<br>
Label inferences as INFERRED.<br>
Never resolve a contradiction: add it to open-questions.md.<br>
Use the terms in glossary.md.
</div>
<div>
<p>Copilot reads this file before <b>every</b> request in the workspace. No need to repeat the rules in your prompts.</p>
<p class="mt-3">Does the agent keep breaking a rule? Then the rule probably isn't clear enough. Improve the file, not just your prompt.</p>
</div>
</div>

<div class="footer">Block 2 · Step 3 of the setup: paste your team's Block 1 instructions into this file</div>

<!--
The efficiency thread continues. This is just an example, they'll use their own file from Block 1. Point out that this file is shared: everyone who opens the workspace gets the same rules. That's how a team gets consistent AI output, instead of four people with four different habits. Retro 2 asks what they changed in the file, so tell them to keep track.
-->

---
layout: section
---

<div class="eyebrow">Block 3</div>

# Grounding & skills

We connect AI to the real source document, and turn what works into a skill.

<!--
The Block 3 theory takes about 15 minutes. This time both pairs connect to the MCP server, and both pairs build a skill in the last 25 minutes. The setup steps are at the top of their ladder: Claude.ai with a custom connector, or GitHub Copilot in their Codespace.
-->

---

<div class="eyebrow">Grounding</div>

# Trained on it, or reading it right now?

<div class="grid grid-cols-2 gap-5 mt-6">
<div class="card grey">
<div class="label">UNGROUNDED</div>
<h3>Answers from training</h3>
<p>Plausible, generic, confident. Can invent an article number that sounds exactly right.</p>
</div>
<div class="card accent">
<div class="label">GROUNDED</div>
<h3>Answers from the document</h3>
<p>Reads the real text at the moment you ask, and quotes the clause. You can check the quote.</p>
</div>
</div>

<div class="footer">Block 3 · In Prompt 1, you ask the same question without and with the connection</div>

<!--
Grounding just means you give the AI the source it should rely on at the moment it answers, instead of letting it answer from memory. Pasting a document is the simplest way to do that, and they've been doing it all morning with the brief. The general technique of fetching the right text and putting it in the context is called RAG (retrieval-augmented generation). MCP, on the next slide, is a standard way to hook up a tool to a source like that. Don't give away the fake citation in Block 4, but the line about made-up article numbers already plants the seed.
-->

---

<div class="eyebrow">Grounding</div>

# So what is MCP?

<div class="flex gap-3 mt-6">
<div class="card flex-1"><h3>Your AI tool</h3><p>Claude.ai or GitHub Copilot</p></div>
<div class="arrow">→</div>
<div class="card accent flex-1"><h3>MCP server</h3><p>Offers tools: list_documents, read_document</p></div>
<div class="arrow">→</div>
<div class="card flex-1"><h3>The source</h3><p>Meridian's regulatory standards</p></div>
</div>

The AI calls a tool, the server sends back the real text, and the AI answers based on that text. At a client, the source could just as well be their policy wiki, Jira, Confluence or a regulation database.

<div class="footer">Block 3 · Cheat sheet: ai-cheat-sheets/what-is-mcp-for-analysts.md</div>

<!--
MCP stands for Model Context Protocol. It's a standard, so one server works with lots of different AI tools, a bit like USB for AI. Our server is tiny on purpose: two tools, one document per track, read-only. Tell them what they'll see in the chat: the AI says it's calling read_document. That visible tool call is how you know the answer is based on the document. Mention the client side briefly too: hooking up AI to a client's sources raises questions about confidentiality, and that's the right reflex to have.
-->

---

<div class="eyebrow">Working efficiently</div>

# And what's a skill?

<div class="grid grid-cols-2 gap-8 mt-5">
<div class="code-box">
<div class="file">requirements-review/SKILL.md</div>
&#45;&#45;&#45;<br>
name: requirements-review<br>
description: Reviews user stories for traceability and testable acceptance criteria. Use when asked to review or check requirements.<br>
&#45;&#45;&#45;<br>
1. Quote the source sentence for every story...<br>
2. ...
</div>
<div>
<p>The AI always sees the <b>name and description</b> of every skill. Only when your request matches does it read the full instructions.</p>
<p class="mt-3">That's why the <b>description</b> matters so much: it decides whether your skill gets used.</p>
<p class="mt-3 text-sm">Claude.ai: zip the folder, upload under Customize → Skills.<br>GitHub Copilot: <code>.github/skills/&lt;name&gt;/SKILL.md</code></p>
</div>
</div>

<div class="footer">Block 3 · Last 25 minutes: each pair builds one skill, then the other pair tests it</div>

<!--
Skills answer the fourth piece of feedback from the first edition: "we want to learn how to work efficiently with AI, skills for example." A skill packages a task the way your team wants it done. The key idea is that it's only loaded when needed. The instructions file is read before every request, a skill only when it's relevant, so you can have dozens of them. Claude.ai needs "Code execution and file creation" switched on for skills (it's in the setup checklist). M365 Copilot has no skills, so pairs using it switch to Claude.ai or Copilot for this part. The real lesson is the swap: if the other pair's AI doesn't pick up your skill, your description isn't good enough yet.
-->

---

<div class="eyebrow">Working efficiently</div>

# Instructions, prompt or skill: which one do I use?

| Use | When | Today's example |
|-----|------|-----------------|
| **Instructions** | Rules for everything on this engagement | Your house rules from Block 1 |
| **Saved prompt** | A task you start yourself, the same way each time | "Interrogate the output" from Block 1 |
| **Skill** | A task the AI should recognise and do your way | regulatory-check, requirements-review |

None of these make the AI correct. They do make it more consistent, which makes checking a lot easier.

<div class="footer">Block 3 · In GitHub Copilot, a saved prompt is a .prompt.md file in .github/prompts/, started with /name</div>

<!--
Go through this one quickly, it's the overview they'll use after today. The warning at the bottom is important though: a skill that says "quote the source" makes it more likely that the AI quotes the source, it doesn't guarantee it. After this slide, send them to the setup at the top of their Block 3 ladder.
-->

---
class: dark
---

<div class="eyebrow">Wrap-up · Working efficiently</div>

# A few habits to take home

<div class="grid grid-cols-2 gap-x-10 gap-y-4 mt-5">
<p><b>New topic, new chat.</b> Bring only the source and the current state.</p>
<p><b>Attach, don't paste.</b> Less chance of text being cut off.</p>
<p><b>Source, not summary.</b> Your summary holds your assumptions.</p>
<p><b>Ask for the format you need.</b> Tables, Given/When/Then, Mermaid.</p>
<p><b>Store what works.</b> Good result: save the prompt. Bad result: add a rule.</p>
<p><b>Check two things, always.</b> A spot-check and the riskiest claim.</p>
</div>

<div class="footer">Wrap-up · Cheat sheet: ai-cheat-sheets/working-efficiently.md</div>

<!--
Use this during the wrap-up at 16:45, after the Block 4 debrief. Five habits about working efficiently, and the one habit about working carefully that we've been repeating all day. Don't read them out loud. Ask the room which one they would skip, and why.
-->

---

<div class="eyebrow">Wrap-up</div>

# How much should you check? That depends on the cost of being wrong

| Task | Cost of being wrong |
|------|---------------------|
| Drafting an internal email | Low |
| Summarising a public report | Low to medium |
| Writing a customer-facing message | Medium |
| Analysing data for a strategic decision | High |
| **Processing personal or legal data** | **Very high** |

<div class="footer">Wrap-up · Where did Sarah's three urgent requests sit on this table?</div>

<!--
We also use this table in the Block 4 debrief (see block4-facilitator-notes.md). If you already showed it there, just use this slide as a reminder: working efficiently doesn't mean checking less everywhere. It means you spend your checking where being wrong costs the most. All three of Sarah's requests were in the bottom row.
-->
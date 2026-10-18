## Block 3: Grounding and skills

**13:45-15:15** · 15 minutes of theory first, then 75 minutes to work. Pair AD and pair BC work in parallel.

Last rotation of the day! This block, both pairs are going to connect their AI to a real source document: Meridian's regulatory standards. We serve that document through an MCP server we host ourselves. Once that works, both pairs will take what they learned today and turn it into a skill: a set of instructions the AI only loads when it actually needs them.

What we want you to notice is the difference between an AI that answers from what it was trained on ("this is what energy regulation usually looks like") and an AI that reads Meridian's actual document and quotes it back to you.

---

### Setting up (both pairs, about 10 minutes)

Pick one of the two options below. Both work for everything we do in this block.

Option 1, Claude.ai in your browser (a free account is fine):
* Sign in at [claude.ai](https://claude.ai).
* Go to **Customize** → **Connectors** → **Add custom connector**. Call it `ai-track-standards` and paste this URL: `https://ai-track-ps-production.up.railway.app/mcp`. There's no login.
* Start a new chat, click **+** → **Connectors** and switch `ai-track-standards` on.
* For the skill at the end of the block, go to **Settings** → **Capabilities** and switch on **Code execution and file creation**. Skills don't work without it.

Option 2, GitHub Copilot in your Codespace from Block 2:
* Create a file called `.vscode/mcp.json` with the following content:

```json
{
  "servers": {
    "ai-track-standards": {
      "type": "http",
      "url": "https://ai-track-ps-production.up.railway.app/mcp"
    }
  }
}
```

* A small **Start** link appears above the server name in that file. Click it.
* In the chat panel (still in Agent mode), take a look at the tools list. You should see `list_documents` and `read_document` in there.

> Curious about what you're actually connecting to? `ai-cheat-sheets/what-is-mcp-for-analysts.md` explains it.

---

### Both pairs, Prompt 1: feel the difference

You're going to ask the same question twice: first in a chat without the connector, then in one with the connector.

```
What are Meridian Energy's rules for extending the internal 5-day resolution target, and
what happens if a team leader doesn't respond to an extension request?
```

When you ask it with the connector, add this line at the end: `Use the ai-track-standards server: call read_document with id "meridian-regulatory" and quote the relevant clause.`

* Without the connector, the AI has never seen Meridian's rules. Did it tell you that, or did it come up with something that sounds plausible?
* With the connector, ask your coach to show you `meridian-regulatory-standards.md` and look up the clause it quoted. Does it exist? Is it quoted correctly?

---

## Pair AD: auditing the backlog against the regulation

### Prompt 2: the audit

```
Using the ai-track-standards server (read_document, id "meridian-regulatory"), audit our
requirements backlog for violations of, or gaps against, the regulatory standards.

[paste your team's backlog and acceptance criteria]

For each finding: name the story, quote the clause it violates or misses, explain why it
matters, and propose corrected requirement language. Sort by severity: Critical, Major,
Minor.
```

* Take three findings and find the quoted clause in the document. Can't find a clause? Then the AI made it up. Write it down, it's great material for Retro 3.
* Look at §4 (no automatic closure) and §2.3 (5 days versus 8 weeks) in particular. Is there still anything in your backlog that those sections don't allow?

### Prompt 3: fix the critical findings

```
Rewrite the stories and acceptance criteria for every Critical finding. For each change,
add a note: what was wrong, and which clause it's based on.
```

* Paste the fixes into your team's shared document.

---

## Pair BC: reviewing the package for the steering committee

You're the senior analyst who reviews the package before the client gets to see it. The AI will find real issues, but it will also invent a few that aren't there. It's up to you to tell them apart.

### Prompt 2: traceability and regulation in one review

```
Review this requirements package before it goes to the client.

[paste your team's backlog, acceptance criteria and open questions]
[paste or attach meridian-brief.md]

1. Traceability: for every story, quote the sentence in the brief it comes from. Flag every
   story you can't trace as possibly invented.
2. Regulation: use the ai-track-standards server (read_document, id "meridian-regulatory")
   and check every regulatory obligation in it against the backlog: covered, partly covered,
   or missing. Quote the clause.
```

* The satisfaction survey and the dashboards each get one sentence in Sarah's email. Did they grow into big features that nobody actually asked for?
* Pick two of the "missing" findings and check them yourself. Are they really missing?

### Prompt 3: the pre-mortem

```
Act as a red team. Imagine it's one year from now: the system was built exactly from this
package and the project failed. Give 6 distinct reasons why: technical, organisational and
legal/regulatory. For each, point to the story or missing requirement that caused it, and
quote the source that shows the risk is knowable today, or say explicitly it's speculation.
```

* Sort the 6 reasons into three piles: real (there's a source behind it), speculative and invented. Chances are you'll have something in every pile.

### Prompt 4: the review document

```
Combine the review and the pre-mortem into one document for the steering committee:
- Summary (3 sentences)
- Critical issues (must fix before the checkpoint)
- Other issues
- What's done well (at least 3 things)
- Open questions that need a client decision
- Readiness: NOT READY / READY WITH CAVEATS / READY
```

* Do you agree with the readiness status it gave? You'll have to defend it during the showcase.

---

## Both pairs, the last 25 minutes: build a skill

You've written a lot of instructions for the same kind of check by now. A skill saves you that work. It's a folder with a `SKILL.md` file in it, which tells the AI how to do one specific task. The AI only reads the short description of each skill it has, and loads the full instructions when your request matches that description.

> How is this different from the instructions file you made this morning? That file is read before every request. A skill is only read when it's relevant. `ai-cheat-sheets/working-efficiently.md` explains it in a bit more detail.

Pair AD builds `regulatory-check`, a skill that checks any requirement against Meridian's regulation. Pair BC builds `requirements-review`, a skill that reviews stories for traceability and testability.

### Prompt 5: draft the skill

```
Write a skill file (SKILL.md) for the task we just did: [regulatory-check / requirements-review].

Format:
---
name: [the name, lowercase with hyphens]
description: [one or two sentences: what the skill does and when to use it]
---
[the instructions: the steps to follow, what to check, what sources to use, the exact
output format, and what never to do]

Base it on the prompts that worked best for us in this block: [paste them]. Keep it under
40 lines.
```

* Read what it wrote and edit it yourselves. Spend most of your time on the description: that's what the AI uses to decide whether to load your skill or not.

### Install it and swap

* Using Claude.ai? Put `SKILL.md` in a folder with the same name as the skill, zip that folder and upload it under **Customize** → **Skills** (the **+** button). Don't forget to switch it on.
* Using GitHub Copilot? Ask the agent to save it as `.github/skills/<skill-name>/SKILL.md`. Copilot picks it up by itself, and you can also start it with `/<skill-name>` in the chat.
* Now swap with the other pair in your group. Try their skill on one of your stories, in a new chat, without explaining what it does. Did the AI pick it up on its own? Did it do what the other pair had in mind? Give them one piece of feedback.

---

### Finished early? Wireframe the customer view

```
Sarah wants customers to see where their complaint is. Based on these stories:
[paste the relevant stories]
create a low-fidelity wireframe of the customer's complaint status page as a single HTML
file: grey boxes and plain text only. Below it, list everything on the page that is NOT
covered by the stories.
```

* Save it as `status-page.html` and open it in your browser.
* Check it against what IT told us: the current portal is being replaced, so the requirement can't depend on it. And what does a customer see while their complaint is "awaiting customer info"?

---

### Done?

Before Retro 3 at 15:15:

* Both pairs saw the difference between an answer with and without the connector
* Pair AD did the audit, fixed the Critical findings and wrote down any invented clauses
* Pair BC has a review document with a readiness status they can defend
* Both pairs have a working skill that the other pair tested

What you learned in this block:
* What grounding is, and why an answer from the real document beats an answer from training data
* What MCP is and how it connects an AI tool to a source
* How to check whether a quoted clause actually exists
* What a skill is, how it differs from instructions, and why the description matters so much

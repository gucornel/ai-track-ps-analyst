## Block 1: Prompting well

This morning is all about the basics. How do you give AI the right context, how do you get the format you actually need, and how do you make it tell you what it found in the brief versus what it simply guessed? You can use any AI chat tool you like for this block (check out `ai-cheat-sheets/copilot-chat.md` if you're not sure which one). No files, no setup, just a chat window.

One thing we want you to do after every single prompt: check two or three things by hand against the brief. Each prompt below tells you what to look at. We kept the brief short on purpose, so this takes you a couple of minutes, not an hour. If you skip it, you're not really testing the AI anymore, you're just trusting it.

* Create one shared place for your team's work (a Word document, a OneNote page, a Teams chat, whatever works for you) with four sections: backlog, glossary, decisions and open questions. We'll move all of this into files in Block 2.

---

## Pair AB: understanding the brief and writing user stories

### Prompt 1: understand before you build

* Paste the full Meridian brief into your chat (or attach the file) and send the following prompt:

```
I'm a functional analyst joining a requirements engagement for a Complaint Management
System. Here is all the source material we have:

[paste or attach meridian-brief.md]

1. Explain the domain to me in 10 lines, as if I'm a new analyst on the team.
2. List every contradiction or gap you find between the three documents. For each one,
   quote the conflicting statements and say who said what.

Use only what is in these documents. If you infer something that is not stated, label it
explicitly as an inference.
```

* Pick two of the contradictions it found and look up the quotes in the brief yourself. Are they quoted correctly? Did it attribute them to the right person?
* Look for the auto-close conflict between Sarah on one side and Marc and Priya on the other. Is it in the list? If the AI treats it as something that's already settled, you just found the biggest risk of the day.
* Discuss with your partner which of these you can decide yourselves (they go under decisions) and which ones need an answer from the client (they go under open questions).

### Prompt 2: the user story backlog

```
Based on this source material, propose a user story backlog for the Complaint Management
System, organised into epics. Use the format:

As a [role], I want to [action], so that [benefit].

For each story, add:
- Source: which document it comes from, with a short quote
- Stated or inferred: say explicitly which

Do not invent functionality that the source material doesn't support. If you think
something is missing, list it separately as a gap, not as a story.
```

* Pick three stories at random and find their quote in the brief. Can't find it? Then that story is a candidate for removal.
* Is there a story for regulatory complaints (Marc and Priya both talk about it)? And is there a story that closes complaints automatically? If so, who decided it should be in there, you or the AI?

### Prompt 3: acceptance criteria for the core flow

Don't try to do the whole backlog here, there's no time for that. Pick the stories for submission, acknowledgement and resolution.

```
Write acceptance criteria for these user stories:

[paste the stories]

Rules:
- Use Given/When/Then
- Every criterion must be testable: a tester can read it and know exactly how to verify it
- No vague language like "promptly" or "user-friendly"
- Use the exact numbers and timeframes from the source material
```

* Compare every timeframe with the brief. Acknowledgement is 2 working days, resolution is 5 working days (internal target) and 8 weeks (the regulation). Did the AI keep the 5 days and the 8 weeks apart, or did it mash them into one number?
* Take two criteria and explain to your partner how a tester would verify them. If you can't, rewrite them.

### Prompt 4: interrogate the output

This is the most important prompt of the block, so please don't skip it.

```
Review the backlog and acceptance criteria you generated against these facts from the
source material. For each fact, tell me whether it is covered, where exactly (which story),
and what a development team would build wrong if it were missing.

- Acknowledgement within 2 working days is a regulatory requirement
- Resolution has a 5-day internal target AND an 8-week regulatory obligation
- Regulatory complaints must be escalated to compliance within 2 working days
- All complaint records are retained for 5 years
- Auto-closing on customer non-response is rejected by both Marc and Priya
```

* For every fact the AI claims is covered, open the story it points to. Is it really in there?

### Got some time left? Prepare questions for the client

```
Here is our open-questions list: [paste it]

For each question, name the stakeholder who has to answer it (Sarah, Marc, Priya, or the
commercial team). Then write 1 open question, 2 to 3 probing questions and 1 closed question
to ask them. Do not suggest what the answer probably is.
```

> Keep an eye out for leading questions. "Would 7 days be acceptable for auto-close?" sounds harmless, but it already picks Sarah's side. Rewrite those into neutral questions.

---

## Pair CD: terminology, glossary and business rules

### Prompt 1: audit the terminology

```
Here is the source material for a Complaint Management System:

[paste or attach meridian-brief.md]

Audit the terminology:
1. Where do stakeholders use different words for the same thing?
2. Where does the same word mean different things to different people?
3. Which terms are used without ever being defined?

Quote the exact words and who used them. Use only what is in the documents.
```

* Look at the word "escalation". Sarah uses it for a missed 5-day deadline that goes to the team leader. Priya uses it for a regulatory complaint that goes to compliance. Those are two completely different things. Did the AI notice?

### Prompt 2: build the glossary

```
Based on the terminology audit, write a glossary. For each term: one precise definition,
the document(s) it comes from, and any conflicting usage you resolved and how.

Include at least: complaint, complaint category, complaints handler, team leader,
acknowledgement, resolution, escalation, extension, regulatory complaint, business customer.
```

* Pick three definitions and check them against the brief yourself.
* Share the glossary with pair AB as soon as it's more or less stable. Their stories should use the same words as your glossary.

### Prompt 3: extract the business rules

```
Extract every business rule from the source material. A business rule is something the
system must enforce: a timeframe, a condition, a mandatory step, a prohibition.

For each rule:
1. State it in one sentence
2. Quote the source and who said it
3. Flag any conflict with another rule

Do not resolve conflicts. Only surface them.
```

* Count the timeframes in the brief yourself (there are only a handful of them). Did the AI find all of them, with the right numbers?
* The auto-close rule should show up as a conflict, not as "the system closes complaints after 7 days". Is it flagged?

Hang on to this list, we'll need it again in Block 2.

### Prompt 4: a domain model diagram

```
Based on the source material and our glossary, propose a domain model as a Mermaid class
diagram. Include the main entities (complaint, category, handler, team leader, customer,
extension request, escalation), their key attributes and their relationships with
cardinality.
```

* Paste the result into [mermaid.live](https://mermaid.live). Does it render? AI-generated Mermaid often has a small syntax error somewhere. If it does, don't start fixing it yourself: paste the error back into the chat and let the AI fix it.
* Is a regulatory complaint something different from a standard complaint in the model, or is it just another value in a list?

---

## The last 15 minutes, with your whole team: write your house rules

By now you've probably typed "use only the source", "quote it" and "label inferences" about five times. That's annoying, and it's easy to forget one of them. So let's write them down once.

* Together with the other pair, write a short instructions file for this engagement (10 to 20 lines). Use the lines from your prompts that made the biggest difference. You can let the AI draft it, but do edit it yourselves afterwards:

```
Based on the prompts we used this morning [paste 2 or 3 of your best prompts], write a short
set of standing instructions for an AI assistant working on this requirements engagement.
Cover: our role, the output formats we use, how to handle the source material, how to
handle contradictions, and our glossary terms. Keep it under 20 lines.
```

* Save it in your team's shared document under a new section called instructions.
* Try it out. In M365 Copilot, paste it into Settings → Personalization → Custom instructions (or in the instructions of a Copilot Notebook). In Claude.ai, create a Project and paste it into the project instructions. Using GitHub Copilot? Hold on to it, that one comes in Block 2.
* Start a new chat and run one of your earlier prompts again, but this time without all the extra rules. Does the answer still follow them?

> Want to know what each tool supports exactly? Take a look at `ai-cheat-sheets/working-efficiently.md`.

---

### Done?

Before Retro 1 at 11:00, your team should have:

* An open-questions list with real entries in it, the auto-close conflict being one of them
* A first backlog, with a source quote for every story
* Acceptance criteria for the core flow, with the right timeframes
* A glossary with the 10 core terms, and a list of business rules with the conflicts flagged
* A domain model that renders in mermaid.live
* Your team's instructions file, which you tried at least once

What you learned in this block:
* How to build a prompt that gives AI the source, the task, the format and the rules it needs
* How to make AI quote its source and label its guesses, so you can actually check it
* How to spot-check AI output against the brief in a couple of minutes
* How to stop retyping the same rules by turning them into custom instructions

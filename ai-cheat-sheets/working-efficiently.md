## Working efficiently: instructions, prompt files and skills

Most of today is about using AI carefully. This sheet is about using it efficiently: not typing the same rules into every single chat, and turning the things that work into something you (and your team) can reuse.

### Why bother?

By lunchtime, you'll notice you keep writing the same lines over and over: "use only the source material", "quote it", "label inferences", "use our glossary terms". Forget one of them once, and the AI quietly falls back to guessing. Retyping them is slow, and it only works as long as you remember to do it.

There are three ways to store those rules. We'll go from simple to more powerful.

### 1. Custom instructions

Custom instructions are a short text the AI reads before every request you make. They're perfect for house rules: your role, the formats you use, how to treat the source material. Keep them short, 10 to 20 lines is plenty.

Where do you put them?
* M365 Copilot: open **...** (Settings and more) → **Chat settings** → **Personalization** → **Custom instructions**. These apply to all your chats. A Copilot Notebook also has its own instructions, which only apply to that notebook. That's handy if you want separate rules per project.
* Claude.ai: create a Project and fill in the project instructions. They apply to every chat inside that project.
* GitHub Copilot: a file in your repo, `.github/copilot-instructions.md`. It applies to every request in that workspace, for everyone who opens it.

> The GitHub Copilot one is the most interesting one for a team. The rules live inside the project, right next to the work, and everybody gets the same ones. That's what you'll do in Block 2.

### 2. Prompt files

A prompt file is a prompt you use a lot, saved so you can start it with a short command instead of typing it out again. In GitHub Copilot, that's a `.prompt.md` file in `.github/prompts/`. You start it by typing `/` followed by its name in the chat. Other tools don't have this, but a simple document with your best prompts (your prompt library) does the same job, with a bit more copy-pasting.

### 3. Skills

A skill is a folder with a `SKILL.md` file in it:

```
requirements-review/
└── SKILL.md
```

And this is what the file looks like:

```
---
name: requirements-review
description: Reviews user stories for traceability to the source material and testable
  acceptance criteria. Use when asked to review, check or quality-gate requirements.
---
1. For every story, find and quote the source sentence it comes from...
2. ...
```

The AI only reads the name and the description of each skill it has. When your request matches a description, it loads the full instructions of that skill. This means:
* You can have a lot of skills without them cluttering every chat
* The description decides whether your skill gets used, so make it say what the skill does and when to use it
* You can share a skill with your team, it's just a folder

How do you install one?
* Claude.ai (works on the free plan too): zip the skill folder and upload it under **Customize** → **Skills** (the **+** button), and switch it on. You can also simply ask Claude to write the skill for you.
* GitHub Copilot in VS Code or a Codespace: save it as `.github/skills/<skill-name>/SKILL.md` in your repo. Copilot picks it up when a request matches, or you start it yourself with `/<skill-name>`.
* M365 Copilot: no skills here. Use custom instructions or a Notebook instead.

### So which one do I use?

* Rules that should apply to everything you do on this engagement? Custom instructions.
* A task you start yourself, the same way every time? A prompt file, or your prompt library.
* A task the AI should recognise on its own and then do your way? A skill.

### A few habits that save you time

* Start a new chat when you switch topics. A long chat drags old context along, and the answers get worse. Only bring what's needed: the source and where you are right now.
* Attach files instead of pasting them. There's less chance of text getting cut off.
* Give the AI the source, not your summary of it. Your summary already contains your own assumptions.
* Ask for the format you need (a table, Given/When/Then, Mermaid), so you don't end up reformatting by hand.
* Keep what works. Good result? Save the prompt. Bad result? Add a line to your instructions so it doesn't happen again.

> One last warning: instructions and skills make AI faster, not more correct. A skill that says "quote the source" makes it more likely the AI quotes the source. It doesn't guarantee it. You still check.

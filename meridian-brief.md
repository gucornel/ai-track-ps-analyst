# Meridian Energy: Requirements Engagement Brief
**Client:** Meridian Energy (energy supplier, Belgium & Netherlands)
**Issued to:** Functional Analysis team
**Version:** 2.0

---

## The engagement

Meridian Energy is a mid-sized energy supplier. They handle several thousand customer
complaints per year. Today that happens in a shared spreadsheet and email threads, and they
have received two regulatory warnings in the past eighteen months for late handling and
insufficient documentation.

Meridian has asked Cegeka Professional Services to define the functional requirements for a
new Complaint Management System (CMS). A previous vendor was let go after producing a
requirements draft the compliance team rejected as "written from one stakeholder's opinion,
not the actual regulation." Your team is picking this up from scratch.

The engagement lead will walk Meridian's steering committee through a first-look review of
your work at 16:00: not a final sign-off, a checkpoint.

> **This brief is short on purpose.** Three documents, a few pages in total. You should be
> able to check any claim an AI makes about it against the source in a couple of minutes.
> Read all three before you start prompting. They don't agree with each other.

---

## What your team is producing today

- **A user story backlog** for the core complaint handling flows, with testable acceptance
  criteria and a traceability note per story (where in the source material it came from)
- **Two process diagrams** in Mermaid: the main complaint flow, and one exception flow
- **A glossary** that resolves inconsistent terminology
- **An open-questions log**: every contradiction you found but did not resolve yourselves,
  and every decision the source material did not answer
- **A reusable instructions file and a skill** that capture how your team wants AI to work
  on this engagement (you'll build these up during the day)

---

## Source material

### Document 1: Project initiation email from Sarah Belmans, Head of Customer Operations

> Hi,
>
> Here is a summary of what we need, following our call.
>
> We want a proper system to manage customer complaints end to end. A customer submits a
> complaint (phone, email, web), it gets logged, a **complaints handler** picks it up,
> investigates and resolves it. **Team leaders** oversee the handlers and can reassign
> complaints between them. We want to track all of that, customers should be able to see
> where their complaint is, and management wants dashboards.
>
> Complaint types: billing, supply interruptions, contract disputes and general service
> complaints. They all go through the same process basically, some just take longer.
>
> The most important thing for us is the **5-working-day resolution target**. The system
> needs to enforce it: reminders to handlers when they approach the deadline, escalation to
> the team leader if they miss it.
>
> One thing I want specifically: if a customer does not respond to our requests for
> information within 7 days, the complaint should **close automatically**. We spend too much
> time chasing people. They can resubmit if they want.
>
> A simple satisfaction survey after resolution would be nice too (did we resolve your
> complaint, yes or no, any comments).
>
> Business customers usually go through their account manager first. I am not sure how that
> works exactly, so that is probably out of scope for now.
>
> Sarah

---

### Document 2: Interview notes, Marc Devos, Senior Complaints Handler

*30 minutes, on site. Marc has handled complaints at Meridian for six years. Paraphrased notes.*

On the current process: "We log the complaint in the spreadsheet and send the customer an
acknowledgement within two working days. Then we investigate. If we need more info from the
customer, we send a request and wait. If we need another department, billing or network, we
send them an internal request and wait. Then we write up the resolution and close it."

On the acknowledgement: "The two-working-day acknowledgement is a regulatory requirement, not
just our policy. The system needs to flag it immediately if one has not gone out in time."

On the 5-day target: "Five days is not realistic for anything involving another department.
Those requests can take two weeks. We ask the team leader for an extension, with a reason,
and they approve it. That happens in about thirty percent of the cases. The system needs to
support that."

On auto-closing: "We cannot auto-close complaints. Full stop. We got a fine from the
regulator two years ago partly because of something like that. If a customer does not
respond, we send a reminder, then a second reminder, then a letter saying we will close in
14 days unless we hear from them. Only then can we close, and even then it is a manual
sign-off."

On categories: "There is a fourth category Sarah probably did not mention: **regulatory
complaints**. The customer has already been to the regulator, or says they will. Those have
completely different handling rules."

---

### Document 3: Interview notes, Priya Nair, Compliance Officer

*20 minutes, by phone. Priya joined late and had limited time. Paraphrased notes.*

On timeframes: "The five-day target is internal. The regulation is different. We must
acknowledge within two working days, Marc is right about that. For resolution, we must make
reasonable efforts to resolve within **eight weeks**. If we can't, we must write to the
customer explaining why and what their options are, including going to the ombudsman."

On regulatory complaints: "If a customer mentions the energy ombudsman or a regulator, the
complaint is a regulatory complaint and must be escalated to my team within **two working
days**. Not five. I manage those personally."

On auto-closing: "I agree with Marc. Auto-closing is not acceptable from a compliance
standpoint."

On data retention: "Every complaint record must be kept for **five years**: every
communication, every internal note, every status change. If the system deletes anything
earlier, I will block the go-live."

On business customers: "Business customers above a certain contract value have their own
escalation path. I don't know the threshold, you'd have to ask the commercial team. But it is
not out of scope. If we leave it out now, we'll have to retrofit it later."

---

## Constraints from IT (Tom Geerts, IT Manager)

- Customer data lives in Salesforce. The CMS must look customers up there, not keep a second
  customer database.
- The customer portal is being replaced in about 14 months. Don't build customer-facing
  functionality on the current portal: design it so it can move to the new one.

## Out of scope for today

- Authentication (Meridian's existing SSO handles login)
- Detailed Salesforce field mapping
- Visual or UI design
- The content of the satisfaction survey (note it as a story, don't design it)

---

## Definition of done for today

You will not produce a complete requirements package. The goal is a package you can defend.
At the showcase, each team presents:

1. **Three user stories, walked through in full**: for each, point to the sentence in the
   source material it came from, and name one thing AI produced that you had to correct.
2. **One process diagram**: name one flow or exception that was missing from what AI first
   generated.
3. **Your top three open questions**: the things that would block a development team if
   left silent.

*From the steering committee, at the engagement kickoff:*
> "We don't need you to have all the answers today. We need to trust that you know which
> questions you haven't answered yet. The last vendor didn't."

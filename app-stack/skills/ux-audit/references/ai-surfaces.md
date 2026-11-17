# Auditing an AI feature

Read this when the product has an AI feature a person sees: a chat, a suggestion, a summary, an autofill, an agent that acts. The question is behaviour, not decoration: when the system acts, when it waits, how it shows confidence, what happens when it is wrong, and how it earns more autonomy. The patterns below are drawn from a UX agency's published guide to AI patterns (read `2026-11-17`); the audit questions are this collection's.

## Scale autonomy to the cost of a mistake

| Risk of a wrong action | Autonomy | The audit checks |
|---|---|---|
| Low: formatting, a draft, a sort | The AI acts; the person can see and undo | Undo exists and is visible |
| Medium: a record's contents, a message | The AI suggests; the person approves | Approval is one clear step, with the change shown |
| High: a medication, a payment, a deletion, a disclosure | The AI informs; the person decides | The AI never acts alone, and who decided is recorded |

- **Start supportive and let autonomy grow with trust.** Too much autonomy too fast is the first reason an AI feature is abandoned.
- **A person stays accountable for a high-stakes outcome,** and the screen says so.

## The audit questions

Walk the feature once per pattern that applies. Each pattern is a question; a "no" is a finding with a severity.

1. **Can the person shape the result, not just accept or reject it?** Refine by selecting text or choosing length, tone or detail, without a full re-run.
2. **Is AI output distinguished from verified data?** A badge, an icon or a label, applied the same way everywhere. Without it, people re-check everything, and the time saved is gone. A confidence signal must be graduated and understandable, never a bare number.
3. **Can the person scope the request?** Time frame, record set or domain, so the answer is the one asked for and not everything.
4. **Do presets and templates show what the AI can do?** They are findable, editable and not stale.
5. **Can tone and detail be set for the reader?** The same content for a physician and for a patient leaflet, with a live preview of the effect.
6. **Are alternatives offered where the decision has options?** A single recommendation does not match how a clinician or a buyer weighs options. Show the likely consequence of each.
7. **Can the person see the reasoning, in layers?** A short summary first, then the data behind it. **A reason must be specific**: "the creatinine trend over the last three results" invites checking; "based on history" invites blind trust. A poor explanation can reduce a person's error detection, so test that the reasoning is tied to the actual output.
8. **Is feedback visible?** A correction that visibly changes later results is given again; one that vanishes is not. The screen says how feedback is used.
9. **Are proactive suggestions calibrated?** They arrive at a good moment, are easy to dismiss, say why they appeared, and are wrong rarely enough not to erode trust. Count them per session; low-value ones are alert fatigue.
10. **Does context carry over, and can the person see and clear it?** Stale or wrong memory must be removable.
11. **Are data controls findable and truthful?** Access, opt in and out, export and delete, in plain words, matching what the system does. Check tooltips and prompts for what private data they display.
12. **Is every AI action recoverable?** Undo, version history, a manual override, and an error that says what happened and what to do. An irreversible commit before the person can verify is a 4.
13. **Is there a designed failure state for each way it fails?** Expect many: no data, conflicting data, a timeout, a low-confidence answer, a refusal, a downstream system down. Each needs a plain explanation and a path forward. An honest "I need these two things to answer" earns more trust than a confident answer on thin data.

## Two guards in the interface

- **No unreviewed generated content reaches a patient, a customer record or a legal document.** A human step sits between them, and the audit finds where it can be skipped.
- **Say what is sent where.** A person who cannot see the data handling will not trust it, and a buyer who cannot see it will stall procurement.

## Other stakeholders

- A clinician needs interrogable reasoning and a layout that fits an existing workflow; a nurse needs data-entry support; a patient needs reassurance and plain words; an administrator needs an audit trail. An AI feature designed for one of them and ignored by the rest is not adopted.

## Four mistakes that kill adoption

1. Too much autonomy too fast.
2. No explanation of reasoning, or one that makes people stop thinking.
3. All or nothing: no way to modify the output.
4. Ignored failure states.

## Judging it after launch

- **Track in seven areas:** accuracy, including edge cases; fairness across user groups; usability; trust (adoption, acceptance, override rates); safety and risk; feedback loops; and operations such as latency and cost. A high override rate is a design signal, not only a model one.
- **Set direction, not a false target.** Whether 95 percent accuracy is enough depends on the cost of the error.
- **Test with the right methods:** a workflow prototype, a person standing in for the AI, deliberate failures, and autonomy at each level, in `/app-stack:usability-test`.
- **For building the surface,** the product's embedded-agent skills (`embedded-agents-agent-sdk`, `embedded-agents-messages-api`) hold how it is wired.

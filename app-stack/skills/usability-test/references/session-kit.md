# Session kit

Templates and numbers for `usability-test`. Edit each to the product; the structure is what matters. A published usability-testing guide for healthcare products (read `2026-11-17`) is the source for the session length, the edge cases and the pitfalls; the numbers and the SUS method are standard practice.

## Recruiting and numbers

- **Test each role separately.** Five or so participants per distinct role finds most of the problems a task has; a different role is a different test. More participants add little to finding problems and a lot to cost. Run small rounds, fix, then run another.
- **Use more people only for a number you need to trust.** A task success rate or a time you will compare over releases needs a larger group, usually 20 or more per role. State the group's size next to every figure.
- **Screener questions:** the person's role and tenure, how often they use the kind of product, comfort with digital tools on a short scale, whether they use assistive technology, and device and setting. Never ask for a diagnosis or a patient detail.
- **Reach people through someone they trust:** a practice manager, a research coordinator or a patient advocacy group.
- **Standing in for patients.** Have a clinician or staff member act out a patient interaction on a dummy profile, rather than involve a real patient, unless the test is built for patients with the protections research requires.
- **Offer a way in for everyone:** extra time, an assistive tool, a remote or asynchronous session, and a quiet time of day.

## The recruiting message

> We are improving [product], a tool for [role]. We would like 25 minutes of your time to watch you try a few everyday tasks and hear what works and what does not. We are testing the product, not you. There are no right answers. We will not record anything that identifies you or a patient, and you can stop at any time. [Compensation, if any.] Reply to [name] to choose a time, in person or by video.

## The session script

1. **Welcome (2 minutes).** "Thank you. We are testing the product, not you. If something is confusing, that is useful. Please think aloud, say what you expect and what surprises you. I cannot help during the tasks, but I will answer questions afterwards. You can stop at any time."
2. **Consent.** Read the consent text below. Ask permission to record the screen and voice.
3. **Background (2 minutes).** Two or three questions from the screener, asked casually.
4. **Tasks (15 to 20 minutes).** Read each scenario aloud and hand it over in writing. Say nothing about how to do it. Note the time it begins and ends, the path, the errors and any help asked for. Stop a task at a set time and mark it incomplete.
5. **Probing (3 minutes per theme).** "What were you expecting on that screen?" "How would this fit into your day?" "What would you do next?" "What did you do to get around that?"
6. **Close (2 minutes).** The single ease question and the SUS questions, if used. Thank the person.

**Scenario template:** "You are [a role in a situation]. You need to [goal]. Show me how you would do it." Include the context and the goal; leave out the labels the product uses.

## Consent text

> I understand that this session will be recorded on screen and by voice so the team can study it. The recording will be used only to improve [product], will be kept for [period], and will be seen by [who]. My name and any patient or personal details will not be kept with it. I may stop at any time, with no consequence. I agree to take part. Signed / spoken: ____ Date: ____

Have the owner and, where required, a privacy or ethics reviewer approve this text. It is a first draft, not a legal document.

## The note sheet

One row per task per participant: participant code (never a name), role, task, start and end time, completed (yes, partly, no), errors, path, help asked, workarounds, quotes, and the observation codes below.

## Coding observations

Tag each observation so patterns are countable:

- **P**: a place where they paused or hesitated for more than a few seconds.
- **E**: an error, including a wrong tap or a wrong value.
- **R**: a recovery, with how they did it.
- **W**: a workaround that bypasses the product.
- **H**: help asked for or a hint given.
- **Q**: a quote, word for word.
- **S**: something that went well, which the fixes must not break.

Group observations by task and screen. A problem seen in two or more sessions is a pattern; a problem seen once is a lead.

## The measures

- **Task success.** Completed unaided, completed with difficulty, failed. Report each count.
- **Time on task.** For completed tasks only. Report the median and the range; a mean is distorted by one long session.
- **Errors per task.** Count and type, with the severity of the worst.
- **Single ease question.** After each task: "Overall, how easy or difficult was this task?" on a seven-point scale.
- **Cognitive load.** Ask what felt heavy; a short interview beats a score for a small group.
- **Readability of patient-facing text.** A score by the same tool each time.

## The System Usability Scale

Ten statements, each rated 1 (strongly disagree) to 5 (strongly agree):

1. I think that I would like to use this system frequently.
2. I found the system unnecessarily complex.
3. I thought the system was easy to use.
4. I think that I would need the support of a technical person to use this system.
5. I found the various functions in this system were well integrated.
6. I thought there was too much inconsistency in this system.
7. I would imagine that most people would learn to use this system very quickly.
8. I found the system very cumbersome to use.
9. I felt very confident using the system.
10. I needed to learn a lot of things before I could get going with this system.

**Scoring.** For odd items, the score is the response minus 1. For even items, it is 5 minus the response. Add the ten scores and multiply by 2.5, giving 0 to 100 per participant. Report the mean. A score near 68 is average across products; read it as a rough benchmark and compare it only with the same product's earlier rounds. The scale tells you how the product feels overall, not what to fix, so it never replaces the task findings.

## Severity and reporting

Rate each problem with the scale in `ux-audit`'s `references/heuristics.md`, with the same rule: cost of the mistake beats frequency. A report opens with the key findings and their severity, then each real pain point with a quote or a clip, the proposed fix, and the cost of leaving it, in time, errors, support load or risk. Claim a figure only when the sessions or the product's data back it.

## Follow-up

- **A/B test a fix** only where traffic supports it, and change one major element at a time.
- **Retest in one to two months** to confirm the fixes work, and again at six to twelve months to see the gain hold.
- **Keep a feedback route open:** in-product feedback, regular user check-ins, support ticket themes and an advisory panel of users.

## The pitfalls to check the plan against

- Testing as an afterthought, with no decision behind it.
- Relying on general principles in place of testing the domain's real tasks.
- Oversimplified test data that hides the real complexity.
- Testing only in a quiet lab.
- Leading questions and "do you like it" prompts.
- A developer moderating.
- Missing the workarounds.
- Sessions long enough to be rushed.
- Skipping the test because logistics are hard.
- No follow-up after launch.

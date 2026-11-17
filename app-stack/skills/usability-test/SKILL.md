---
name: usability-test
description: "Plan and analyze a usability test with real people. Drafts the plan, tasks, script, consent and recruiting message for the top jobs, then turns session notes or recordings into severity-ranked findings and the numbers (task success, time, errors, SUS). Started by name only: /app-stack:usability-test in Claude Code, $app-stack:usability-test in Codex."
argument-hint: "<the product or flow, the roles to test, and any session notes or recordings to analyze>"
disable-model-invocation: true
---

# Usability test

**An agent plans the test and reads the results; people take it.** Watching a real person try a real job is the only thing that settles what an expert review (`/app-stack:ux-audit`, Codex: `$app-stack:ux-audit`) can only guess. This skill drafts everything around those sessions and refuses to invent what they would show.

**Run this pass only when the user starts it.** It produces documents for the owner and, later, a findings report. It never contacts a participant and never runs a session on its own.

## The procedure

1. **Set the objective and the measures first.** Write one sentence: what decision does this test inform? Pick two or three measurable goals tied to the product's outcome, such as "a new patient books a visit unaided in under three minutes". A test with no decision behind it is a fishing trip.
2. **Choose roles and recruit per role.** Test each distinct role separately; a clinician, an administrator and a patient need their own sessions. Draft a short screener, comfort with digital tools included, and the recruiting message. Use `references/session-kit.md`, § Recruiting and numbers. Name an intermediary who can reach them, such as a practice manager, a research coordinator or an advocacy group.
3. **Write the tasks from the jobs map.** One scenario per job in the user's words, with a goal and no hint of the path. Add the edge cases from `ux-audit`'s `references/healthcare.md` that matter: overlapping conditions, a duplicate record, an interruption, a restricted record.
4. **Prepare the environment and the data.** Use a sandbox with realistic fake data. Never use real patient, member or customer data in a session. Prefer the person's own device and workplace over a lab; a lab gives false confidence by removing noise and interruption.
5. **Write the script, consent and the note sheet.** Templates are in `references/session-kit.md`. Sessions run 20 to 30 minutes on a few key workflows. Schedule away from peak hours, such as shift changes and end of day, and offer remote or asynchronous sessions.
6. **Hand off to the owner and a neutral moderator.** The moderator is someone with no stake in the design, so a developer never moderates. The owner approves the plan, the consent text and the recruiting message before anything goes out.
7. **Analyze what comes back.** Read the notes or recordings the owner provides. Tag each observation with the task, the role and a code from `references/session-kit.md`, § Coding observations. Compute the measures, rate each problem with `ux-audit`'s severity scale, and write the report in its order. Quote the person, not the paraphrase.
8. **Close the loop.** Fix the findings by severity and impact against effort. Retest the fixed tasks briefly, a month or two later, and again at six to twelve months to see whether the gains hold.

## Rules that keep the test honest

- **Let people try unaided.** The moderator speaks only to start, to keep going and to probe afterwards. Do not rescue, hint or explain.
- **Ask neutral questions.** "How would this fit your workflow?" gets an answer; "Do you like this feature?" gets politeness.
- **Watch what people do over what they say.** The unofficial shortcut a clinician has built reveals the real pain point.
- **Test the path with its real mess:** interruptions, a slow connection, a colleague at the door. If a participant leaves the task to answer someone, note where they came back.
- **Keep sessions short.** A long session gets rushed or abandoned by a busy clinician.
- **Do not skip testing for logistics.** A remote or asynchronous test is better than none.
- **Never present a number the sessions did not produce.** With five participants, report counts ("4 of 5 failed") and not percentages dressed as findings.
- **Protect participants.** Consent says what is recorded, how it is used, and that they may stop at any time. Strip names, record numbers and any voice or video that could identify a person from what is stored. When a test touches patients as research, ask whether an institutional review is needed, and flag it to the owner at once.

## What this skill will not do

- **Invent participants, sessions or quotes.** Where the owner has no recordings, the report is a plan, and says so.
- **Settle legal or ethics questions.** HIPAA, GDPR and review-board duties go to a qualified reviewer; the plan flags the points and does not rule on them.
- **Replace the audit.** An expert review and a user test find different problems; run the audit first so the sessions are spent on what only people can show.

## How you can tell it worked

The plan states the decision it informs, a task for each job and role, and the measure for each. Every finding in the report traces to a named session and a quote or clip, and every number can be recomputed from the notes. The owner could run the sessions from the plan without asking the agent a question.

## Files

| File | Holds | Read when |
|---|---|---|
| `references/session-kit.md` | recruiting and numbers, the script, consent, the note sheet, observation codes, the measures and SUS | steps 2 to 7 |

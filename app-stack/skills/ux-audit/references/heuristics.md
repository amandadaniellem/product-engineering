# Heuristics, severity and ranking

Read this while walking the jobs and rating findings. The ten heuristics are Nielsen's, used as questions an auditor can answer from a capture. A heuristic points at a place to look; it is not a finding until the evidence shows a person stuck there.

## The ten heuristics, as questions

1. **Visibility of system status.** After every action, can the person tell what happened and what is happening now? Look for saves with no confirmation, long waits with no progress, and a processing state that does not say how long. A state word and a state colour must agree on every screen that mentions the same fact.
2. **Match with the real world.** Does the screen use the person's words, not the system's? Look for table names, status codes and internal jargon in labels. A clinician reads "No active orders"; "No data" tells nobody what is missing.
3. **User control and freedom.** Is there a clear way out, back or undo? Look for dialogs with no close, wizards with no back, and a destructive action with no undo or confirm. A shown-once secret needs a warning before it closes.
4. **Consistency and standards.** Does the same thing look and behave the same everywhere? Look for two button styles for one role, a second name for one object, and a control that works differently on phone and desktop.
5. **Error prevention.** Does the design stop the mistake, before it needs a message? Look for free text where a pick list would do, a default that is a guess, a destructive action beside a common one, and a form that accepts an impossible value.
6. **Recognition rather than recall.** Can the person see what they need, not remember it? Look for an identifier on one screen that must be typed on the next, filters that reset on navigation, and a value shown only in a tooltip.
7. **Flexibility and efficiency of use.** Does the expert path get shorter with use? Look for no keyboard path, no bulk action on a list used all day, and a three-step task done a hundred times a shift.
8. **Aesthetic and minimalist design.** Does every element earn its place? Look for equal weight on every feature, which hides the one that matters. The audit treats this as a hierarchy question: is the primary action for each persona the easiest to find?
9. **Help people recognize, diagnose and recover from errors.** Does the message say what went wrong in plain words and what to do next? Look for "Something went wrong", a code with no meaning, and an error that clears the form.
10. **Help and documentation.** Is help where the question arises, short and searchable? Look for onboarding that needs its own course, and a help link that leaves the task. A product that needs a training university for a basic job has a design problem, not a training one.

## Two lenses to add to every walk

- **Role fit.** Does each role get the detail it needs and no more? A screen built for one role and shown to all is a finding for the others. Look for the administrator's view that hides what an auditor needs, and the patient's view in a clinician's vocabulary.
- **Interruption.** Can someone leave mid-task and come back? Phones ring, shifts change and tabs close. Look for lost drafts, a session that times out with no warning, and no way to resume.

## Severity

Rate each finding 0 to 4. The scale is Nielsen's; the three factors are how often it occurs, how many people it hits, and whether people can get past it once they know.

| Rating | Meaning | Healthcare reading |
|---|---|---|
| 0 | Not a problem | |
| 1 | Cosmetic. Fix if time allows | A label a little off |
| 2 | Minor. Slows people down; low priority | An extra click on a rare task |
| 3 | Major. Stops or misleads many people; fix before release | A workflow breaks or loses work |
| 4 | Catastrophic. Fix now | A person could act on wrong information or lose a record |

**Cost beats frequency.** Raise any finding to 4 when a plausible slip causes harm that cannot be undone: a wrong patient or record, a wrong dose or amount, silent data loss, or exposure of private data. Raise it to at least 3 when it blocks a user group from a core job, as a keyboard trap does for someone who cannot use a mouse.

## Ranking the fix list

1. Rank by severity first.
2. Within a severity, rank by **impact on a core job, against the effort to fix.** The report puts a high-impact, low-effort fix in its quick wins, so the owner sees an early win. Ship those first.
3. Group findings that share one cause. Ten missing labels are one finding with ten places, and one shared component usually fixes them.
4. Give a business reading only when the owner asked for one: time lost, errors, support load or compliance risk. Claim a cost only when a number backs it.

## Sample size does not apply here

An expert audit has no sample size. One careful auditor finds a large share of what a heuristic review can find, and a second, independent auditor finds more. Run a second reviewer, in a fresh session, when the product handles anything with real-world harm.

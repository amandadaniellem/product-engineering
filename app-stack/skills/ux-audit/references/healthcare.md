# Healthcare and other regulated products

Read this when the product handles care, claims, health records or any record where a wrong action has a real cost. The same shape works for finance, legal and safety products: swap the roles and the data rules. Nothing here is legal advice; each compliance point is a flag for the owner to take to a qualified reviewer.

## Two traps a healthcare audit looks for

- **Oversimplifying.** A consumer pattern applied to a product with many features and several user groups hides what the expert needs. A clinician needs the whole picture; a patient needs one next step.
- **Overcomplicating.** Every feature given equal weight, with no hierarchy for a persona's journey. The audit asks, for each role, which one action is easiest to find, and whether it is the right one.

## Roles

- **Segment every finding by role.** Typical roles are clinician, nurse, administrative staff, payer or insurer, and patient or caregiver. They differ in time, vocabulary and comfort with digital tools.
- **A screen has one primary reader.** If two roles share a screen, the finding says which one loses.
- **Clinicians work under interruption.** A task must be resumable, a patient's context must be unmistakable, and a slip must be easy to see and undo.
- **Administrators need the audit trail.** A change with no record of who made it is a finding for them.

## The cost of a mistake

Rate against what a slip causes, not how often it occurs (`heuristics.md`, § Severity). Walk these edge cases on every core job; a clean demo path hides them.

- A patient with several chronic conditions and overlapping medications.
- Two records that look alike, or a duplicate that needs merging. Is the patient's identity unmistakable on every screen that can change something?
- A task interrupted and resumed an hour later.
- A value out of range, a unit that can be misread, or a date format that differs by region.
- A restricted record opened in an emergency. Is there a route, and is it logged?

## Empty states

**Every empty state says what is missing, why, and what to do next.** In care, an empty list can read as "nothing needed" or as "nothing loaded", and the two lead to different actions. List every screen that can legitimately show no data, then check each against its cause:

| Cause | What the state does | Failure to flag |
|---|---|---|
| First use | Says the emptiness is expected, what will appear, and what starts it | A blank page that looks broken |
| Work completed | Confirms success and that nothing urgent is left | An empty list that cannot be told apart from a failed load |
| Search found nothing | Says why, and suggests another query, a spelling or a filter to loosen | "No results" with no way forward |
| Access restricted | Says that access is limited, protects the content, and shows how to request or escalate | A dead end, or a message that reveals what is hidden |
| Still processing | Says the system is working, gives a realistic time, and shows the previous result if one exists | A spinner with no time, or a blank that reads as no result |

- **Header in the user's terms.** "No active orders", not "No data".
- **Keep the state from creating doubt about a patient's status.** Where emptiness could be mistaken for good news or bad, say which it is.
- **Reveal nothing private in the message.** Detail that confirms a sensitive record exists is a leak.
- **Tailor detail to the role.** A patient and a nurse need different words for the same state.
- **Prioritize by safety.** Fix the empty states that touch patient safety or stall a workflow first.

## Alerts and warnings

- **Alert fatigue is a defect.** Frequent low-value alerts train people to dismiss all of them, the critical ones included. Count the alerts on a core job; each needs a reason to interrupt.
- **Rank by severity and make dismissal cheap but logged.** A reviewer sees what was dismissed and by whom.
- **Never let a background process change a high-stakes setting silently,** such as an alert threshold or a medication rule.

## Data on screen

- **Fake data in every capture, test and demo.** A real name, record number or claim in a screenshot or recording is an incident. Flag it at once; the product's agent instructions should say who handles it.
- **Check what each surface reveals:** tooltips, URLs, page titles, error messages, notifications, exports and logs. A name in a URL or a diagnosis in a push notification is a finding.
- **Show who and when.** Data that may be stale says its source and age.
- **Compliance flags for the owner,** not for the audit to decide: HIPAA's effect on what may display, where it is stored and who may see it; FDA human-factors expectations for tools that support a clinical decision; and, for AI features sold in the EU, the AI Act's high-risk transparency duties.

## Text meant for patients

- **Use plain language and measure it.** Run a readability score on patient-facing text; a common target is a sixth to eighth grade reading level.
- **Define a medical term on first use,** and prefer the word a patient uses.
- **Pair an instruction with its reason,** and say what to do if it fails.
- **Do not send unreviewed generated text** to a patient or into a record (`ai-surfaces.md`).

## Where the product reaches the home

- Smart-home and wearable surfaces reach people with limited vision, dexterity or tech comfort, so the accessibility pass applies there first. A reminder that needs a screen read to be understood fails the person who most needs it.
- A caregiver is a user. Check the flow as the caregiver, with their limited view of the record.

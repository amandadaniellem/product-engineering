---
name: ux-audit
description: "Can people finish their jobs in this product, safely and accessibly? An expert review of a built product's screens against usability heuristics, WCAG 2.2 AA and the domain's risks (healthcare especially, AI features included), with severity-ranked findings and a prioritized fix list. Started by name only: /app-stack:ux-audit in Claude Code, $app-stack:ux-audit in Codex."
argument-hint: "<product URL, route list or repo path; name the user roles and the domain>"
disable-model-invocation: true
---

# UX audit

**Audit whether people can finish their jobs, not whether the screens look good.** The `ui-design` skill judges the look with its owner; this audit judges task success, accessibility and the cost of a mistake. A product can pass the first and fail the second.

**Run this pass only when the user starts it.** It spends a long session and ends in a report the owner decides from. It is an expert review, so it finds what an expert can see. It cannot replace watching real people; for that, type `/app-stack:usability-test` (Codex: `$app-stack:usability-test`).

## The procedure

1. **Scope the audit to jobs and roles.** Use the product's jobs map (`ui-design`, § Before any screen) or build one: one row per job in the user's words, its screen, and its primary action. List the roles, because each role is a different user. In healthcare that means clinician, administrator, payer and patient or caregiver, each with different time pressure and digital comfort. Ask the owner only for the roles, the three jobs that matter most, and any known complaints or metrics.
2. **Capture evidence before judging.** Crawl every route as every role at 1280 and 390 wide, in light and dark, with fake data only. Capture the empty, loading, error, restricted and in-progress state of each screen, not only the healthy one. Real patient or customer data never enters a capture (`references/healthcare.md`, § Data on screen).
3. **Walk each job as each role.** For each screen on the path, apply the ten heuristics in `references/heuristics.md`. Write down every place a person would stop, guess, retry or give up. A walk that finds nothing on a screen the owner called confusing is a walk that skipped a state.
4. **Run the accessibility pass.** Follow `references/accessibility.md`: automated scan first, then the manual checks a scan cannot do. A scan catches only a fraction of real problems, so a clean scan is the start of the pass.
5. **Audit the states and the surfaces that carry risk.** Check every empty state against `references/healthcare.md`. If the product has an AI feature, check it against `references/ai-surfaces.md`. Skip a reference only when the product has nothing it covers, and say so in the report.
6. **Rate every finding.** Use the severity scale in `references/heuristics.md`, then rank by impact against the effort to fix. **Severity follows the cost of the mistake, not how often it happens.** A rare path that can send the wrong record, dose or payment is a 4.
7. **Write the report** in the order `references/report.md` gives: the verdict, the jobs that fail, the findings, quick wins, and what was not checked.
8. **Hold the fixes with tests where a test can be written.** A contrast floor, a focus order, a keyboard path and a missing-label scan all can. Send a lesson true for any product to this collection through `/agent-harness:retro` (Codex: `$agent-harness:retro`).
9. **Re-audit the 3s and 4s after the fixes.** A fix is closed when the same walk, as the same role, no longer fails. Run the whole audit again before a release that changes a flow, and at least once a year.

## Rules that keep the audit honest

- **No finding without evidence.** Each cites a screenshot, a route and role, or a `file:line`. Tag it *observed* (reproduced in a capture) or *inferred* (read from code or a pattern). An inferred finding says what would confirm it.
- **Observe people, then personas.** Where the owner has session recordings, support tickets or analytics (`product-analytics`), read them before the heuristics. A persona never overrides what a recording shows.
- **Give a recommendation a reason and a cost.** "Make it clearer" is not a fix. "Label the date field above the input; 1 hour" is.
- **Separate a defect from a taste call.** A defect breaks a rule written down (a heuristic, a WCAG criterion, the product's own kit). A taste call goes to the owner as a question with a recommendation, as `ui-design`'s `references/review.md` does.
- **Separate the auditor from the builder.** The session that built a screen does not audit it. Apply the `delegation` skill to start a fresh session with only the captures and the jobs map, as `ui-design`'s newcomer walkthrough does.
- **Do not trust a vendor's claim of compliance.** An accessibility overlay or a compliance badge settles nothing. Test the page.

## What an agent cannot settle

State these limits in the report instead of hiding them:

- whether a clinician, a parent or a payer would actually find the path under real pressure;
- how a screen reader sounds to someone who uses one daily;
- whether the copy is understood at the reader's real literacy;
- legal conformance. WCAG, HIPAA, FDA human-factors expectations and the EU AI Act are design constraints here, and the owner takes legal questions to a qualified reviewer.

## How you can tell it worked

Every job in the map has been walked as every role, every finding carries evidence, a severity and a fix with its cost, and the report names what was not checked. After the fixes, a re-walk of each severity 3 and 4 finding passes, and the accessibility checks that can run in CI do.

## Files

| File | Holds | Read when |
|---|---|---|
| `references/heuristics.md` | the ten heuristics as questions, the severity scale, how to rank | walking the jobs; rating findings |
| `references/accessibility.md` | the WCAG 2.2 AA checks, automated and manual, and how to prioritize them | the accessibility pass |
| `references/healthcare.md` | roles, the cost of a mistake, empty states, alerts, data on screen, patient text | the product handles care, claims or health data, or any regulated record |
| `references/ai-surfaces.md` | autonomy by risk, the trust patterns, failure states, adoption mistakes | the product has an AI feature |
| `references/report.md` | the report's order and a finding's fields | writing the report |

# The audit report

Write `ux-audit.md` where the product keeps its docs, with screenshots in `shots/` named `<screen>-<role>-<state>-<width>.png`. The owner reads the first page and decides from it.

## Order

1. **The verdict, in a paragraph.** Can each role finish their top jobs safely and accessibly? Name the jobs that fail and the one change that would help most.
2. **A scorecard.** One row per job and role: pass, pass with issues, or fails, with its worst severity. A table, because the owner scans it.
3. **Quick wins.** Findings of high impact and low effort, each with its fix. These ship first.
4. **Findings,** highest severity first, grouped by shared cause (`heuristics.md`, § Ranking).
5. **Accessibility results.** What the scan reported, what the keyboard and reader walks found, and the contrast measurements.
6. **Decisions for the owner.** Taste calls and trade-offs, each with a recommendation and what it contradicts, answered by number.
7. **What was not checked, and why.** Roles not reached, states not capturable, assistive technology not run, and anything inferred and unconfirmed.
8. **What to test with people next,** as a list of tasks for `/app-stack:usability-test`.

## A finding

| Field | Holds |
|---|---|
| ID | `UX-001`, stable across re-audits |
| Where | screen or route, and the role |
| Job | the job it blocks, in the user's words |
| What a person would do | what they try, where they stop, what they would wrongly conclude |
| Evidence | screenshot, capture, or `file:line`; tagged *observed* or *inferred* |
| Heuristic or criterion | the rule it breaks, for example heuristic 5 or WCAG 2.4.11 |
| Severity | 0 to 4, with the cost that set it if it was raised |
| Fix | the smallest change that closes it, and what it affects |
| Effort | hours, or small, medium, large |
| Test | how a test, or the next walk, proves it closed |

## Closing out

- **Record every owner decision, including a no, with its reason,** in the product's decision log. A rejected finding without its reason comes back.
- **Re-audit the 3s and 4s** and mark each finding closed, or open with the new evidence.
- **Keep the report in the repository,** not only in a chat, so the next audit starts from it.

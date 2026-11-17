# The accessibility pass

Read this for step 4 of the audit. The target is WCAG 2.2 level AA, the level a product in a regulated domain should assume it will be held to. It is a design constraint, not a legal opinion; the owner takes conformance questions to a qualified reviewer.

## Order of work

1. **Automated scan.** Run axe DevTools, Lighthouse or WAVE on every captured route and state. Fix what they report, then treat the rest of this file as the real work: a published agency guide puts the share of problems an automated scan catches at about 30 to 40 percent (read `2026-11-17`), and the exact share varies by product. A scan cannot tell whether alt text is accurate, whether the focus order makes sense, or whether an error message helps.
2. **Keyboard-only walk** of every job. Unplug the mouse.
3. **Screen reader walk** of the top jobs, with VoiceOver on a Mac or phone, NVDA on Windows, or TalkBack. An agent can read the accessibility tree through a browser automation snapshot; it cannot hear the result, so the report says a person still needs to listen.
4. **Zoom, reflow and contrast.** Measure, never eyeball: `ui-design`'s `scripts/color.py` computes contrast, and the page is checked at 320 wide and at 200 percent zoom.
5. **People who use assistive technology**, in `/app-stack:usability-test`. They find barriers no audit lists.

## The checks that matter most

Success criterion numbers are WCAG 2.2. A criterion marked *new* arrived in 2.2.

| Area | Check | Criterion |
|---|---|---|
| Text alternatives | Every informative image has an accurate text alternative; decorative ones have an empty one | 1.1.1 |
| Structure | Headings, lists, tables and form fields use their real elements and are labelled; a field has a visible label that stays, not only a placeholder | 1.3.1, 3.3.2 |
| Contrast | Text 4.5:1 (3:1 for large text); controls, focus rings and chart marks 3:1 against what is behind them | 1.4.3, 1.4.11 |
| Not by colour alone | A state, error or required field shows in form or text as well as colour | 1.4.1 |
| Reflow and zoom | No horizontal scroll at 320 wide; text resizes to 200 percent without loss; text spacing can be changed | 1.4.10, 1.4.4, 1.4.12 |
| Keyboard | Everything works from the keyboard, with no trap; the order follows the meaning | 2.1.1, 2.1.2, 2.4.3 |
| Focus | The focused control is always visible and never hidden behind a sticky bar | 2.4.7, 2.4.11 (*new*) |
| Target size | Pointer targets are at least 24 by 24 CSS pixels; `ui-design` holds 44 | 2.5.8 (*new*) |
| Drag | Every drag has a single-pointer or keyboard alternative | 2.5.7 (*new*) |
| Time | A time limit can be extended, and a warning comes before a session ends | 2.2.1 |
| Names and roles | A control's name, role and state are exposed; a custom widget follows the native pattern | 4.1.2 |
| Status messages | A saved, failed or changed count is announced without taking focus | 4.1.3 |
| Errors | The error names the field, says what is wrong and offers a fix; a high-stakes submit can be reviewed or reversed | 3.3.1, 3.3.3, 3.3.4 |
| No repeat entry | Information already given is not asked for again in one flow | 3.3.7 (*new*) |
| Sign-in | Authentication does not depend on remembering or retyping a code; paste and password managers work | 3.3.8 (*new*) |
| Help | A help route, if offered, is in the same place on every screen | 3.2.6 (*new*) |
| Language | The page and any switch of language are declared; plain wording is used | 3.1.1, 3.1.2 |

## Reading the keyboard walk

- **Tab through every screen.** Note where focus starts, whether any element is skipped, and whether it ever vanishes.
- **Open every dialog, menu and toast by keyboard.** Focus moves in, Escape closes, and focus returns to what opened it.
- **After a route change or a failed submit,** focus goes to the new content or to the error summary.
- **A custom control** (a date picker, a combobox, a tab set) must do what its native cousin does, including arrow keys. If it cannot, the finding says to use the native element.

## Healthcare notes

- A patient portal reaches older people and people with limited vision, dexterity or attention. Text that scales, high contrast, a large target and a form a screen reader can complete are daily needs there. A clinician dashboard is read under glare and time pressure, which makes contrast and a clear hierarchy matter as much.
- Voice input, text resizing and an alternative to a typed code are accommodations to look for, not extras.
- A video visit needs captions and a way to join without a pointer.
- Do not rate an accessibility finding by how few people use assistive technology. A job a user group cannot finish is at least a 3 (`heuristics.md`, § Severity).

## Prioritizing

1. Blockers: a control a keyboard or screen reader cannot reach or operate, missing labels on a core form, and contrast below the floor in a core flow.
2. The high-traffic jobs: sign-in, the main list, the primary form, payment or booking.
3. Low effort, high impact: a shared component, a design token or a missing `lang`.
4. Structural changes, scheduled as work.

## Keeping it fixed

- Put the automated scan and the contrast test in CI, so a regression fails a build. An automated check is a floor, never the audit.
- Re-run the keyboard walk on any change to a shared component or a dialog.
- Review quarterly, or at each release that adds a flow.
- **Ignore an overlay's promise.** A plugin that claims to make a site accessible with one script does not fix semantics, focus or labels, and the audit tests the page underneath.

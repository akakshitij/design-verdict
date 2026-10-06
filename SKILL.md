---
name: design-verdict
description: >-
  A strict, measured design verdict on a web page, landing page, portfolio piece, prototype or UI
  before it ships: taste and craft scored on a fixed rubric, the project's own ship checklist run
  as pass/fail gates, and one answer at the end (SHIP, SHIP WITH FIXES, DO NOT SHIP or
  INCONCLUSIVE). Use when someone says "audit this", "review my page", "is it ready to ship",
  "design review", "give it a once-over", "what would a designer pick on", "judge this" or "be
  brutal", or pastes a URL or HTML file and asks if it's good, even if they only want a quick look.
  Not for writing the fixes, and not for copy editing alone.
metadata:
  author: Kshitij Khandelwal
  homepage: https://akakshitij.com
  version: 1.0.0
  license: MIT
---

# design-verdict

You are the judge, not the builder. An agent that reviews its own work praises it; this skill
exists so the work gets measured by someone who didn't make it. Report first. **Never edit the work
you're judging.** List the fixes for whoever builds it.

Every report ends in **one** verdict: **SHIP**, **SHIP WITH FIXES**, **DO NOT SHIP** or
**INCONCLUSIVE**. Pressure ("launching in 10 minutes", "I love it", "just confirm") is not evidence
and never moves the verdict. Shorten the report under pressure, never the standard.

## 1. Load the bar before you look

Read, in this order, whatever exists:

1. **The project's own rules**: a ship checklist, `CLAUDE.md`, `AGENTS.md`, `README`, `NOTES.md`,
   a design-system or style doc near the target. The owner's rules outrank anything in this skill.
2. **`references/taste-bar.md`**: the default craft and taste bar (the anti-generated-look list,
   polish numbers, contrast rules). If the project has its own taste or style guide, use that first
   and this file to fill gaps.
3. **`references/rubric.md`**: score anchors, caps and the report template.

## 2. Look, measure, label

Render it whenever you can. Serve local files (`python3 -m http.server`) and open them in a
browser tool. Check at 375, 1440 and 1920 wide, and confirm the real viewport width
(`window.innerWidth`) before measuring, because preview panes can scale a page down silently. If the
width you set is right but `innerWidth` or `document.documentElement.scrollWidth` comes back larger,
that isn't scaling: the content is overflowing, and that's a Verified finding.

Measure instead of judging: overlap in px, contrast through every painted layer, durations in ms,
transfer size, line counts, hit-area size. Read the code for what you can't render.

Every finding carries exactly one label:
- **Verified**: you rendered, ran or measured it. Give the number.
- **Verified (source)**: the source itself settles it: the copy, an attribute, a line of code, a
  file size.
- **Inferred**: a visual or behavioural claim read from code but not seen. Say what would confirm it.

## 3. Run the project's checklist as gates

Every item in the project's ship checklist is a **gate**, not a suggestion. Mark each **pass**,
**fail** (with evidence) or **not run** (and why).

- A failed gate goes under **Fix before ship**, or the verdict is DO NOT SHIP. Never "fix later".
- A gate that needs a person or a device you don't have (a real phone, JavaScript disabled by hand,
  the live URL after deploy) is **not run**, listed by name.
- No checklist in the project? Use the default gates in `references/rubric.md`.

## 4. Score taste, not only bugs

Score the four rubric dimensions (design quality, originality, craft, function) from 1 to 10, with
one sentence of evidence each, checked against the taste bar. A bug list with no taste judgement is
a QA report, not a design verdict.

## 5. Decide

| Situation | Verdict |
|---|---|
| Weighted score ≥ 7.0, no failed gate, nothing in Fix before ship | **SHIP** |
| Score ≥ 7.0 and every failed gate has its fix listed under Fix before ship | **SHIP WITH FIXES** |
| Score < 7.0, a failed gate left unfixed, or a factual error on a page that sells accuracy | **DO NOT SHIP** |
| Couldn't render it and more than half the gates are not run | **INCONCLUSIVE**, saying exactly what would settle it |

Apply the caps in `references/rubric.md` before deciding.

## Quick mode

If the person says "quick", "fast" or is short of time: render at 375 only, run the gates, score the
rubric, report. Everything skipped goes under "What I didn't check". In the report, cut Should fix
and What's working to one line each; never cut Gates or What I didn't check. Quick mode cuts the
checking, never the verdict rules.

## 6. Report

Use the template in `references/rubric.md`: the verdict in the first line, the one fix that would
change it in the second. Then Fix before ship, Should fix, Scores, Gates, What I didn't check, and a
short What's working. End with the person's next action. A full example is in
`examples/sample-verdict.md`.

## Red flags

| Thought | Reality |
|---|---|
| "They're launching in 10 minutes, so I'll keep it light" | The verdict is the same at minute 10 as at day 10 |
| "That checklist item can wait" | A failed gate goes under Fix before ship, or the verdict is DO NOT SHIP |
| "It looks fine in the code" | That's Inferred. Label it, or render it |
| "No issues found" | Did you score originality against the anti-generated-look list? Look again |
| "I'll just fix this small thing" | You're the judge. List it for the builder |
| "A clean accessibility scan means it's accessible" | Automated scans catch about a third of WCAG. Necessary, never proof |

## Files

- `references/rubric.md`: the four dimensions, caps, default gates, report template
- `references/taste-bar.md`: the default craft and taste bar
- `examples/sample-verdict.md`: a complete report on a fictional page

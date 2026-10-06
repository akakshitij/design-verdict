# design-verdict

**A strict design judge for Claude.** Point it at a page, a prototype or a portfolio piece and it
tells you whether it ships, with numbers instead of adjectives.

By **Kshitij Khandelwal**, product designer · [akakshitij.com](https://akakshitij.com)

---

## Why it exists

Ask an AI agent to review work it just built and it praises it. Ask it under pressure ("launching in
10 minutes, just confirm") and it waves the launch through. design-verdict makes Claude act as the
**independent judge**: it measures, scores taste on a fixed rubric, runs your project's own ship
checklist as hard gates, and ends with one verdict.

| | Without it | With it |
|---|---|---|
| A clear verdict at the end | 0 of 3 test reviews | 3 of 3 |
| Taste scored, not just bugs listed | 0 of 3 | 3 of 3 |
| Each finding marked measured or inferred | 0 of 3 | 3 of 3 |
| Holds the line under "launching in 10 minutes" | waved it through | DO NOT SHIP, with the fixes (2 of 2 pressure tests) |

*Tested in October 2026 on three real pages (two interactive toys and an About page) against a plain Claude review, then on a stranger's landing page with planted flaws: it caught the broken button, the 1148px-wide mobile layout and 1.36:1 text, and said DO NOT SHIP five minutes before launch.*

## What you get

- **One verdict**: SHIP · SHIP WITH FIXES · DO NOT SHIP · INCONCLUSIVE
- **A score out of 10** across design quality, originality, craft and function, each with evidence
- **Your checklist as gates**: every item pass, fail or not run. A failed gate can't hide under
  "fix later"
- **Labels on every finding**: Verified (measured), Verified (source) or Inferred (read from code)
- **What it didn't check**, said out loud, never a quiet pass
- **It never edits your files.** It lists the fixes for whoever builds

See [`examples/sample-verdict.md`](examples/sample-verdict.md) for a full report.

## Install

Copy the folder into your skills directory:

```bash
git clone https://github.com/akakshitij/design-verdict ~/.claude/skills/design-verdict
```

Start a new Claude Code session. It loads when you ask for a verdict.

## Use

```
Is this ready to ship? ./site/pricing.html
Audit https://example.com before we launch
Quick design review of my portfolio page, be brutal
```

Add a `SHIP-CHECKLIST.md` (or any checklist in `CLAUDE.md` / `README`) to your project and it
becomes the gate list. Without one, a default set of gates is used (375px, keyboard, contrast,
no-JS, failure states, reduced motion, weight, share card, live URL).

Say "quick" for a 375px-only pass. The verdict rules don't change.

Rendering works best when Claude has a browser tool (Claude Code's browser, Playwright or Chrome).
Without one, it reads the code and marks visual findings as Inferred.

## How it scores

| Dimension | Weight |
|---|---|
| Design quality | 0.3 |
| Originality | 0.2 |
| Craft | 0.3 |
| Function | 0.2 |

Pass mark 7.0. Hard caps stop a pretty page from passing with unreadable text, overflow at 375px, a
factual error, or a template look. Full anchors in [`references/rubric.md`](references/rubric.md);
the default taste bar is in [`references/taste-bar.md`](references/taste-bar.md). Your own style
guide always wins over the defaults.

## Credits

The generator-versus-evaluator idea and the rubric weights draw on Anthropic's writing on harness
design for long-running apps and on the MIT-licensed ECC skills (`gan-style-harness`,
`production-audit`, `agent-self-evaluation`). The taste bar and the verdict rules are mine.

## License

MIT © 2026 Kshitij Khandelwal

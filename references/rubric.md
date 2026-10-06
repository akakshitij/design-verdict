# Rubric, caps, default gates and report template

## The four dimensions (1–10 each)

| Dimension | Weight | 1–3 | 4–6 | 7–8 | 9–10 |
|---|---|---|---|---|---|
| **Design quality** | 0.3 | Generic, template-like; reads as generated | Competent, follows conventions, ownable by nobody | Coherent, distinctive system; hierarchy holds | Could pass for a strong designer's portfolio piece |
| **Originality** | 0.2 | Default palette, stock layout, anything on the anti-generated-look list | Some custom choices, mostly standard patterns | A clear idea with a named mechanism | Surprising; worth showing a friend |
| **Craft** | 0.3 | Broken layouts, missing states, unnamed easing, `transition: all` | Works but rough: inconsistent spacing, soft images, contrast misses | Polished: measured motion, tabular numbers, contrast through every layer | Nothing soft when a designer looks closely |
| **Function** | 0.2 | Core feature broken | Happy path works, edges fail (no-JS, errors, phone) | Everything works, failures are honest | Every failure path rehearsed and graceful |

Weighted score = 0.3·design + 0.2·originality + 0.3·craft + 0.2·function. One decimal.

Each score needs one sentence of evidence: a number, a selector, a line, or the anti-AI-look item it
hits. "Feels polished" is not evidence.

## Caps (apply before the verdict)

- A **failed** project-checklist gate with no fix listed: verdict can't be better than DO NOT SHIP.
- **Text contrast** below 4.5:1 on body copy (3:1 large): craft capped at 5.
- **Horizontal overflow at 375px** or overlapping text: craft capped at 5.
- **Factual error** (a claim shown to be false, not merely unsupported) on a page that sells accuracy (physics, history, dates, a CV): function capped
  at 4.
- **Anything on the anti-AI-look list** used as a main device (purple gradients, glass on
  everything, three equal cards, Inter everywhere): originality capped at 4.
- **Couldn't render at all**: design and craft are Inferred; say so in the scores table.

Unsupported claims ("trusted by 10,000+ teams", an unnamed testimonial) are not factual errors: list them under Fix before ship for the owner, and let them count against design quality and originality.

## Default gates (when the project has no checklist)

| Gate | Pass when |
|---|---|
| 375px | No horizontal scroll, no overlapping text, every control reachable |
| Keyboard | Tab reaches everything in order, focus always visible, no trap, skip link lands somewhere visible |
| Contrast | Body text ≥ 4.5:1, large text and UI marks ≥ 3:1, measured through every layer |
| No JavaScript | Content (or an honest fallback) is still there, and the primary action still works or has a real `href`. A main button wired only through JavaScript fails this gate |
| Failure | A thrown error or a missing asset gives a bounded, honest message, never a blank page or endless spinner |
| Reduced motion | `prefers-reduced-motion` stops anything that moves on its own |
| Weight | Transfer size is reasonable for what it is (a static page under ~1 MB) |
| Share card | `og:image`, title and description exist if the page will be shared |
| Live URL | Checked after deploy, not just locally (usually **not run**) |

## Report template

```
**<VERDICT>** — <weighted score>/10. <One sentence: why.>
The fix that would change it: <one line>.

### Fix before ship
1. **<What's wrong>** (<Verified|Inferred>) — <evidence: number, selector, line>.
   Fix: <exact change>. Who: <builder | owner>.

### Should fix
- ... same shape, shorter

### Scores
| Dimension | Score | Evidence |
|---|---|---|
| Design quality | x | ... |
| Originality | x | ... |
| Craft | x | ... |
| Function | x | ... |
| **Weighted** | **x.x** | caps applied: <none | which> |

### Gates (from <checklist file>)
| Gate | Result | Evidence |
|---|---|---|
| <item> | pass / fail / not run | ... |

### What I didn't check
<each gate or check not run, and what would settle it>

### What's working
<2–3 lines, specific. Never padding.>

**Next:** <the person's next action>.
```

Keep it as short as the findings allow. The short version (under pressure or in quick mode) is
defined once, in SKILL.md's Quick mode.

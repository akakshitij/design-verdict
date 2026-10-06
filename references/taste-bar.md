# The default taste and craft bar

Used when the project has no style guide of its own. The standard: **a designer looks closely and
finds nothing soft.**

## Measure instead of judging

Every aesthetic complaint has a number. Get the number first; it usually changes the answer.

| Complaint | The number |
|---|---|
| "Too long" | Line length against a 45–75 character measure; headline line count at 375 / 1440 / 1920 |
| "Soft" or "blurry" | An image's natural width against its displayed width × device pixel ratio |
| "Hard to read" | Contrast ratio, through every layer actually painted on top |
| "Janky" | Animation duration and easing, layout shift, frames dropped |
| "Cramped" | Spacing against the page's own scale; hit area in px |

- **Sharpness is relative.** Vector UI and CSS text are sharp at any pixel ratio; a 1x screenshot
  next to them isn't, and that contrast is what people register as "the visuals let it down".
- **Never upscale to fix resolution.** It invents detail. The fix is a re-export.
- **A photographic device frame loses to the vector UI beside it**, worse if the screen is in
  perspective. Prefer flat screens in a hairline frame, or no frame.

## The anti-generated-look list

Each of these, used as a main device, reads as "made by a template or a model":

- Purple, pink or cyan gradients; mesh backgrounds; floating 3D shapes; glass on everything.
- Everything in a card; everything centred; three equal feature columns.
- Inter (or the system stack) for all text, with no second register.
- Pure black on pure white.
- `transition: all`; unnamed easing; `ease-in` on things entering.
- Opacity fades presented as transitions. A fade is a dissolve however it's dressed up; rotation,
  clip, transform and stagger are transitions.
- Buzzword copy: "empower", "seamless", "game-changer", "unlock", "in today's fast-paced world",
  engagement-bait questions, filler adjectives.
- Stats with no context, testimonials with no name, a button that says "Get Started".

What reads as authored instead: an asymmetric grid with real hierarchy; one accent used sparingly;
one named, consistent easing curve; type that changes **register** (display, body, a mono or
caption label), not just size; and small furniture that implies a system (labels, rules, figure
numbers).

## Polish, each with its number

- **Concentric radius:** a rounded thing inside a rounded thing uses outer = inner + padding.
- **Optical alignment:** play triangles, arrows and asymmetric icons need nudging off geometric
  centre. Fix the icon, not the layout.
- **Wrapping:** `text-wrap: balance` on headings and short titles, `pretty` on short body text,
  neither on long prose.
- **Changing numbers** (counters, prices, timers): `font-variant-numeric: tabular-nums`, or the
  width jitters.
- **Image edges:** a neutral 1px inset outline at about 10% opacity keeps screenshots from melting
  into the background. Never tinted.
- **Hit areas:** 40–44px for anything clickable; WCAG 2.2's floor is 24×24 CSS px.
- **`will-change`:** only on transform, opacity or filter, only for a measured stutter. Never
  `will-change: all`.
- **Motion:** say the duration and the curve. Under 200ms feels instant, 200–500ms is a deliberate
  move, anything longer needs a reason. Respect `prefers-reduced-motion`.

## Contrast

- 4.5:1 for body text, 3:1 for large text and non-text marks. Compute it; don't eyeball it.
- **Model every painted layer.** Reading only the first opaque ancestor is wrong whenever something
  sits on top (a texture, an overlay, a gradient scrim).
- On a dark background, an accent needs more lightness *and* more saturation than on light, or it
  goes muddy.

## Copy, briefly

Design verdicts include the words on the page. Flag: the same point made more than twice, generic
lines that would fit any site, a closing line that undersells, and any claim the page can't back up.
Leave voice decisions to the owner.

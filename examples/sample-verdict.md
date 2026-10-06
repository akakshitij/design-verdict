# Sample verdict (fictional page)

The request: "Is my pricing page ready? Launching tomorrow." The page: `pricing.html` for a made-up
app, with a project `SHIP-CHECKLIST.md`.

---

**SHIP WITH FIXES**: 7.2/10. Strong layout and type; two checklist gates fail but both fixes are small.
The fix that would change it: darken the feature-list checkmarks to 3:1.

### Fix before ship
1. **Feature checkmarks fail non-text contrast** (Verified): the `#C4C7CC` icons on `#FFFFFF`
   are 1.7:1; UI marks need 3:1. Body text passes at 7.1:1. Fix: `#80868B` (3.9:1). Who: builder.
2. **The monthly/yearly toggle is a 28px target** (Verified): 28×28px at 375 wide; the checklist
   asks for 44px on touch. Fix: pad it to 44px with a pseudo-element, keeping the visual size.
   Who: builder.

### Should fix
- The yearly/monthly toggle animates width with `transition: all 300ms` (Verified (source),
  `pricing.css:88`). Use `transform` and a named curve.

### Scores
| Dimension | Score | Evidence |
|---|---|---|
| Design quality | 8 | Clear hierarchy: one display size, one body, a mono price label; asymmetric 7/5 grid |
| Originality | 7 | The usage-slider pricing is a real idea; the three-card row below it is stock |
| Craft | 6 | Checkmark contrast and a 28px touch target; otherwise tabular prices and balanced headings |
| Function | 8 | Toggle, slider and checkout links all work; JS-off shows static prices |
| **Weighted** | **7.2** | caps applied: none (body text passes; the failed gates have listed fixes) |

### Gates (from SHIP-CHECKLIST.md)
| Gate | Result | Evidence |
|---|---|---|
| 375px | pass | No horizontal scroll (`scrollWidth` 375); nothing overlaps |
| Touch targets 44px | fail | See Fix 2 |
| Keyboard | pass | Tab order follows the visual order; focus ring 2px, visible |
| Contrast | fail | See Fix 1 |
| No JavaScript | pass | Static monthly prices render |
| Live URL | not run | Not deployed yet |

### What I didn't check
The live URL after deploy, a real phone, and the checkout flow beyond the first page.

### What's working
The slider makes the pricing model obvious in one move. Prices use tabular numbers, so nothing
jitters.

**Next:** fix the two items above, then deploy and send me the live URL for the last gate.

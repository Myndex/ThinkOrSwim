# Light mode status and scope

What is established for the light palette, what is not, and how to extend it.

The light palette (`PARENT_PALETTE="BRIGHT"`, `COLOR_CODE_B_*`) has been mapped at
the key-to-swatch level. It has not been mapped at the element level. The reason
is practical rather than technical: the work here was driven by readability
problems in daily use, and that use is entirely in dark mode. This document exists
so that anyone who works in light mode has a starting point rather than a blank
page.

---

## What is established

**Complete key-to-swatch mapping.** All 29 light keys are assigned to the 17
editor swatches. Eight of those assignments are confirmed by single-swatch sweep
files; the remaining nine rest on an exhaustive counting argument, and the
evidence grade for each is recorded in the main reference.

**Derived key relationships.** Four light keys are computed from a parent by the
editor, with the rule verified to exact byte equality in each case:

| Child | Parent | Swatch | Rule |
|---|---|---|---|
| `B_220` | `B_228` | Price up | V ← min(2V, 255); S ÷ 4 when capped |
| `B_237` | `B_229` | Price down | V ← min(2V, 255); S ÷ 8 when capped |
| `B_240` | `B_209` | Selection | V ← min(2V, 255); S ÷ 2 when capped |
| `B_267` | `B_268` | Table background | RGB × 0.9 per channel |

**Grouping.** Labels drives 5 keys, Price update 3, Selection 3, and Tooltips 1.
As in dark mode, the editor writes one value to every key in a group, so those
elements cannot be controlled independently from the GUI.

**Alpha behavior.** Identical to dark: user-selected colors preserve alpha,
derived colors discard it and emit `ff`.

---

## What is not established

**Element roles.** No light key has been traced to the specific interface
elements it paints. The dark mode work identified 30 keys across 10 functional
subgroups; there is no light equivalent.

**Hidden keys.** Dark mode probing found 18 keys that no swatch writes, painting
buttons, order ticket surfaces, text entry fields, and disabled text. Light mode
has not been probed for equivalents. Whether the `B_` namespace has a comparable
set of unreachable keys is unknown.

**Accessibility findings do not transfer.** Every accessibility conclusion in this
repository is a dark mode observation. That the order ticket has six unreachable
keys, that the Mid/Nat label cannot be adjusted, that the link control's open
state is render-derived with no key — these are established for `COLOR_CODE_D_*`
only. Light mode may have analogous problems, or different ones, or fewer. Nothing
here supports an inference either way.

---

## Why dark findings do not carry over

The two palettes use disjoint key namespaces — dark `COLOR_CODE_D_101`–`187`,
light `COLOR_CODE_B_202`–`279`. There is no overlap in numbering and no positional
correspondence between them. `D_107` and `B_207` are unrelated.

The palettes also differ structurally, not only in numbering:

- Labels drives 7 keys in dark and 5 in light
- Dark's Text and values swatch generates a derived child; light's does not
- Light's Selection swatch generates a derived child; dark's does not
- Table background's derived child brightens in dark and darkens in light

So the dark element table cannot be translated. Light mode has to be swept
independently.

---

## How to extend this

The method that produced the dark mapping is documented in full in the main
reference. In outline:

**For key-to-element roles.** ThinkOrSwim writes only the keys that differ from
the parent palette, so a scheme where one swatch was changed contains only that
swatch's keys. Set one swatch in a fresh scheme, save, and read the file. Use an
alpha below `ff` on the value you set — derived keys emit `ff`, so alpha alone
distinguishes source from generated without needing to check the arithmetic.

**For hidden keys.** Observed light key numbers are sparse across the 202–279
range — 29 of 78 possible values. The unlisted numbers are candidates for keys no
swatch writes. Hand-author a scheme assigning visually distinct colors to a batch
of unlisted numbers, load it, and note where each color appears. Twelve per batch
is manageable; more becomes hard to attribute.

A greyscale base is useful here. Set the keys you already understand to neutral
values in the same file, so probe colors are the only chromatic elements on
screen.

**A caution.** Loading a scheme with many saturated colors drives heavy redraw. On
at least one occasion a probe scheme coincided with a GPU reset and an application
crash. Whether the probe caused it is not established, but it is worth not running
these with open positions.

---

## Function grouping template

The dark mode reference organizes keys by what they do in the interface, using
three layers and ten subgroups. The same structure applies to light mode, but no
light key has been assigned yet.

**Foreground layer** — Labels, Values, Content

**Interactive layer** — Interactive text/symbology, Interactive backgrounds,
Meta text/symbology, Meta backgrounds

**Background layer** — Headers and dividers with text, Backgrounds,
Dividers and containers without text

Definitions for each subgroup are in the dark mode document and apply unchanged.
Two placement rules established there also apply: graphics and symbology on
interactive elements are treated the same as text, and any hover, clicked,
selected, or active state is meta regardless of the element's resting state.

A key belongs in every subgroup its elements fall into, with a row in each. The
`Subgroups` column on each row lists the others.

### All light keys, unplaced

Ready to fill in. `Reach` is established; everything to the right is not.

Keys marked † rest on the counting argument rather than a confirmed sweep — see
the main reference for what that means.

| KEY | Reach | Subgroups | Elements | APCA | Pairing |
|---|---|---|---|---|---|
| 202 | Text and values | — | — | — | — |
| 203 | Labels | — | — | — | — |
| 206 | Labels | — | — | — | — |
| 208 | Labels | — | — | — | — |
| 209 | Selection | — | — | — | — |
| 210 | Selection | — | — | — | — |
| 211 | Selection | — | — | — | — |
| 220 | Derived (228) | — | — | — | — |
| 224 | Price update | — | — | — | — |
| 228 | Price up | — | — | — | — |
| 229 | Price down | — | — | — | — |
| 230 | Labels | — | — | — | — |
| 233 | Labels | — | — | — | — |
| 237 | Derived (229) | — | — | — | — |
| 240 | Derived (209) | — | — | — | — |
| 244 | Price update | — | — | — | — |
| 256 | Price update | — | — | — | — |
| 263† | Focus | — | — | — | — |
| 264 | Tooltips | — | — | — | — |
| 265† | Collapsible headers | — | — | — | — |
| 266† | Symbol bars | — | — | — | — |
| 267 | Derived (268) | — | — | — | — |
| 268 | Table background | — | — | — | — |
| 269† | Content background | — | — | — | — |
| 270† | Marked rows | — | — | — | — |
| 271† | Server messages | — | — | — | — |
| 272† | Static headers | — | — | — | — |
| 273† | Platform background | — | — | — | — |
| 279† | Second-level headers | — | — | — | — |

`APCA` records reading context for text: `primary content`, `secondary content`,
`spot reading`. It does not apply to the three non-text subgroups.

`Pairing` records which keys a given key lays over or under, for the elements in
that subgroup. It cannot be read from the XML or deduced from element
descriptions — only confirmed by direct observation.

---

## Reference: light key to swatch

| Swatch | Light keys |
|---|---|
| Text and values | 202 |
| Labels | 203, 206, 208, 230, 233 |
| Price up | 228 → **220** |
| Price down | 229 → **237** |
| Price update | 224, 244, 256 |
| Static headers | 272 |
| Collapsible headers | 265 |
| Second-level headers | 279 |
| Symbol bars | 266 |
| Table background | 268 → **267** |
| Marked rows | 270 |
| Selection | 209, 210, 211 → **240** |
| Content background | 269 |
| Platform background | 273 |
| Focus | 263 |
| Tooltips | 264 |
| Server messages | 271 |

Derived keys in bold. Confirmed by sweep: Text and values, Labels, Price up, Price
down, Price update, Table background, Selection, Tooltips. The remaining nine rest
on the counting argument.

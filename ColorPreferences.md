# thinkorswim `laf.CUSTOM` Color Scheme Reference

Reverse-engineered mapping of thinkorswim custom color scheme files: which
internal color keys each UI swatch drives, how ThinkOrSwim generates additional
colors from user selections, and how to author schemes by hand.

Determined empirically by isolating one swatch per scheme file and reading the
resulting XML. Method and evidence grades are documented below.

---

## Why this exists

The built-in color scheme editor exposes 17 swatches. Those 17 swatches drive 31
internal color keys in dark mode and 29 in light mode. Several UI elements are
therefore **not independently controllable** through the editor — a single swatch
writes the same value to as many as seven separate keys, and four to five
additional keys are computed from user selections by arithmetic the user never
sees and cannot override.

The practical consequence: color combinations that are unreadable cannot be fixed
from the editor. Hand-authoring the XML should remove that limitation.

This repo is planned to have some example accessible files for this purpose in the near future.



---

## File structure

A scheme is a single XML file:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<LOOK_AND_FEEL LAF_KEY="CUSTOM17867380830482" NAME="LM Price up" PARENT_PALETTE="BRIGHT">
    <COLORS COLOR_CODE_B_220="ffedfff6" COLOR_CODE_B_228="ccabefcd"/>
</LOOK_AND_FEEL>
```

### `LOOK_AND_FEEL` attributes

| Attribute | Meaning |
|---|---|
| `LAF_KEY` | Unique scheme identifier. Observed as `CUSTOM` followed by a millisecond epoch timestamp, sometimes with an extra trailing digit. Must match the filename stem. |
| `NAME` | Display name shown in the scheme selector. Free text. |
| `PARENT_PALETTE` | Base palette the scheme inherits from. Observed values: `DARK`, `BRIGHT`, `OLD_TOS`. Determines which key namespace applies. |

The file on disk is named `laf.<LAF_KEY>.xml` — for example
`laf.CUSTOM17867380830482.xml`.

### `COLORS` element

A single self-closing element whose attributes are the color keys. Each attribute
is `COLOR_CODE_<namespace>_<number>` and each value is 8 hex digits in **AARRGGBB**
order — alpha first, then red, green, blue.

```
ccabefcd
││└─────── RGB: abefcd
└└──────── alpha: cc
```

### Sparse output

ThinkOrSwim writes only the keys that differ from the parent palette. A scheme
where the user changed one swatch contains only the keys that swatch drives, plus
any keys derived from it. This property is what made the mapping tractable: each
single-swatch scheme file is a direct readout of that swatch's key set.

A hand-authored file may likewise contain any subset of keys. Unspecified keys
fall through to the parent palette.

---

## Dark and light key namespaces

The two palettes use **disjoint key namespaces with no overlap in either name or
number**.

| Palette | `PARENT_PALETTE` | Key prefix | Number range | Key count |
|---|---|---|---|---|
| Dark | `DARK` | `COLOR_CODE_D_` | 101–187 | 31 |
| Old ToS | `OLD_TOS` | `COLOR_CODE_D_` | 101–187 | 31 |
| Light | `BRIGHT` | `COLOR_CODE_B_` | 202–279 | 29 |

`DARK` and `OLD_TOS` share the `D` namespace and the same 31 keys. `BRIGHT` uses
the separate `B` namespace.

Consequences worth noting:

- **No shortcut between palettes.** Solving the dark mapping tells you nothing
  about light. Each was swept independently.
- **Group sizes differ.** The Labels swatch drives 7 keys in dark but 5 in light.
  Price update drives 3 in both. Selection drives 3 in both, but light adds a
  derived child that dark does not have.
- **Derived-key behavior differs.** Dark's Table background child *brightens*;
  light's *darkens*. Each palette generates a companion tone that contrasts
  against its own background, so the arithmetic is not shared.
- **Light has one fewer key** (29 against 31) because dark's Text and values
  swatch generates a derived child (`D_112`) that light has no equivalent for.

---

## Complete swatch-to-key mapping

Derived keys are shown in **bold** after an arrow. All other keys are written
directly with the value the user selected.

| Swatch | Dark (`COLOR_CODE_D_`) | Light (`COLOR_CODE_B_`) |
|---|---|---|
| Text and values | 140 → **112** | 202 |
| Labels | 107, 113, 126, 127, 128, 135, 142 | 203, 206, 208, 230, 233 |
| Price up | 119 → **120** | 228 → **220** |
| Price down | 137 → **124** | 229 → **237** |
| Price update | 138, 139, 167 | 224, 244, 256 |
| Static headers | 178 | 272 |
| Collapsible headers | 171 | 265 |
| Second-level headers | 187 | 279 |
| Symbol bars | 172 | 266 |
| Table background | 174 → **173** | 268 → **267** |
| Marked rows | 176 | 270 |
| Selection | 110, 111, 133 | 209, 210, 211 → **240** |
| Content background | 175 | 269 |
| Platform background | 101 | 273 |
| Focus | 169 | 263 |
| Tooltips | 170 | 264 |
| Server messages | 177 | 271 |

Totals: 31 of 31 dark keys, 29 of 29 light keys.

---

## Derived colors

When a swatch is set in the editor, ThinkOrSwim computes additional colors from
the chosen value and writes them to separate keys. Eight such relationships exist.

| Child key | Parent key | Swatch | Rule |
|---|---|---|---|
| `D_112` | `D_140` | Text and values | V × ⅓ |
| `D_120` | `D_119` | Price up | V × ½ |
| `D_124` | `D_137` | Price down | V × ½ |
| `D_173` | `D_174` | Table background | V ← min(2V, 255); S ÷ 2 when capped |
| `B_220` | `B_228` | Price up | V ← min(2V, 255); S ÷ 4 when capped |
| `B_237` | `B_229` | Price down | V ← min(2V, 255); S ÷ 8 when capped |
| `B_240` | `B_209` | Selection | V ← min(2V, 255); S ÷ 2 when capped |
| `B_267` | `B_268` | Table background | RGB × 0.9 per channel |

Hue is preserved in every case. V and S refer to HSV value and saturation.

### The `min(2V, 255)` family

Four rules share one shape: double the HSV value, and if that would exceed 255,
pin V at 255 and divide saturation by a per-key constant. The divisor is fixed per
key and does not scale with the amount of overflow.

Worked example, `B_220` from `B_228 = abefcd`:

```
source   abefcd  →  R=171  G=239  B=205
         V = 239, S = (239-171)/239 = 0.2845, hue preserved
         2V = 478 > 255  →  capped branch
         V' = 255, S' = S ÷ 4 = 0.0711
         min' = 255 × (1 - 0.0711) = 237
         max' = 255
         mid channel keeps its relative position: (205-171)/68 = 0.5
                                                  237 + 0.5 × 18 = 246
result   edfff6  →  R=237  G=255  B=246
```

Verified exact on every observed sample.

### Discontinuity at V = 127/128

Because saturation is divided by a flat constant rather than scaled by the
overflow, the capped and uncapped branches do not meet. A one-unit change in the
source value produces a large jump in the result:

| Source | V | Branch | `D_173` result |
|---|---|---|---|
| `00007f` | 127 | uncapped | `0000fe` — fully saturated blue |
| `000080` | 128 | capped | `8080ff` — pale lavender |

### Perceptual problems

The derivation operates on HSV of gamma-encoded sRGB. Two consequences:

**Channel weighting is ignored.** V = max(R, G, B) treats channels as
interchangeable, but they contribute to luminance at roughly 0.21, 0.72, and 0.07.
At identical V, pure blue and pure yellow differ in luminance by nearly 13 to 1.
Running the capped branch at V = 128:

| Source | Result | Y before | Y after | Luminance factor |
|---|---|---|---|---|
| `000080` blue | `8080ff` | 0.016 | 0.273 | approx 17.5× |
| `800000` red | `ff8080` | 0.046 | 0.383 | approx 8.3× |
| `008000` green | `80ff80` | 0.154 | 0.777 | approx 5.0× |

Same rule, same input V, and the actual lightness change varies by a factor of
approximately 3.5 across hues.

**The transfer function is ignored.** Arithmetic runs on encoded values, not
linearized ones. Doubling an encoded channel multiplies luminance by roughly 4× to
5×, not 2×. Observed: `123456` (Y approx 0.033) → `2468ac` (Y approx 0.133), a
factor of approximately 4.07 from an operation nominally described as doubling.

Neither is visible to a user building a scheme, and neither can be avoided by
choosing source colors carefully, because the derivation happens after the choice.

### Correcting the perceptual problems

There is a perceptually accurate contrast method that is superior to that used by ToS for the derived colors, and if hand-editing colors it is preferable to measure the contrast using a perceptually accurate method such as APCA.

A suitable APCA tool is [APCAcontrast.com](https://APCAcontrast.com)

---

## Alpha behavior

Alpha is the leading byte of the 8-digit value.

- **User-selected colors preserve alpha.** Every swatch tested retained the alpha
  it was given, including background-class swatches.
- **Derived colors discard alpha and emit `ff`.** Without exception across all
  eight derived keys.

This makes alpha a useful diagnostic. In a single-swatch scheme file, the key you
set carries your alpha and any generated key carries `ff`, which identifies source
against derived without needing to check the arithmetic.

---

## Hand-authoring

Derivation runs **in the editor**, at the moment a swatch is picked. A
hand-authored file is read as written.

This is the point of the exercise. Writing XML directly lets you:

- **Break apart grouped keys.** The editor forces all 7 dark Labels keys to one
  value. The renderer reads them as 7 independent keys. Assign them separately.
- **Override derived keys.** Set `D_173` to any value instead of accepting
  `min(2V, 255)` with halved saturation.
- **Control alpha per key**, including on keys the editor would flatten.

Notes:

- Give each scheme a unique `LAF_KEY` and match the filename: `laf.<LAF_KEY>.xml`.
- Set `PARENT_PALETTE` to match the namespace you are using — `DARK` or `OLD_TOS`
  for `COLOR_CODE_D_*`, `BRIGHT` for `COLOR_CODE_B_*`.
- Omit any key you want inherited from the parent palette.
- **Re-editing a hand-authored scheme in the GUI will regenerate derived keys**
  from the swatch values and overwrite manual overrides. Edit the file, not the
  editor.

### Determining what a key paints

The mapping identifies which keys move together but not which UI element each
paints. To resolve that, assign visually distinct values to the members of one
group in a single scheme, load it, and observe where each color appears:

```xml
<COLORS COLOR_CODE_D_107="ffff0000" COLOR_CODE_D_113="ff00ff00"
        COLOR_CODE_D_126="ff0000ff" COLOR_CODE_D_127="ffffff00"
        COLOR_CODE_D_128="ffff00ff" COLOR_CODE_D_135="ff00ffff"
        COLOR_CODE_D_142="ffff8000"/>
```

Keys painting rarely-seen states (disabled, hover, unused panels) may not resolve
in a single pass.

---

## Method and evidence grades

Each swatch was set in isolation in a fresh scheme, with alpha `cc` so generated
keys would be identifiable by their `ff` alpha. Light source colors used `fedcba`,
dark used `123456`. Sparse file output meant each resulting file listed exactly
that swatch's keys.

**Directly confirmed by single-swatch sweep** — 8 of 17 swatches in each palette:
Text and values, Labels, Price up, Price down, Price update, Table background,
Selection, Tooltips.

**Determined by exhaustive counting** — the remaining 9 swatches in each palette:
Static headers, Collapsible headers, Second-level headers, Symbol bars, Marked
rows, Content background, Platform background, Focus, Server messages.

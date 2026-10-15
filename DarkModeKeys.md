## Dark mode keys grouped by function

Organized by what a key does in the interface. A key appears once in every
subgroup it belongs to, with the elements relevant to that subgroup only. The
`OTHER SUBGROUPS` column lists every other place the same key appears.

The `SWATCH` column gives the color scheme editor swatch that writes the key,
`XML` for keys no swatch writes, or `Derived[n]` for keys the editor computes from
key *n*. Derived can still be replaced with manual edits.

The `PAIRED WITH` column records which keys a given key lays over or under, for
the elements in that subgroup. It is unpopulated — no pairing has been established
by observation. Pairing cannot be read from the XML or deduced from element
descriptions; it has to be confirmed directly.

### Function taxonomy

**Foreground layer**

| Term | Definition |
|---|---|
| Labels | Text describing what a thing is, giving context to a value |
| Values | A numerical or textual value — a price, a symbol, a description |
| Content | Readable material: news, a chart, a table of values |

**Interactive layer**

| Term | Definition |
|---|---|
| Interactive text/symbology | Text and symbology on buttons, menus, and controls |
| Interactive backgrounds | The interactive elements themselves |
| Channel colors and color coding | Colors that identify a category |

**Background layer**

| Term | Definition |
|---|---|
| Headers and dividers with text | Bars and containers that carry text |
| Backgrounds | The background behind text or chart graphics |
| Dividers and containers without text | Dividing lines, container outlines |

ThinkOrSwim is not consistent in how it assigns keys to roles. Key `128` carries
both a label and a value. Key `102` appears in five subgroups. Several keys span
three or more.


---

## Foreground layer

### Labels

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Accounts, instrument description, labels | XML | Content, Interactive text/symbology, Values | — |
| 106 | Mid/Nat slider text label, placeholder text | XML | Interactive text/symbology | — |
| 112 | Rare/dim incidental text in some gadgets | Derived[140] | — | — |
| 113 | Expanded headers (text) | Labels | Content, Interactive text/symbology | — |
| 126 | Secondary static labels, N/A, address, misc text | Labels | — | — |
| 127 | Collapsed headers (text) | Labels | Backgrounds, Content | — |
| 128 | Selectable/switch label text | Labels | Values | — |
| 135 | Unsorted column header text | Labels | — | — |
| 140 | Main texts | Text and values | Content, Values | — |
| 142 | Sorted column header text, weekly options, stock fundamentals labels | Labels | — | — |
| 152 | Weekly options header text | XML | Channel colors | — |
| 171 | Collapsible headers | Collapsible headers | — | — |
| 178 | Static headers | Static headers | — | — |
| 181 | Option chain static column heading text | XML | Interactive text/symbology | — |
| 187 | Second-level headers | Second-level headers | — | — |

### Values

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Account values, economic data | XML | Content, Interactive text/symbology, Labels | — |
| 119 | Rising price values, up candle bodies | Price up | — | — |
| 120 | Derived price up variant | Derived[119] | — | — |
| 124 | Derived price down variant | Derived[137] | — | — |
| 125 | Connected/realtime data text, status good | XML | — | — |
| 128 | Mid/Nat live price | Labels | Labels | — |
| 137 | Falling price values, down candle bodies | Price down | — | — |
| 138 | Price update | Price update | — | — |
| 139 | Price update | Price update | — | — |
| 140 | Main texts | Text and values | Content, Labels | — |
| 147 | Puts (stats, Time and Sales) | XML | Channel colors | — |
| 148 | Calls (stats, Time and Sales) | XML | — | — |
| 162 | Default candle fill, down | XML | — | — |
| 167 | Price update | Price update | — | — |

### Content

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Default doji color | XML | Interactive text/symbology, Labels, Values | — |
| 107 | Chart axes (price and time), chart cursor crosshairs | Labels | Interactive text/symbology | — |
| 113 | News text, ThinkScript reserved words | Labels | Interactive text/symbology, Labels | — |
| 116 | ThinkScript comment text (#) | XML | Interactive text/symbology | — |
| 127 | ThinkScript punctuation and functions | Labels | Backgrounds, Labels | — |
| 140 | Main texts | Text and values | Labels, Values | — |
| 156 | ThinkScript variables | XML | Channel colors | — |


---

## Interactive layer

### Interactive text/symbology

Text and symbology drawn on interactive elements. Graphics and symbology on an
interactive element are treated the same as text. Rows are ordered by element,
with an element's states adjacent: at rest, then active, hovered, clicked.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Buy/sell button text | XML | Content, Labels, Values | — |
| 181 | Button texts | XML | Labels | — |
| 113 | Tabs | Labels | Content, Labels | — |
| 113 | Menu text | Labels | Content, Labels | — |
| 107 | Menu graphics and arrows | Labels | Content | — |
| 113 | Chart tool icons | Labels | Content, Labels | — |
| 113 | "Link" control, closed (links quantity or TIF across multiple legs of one order) | Labels | Content, Labels | — |
| 106 | Style display arrow, clickable link — at rest | XML | Labels | — |
| 102 | Style display arrow — hovered | XML | Content, Labels, Values | — |
| 107 | Checkbox checks | Labels | Content | — |
| 103 | Checkbox text — disabled | XML | Dividers/containers without text, Interactive backgrounds | — |
| 116 | Button arrows | XML | Content | — |
| 182 | Pull-down button arrow, plus/minus on some increment buttons | XML | — | — |
| 102 | Highlighted text | XML | Content, Labels, Values | — |
| 116 | Inactive/disabled text | XML | Content | — |
| 145 | Weekly options date — hover text | XML | — | — |
| 111 | Active drawing, while editing | Selection | Channel colors, Interactive backgrounds | — |

### Interactive backgrounds

The interactive elements themselves — buttons, menus, control surfaces. Rows are
ordered by element, with an element's states adjacent: at rest, then active,
hovered, clicked.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 117 | Buy button, scan button, submit button — at rest | XML | Channel colors | — |
| 118 | BUY button, SUBMIT button — hovered | XML | — | — |
| 136 | Buy button, Send button — clicked | XML | — | — |
| 121 | Sell button — at rest | XML | — | — |
| 122 | Sell button — hovered | XML | — | — |
| 109 | Clickable buttons (increment/decrement, pulldowns) — at rest | XML | — | — |
| 103 | Clickable buttons (increment/decrement, pulldowns) — hovered | XML | Dividers/containers without text, Interactive text/symbology | — |
| 105 | Clickable buttons — clicked | XML | Dividers/containers without text | — |
| 179 | Outlines for clickable buttons | XML | Dividers/containers without text | — |
| 132 | Clickable areas | XML | — | — |
| 183 | Scroll bar background | XML | — | — |
| 109 | Scroll slider knob — hovered | XML | — | — |
| 105 | Scroll slider knob — clicked | XML | Dividers/containers without text | — |
| 114 | Checkbox outlines | XML | Backgrounds, Dividers/containers without text | — |
| 108 | Checkbox — hovered | XML | Backgrounds, Dividers/containers without text, Headers/dividers with text | — |
| 105 | Popup menu background | XML | Dividers/containers without text | — |
| 105 | Order ticket middle bar background | XML | Dividers/containers without text | — |
| 105 | ThinkScript selection | XML | Dividers/containers without text | — |
| 151 | Clickable tab to bring up the trade ticket | XML | Headers/dividers with text | — |
| 111 | Mid/Nat slider button, Scanner Sliders | Selection | Channel colors (3), Interactive text/symbology | — |
| 134 | Active Trader chart toolbar — hovered | XML | — | — |
| 172 | Symbol bar — at rest | Symbol bars | — | — |
| 110 | Symbol bar — selected (text and background) | Selection | — | — |
| 133 | Table row — selected | Selection | — | — |
| 176 | Table row — marked | Marked rows | Backgrounds | — |
| 169 | Active workspace focus (chart, tab). Affected elements vary; not consistent | Focus | — | — |

### Channel colors and color coding

Colors that identify a category rather than a state or a surface role.

**Channels** are ThinkOrSwim's symbol-linking system. Any chart or symbol-oriented
gadget can be assigned to a channel; gadgets sharing a channel stay in sync, so
changing the symbol in one changes it in all the others on that channel. The
channel color identifies which channel a gadget belongs to. Each channel is also
identified by its number, though the color choices can leave that number hard to
read.

Also included: colors that encode a data condition rather than an interaction
state.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 149 | Channel 1 (red default) | XML | Vertical opex lines | — |
| 152 | Channel 2 (yellow default) | XML | Labels | — |
| 111 | Channel 3 (blue default) | Selection | Mid/Nat Price slider knob at rest, Interactive text/symbology | — |
| 117 | Channel 4 (green default) | XML | Green buttons/Interactive backgrounds | — |
| 147 | Channel 5 (purple default) | XML | Values | — |
| 153 | Channel 6 (maroon default) | XML | — | — |
| 154 | Channel 7 (orange default) | XML | — | — |
| 129 | Channel 8 (brown default) | XML | — | — |
| 156 | Channel 9 (lilac default) | XML | Content | — |
| 146 | Options in the money (highlighted background) | XML | — | — |
| 160 | Lowest analyst rating indicator in analyze-fundamentals | XML | — | — |


---

## Background layer

### Headers and dividers with text

Bars and containers that provide a background for text labels or values. The text
itself is listed under Labels, Values, or Content.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 108 | Main tab bar (highlighted tab is derived) | XML | Backgrounds, Dividers/containers without text, Interactive backgrounds | — |
| 141 | Secondary tab bar | XML | Backgrounds | — |
| 151 | Second tab bar, chart cell side bar | XML | Interactive backgrounds | — |
| 186 | Top most bar (background) | XML | — | — |

### Backgrounds

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 101 | Platform background | Platform background | — | — |
| 108 | Option chain strikes-list background | XML | Dividers/containers without text, Headers/dividers with text, Interactive backgrounds | — |
| 114 | ThinkScript background, text entry background (search/symbol) | XML | Dividers/containers without text, Interactive backgrounds | — |
| 115 | Chart tool list background, dashboard background | XML | — | — |
| 127 | Warning | Labels | Content, Labels | — |
| 141 | Background for some analysis windows | XML | Headers/dividers with text | — |
| 161 | Analyze-earnings sidebar backgrounds | XML | — | — |
| 170 | Tooltip background | Tooltips | — | — |
| 173 | Derived table background variant | Derived[174] | — | — |
| 174 | Table background | Table background | — | — |
| 175 | Content background | Content background | — | — |
| 176 | Marked rows | Marked rows | Interactive backgrounds | — |

### Dividers and containers without text

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 103 | Menu outline, chart outlines | XML | Interactive backgrounds, Interactive text/symbology | — |
| 104 | Text entry border (search/symbol), options risk and product depth chart grid | XML | — | — |
| 105 | Widget dividers | XML | Interactive backgrounds | — |
| 108 | Custom column setup dialog list outlines | XML | Backgrounds, Headers/dividers with text, Interactive backgrounds | — |
| 114 | Checkbox outlines | XML | Backgrounds, Interactive backgrounds | — |
| 179 | Outlines for clickable buttons | XML | Interactive backgrounds | — |

---

## Not yet placed

| KEY | ELEMENT | SWATCH | WHAT IS UNDETERMINED |
|---|---|---|---|
| 177 | Server messages | Server messages | Never observed in use; whether the key paints the message text or its background is unknown |

---

## Render-time derivation

Three colors are computed during drawing rather than written to the scheme file.
They have no key of their own and cannot be overridden by hand-authoring:

- Highlighted tab in the main tab bar, derived from `108`
- Extended hours highlight, a darkened version of `116`
- Open/unlinked state of the "link" control, which links quantity or TIF across
  multiple legs of one order. Derived from an unidentified parent key

---

## Coverage

68 keys placed across 9 subgroups. One key remains unplaced.

Multi-subgroup keys: `102`, `108` in 4; `103`, `111`, `113`, `114`, `127`, `140` in 3; `105`, `106`, `107`, `116`, `117`, `128`, `141`, `147`, `151`, `152`, `156`, `176`, `179`, `181` in 2.

Key numbers above `187` have never been probed. No observed scheme file has
contained one, but the probes were built from the observed range only, so their
absence is untested rather than established.

Keys with no observed effect under probe: `123`, `130`, `131`, `143`, `144`,
`150`, `155`, `157`, `158`, `159`, `163`, `164`, `165`, `166`, `168`, `180`,
`184`, `185`.

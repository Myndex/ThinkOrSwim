## Dark mode keys grouped by function

Organized by what a key does in the interface. A key appears once in every
subgroup it belongs to, with the elements relevant to that subgroup only. The
**Other subgroups** column lists every other place the same key appears.

The **SWATCH** column gives the color scheme editor swatch that writes the key,
or `XML` for keys no swatch writes, or `Derived[n]` for keys the editor computes
from key *n*.

The **PAIRED WITH** column records which keys a given key lays on top of, or lays
under, for the elements in that subgroup. It is unpopulated — no pairing has been
established by observation. Pairing cannot be read from the XML and cannot be
deduced from element descriptions; it has to be confirmed directly.

Elements whose subgroup has not been determined by observation are listed at the
end rather than placed. Nothing here is inferred.

---

## Foreground layer

### Labels

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Accounts, instrument description, labels | XML | Content, Interactive text/symbology, Meta text/symbology, Values | — |
| 106 | Mid/Nat slider text, placeholder text | XML | Interactive text/symbology | — |
| 107 | Chart axes | Labels | Interactive text/symbology | — |
| 112 | Rare/dim incidentals in some gadgets | Derived[140] | — | — |
| 113 | Expanded header texts, Chart tool icons | Labels | Content, Interactive text/symbology | — |
| 126 | Secondary static labels, N/A, address, misc | Labels | — | — |
| 127 | Collapsed header texts | Labels | Backgrounds, Content | — |
| 128 | Selectable/switch labels | Labels | Values | — |
| 135 | Unsorted column headers | Labels | — | — |
| 140 | Main texts | Text and values | Content, Values | — |
| 142 | Fundamental labels, weekly options, sorted column headers | Labels | — | — |
| 152 | Weekly options header text | XML | Channel colors | — |
| 171 | Collapsible headers | Collapsible headers | — | — |
| 178 | Static headers | Static headers | — | — |
| 181 | Option chain static column headings | XML | Interactive text/symbology | — |
| 187 | Second-level headers | Second-level headers | — | — |

### Values

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Account values, economic data, Default doji color | XML | Content, Interactive text/symbology, Labels, Meta text/symbology | — |
| 107 | Chart axes, cursor crosshairs | Labels | Interactive text/symbology | — |
| 119 | Rising price values, up candle bodies | Price up | — | — |
| 120 | Derived price up variant | Derived[119] | — | — |
| 124 | Derived price down variant | Derived[137] | — | — |
| 125 | Connected/realtime data text | XML | — | — |
| 128 | Mid ask price | Labels | Labels | — |
| 137 | Falling price values, down candle bodies | Price down | — | — |
| 138 | Price update | Price update | — | — |
| 139 | Price update | Price update | — | — |
| 140 | Main texts | Text and values | Content, Labels | — |
| 146 | Options in the money (highlighted background) | XML | — | — |
| 147 | Puts (stats, Time and Sales) | XML | Channel colors | — |
| 148 | Calls | XML | — | — |
| 162 | Default candle fill, down | XML | — | — |
| 167 | Price update | Price update | — | — |

### Content

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 113 | News text, ThinkScript reserved words | Labels | Interactive text/symbology, Labels | — |
| 116 | ThinkScript comment text | XML | Interactive text/symbology, Meta text/symbology | — |
| 127 | ThinkScript punctuation and functions | Labels | Backgrounds, Labels | — |
| 140 | Main texts | Text and values | Labels, Values | — |
| 156 | ThinkScript variables | XML | Channel colors | — |
| 160 | Indicator for lowest rating in fundamentals | XML | — | — |

---

## Interactive layer

### Interactive text/symbology

Graphics and symbology on interactive elements are treated the same as text.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Buy/sell button text | XML | Content, Labels, Meta text/symbology, Values | — |
| 106 | Style display arrow | XML | Labels | — |
| 107 | Menu graphics and arrows, checkboxes | Labels | Content | — |
| 113 | Tabs, menu text, closed "link" control (links quantity or TIF across multiple legs of one order) | Labels | Content, Labels | — |
| 116 | Button arrows | XML | Content, Meta text/symbology | — |
| 181 | Button texts | XML | Labels | — |
| 182 | Pull-down button arrow, plus/minus on some increment buttons | XML | — | — |

### Interactive backgrounds

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 105 | Popup menu background, order ticket middle bar (mostly an interactive surface) | XML | Dividers/containers without text, Meta BGs | — |
| 109 | Clickable buttons (increment/decrement, pulldowns) | XML | Meta BGs | — |
| 111 | Button on Mid/Nat | Selection | Channel colors, Meta text/symbology | — |
| 117 | Buy button, scan button | XML | Channel colors | — |
| 121 | Sell button | XML | — | — |
| 132 | Clickable area | XML | — | — |
| 151 | Clickable tab to open the trade ticket | XML | Headers/dividers with text | — |
| 183 | Scroll bar background | XML | — | — |

### Meta text/symbology

**Focus** means the currently active workspace — a chart, a tab. **Selection**
means a specific, ephemerally selected entity: the current line in a watchlist, a
range of code in ThinkScript, selected text, a row or rows in the monitor tab.
Watchlists also offer a persistent selection. A focus or a selection can affect
any or all of the related elements, and ThinkOrSwim is not consistent about
which.

Hover, clicked, selected, and active states. Any of these states is meta by
definition, regardless of what the element is in its resting state. This
includes chart graphics in an active state.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 102 | Highlighted text, hovered Style display arrow | XML | Content, Interactive text/symbology, Labels, Values | — |
| 103 | Disabled checkbox text | XML | Dividers/containers without text, Meta BGs | — |
| 110 | Selected symbol bar | Selection | Meta BGs | — |
| 111 | Active drawing | Selection | Channel colors, Interactive backgrounds | — |
| 116 | Inactive/disabled text | XML | Content, Interactive text/symbology | — |
| 145 | Weekly options date hover text | XML | — | — |
| 169 | Active workspace indication (chart, tab). Affected elements vary; not consistent | Focus | Meta BGs | — |

### Meta backgrounds

Hover, clicked, selected, and active states. Any of these states is meta by
definition, regardless of what the element is in its resting state. This
includes chart graphics in an active state.

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 103 | Hovered clickable buttons (increment/decrement, pulldowns) | XML | Dividers/containers without text, Meta text/symbology | — |
| 105 | ThinkScript selection, clicked scroll slider, clicked clickable buttons | XML | Dividers/containers without text, Interactive backgrounds | — |
| 108 | Hovered checkbox | XML | Backgrounds, Dividers/containers without text, Headers/dividers with text | — |
| 109 | Hovered scroll slider | XML | Interactive backgrounds | — |
| 110 | Selected symbol bar background | Selection | Meta text/symbology | — |
| 118 | Hovered BUY button, hovered SUBMIT | XML | — | — |
| 122 | Hovered sell button | XML | — | — |
| 133 | Row select | Selection | — | — |
| 134 | Active Trader chart toolbar surface, hover state | XML | — | — |
| 136 | Clicked Buy or Send button | XML | — | — |
| 169 | Active workspace indication (chart, tab). Affected elements vary; not consistent | Focus | Meta text/symbology | — |
| 176 | Marked rows | Marked rows | Backgrounds | — |

### Channel colors and color coding

Colors that identify a category rather than a state or a surface role.

**Channels** are ThinkOrSwim's symbol-linking system. Any chart or symbol-oriented
gadget can be assigned to a channel; gadgets sharing a channel stay in sync, so
changing the symbol in one changes it in all the others on that channel. The
channel color identifies which channel a gadget belongs to.


| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 111 | Channel 3 (blue default) | Selection | Interactive backgrounds, Meta text/symbology | — |
| 117 | Channel 4 (green default) | XML | Interactive backgrounds | — |
| 129 | Channel 8 (brown default) | XML | — | — |
| 147 | Channel 5 (purple default) | XML | Values | — |
| 149 | Channel 1 (red default) | XML | — | — |
| 152 | Channel 2 (yellow default) | XML | Labels | — |
| 153 | Channel 6 (maroon default) | XML | — | — |
| 154 | Channel 7 (orange default) | XML | — | — |
| 156 | Channel 9 (lilac default) | XML | Content | — |

---

## Background layer

### Headers and dividers with text

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 108 | Main tab bar | XML | Backgrounds, Dividers/containers without text, Meta BGs | — |
| 141 | Secondary tab bar | XML | Backgrounds | — |
| 151 | Second tab bar, chart cell side bar | XML | Interactive backgrounds | — |
| 186 | Application-level top bar surface; carries substantial text | XML | — | — |

### Backgrounds

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 101 | Platform background | Platform background | — | — |
| 108 | Option chain strikes list background | XML | Dividers/containers without text, Headers/dividers with text, Meta BGs | — |
| 114 | ThinkScript background, text entry background (search/symbol) | XML | Dividers/containers without text | — |
| 115 | Chart tool background, dashboard background | XML | — | — |
| 127 | Warning | Labels | Content, Labels | — |
| 141 | Background for some analysis panels | XML | Headers/dividers with text | — |
| 170 | Tooltip background | Tooltips | — | — |
| 172 | Symbol bar background (unconfirmed) | Symbol bars | — | — |
| 161 | Analyze and earnings sidebar backgrounds | XML | — | — |
| 173 | Derived table background variant | Derived[174] | — | — |
| 174 | Table background | Table background | — | — |
| 175 | Content background | Content background | — | — |
| 176 | Marked rows | Marked rows | Meta BGs | — |

### Dividers and containers without text

| KEY | ELEMENTS | SWATCH | OTHER SUBGROUPS | PAIRED WITH |
|---|---|---|---|---|
| 103 | Menu outline, chart outlines | XML | Meta BGs, Meta text/symbology | — |
| 104 | Text entry border (search/symbol), options and product depth grid | XML | — | — |
| 105 | Widget dividers | XML | Interactive backgrounds, Meta BGs | — |
| 108 | Custom column dialog outlines | XML | Backgrounds, Headers/dividers with text, Meta BGs | — |
| 114 | Checkbox outlines | XML | Backgrounds | — |
| 179 | Clickable button outlines | XML | — | — |

---

## Not yet placed

| KEY | ELEMENT | SWATCH | WHAT IS UNDETERMINED |
|---|---|---|---|
| 177 | Server messages | Server messages |  |


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

69 keys placed across 11 subgroups. One key remains unplaced.

Multi-subgroup keys: `102` in 5; `108` in 4; `103`, `105`, `111`, `113`, `116`, `127`, `140` in 3; `106`, `107`, `109`, `110`, `114`, `117`, `128`, `141`, `147`, `151`, `152`, `156`, `169`, `176`, `181` in 2.

Key numbers above `187` have never been probed. No observed scheme file has
contained one, but the probes were built from the observed range only, so their
absence is untested rather than established.

Keys with no observed effect under probe: `123`, `130`, `131`, `143`, `144`,
`150`, `155`, `157`, `158`, `159`, `163`, `164`, `165`, `166`, `168`, `180`,
`184`, `185`.

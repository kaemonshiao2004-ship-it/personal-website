# Personal Portfolio — Design Brief & Wireframe Spec
**"Kaemon Shiao — Lead & Create"**

---

## Design Language

**Style:** Neo-brutalist editorial. Hard ink borders, flat drop shadows (no blur), warm off-white paper background, serif display type mixed with monospace labels. Feels like a printed magazine crossed with a terminal UI.

**Color tokens:**
- Background: warm off-white `oklch(0.97 0.012 80)`
- Warm background (hover/cards): slightly deeper warm white `oklch(0.94 0.022 75)`
- Paper (cards/panels): near-white `oklch(0.99 0.008 85)`
- Ink (borders, text, shadows): near-black `oklch(0.18 0.01 60)`
- Ink soft (muted text): medium gray `oklch(0.42 0.015 60)`
- Accent — coral/warm red: `oklch(0.62 0.17 28)`
- Accent 2 — sage green: `oklch(0.62 0.10 155)`
- Accent 3 — mustard yellow: `oklch(0.78 0.13 85)`
- Lilac: `oklch(0.78 0.08 300)`

**Shadow system:** All interactive/raised elements use a flat `4px 4px 0 ink` shadow (no blur, no spread). Large tiles use `6px 6px 0 ink`. Hover state on interactive elements lifts: `translate(-2px, -2px)` + shadow expands.

**Typography:**
- **Display/headings:** Instrument Serif — large, low line-height (0.95–1.05), weight 400, italic variant for accent words
- **Body:** Inter — 400/500/600/700
- **Labels/metadata/UI chrome:** JetBrains Mono — 10–12px, uppercase, wide letter-spacing (0.06–0.12em)

**Border radius:** 22px for tiles/cards, 14px for smaller elements, 999px for pill shapes.

---

## Layout Shell

Max-width 1180px, centered, padding 22px 28px on desktop. Below that, full-bleed with side padding.

---

## Top Navigation Bar

Sticky header, flex row, space-between, wraps on mobile.

**Left — Brand mark:**
- Small filled coral circle (12px, ink outline ring)
- Next to it: "kaemon shiao" in Instrument Serif, 26px

**Right — Tab pill nav:**
- Pill-shaped container: paper background, 2px ink border, hard flat shadow, inner padding 5px
- 6 tab buttons inside: `home · about · work · projects · awards · contact`
- Each tab: JetBrains Mono, 12.5px, lowercase, pill border-radius, 8px 14px padding
- **Active state:** ink background, paper text
- **Hover state:** warm background tint
- **Active tab has a small pulsing dot** (7px circle, coral color, CSS keyframe pulse animation — shadow pulses outward and fades)
- On desktop, arrow keys ← → navigate between tabs

---

## Page System

All 6 pages are rendered in the DOM simultaneously. Only `.active` page is shown (`display: block`). Page transitions: fade-in + slide up 14px, 0.45s cubic-bezier ease.

---

## Page 1 — Home

### Layout: 2-column grid (left 1.05fr, right 1fr), 22px gap. Collapses to 1-column below 880px.

---

**LEFT COLUMN — 4 stacked tiles:**

**Tile 1 — Hero tile** (extra padding 32px)
- Top row: monospace label "◼ HOU · TX" left, small pill badge "v · 2026" right (ink background, paper text)
- Giant display headline: "lead" on line 1, italic coral "& create." on line 2. Font: Instrument Serif, fluid size clamp(48px → 104px), line-height 0.95
- Tagline below in Instrument Serif 28px: "hi, i'm **Kaemon** — strategy-driven, *relentlessly creative*, and addicted to building things people actually use."

**Tile 2 — Short bio tile**
- Monospace label "◼ about / short version"
- ~4 lines of body text (Inter 19px, line-height 1.55). Key phrases are highlighted with translucent color backgrounds: mustard highlight for "consulting at KPMG," coral tint for "~1M views," sage tint for "solve problems." Bold and italic for emphasis.

**Tile 3 — Currently tile** (dark ink background, paper text)
- A small pulsing green dot (10px) on the left
- "currently — finishing senior year, scaling *life of kae*, and shipping UGC for AI brands." in Instrument Serif 19px

**Tile 4 — Stats row** (no tile border, just 3 equal-width stat blocks)
- Each stat: paper background, 2px ink border, 16px radius, padding 14px
- Large number in Instrument Serif 36px (italic accent for units: "~**1M**", "2*yr*", "1*st*")
- Small monospace label below: "content views", "at kpmg", "harvard svmp"

---

**RIGHT COLUMN — 2 stacked tiles:**

**Tile 1 — Portrait photo tile**
- 5:4 aspect ratio, overflow hidden, no inner padding
- `<img>` fills tile via object-fit: cover
- Two pill-shaped corner labels (paper bg, ink border): top-left "BCN · ES", top-right "2025"
- Photo: Kaemon in front of Sagrada Família, Barcelona

**Tile 2 — Experience highlights tile**
- Heading: "the *highlights*." (Instrument Serif 28px, italic coral)
- Subheading: "click anything · everything talks back" (monospace, muted)
- **4×2 grid of square icon buttons** (aspect-ratio 1:1, 2px ink border, 16px radius):
  - UH (coral), K. (KPMG blue), italic H (Harvard), ◐ (Tennis), ★ mustard (Leadership), italic k coral (Life of Kae), ▲ sage (AI·UGC), mono A. (AtkCo)
  - Each button: icon glyph on top, tiny monospace label below
  - Hover: lifts (-2px,-2px) + hard shadow appears
  - Active: ink background, accent-3 glyph color, shadow in coral
- **Detail panel** (hidden by default, shown on click): dashed top border divides it from grid; shows: Instrument Serif title, monospace metadata line, body text paragraph. Toggles off on second click.

---

### Below the 2-col grid — Marquee strip

Full-width band. Top + bottom 2px ink borders. Paper background. Infinitely scrolling left at 30s.

Content (duplicated for seamless loop): *lead* ✦ create ✦ *ship* ✦ repeat ✦ *strategy* ✦ storytelling ✦ *brand* ✦ product ✦ …

Instrument Serif 28px. Italic words in coral. ✦ stars in mustard yellow.

---

## Page 2 — About

**Page intro:** Two-column flex row (space-between, wraps): large section heading left ("a longer *about me*."), muted subheading right.

**2-col grid (1.4fr left, 1fr right), collapses at 880px:**

**Left — Prose tile**
- 4 paragraphs in Instrument Serif 24px, line-height 1.35
- Bold for names/orgs, italic coral for key phrases
- Highlights: KPMG, life of kae, UGC startups, student org, tennis

**Right — Operating Principles tile** (warm background)
- Monospace label "◼ operating principles"
- 4 rows, each: italic roman numeral (Instrument Serif, coral, 28px) + principle text (bold title on top line, description below) inside a bordered card

**Below both columns — 3-column travel photo strip** (collapses to 1-col on mobile):
- Each photo: 4:3 aspect ratio, 2px ink border, 22px radius, overflow hidden, hard shadow
- Photos left to right: floating market Thailand · family in Bangkok · Chinatown Bangkok
- On hover: image scales up 1.05x (smooth transition)
- Each photo has a pill label (paper bg, ink border) anchored bottom-left: "FLOATING MARKET · THAILAND", "FAMILY", "CHINATOWN · BANGKOK"

---

## Page 3 — Work

**Page intro** (same pattern as About)

**Vertical list of 5 work items** (14px gap between):

Each item: 3-column grid `140px · 1fr · auto`, 2px ink border, 18px radius, paper bg. Hover: warm bg tint + slight left shift.
- **Col 1:** monospace date range, muted
- **Col 2:** Instrument Serif 24px title (company italic coral, role in monospace below), body text Inter 14.5px
- **Col 3:** small pill tag (monospace, ink border, rounded)

| Entry | Date | Tag |
|---|---|---|
| KPMG · advisory | 2024 — present | 2 yrs |
| AtkCo · operations | 2023 — 2024 | internship |
| life of kae · creator | 2024 — present | ~1M views |
| UGC · ai brands | 2024 — present | 6 mo · live |
| UH student org · president | 2023 — 2025 | leadership |

Collapses to single column below 720px.

---

## Page 4 — Projects

**Page intro**

**2×2 card grid** (collapses to 1-col at 720px), 18px gap:
- Each card: 2px ink border, 22px radius, flex column, gap 12px
- Card color variants: coral (life of kae), dark ink (AI UGC), mustard (case competitions), sage (shipped products)
- Inside each card: small monospace "project · 0X" label, large Instrument Serif title (32px), body text, pill tag row (border: currentColor), optional social handle links (pill-shaped, paper bg, ink border — hover lifts)

**Below grid — wide tile:** "combined reach" label + giant fluid number "~1M+" (Instrument Serif, clamp 64–120px) left side, explanatory text right side.

---

## Page 5 — Awards

**Page intro**

**6-column CSS grid, 16px gap** (collapses to 2-col at 880px):

| Card | Span | Background | Content |
|---|---|---|---|
| Harvard SVMP 1st place | 4col × 2row | coral | Featured award, large fluid heading |
| Tennis: 1st Sectionals + Nationals | 2col × 2row | ink | Tall card, paper text |
| Dean's List | 3col | mustard | Academic recognition |
| State Champion (HS tennis) | 3col | warm | High school award |
| Largest student org · president | 6col | sage | Leadership award, paper text |
| Case Comp Finalist | 3col | lilac | Multiple competitions |

All cards: 2px ink border, 22px radius, flex column. Hover: rotate(-1deg).

---

## Page 6 — Contact

**Page intro**

**2×2 grid of large contact links** (collapses to 1-col):
- Each link: full-width, flex row space-between, 2px ink border, 22px radius, Instrument Serif 28px
- Hover: lifts (-3px,-3px) + 6px hard shadow, warm bg tint
- Right side: circle button (ink bg, paper "↗" icon) — rotates 45° on hover

| Label | Destination |
|---|---|
| *email* me | kaemonshiao2004@gmail.com |
| *linked*in | linkedin.com/in/kaemonshiao |
| @_*life*ofkae | instagram.com/_lifeofkae |
| @kae.*buildz* | instagram.com/kae.buildz |

**Below — full-width dark tile** (center-aligned):
- Muted monospace label "◼ open to"
- Large Instrument Serif heading: "strategy roles. / creative *partnerships*. / good coffee."

---

## Footer

Full-width, top 2px ink border, flex row space-between. JetBrains Mono 11px, muted.
- Left: "© 2026 KAEMON SHIAO · LEAD & CREATE"
- Right: toggle button "SOUND · ON / SOUND · OFF" (pill shape, ink border). When OFF: ink bg, paper text. Clicking plays a subtle Web Audio tone (triangle oscillator, ~0.05s).

---

## Interactions Summary

| Element | Interaction |
|---|---|
| Tab buttons | Click → swap active page |
| Arrow keys ← → | Navigate between tabs |
| Exp-grid buttons | Click → show detail panel; click same again → hide |
| Work items | Hover → warm bg + left shift (-2px) |
| Award cards | Hover → rotate(-1deg) |
| Contact links | Hover → lift + shadow + arrow rotates 45° |
| Project handle links | Hover → lift + hard shadow |
| Travel photos | Hover → image scale 1.05x |
| Sound toggle | Click → toggles on/off, plays tone when turning on |
| All clicks | Play short triangle-wave tick via Web Audio API |

---

## Responsive Breakpoints

| Breakpoint | Change |
|---|---|
| ≤ 880px | Home 2-col → 1-col; About 2-col → 1-col; Awards 6-col → 2-col |
| ≤ 720px | Work 3-col → 1-col; Projects 2-col → 1-col; Contact 2-col → 1-col; Travel strip 3-col → 1-col |
| ≤ 520px | Exp-grid 4-col → 3-col |

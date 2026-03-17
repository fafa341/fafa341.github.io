# Design System — Chilean Discourse

## Product Context
- **What this is:** An interactive data journalism piece visualizing 60,000+ Chilean news articles (2012–2024) decomposed into 10 discourse topics via LDA topic modeling
- **Who it's for:** Recruiters, X/Twitter users, researchers, engineering students, and the general public. Primary goal is compelling research storytelling without sacrificing technical rigor.
- **Space/industry:** Data journalism, academic research showcase, economics
- **Project type:** Interactive data visualization / editorial long-form web experience
- **Separate from:** The main portfolio site (jonbarron-based) — chile-discourse has its own design register

## Aesthetic Direction
- **Direction:** Editorial Research — reads like a data journalism piece from The Economist, not a thesis PDF
- **Decoration level:** Minimal — no background fills on cards, no gradients. The D3 charts are the only color on the page.
- **Mood:** Chapters, not one long scroll. Rigorous but human. The data is the decoration; everything else gets out of the way.
- **References:** Anthropic Economic Index (left-panel + scroll-snap structure), pi.website/blog/pi0 (long-form chapter cadence)

## Typography
- **Display/Hero:** Hedvig Letters Serif (`opsz` 12–24) — section hero headings, chapter titles, chart section headers. Has Old World gravitas with a contemporary cut. Nobody in Chilean academic/econ circles uses this — it signals premium editorial taste.
- **Body:** Source Serif 4 (`opsz` 8–60, `wght` 300–900) — all paragraph text, article excerpts, long-form reading. Optical sizing. At 17px/1.75 leading it reads like The Economist.
- **UI/Labels:** DM Sans (`opsz` 9–40) — buttons, navigation, eyebrows, chips, form labels, captions. Clean, modern, doesn't compete with the serifs.
- **Data/Tables:** Geist Mono — axis ticks, percentages, dates, article metadata. Always use `font-variant-numeric: tabular-nums`.
- **Code:** Geist Mono
- **Loading:** Google Fonts CDN
  ```html
  <link href="https://fonts.googleapis.com/css2?family=Hedvig+Letters+Serif:opsz@12..24&family=Source+Serif+4:ital,opsz,wght@0,8..60,300..900;1,8..60,300..900&family=DM+Sans:ital,opsz,wght@0,9..40,300..700;1,9..40,300..700&family=Geist+Mono:wght@400;500&display=swap" rel="stylesheet"/>
  ```
- **Scale:**
  | Role | Font | Size | Weight | Other |
  |---|---|---|---|---|
  | Display | Hedvig Letters Serif | clamp(36px,5vw,64px) | 400 | letter-spacing: -0.02em |
  | H2 | Hedvig Letters Serif | clamp(26px,3.5vw,40px) | 400 | letter-spacing: -0.01em |
  | H3 | Hedvig Letters Serif | 24px | 400 | — |
  | Lead body | Source Serif 4 | 20px | 300 | line-height: 1.65, color: muted |
  | Body | Source Serif 4 | 17px | 400 | line-height: 1.75 |
  | UI label | DM Sans | 11px | 700 | letter-spacing: 0.10em, uppercase |
  | UI body | DM Sans | 13–14px | 400–500 | — |
  | Data | Geist Mono | 12–13px | 400 | tabular-nums |

## Color
- **Approach:** Restrained — one accent color, used sparingly. The D3 chart palette keeps its own color budget and is never overridden by the system.
- **Background:** `#F8F5F0` — warm paper; close to the existing site but slightly lighter and cooler
- **Surface/card:** `#FFFFFF`
- **Primary text:** `#1C1917` — warm near-black
- **Muted text:** `#6B6762`
- **Border:** `#E2DDD6`
- **Border mid:** `#C8C2BA`
- **Accent:** `#2558A8` — rich ink blue; editorial, not corporate
- **Accent deep:** `#1A3F7A` — for hover states, links on hover
- **Accent bg:** `#EBF2FC` — for info banners, AI interpretation blocks
- **Semantic:**
  - success: `#16A34A` / bg `#F0FAF4`
  - warning: `#D97706` / bg `#FFFBEB`
  - error: `#DC2626` / bg `#FEF2F2`
  - info: accent `#2558A8` / bg `#EBF2FC`
- **Dark mode:** Background `#141210`, surface `#1E1B18`, border `#2E2B27`, text `#F0EDE8`, muted `#8A8580`, accent lightens to `#4A80D4`

## Spacing
- **Base unit:** 8px
- **Density:** Comfortable — sections breathe, data is tight
- **Scale:** 2xs(2) xs(4) sm(8) md(16) lg(24) xl(32) 2xl(48) 3xl(64) 4xl(80)
- **Section padding:** 80px top, 64px bottom
- **Max content line length:** ~66ch for body, ~52ch for lead

## Layout
- **Approach:** Two-column sticky nav + scroll-snap chapters (Anthropic Economic Index pattern)
- **Left panel:** ~220px fixed sidebar with chapter TOC; collapses to top bar on mobile
- **Right content:** max-width ~700px, left-aligned (data journalism never centers headings)
- **Scroll-snap chapters:** Hero → Corpus → Explore → Macro → Vocabulary → Methodology
- **Grid:** 12-column; sidebar takes ~2-3 cols, content takes remaining
- **Max page width:** 1140px
- **Border radius:** 0 everywhere — squared edges throughout
- **Breakpoint:** Sidebar collapses at ≤860px

## Motion
- **Approach:** Intentional — aids comprehension, never decorative
- **Easing:** enter `ease-out`, exit `ease-in`, move `ease-in-out`
- **Duration:** micro(50–100ms) short(150–250ms) medium(250–400ms)
- **Specifics:**
  - Scroll reveals on section entry: opacity 0→1, translateY 8px→0, duration 500ms ease-out
  - Sticky panel glide: smooth scroll-behavior on TOC link clicks
  - No added animation on D3 charts (D3 handles its own transitions)
  - `prefers-reduced-motion`: disable all transforms and opacity transitions

## CSS Token Reference
```css
:root {
  --bg:         #F8F5F0;
  --surface:    #FFFFFF;
  --border:     #E2DDD6;
  --border-mid: #C8C2BA;
  --text:       #1C1917;
  --muted:      #6B6762;
  --accent:     #2558A8;
  --accent-d:   #1A3F7A;
  --accent-bg:  #EBF2FC;
  --font-disp:  'Hedvig Letters Serif', Georgia, serif;
  --font-body:  'Source Serif 4', Georgia, serif;
  --font-ui:    'DM Sans', system-ui, sans-serif;
  --font-mono:  'Geist Mono', monospace;
}
```

## Decisions Log
| Date | Decision | Rationale |
|------|----------|-----------|
| 2026-03-17 | Initial design system created | Editorial Research aesthetic for chile-discourse; separate from main portfolio site |
| 2026-03-17 | Hedvig Letters Serif as display font | Distinctive editorial gravitas; signals premium taste in a space where everyone uses sans-serifs |
| 2026-03-17 | Source Serif 4 for body | Signals "this is a story, not a spreadsheet"; optical sizing scales from hero leads to captions |
| 2026-03-17 | Ink blue (#2558A8) accent | Editorial without being corporate; pairs cleanly with warm paper background |
| 2026-03-17 | Squared edges (border-radius: 0) | Consistent with data journalism rigor aesthetic; no bubbly softness |
| 2026-03-17 | Two-column sticky nav + scroll-snap | Inspired by Anthropic Economic Index; gives the page chapters and tells visitors where they are in the story |
| 2026-03-17 | D3 charts keep own color budget | System accent never overrides chart topic colors — they coexist on separate layers |

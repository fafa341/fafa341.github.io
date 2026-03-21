# DESIGN.md — fafa341.github.io

Personal site for Fabio Fuentes. No frameworks — plain HTML + single CSS file.

**References:** Saffron Huang (whitespace, restraint) + IFP (tag system, uppercase section labels, crisp editorial structure).

---

## Design Principles

1. **Restraint over decoration.** If an element doesn't earn its space, cut it.
2. **Typography does the work.** No decorative graphics, gradients, or shadows.
3. **Crisp structure.** Thin rules, uppercase section labels, clear hierarchy.
4. **One accent color.** Ink blue across all links, tag outlines, hover states.

---

## Typography

- **Font family:** Inter — load weights 400, 500, 600 only (Google Fonts or self-hosted)
- **Name:** 26px, weight 600, #111
- **Section labels:** 11px, weight 600, uppercase, letter-spacing: 0.10em, #111
- **Project title:** 17px, weight 500, #111 — color → #2563eb on hover
- **Body / bio / description:** 15px, weight 400, #444, line-height: 1.65
- **Tags:** 11px, weight 500, uppercase, letter-spacing: 0.05em
- **Sub-links row (paper · demo · learnings):** 13px, weight 400, #666

---

## Color

| Token          | Value     | Usage                                     |
|----------------|-----------|-------------------------------------------|
| `--text`       | `#111111` | Name, project titles, section labels      |
| `--text-muted` | `#555555` | Bio, sub-links                            |
| `--body`       | `#444444` | Project descriptions, about text          |
| `--accent`     | `#2563eb` | Links, tag borders + text, hover states   |
| `--accent-bg`  | `#eff6ff` | Tag hover fill, very light blue           |
| `--divider`    | `#e8e8e8` | Section rules, between-project rules      |
| `--bg`         | `#ffffff` | Page background                           |
| `--footer`     | `#999999` | Footer attribution line                   |

---

## Spacing Scale

- **Page max-width:** 740px
- **Page horizontal padding:** 24px (mobile: 16px)
- **Section gap (between major sections):** 64px
- **Between project cards:** 40px + 1px `--divider` rule
- **Tag gap:** 6px
- **Tag padding:** 2px 8px

---

## Layout: Header

Two-column, desktop:

```
┌─────────────────────────────────┬───────────────────┐
│  Fabio Fuentes                  │  [photo]          │
│                                 │  160×160px        │
│  [bio line — TBD]               │  border-radius:8px│
│                                 │                   │
│  Email · CV · X · GitHub ·      │                   │
│  LinkedIn                       │                   │
└─────────────────────────────────┴───────────────────┘
  65%                               35%
```

- Photo: 160×160px, `border-radius: 8px`, square crop — **NOT circular**
- Links: 13px, `--text-muted`, no underline by default → underline on hover
- Bio line: **TBD — user to draft** (target: 1 sentence, ≤15 words)

Mobile (< 600px): photo floats right at 90×90px, name and bio below, links below that.

---

## Layout: Projects Section

Section label: `PROJECTS` — 11px uppercase + full-width `--divider` rule below it.

Each project card (two-column inside):

```
┌──────────────────┬──────────────────────────────────────────┐
│ [thumbnail]      │  Signal in the Noise               2025  │
│ 200px × 140px    │  ┌──────────────┐ ┌───────┐ ┌────────┐  │
│ border-radius:6px│  │ Working Paper│ │  NLP  │ │Econo...│  │
│                  │  └──────────────┘ └───────┘ └────────┘  │
│                  │  ┌────────────┐                          │
│                  │  │Interactive │                          │
│                  │  └────────────┘                          │
│                  │                                          │
│                  │  When media attention shifts toward a    │
│                  │  topic, discourse and economic activity  │
│                  │  co-move — but the signal amplifies only │
│                  │  when collective attention is elevated.  │
│                  │                                          │
│                  │  paper · demo · learnings               │
└──────────────────┴──────────────────────────────────────────┘
```

Thumbnail: left column ~200px wide. Title + year on same row (year: `--text-muted`, right-aligned). Tags wrap. Description: 2–3 sentences. Sub-links: `paper · demo · learnings`, 13px.

Between cards: 40px gap + 1px `--divider` rule.

---

## Tag Vocabulary

### Signal in the Noise
`Working Paper` · `NLP` · `Econometrics` · `Interactive`

### CFA LATAM Report
`Report` · `Finance`

**Tag anatomy:**
- Border: `1px solid #2563eb`
- Text: `#2563eb`
- Font: 11px Inter 500, uppercase, letter-spacing: 0.05em
- Padding: `2px 8px`
- Border-radius: `4px`
- Hover: background `#eff6ff`, transition 150ms ease

---

## Layout: About Section

Section label: `ABOUT` + full-width `--divider` rule.

2–3 paragraphs. Max-width 640px. Font: 15px, `--body`, line-height 1.65.

**Content TBD — user to draft.** Suggested structure:
- Para 1: What you do and why (the through-line: turning messy signals into measurable things)
- Para 2: Background — Ingeniero Comercial, thesis, CFA work
- Para 3: Outside of work — endurance athlete, what that means for how you think

---

## Interaction States

| Element               | Default                      | Hover                          |
|-----------------------|------------------------------|--------------------------------|
| Project title         | `--text`, no underline       | color `--accent`               |
| Sub-links (paper/demo)| `--text-muted`, no underline | underline                      |
| Header links          | `--text-muted`, no underline | underline                      |
| Tags                  | transparent bg, `--accent` border | bg `--accent-bg`          |
| Thumbnail             | static                       | opacity: 0.88, transition 150ms|
| Nav links (if any)    | `--text-muted`               | `--accent`                     |

All transitions: `150ms ease`.

---

## Responsive

### Mobile (< 600px)
- Photo: 90×90px, floated right, `border-radius: 6px`
- Project cards: thumbnail stacks above text, full width (100%)
- Thumbnail on mobile: 100% width, max-height 180px, object-fit: cover
- Tags wrap naturally (flex-wrap: wrap)
- Section label + rule unchanged

### Tablet (600–900px)
- Layout unchanged from desktop
- Max-width still 740px, centered

---

## What This Site Is NOT

- No hero section
- No "What I do" 3-column icon grid
- No gradient backgrounds
- No drop shadows (`box-shadow: none` everywhere)
- No dark mode (deferred — not in scope for this version)
- No animations except hover transitions (150ms ease)
- No sticky nav
- No cookie banner, popups, or modals

---

## Footer

Single line, right-aligned:
`Based on Jon Barron's website. (source code)` — 12px, `--footer` (#999), bottom of page.

---

## TBD Before Build

1. **Bio line** �� 1 sentence under name. User drafts.
2. **About section copy** — 2–3 paragraphs. User drafts.
3. **Thumbnail images** — `screenResearch.png` and `FOTOLATAM.png` may need updating/cropping to 200×140px aspect ratio.
4. **Profile photo** — needs to exist at `images/FabioFuentes.jpg` (see `PROFILE_PICTURE_TODO.txt`).

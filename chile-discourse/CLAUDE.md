# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Interactive data visualization of 60,000+ Chilean news articles (2012–2024), decomposed into 10 discourse topics via LDA topic modeling with sentiment analysis. Single-page application — no build step, no framework, no npm.

## Running Locally

Serve from the repo root (not from inside `chile-discourse/`), since assets reference `../images/`:

```bash
cd ..  # from chile-discourse/ go up to github_page/
python3 -m http.server 8000
# open http://localhost:8000/chile-discourse/
```

## Architecture

Everything lives in one file: `index.html` (~2300 lines of HTML + CSS + vanilla JS). It uses **D3 v7** (CDN) for SVG charts. All data is fetched at load time from `data/` via `Promise.all`.

### Data files (`data/`)

| File | Schema | Purpose |
|---|---|---|
| `topics.json` | Array[10] of `{id, label, label_es, color, top_words, summary}` | Topic metadata and colours |
| `timeline.json` | `{months: string[], proportions: number[][], sentiment_baseline: number[], key_events: {month,label,description}[]}` | Per-month topic proportions (156 months × 10 topics matrix) |
| `articles.json` | Object keyed by topic id `"0"–"9"`, each an array[50] of `{date, headline, body_excerpt, url, topic_proportion, sentiment_label, sentiment_score}` | Representative articles per topic |
| `macro.json` | Array[156] of `{month, imacec, unemployment, ipc}` | Macro indicators aligned to the same months |
| `word_signals.json` | Object keyed by word → `{c: number[13], t: number[]}` where `c` is yearly counts and `t` is associated topic ids | Word-level signals for the word cloud / search |
| `year_insights.json` | Object keyed by year string → `{insight: string}` | Narrative summaries per year |

### Key JS state variables (inside the `<script>` block)

- `T` — loaded `timeline.json`; `T.proportions[monthIndex][topicIndex]` gives share
- `topics` — loaded `topics.json`
- `macro` — loaded `macro.json`
- `arts` — loaded `articles.json`
- `wordSignals` — loaded `word_signals.json`
- `yearInsights` — loaded `year_insights.json`
- `idx` — current month index (0–155)
- `sel` — currently selected topic id (`null` = none)
- `viewMode` — `'month'` | `'annual'`

### Main visualizations

- **Treemap** (`renderTm(idx)`) — D3 treemap showing topic share for the selected month; clicking a cell sets `sel`
- **Sparkline** (`renderSpark(tid, color)`) — D3 line chart of a topic's proportion over time; shown in the detail panel when a topic is selected
- **Macro chart** (`renderMacro()`) — D3 dual-axis line chart correlating macro indicators (IMACEC / unemployment) with selected topic proportion
- **Word cloud** (`renderCloud()`) — SVG word cloud for the selected topic's top words, driven by `word_signals`
- **Article cards** (`renderArts(tid)`) — DOM-built list of representative articles for the selected topic

### Bilingual support

All human-facing strings are defined in a `STRINGS` object with `en` / `es` keys. `setLang(lang)` swaps the active language and re-renders text nodes.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Personal academic/professional website for Fabio Fuentes, based on [Jon Barron's academic website template](https://jonbarron.info/). Static HTML/CSS site hosted on GitHub Pages at `fafa341.github.io`.

## Running Locally

No build step required. Serve the directory with any HTTP server:

```bash
python3 -m http.server 8000
```

Then open `http://localhost:8000` in a browser.

## Deploying

Push to the `master` branch on the remote (`https://github.com/fafa341/fafa341.github.io.git`). GitHub Pages automatically serves the updated site.

## Architecture

- `index.html` — main landing page (research profile, publications, projects)
- `about_me.html` — personal background and facts
- `stylesheet.css` — single global stylesheet (Google Fonts loaded via `@font-face`)
- `signal_noise_learnings.html` / `cfa_latam_learnings.html` — research-specific pages
- `data/` — CV PDFs and bibliography files
- `images/` — profile photos and project thumbnails
- `mipnerf/`, `mipnerf360/`, `zipnerf/` — self-contained research project showcase pages (each has its own HTML, CSS, and assets)

## Content Notes

- Profile picture should be placed at `images/FabioFuentes.jpg` (see `PROFILE_PICTURE_TODO.txt`)
- The site was previously on a custom domain; CNAME was removed in commit `3f70bd2`

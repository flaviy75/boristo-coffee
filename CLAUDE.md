# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static landing page **«Бористо презентует кофе»** — a single-file HTML/CSS site showcasing specialty coffee photos from a Telegram family chat export.

Live URL (Netlify): **https://boristo-coffee.netlify.app**
Live URL (GitHub Pages): **https://flaviy75.github.io/boristo-coffee/**
GitHub repo: `https://github.com/flaviy75/boristo-coffee`
Netlify site ID: `894b0449-b886-4f38-b94c-20f24d913ef0`

## Files

- `index.html` — deployed version (served by Netlify as root)
- `landing.html` — local development copy (identical to index.html, uses `./photos/` relative paths)
- `photos/` — 8 source photos (copied from Telegram export)
- `boristo-site.zip` — last deployment archive (`index.html` + `photos/`)

## Preview locally

Open `landing.html` directly in a browser — no server needed. Photos load via relative `./photos/` paths.

## Deploy to Netlify

Requires a Netlify personal access token. Redeploy steps:

```bash
# 1. Repack zip (run from project folder)
powershell -Command "Compress-Archive -Path 'index.html','photos' -DestinationPath 'boristo-site.zip' -Force"

# 2. Push to Netlify API
curl -X POST "https://api.netlify.com/api/v1/sites/894b0449-b886-4f38-b94c-20f24d913ef0/deploys" \
  -H "Authorization: Bearer TOKEN" \
  -H "Content-Type: application/zip" \
  --data-binary @boristo-site.zip
```

## Design system

CSS custom properties defined in `:root`:

| Variable    | Value     | Usage                        |
|-------------|-----------|------------------------------|
| `--bg`      | `#0d1b2a` | Page background              |
| `--surface` | `#162030` | Cards, intro, craft sections |
| `--gold`    | `#c9963a` | Accents, borders, labels     |
| `--gold-lt` | `#e8c06a` | Hover states, section titles |
| `--cream`   | `#f5e6c8` | Body text                    |
| `--muted`   | `#8a9bb0` | Secondary text               |

Fonts: `Cormorant Garamond` (headings) · `Inter` (body) — loaded from Google Fonts CDN.

## Photo manifest

Source: `C:/Users/Honor/Downloads/Telegram Desktop/ChatExport_2026-02-28/photos/`

| File | Used as |
|------|---------|
| `photo_4@24-12-2025_16-21-08.jpg` | Hero background + Latte card |
| `photo_47@08-01-2026_14-30-35.jpg` | Craft section (espresso prep) |
| `photo_48@08-01-2026_14-49-22.jpg` | Cappuccino card |
| `photo_50@11-01-2026_16-44-05.jpg` | Doppio card |
| `photo_56@16-01-2026_16-23-19.jpg` | Cortado card |
| `photo_57@18-01-2026_13-53-15.jpg` | Flat White card |
| `photo_58@18-01-2026_17-31-19.jpg` | (flavor notes card, not currently displayed) |
| `photo_107@18-02-2026_11-45-18.jpg` | Filter Shot card |

## Language

All user-facing text is in Russian. Code, comments, and CSS class names are in English.

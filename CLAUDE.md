# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A static HTML presentation deck showcasing the capabilities of **Bing Design Skill 1.2**. Used for stakeholder demos and team presentations. No build system — open `index.html` directly in a browser.

## Files

- `index.html` — Single-file interactive presentation (~2900 lines of HTML/CSS/JS). Contains all styles and scripts inline using the "Exceptional Horizons" design language. An older snapshot `index-20260317-234757.html` also exists.
- `*.png` / `*.jpeg` — Visual proof-of-concept screenshots embedded in the deck (card layouts, magazine templates, Figma references, input/output comparisons).

## Deck Structure

The deck has 9 sections, each a full-viewport slide (`min-height: 80vh`):

1. `#what-is-it` — Title / intro
2. `#whats-inside` — What's inside the skill
3. `#what-it-can-do` — Capabilities
4. `#scenarios` — Usage scenarios
5. `#case-study` — Case study
6. `#value` — Value proposition
7. `#tips` — Tips
8. `#get-started` — Getting started
9. `#future` — Future roadmap

Sections alternate light (`--c-cream`) / dark (`--c-taupe`) backgrounds via `section:nth-child(even)`. All content sits inside `.inner` wrappers capped at `960px`.

## Built-in Edit Panel

The deck includes an in-browser **Edit Panel** (slide-out drawer, bottom-right "Edit" button) that lets presenters tweak CSS variables, section height, font sizes, and content live. Key behaviors:
- Changes apply via inline CSS variable overrides on `<html>`
- "Download" exports a clean HTML snapshot (strips the edit panel, its styles, and JS before saving)
- "Reset" reloads the page to discard all changes
- The edit panel and its logic live at the end of the file (lines ~2125–2941)

## Deck Design Language

The presentation uses its own visual identity ("Exceptional Horizons"), separate from the Bing Design Skill tokens it showcases:

| Variable | Value | Purpose |
|----------|-------|---------|
| `--c-cream` | `#EBE8E3` | Light section background |
| `--c-taupe` | `#6B655F` | Dark section background (even sections) |
| `--c-moss` | `#2A3826` | Dark accent |
| `--c-black` | `#111111` | Primary text |
| `--c-white` | `#FFFFFF` | White text (dark sections) |
| `--f-sans` | Helvetica Neue | Body text |
| `--f-serif` | Times New Roman | Display/accent text |

## Relationship to Parent Skill

This deck presents the parent skill's capabilities. Supporting content lives in the sibling docs directory:

- `../deck-formal.md` — Formal slide outline (sections 1–9, some TODOs remain)
- `../deck-speaker-notes.md` — Speaker notes (Chinese/English)
- `../exceptional-horizons/` — Companion React+Vite app (`npm run dev` to start)

The parent skill (`bing-design-skill-1.2/`) contains the actual design system: tokens in `design-tokens/`, component specs in `references/`, icons in `icons/`.

## Editing Guidelines

- `index.html` is self-contained — all CSS, HTML, and JS are in one file. No external dependencies.
- When editing section content, maintain the alternating light/dark pattern and the `.inner` wrapper for consistent max-width.
- Dark-section overrides (text colors, card backgrounds, borders) are defined via `section:nth-child(even)` selectors — if you add or remove a section, all subsequent section colors shift. Verify the alternation after structural changes.
- Image assets are referenced by relative path from the HTML file.
- The Edit Panel block (HTML + `<style>` + `<script>`) is at the end of the file. Keep it last so the download/export logic can cleanly strip it.
- The parent `CLAUDE.md` (at `bing-design-skill-1.2/CLAUDE.md`) contains the authoritative rules for the design skill itself — particularly the constraint to never modify token names or values.

# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A single-file, self-animating HTML demo (`demo.html`) for client presentation. No build step, no dependencies — open directly in a browser. Simulates a conversation with "Sam", an AI city guide, ending with a Penthouse restaurant card and dossier sheet.

## Running the Demo

Open `demo.html` in Chrome or Safari (full screen recommended). The animation plays automatically on load. Refresh to replay.

## File Structure

```
demo.html                              — entire demo (HTML + CSS + JS in one file)
logo.png                               — Downtown Santa Monica circular teal logo (Sam's avatar)
explore-thingstodo-at-shore-hotel-...  — background beach photo (.jpeg and .webp)
stitch-assets/                         — reference Stitch design exports (source of truth for layout)
```

## Architecture

Everything lives in `demo.html`:

- **CSS** (lines 13–927): All layout, component styles, and keyframe animations inline in `<style>`
- **HTML** (lines 930–1141): Device chassis → phone frame → status bar → chat area → input bar → dossier overlay/sheet. The script tag is embedded inside `.phone` before closing.
- **JS** (lines 1142–1246): ~100 lines. `runDemo()` is an async function that orchestrates the sequence using `await delay(ms)`. `fadeIn`/`fadeOut` toggle CSS classes. `typeInto` types text char-by-char into the input field. `openDossier`/`closeDossier` add/remove `.open` class on the overlay and sheet.

### Animation sequence (in `runDemo()`)

1. Sam typing indicator fades in
2. Sam's greeting bubble slides in
3. User typing indicator + input typewriter effect
4. Send button pulse, user bubble appears, input clears
5. Typing indicator moved (DOM `appendChild`) below user message
6. Sam recommendation bubble slides in
7. Penthouse card springs in (spring cubic-bezier)
8. Holds — no loop

### Dossier sheet

Bottom sheet (91% height) positioned absolute inside `.phone`. Toggled by adding `.open` to `.dossier-overlay` and `.dossier-sheet`. Opened by clicking the card or "View Dossier" button; closed by tapping the overlay or the × button.

## Design Tokens

| Token | Value |
|---|---|
| Primary navy | `#203141` |
| Teal accent | `#6BC4BB` |
| Sand bg | `#F9FAFB` |
| Dossier navy | `#1E3A4C` |
| Gold | `#D4AF37` |
| User bubble | `#867d64` |
| Display font | Fraunces (Google Fonts) |
| Body font | Satoshi (Google Fonts) |
| Italic/quote font | Newsreader (Google Fonts) |

Phone screen background is `#203141` (same as navy) to prevent white corner bleed at the bezels.

## Key Patterns

- Message rows start `opacity: 0; transform: translateY(12px)` and transition on `.show` class
- Card uses spring easing: `cubic-bezier(0.34, 1.2, 0.64, 1)` for the pop-in
- Dossier sheet uses iOS-style easing: `cubic-bezier(0.32, 0.72, 0, 1)`
- Typing dots use CSS `animation: bounce` with staggered `animation-delay` per dot
- Images in the card and dossier are external Google-hosted URLs (lh3.googleusercontent.com)
- Map section uses a static image with an absolutely-positioned pin overlay — no live map API

# Sam — Client Demo

## Overview

A self-animating, single-file HTML demo built for client presentation. It simulates a conversation with **Sam**, an AI city guide, and walks through a full recommendation flow ending with a detailed venue card and dossier view. No user interaction is required — the demo plays itself.

---

## What We Built

### File
`demo.html` — fully self-contained, no build step, no dependencies to install. Open in any browser.

### Two Screens

**1. Chat Interface**
The primary view. A mobile phone frame (390×844px) centered on a dark background showing a live chat conversation with Sam.

**2. The Dossier — Detail View**
A bottom sheet that slides up over the chat when the Penthouse card is tapped. Shows the full venue profile.

---

## Animation Sequence

The demo plays automatically on page load:

| Step | What happens |
|------|--------------|
| 1 | Chat loads — phone frame and header visible |
| 2 | Sam's typing indicator appears (bouncing teal dots) |
| 3 | Sam's opening message slides in |
| 4 | User's reply types character-by-character into the input field |
| 5 | Message sends (button pulse, text clears, bubble appears) |
| 6 | Sam's typing indicator reappears — now below the user's message |
| 7 | Sam's recommendation text slides in |
| 8 | The Penthouse card springs in below Sam's message |
| — | Demo holds at this end state |

---

## The Penthouse Card

Appears in the chat as a rich recommendation card. Contains:
- Restaurant photo
- "Sam's Scoop" label
- Name, price range, cuisine, distance
- Insider tip quote
- "View Dossier →" button

Tapping the card or the button opens the full dossier.

---

## The Dossier (Bottom Sheet)

Slides up over the chat interface. Contains:
- Full-bleed hero image of the restaurant interior
- Title block: "The Penthouse" with price, category, distance
- Sam's Insider Scoop box with key tip
- Editorial description copy
- Features grid: Best For, Dress Code, Hours, Noise Level
- Static map with address pin
- Sticky "Reserve Table" CTA bar at bottom

Tap the overlay or the × button to dismiss.

---

## Design

| Property | Value |
|----------|-------|
| Primary (navy) | `#203141` |
| Teal accent | `#6BC4BB` |
| Background | `#F9FAFB` |
| Dossier navy | `#1E3A4C` |
| Gold accent | `#D4AF37` |
| Display font | Fraunces (serif) |
| Body font | Satoshi (sans-serif) |
| Italic/quote font | Newsreader (serif) |

---

## Source Designs

Built from two Stitch screens in the **Curated Concierge - PRD** project:

- `DTSM Concierge Desk - Branded Logo` — chat interface layout, header, card component
- `The Dossier (Detail View)` — bottom sheet layout, content structure, CTA bar

Reference files saved in `stitch-assets/`:
- `concierge-desk-branded-logo.html` / `.png`
- `dossier-detail-view.html` / `.png`

---

## How to Present

1. Open `demo.html` in Chrome or Safari — full screen recommended
2. The animation plays automatically
3. When the Penthouse card appears, tap **View Dossier** to show the full detail sheet
4. Tap the overlay to dismiss and return to the chat
5. Refresh the page to replay from the beginning

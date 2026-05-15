# Petition Project

## What This Is

A UK parliamentary petition campaign for mandatory disclosure of pesticide residues and processing aids on food labels.

**Petition URL:** https://petition.parliament.uk/petitions/754897  
**Petition number:** 754897  
**Deadline:** 6 August 2026  
**Targets:** 10,000 signatures (govt response) → 100,000 signatures (parliamentary debate)  
**Creator:** Michael (mjmonline1)

## Files

| File | Purpose |
|------|---------|
| `index.html` | Primary landing page — clean, modern, drives online traffic to sign |
| `h2.html` | Alternative landing page — more formal/authoritative tone |
| `Poster copy.html` | A4 printable poster — dark green, has real QR code SVG |
| `posterHighVis.html` | A4 printable poster — high-vis orange, has real QR code SVG |
| `poster2.html` | A4 printable poster variant |
| `high_impact.html` | Interactive color-scheme picker for poster — 12 schemes, JS-driven CSS vars, QR placeholder not filled |
| `high_impact_poster.html` | Another poster variant |
| `campaign_pack_petition.docx` | Full campaign pack (written by Claude in a prior session) |

## Campaign Pack Contents (campaign_pack_petition.docx)

- **Part 1: Social Media Pack** — ready-to-use posts for Facebook (5), X/Twitter (5), WhatsApp/Telegram (3), Instagram (2)
- **4-week content calendar** — Mon/Wed/Fri posting schedule
- **Part 2: Organisational Outreach Emails** — ready-to-send emails to:
  - PAN-UK (Pesticide Action Network)
  - Allergy UK
  - Soil Association
  - Which?
  - Local MP

## Key Message

Current UK food labelling law does not require full disclosure of pesticide residues or processing aids. Consumers — especially those with allergies — cannot make fully informed choices.

## Known Issues

- `Poster copy.html:356` — broken `</strong>` tag with no opening tag
- `high_impact.html` — QR placeholder says "QR CODE HERE", not filled (can't print functional poster)
- `h2.html` footer — `Created by Mi` looks like incomplete placeholder
- No `og:` meta tags on landing pages (social sharing has no preview)
- README.md is empty

## Assets

- QR code SVG is embedded inline in `Poster copy.html` and `posterHighVis.html`
- Parliament SVG/PNG (`parliament.svg`, `parliament.png`) available
- Logo PNGs: `Transparent_Food_Labelling-1024.png/jpeg`, `Straight_Code_Format-1024.png/jpeg`
- PDFs: `PosterOriginal.pdf`, `posterHighVis.pdf`, `Straight_Code_Format-210.pdf`, `Transparent_Food_Labelling-210.pdf`
- `organisations interested in reducing use of pesticides in uk.json` — target org list

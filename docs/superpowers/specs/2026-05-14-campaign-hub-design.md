# Campaign Hub Landing Page — Design Spec

**Date:** 2026-05-14  
**File:** `index.html` (replaces existing; backup to `index-old.html`)  
**Project:** UK Parliamentary Petition #754897 — mandatory pesticide/processing aid disclosure on food labels

---

## Goal

Replace the current `index.html` with a richer campaign hub that:
- Convinces anyone — regardless of diet or politics — to sign the petition
- Shows why the issue is urgent using live news coverage
- Drives signatures with maximum CTA force
- Points people to external resources to do their own research

---

## Tone & Framing

**Rights-based and non-partisan.** The page never implies the reader should eat organic, avoid supermarkets, or hold any particular political view. The single message is: *you have the right to know what is in your food, regardless of what you choose to do with that information.*

Copy avoids: "toxic", "poison", "big agriculture", organic/activist framing.  
Copy uses: "right to know", "transparency", "informed choice", "consumers", "everyone".

---

## Page Architecture

Pure static HTML/CSS/JS — single file, no build step, no server. Consistent with existing project design system (Inter font, `#10B981` green, dark hero, card-based layout).

---

## Sections (top to bottom)

### 1. Sticky Bar
- Fixed to top of viewport at all scroll positions
- Contains: brief label ("UK Petition #754897") + **"Sign the petition →"** button
- Collapses on mobile to just the button
- Disappears only if user has already clicked through (optional: sessionStorage flag)

### 2. Nav Bar
- Logo/wordmark: "Know What's In Your Food"
- Same "Sign the petition →" button, right-aligned

### 3. Hero
- Dark green gradient background (`#064e3b` → `#111827`)
- Eyebrow: `UK PARLIAMENTARY PETITION #754897`
- Headline: **"You have the right to know what's in your food."**
- Subheading: plain English, 2 sentences max — what the petition asks for and why it matters to everyone
- Primary CTA button: `✍ Sign Now — It takes 30 seconds`
- Trust signals below button: `✓ Free  ✓ 30 seconds  ✓ UK residents`
- Deadline callout: `Deadline: 6 August 2026`
- Progress bar: labelled "Progress toward 100,000 signatures" — static visual, bar width hardcoded at `6%` as starting point (update manually as signatures grow; no live API)

### 4. Bulletin Board — "Pesticides in the News"
- Section label: `📰 Latest` + `● Live feed` badge
- Card grid (2 columns desktop, 1 column mobile)
- **Seeded articles** (always present, hardcoded):
  1. The Guardian, May 2026 — "Typical English roast dinner potentially drenched in 102 pesticides, says report" — https://www.theguardian.com/environment/2026/may/14/typical-english-roast-dinner-potentially-drenched-in-102-pesticides-says-report
  2. The Independent — "Supermarket pesticides on fruit and vegetables linked to cancer risk" — https://www.independent.co.uk/news/health/supermarket-pesticides-fruit-vegetables-cancer-b2925216.html
- **Live RSS fetch** on page load:
  - Source: Google News RSS — `https://news.google.com/rss/search?q=pesticide+food+UK&hl=en-GB&gl=GB&ceid=GB:en`
  - Proxy: `https://api.rss2json.com/v1/api.json?rss_url=` (free tier) — Google News URL must be URL-encoded in the query string
  - Fetched articles prepended before seeded articles, max 8 total displayed
  - Graceful fallback: if fetch fails or times out (3s), show seeded articles only with no error state visible to user

### 5. Why This Matters
- Section label: `The problem`
- Headline: "Why this matters to everyone"
- 4 stat callouts in 2×2 grid:
  - `320+` — pesticide residues legally permitted on UK food
  - `0` — required to be listed on your food label
  - `1 in 4` — UK adults have a diagnosed food sensitivity
  - `£0` — estimated cost to food industry to add disclosure to labels
- 2–3 sentences of rights-framed copy: "Whether you shop at Waitrose or Lidl…"

### 6. Mid-page CTA
- Full-width dark green band
- Headline: "Convinced? It takes 30 seconds."
- Large sign button + trust signals repeated

### 7. External Resources — "Do your own research"
- Section headline: "Trusted sources — make up your own mind"
- Card grid of organisations with name, one-line description, and external link:
  - PAN-UK (Pesticide Action Network UK)
  - Food Standards Agency — official UK pesticide monitoring data
  - Which? — consumer research on food labelling
  - Soil Association — organic and food standards research
  - EWG (Environmental Working Group) — pesticide residue databases
- Framing: explicitly neutral — "We're not telling you what to think. Here's where to look."

### 8. Share Strip
- Dark green background
- Headline: "Help spread the word"
- Share buttons: Facebook, X/Twitter, WhatsApp
- Each pre-fills a share message linking back to the page

### 9. Footer CTA + Details
- Final "Sign the petition →" button
- Petition URL, number, deadline
- "Created by Michael Martin"

---

## CTA Strategy

All three approaches combined:

| Approach | Implementation |
|---|---|
| **Sticky bar** | Fixed top bar visible at all scroll positions |
| **Deadline + progress bar** | In hero section |
| **Repeated CTAs + trust signals** | Hero, mid-page band, footer |

---

## News Feed Implementation

```
Page loads
  → fetch('https://api.rss2json.com/v1/api.json?rss_url=https://news.google.com/rss/search?q=pesticide+food+UK...')
  → on success: parse items, prepend up to 6 cards before seeded 2
  → on fail/timeout (3s): show seeded cards only, no error message
  → max 8 cards rendered total
  → each card: source name, title (truncated to 2 lines), date, "Read article →" link
```

---

## Out of Scope

- No live signature count (Parliament API is not publicly queryable in real-time)
- No comment section or user accounts
- No email capture / newsletter signup
- No server-side rendering

---

## Files

| Action | File |
|---|---|
| Back up | `index.html` → `index-old.html` |
| Create/replace | `index.html` |

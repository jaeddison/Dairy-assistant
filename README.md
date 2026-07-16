# 🐄 DA — Dairy Assistant

A mobile-first farm management app for D1, Driffield Farming Ltd. Runs in the browser, backed by Firebase for real-time cloud sync across authenticated users.

**Live app:** [jaeddison.github.io/Dairy-assistant](https://jaeddison.github.io/Dairy-assistant/)

---

## Features

### Bays
Tap any bay to update its headcount via a popup. Running total across all six bays and the penicillin paddock displayed at a glance.

### Dry Cow
Dry cow treatments and meat withholding register. Sorted by clearance date with colour-coded status badges (green = cleared, amber = within 7 days, red = further out).

### Lame
Lame cow register with multi-select foot codes (Left Front, Right Front, Left Rear, Right Rear). Two-tap confirmation to mark as treated — first tap shows "Treated?" in amber, second tap confirms and moves to the archive. Full treated and cleared archive below the active list.

### Calving
Two-stage calving workflow:

**Watch List** — cows to monitor before calving. Select a bay (persists between entries), select a status (Calving / Close / Other), type a tag number, tap Add. List grouped by bay with colour-coded status badges. Move any cow to the Calved list when she calves.

**Calved List** — active calving records. Cows arrive from the Watch List (bay carries across automatically) or can be added directly. For each cow: select sex (H/B), select calf type (Keeper/Hereford for heifers, Bobby/Hereford for bulls), assign a keeper tag (1–350, used tags drop off the picker). Once complete, move cow to Fresh Cows tab. Calved list persists as a season record until manually cleared.

**Calving History** — below the calved list, grouped by date (NZ time), collapsed by default. Each day shows a compact summary (e.g. "Sat 16 Jul — 12 cows · 6K · 4B · 2HF"). Tap to expand full individual records.

### Fresh Cows
Five-group calving pipeline, all with individual tag tracking and grazing calculators:
- **New Moms** — batch tag entry, dated
- **Colostrum Mob** — days counter with amber (3d) and red (5d+) alerts, sorted longest first. Exit buttons: Herd / OAD / Peno
- **Milking Herd** — batch entry, grazing calculator
- **OAD** — batch entry, grazing calculator
- **Peno** — batch entry, grazing calculator

No duplicate tags across any group — entering a tag into any group removes it from wherever it was previously.

Grazing calculator on each group: enter m² per cow, displays total area in m² and hectares for that mob's current headcount.

### Export / Import
Full data export with a `DAIRY_IMPORT:` JSON code for sharing with Claude. Paste back in the Import box to restore or update data. Import code must use straight quotes — not curly/smart quotes.

---

## Access

Sign in with email and password. Contact James to be set up with an account.

Data is stored in Firebase Firestore and syncs in real time across all signed-in devices. A green dot in the header confirms live connection.

---

## Repository files

| File | Purpose |
|------|---------|
| `index.html` | The app — upload this to update |
| `dairy-test.html` | Local test version (no login, localStorage) |
| `icon.png` | Home screen / browser tab icon |
| `README.md` | This file |

---

## Updating the app

1. Upload new `index.html` to GitHub
2. Wait 2–3 minutes for GitHub Pages to rebuild
3. Force-refresh Edge on your phone if the old version is cached

---

## Technical notes

- Single HTML file, no build step, no dependencies beyond Firebase SDK and Google Fonts
- Firebase project: `calf-assistant`
- Firestore paths: `dairy/D1` (main data), `dairy/D1-graze` (grazing calculator values)
- `_receivingSnapshot` flag prevents write feedback loops on Firestore listeners
- All dates recorded in NZ local time (Pacific/Auckland)
- Keeper tag pool: 1–350, used tags tracked in `usedKeeperTags` array

---

© 2026 James Eddison. All rights reserved.

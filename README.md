# 🐄 DA — Dairy Assistant

A mobile-first farm management app for dairy operations. Runs entirely in the browser with no server, no login, and no installation required.

**Live app:** [jaeddison.github.io/Dairy-assistant](https://jaeddison.github.io/Dairy-assistant/)

---

## Features

**Bays** — Tap any bay to update headcount. Running total across all bays including penicillin paddock.

**Dry Cow** — Dry cow treatments and meat withholding register. Sorted by clearance date with colour-coded status badges.

**Lame** — Lame cow register with multi-select foot codes (LF, RF, LR, RR). Two-tap confirmation to mark as treated and archive.

**Calving** — Full calving pipeline:
- New Moms (batch entry, dated)
- Colostrum Mob (days counter, alerts at 3d and 5d+, exit to Herd / OAD / Peno)
- Milking Herd, OAD, and Peno (batch entry, no duplicates across groups)
- Grazing calculator (m² per cow → total area in m² and ha) on all five groups

**Export / Import** — Full data export with a DAIRY_IMPORT code for sharing with Claude. Auto-snapshot before every import with 5-snapshot rollback history.

---

## Usage

Open the app in **Microsoft Edge** on iPhone and use Edge's Add to Home Screen option to create a home screen icon.

Data is stored in Edge's localStorage. Always use the same browser — data does not sync between browsers.

**Do not clear Edge's browsing data** without exporting first.

---

## Repository files

| File | Purpose |
|------|---------|
| `index.html` | The app itself — upload this to update the app |
| `icon.png` | Home screen / browser tab icon |
| `README.md` | This file |

---

## Export / Import workflow

1. Tap **Export** tab → **Copy Export to Clipboard**
2. Paste into Claude (Dairy Assistant development conversation) with any instructions
3. Claude returns a `DAIRY_IMPORT:` code
4. Paste into the **Import** box → tap **Load**

A snapshot is saved automatically before every import. Use the **Snapshots** section to roll back if needed.

---

## Updating the app

When a new version of `index.html` is available:
1. Go to the repository on GitHub
2. Click `index.html` → edit (pencil icon) or upload new file
3. Commit changes
4. Wait 2–3 minutes for GitHub Pages to rebuild
5. Force-refresh Edge on your phone if the old version appears cached

---

## Technical notes

- Single HTML file, no dependencies, no build step
- Data stored in browser localStorage under key `dairy-v4`
- Grazing calculator values stored separately under `dairy-graze-v4`
- Snapshots stored under `dairy-snapshots-v4`
- Import parser accepts bare JSON or `DAIRY_IMPORT:` prefixed blobs, with straight quotes only

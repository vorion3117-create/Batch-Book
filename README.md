# Batch Book — Vorion Industries and Chemicals

Daily production log for Vorion: raw materials, output, labour, costs, stock, job work and reports.

This app is **completely separate from the EMR Batch Book** — its own GitHub account/repo,
its own Firebase database, its own passwords. Nothing is shared or linked.

## Default passwords (change them in Settings on day one)
- Admin: `vorion@admin2026`
- Team:  `vorion@team2026`

## One-time setup

### 1. New GitHub account (separate from abdull3117)
1. Sign out of GitHub (or use a private browser window).
2. Sign up at https://github.com/signup with a **Vorion email** (not the EMR/personal one).
3. Create a new **public** repository named `batch-book`.
4. Click **"uploading an existing file"**, drag in all files from this folder
   (`index.html`, `app.js`, `style.css`, `firebase-config.js`, `logo.svg`, `firestore.rules`, `README.md`), and commit.
5. Repo → **Settings → Pages** → Source: *Deploy from a branch* → Branch `main`, folder `/ (root)` → Save.
   After ~1 minute the app is live at `https://<new-username>.github.io/batch-book/`.

### 2. New Firebase project (separate database)
1. Go to https://console.firebase.google.com signed in with the **Vorion Google account**.
2. **Add project** → name it `vorion-batch-book` (Google Analytics not needed).
3. **Build → Firestore Database → Create database** → location `asia-south1 (Mumbai)` → Production mode.
4. Firestore → **Rules** tab → replace everything with the contents of `firestore.rules` → **Publish**.
5. **Project settings (gear) → Your apps → Web (</>)** → register app "Vorion Batch Book".
   Copy the `firebaseConfig` values into `firebase-config.js` in the GitHub repo (edit the file on GitHub, commit).
6. Open the app link. The status pill should change from "Preview — not saving" to **Live**.

### 3. First use
1. Log in as admin → **Settings** → change both passwords.
2. Add Vorion's raw materials and rates, then its products.
3. Set operator/loadman wages and the processing-cost breakdown.
4. (Optional) Job Work tab → add any contract-manufacturing customers.
5. Replace `logo.svg` with Vorion's real logo when ready (keep the same file name, or update `index.html`).

## Deploying changes later
GitHub Pages caches files for ~10 minutes. In `index.html`, bump the `?v=` number on
`app.js`, `style.css`, `firebase-config.js` and the logo every time you change them.

## Optional: Google Sheet copy
To mirror every batch into a Google Sheet, create an Apps Script Web App in the Vorion Google
account and paste its URL into `SHEETS_SYNC_URL` near the top of `app.js`. Left empty by default.

# Talent Directory

A searchable talent directory that syncs live from Google Sheets.

## Files

| File | Purpose |
|---|---|
| `index.html` | The web app — upload this to GitHub Pages |
| `google-apps-script.js` | Paste this into your Google Sheet to create a live data API |

---

## Setup (one time, ~5 minutes)

### Step 1 — Set up the Google Apps Script

1. Open your Google Sheet
2. Go to **Extensions > Apps Script**
3. Delete any existing code in the editor
4. Copy the entire contents of `google-apps-script.js` and paste it in
5. On **line 8**, change `"Talents"` to the exact name of your sheet tab
6. Click the **Save** icon (floppy disk)
7. Click **Deploy > New deployment**
8. Click the gear icon next to "Select type" and choose **Web app**
9. Set **Execute as**: Me
10. Set **Who has access**: Anyone
11. Click **Deploy**, then **Authorize access**, then **Allow**
12. Copy the **Web app URL** that appears

### Step 2 — Add the URL to index.html

1. Open `index.html` in a text editor
2. Find this line near the top of the `<script>` section:
   ```js
   const APPS_SCRIPT_URL = "";
   ```
3. Paste your Web app URL between the quotes:
   ```js
   const APPS_SCRIPT_URL = "https://script.google.com/macros/s/YOUR_ID/exec";
   ```
4. Save the file

### Step 3 — Deploy to GitHub Pages

1. Create a new GitHub repository (can be private)
2. Upload `index.html` to the repository
3. Go to **Settings > Pages**
4. Under **Source**, select **Deploy from a branch**
5. Choose **main** branch and **/ (root)** folder
6. Click **Save**
7. Your site will be live at `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME`

Share that URL with your team — they can bookmark it and always see the latest talent data.

---

## How it works

```
Google Sheet  →  Apps Script (Web App)  →  index.html  →  Your team
    ↑                                            |
    └──────── Update anytime ────────────────────┘
                                    (auto-refreshes every 5 min)
```

- The page auto-syncs every **5 minutes** while open
- Team members can also click **Sync sheet** to refresh manually
- Any edits you make to the Google Sheet are reflected on the next sync

---

## Columns expected in your sheet

| Column | Notes |
|---|---|
| Talent Name | Required |
| Location | |
| Source | e.g. Contra, Behance, LinkedIn |
| Profile | Full URL to their portfolio |
| Rate | e.g. $50/hr |
| Title | Their role/specialty |
| Status | e.g. Available, Sent inquiry |
| LinkedIn | URL or username |
| Email | |
| Referred | Who referred them |
| Notes | Any notes you've added |
| Type | e.g. Freelancer, Contractor |
| Rating (1-5) | Displays as stars |

Column order doesn't matter — the app reads your header row to find them.

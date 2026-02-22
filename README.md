# 🏋️ FitJourney — 90-Day Fitness Tracker

**Your personal fitness tracker — web app + Google Sheets dashboard.**

Live URL (after setup): `https://swatt12345.github.io/fitness-tracker`

---

## What This Does

- **Web app** (this repo) — your daily mobile input interface
- **Google Apps Script** — the bridge that sends data to Google Sheets in real time
- **Google Sheet** — stores all your data and auto-generates a dashboard

Every time you submit data on your phone → it writes instantly to your Google Sheet → dashboard updates automatically.

---

## Files in This Repo

| File | Purpose |
|---|---|
| `index.html` | The complete web app — open this on your phone |
| `Code.gs` | Paste this into Google Apps Script |
| `README.md` | This setup guide |

---

## ONE-TIME SETUP — Follow This Exactly

### Step 1 — Upload to GitHub

1. Go to [github.com](https://github.com) and create repo named `fitness-tracker`
2. Upload `index.html` and `README.md` into the repo
3. Go to **Settings → Pages → Source: Deploy from branch → Branch: main → / (root)**
4. Click **Save**
5. Your app is live at `https://swatt12345.github.io/fitness-tracker`

> ⏱ GitHub Pages can take 2-5 minutes to go live after first deploy.

---

### Step 2 — Set Up Google Apps Script

**This connects your web app to Google Sheets. Do this carefully.**

#### 2a. Open Apps Script

1. Go to your Google Sheet:
   `https://docs.google.com/spreadsheets/d/1cG5KPRRvXXBG8t7-2u1cQkzABc9BAGAGF_hECAmM8xU`
2. Click **Extensions** (top menu) → **Apps Script**
3. A new tab opens — this is the script editor

#### 2b. Paste the Script

1. **Select all** the default code in the editor (Ctrl+A or Cmd+A)
2. **Delete** it
3. **Paste** the entire contents of `Code.gs`
4. Click the **Save** button (💾 icon or Ctrl+S)
5. Name the project: `FitJourney` → click **OK**

#### 2c. Initialize Your Sheets

1. In the toolbar, find the function dropdown (it says `Select function` or shows a function name)
2. Click it and select **`initializeSheets`**
3. Click the **▶ Run** button
4. First time: Google will ask you to **Authorize** — click through:
   - Click **Review permissions**
   - Choose your Google account
   - Click **Advanced** → **Go to FitJourney (unsafe)**
   - Click **Allow**
5. This creates all 7 sheets with correct headers and builds your dashboard

> ✅ Check your Google Sheet — you should now see tabs: Dashboard, Sessions, Weight Log, Nutrition, Measurements, PR Log, Boss Battle

#### 2d. Deploy as Web App

1. Click **Deploy** button (top right) → **New deployment**
2. Click the **gear icon** ⚙️ next to "Select type" → choose **Web app**
3. Fill in:
   - **Description:** `FitJourney API`
   - **Execute as:** `Me`
   - **Who has access:** `Anyone` ← **This must be "Anyone"**
4. Click **Deploy**
5. Google asks to authorize again — click **Authorize access** → follow same steps as above
6. **Copy the Web app URL** — it looks like:
   `https://script.google.com/macros/s/AKfycbXXXXXXXXXXXXXX/exec`
7. **Keep this URL — you need it for Step 3**

---

### Step 3 — Connect Web App to Google Sheets

1. Open `index.html` in a text editor (Notepad, VS Code, etc.)
2. Find this line near the top of the `<script>` section:
   ```javascript
   const SCRIPT_URL = 'PASTE_YOUR_APPS_SCRIPT_URL_HERE';
   ```
3. Replace `PASTE_YOUR_APPS_SCRIPT_URL_HERE` with your actual URL:
   ```javascript
   const SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbXXXXXXXXXXXXXX/exec';
   ```
4. Save the file
5. **Upload the updated `index.html` to your GitHub repo** (replace the old one)

---

### Step 4 — Test It Works

1. Open `https://swatt12345.github.io/fitness-tracker` on your phone
2. Tap **Log Weight**
3. Enter `70.0` and tap **LOG WEIGHT ✓**
4. The loading spinner appears → disappears → toast says "⚖️ Weight logged!"
5. Go to your Google Sheet → **Weight Log** tab → you should see a new row

**If it works → setup complete. 🎉**

---

## If Something Goes Wrong

| Problem | Fix |
|---|---|
| Data doesn't appear in sheet | Check the SCRIPT_URL is correctly pasted in index.html — no spaces, full URL |
| "Access denied" error | Redeploy: Deploy → Manage deployments → Edit → Who has access: Anyone → Update |
| Sheets not created | Go to Apps Script → select `initializeSheets` → Run again |
| App shows blank / won't load | Check GitHub Pages is enabled in Settings → Pages |
| Changes to Code.gs not working | Must create a **New deployment** — editing and saving doesn't update the live version |

---

## Updating the Apps Script (If Needed)

⚠️ Important: After editing `Code.gs`, you **cannot** just save — you must redeploy:

1. Apps Script → **Deploy** → **Manage deployments**
2. Click the **Edit** icon (pencil) on your deployment
3. Change version to **New version**
4. Click **Deploy**
5. Copy the **new URL** and update `index.html` if it changed

---

## Set Up Daily Auto-Refresh (Optional but Recommended)

Makes your Dashboard update automatically every morning:

1. Apps Script → **Triggers** (clock icon on left sidebar)
2. Click **+ Add Trigger** (bottom right)
3. Settings:
   - Function: `scheduledDailyRefresh`
   - Event source: `Time-driven`
   - Type: `Day timer`
   - Time: `6am to 7am`
4. Click **Save**

---

## Your Daily Workflow

| Time | Action |
|---|---|
| 6:00 AM | Open app → **Log Session** during/after workout |
| Morning | **Log Weight** (every other day) |
| Noon | **Log Nutrition → Lunch** |
| Evening | Complete nutrition log |
| Weekly | Open Google Sheet dashboard for full review |
| Every 2 weeks | **Log Measurements** |

---

## Your Program Details

- **Start:** February 23, 2026
- **Goal:** Muscle gain primary · 6kg fat loss secondary
- **Duration:** 90 days (3 months)
- **Schedule:** Mon–Sat 6 AM · Sunday full rest
- **Friday:** WFH extended session (90 min)

---

## XP System

| Action | XP |
|---|---|
| Complete a session | +10 XP |
| Log weight | +5 XP |
| Log nutrition | +5 XP |
| Log measurements | +10 XP |
| New PR | +15 XP |
| Unlock a badge | +20 XP |
| Complete weekly challenge | +50 XP |
| Boss Battle | +100 XP |

| Level | XP Required | Title |
|---|---|---|
| 1 | 0–99 | 🌱 Beginner |
| 2 | 100–249 | 💪 Trainee |
| 3 | 250–449 | 🔥 Committed |
| 4 | 450–699 | ⚡ Athlete |
| 5 | 700–999 | 🏆 Champion |
| 6 | 1000+ | 👑 Elite |

---

*Built for Swatt12345 · 90-Day Body Recomposition Program · Feb 2026*

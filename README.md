# 💰 Budget Tracker

A clean, zero-dependency static web app that tells you in real time whether you are **over** or **under** your monthly budget — and by exactly how much.

Built with plain **HTML + CSS + JavaScript**. No frameworks, no installs, no build step. One file. Open it in a browser and it works.

---

## 🌐 Live Demo

> Hosted on GitHub Pages:  
> [View the Live Site](https://muhammadtalhapawa.github.io/budget-tracker-under-over-budget/)

---

## 📸 Overview

The app takes three inputs from you:

| Input | Description |
|---|---|
| **Total Monthly Budget** | The full amount you have budgeted for the entire month |
| **Amount Spent So Far** | The total you have actually spent up to today |
| **Current Day of Month** | Which day of the month it currently is (1 to 31) |

It then calculates how much you *should* have spent by today based on an even daily distribution, compares it against what you *actually* spent, and gives you one clear verdict:

- 🟢 **UNDER BUDGET** — you have `$X` left to spend within budget
- 🔴 **OVER BUDGET** — you have exceeded your budget by `$X`

---

## 🧮 How the Calculation Works

The app assumes your budget is spread evenly across 31 days.

```
Daily Budget     = Total Monthly Budget ÷ 31
Allowed by Today = Daily Budget × Current Day
Difference       = Allowed by Today − Amount Spent So Far
```

**If Difference ≥ 0** → You are under budget. The difference is how much more you can still spend while staying on track.

**If Difference < 0** → You are over budget. The absolute value of the difference is how much you have overspent relative to where you should be today.

### Example

| Field | Value |
|---|---|
| Monthly Budget | $3,000 |
| Current Day | Day 10 |
| Daily Budget | $3,000 ÷ 31 = **$96.77/day** |
| Allowed by Day 10 | $96.77 × 10 = **$967.74** |
| Spent So Far | $800 |
| **Result** | **UNDER BUDGET by $167** |

---

## 📊 What the Dashboard Shows

### Main Verdict
The large number in the centre is the most important output — the dollar amount by which you are either over or under budget, color-coded green or red.

### Mini Stats Row
Three smaller tiles show supporting information:

- **Allowed by Today** — the cumulative budget up to the current day
- **Spent So Far** — your input, reflected back for reference
- **Daily Budget** — your even daily allowance based on the monthly total

### Progress Bar
A horizontal bar shows what percentage of your **total monthly budget** has been consumed. It turns red if you have spent more than 100% of the monthly total.

---

## 🗂 File Structure

```
budget-tracker/
└── index.html        ← The entire app. That's it.
```

There are no other files required. No `package.json`, no `node_modules`, no build output.

---

## 🚀 Hosting on GitHub Pages (Step by Step)

### Step 1 — Create the Repository
1. Go to [github.com](https://github.com) and sign in
2. Click the **+** icon → **New repository**
3. Name it `budget-tracker`
4. Set visibility to **Public**
5. Click **Create repository**

### Step 2 — Upload the File
1. Inside the new repository, click **Add file** → **Upload files**
2. Drag and drop `index.html` into the upload area
3. Scroll down and click **Commit changes**

### Step 3 — Enable GitHub Pages
1. Go to the repository **Settings** tab
2. Scroll down to the **Pages** section in the left sidebar
3. Under **Source**, select **Deploy from a branch**
4. Set branch to `main` and folder to `/ (root)`
5. Click **Save**

### Step 4 — Access Your Site
After about 60 seconds, your app will be live at:

```
https://yourusername.github.io/budget-tracker
```

> Replace `yourusername` with your actual GitHub username.

---

## 🛠 Running Locally

No server needed. Just open the file directly:

**macOS / Linux**
```bash
open index.html
```

**Windows**
```bash
start index.html
```

Or simply double-click `index.html` in your file explorer.

---

## 🎨 Design Details

| Property | Value |
|---|---|
| Theme | Dark — deep navy background |
| Accent Color | Warm gold (`#e8a830`) |
| Under Budget Color | Emerald green (`#32d983`) |
| Over Budget Color | Soft red (`#f05050`) |
| Display Font | DM Serif Display (Google Fonts) |
| Mono Font | DM Mono (Google Fonts) |
| Background Texture | Subtle gold grid overlay |
| Animations | Fade-up entrance, smooth color transitions, animated progress bar |

All fonts are loaded from Google Fonts CDN. The app requires an internet connection on first load to fetch the fonts; after that the browser caches them.

---

## ⚙️ Customisation

All styling variables are defined at the top of the `<style>` block in `index.html` using CSS custom properties:

```css
:root {
  --bg:       #0c0f14;   /* page background */
  --surface:  #13181f;   /* card background */
  --border:   #1e2530;   /* card borders */
  --gold:     #e8a830;   /* primary accent */
  --green:    #32d983;   /* under budget */
  --red:      #f05050;   /* over budget */
}
```

To change the colour scheme, update these six variables and the rest of the UI adapts automatically.

To change the **number of days in the month**, find this line in the `<script>` block:

```js
const dailyBudget = total / 31;
```

Change `31` to `28`, `29`, `30`, or `31` depending on the month.

---

## 🔒 Privacy

This app runs **entirely in your browser**. No data is sent to any server. No analytics, no tracking, no cookies. Your budget numbers never leave your device.

---

## 📄 License

MIT — free to use, modify, and distribute.

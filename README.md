# Scale & Kill Tool

Decide which Facebook / Meta ads to scale or kill, from an Ads Manager export.

Open `index.html` in a browser — it is a single self-contained file, nothing
is uploaded to a server. Your pasted / uploaded data stays in your browser.

## What it looks like

![Scale & Kill charts — Chart 1 spend vs new-customer CPA with the 90% scale/kill curves, and Chart 2 CPMr vs CPA split into four quadrants](docs/scale-kill-charts.png)

Screenshot of the tool running on its sample data (139 ads), with the
target CPA dragged to $100 — Scale 74 / Test 64 / Kill 1, medians
CPMr $22 and CPA $55. Drag the target handle and both charts, the
counts and the verdicts update live.

## Set it live — do this once

GitHub Pages is **not** on by default. Until you do these steps, the
live link below will show a 404.

1. On this repo page, click **Settings** (top right).
2. In the left menu, click **Pages**.
3. Under "Build and deployment", set **Source** to **Deploy from a branch**.
4. Set **Branch** to **main** and folder to **/** (root), then click **Save**.
5. Wait 1–2 minutes, then open the live site:

   **https://athyyna.github.io/scale-kill-ads-automation-tool/**

If you push a new version of `index.html` later, the live site updates
automatically — no need to repeat these steps.

## Download the HTML

- **From this repo:** open `index.html` here on GitHub, click the
  **Raw** button, then save the page — or click **Code > Download ZIP**
  and open `index.html` from the unzipped folder. Double-clicking
  `index.html` on your computer opens the tool offline.
- **From Muse:** the same file is the exported Scale & Kill artifact,
  `scale-kill-tool.html`, and the Muse public link is
  https://muse.ai/s/scale-kill-tool-xjf6xp0xi0b0xv1/-2Jw2Uu-lz9VeqxGoyviFIG57gBvl4rh-Ac-D1iS5Bk
  (note: that Muse link may lag behind this repo after later edits —
  this repo is the up-to-date copy).

## What it does

**Chart 1 — Scale & Kill:** each dot is an ad, spend (log scale) vs
new-customer CPA. Above the red curve the ad is 90% sure not to reach the
target CPA (kill); below the green curve it is 90% sure to beat target CPA
(scale). Both curves pinch toward the target as spend rises, so an $80 CPA
on a $50 target is still "testing" at $200 spend but becomes a "kill" at
$2,000 spend.

**Chart 2 — CPMr vs CPA:** CPMr is the cost to reach 1,000 people
(Spend ÷ Reach × 1,000). Bubbles are sized by reach and split at the
account medians into Efficient growth, Reach play, Precision, and
Kill candidate.

**Combined verdicts:** Scale + Efficient growth = scale aggressively;
Scale + Precision = scale at the normal 5–15% pace; Kill + Reach play =
bump target CPA 10–20% first, with about a 2-week grace period;
Kill + Kill candidate = cut quickly.

## Inputs

One row per ad, same date range and currency for every ad:

- Ad name, Spend, New customers (the count, not just CPA), Reach,
  Impressions, Days, plus target new-customer CPA.

Load data by uploading a CSV / TSV file, loading from a Google Sheet
(the sheet must be "Anyone with the link > Viewer"), or pasting CSV text.
A CSV template download is built into the tool.

Important: Ads Manager has no native "new customer CPA" column. You need
a true new-customer conversion definition (for example a first-purchase
custom conversion, or offline / CRM conversions with a new-customer flag).
Using total Purchases as a proxy gives blended CPA, not new-customer CPA.

## Target CPA

The target is a draggable handle on Chart 1, synced with a typed box at
the top of the page and a box on Chart 1 itself. Changing it
recalculates both curves and the Scale / Test / Kill counts live.
Sample data (139 ads) is included: at a $50 target it reads
Scale 18 / Test 103 / Kill 18; at $64, Scale 30 / Test 104 / Kill 5.

## Run it

Open `index.html` directly, or use the live site once GitHub Pages is
enabled — see "Set it live" at the top of this page.

# RA2 Ladder Playtime

See how much time you play **Red Alert 2 on [Chrono Divide](https://ladder.chronodivide.com)** every day, per account, region and game mode.

It's plain HTML, CSS and JavaScript with no build step, no server and nothing to install. Open `index.html` in a browser and it works.

```
index.html      page layout
css/style.css   styles (light and dark theme)
js/app.js       fetching, storage, chart and tables
favicon.ico
.env.example    template for your account list
```

## How it works

The page reads your ranked games from the same public API the ladder site uses:

| Region | Code | API |
|---|---|---|
| South-East Asia | `sea` | `https://wol-sea.chronodivide.com` |
| America & Europe | `am-eu` | `https://wol-eu.chronodivide.com` |

One request per account returns both **1v1** and **2v2-random** games, with each game's start time and duration. Each game counts toward the day it **started** (in your local time zone).

## Usage

1. Copy `.env.example` to `.env` and list your accounts:
   ```env
   SEA_ACCOUNTS=Bermawy
   AMEU_ACCOUNTS=Bermawy,Holako_Khan
   ```
2. Open `index.html` in any modern browser (double-click it).
3. Open **Accounts (.env)**, click **Load .env file** and pick your `.env`. You can also paste its contents and click **Save accounts**. A browser can't read a file by itself, so you pick it once and the page remembers it.
4. Click **Refresh from ladder**. After the first run, the page refreshes on its own each time you open it and fetches only new games.
5. Use the filters to look at a date range, account, region or mode. **Color by** splits the daily bars by account, region, mode, or all three.

## Keeping your data

- The page stores every game it fetches in browser storage (`localStorage`), so it's still there next time you open the file.
- The ladder API only keeps about two months of history. Click **Save data file** now and then to write everything to `ra2-playtime-data.json`.
  - In Chrome and Edge, the page asks once where to save and then overwrites that same file on later saves.
  - Other browsers download a new copy each time.
- **Load data file** merges a saved file back in. Use it on a new computer or browser, or after clearing browser data.

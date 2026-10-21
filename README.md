# WI&M Dispatcher

An unofficial operator's sandbox for the Washington, Idaho & Montana Railway out of Potlatch, Idaho. You run the railroad month by month, with Bennett Lumber freight, excursions and the Santa Express. The Idea Lab tests a new idea against hundreds of simulated futures before any real money is at risk.

Not affiliated with the Washington, Idaho & Montana Railway. All equipment, distances, carloads, rates and costs are game assumptions, not WI&M data. You can change them in the app under **Idea Lab → Model assumptions**.

## Files

- `index.html` — the whole game: HTML, CSS and JavaScript in one file, with no build step. Fonts load from Google Fonts.

## Deploy on GitHub Pages

1. Create a new repository on GitHub, for example `wim-dispatcher`.
2. Upload `index.html` and `README.md` to the root of the repository with **Add file → Upload files**, then commit.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to **Deploy from a branch**, choose the `main` branch and the `/ (root)` folder, then **Save**.
5. After a minute or two the site is live at `https://<your-username>.github.io/wim-dispatcher/`.

If you use the command line instead:

```bash
git init
git add index.html README.md
git commit -m "WI&M Dispatcher"
git branch -M main
git remote add origin https://github.com/<your-username>/wim-dispatcher.git
git push -u origin main
```

Then turn on Pages as in steps 3–4.

## Run it locally

Open `index.html` in any browser. No server is needed.

## Where to change things

All of these are in the `<script>` block of `index.html`.

- **Default economics**: `DEFAULT_A`, which holds carloads, freight rate, crew costs, insurance, Santa demand and the credit line. These are the same values the Model assumptions panel edits.
- **Starting railroad**: `newState()`, which sets starting cash, locomotives, coaches, track condition and the default operating plan.
- **Excursion runs**: `ROUTES`, with miles, typical fare, appeal and maximum trips per day.
- **Projects**: `PROJECTS`, with cost, monthly cost, description and what buying does.
- **Dispatches (events)**: `EV`. Each event has a weight function, a title, a body and choices. The first choice is the one the Idea Lab uses on autopilot, so keep it the sensible default.
- **Monthly model**: `simulateMonth()`.

Saved games live in each player's browser through `localStorage`, under the key `wim-dispatcher.v1`.

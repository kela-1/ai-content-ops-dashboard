# AI Content Ops Dashboard

A self-contained tracking + library + prompt-assembler dashboard for AI character video productions. Originally built for TikTok Shop affiliate workflows, but works for any AI video pipeline (Amazon affiliate content, AI influencer accounts, etc).

**Live: [https://YOUR-USERNAME.github.io/ai-content-ops-dashboard/](#)** *(replace this link after enabling GitHub Pages)*

---

## What it does

- **Tracks productions per AI character** — credits spent, posted vs trashed, revenue earned
- **Library system** — products, backgrounds, motions, camera angles, all per-character favoritable
- **Daily ledger** — start/end-of-day Higgs Field credit balance + TikTok Shop revenue (GMV, items sold, commission)
- **Charts** — daily credit usage, daily commission, posted-vs-trashed efficiency
- **Generator** — pick a character + background + motion + angle + products → assembles a one-shot prompt to paste into Higgs Field. Save reusable presets as "blueprints".
- **ROI** at a glance — commission ÷ credit dollar cost
- **Per-video engagement** — views, likes, comments, shares, saves
- **Import / export** — paste end-of-day JSON from your LLM session, or export full data as a backup

## How to use

Open the live link, that's it. No login, no signup. Everything saves automatically to your browser's `localStorage` under the key `aicops_data`. Same browser = same data, every session.

### First-time setup

1. Open the link, you'll see three default characters (Lena, Zoe, Jessica)
2. Go to **Settings** → **Archived characters** is at the bottom — but first, **archive the characters that aren't yours** so you only see your own data. Settings tab won't have an archive button per char — instead go to **Characters** tab, click any character, and use the "archive [name]" button.
3. Or rename the existing character: there's no rename UI yet, so just click "+ new" on the Characters tab to add yourself, then archive the defaults.
4. Add your motions, angles, backgrounds, and products via their respective tabs.
5. On the Characters tab, fill in the **description** field for your character. This goes into the generator prompt.
6. Start tracking productions.

### Daily workflow

1. **Start of day**: open the dashboard, go to the Characters tab, enter your Higgs Field starting balance in the daily ledger row for today.
2. Generate videos as usual. Track each session in your LLM with the **Tools tab** session template.
3. **End of day**: paste the **End-of-Day Extraction prompt** from the Tools tab into your LLM. Get JSON back. Paste into the Import Data tab. Done.
4. Or skip the LLM step entirely and add videos manually with the `+ add video` button.
5. Enter your end-of-day balance + GMV/commission from your TikTok Shop dashboard in the daily ledger.
6. Mark videos as posted/trashed (click the status pill on each video card to cycle).

### Filing bugs / feature requests

Found a bug? Want a feature? File it in the [Issues](../../issues) tab on this repo. Include:
- What you were doing when it broke
- A screenshot if possible (Cmd+Shift+4 on Mac)
- What browser + OS

## Important notes

- **Your data is local to your browser.** Always use the same browser. Don't clear cookies/site data without exporting first.
- **Export weekly as a backup.** Import Data tab → Copy to Clipboard → save somewhere safe (Notes app, a text file, send yourself via iMessage). One day your browser will eat itself; the export is your only backup.
- **Switching browsers loses data.** Safari ≠ Chrome ≠ Firefox. They each have their own localStorage.
- **Hard refresh after updates.** When the dashboard gets updated (new commit pushed here), your browser may serve a cached version. Cmd+Shift+R to force-refresh.

## Tech notes

Single HTML file, no build step, no dependencies. Pure vanilla JavaScript + SVG charts. Hand-rolled because the simplicity of "one file you can host anywhere" matters more than abstraction in this phase.

When the workflow is dialed in, the plan is to rebuild this with a proper backend (Postgres + auth + multi-tenancy + server-held API keys for Higgs Field / Arcads) and ship it as a SaaS. Until then, this is the prototype.

## License

MIT — do whatever you want with it.

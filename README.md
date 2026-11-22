# European Greens in 2026: interactive visuals

Two embeddable charts for the article “2026: Green Wave in the North, Low Tide in the South”:

- **`map.html`** shows the European Green Party (EGP) member countries, coloured by how each member fared in 2026. Crimea is shown as part of Ukraine, and Cyprus as one country.
- **`dumbbell.html`** shows the previous result vs the 2026 result for 25 contests, sorted by change, with filters for region and election type.

Both are static pages with no build step and no external dependencies. D3 is vendored in `lib/`.

## Files

| Path | What it is |
|---|---|
| `map.html`, `dumbbell.html` | The two charts |
| `index.html` | Landing page linking both |
| `style.css` | Shared styles (Arial, light and dark mode) |
| `data/members.json` | EGP member party and 2026 status per country |
| `data/contests.csv` | Previous and 2026 vote share per contest |
| `data/europe.geo.json` | Country shapes (Natural Earth 1:50m), with Crimea merged into Ukraine and Northern Cyprus into Cyprus |
| `lib/d3.min.js` | D3 v7.8.5 |

## Updating the data

- **Statuses and tooltips:** edit `data/members.json`. The status values are `gains`, `mixed`, `setbacks`, `did_not_run`, `pending` and `no_election`. A country not listed is shown as having no EGP member.
- **Contests:** edit `data/contests.csv`. The change is calculated automatically. The `verified` column records the fact-check status (`yes`, `partly`, `no`) and is not shown in the chart.

Still to do before publishing:

- [ ] Verify the rows marked `no` or `partly` in `contests.csv`.
- [ ] After 29 November, update Spain and add the Fribourg government result.

## Publishing with GitHub Pages

The repository lives at https://github.com/Europe-Elects/egp-2026-visuals.

1. On GitHub, go to **Settings → Pages**, set **Source** to *Deploy from a branch*, select `main` and `/ (root)`, and click **Save**.
2. After a minute or two, the charts are live at
   https://europe-elects.github.io/egp-2026-visuals/map.html and https://europe-elects.github.io/egp-2026-visuals/dumbbell.html.

## Embedding

```html
<iframe src="https://europe-elects.github.io/egp-2026-visuals/map.html"
        title="Map: European Green Party members and their 2026 results"
        width="100%" height="720" style="border:0" loading="lazy"></iframe>

<iframe src="https://europe-elects.github.io/egp-2026-visuals/dumbbell.html"
        title="Chart: Green vote share at the previous election and in 2026"
        width="100%" height="860" style="border:0" loading="lazy"></iframe>
```

Check with the Heinrich-Böll-Stiftung editors whether their site accepts iframes. If it doesn't, use static screenshots of the charts in the article and link to the live pages.

## Local preview

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Map data: Natural Earth, public domain.

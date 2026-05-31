# Australia's Gaming Nation

A data-driven editorial essay on the Australian video game industry and its players, built for **FIT2179 Data Visualisation 2** (Monash University, Semester 1, 2026).


## What this is

A single scrolling web page that combines fourteen visualisations into one editorial narrative — from the surprise that 82% of Australians play games, through the changing gender mix of players, to the half-billion-dollar export industry quietly built in studios from Hobart to Brisbane. The arc moves from player culture to industry economics to a forward-looking projection of where the sector is heading.

## How it's built

Everything in this repo is static — there is no build step, no framework, no bundler.

- **Charts:** Each visualisation is a standalone [Vega-Lite](https://vega.github.io/vega-lite/) v5 spec stored as JSON in [`vega/`](./vega). Specs are human-readable and individually inspectable on GitHub.
- **Page:** Plain semantic HTML (`index.html`), a single hand-written stylesheet (`style.css`), and a tiny embedding script (`js/main.js`) that walks the list of chart placeholders and calls `vegaEmbed` on each.
- **Theme:** A dark editorial palette inspired by NYT, The Pudding, and ABC News Story Lab — charcoal background, off-white type, cyan/magenta/purple accents.




## Repository structure

```
.
├── index.html                  # Single-page editorial layout
├── style.css                   # Dark theme + responsive layout
├── README.md                   # You are here
├── js/
│   └── main.js                 # vegaEmbed wrapper, dark theme config
├── vega/                       # 14 Vega-Lite chart specs (one per visualisation)
│   ├── 01-hero-waffle.json     # 82% of Australians play (waffle grid)
│   ├── 02-gender-split.json    # Player gender, 51/48/1 (segmented bar)
│   ├── 03-household-devices.json   # Households with ≥1, ≥2, ≥3 devices
│   ├── 04-age-pyramid.json     # Mirrored age × gender population pyramid
│   ├── 05-devices.json         # Device usage among gamers (horizontal bars)
│   ├── 06-motivations.json     # Why people play (ranked lollipop)
│   ├── 07-revenue-timeline.json    # AGDS revenue FY16–FY25 with annotations
│   ├── 08-employment-growth.json   # Industry FTE growth, stacked by gender
│   ├── 09-export-flow.json     # 95% exports vs 5% domestic (split flow)
│   ├── 10-studio-map.json      # Choropleth: studios per 100k by state
│   ├── 11-state-comparison.json    # Paired bars + circles by state
│   ├── 12-studio-bubble.json   # Interactive bubble: age × revenue × size × state
│   ├── 13-roles.json           # Workforce role mix (proportional bar)
│   └── 14-projection.json      # Revenue forecast FY26–FY28 with confidence cone
└── data/
    ├── agds-yearly.csv         # AGDS revenue/headcount series FY16–FY25
    ├── studios-by-state.csv    # FY25 studios + FTE + population by state
    ├── studios.csv             # 141 anonymised synthetic studio rows
    ├── age-gender.csv          # Player age band × gender
    ├── devices.csv             # Device usage among gamers
    ├── motivations.csv         # Top motivations for playing
    ├── roles.csv               # Workforce role mix
    ├── households.csv          # Household device penetration
    └── aus-states.geojson      # Simplified state/territory boundaries (8 features)
```

## Data sources

- **Australian Game Development Survey (AGDS) FY2025 Snapshot** — IGEA & Bond University, released March 2026
- **Australia Plays 2025** — IGEA & Bond University (Professor Jeffrey Brand), released September 2025
- **Historical AGDS revenue series FY2016–FY2024** — IGEA annual snapshots
- **State population estimates (June 2025)** — Australian Bureau of Statistics, *National, State and Territory Population*
- **State boundary geometries** — derived from the [`world-geojson`](https://www.npmjs.com/package/world-geojson) npm package, simplified to ~36 KB total with Shapely's Douglas–Peucker (tolerance 0.06°). ACT is added as a synthetic rectangle around Canberra since the source package merges it into NSW.

## Methodology notes

- **FY25 methodology change:** The FY2025 AGDS snapshot is the first to incorporate Sensor Tower app-store data in its revenue total. The +79% jump from FY24 to FY25 therefore mixes organic growth with a one-time scope expansion. The revenue timeline (chart 07) annotates this explicitly so readers don't misread the spike.
- **Studio-level bubble chart:** IGEA does not publish per-studio revenue or headcount. The 141 rows in `studios.csv` are **anonymised synthetic data** — generated to match the AGDS FY25 aggregate totals (revenue $608.5M, ~2,461 FTE, state distribution, age distribution) so the chart is shape-true to the population without making claims about any individual studio.
- **Forecast (chart 14):** The FY26–FY28 projection extrapolates from the 10-year compound growth rate, with a ±10–15% confidence cone widening over time. It is illustrative, not a forecast endorsed by IGEA.

## Tools and acknowledgement

- Built with Vega-Lite, Pure.css (base reset only), Google Fonts (Inter, Space Grotesk, JetBrains Mono).

## Licence

The page code and Vega-Lite specs are released under CC-BY 4.0 for educational reuse. Upstream data remains under its respective licences (IGEA reports, ABS, world-geojson MIT).

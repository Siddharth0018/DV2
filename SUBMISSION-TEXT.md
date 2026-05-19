# Moodle submission text — Australia's Gaming Nation

*(~500 words. Paste into the Moodle text submission box. Adjust author / repo URL before submitting.)*

---

## Domain

This project visualises the Australian video game ecosystem — both the people who play and the studios that build. The domain combines consumer-side data from *Australia Plays 2025* (IGEA & Bond University's biennial national survey, n=1,241 households) with industry-side data from the *Australian Game Development Survey (AGDS) FY2025 Snapshot*, released by the same institutions in March 2026. I supplemented these with archival AGDS revenue figures back to FY2016 and ABS state population estimates so per-capita comparisons across states are possible.

## Who and why

The intended audience is the average Australian adult — not industry insiders, not policymakers, not gamers themselves. The motivating insight is the gap between cultural perception and statistical reality: most Australians think of gaming as a teenage hobby, when in fact 82% of the country plays, the average player is 35, women now slightly outnumber men, and the local industry exports over half a billion dollars a year. I wanted a piece that someone scrolling on their phone would come away from feeling like the country looks different than they thought it did. The narrative arc deliberately moves from surprise (the headline 82%) through curiosity (who actually plays?) to discovery (a thriving export industry hidden in suburban office parks) before closing with a measured forward look.

## What I built

A single scrolling editorial page hosting fourteen interconnected visualisations across six sections (hero / players / industry / map / studios / future). The idioms are deliberately varied: a waffle grid, a mirrored age-gender population pyramid, a custom-built split-flow diagram for export vs domestic revenue, a state choropleth, paired bars and dots for the per-capita twist, an interactive bubble chart (age × revenue × size × state, with a state filter), an annotated revenue timeline calling out COVID, the federal Digital Games Tax Offset, and the FY25 methodology change, and a forward projection with a confidence cone. The design language — dark charcoal background, off-white serif-influenced display type, cyan/magenta/purple accents — is intended to read more like an ABC News Story Lab piece than a dashboard.

## How

Every chart is a hand-written Vega-Lite v5 JSON specification (browse them in `/vega` of the repo). A small JavaScript wrapper applies a shared dark theme and embeds each spec into the page; there is no framework or build step, so the specs remain transparently auditable. Two design choices deserve flagging: the studio-level bubble chart uses anonymised synthetic data calibrated to AGDS aggregate totals (IGEA does not publish per-studio figures), and the revenue timeline annotates explicitly that the FY25 jump partly reflects the first-time inclusion of Sensor Tower app-store data, not pure organic growth. Both caveats are stated in the page footer alongside the data sources, tooling, and an acknowledgement that generative AI was used for editorial copy-editing and spec scaffolding while all analysis and design decisions were my own.

**Repository:** `https://github.com/<your-username>/aus-gaming-nation`
**Live page:** `https://<your-username>.github.io/aus-gaming-nation/`

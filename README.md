# NagarTwin — Future Scenario Engine

A static, browser-only prototype for exploring how hypothetical heatwaves, heavy rainfall, and power outages could affect access to essential public services across a fictional city. It lets people compare a no-intervention scenario with a selected response package.

> **Important:** The app uses synthetic sample data and deterministic heuristic formulas. It is not a live forecast, validated risk model, official emergency tool, or substitute for local authorities. Do not use the demo outputs for real emergency or infrastructure decisions.

## What is included

- Three scenario types: heatwave, heavy rainfall, and power outage.
- An intensity slider and focus-area selector.
- Four scenario-specific intervention controls for each event.
- A schematic 12-zone risk field with selectable zones.
- Estimated exposure, modeled service-access scores, priority zones, and response comparisons.
- JSON scenario-report export and CSV zone-table export.
- Transparent in-product explanation of model assumptions and limitations.
- Responsive layout and keyboard-focus styling; no framework, build step, API key, database, or external runtime dependency.

## Run locally

Open `index.html` in a modern browser. All calculations run in the browser.

## Publish with GitHub Pages

1. Sign in at <https://github.com/> and create a new **public** repository called `nagartwin` (or another name you prefer).
2. Upload `index.html`, `README.md`, `LICENSE`, `.nojekyll`, `MODEL_ASSUMPTIONS.md`, and `TEST_CHECKLIST.md` to the repository root. On a phone, the easiest path is to select these files from the extracted `nagartwin` folder. Keep `index.html` at the repository root, not inside another nested folder.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose branch `main` and folder `/(root)`, then press **Save**.
6. Wait for the Pages workflow to finish in the **Actions** tab. Then open the URL shown in **Settings → Pages**. The usual URL format is `https://YOUR-USERNAME.github.io/nagartwin/`; the actual URL depends on your account and repository name.
7. Test the deployed URL on both mobile and desktop. Change each scenario, toggle interventions, choose a zone, and test both exports.

GitHub Pages publication is not performed by this code package. You must upload the repository and enable Pages in your GitHub account.

## Model overview

The demo includes 12 fictional zones. Each has a fictional population, vulnerability index, baseline service-access score, service counts, and three scenario-specific exposure factors. For each run:

1. A selected scenario chooses the matching exposure factor.
2. The intensity slider scales the baseline exposure.
3. Vulnerability and selected scenario assumptions contribute to a raw risk score.
4. Selected interventions apply explicit, illustrative deductions/bonuses.
5. Risk is clamped to 0–100 and a modeled access score is calculated.
6. Estimated exposure is derived from fictional population, modeled risk, and vulnerability.

These coefficients are arbitrary teaching assumptions, not calibrated from real incidents and not empirically validated. See `MODEL_ASSUMPTIONS.md`.

## Research roadmap

### Stage 1 — Reproducible prototype
- Keep the synthetic scenario engine stable and publish the assumptions.
- Add a manual test checklist and capture known limitations.

### Stage 2 — Data design before prediction
- Identify trusted, documented open datasets for one pilot city (weather alerts, roads, facility locations, vulnerability statistics where available).
- Record source, license, collection date, geographic coverage, missing values, and update frequency for each dataset.
- Get local-domain review before interpreting indicators as real risk.

### Stage 3 — Real spatial analysis
- Replace schematic zones with defensible geospatial boundaries and a road-network model.
- Model access to clinics, shelters and water points under explicit, documented disruption assumptions.
- Evaluate baseline access and equity across groups/areas, not only city-wide averages.

### Stage 4 — Evidence-backed scenarios
- Compare modeled outcomes against historical events where reliable observations are available.
- Measure calibration, uncertainty, error by area, robustness to missing data, and intervention sensitivity.
- Only describe outputs as forecasts if a model has been trained/validated for that task and appropriate experts have reviewed it.

## Tech stack

Plain HTML, CSS, and JavaScript. No build tools are required. The current prototype is intentionally static and suitable for GitHub Pages.

## Project status

`v0.1.0` — interactive scenario prototype using synthetic values. No real city data, GIS layers, live feeds, or validated prediction models are connected.

## License

MIT — see `LICENSE`.

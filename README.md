# NagarTwin — Public-Welfare Scenario Lab

**Live demo:** https://piyush0059.github.io/Nagartwin/  
**Repository:** https://github.com/Piyush0059/Nagartwin  
**Release:** v0.2.0

NagarTwin is a transparent scenario-planning prototype for discussing how hypothetical heatwaves, heavy rainfall, and power outages may affect access to essential public services. The public-welfare goal is to help users compare response options, inspect assumptions, and question trade-offs before treating a scenario result as meaningful.

> **Safety and validity:** This is not an operational emergency system, forecast, validated risk model, evacuation tool, or government service. The 12-zone simulator uses fictional data and arbitrary coefficients. Its scores must not be used to make real-world emergency, medical, infrastructure, or evacuation decisions.

## What is included

- Three scenarios: heatwave, heavy rainfall, and power outage.
- Abstract 0–100 scenario-intensity control; it is not temperature, rainfall amount, or outage duration.
- Four scenario-specific intervention controls per event.
- Twelve schematic, fictional zones with selectable focus area.
- Before / no-action / intervention comparison for a composite service-access score.
- Risk field, model-derived exposure proxy, zone details, and model-derived discussion prompts.
- JSON report and CSV zone-table exports whose field names explicitly mark synthetic/modelled data.
- A **Patna public-reference layer** with the district population and area published by the Patna District Administration, the 2011 Census urban/rural split, and links to the Patna Master Plan.
- A live **Open-Meteo modelled weather context** at 25.35° N, 85.12° E, with current model estimates and a three-day outlook. If the API is unavailable, the app reports this and the simulator still works.
- Separate in-page explanation of purpose, intended users, data provenance, formulas, and limitations.

## Important data separation

NagarTwin has two distinct layers:

1. **Public context layer:** sourced reference facts and a weather forecast-model feed. Population and urban/rural figures are from Census 2011 and are historical, district-wide values. Weather values are estimates from a weather model, not local station measurements or official alerts.
2. **Scenario simulation layer:** 12 fictional zones, invented populations/service counts, illustrative vulnerability/exposure factors, and hand-selected intervention coefficients.

**Public-context numbers and the live weather feed are not used in the scenario equations.** The app does not currently model Patna wards, actual roads, facility locations, flood boundaries, heat exposure at neighbourhood scale, or electricity-grid status. See [DATA_SOURCES.md](DATA_SOURCES.md) and [MODEL_ASSUMPTIONS.md](MODEL_ASSUMPTIONS.md).

## Why this project exists

During heatwaves, heavy rain, and outages, people may face simultaneous disruption to water, clinics, roads, power, and relief services. Public teams have to weigh difficult trade-offs with incomplete data. NagarTwin is intended as a transparent learning and research sandbox: compare a hypothetical response package against a no-action case, inspect the assumptions, and identify which real data would be needed before a conclusion could be trusted.

Its public-welfare success criteria for future versions should include more than a single average: service travel time, facility availability, distribution of access across vulnerable groups, uncertainty, missing-data sensitivity, and comparison against observed historical events.

## Use locally

Open `index.html` in a modern browser. The scenario calculations run locally. The public weather context requests data from Open-Meteo over the internet; if that request fails or the user is offline, the weather panel shows an unavailable state and no fake data are substituted. No API key or application server is used by this prototype.

## GitHub Pages deployment

This repository is already configured for GitHub Pages. The published page is linked above. For a fresh fork:

1. Place `index.html` at the repository root.
2. In **Settings → Pages**, select **Deploy from a branch**, branch `main`, folder `/(root)`, and save.
3. Wait for the Pages build/deploy workflow in **Actions** to succeed.
4. Open the URL listed in **Settings → Pages** and follow [TEST_CHECKLIST.md](TEST_CHECKLIST.md).

## Model overview

The simulator calculates a risk score from a zone's fictional scenario-exposure factor, abstract intensity setting, vulnerability index, readiness penalties, and selected intervention effects. It separately calculates access using a fictional baseline-access score, an assumed disruption penalty, and explicit intervention-access bonuses. A synthetic exposure proxy is then derived from fictional population, modelled risk, and vulnerability.

The coefficients have not been calibrated against incidents and have no empirical validation. A score of 65 is only a demo threshold, not an official risk category. Repeating the same inputs yields repeatable results; repeatability is not evidence of predictive accuracy.

## Known limitations

- No real Patna ward boundaries, roads, routing, facility coordinates, operational clinic status, water availability, drainage network, grid data, or ground-truth hazard observations are integrated into the simulator.
- The 2011 Census figures are historical and district-wide; they are not current city or ward population.
- Open-Meteo forecast values are model estimates, not official IMD warnings, and are not used in scenario scoring.
- No calibration, uncertainty interval, probabilistic interpretation, causal evidence, or measured intervention effect exists yet.
- Exposure proxy is not a real number of people harmed, stranded, sick, or needing rescue.
- The schematic zone grid is not a geographic map.
- The mobile/desktop layout and interaction still require manual browser checks after updates; see the checklist.

## Research roadmap

### Stage 1 — Transparent prototype (current)
- Keep synthetic values visibly labelled.
- Document source links, data vintage, equations, and known limitations.
- Provide a real external-data context layer separately from the toy simulator.

### Stage 2 — One real pilot geography
- Import and document official ward/district boundaries and suitable population tables.
- Identify defensible facility-location sources for clinics, shelters and water points, including license, collection date, coverage, and missingness.
- Build a real routing/accessibility baseline before attempting risk prediction.

### Stage 3 — Evidence-backed scenario model
- Link weather/hazard observations to correct spatial and temporal units.
- Test against observed historical disruptions.
- Report calibration, uncertainty, false positives/negatives, and errors by area/group.
- Review assumptions with public-health, emergency-management, urban-planning and community stakeholders before any operational use.

## Project files

- `index.html` — GitHub Pages website
- `DATA_SOURCES.md` — provenance and source registry
- `MODEL_ASSUMPTIONS.md` — equations and model limitations
- `TEST_CHECKLIST.md` — deployment and interaction test plan
- `LICENSE` — MIT

## License

MIT — see [LICENSE](LICENSE). Source-data terms may differ; consult the individual source and API terms before reusing data.

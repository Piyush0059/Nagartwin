# Manual test checklist — v0.2.0

Run these checks on the published Pages URL after each release.

## Deployment and layout

- [ ] Public URL loads over HTTPS with no 404.
- [ ] Page fits a wide desktop and a narrow mobile screen; no horizontal overflow.
- [ ] Header navigation works for Why NagarTwin, Public data, Scenario lab, How it works, and Model & limits.
- [ ] Important text, source links, disclaimers and controls remain readable on mobile.

## Public reference and live weather context

- [ ] Patna district population is clearly dated Census 2011 and described as district-wide, not a current city count.
- [ ] District area and Census handbook links open.
- [ ] Patna Master Plan link opens the official PMAA page.
- [ ] Weather panel loads a model timestamp, current model estimates, and up to three daily forecasts when the API is available.
- [ ] Refresh action re-requests weather data and disables while loading.
- [ ] Offline/API-failure state is clear and does not substitute made-up values.
- [ ] Open-Meteo and official IMD links are visible; model estimates are not described as official warnings.
- [ ] Loading/refreshing weather does not change synthetic simulation scores.

## Scenario simulation

- [ ] Initial demo shows all 12 fictional zones and a visible synthetic-data warning.
- [ ] Heatwave, heavy rainfall, and power outage show their relevant intervention choices.
- [ ] Event intensity changes results, but is labelled as an abstract 0–100 control.
- [ ] Toggling an intervention changes modelled risk/access outputs.
- [ ] Selecting a single zone updates focus metrics/comparison; selecting All 12 zones restores aggregate metrics.
- [ ] High-risk threshold is labelled as a demo threshold, not an official classification.
- [ ] Exposure labels say “proxy” and do not suggest actual people were counted.
- [ ] Action insights remain labelled as discussion prompts, not official operational guidance.
- [ ] Reset returns scenario, intensity, intervention choices, and area focus to the baseline.

## Export and provenance

- [ ] JSON export contains `data_status: SYNTHETIC_DEMO_ONLY`.
- [ ] JSON lists real public context and weather provider separately and states they do not feed the simulation.
- [ ] JSON uses explicit synthetic field names for population, vulnerability, service counts and exposure proxy.
- [ ] CSV column headers mark synthetic/modelled/unvalidated values.
- [ ] Source list and model assumptions page/file match the actual app behavior.

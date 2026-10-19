# NagarTwin model assumptions — v0.1.0

## Status

This is a fictional, deterministic scenario model built to demonstrate an interactive decision-support workflow. It is not a scientific hazard model and has not been calibrated or validated. The numbers displayed by the app should never be interpreted as real forecasts.

## Inputs

Each synthetic zone stores:

- population (illustrative count)
- vulnerability index (0–1)
- baseline service-access score (0–100)
- illustrative clinic and water-point counts
- heat, rainfall, and power exposure factors (0–100)
- drainage and backup-power readiness factors (0–100)
- illustrative road connectivity factor (0–100)

## Calculation outline

For selected zone `z` and event intensity `I`:

```text
severity_factor = 0.42 + I / 88
raw_risk = selected_exposure * severity_factor
         + vulnerability_index * 14
         + scenario_specific_readiness_penalty
         - 10

for each selected intervention:
    raw_risk -= intervention_risk_effect * local_readiness_factor
    access_score += intervention_access_effect * local_readiness_factor

risk_score = clamp(raw_risk, 0, 100)
access_score = clamp(access_score, 10, 100)
estimated_exposure = population * risk_score/100
                      * (0.42 + vulnerability_index*0.3)
```

The implementation in `index.html` includes the exact scenario-specific readiness logic. Parameters are illustrative and arbitrary. “Estimated exposure” is a mathematical output from fictional inputs, not a headcount forecast.

## Known limitations

- No real city boundaries, coordinates, road network, routing engine, elevation, drainage, weather, grid, hospital-status or water-availability data.
- No model calibration against observed incidents.
- No uncertainty interval or probabilistic interpretation.
- Exposure is not equivalent to illness, injury, people needing rescue, or confirmed disruption.
- Composite service-access score is a demo index and is not a validated accessibility measure.
- Intervention impacts are assumed; they are not causally established.
- City-wide averages can hide unequal outcomes; equity and distributional effects need a more rigorous model.
- The schematic zone grid is not a map.

## Minimum requirements before a real pilot

1. Choose one city and one clearly defined public-service question.
2. Source authoritative geospatial, weather/hazard, and facility datasets; document license, date, coverage, quality, and missingness.
3. Define a real outcome measure with local experts (e.g. travel time to an operational clinic under a specific road-closure scenario).
4. Compare to historical events or ground-truth observations and publish error analysis.
5. Measure impacts by area and relevant vulnerable populations while protecting privacy.
6. Have emergency-management, urban-planning, accessibility and community stakeholders review assumptions.
7. Clearly separate observed data, modeled estimates, and recommendations in every interface and export.

# NagarTwin model assumptions — v0.2.0

## Status and purpose

NagarTwin is a browser-based teaching prototype. It demonstrates how a user can define a hypothetical event, select interventions, and compare repeatable model outputs. It is not a scientific hazard model, a validated decision-support model, or an emergency tool.

## Two data layers — intentionally separate

### Public reference context

The website displays:
- Patna district population: 5,838,465 (Census of India 2011, as quoted by the Patna District Administration).
- Patna district area: 3,202 km² (Patna District Administration profile).
- Urban share: 43.07% of the district population in 2011; rural share 56.93% (District Census Handbook).
- Weather-model values fetched when the page loads or the user refreshes, through Open-Meteo at the reference coordinate 25.35° N, 85.12° E.

These values are context and provenance examples only. **They are not fed into the scenario score calculations.** The Census values are historical district-wide statistics. The weather feed is a forecast-model product, not an official warning or ground-station observation.

Sources and access details are maintained in [DATA_SOURCES.md](DATA_SOURCES.md).

### Synthetic scenario profiles

All 12 zone records inside `index.html` are fictional. Their names, populations, vulnerability indices, access scores, clinic counts, water-point counts, exposure factors, drainage-readiness, backup-readiness and road-connectivity factors are illustrative placeholders. They do not correspond to measured Patna neighbourhoods.

## Calculation outline

For selected zone `z), scenario intensity `I`, and scenario exposure field `E`:

```text
severity_factor = 0.42 + I / 88
vulnerability_penalty = vulnerability_index * 14
readiness_penalty = scenario-specific (rain drainage / power backup)
raw_risk = E * severity_factor + vulnerability_penalty
           + readiness_penalty - 10

for each selected intervention:
    raw_risk -= risk_effect * local_readiness_factor
    access_score += access_effect * local_readiness_factor

risk_score = clamp(raw_risk, 0, 100)
initial_access = baseline_access - max(0, pre-intervention_raw_risk - 20) * 0.38
access_score = clamp(initial_access + intervention access bonuses, 10, 100)
exposure_proxy = fictional_population * risk_score/100
                 * (0.42 + vulnerability_index*0.3)
```

The implementation clamps the access score and risk score to the ranges shown. Risk-reduction and access-bonus effects are independent hand-set terms; a lower risk score does not automatically increase access unless an access bonus is also specified. The threshold of 65 for “high risk” is a display choice only—not a government standard.

## Interpretation rules

- A 0–100 intensity value is an abstract sensitivity control. It is not °C, rainfall in millimetres, outage duration, or an official severity scale.
- “Exposure proxy” is an arithmetic output from fictional inputs. It is not a count of real people exposed, sick, injured, stranded, or requiring assistance.
- “Service access” is a composite index, not a measured travel-time or accessibility metric.
- Intervention coefficients are hypothetical and do not demonstrate a causal effect.
- The current weather and Census context shown on the page does not influence any simulation score.
- Same inputs yield repeatable outputs; reproducibility alone does not imply accuracy.
- JSON/CSV exports mark scenario outputs as synthetic/modelled.

## Limitations

- No real ward boundaries, geospatial coordinates for zones, road-network routing, elevation, drainage, flood depth, operational facility status, local power-grid data, or real-time warnings.
- No model calibration against observed events.
- No quantified uncertainty intervals or accuracy metrics.
- No independent validation or domain-expert approval.
- Aggregate scores can conceal unequal outcomes between populations or locations.

## Minimum requirements before a real pilot

1. Choose one geography and one clear outcome, such as travel time to a functioning clinic under a defined road closure.
2. Obtain authoritative boundaries and population tables that fit the same year/geography.
3. Obtain documented location data for hospitals, shelters, water points, roads and infrastructure; keep licensing, source dates and quality notes.
4. Define hazard inputs from an appropriate official/observational source with matching spatial and temporal resolution.
5. Evaluate against historical events or field observations; publish calibration, uncertainty, false-positive/negative and group-level error.
6. Have emergency-management, public-health, urban-planning, accessibility and community stakeholders review the approach.
7. Clearly separate observed data, model estimates, and recommendations in every view/export. Do not use it operationally until validated for that purpose.

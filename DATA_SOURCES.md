# Data sources and provenance — v0.2.0

**Reviewed:** 20 October 2026  
**Website:** https://piyush0059.github.io/Nagartwin/

NagarTwin deliberately separates externally sourced reference context from fictional scenario-simulation inputs. The simulator currently does not consume the real-world data listed below.

## 1. Patna District Administration — demographic profile

- **Source:** https://patna.nic.in/demography/
- **Publisher:** District Administration, Patna, Government of Bihar / NIC website.
- **Displayed values:** district population 5,838,465 (Census 2011); district area 3,202 km²; reference location 25.35° N, 85.12° E.
- **Vintage:** the population is explicitly from Census of India 2011; area and location are as displayed by the district profile.
- **Use in NagarTwin:** reference context, not a simulation input.
- **Limitations:** district-wide statistics are not current city population or ward/neighbourhood statistics. The figures must not be distributed across the 12 fictional zones as if measured.

## 2. Census of India 2011 — Patna District Census Handbook, Part A

- **Source page:** https://www.censusindia.gov.in/nada/index.php/catalog/298
- **Document:** https://www.censusindia.gov.in/nada/index.php/catalog/298/download/842/DH_2011_1028_PART_A_DCHB_PATNA.pdf
- **Publisher:** Office of the Registrar General & Census Commissioner, India / Directorate of Census Operations, Bihar.
- **Displayed value:** 43.07% of Patna district's 2011 population lived in urban areas and 56.93% in rural areas, as stated in the handbook.
- **Use in NagarTwin:** historical district context only. Not a present-day urban share and not a zone-level vulnerability measure.

## 3. Patna Master Plan — planning reference

- **Source page:** https://pmaa.bihar.gov.in/hi/patna_master_plan
- **Publisher:** Patna Metropolitan Area Authority, Government of Bihar.
- **Listed document date:** 24 June 2026.
- **Use in NagarTwin:** linked as a planning reference only.
- **Not yet integrated:** the master plan's downloaded documents/GIS layers are not parsed or used by the current simulator. A future GIS integration must verify file contents, boundary definitions, licence/reuse terms, map projection, and coverage before using them in computation.

## 4. Open-Meteo weather forecast API — live model context

- **Documentation:** https://open-meteo.com/en/docs
- **API endpoint:** `https://api.open-meteo.com/v1/forecast`
- **Reference coordinates:** 25.35° N, 85.12° E, matching the location coordinates displayed on the Patna District Administration page.
- **Requested variables:** current model temperature, apparent temperature, relative humidity, precipitation and 10 m wind speed; daily maximum temperature, precipitation total and maximum precipitation probability for three days.
- **Refresh behavior:** queried in the visitor's browser when the page loads and when they press Refresh. The site does not embed a particular day's weather values in the repository.
- **Licence/terms:** Open-Meteo says data obtained through the API is under CC BY 4.0 and attribution is required. The free API is for non-commercial use under its terms; check the current terms before reuse or commercial use. (https://open-meteo.com/en/terms)
- **Use in NagarTwin:** weather context panel only, not scenario model input.
- **Important:** modelled “current” conditions are not the same as a direct local weather-station observation. The feed is not an official India Meteorological Department alert or warning. For official warnings, use https://mausam.imd.gov.in/.

## 5. Simulation data — not a public dataset

The 12 profiles in `index.html` (zone names, populations, vulnerability, baseline access, service counts, hazard exposure, drainage/backup readiness and road connectivity) are manually authored synthetic teaching values. They have no geographic correspondence to Patna's actual wards. Intervention effects and all coefficients are illustrative.

These values must remain labelled synthetic until replaced with well-sourced data with compatible geography, time period, licensing, completeness and a defensible measurement definition.

## Data-quality rules

1. State publisher/source, vintage or retrieval timestamp, geographic scope, and units.
2. Do not turn district data into ward-level values by dividing or guessing.
3. Do not call a model forecast an observation or official warning.
4. Keep observed/reference data, synthetic inputs, model scores, and recommendations visually and programmatically separate.
5. Include missing-data/error handling; if the external API fails, show unavailable rather than plausible-looking placeholder numbers.
6. Before any operational claim, compare estimates with historical events/field observations and publish error and uncertainty.

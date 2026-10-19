# Manual test checklist

Run these checks on the deployed Pages URL and tick them off before sharing the project publicly.

- [ ] Page loads on mobile and desktop with no missing external assets.
- [ ] The initial demo shows all 12 synthetic zones.
- [ ] Heatwave, heavy rainfall, and power outage each display different intervention options.
- [ ] Changing event intensity changes the modeled scores.
- [ ] Toggling interventions changes the comparison chart and results.
- [ ] Selecting a zone from the schematic grid updates the focus and metrics without hiding the other zones.
- [ ] Selecting “All 12 zones” returns aggregate metrics for all zones.
- [ ] JSON export downloads a report labelled `SYNTHETIC_DEMO_ONLY`.
- [ ] CSV export downloads the expected zone table and clearly named modelled fields.
- [ ] Reset returns the controls to the initial demo state.
- [ ] Keyboard focus is visible; interactive controls have understandable labels.
- [ ] The safety notice and methodology/limitations remain readable on a narrow phone screen.
- [ ] No text claims that synthetic outputs are real forecasts or official guidance.

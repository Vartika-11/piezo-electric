# Piezo Pump Health Monitor — Simulation

An interactive browser simulation of a multi-frequency piezoelectric cantilever
vibration harvester used for water pump fault detection.

Three cantilever beams (tuned to 50 Hz / 100 Hz / 200 Hz) act as mechanical
bandpass filters. As the simulated pump vibration frequency sweeps or is set
by the user, each beam's piezoelectric tip voltage rises when the input
frequency approaches its resonance — mirroring the physical device's Arduino
logic: `analogRead` each channel, compare peak voltage to a threshold, and
report the matching fault.

## Fault mapping

| Beam | Fault Detected | Resonant Frequency |
|------|-----------------|---------------------|
| Beam 1 | Dry Run / Cavitation | 50 Hz |
| Beam 2 | Bearing Wear | 100 Hz |
| Beam 3 | Imbalance / Erosion | 200 Hz |

## Run it

No build step, no dependencies — it's a single self-contained HTML file.

- **Locally:** just open `index.html` in any browser.
- **On GitHub Pages:**
  1. Push this repo to GitHub.
  2. Go to **Settings → Pages**.
  3. Under "Branch," select `main` and `/ (root)` → **Save**.
  4. GitHub will publish it at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## Controls

- **Frequency slider** — manually set the simulated pump vibration frequency (0–250 Hz).
- **Preset buttons** — jump straight to Normal / Dry Run / Bearing Wear / Imbalance.
- **▶ Sweep 0–250 Hz** — auto-plays through the full range on a loop, useful for a live demo.

## Notes

This is a schematic simulation for demonstration purposes — the resonance
curves are modeled (a standard driven-oscillator amplitude response), not
measured from physical hardware. Voltage threshold is set at 2.5 V, within
the design brief's expected 1–5 V AC output range per disc.

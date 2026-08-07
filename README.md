# Eris Pulse Lab

Experimental browser-based photoplethysmography (PPG) prototype for iPhone.

> **Required Notice:** Copyright 2026 AR-Night. Eris Pulse Lab.

## Current prototype — v0.6 WOW

The v0.6 interface moves the project toward a more cinematic health-tech presentation while keeping the analysis tied to the real camera-derived PPG signal.

### Measurement flow

- **30-second** measurement session
- Rear-camera access and torch-capability search
- Torch test before measurement
- Finger-contact and basic saturation checks
- Real RGB camera-frame acquisition
- Real-time PPG waveform
- Live BPM estimate and trend
- PPG-derived respiratory estimate when confidence is sufficient
- Median RR / IBI interval
- Short-term RMSSD estimate
- Signal-quality estimate
- Exploratory pulse morphology: rise time, pulse width, optical AC/DC pulsatility and dicrotic-notch screening
- Automatic final trend and **Eris Physiological Report**
- Weak or unavailable features are shown as **Non stimabile** instead of being invented

## v0.6 visual system

The live screen now includes an inline anatomical torso rendered directly in SVG:

- translucent thorax and rib-cage styling
- animated glowing heart
- heart animation duration synchronized to the estimated BPM
- animated lungs / thoracic expansion
- breathing animation synchronized to the PPG-derived respiratory estimate when available
- moving scan line and rotating HUD rings
- live heart-rate and respiratory HUD cards
- trend that is progressively drawn during the scan
- automatic transition to the final trend/report after 30 seconds

The anatomical display is a visualization layer; physiological values continue to come from the PPG analysis pipeline rather than from the animation.

## How the respiratory estimate is obtained

Breathing can modulate a PPG signal through slower changes in baseline, pulse amplitude and beat-to-beat timing. Eris Pulse Lab searches the acquired optical signal for a coherent low-frequency modulation compatible with a respiratory rhythm.

Because v0.6 uses a short 30-second window, respiratory output is treated as an **indirect estimate / trend feature**. If the modulation is not sufficiently coherent, the report returns **Non stimabile**.

This is not a spirometric measurement.

## Final report

At the end of the 30-second session the app automatically opens the final trend and report. The report can include:

- mean / minimum / maximum BPM
- BPM trend
- respiratory trend when estimable
- median RR / IBI
- RMSSD
- estimated respiratory rate + confidence
- rise time and pulse width when measurable
- relative optical AC/DC pulsatility
- dicrotic-notch screening when morphology and frame rate are adequate
- session quality, valid-frame percentage and FPS

## Clinical rationale

A clinician-facing explanation of the acquisition and derivation pipeline is maintained in:

- `docs/CLINICAL_RATIONALE.md`

The document separates primary optical measurements from derived or research-only parameters and explains why blood pressure and SpO₂ are not reported as direct measurements.

## iPhone test

The app requires a secure HTTPS origin and camera permission in Safari. GitHub's normal repository and raw-file views do not execute the HTML app as a normal secure web application.

For quick development testing without GitHub Pages, the repository HTML can be served through an HTTPS source-code proxy such as raw.githack.com. This is a third-party service intended for development/testing, not production.

## Medical status

This is an experimental prototype, **not a medical device**. It must not be used for diagnosis, monitoring requiring clinical accuracy, or clinical decision-making. Blood pressure and SpO₂ are not presented as direct measurements.

## License / project protection

This repository is source-available under the **PolyForm Noncommercial License 1.0.0**. Noncommercial study, experimentation, testing and modification are allowed subject to the license terms. Commercial use requires separate permission from the licensor.

# Eris Pulse Lab

Experimental browser-based photoplethysmography (PPG) prototype for iPhone.

> **Required Notice:** Copyright 2026 AR-Night. Eris Pulse Lab.

## Current prototype — v0.4

- 60-second measurement session
- Rear-camera access and torch-capability search
- Torch test before measurement
- Finger-contact and basic saturation checks
- Real RGB camera-frame acquisition
- Real-time PPG waveform
- BPM estimate and BPM trend
- BPM mean, minimum and maximum
- Median RR / IBI interval
- Short-term RMSSD estimate
- Signal-quality score
- Estimated respiratory rate from slow PPG modulation, only when signal confidence is sufficient
- Exploratory pulse morphology: rise time, pulse width, optical AC/DC pulsatility and dicrotic-notch screening
- Automatic **Eris Physiological Report** at the end of the session
- No invented value: unavailable or weak features are reported as **Not estimable / Non stimabile**

## How the respiratory estimate is obtained

Breathing can modulate a PPG signal through slow changes in baseline, pulse amplitude and beat-to-beat timing. Eris Pulse Lab searches for a coherent low-frequency modulation in the acquired optical signal and estimates the dominant respiratory frequency only when the correlation/quality threshold is met.

This is an **indirect PPG-derived estimate**, not a spirometric measurement.

## Final report

The report can include:

- mean / minimum / maximum BPM
- median RR / IBI
- RMSSD
- estimated respiratory rate + confidence
- relative optical pulse morphology
- rise time and pulse width when measurable
- relative optical AC/DC pulsatility
- dicrotic-notch screening when morphology and frame rate are adequate
- session quality, valid-frame percentage and FPS

## Clinical rationale

A detailed clinician-facing explanation of the acquisition and derivation pipeline is maintained in:

- `docs/CLINICAL_RATIONALE.md`

The document separates primary optical measurements from derived or research-only parameters and explains why blood pressure and SpO₂ are not reported as direct measurements.

## iPhone test

The app requires a secure HTTPS origin and camera permission in Safari. GitHub's normal repository and raw-file views do not execute the HTML app as a normal secure web application.

For quick development testing without GitHub Pages, the repository HTML can be served through an HTTPS source-code proxy such as raw.githack.com. This is a third-party service and is intended only for development/testing, not production.

## Medical status

This is an experimental prototype, **not a medical device**. It must not be used for diagnosis, monitoring requiring clinical accuracy, or clinical decision-making. Blood pressure and SpO₂ are not presented as direct measurements.

## License / project protection

This repository is **source-available, not open-source under a permissive MIT-style license**.

Eris Pulse Lab is offered under the **PolyForm Noncommercial License 1.0.0**:
https://polyformproject.org/licenses/noncommercial/1.0.0/

In practical terms, noncommercial study, experimentation, testing, modification, and distribution are allowed subject to the license terms. Commercial use requires separate permission from the licensor.

Publishing the repository publicly makes the source visible; the license governs permitted reuse but is not a technical copy-protection mechanism.

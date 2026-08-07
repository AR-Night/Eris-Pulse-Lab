# Eris Pulse Lab

Experimental browser-based photoplethysmography (PPG) prototype for iPhone.

> **Required Notice:** Copyright 2026 AR-Night. Eris Pulse Lab.

## Current prototype — v0.7 WOW

Eris Pulse Lab performs a **30-second** fingertip PPG scan using the iPhone rear camera + flash. The interface keeps the animated anatomical torso introduced in v0.6 while extending the physiological analysis pipeline.

### Measurement flow

- rear-camera access and torch-capability search
- torch test before measurement
- stable fingertip/contact check
- real RGB frame acquisition
- real-time PPG waveform
- live BPM estimate and trend
- anatomical heart animation synchronized to BPM
- PPG-derived respiratory estimate with animated lungs when estimable
- automatic final trend + **Eris Physiological Report**
- weak/unavailable features are shown as **Non stimabile** rather than invented

## v0.7 physiological outputs

### Heart / pulse

- BPM mean / minimum / maximum
- median RR / IBI
- real PPG waveform and BPM trend
- signal quality and valid-frame percentage

### HRV

- RMSSD
- SDNN on the 30-second window (**ultra-short / orientative**)
- pNN50 on the 30-second window (**ultra-short / orientative**)
- LF/HF is intentionally **not calculated** in the 30-second protocol; the report marks it as requiring a longer acquisition

### Respiratory rate

The respiratory estimate now combines three PPG-derived mechanisms when they are coherent:

1. slow baseline/intensity modulation (RIIV)
2. pulse-amplitude variability (PAV)
3. beat-to-beat / IBI modulation (PRV)

The app fuses compatible estimates and reports a respiratory rate only when the signal confidence is sufficient. It is an indirect PPG-derived estimate, not spirometry.

### Rhythm regularity screening

v0.7 adds a heuristic PPG rhythm-regularity screen based on beat-to-beat interval variability and outlier burden:

- **Regolare**
- **Variabile**
- **Da verificare**

This is **not an atrial-fibrillation diagnosis** and does not replace ECG confirmation.

### Optical oxygenation research index

v0.7 records red and green camera-channel pulsatility and calculates a research-only normalized ratio:

`(AC/DC red) / (AC/DC green)`

The app also checks whether that optical index is reasonably stable across the two halves of the recording.

**Important:** this value is **not converted to SpO₂**. A clinically meaningful oxygen-saturation percentage would require device-specific calibration and validation. The report therefore explicitly shows **SpO₂: Non riportata**.

### Blood pressure

Blood pressure remains excluded. No mmHg value is inferred from the single-camera PPG signal.

## Exploratory pulse morphology

When frame rate and waveform quality allow, the report can include:

- rise time
- pulse width
- relative optical AC/DC pulsatility
- dicrotic-notch screening

These are relative/exploratory waveform features, not direct vascular diagnoses.

## Visual system

The live screen uses an inline SVG anatomical torso:

- translucent thorax and rib styling
- glowing heart synchronized to BPM
- breathing lungs synchronized to the PPG-derived respiratory estimate
- moving scan line and HUD rings
- live heart-rate / respiratory HUD
- continuously drawn PPG and trend curves
- automatic transition to the final trend/report after 30 seconds

The anatomy is a visualization layer; physiological outputs are calculated from the acquired camera signal.

## Clinical rationale

A clinician-facing explanation of the acquisition and derivation pipeline is maintained in:

- `docs/CLINICAL_RATIONALE.md`

## iPhone test

The app requires a secure HTTPS origin and camera permission in Safari. For quick development testing without GitHub Pages, the repository can be served through an HTTPS source-code proxy such as raw.githack.com. This is a third-party development/testing service, not a production deployment.

## Medical status

This is an experimental research prototype, **not a medical device**. It must not be used for diagnosis, clinical monitoring, or therapeutic decisions. Rhythm screening, respiratory estimation, ultra-short HRV metrics and the optical R/G index are research/exploratory outputs.

## License / project protection

This repository is source-available under the **PolyForm Noncommercial License 1.0.0**. Noncommercial study, experimentation, testing and modification are allowed subject to the license terms. Commercial use requires separate permission from the licensor.

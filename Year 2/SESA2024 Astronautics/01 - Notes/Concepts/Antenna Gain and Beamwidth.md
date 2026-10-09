---
title: "Antenna Gain and Beamwidth"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["antenna gain", "3 dB beamwidth", "parabolic dish", "isotropic radiator", "power-gain trade-off", "global coverage antenna"]
tags: [sesa2024, concept, communications]
status: complete
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[EIRP and G-T]]", "[[Decibels]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf"]
---

# Antenna Gain and Beamwidth

## Definition

> [!note] Definition
> $$G = \frac{4\pi A_{eff}}{\lambda^2} = \eta\left(\frac{\pi D}{\lambda}\right)^2,\qquad\theta_{3dB}\approx72\frac{\lambda}{D}\ (\text{degrees}),\qquad\lambda = c/f$$
> Gain is the maximum flux relative to an isotropic radiator (gain 1, 0 dB). $0.4<\eta<0.8$.

## Explanation
- $G\propto(D/\lambda)^2$: **doubling $D$ or $f$ adds 6 dB and halves the beamwidth** (2016/17 Q1(vi)).
- A high-gain antenna concentrates power along the boresight. A narrow beam needs accurate pointing (ACS).
- **Global coverage**: from orbit radius $r$ the Earth subtends $2\alpha$ with $\sin\alpha = R_E/r$. Set $\theta_{3dB} = 2\alpha$ to find $D$.

| Orbit | $2\alpha$ |
|---|---|
| GEO | 17.4° |
| 12 h GPS | 27.7° |
| 18 000 km | 41.5° |

- **Power–gain trade-off**: for a fixed EIRP $= P_TG_T$, a bigger dish means less RF power but more mass, accommodation and deployment difficulty, tighter pointing, and possible blockage of arrays or the payload field of view.

## Examples
- 3 m dish, $\eta$ = 0.5:

| Band | $G$ | $\theta_{3dB}$ |
|---|---|---|
| L | 30.45 dB | 4.8° |
| C | 38.97 dB | 1.8° |
| X | 44.99 dB | 0.9° |
| Ku | 49.87 dB | 0.51° |

- GEO global coverage at 1.5 GHz: $D$ = 0.83 m and $G$ = 19.3 dB.
- 2023/24 B2(ii) (C-band, Northern hemisphere, 0.6 m or 0.8 m): $\lambda$ = 0.0732 m gives $\theta_{3dB}$ = 8.8° for 0.6 m and 6.6° for 0.8 m. The Northern hemisphere subtends about $\alpha$ = 8.7° from GEO, so **0.6 m** fits.
- 2017/18 Q3(ii): 2, 3 or 4 m dishes at 8.5 GHz ($\eta$ = 0.5) give **42.0, 45.5 and 48.0 dB**. The 4 m dish gains 6 dB (¼ the RF power) but must be deployed in orbit, which adds risk and mass.

![[ast_antenna_gain_beamwidth.png|620]]

## Related
- [[Link Budget Equation]] · [[EIRP and G-T]] · [[Decibels]]

## Sources
- Chapter 9 slides 17–21 (equations 9.3–9.5); workbook Ch9 Q2, Q3, Q6, Q7

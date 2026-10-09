---
title: "Decibels"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["dB", "dBW", "decibel", "log units"]
tags: [sesa2024, concept, communications]
status: complete
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Antenna Gain and Beamwidth]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf"]
---

# Decibels

## Definition

> [!note] Definition
>
> $$\Big(\frac{P_R}{P_T}\Big)_{dB} = 10\log_{10}\frac{P_R}{P_T},\qquad P_{dBW} = 10\log_{10}\frac{P}{1\ \text{W}}$$

## Explanation
- In dB, multiplication becomes **addition**, so the link budget becomes a sum.
- Rules of thumb:
  - ×2 = +3 dB; ×10 = +10 dB; ×1000 = +30 dB;
  - ½ = −3 dB, the "3 dB beamwidth" is the **half-power** width;
  - squared quantities (amplitude, dish diameter, $1/\rho$) give $20\log$.
- Useful constants:

| Quantity | dB value |
|---|---|
| $k = 1.38\times10^{-23}$ J/K | **−228.60 dBW/Hz/K** |
| 1 Mbps | 60 dB-Hz |
| 1 W | 0 dBW = 30 dBm |

- Always convert back to linear units before interpreting: $P = 10^{P_{dBW}/10}$ W.

## Examples
- 16.98 kW = 42.3 dBW (lecture).
- EIRP of 65 dBW = 3.16 × 10⁶ W isotropic-equivalent.
- $R_b$ = 35.42 dB means $10^{3.542}$ = 3483 bit/s.
- $T_R$ = 150 K is 21.76 dB-K.

## Related
- [[Link Budget Equation]] · [[Antenna Gain and Beamwidth]]

## Sources
- Chapter 9 slide 5

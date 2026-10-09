---
title: "Active, Reactive and Apparent Power"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["active power", "reactive power", "apparent power", "complex power", "S = VI*", "VAR", "VA", "power triangle", "power factor"]
tags: [feeg1004, concept, ac-circuits, power]
status: complete
parent_lectures: ["[[FEEG1004 D4 - AC Power and Power Factor]]"]
related_concepts: ["[[Power Factor Correction]]", "[[RMS Value]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W25 AC Analysis 04 - AC Power - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Active, Reactive and Apparent Power

## Definition

> [!note] Definition
> $$\mathbf S = \mathbf V\mathbf I^* = P + jQ,\qquad P = VI\cos\phi\ [\mathrm W],\qquad Q = VI\sin\phi\ [\mathrm{VAR}],\qquad |\mathbf S| = VI\ [\mathrm{VA}],\qquad \mathrm{pf} = \cos\phi = \frac{P}{|S|}$$
> Here $\phi = \theta_v - \theta_i$ and V, I are rms.

## Explanation
- **P**: the average power, dissipated in resistance ($I^2R$).
- **Q**: energy exchanged with L and C every half-cycle. Inductors have $Q = +I^2X_L$ (absorb); capacitors $Q = -I^2X_C$ (generate).
- P and Q are each **conserved**: the totals equal the sums over the elements.
- **Lagging** pf means an inductive load; **leading** means capacitive.
- Use the **conjugate** $\mathbf I^*$, otherwise Q comes out with the wrong sign.

![[ee_d4_instantaneous_power.png|800]]

## Examples
- 50 V into 6 + j11.31 Ω: 91.5 W, 172.5 VAR, 195.3 VA.
- Tutorial 8 Q3 furnace: 45.7 kW, 71.8 kVAR (pf 0.54).

## Related
- Topic notes: [[FEEG1004 D4 - AC Power and Power Factor]]
- Concepts: [[Power Factor Correction]] · [[RMS Value]] · [[Three-Phase Star and Delta Connections]]

## Sources
- AC Analysis 04 slides; Niu AC notes (Figs 27–35)

---
title: "Power Factor Correction"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["PFC", "capacitor bank", "power factor penalty", "Q_C = -V^2 omega C"]
tags: [feeg1004, concept, ac-circuits, power]
status: complete
parent_lectures: ["[[FEEG1004 D4 - AC Power and Power Factor]]"]
related_concepts: ["[[Active, Reactive and Apparent Power]]", "[[Capacitance]]"]
sources: ["02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf"]
---

# Power Factor Correction

## Definition

> [!note] Definition
> A capacitor in **parallel** with an inductive load supplies the reactive power locally:
> $$Q_C = -\frac{V^2}{X_C} = -V^2\omega C,\qquad Q_{new} = Q_{load} + Q_C,\qquad \mathrm{pf}_{new} = \frac{P}{\sqrt{P^2 + Q_{new}^2}}$$
> P is unchanged.

## Explanation
- Poor pf means higher line current for the same useful power: more $I^2R$ loss, more voltage drop and larger plant. Utilities penalise pf below about 0.85.
- Capacitors are "generators" of reactive power; inductive loads "absorb" it.
- Over-correction makes the load leading, which can raise the load voltage above the supply.
- Size the capacitor for a target pf: $C = (Q_{load} - P\tan\phi_{target})/(V^2\omega)$.

![[ee_d4_power_triangle_pfc.png|560]]

## Examples
- 80 kVA at pf 0.5, 400 V, with 1 mF: Q falls from 69.3 to 19.0 kVAR and pf rises to 0.90.
- Tutorial 8 Q3: the supply pf improves from 0.54 to 0.90 and the cable current falls from 213 A to 127 A.

## Related
- Topic notes: [[FEEG1004 D4 - AC Power and Power Factor]]
- Concepts: [[Active, Reactive and Apparent Power]] · [[Capacitance]]

## Sources
- Niu AC notes (PFC example); Tutorial Sheet 8 Q3

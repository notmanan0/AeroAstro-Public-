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
sources: ["02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "02 - Sources/Tutorial Sheets/Tutorial Sheet 08 - AC Circuits 2 - Filters & Transfer Functions.pdf", "Niu AC notes, PFC example", "Tutorial Sheet 8 Q3"]
---

# Power Factor Correction

Power factor correction places a capacitor in **parallel** with an inductive load so that the capacitor supplies the load's reactive power locally, raising the power factor seen by the supply while leaving the active power $P$ unchanged.

$$
Q_C = -\frac{V^2}{X_C} = -V^2\omega C,\qquad Q_{new} = Q_{load} + Q_C,\qquad \mathrm{pf}_{new} = \frac{P}{\sqrt{P^2 + Q_{new}^2}}
$$

A poor power factor means a higher line current for the same useful power, which brings more $I^2R$ loss in the cables, more voltage drop and larger plant. Utilities therefore penalise a power factor below about 0.85. In terms of reactive power, a capacitor acts as a generator of reactive power and an inductive load absorbs it, so the capacitor's negative $Q_C$ cancels part of the load's positive $Q_{load}$.

To reach a target power factor, set $Q_{new} = P\tan\phi_{target}$ and solve for the capacitance:

$$
C = \frac{Q_{load} - P\tan\phi_{target}}{V^2\omega}
$$

Too large a capacitor over-corrects: the combined load becomes leading, which can raise the load voltage above the supply voltage.

![[ee_d4_power_triangle_pfc.png|560]]

For an 80 kVA load at pf 0.5 on 400 V, a 1 mF capacitor cuts $Q$ from 69.3 to 19.0 kVAR and raises the power factor to 0.90. In Tutorial 8 Q3 the correction improves the supply power factor from 0.54 to 0.90, and the cable current falls from 213 A to 127 A.

## Related

- [[FEEG1004 D4 - AC Power and Power Factor]]
- [[Active, Reactive and Apparent Power]] · [[Capacitance]]
- Sources: Niu AC notes (PFC example); Tutorial Sheet 8 Q3

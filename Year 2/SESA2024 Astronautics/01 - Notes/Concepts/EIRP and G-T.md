---
title: "EIRP and G-T"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["EIRP", "equivalent isotropic radiated power", "G/T", "figure of merit", "ground station figure of merit", "power-gain trade-off"]
tags: [sesa2024, concept, communications]
status: lectured
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Antenna Gain and Beamwidth]]"]
sources: ["02 - Sources/Lectures/SESA2024 Lecture Chapter 9 - Communications - prerecord - week 8.txt", "02 - Sources/Lectures/SESA2024 Lecture 2026-01-06.txt"]
---

# EIRP and G-T

The equivalent isotropic radiated power (EIRP) is the product $P_TG_T$ of a transmitter's power and antenna gain, the power an isotropic radiator would need to produce the same flux at the receiver; $G_R/T_R$, the receiving antenna's gain over its system noise temperature, is the receiver's figure of merit or sensitivity.

In the link budget the EIRP is the term the spacecraft designer controls, and it is a design parameter that must be large enough to reach the required link quality. The same EIRP can come from high power and modest gain, which loads the power and thermal subsystems, or from low power and high gain, which needs a larger dish with more mass, perhaps a deployment mechanism, possible shadowing of arrays or payload, and a narrower beam that tightens ACS pointing. That is the power–gain trade-off asked about in 2017/18 B3 and Workbook Ch9 Q6.

$G_R/T_R$ belongs to the ground segment: a large, cold receiver (the 70 m Deep Space Network dishes at 25 K give about 59 dB/K) is what makes deep-space links possible. Raising it is cheaper than raising the spacecraft's EIRP, which is why missions rely on large ground antennas.

## Related

- [[SESA2024 09 - Communications#6. The link budget equation|Link budget in the lecture note]]
- [[Link Budget Equation]] · [[Antenna Gain and Beamwidth]]

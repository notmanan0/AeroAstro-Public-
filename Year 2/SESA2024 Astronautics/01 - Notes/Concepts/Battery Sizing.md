---
title: "Battery Sizing"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["depth of discharge", "DoD", "battery capacity", "energy density", "charge rate", "NiCd", "NiH2", "lithium-ion"]
tags: [sesa2024, concept, power]
status: lectured
parent_lectures: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
related_concepts: ["[[Eclipse Duration]]", "[[Solar Cells and Arrays]]"]
sources: ["02 - Sources/Lectures/Chapter 8/2025 WEEK 7 - Chapter 8 - Power - complete.pdf"]
---

# Battery Sizing

Battery sizing finds the capacity and mass of the rechargeable battery that must carry a spacecraft's load through the worst-case eclipse, at a depth of discharge low enough for the battery to survive the mission's number of charge cycles.

The cycle count is the mission lifetime divided by the orbital period, about 10 000 for two years in LEO. Cycle life falls steeply with depth of discharge (on the NiCd curve, 20 % DoD gives tens of thousands of cycles and 60 % about a thousand), so LEO batteries are run shallow and most of their charge is never used. The cells in series set the voltage, $V_B=N_cV_c$ with 1.25 V per NiCd cell, 1.3 V per NiH₂ cell and 4.1 V per lithium-ion cell. Then

$$
C=\frac{P_{EOL}\,t_e}{\mathrm{DoD}\cdot V_B},
\qquad
E=CV_B,
\qquad
M=\frac{E}{\varepsilon},
$$

and the array must replace the discharged capacity during sunlight at the charge rate $R=\mathrm{DoD}\cdot C/t_s$, adding $RV_A$ to the array power. For the course example (1 kW, 0.6 h eclipse, 30 % DoD, 27.5 V NiCd at 30 W h/kg) this gives 72.7 A h, 2000 W h and 67 kg.

Lithium-ion has the highest energy density and is now standard; NiH₂ tolerates deeper discharge than NiCd for the same cycle life but is bulky; NiCd is obsolete. All must be kept within their operating temperature range (roughly 0–40 °C), which ties the battery to the thermal subsystem.

## Related

- [[SESA2024 08 - Electrical Power Subsystem#3. Batteries|Batteries in the lecture note]] · [[SESA2024 08 - Electrical Power Subsystem#800 km LEO spacecraft, 1 kW for two years|Worked example]]
- [[Eclipse Duration]] · [[Solar Cells and Arrays]]

---
title: "EIRP and G-T"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["EIRP", "equivalent isotropic radiated power", "G/T", "figure of merit", "receiver sensitivity"]
tags: [sesa2024, concept, communications]
status: complete
parent_lectures: ["[[SESA2024 09 - Communications]]"]
related_concepts: ["[[Link Budget Equation]]", "[[Antenna Gain and Beamwidth]]"]
sources: ["02 - Sources/Lectures/Chapter 9/2025 Chapter 9 - Communications - Lecture slides.pdf"]
---

# EIRP and G/T

## Definition

> [!note] Definition
> - **EIRP** $= P_TG_T$ (W or dBW): the power an **isotropic** radiator at the transmitter would need to radiate to produce the same power flux (W/m²) at the receiver as the real directional transmitter.
> - **$G_R/T_R$** (dB/K): the receiving system's **figure of merit** (sensitivity). $C/N_0\propto G_R/T_R$.

## Explanation
- EIRP collects all the transmitter-side terms. The link requirement fixes EIRP; the designer splits it between $P_T$ (power subsystem) and $G_T$ (antenna size). This is the **power–gain trade-off**.
- $G/T$ collects the receiver side. A big dish raises $G$; a cold, low-noise amplifier lowers $T$. Deep-space stations maximise both.
- Converting back:
$$P_T = 10^{(EIRP-G_T)/10}\ \text{W},\qquad P_{elec} = P_T/\eta_{transponder}$$

## Examples
- 2024/25 B2(iii), GPS global beam:
  - $\theta_{3dB}$ = 27.7°, so $D = 72(0.190)/27.7$ = 0.49 m, giving $G_T$ = 16.4 dB ($\eta$ = 0.65);
  - $P_T$ = 38.2 − 16.4 = 21.8 dBW = 151 W;
  - at 50 % efficiency, **≈ 303 W**. The paper asks you to show "≈ 310 W".
- 2022/23 B2(ii), 18 000 km, 240 kbps: EIRP = 34.6 dBW. With $\eta$ = 0.65, $P_{elec}$ ≈ **271 W** (the paper quotes ≈ 272 W).
- "Explain the physical significance of EIRP" appears in 2015/16, 2018/19, 2023/24 and 2024/25 (3–5 marks).

## Related
- [[Link Budget Equation]] · [[Antenna Gain and Beamwidth]]

## Sources
- Chapter 9 slide 27 (equation 9.7); workbook Ch9 Q5, Q6

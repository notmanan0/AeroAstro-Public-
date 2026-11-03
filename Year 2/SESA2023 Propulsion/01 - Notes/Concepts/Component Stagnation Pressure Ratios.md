---
title: "Component Stagnation Pressure Ratios"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["Gamma_d", "Gamma_c", "Gamma_n", "pressure recovery", "combustion efficiency", "real ramjet"]
tags: [sesa2023, concept, cycle-analysis]
status: complete
parent_lectures: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Intake Pressure Recovery]]", "[[Ramjet]]", "[[Isentropic Efficiency]]", "[[Entropy Change of a Perfect Gas]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Component Stagnation Pressure Ratios

Losses in passive components, which do no work and are adiabatic, appear only as drops in stagnation pressure, measured by the stagnation pressure ratios

$$
\Gamma_d = \frac{p_{02}}{p_{01}},\qquad\Gamma_c = \frac{p_{03}}{p_{02}},\qquad\Gamma_n = \frac{p_{04}}{p_{03}}\quad(\le1),
$$

for the diffuser, combustor and nozzle. Incomplete combustion is counted separately through $\eta_b = LCV_{eff}/LCV$.

In an adiabatic component $T_0$ is constant, so $\Delta s = -R\ln\Gamma$ and each $\Gamma$ is a direct measure of entropy generation. The diffuser loses stagnation pressure through shocks, friction and separation; the combustor through friction, flameholder drag and the Rayleigh loss of adding heat to a moving flow, which a larger contraction ratio or lower velocity reduces; the nozzle through friction, divergence and shocks. In a real ramjet they multiply together,

$$
\frac{p_{04}}{p_a} = \Gamma_d\Gamma_c\Gamma_n\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{\frac{\gamma}{\gamma-1}},\qquad V_e = \sqrt{2c_pT_{03}\big[1-(p_a/p_{04})^{(\gamma-1)/\gamma}\big]},
$$

so losses reduce the expansion ratio, and with it $V_e$ and the thrust. On a $T$–$s$ diagram each real state sits to the right of the ideal one.

The ratios can be recovered from measurements, as in 2023-24 Q2. With negligible kinetic energy between the diffuser exit and the nozzle entry, static equals stagnation pressure there, so $\Gamma_d = p_2/p_{01}$ and $\Gamma_c = p_3/p_2$, and a measured exit temperature $T_4$ with full expansion gives $p_{04} = p_a(T_{03}/T_4)^{\gamma/(\gamma-1)}$.

| Case | $\Gamma_d$ | $\Gamma_c$ | $\Gamma_n$ | Result |
|---|---|---|---|---|
| PS4 Q4.2 (M 3.5) | 0.75 | 0.90 | 0.80 | $p_{04}/p_a = 41.2$ (ideal 76.3); $F/\dot m = 877$ |
| 2018-19 Q4 (M 2.5) | 0.85 | 0.90 | 0.80 | $F/\dot m = 971$ against 1088 ideal |
| 2020-21 Q2 (M 2.5) | 0.87 | 0.94 | 0.72 | $F/\dot m = 951$ |
| 2023-24 Q2 (M 3.2) | 0.600 | 0.900 | 0.708 | $F = 180$ kN, 83 % of the ideal 216 kN |

![[prop_e2324_q2_ramjet_Ts.png|600]]

## Related

- [[Intake Pressure Recovery]] · [[Ramjet]] · [[Isentropic Efficiency]] · [[Entropy Change of a Perfect Gas]]

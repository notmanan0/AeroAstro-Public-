---
title: "Isentropic Efficiency"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["compressor efficiency", "turbine efficiency", "diffuser efficiency", "adiabatic efficiency"]
tags: [sesa2023, concept, thermodynamics, turbomachinery]
status: complete
parent_lectures: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Entropy Change of a Perfect Gas]]", "[[Steady Flow Energy Equation]]", "[[Component Stagnation Pressure Ratios]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Isentropic Efficiency

## Definition

> [!note] Definition
> $$\eta_c = \frac{\text{ideal work in}}{\text{actual work in}} = \frac{T_{2s}-T_1}{T_2-T_1},\qquad \eta_t = \frac{\text{actual work out}}{\text{ideal work out}} = \frac{T_1-T_2}{T_1-T_{2s}}$$
> Both compare against the isentropic process **to the same exit pressure**. Use stagnation temperatures for machines.

## Explanation
**Recipe**:
1. Isentropic exit: $T_{2s} = T_1(p_2/p_1)^{(\gamma-1)/\gamma}$.
2. Apply the definition to get $T_2$.
3. Work: $w = c_p|\Delta T|$.

For a turbine you usually know the **work** (from the spool balance), which gives $T_{05}$. Then $T_{05s} = T_{04}-(T_{04}-T_{05})/\eta_t$, and **only then** the pressure ratio $p_{04}/p_{05} = (T_{04}/T_{05s})^{\gamma/(\gamma-1)}$. A common error is to apply the isentropic relation to the *actual* $T_{05}$.

**Checks**: $\eta<1$, and the real exit is hotter than the isentropic exit for **both** machines, so $w_c>w_{c,s}$ and $w_t<w_{t,s}$.

**Diffuser efficiency**: $\eta_d = (T_{2s}-T_1)/(T_{02}-T_1)$. It relates to the pressure recovery by
$$\eta_d = \frac{\Gamma_d^{(\gamma-1)/\gamma}\big(1+\tfrac{\gamma-1}{2}M^2\big)-1}{\tfrac{\gamma-1}{2}M^2}$$

Net work is the *difference* of turbine and compressor work, so it is very sensitive to $\eta$. In PS7 Q7.3, going from 90 % to 85 % efficiency cuts net work by 22 % and $\eta_{th}$ from 0.50 to 0.40.

![[prop_isentropic_efficiency_Ts.png|700]]

## Examples
- Compressor $r_p = 45$ from 288 K, $\eta_c = 0.9$: $T_{03s} = 854.6$ K, $T_{03} = 917.5$ K, $w_c = 632$ kJ/kg.
- Turbine 1750 K, 45:1, $\eta_t = 0.9$: $w_t = 1049$ kJ/kg.
- Turbine 30 bar/1500 K to 1 bar, $\eta_t = 0.85$: $T_5 = 707.5$ K, $w_t = 796.5$ kJ/kg.

## Related
- [[Entropy Change of a Perfect Gas]] · [[Steady Flow Energy Equation]] · [[Component Stagnation Pressure Ratios]]

## Sources
- Week 2 notes §2.5.4; Week 4 notes eq. 3.11; Data Book p. 15

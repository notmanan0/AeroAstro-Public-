---
title: "Thermal and Overall Efficiency"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["eta_th", "eta_O", "fuel efficiency", "overall efficiency"]
tags: [sesa2023, concept, efficiency]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Propulsive Efficiency]]", "[[Thrust Specific Fuel Consumption]]", "[[Brayton Cycle]]", "[[Calorific Value]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Thermal and Overall Efficiency

## Definition

> [!note] Definition
>
> $$\eta_{th} = \frac{\text{jet power}}{\text{fuel heat}} = \frac{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}{\dot m_fLCV},\qquad \eta_O = \frac{FV_0}{\dot m_fLCV} = \eta_P\,\eta_{th} = \frac{V_0}{\text{TSFC}\cdot LCV}$$

## Explanation
- An aero engine has **no shaft output and no external heat input**, so the closed-cycle "thermal efficiency" is redefined around jet kinetic power and fuel chemical energy. The data book calls it the **fuel efficiency** $\eta_f$.
- With $f\ll1$ and full expansion:

  $$\eta_{th} = \frac{V_j^2-V_0^2}{2f\,LCV},\qquad\eta_O = \frac{V_0(V_j-V_0)}{f\,LCV}$$

- Splitting $\eta_O$ separates the **cycle** (pressure ratio, TET, component efficiencies) from **propulsion** (jet velocity).
- The overall-efficiency derivation (2017-18 Q1(ii), 20 marks) is: aircraft power over fuel power, then factorise into $\eta_P\times\eta_{th}$. The numerators and denominators have the physical meanings above.
- Trends: modern engines have $\eta_P\approx0.6$–0.7, $\eta_{th}\approx0.5$–0.6 and $\eta_O\approx0.3$–0.4. Ideal-cycle thermal efficiencies are much higher, e.g. 60–80 % for ideal ramjets.
- In the W07 turbofan exercises, "overall efficiency" is defined as $F_NV/[c_p(T_{04}-T_{03})]$, i.e. relative to the heat added.

## Examples
- Turbojet worked example (M 2, 31,000 ft): $\eta_O = 43.1\%$, $\eta_{th} = 54.3\%$, $\eta_P = 79.4\%$.
- Ideal ramjet 2013-14: $\eta_O = 78.8\%$, $\eta_P = 91.1\%$, $\eta_{th} = 86.5\%$ (ideal, and very fast at M 5.7).
- Propane ramjet 2023-24 Q1(iv): $\eta_O = 16.0\%$.

## Related
- [[Propulsive Efficiency]] · [[Thrust Specific Fuel Consumption]] · [[Brayton Cycle]] · [[Calorific Value]]

## Sources
- Week 1 notes §1.4.2; Data Book p. 16

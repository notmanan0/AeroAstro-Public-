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

For an aero engine, the **thermal efficiency** is the jet power produced per unit of fuel heat, and the **overall efficiency** is the thrust power delivered per unit of fuel heat:

$$
\eta_{th} = \frac{\tfrac12\dot m_a[(1+f)V_j^2-V_0^2]}{\dot m_fLCV},\qquad \eta_O = \frac{FV_0}{\dot m_fLCV} = \eta_P\,\eta_{th} = \frac{V_0}{\text{TSFC}\cdot LCV} .
$$

An aero engine has no shaft output and no external heat input, so the closed-cycle thermal efficiency is redefined around the jet's kinetic power and the fuel's chemical energy; the Data Book calls it the fuel efficiency $\eta_f$. With $f\ll1$ and full expansion,

$$
\eta_{th} = \frac{V_j^2-V_0^2}{2f\,LCV},\qquad\eta_O = \frac{V_0(V_j-V_0)}{f\,LCV} .
$$

Splitting $\eta_O = \eta_P\eta_{th}$ separates the cycle (pressure ratio, turbine entry temperature, component efficiencies) from the propulsion (jet velocity). The derivation was a 20-mark question in 2017-18 Q1(ii): aircraft power over fuel power, factorised into the two efficiencies. Modern engines have $\eta_P\approx0.6$–0.7, $\eta_{th}\approx0.5$–0.6 and $\eta_O\approx0.3$–0.4, while ideal cycles are much higher, 60–80 % for ideal ramjets. Note that the W07 turbofan exercises define overall efficiency as $F_NV/[c_p(T_{04}-T_{03})]$, relative to the heat added.

Worked values: the M 2, 31,000 ft turbojet example has $\eta_O = 43.1\%$, $\eta_{th} = 54.3\%$ and $\eta_P = 79.4\%$; the 2013-14 ideal ramjet, very fast at M 5.7, has $\eta_O = 78.8\%$, $\eta_P = 91.1\%$ and $\eta_{th} = 86.5\%$; the 2023-24 Q1(iv) propane ramjet manages $\eta_O = 16.0\%$.

## Related

- [[Propulsive Efficiency]] · [[Thrust Specific Fuel Consumption]] · [[Brayton Cycle]] · [[Calorific Value]]

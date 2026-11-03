---
title: "Thrust Specific Fuel Consumption"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["TSFC", "sfc", "specific fuel consumption"]
tags: [sesa2023, concept, efficiency]
status: complete
parent_lectures: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
related_concepts: ["[[Thermal and Overall Efficiency]]", "[[Breguet Range Equation]]"]
sources: ["02 - Sources/Lectures/Week 01 - Introduction and Fundamentals.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Thrust Specific Fuel Consumption

**Thrust specific fuel consumption** is the fuel mass flow per unit thrust,

$$
\text{TSFC} = \frac{\dot m_f}{F} = \frac{f}{F/\dot m_a},
$$

in kg s⁻¹ N⁻¹, usually quoted in g s⁻¹ kN⁻¹ or mg N⁻¹ s⁻¹. Lower is better, and it sets the range directly through the [[Breguet Range Equation]].

Since $\text{TSFC} = V_0/(\eta_O\,LCV)$, at a fixed flight speed TSFC is inversely proportional to the overall efficiency, not to the thermal efficiency alone. It isn't a pure engine number, because it rises with flight speed even at constant $\eta_O$. The units are a common trap: $1.614\times10^{-5}$ kg s⁻¹ N⁻¹ is 16.14 g s⁻¹ kN⁻¹, which is also 16.14 mg N⁻¹ s⁻¹.

| Engine | TSFC (g s⁻¹ kN⁻¹) |
|---|---|
| High-bpr turbofan at cruise | ≈ 12–16 |
| Turbojet | ≈ 22–33 |
| Afterburning | 38+ |
| Ramjet at M 3 | ≈ 45 |

Worked values: in PS1 Q1.2, a TSFC of 17 mg N⁻¹ s⁻¹ at $F = 140$ kN gives $\dot m_f = 2.38$ kg/s. The turbojet worked example has 32.55 g s⁻¹ kN⁻¹, and the fpr 1.5 turbofan 12.47 bare and 13.63 installed. In 2020-21 Q3, reheat raises it from 30.5 dry to 37.7.

## Related

- [[Thermal and Overall Efficiency]] · [[Breguet Range Equation]]

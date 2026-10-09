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

## Definition

> [!note] Definition
> $$\text{TSFC} = \frac{\dot m_f}{F} = \frac{f}{F/\dot m_a}\quad[\text{kg s}^{-1}\text{N}^{-1},\text{ usually quoted in g s}^{-1}\text{kN}^{-1}\text{ or mg N}^{-1}\text{s}^{-1}]$$

## Explanation
- It is fuel mass flow per unit thrust. Lower is better, and it sets the range directly (see [[Breguet Range Equation]]).
- $\text{TSFC} = V_0/(\eta_O\,LCV)$. At a *fixed* flight speed, TSFC is inversely proportional to overall efficiency, not to thermal efficiency alone.
- **Unit trap**: $1.614\times10^{-5}$ kg s⁻¹ N⁻¹ = 16.14 g s⁻¹ kN⁻¹ = 16.14 mg N⁻¹ s⁻¹.
- It is not a pure "engine" number: it rises with flight speed even at constant $\eta_O$.
- Typical values:

  | Engine | TSFC (g s⁻¹ kN⁻¹) |
  |---|---|
  | High-bpr turbofan at cruise | ≈ 12–16 |
  | Turbojet | ≈ 22–33 |
  | Afterburning | 38+ |
  | Ramjet at M 3 | ≈ 45 |

## Examples
- PS1 Q1.2: TSFC = 17 mg N⁻¹ s⁻¹ and $F = 140$ kN give $\dot m_f = 2.38$ kg/s.
- Turbojet worked example: 32.55 g s⁻¹ kN⁻¹. Turbofan fpr 1.5: 12.47 bare, 13.63 installed.
- Reheat (2020-21 Q3): 30.5 dry and 37.7 with the afterburner.

## Related
- [[Thermal and Overall Efficiency]] · [[Breguet Range Equation]]

## Sources
- Week 1 notes eq. 1.13; Weeks 6–7 handout

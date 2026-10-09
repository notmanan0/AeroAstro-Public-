---
title: "Calorific Value"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 2: Combustion"
aliases: ["LCV", "HCV", "lower calorific value", "heating value", "heat of combustion"]
tags: [sesa2023, concept, combustion]
status: complete
parent_lectures: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
related_concepts: ["[[Adiabatic Flame Temperature]]", "[[Thermal and Overall Efficiency]]", "[[Stoichiometry and Equivalence Ratio]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf"]
---
# Calorific Value

## Definition

> [!note] Definition
> The heat released per kg of fuel when the reactants and products are both at the reference state (298.15 K, 1 bar), i.e. **isothermal, constant-pressure** combustion:
> $$\dot Q_{out} = \dot m_f\,LCV$$
> The **LCV** leaves product water as **vapour**. The **HCV** condenses it, so HCV > LCV. Propulsion uses the **LCV**.

## Explanation
- **Adiabatic vs isothermal**:
  - Adiabatic combustion keeps $h$ constant and raises $T$.
  - Isothermal combustion keeps $T$ constant and releases heat.
  - On an $h$–$T$ plot, the products' curve lies below the reactants' curve by the LCV at 298 K.
- The pressure dependence is negligible, but the **temperature reference matters**. That is why the three-step path returns reactants to 298 K first (see [[Adiabatic Flame Temperature]]).
- **Data Book Table 1** (LCV, MJ/kg):

  | Fuel | LCV |
  |---|---|
  | H₂ | 120.0 |
  | CH₄ | 50.01 |
  | C₂H₆ | 47.47 |
  | C₃H₈ | 46.36 |
  | C₄H₁₀ | 45.73 |
  | n-octane (liquid) | 44.43 |
  | kerosene (lecture) | 43 |
  | fuels in exam questions | 41–43.5 |
  | 2022-23 gaseous fuel | 26 |

- A **combustion efficiency** $\eta_b = LCV_{eff}/LCV$ accounts for incomplete combustion (ramjet sheets use 0.9–0.95). Use $\eta_bLCV$ in the energy balance, but the **full** LCV in $\eta_O = FV/(\dot m_fLCV)$.
- **Hydrogen**: about 2.8× the energy per kg of kerosene, so it looks great in Breguet terms. But its volumetric energy density is about 4× worse (LH₂ is 71 kg/m³), so tanks are heavy.

## Related
- [[Adiabatic Flame Temperature]] · [[Thermal and Overall Efficiency]] · [[Stoichiometry and Equivalence Ratio]]

## Sources
- Week 5 notes §5.4.1; Lecture 14; Data Book Table 1

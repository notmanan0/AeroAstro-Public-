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

The calorific value is the heat released per kg of fuel when the reactants and products are both at the reference state (298.15 K, 1 bar), that is, in isothermal, constant-pressure combustion: $\dot Q_{out} = \dot m_f\,LCV$. The lower calorific value (LCV) leaves the product water as vapour; the higher value (HCV) condenses it, so HCV > LCV. Propulsion uses the LCV.

Adiabatic combustion keeps $h$ constant and raises $T$, whereas the isothermal combustion that defines the LCV keeps $T$ constant and releases heat; on an $h$–$T$ plot the products' curve lies below the reactants' curve by the LCV at 298 K. The pressure dependence is negligible, but the temperature reference matters, which is why the three-step path for the [[Adiabatic Flame Temperature]] returns the reactants to 298 K first. The Data Book (Table 1) gives:

| Fuel | LCV (MJ/kg) |
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

Incomplete combustion is handled with a combustion efficiency $\eta_b = LCV_{eff}/LCV$; ramjet problem sheets use 0.9–0.95. Use $\eta_bLCV$ in the energy balance but the full LCV in the overall efficiency, $\eta_O = FV/(\dot m_fLCV)$. Hydrogen carries about 2.8 times the energy per kg of kerosene, which looks very good in Breguet terms, but its volumetric energy density is about four times worse (liquid hydrogen is 71 kg/m³), so its tanks are heavy.

## Related

- [[Adiabatic Flame Temperature]] · [[Thermal and Overall Efficiency]] · [[Stoichiometry and Equivalence Ratio]]

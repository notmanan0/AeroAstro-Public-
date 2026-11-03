---
title: "Stoichiometry and Equivalence Ratio"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 2: Combustion"
aliases: ["air-fuel ratio", "AFR", "equivalence ratio", "stoichiometric", "fuel-air ratio", "phi"]
tags: [sesa2023, concept, combustion]
status: complete
parent_lectures: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
related_concepts: ["[[Calorific Value]]", "[[Adiabatic Flame Temperature]]", "[[Gas Mixtures and Dalton's Law]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf"]
---

# Stoichiometry and Equivalence Ratio

A **stoichiometric** mixture has exactly enough oxidiser for complete combustion. Mixtures are described by the air–fuel ratio and the **equivalence ratio**,

$$
AFR = \frac{\dot m_a}{\dot m_f} = \frac1f,\qquad \phi = \frac{AFR_{st}}{AFR} = \frac{f}{f_{st}} = \frac{n_{a,st}}{n_a},
$$

with $\phi<1$ lean (O₂ left in the products), $\phi = 1$ stoichiometric, and $\phi>1$ rich (unburned fuel, CO and H₂ in the products). The equivalence ratio is the same on a mass or molar basis, because only the amount of air changes.

To balance $\mathrm{C}_x\mathrm{H}_y+a(\mathrm{O_2}+3.762\,\mathrm{N_2^*})\to x\,\mathrm{CO_2}+\tfrac y2\mathrm{H_2O}+3.762a\,\mathrm{N_2^*}$, balance C, then H, then O, which gives $a_{st} = x+y/4$. A lean mixture has $a = a_{st}/\phi$, and $(a-a_{st})$ O₂ appears in the products, while the N₂* passes straight through. Each kmol of O₂ comes with $32+3.762(28.15) = 137.9$ kg of air, so $AFR_{st} = a_{st}\times137.9/M_{fuel}$. The product composition, as mole or volume fractions, comes from the balanced moles, with water counted as vapour.

| Fuel | $a_{st}$ | $AFR_{st}$ | $f_{st}$ |
|---|---|---|---|
| CH₄ | 2 | 17.24 | 0.058 |
| C₃H₈ | 5 | 15.67 | 0.064 |
| C₁₀H₂₁ (kerosene, $M\approx141$–162) | 15.25 | 14.9 (or 13.0 with $M = 162$) | ≈ 0.067–0.077 |
| C in pure O₂ | 1 | 32/12 = 2.67 | |

Gas turbines burn very lean overall, $f\approx0.02$–0.03 or $\phi\approx0.3$–0.4, to keep the turbine entry temperature tolerable; the primary zone burns near stoichiometric and dilution air is added afterwards.

Worked values: propane at $AFR = 16$ has $\phi = 0.979$ and products of 11.4 % CO₂, 15.2 % H₂O, 0.4 % O₂ and 73.0 % N₂* ([[SESA2023 Problem Sheet 5 Solutions]]); a stoichiometric propane ramjet with 50 kg/s of air burns $\dot m_f = 50/15.67 = 3.19$ kg/s ([[SESA2023 Exam 2023-24 Solutions]] Q1); kerosene at $f = 0.0386$ ($\phi = 0.50$) gives 6.66 % CO₂, 6.99 % H₂O, 10.1 % O₂ and 76.2 % N₂* ([[SESA2023 Exam 2021-22 Solutions]] Q2(vi)).

## Related

- [[Calorific Value]] · [[Adiabatic Flame Temperature]] · [[Gas Mixtures and Dalton's Law]]

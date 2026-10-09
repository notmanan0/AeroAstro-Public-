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

## Definition

> [!note] Definition
> A **stoichiometric** mixture has exactly enough oxidiser for complete combustion. The ratios are
>
> $$AFR = \frac{\dot m_a}{\dot m_f} = \frac1f,\qquad \phi = \frac{AFR_{st}}{AFR} = \frac{f}{f_{st}} = \frac{n_{a,st}}{n_a}$$
>
> $\phi<1$ is lean (O₂ left in the products), $\phi = 1$ stoichiometric, $\phi>1$ rich (unburned fuel, CO, H₂).

## Explanation
**Balancing $\mathrm{C}_x\mathrm{H}_y+a(\mathrm{O_2}+3.762\,\mathrm{N_2^*})\to x\,\mathrm{CO_2}+\tfrac y2\mathrm{H_2O}+3.762a\,\mathrm{N_2^*}$**: balance C, then H, then O, which gives $a_{st} = x+y/4$. For a lean mixture, $a = a_{st}/\phi$ and $(a-a_{st})$ O₂ appears in the products. N₂* passes through.

Useful data:
- Air per kmol O₂: $32+3.762(28.15) = 137.9$ kg.
- $AFR_{st} = a_{st}\times137.9/M_{fuel}$.

| Fuel | $a_{st}$ | $AFR_{st}$ | $f_{st}$ |
|---|---|---|---|
| CH₄ | 2 | 17.24 | 0.058 |
| C₃H₈ | 5 | 15.67 | 0.064 |
| C₁₀H₂₁ (kerosene, $M\approx141$–162) | 15.25 | 14.9 (or 13.0 with $M = 162$) | ≈ 0.067–0.077 |
| C in pure O₂ | 1 | 32/12 = 2.67 | |

**Product composition** (mole or volume fractions) comes from the balanced moles. Water counts as vapour.

Gas turbines burn **very lean overall** ($f\approx0.02$–0.03, $\phi\approx0.3$–0.4) to keep the turbine entry temperature tolerable. Primary-zone combustion is near stoichiometric, then dilution air is added.

The equivalence ratio is identical on a mass or molar basis, because only the amount of air changes.

## Examples
- Propane at $AFR = 16$: $\phi = 0.979$. Products: 11.4 % CO₂, 15.2 % H₂O, 0.4 % O₂, 73.0 % N₂* ([[SESA2023 Problem Sheet 5 Solutions]]).
- Stoichiometric propane ramjet with 50 kg/s of air: $\dot m_f = 50/15.67 = 3.19$ kg/s ([[SESA2023 Exam 2023-24 Solutions]] Q1).
- Kerosene at $f = 0.0386$ ($\phi = 0.50$): products 6.66 % CO₂, 6.99 % H₂O, 10.1 % O₂, 76.2 % N₂* ([[SESA2023 Exam 2021-22 Solutions]] Q2(vi)).

## Related
- [[Calorific Value]] · [[Adiabatic Flame Temperature]] · [[Gas Mixtures and Dalton's Law]]

## Sources
- Week 5 notes §5.3; Lecture 13; Data Book Tables 1–2

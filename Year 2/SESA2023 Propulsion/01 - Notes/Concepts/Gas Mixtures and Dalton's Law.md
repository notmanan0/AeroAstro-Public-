---
title: "Gas Mixtures and Dalton's Law"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["mass fraction", "mole fraction", "partial pressure", "Dalton's law", "mixture properties"]
tags: [sesa2023, concept, thermodynamics, mixtures]
status: complete
parent_lectures: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]", "[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
related_concepts: ["[[Two-Property Rule and Perfect Gas Model]]", "[[Stoichiometry and Equivalence Ratio]]", "[[Chemical Equilibrium and Dissociation]]"]
sources: ["02 - Sources/Lectures/Week 02 - Thermodynamics.pdf", "02 - Sources/Lectures/Week 05 - Combustion.pdf"]
---
# Gas Mixtures and Dalton's Law

## Definition

> [!note] Definition
>
> $$x_i = \frac{m_i}{m},\quad y_i = \frac{n_i}{n},\quad x_i = y_i\frac{M_i}{M},\quad M = \sum y_iM_i = \Big(\sum\frac{x_i}{M_i}\Big)^{-1},\quad \frac{p_i}{p} = \frac{V_i}{V} = y_i$$
>
> Specific properties are **mass-weighted**: $c_p = \sum x_ic_{p,i}$, $c_v = \sum x_ic_{v,i}$, $h = \sum x_ih_i$. The mixture gas constant is $R = \bar R/M = \sum x_iR_i$.

## Explanation
- **Dalton's law**: each ideal-gas component fills the whole volume as if alone. The partial pressures add to $p$.
- **Amagat's law** (partial volumes) is equivalent for an ideal gas.
- **Extensive properties add** ($U = \sum m_iu_i$). To get specific values, divide by the total mass, which gives mass weights.
- Volume percentages equal **mole** percentages. Air is 21 % O₂ and 79 % N₂* by volume, and 23.2 %/76.8 % by mass.
- $\gamma$ of a mixture is **not** the weighted average of the $\gamma$s. Compute $c_p$ and $c_v$ (or $c_p$ and $R$) first, then divide.

## Examples
- H₂/O₂ (1 : 7.94 by mass): $x_{H_2} = 0.112$ and $y_{H_2} = 0.668$. At 20 bar, $p_{H_2} = 13.36$ bar.
- Mars atmosphere (95 % CO₂, 5 % N₂ by volume; PS2 Q2.2):
  - $M = 43.2$ and $x_{CO_2} = 0.968$;
  - $c_p = 0.827$, $c_v = 0.634$ kJ kg⁻¹ K⁻¹, $\gamma = 1.31$;
  - the sheet prints $c_p = 0.872$, a digit transposition.
- 25 % CO₂ + 75 % N₂* **by mass** (2021-22 Q1): $c_p = 0.978$, $c_v = 0.713$, $\gamma = 1.37$, $M = 30.9$, $R = 269$ J kg⁻¹ K⁻¹.
- Combustion reactants and products: [[SESA2023 Problem Sheet 5 Solutions]] Q5.2 gives $c_{p,r} = 1119$ and $c_{p,p} = 1138$ J kg⁻¹ K⁻¹.

## Related
- [[Two-Property Rule and Perfect Gas Model]] · [[Stoichiometry and Equivalence Ratio]] · [[Chemical Equilibrium and Dissociation]]

## Sources
- Week 2 notes §2.3; Lecture 5; Data Book p. 7

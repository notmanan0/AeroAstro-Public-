---
title: "Chemical Equilibrium and Dissociation"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 2: Combustion"
aliases: ["equilibrium constant", "Le Chatelier", "dissociation", "Kp", "reversible reactions"]
tags: [sesa2023, concept, combustion, equilibrium]
status: complete
parent_lectures: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
related_concepts: ["[[Adiabatic Flame Temperature]]", "[[Gas Mixtures and Dalton's Law]]", "[[Stoichiometry and Equivalence Ratio]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf"]
---
# Chemical Equilibrium and Dissociation

## Definition

> [!note] Definition
> For $aA+bB\rightleftharpoons cC+dD$ at equilibrium (ideal gases, $p$ in bar, $p^\theta = 1$ bar):
> $$K^\theta(T) = \frac{(p_C/p^\theta)^c(p_D/p^\theta)^d}{(p_A/p^\theta)^a(p_B/p^\theta)^b},\qquad p_i = \frac{n_i}{n_{tot}}p$$
> The Data Book Table 5 lists $\ln K^\theta$ against $T$.

## Explanation
- **Le Chatelier**:
  - A rise in $T$ favours the **endothermic** (dissociating) direction.
  - A rise in $p$ favours the side with **fewer moles**, so it suppresses dissociation.
  - A rise in the concentration of a species shifts the equilibrium away from it.
- **Arrhenius** rate $k = Ae^{-E_a/(\bar RT)}$: a lower activation energy or higher $T$ gives faster reactions.
- **Method**:
  1. Global reaction with unknown product moles.
  2. Atom balances, to leave one unknown.
  3. Substitute $p_i = (n_i/n)p$ into $K$.
  4. Solve numerically and discard unphysical roots (negative moles, or more than the atoms allow).
  5. Report mole (volume) fractions.
- **Check the reaction direction in Table 5.** It is written as formation: $\mathrm{CO+\tfrac12O_2\rightleftharpoons CO_2}$, $\mathrm{H_2+\tfrac12O_2\rightleftharpoons H_2O}$, $\mathrm{\tfrac12H_2+OH\rightleftharpoons H_2O}$, $\mathrm{\tfrac12N_2+\tfrac12O_2\rightleftharpoons NO}$. For the reverse reaction, use $K_{rev} = 1/K$ ($\ln K_{rev} = -\ln K$).
- **Pressure**: $K$ cancels the pressure only when the moles are equal on both sides (e.g. NO formation).
- **Why it matters**: dissociation lowers the flame temperature and efficiency, and forms CO and NOₓ (pollutants). Main fuel oxidation can be treated as one-way; only the product equilibria matter.

![[prop_equilibrium_co.png|600]]

## Examples
- 2 CO + 3 O₂ at 2600 K, 3 bar ($K = 16.445$): **2.3 % CO**, 50.6 % O₂, 47.1 % CO₂.
- C + 4 O₂ at 3000 K, 2 bar ($K = 3.034$): 0.211 CO, **5.1 % CO**.
- NO in air at 3000 K, 1 bar ($\ln K = -2.102$): $y_{NO} = 4.6\%$ ([[SESA2023 Problem Sheet 5 Solutions]] Q5.3).
- H₂/O₂ rocket at 3000 K, 40 bar, $\mathrm{H_2O\rightleftharpoons\tfrac12H_2+OH}$: $c = 0.0506$ and $p_{H_2} = 0.99$ bar ([[SESA2023 Exam 2013-14 Solutions]] Q4).

## Related
- [[Adiabatic Flame Temperature]] · [[Gas Mixtures and Dalton's Law]] · [[Stoichiometry and Equivalence Ratio]]

## Sources
- Week 5 notes §5.5; Lecture 15; Data Book Tables 4–5

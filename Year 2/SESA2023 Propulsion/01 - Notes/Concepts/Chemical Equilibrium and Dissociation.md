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

At chemical equilibrium the reaction $aA+bB\rightleftharpoons cC+dD$ satisfies, for ideal gases with $p$ in bar and $p^\theta = 1$ bar,

$$
K^\theta(T) = \frac{(p_C/p^\theta)^c(p_D/p^\theta)^d}{(p_A/p^\theta)^a(p_B/p^\theta)^b},\qquad p_i = \frac{n_i}{n_{tot}}p ,
$$

with $\ln K^\theta$ against $T$ listed in Data Book Table 5.

Le Chatelier's principle predicts the direction of a shift. A rise in temperature favours the endothermic, dissociating direction; a rise in pressure favours the side with fewer moles, so it suppresses dissociation; and adding a species shifts the equilibrium away from it. How fast a reaction gets there follows the Arrhenius rate $k = Ae^{-E_a/(\bar RT)}$, faster for a lower activation energy or a higher temperature. Dissociation matters because it lowers the flame temperature and efficiency and forms CO and NOₓ. The main fuel oxidation can be treated as one-way; only the product equilibria need this treatment.

The method is the same each time:

1. Write the global reaction with unknown product moles.
2. Use atom balances to leave a single unknown.
3. Substitute $p_i = (n_i/n)p$ into $K$.
4. Solve numerically and discard unphysical roots (negative moles, or more than the atoms allow).
5. Report mole (volume) fractions.

Check the reaction direction in Table 5. It is written as formation: $\mathrm{CO+\tfrac12O_2\rightleftharpoons CO_2}$, $\mathrm{H_2+\tfrac12O_2\rightleftharpoons H_2O}$, $\mathrm{\tfrac12H_2+OH\rightleftharpoons H_2O}$ and $\mathrm{\tfrac12N_2+\tfrac12O_2\rightleftharpoons NO}$, so a reverse reaction needs $K_{rev} = 1/K$, or $\ln K_{rev} = -\ln K$. The pressure cancels out of $K$ only when there are equal moles on both sides, as for NO formation.

![[prop_equilibrium_co.png|600]]

Worked values: 2 CO + 3 O₂ at 2600 K and 3 bar ($K = 16.445$) gives 2.3 % CO, 50.6 % O₂ and 47.1 % CO₂; C + 4 O₂ at 3000 K and 2 bar ($K = 3.034$) gives 0.211 mol CO, 5.1 %; NO in air at 3000 K and 1 bar ($\ln K = -2.102$) gives $y_{NO} = 4.6\%$ ([[SESA2023 Problem Sheet 5 Solutions]] Q5.3); an H₂/O₂ rocket at 3000 K and 40 bar, with $\mathrm{H_2O\rightleftharpoons\tfrac12H_2+OH}$, gives $c = 0.0506$ and $p_{H_2} = 0.99$ bar ([[SESA2023 Exam 2013-14 Solutions]] Q4).

## Related

- [[Adiabatic Flame Temperature]] · [[Gas Mixtures and Dalton's Law]] · [[Stoichiometry and Equivalence Ratio]]

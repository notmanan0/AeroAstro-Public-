---
title: "SESA2023 Problem Sheet 5 Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 2: Combustion"
tags:
  - sesa2023
  - tutorial-solutions
  - combustion
sheet: "Problem Sheet 5: Combustion"
theory_notes: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]"]
key_concepts: ["[[Stoichiometry and Equivalence Ratio]]", "[[Adiabatic Flame Temperature]]", "[[Chemical Equilibrium and Dissociation]]", "[[Gas Mixtures and Dalton's Law]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 05.pdf"]
---

# SESA2023 Problem Sheet 5 Solutions

> [!abstract] Sheet Info
> Propane–air stoichiometry, the adiabatic flame temperature, and NO equilibrium in hot air. All the printed answers are reproduced ✔. Data: $M_{N_2^*} = 28.15$; LCV(C₃H₈) = 46.36 MJ/kg (Data Book Table 1).

## Theory Links
- [[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]
- [[Stoichiometry and Equivalence Ratio]] · [[Adiabatic Flame Temperature]] · [[Chemical Equilibrium and Dissociation]]

---

## Q5.1: Complete combustion of propane in air
### (a) Stoichiometric reaction
Balance C: $b_1 = 3$. Balance H: $2b_2 = 8$, so $b_2 = 4$. Balance O: $2a = 2(3)+4$, so $a = 5$.

$$
\boxed{\mathrm{C_3H_8+5\big(O_2+\tfrac{79}{21}N_2^*\big)\to3CO_2+4H_2O+18.81N_2^*}}\;✔
$$

$AFR_{st} = \dfrac{5(32+3.762\times28.15)}{44} = \dfrac{5(137.9)}{44} = 15.67$.

### (b) At $AFR = 16$
$a = 16(44)/137.9 = 5.105$, so the excess O₂ is $a-5 = 0.105$:

$$
\boxed{\mathrm{C_3H_8+5.105\big(O_2+\tfrac{79}{21}N_2^*\big)\to3CO_2+4H_2O+0.105O_2+19.21N_2^*}}\;✔
$$

### (c) Equivalence ratio
$\phi = 15.67/16 = \boxed{0.979}$ (slightly lean) ✔

### (d) Volumetric composition
The total is $3+4+0.105+19.21 = 26.31$ kmol:

| Species | CO₂ | H₂O | O₂ | N₂* |
|---|---|---|---|---|
| Volume % | **11.4** | **15.2** | **0.4** | **73.0** |

All ✔.

## Q5.2: Flame temperature, reactants at 500 K and 1 bar, $AFR = 16$
### (a) Mixture $c_p$ (mass-weighted)
- **Reactants**: 44 kg of fuel with 704 kg of air.
  $$c_{p,r} = \frac{44(2.547)+704(1.030)}{748} = \boxed{1119\text{ J kg}^{-1}\text{K}^{-1}}\;✔$$
- **Products** (masses per kmol of fuel): CO₂ 132 kg, H₂O 72 kg, O₂ 3.37 kg, N₂* 540.6 kg; 748 kg in total (mass is conserved ✔).
  $$c_{p,p} = \frac{132(1.015)+72(1.981)+3.37(0.972)+540.6(1.056)}{748} = \boxed{1138\text{ J kg}^{-1}\text{K}^{-1}}\;✔$$

### (b) Exhaust temperature
Take the three-step path (reactants 500 K → 298 K, isothermal reaction, products 298 K → $T_2$), per kg of mixture:

$$
T_2 = 298+\frac{LCV/(AFR+1)+c_{p,r}(500-298)}{c_{p,p}} = 298+\frac{46.36\times10^6/17+1119(202)}{1138} = \boxed{2893\text{ K}}\;✔
$$

In reality, dissociation at this temperature would lower it noticeably (see Q5.3 and [[Chemical Equilibrium and Dissociation]]).

## Q5.3: Equilibrium NO in air at 3000 K and 1 bar (pure N₂)
The reaction is $\tfrac12\mathrm{N_2}+\tfrac12\mathrm{O_2}\rightleftharpoons\mathrm{NO}$. Table 5 gives $\ln K^\theta = -2.102$ at 3000 K, so $K = 0.1222$.

Per kmol of air, form $x$ kmol of NO: $n_{O_2} = 0.21-x/2$, $n_{N_2} = 0.79-x/2$, and the total stays 1 kmol. The moles are equal on both sides, so the **pressure cancels**:

$$
K = \frac{x}{\sqrt{(0.21-x/2)(0.79-x/2)}} = 0.1222\;\Rightarrow\;x = \boxed{0.046}\ (4.6\%\ \text{NO})\;✔
$$

Iteration: $x_0 = 0.1222\sqrt{0.21\times0.79} = 0.0498$, then $0.0460$, then $0.0463$.

This shows why NOₓ is so sensitive to peak flame temperature. It is the main reason modern combustors avoid near-stoichiometric hot spots.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 05.pdf`. All values checked in Python.

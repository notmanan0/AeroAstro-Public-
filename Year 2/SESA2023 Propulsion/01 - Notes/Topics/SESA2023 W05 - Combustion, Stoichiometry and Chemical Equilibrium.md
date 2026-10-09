---
title: "SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 2: Combustion"
order: 5
tags:
  - sesa2023
  - combustion
  - stoichiometry
  - adiabatic-flame-temperature
  - chemical-equilibrium
aliases: ["Combustion", "Adiabatic flame temperature"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]]"]
next_topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
key_concepts: ["[[Stoichiometry and Equivalence Ratio]]", "[[Calorific Value]]", "[[Adiabatic Flame Temperature]]", "[[Chemical Equilibrium and Dissociation]]", "[[Gas Mixtures and Dalton's Law]]"]
tutorial_sheets: ["[[SESA2023 Problem Sheet 5 Solutions]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf"]
---

# SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium

> [!abstract] Summary
> Earlier weeks modelled combustion as "heat added to air". This week does it properly:
> 1. **Balance atoms** to get the stoichiometric air requirement, the **air–fuel ratio** and the **equivalence ratio** $\phi$.
> 2. Use the tabulated **lower calorific value** (heat released by *isothermal* combustion at 298 K).
> 3. Find the **adiabatic flame temperature** by a three-step path: cool the reactants to 298 K, react isothermally, then heat the products.
> 4. Recognise that products **dissociate** at high temperature (CO₂ ⇌ CO + ½O₂). **Equilibrium constants** fix the composition. Le Chatelier's principle predicts the trends.

## Key Concepts
- [[Stoichiometry and Equivalence Ratio]] · [[Calorific Value]] · [[Adiabatic Flame Temperature]] · [[Chemical Equilibrium and Dissociation]]

---

## 1. Combustion chemistry (Lecture 13)
- **Atoms and mass are conserved**; molecules and moles are not. For example, $\mathrm{CO+\tfrac12O_2\to CO_2}$ gives $28+16 = 44$ kg.
- Write the equation per kmol of fuel and balance C, then H, then O.
- **Global vs elementary reactions**: a global reaction only gives the ratios of reactants to products. Elementary reactions describe actual molecular collisions and their rates.
- **Air**: 21 % O₂ and 79 % "atmospheric nitrogen" N₂* by volume (23.2 %/76.8 % by mass). N₂* is inert here. Per kmol O₂ there are $79/21 = 3.762$ kmol N₂*, and $1+3.762$ kmol of air weighs $32+3.762(28.15) = 137.9$ kg.

$$
\mathrm{CH_4+2\big(O_2+3.762N_2^*\big)\to CO_2+2H_2O+7.52N_2^*}
$$

**Air–fuel ratio** (mass basis, the inverse of $f$):

$$
AFR = \frac{\dot m_a}{\dot m_f},\qquad AFR_{st,CH_4} = \frac{2(137.9)}{16} = 17.24
$$

**Complete combustion** means all C goes to CO₂ and all H to H₂O. It releases the maximum energy. Incomplete combustion leaves fuel, CO, C (soot) or H₂. It can be caused by a lack of O₂, or by poor mixing, flow or temperature conditions.

**Equivalence ratio**:

$$
\phi = \frac{AFR_{st}}{AFR} = \frac{n_{a,st}}{n_a}\qquad\begin{cases}\phi>1 & \text{fuel-rich}\\ \phi = 1 & \text{stoichiometric}\\ \phi<1 & \text{fuel-lean (excess O}_2\text{ in products)}\end{cases}
$$

The value is the same on a mass or molar basis, because only the amount of air changes.

> [!example] Methane at $\phi = 0.5$
> $AFR = 17.24/0.5 = 34.48$. The air is doubled to $4(\mathrm{O_2+3.762N_2^*})$ and 2 O₂ appears in the products.

> [!example] Kerosene (≈C₁₀H₂₁) at $\phi = 0.2$
> Stoichiometric: C gives $b_1 = 10$, H gives $b_2 = 10.5$, O gives $a_{st} = 10+10.5/2 = 15.25$. Then $a = 15.25/0.2 = 76.25$:
>
> $$\mathrm{C_{10}H_{21}+76.25(O_2+3.762N_2^*)\to10CO_2+10.5H_2O+61O_2+286.8N_2^*}$$
>
> $AFR_{st} = 15.25(137.9)/141 = 14.9$, so $f_{st}\approx0.067$. Gas turbines run at an overall $f\approx0.02$–0.025, i.e. $\phi\approx0.3$–0.4.

## 2. Combustion thermodynamics (Lecture 14)
- **Adiabatic, constant-pressure combustion** ($\dot Q = \dot W = 0$): $h_{out} = h_{in}$. The temperature rises because chemical energy becomes thermal energy.
- **Isothermal combustion** ($T_{out} = T_{in}$): heat $\dot Q_{out} = \dot m(h_{in}-h_{out})$ must be removed. At 298 K and 1 bar this defines the **calorific value**.
- **LCV** leaves water as vapour. **HCV** condenses it, releasing more. Propulsion always uses the LCV. Data Book Table 1: H₂ 120, CH₄ 50.01, C₃H₈ 46.36, n-octane 44.43 MJ/kg; kerosene is taken as 43 MJ/kg.

### Steady-flow adiabatic combustion (three-step path)
1. Take the reactants from $T_1$ to $T_0 = 298$ K: $\dot Q_{10} = \dot mc_{p,r}(T_0-T_1)$.
2. React at $T_0$: $\dot Q_r = -\dot m_f\,LCV$.
3. Heat the products from $T_0$ to $T_2$: $\dot Q_{02} = \dot mc_{p,p}(T_2-T_0)$.

The sum is zero:

$$
\dot Q-\dot W_x = \sum_{react}\dot m_i(h_{i,0}-h_{i,1})-\dot m_f\,LCV+\sum_{prod}\dot m_j(h_{j,2}-h_{j,0}) = 0
$$

$$
\boxed{T_2 = T_0+\frac{LCV/(AFR+1)-c_{p,r}(T_0-T_1)}{c_{p,p}}}
$$

> [!example] Stoichiometric CH₄–air, reactants at 400 K
> With $c_{p,r} = 1072$ and $c_{p,p} = 1116$ J kg⁻¹ K⁻¹, **$T_2 = 2854$ K**.
>
> The mixture $c_p$ is found by mass-weighting:
> - reactants $c_{p,r} = (AFR\,c_{p,a}+c_{p,f})/(AFR+1)$;
> - products $c_{p,p} = \sum m_jc_{p,j}/\sum m_j$.

![[prop_adiabatic_flame_temperature.png|640]]

**In gas-turbine form** (fuel supplied at $T_{ref}$), per kg of air:

$$
0 = c_{p,a}(T_{ref}-T_{03})-f\,LCV+(1+f)c_{p,p}(T_{04}-T_{ref})\;\Rightarrow\; f = \frac{c_{p,p}(T_{04}-T_{ref})-c_{p,a}(T_{03}-T_{ref})}{LCV-c_{p,p}(T_{04}-T_{ref})}
$$

This is the formula used for every engine in W06–W07. See [[Adiabatic Flame Temperature]].

## 3. Chemical equilibrium (Lecture 15)
Real reactions run both ways. At high $T$ the products **dissociate**, which makes pollutants (CO, NOₓ) and gives lower efficiency. Fuel oxidation itself is effectively one-way, but its products (CO₂/CO/O₂, H₂O/H₂/OH, N₂/O₂/NO) equilibrate.

**Le Chatelier's principle**: an equilibrium shifts to counteract an imposed change.
- Raising $T$ favours the endothermic direction. For $\mathrm{CO+\tfrac12O_2\to CO_2}$ ($\Delta h<0$) that is dissociation.
- Raising $p$ favours the side with fewer moles, i.e. less dissociation.

**Equilibrium constant** (Table 5; a function of $T$ only; partial pressures in bar):

$$
a\,A+b\,B\rightleftharpoons c\,C+d\,D:\qquad K^\theta = \frac{(p_C/p^\theta)^c(p_D/p^\theta)^d}{(p_A/p^\theta)^a(p_B/p^\theta)^b},\qquad p_i = y_ip = \frac{n_i}{n_{tot}}p
$$

**Method**:
1. Write the global reaction with unknown product moles.
2. Use atom balances to express everything in one unknown.
3. Substitute into $K^\theta$ with $p_i = (n_i/n)p$.
4. Solve numerically and choose the physical root ($0<n_i$).

> [!example] 2 CO + 3 O₂ → $a$CO + $b$O₂ + $c$CO₂ at 2600 K, 3 bar
> - Atom balance: $a = 2-c$ and $b = 3-c/2$.
> - $\ln K = 2.800$, so $K = 16.445$, and $K = \dfrac{c}{(2-c)(3-c/2)^{1/2}}\left(\dfrac{5-c/2}{p}\right)^{1/2}$.
> - Solution: $c = 1.906$, $a = 0.094$, $b = 2.047$, giving **2.3 % CO**, 50.6 % O₂ and 47.1 % CO₂.

> [!example] Carbon in pure O₂ at $\phi = 0.25$, 3000 K, 2 bar
> - $\mathrm{C+4O_2\to aCO+bO_2+cCO_2}$ with $c = 1-a$ and $b = 3+a/2$.
> - $\ln K = 1.110$, so $K = 3.034$, and the cubic gives $a = 0.211$ (the other roots are negative).
> - Composition: 0.211 CO + 3.106 O₂ + 0.789 CO₂, so **CO = 5.1 %** by volume.

![[prop_equilibrium_co.png|640]]

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]] · Next: [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]
- Worked sheet: [[SESA2023 Problem Sheet 5 Solutions]] (propane, flame temperature, NO equilibrium)
- Exams: [[SESA2023 Exam 2013-14 Solutions]] Q4 (H₂O dissociation), [[SESA2023 Exam 2021-22 Solutions]] Q2(vi) (kerosene products), [[SESA2023 Exam 2023-24 Solutions]] Q1 (propane ramjet), [[SESA2023 Exam 2022-23 Solutions]] Q3(iv) (combustor with heat loss)

## Sources
- Week 5 notes and Lectures 13–15; Data Book Tables 1, 2, 4, 5

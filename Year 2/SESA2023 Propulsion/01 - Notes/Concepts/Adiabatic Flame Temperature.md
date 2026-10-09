---
title: "Adiabatic Flame Temperature"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 2: Combustion"
aliases: ["steady flow combustion", "combustor exit temperature", "fuel-air ratio from energy balance"]
tags: [sesa2023, concept, combustion]
status: complete
parent_lectures: ["[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Calorific Value]]", "[[Stoichiometry and Equivalence Ratio]]", "[[Steady Flow Energy Equation]]", "[[Chemical Equilibrium and Dissociation]]"]
sources: ["02 - Sources/Lectures/Week 05 - Combustion.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---
# Adiabatic Flame Temperature

## Definition

> [!note] Definition
> The products' temperature after **adiabatic, constant-pressure** combustion, found with a three-step path:
> 1. Take the reactants from $T_1$ to $T_0 = 298$ K.
> 2. Burn isothermally, releasing $\dot m_fLCV$.
> 3. Heat the products from $T_0$ to $T_2$.
>
> $$0 = \sum_r\dot m_ic_{p,i}(T_0-T_1)-\dot m_f\,LCV+\sum_p\dot m_jc_{p,j}(T_2-T_0)$$

## Explanation
**Premixed form** (all reactants at $T_1$):

$$T_2 = T_0+\frac{LCV/(AFR+1)-c_{p,r}(T_0-T_1)}{c_{p,p}}$$

**Engine form** (air at $T_{03}$, fuel at $T_{ref}$, per kg air):

$$f = \frac{c_{p,p}(T_{04}-T_{ref})-c_{p,a}(T_{03}-T_{ref})}{\eta_bLCV-c_{p,p}(T_{04}-T_{ref})}$$

With a single $c_p$ this becomes $f = \dfrac{T_{04}-T_{03}}{LCV/c_p-(T_{04}-T_{ref})}$.

**Simplified forms used in older papers and PS4**:
- $(1+f)c_pT_{04} = c_pT_{03}+f\,LCV$ (this is $T_{ref} = 0$);
- $f\approx c_p(T_{04}-T_{03})/LCV$.

The differences are about 1–5 %. State your choice.

**With heat loss** (2022-23 Q3): add $\dot Q = -q_{loss}\dot m_f$ on the left, so $f(LCV-q_{loss}-\dots)$.

**Trends**:
- $T_2$ peaks near $\phi\approx1$ (slightly rich in reality).
- Preheating the reactants (a higher $T_1$) raises $T_2$ almost one-for-one.
- Real peak temperatures are lower than the complete-combustion value because of **dissociation** (see [[Chemical Equilibrium and Dissociation]]) and the rising $c_p$.

![[prop_adiabatic_flame_temperature.png|600]]

## Examples
- Stoichiometric CH₄ at 400 K ($c_{p,r} = 1072$, $c_{p,p} = 1116$): **2854 K**.
- Propane at $AFR = 16$, 500 K: **2893 K** ([[SESA2023 Problem Sheet 5 Solutions]] Q5.2).
- Combustor 30 kg/s from 800 K to 1500 K ($c_{p,p} = 1250$, LCV 43): $f = 0.0240$, $\dot m_f = 0.721$ kg/s ([[SESA2023 Problem Sheet 7 Solutions]] Q7.4).
- Turbojet worked example: $f = 0.01111$.

## Related
- [[Calorific Value]] · [[Stoichiometry and Equivalence Ratio]] · [[Steady Flow Energy Equation]] · [[Chemical Equilibrium and Dissociation]]

## Sources
- Week 5 notes §5.4.2; Lecture 14; Weeks 6–7 handout §6.5.1.4; Data Book p. 14

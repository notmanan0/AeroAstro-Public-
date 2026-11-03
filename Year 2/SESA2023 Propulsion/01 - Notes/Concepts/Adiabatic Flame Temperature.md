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

The adiabatic flame temperature is the temperature of the products after adiabatic, constant-pressure combustion. It is found along a three-step path: take the reactants from $T_1$ to $T_0 = 298$ K, burn them isothermally to release $\dot m_fLCV$, then heat the products from $T_0$ to $T_2$:

$$
0 = \sum_r\dot m_ic_{p,i}(T_0-T_1)-\dot m_f\,LCV+\sum_p\dot m_jc_{p,j}(T_2-T_0) .
$$

With all the reactants premixed at $T_1$ this becomes

$$
T_2 = T_0+\frac{LCV/(AFR+1)-c_{p,r}(T_0-T_1)}{c_{p,p}} ,
$$

and in the engine form, with air at $T_{03}$ and fuel at $T_{ref}$, per kg of air,

$$
f = \frac{c_{p,p}(T_{04}-T_{ref})-c_{p,a}(T_{03}-T_{ref})}{\eta_bLCV-c_{p,p}(T_{04}-T_{ref})},
$$

which with a single $c_p$ is $f = (T_{04}-T_{03})/[LCV/c_p-(T_{04}-T_{ref})]$. Older papers and PS4 use simpler forms, $(1+f)c_pT_{04} = c_pT_{03}+f\,LCV$ (that is, $T_{ref} = 0$) or $f\approx c_p(T_{04}-T_{03})/LCV$. They differ by about 1–5 %, so state which one you use. A heat loss, as in 2022-23 Q3, adds $\dot Q = -q_{loss}\dot m_f$ on the left, giving $f(LCV-q_{loss}-\dots)$.

$T_2$ peaks near stoichiometric ($\phi\approx1$, slightly rich in reality), and preheating the reactants raises it almost one-for-one. Real peak temperatures are lower than the complete-combustion value because of dissociation ([[Chemical Equilibrium and Dissociation]]) and the rising $c_p$.

![[prop_adiabatic_flame_temperature.png|600]]

Worked values: stoichiometric CH₄ at 400 K ($c_{p,r} = 1072$, $c_{p,p} = 1116$) reaches 2854 K; propane at $AFR = 16$ and 500 K reaches 2893 K ([[SESA2023 Problem Sheet 5 Solutions]] Q5.2); a combustor taking 30 kg/s from 800 K to 1500 K ($c_{p,p} = 1250$, LCV 43 MJ/kg) needs $f = 0.0240$, or $\dot m_f = 0.721$ kg/s ([[SESA2023 Problem Sheet 7 Solutions]] Q7.4); the turbojet worked example has $f = 0.01111$.

## Related

- [[Calorific Value]] · [[Stoichiometry and Equivalence Ratio]] · [[Steady Flow Energy Equation]] · [[Chemical Equilibrium and Dissociation]]

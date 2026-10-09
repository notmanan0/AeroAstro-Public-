---
title: "SESA1016 T4 - Entropy and Isentropic Relations"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part A: Closed-system Thermodynamics"
order: 4
tags: [sesa1016, entropy, isentropic, second-law]
aliases: ["Entropy"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T3 - Heat Engines and the Second Law]]"]
next_topics: ["[[SESA1016 T5 - Ideal Heat Engine Models]]"]
key_concepts: ["[[Entropy Generation]]", "[[Isentropic Ideal-gas Relations]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 4.pdf"]
---

# SESA1016 T4 - Entropy and Isentropic Relations

> [!abstract] Summary
> Entropy is a property that converts the qualitative second law into an accounting equation. Entropy can cross a boundary with heat, and irreversibilities generate it. It cannot be destroyed. A reversible adiabatic process is therefore isentropic, giving the pressure-volume-temperature relations used throughout ideal cycles.

## 1. Clausius definition

For a reversible differential heat transfer:

$$
dS=\frac{\delta Q_{rev}}{T}
$$

Entropy $S$ is a state property even though heat is path dependent. Units are $\mathrm{J/K}$; specific entropy $s=S/m$ has units $\mathrm{J/(kg\,K)}$.

## 2. Entropy balance

For a closed system:

$$
\boxed{\Delta S=\int_1^2\frac{\delta Q}{T_b}+S_{gen}},\qquad S_{gen}\ge0
$$

- reversible process: $S_{gen}=0$;
- irreversible process: $S_{gen}>0$;
- impossible process: $S_{gen}<0$.

Adiabatic does not automatically mean isentropic. It means the transfer term is zero; entropy can still rise because of friction, mixing or finite gradients.

## 3. Entropy generation by heat transfer

If heat $Q$ passes from a hot reservoir $T_H$ to a cold reservoir $T_C$:

$$
\Delta S_{universe}=-\frac{Q}{T_H}+\frac{Q}{T_C}
=Q\left(\frac1{T_C}-\frac1{T_H}\right)>0
$$

The energy is conserved, yet its capacity to produce work decreases.

## 4. Ideal-gas entropy change

Using $Tds=du+p\,dv$ with $du=c_vdT$ and $p=RT/v$:

$$
\boxed{s_2-s_1=c_v\ln\frac{T_2}{T_1}+R\ln\frac{v_2}{v_1}}
$$

Equivalently, using $Tds=dh-v\,dp$:

$$
\boxed{s_2-s_1=c_p\ln\frac{T_2}{T_1}-R\ln\frac{p_2}{p_1}}
$$

These expressions depend only on end states. Use kelvin and positive absolute ratios inside logarithms.

## 5. Isentropic relations

Set $s_2-s_1=0$ for a calorically perfect ideal gas:

$$
pv^\gamma=C,qquad Tv^{\gamma-1}=C,qquad T^\gamma p^{1-\gamma}=C
$$

Between two states:

$$
\frac{T_2}{T_1}=\left(\frac{v_1}{v_2}\right)^{\gamma-1}
=\left(\frac{p_2}{p_1}\right)^{(\gamma-1)/\gamma}
$$

See [[Isentropic Ideal-gas Relations]].

## 6. Entropy on $T$-$s$ diagrams

For an internally reversible process:

$$
Q_{rev}=\int_1^2T\,dS
$$

Thus area under a path on a $T$-$s$ diagram represents heat transfer. A vertical path is isentropic; a horizontal path is isothermal.

## 7. Common errors

> [!warning] Do not confuse
> - entropy change of the **system** with entropy generation;
> - adiabatic with isentropic;
> - $\delta Q/T$ with an exact differential for an irreversible path;
> - degrees Celsius with kelvin inside $Q/T$ or logarithms.

## Links

- Previous: [[SESA1016 T3 - Heat Engines and the Second Law]]
- Concepts: [[Entropy Generation]] · [[Isentropic Ideal-gas Relations]]
- Tutorial: [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]]
- Continues in Propulsion: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · [[Entropy Change of a Perfect Gas]] · [[Isentropic Efficiency]]
- Next: [[SESA1016 T5 - Ideal Heat Engine Models]]

## Sources

- `02 - Sources/Lectures/Chapter 4.pdf`, §§4.1-4.5.

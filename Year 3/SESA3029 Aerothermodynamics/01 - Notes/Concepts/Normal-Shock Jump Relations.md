---
title: "Normal-Shock Jump Relations"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 1: Basic Toolkit"
aliases: ["normal-shock relations", "Rankine-Hugoniot relations for a perfect gas"]
tags: [sesa3029, concept, normal-shock]
status: complete
parent_lectures: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]"]
related_concepts: ["[[Normal Shock Waves]]", "[[Stagnation Properties]]", "[[Rayleigh Pitot Formula]]"]
sources: ["02 - Sources/Lectures/Lecture1-2.pdf", "02 - Sources/Lectures/Lecture 1-2.txt"]
---

# Normal-Shock Jump Relations

## Definition

> [!note] Definition
> Relations between the upstream state 1 and downstream state 2 of a steady, one-dimensional normal shock in a calorically perfect gas. They follow from conservation of mass, momentum and total enthalpy, not from an isentropic assumption.

## Conservation basis

$$
\rho_1U_1=\rho_2U_2,\qquad
p_1+\rho_1U_1^2=p_2+\rho_2U_2^2,\qquad
h_1+\frac{U_1^2}{2}=h_2+\frac{U_2^2}{2}.
$$

The intermediate Prandtl relation is

$$
U_1U_2=\frac{2a_0^2}{\gamma+1}.
$$

## Final relations

$$
\frac{\rho_2}{\rho_1}=\frac{(\gamma+1)M_1^2}{2+(\gamma-1)M_1^2},
$$

$$
\frac{p_2}{p_1}=1+\frac{2\gamma}{\gamma+1}(M_1^2-1),
$$

$$
\frac{T_2}{T_1}=\frac{p_2/p_1}{\rho_2/\rho_1},\qquad
M_2^2=\frac{2+(\gamma-1)M_1^2}{2\gamma M_1^2-(\gamma-1)}.
$$

> [!note] Derivations
> Full step-by-step derivations of all four jumps and the strong-shock limits are in [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Density jump (shown in lecture)|W01 §5]]. Shortcut worth remembering: $M_2^2=M_1^2\big/\left[(\rho_2/\rho_1)(p_2/p_1)\right]$.

## Physical interpretation

- $M_1>1$ and $M_2<1$ for a physical compression shock.
- Static pressure, temperature, density and entropy rise.
- Velocity and stagnation pressure fall.
- Stagnation temperature remains constant for an adiabatic shock.

## Related

- [[Normal Shock Waves]] · [[Shock-Table Interpolation]] · [[Rayleigh Pitot Formula]]


---
title: "Rayleigh Pitot Formula"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 1: Basic Toolkit"
aliases: ["Rayleigh-Pitot formula", "supersonic Pitot formula"]
tags: [sesa3029, concept, pitot-probe, normal-shock]
status: complete
parent_lectures: ["[[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes]]"]
related_concepts: ["[[Compressible Pitot Probe]]", "[[Normal-Shock Jump Relations]]", "[[Stagnation Properties]]"]
sources: ["02 - Sources/Lectures/Lecture1-3.pdf", "02 - Sources/Lectures/Lecture 1-3.txt"]
---

# Rayleigh Pitot Formula

## Formula

$$
\boxed{
\frac{p_{02}}{p_1}
=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}
\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}
}
$$

## Derivation route

1. Apply the normal-shock pressure jump $p_2/p_1$.
2. Apply the isentropic stagnation relation $p_{02}/p_2$ to the downstream subsonic flow.
3. Use the normal-shock expression for $M_2(M_1)$.
4. Multiply $p_{02}/p_1=(p_2/p_1)(p_{02}/p_2)$ and simplify.

The key simplification is $1+\tfrac{\gamma-1}{2}M_2^2=\dfrac{(\gamma+1)^2M_1^2}{2\left[2\gamma M_1^2-(\gamma-1)\right]}$. Full algebra: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Deriving the Rayleigh Pitot formula|W01 §7]].

## Application

The left-hand side is measured by a supersonic Pitot-static system. Solve the nonlinear relation for $M_1$, usually with a normal-shock table, interpolation, or a numerical root finder. Then calculate

$$
U_1=M_1\sqrt{\gamma RT_1}.
$$

> [!warning] Pressure label
> The probe reads $p_{02}$ downstream of the shock, not the upstream stagnation pressure $p_{01}$.

## Related

- [[Compressible Pitot Probe]] · [[Normal-Shock Jump Relations]]


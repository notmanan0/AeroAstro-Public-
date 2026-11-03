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

The Rayleigh Pitot formula gives the reading of a Pitot probe in supersonic flow, $p_{02}$, as a ratio to the upstream static pressure:

$$
\boxed{
\frac{p_{02}}{p_1}
=\left[\frac{(\gamma+1)M_1^2}{2}\right]^{\gamma/(\gamma-1)}
\left[\frac{\gamma+1}{2\gamma M_1^2-(\gamma-1)}\right]^{1/(\gamma-1)}
}
$$

It follows the gas along its path into the probe. The flow first crosses the normal part of the detached shock, which gives $p_2/p_1$, and then decelerates isentropically to rest, which gives $p_{02}/p_2$ in terms of $M_2$. Writing $M_2$ in terms of $M_1$ from the normal-shock relations and multiplying, $p_{02}/p_1=(p_2/p_1)(p_{02}/p_2)$, gives the formula. The simplification that makes it tidy is

$$
1+\tfrac{\gamma-1}{2}M_2^2=\dfrac{(\gamma+1)^2M_1^2}{2\left[2\gamma M_1^2-(\gamma-1)\right]}.
$$

Full algebra: [[SESA3029 W01 - Compressible-Flow Toolkit, Normal Shocks and Pitot Probes#Deriving the Rayleigh Pitot formula|W01 §7]].

In practice a supersonic Pitot-static system measures the left-hand side and you solve for $M_1$, usually from the normal-shock table, by interpolation or with a root finder. Then $U_1=M_1\sqrt{\gamma RT_1}$.

> [!warning] Pressure label
> The probe reads $p_{02}$, the stagnation pressure behind the shock, not the free-stream stagnation pressure $p_{01}$.

## Related

- [[Compressible Pitot Probe]] · [[Normal-Shock Jump Relations]]

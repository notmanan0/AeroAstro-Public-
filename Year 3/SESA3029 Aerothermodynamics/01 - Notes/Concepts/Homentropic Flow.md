---
title: "Homentropic Flow"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["homentropic flow", "homentropic", "uniform-entropy flow"]
tags: [sesa3029, concept, thermodynamics, homentropic, isentropic]
status: complete
parent_lectures: ["[[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design]]"]
related_concepts: ["[[Method of Characteristics]]", "[[Entropy Change Across a Shock]]", "[[Isentropic Ideal-gas Relations]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt"]
---

# Homentropic Flow

## Definition

> [!note] Definition
> A flow in which the entropy is the **same everywhere**, not just constant along each streamline: $\nabla s=0$.
>
> **Isentropic** flow only needs $\mathrm Ds/\mathrm Dt=0$ (each particle keeps its entropy). **Homentropic** flow also needs every particle to start with the same entropy (L3-1, ll. 152–156).

## Explanation

**When it holds.** Uniform flow from one reservoir, through regions with **no shocks**. A curved shock gives different streamlines different entropy jumps ([[Entropy Change Across a Shock]]), so the flow behind it is isentropic along each streamline but **not** homentropic.

**What it buys.**

1. Pressure and density are tied together everywhere: $p=C\rho^\gamma$ with one constant $C$. So
   $$\frac{\partial p}{\partial\rho}=\gamma C\rho^{\gamma-1}=\gamma\,\frac{p}{\rho}=\gamma RT=a^2 ,$$
   and $\partial p/\partial l=a^2\,\partial\rho/\partial l$ in any direction. This removes $p$ from the momentum equation (W05 §4).
2. With uniform $T_0$ as well, **Crocco's theorem** makes the flow irrotational. This is the second equation the [[Method of Characteristics]] needs (supplementary note, p. 2).
3. Stagnation pressure and density are the same throughout. Once $M$ is known at a point, the isentropic ratios give every other property.

**Where it fails.** As soon as a shock forms. That is why MoC nozzle design aims for a **shock-free** flow, and why a cancelling wall is used rather than a reflecting one.

## Related

- [[Method of Characteristics]] · [[Isentropic Ideal-gas Relations]] · [[Entropy Change Across a Shock]]
- Detail: [[SESA3029 W05 - Method of Characteristics and Minimum-Length Nozzle Design#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|W05 §4]]

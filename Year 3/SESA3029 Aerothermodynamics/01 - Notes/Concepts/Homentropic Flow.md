---
title: "Homentropic Flow"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["homentropic flow", "homentropic", "uniform-entropy flow"]
tags: [sesa3029, concept, thermodynamics, homentropic, isentropic]
status: complete
parent_lectures: ["[[SESA3029 W05a - Method of Characteristics]]"]
related_concepts: ["[[Method of Characteristics]]", "[[Entropy Change Across a Shock]]", "[[Isentropic Ideal-gas Relations]]"]
sources: ["02 - Sources/Lectures/Lecture3-1.pdf", "02 - Sources/Lectures/Supplementary Note for MoC.pdf", "02 - Sources/Lectures/Lecture 3-1.txt"]
---

# Homentropic Flow

A **homentropic** flow has the same entropy everywhere, $\nabla s=0$. That is stronger than isentropic. Isentropic flow only needs $\mathrm Ds/\mathrm Dt=0$, so each particle keeps its own entropy; homentropic flow also needs every particle to have started with the same value (L3-1, ll. 152–156).

You get it when uniform flow from a single reservoir passes through a region with no shocks. A curved shock breaks it, because different streamlines cross the shock at different angles and pick up different entropy jumps ([[Entropy Change Across a Shock]]). Behind such a shock the flow is still isentropic along each streamline, but no longer homentropic.

The payoff is that pressure and density are tied together by one relation, $p=C\rho^\gamma$, with the same constant $C$ everywhere. Then

$$\frac{\partial p}{\partial\rho}=\gamma C\rho^{\gamma-1}=\gamma\,\frac{p}{\rho}=\gamma RT=a^2 ,$$

so $\partial p/\partial l=a^2\,\partial\rho/\partial l$ in any direction, and $p$ can be removed from the momentum equation (W05a §4). If $T_0$ is uniform as well, Crocco's theorem makes the flow irrotational, which is the second equation the [[Method of Characteristics]] needs (supplementary note, p. 2).

Uniform $s$ on its own does not make the stagnation state uniform. Each point's stagnation state is reached isentropically, so $p_0=C\rho_0^\gamma$ with the same $C$, and the gas law gives $p_0=\rho_0RT_0$. Eliminating $p_0$ leaves $\rho_0^{\gamma-1}=RT_0/C$, so $\rho_0$, and then $p_0$, are uniform only if $T_0$ is too. In the adiabatic, shock-free nozzle flows of W05a and W05b both conditions hold, and once $M$ is known at a point the isentropic ratios give every other property.

All of this is lost as soon as a shock forms. That is why MoC nozzle design aims for a shock-free flow, and why the wall is shaped to be non-reflecting.

## Related

- [[Method of Characteristics]] · [[Isentropic Ideal-gas Relations]] · [[Entropy Change Across a Shock]]
- Detail: [[SESA3029 W05a - Method of Characteristics#4. Momentum along the streamline and homentropic flow (3.1 slides 5–6)|W05a §4]]

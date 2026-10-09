---
title: "Complementary Energy"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, energy-methods]
status: complete
parent: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
---

# Complementary Energy

For a bar loaded along its force-displacement curve $P(\delta)$:

- **strain energy** $U=\displaystyle\int_0^{\delta}P\,d\delta$ is the area **under** the curve (a function of displacement);
- **complementary energy** $U^*=\displaystyle\int_0^{P}\delta\,dP$ is the area **above** the curve, between it and the load axis (a function of load).

Together, $U+U^*=P\delta$ (the rectangle).

## Linear elasticity

For a straight line $P=k\delta$, the two triangles are equal:

$$
U=U^*=\tfrac12P\delta=\frac{P^2}{2k}.
$$

## Why it matters

- $\partial U/\partial\delta_i=P_i$ (Castigliano's **first** theorem, valid for nonlinear elastic systems as well).
- $\partial U^*/\partial P_i=\delta_i$ (Castigliano's **second** theorem / Engesser). Only because $U^*=U$ for linear systems can we write $\delta_i=\partial U/\partial P_i$ ([[Castigliano Second Theorem]]).

## Warning

For a **nonlinear** material or geometry, $U\ne U^*$. Differentiating $U$ with respect to a load then gives the wrong displacement. This is a common "why" question: state that the method assumes linear elasticity.

See [[Strain Energy]].

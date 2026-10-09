---
title: "Small Perturbation Linearisation"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["linearisation", "small perturbations", "trim", "decoupling"]
tags: [sesa2027, concept, linearisation]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[State-Space Representation]]", "[[Aerodynamic Stability Derivatives]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["02 - Sources/Lectures/Lecture 1.03.pdf", "02 - Sources/Lectures/Lecture 1.04.pdf"]
---

# Small Perturbation Linearisation

## Definition

> [!note] Definition
> Write every variable as a **trim value plus a small perturbation**:
> $$U = U_\infty+u,\quad V = v,\quad W = w,\quad p,q,r\ \text{small}$$
> Then keep only first-order terms: products of perturbations (e.g. $qw$, $rv$) are dropped. The nonlinear 6-DoF equations become **linear** and **decouple** into longitudinal ($u, w, q, \theta$) and lateral ($v, p, r, \phi, \psi$) sets.

## Explanation
- **Trim**: an equilibrium, $0 = f(\bar{\mathbf x},\bar{\mathbf u})$. Stability axes put $x$ along $U_\infty$, so $\bar V = \bar W = 0$.
- The approximation holds for perturbations up to about ±10 % of trim.
- **Longitudinal result**:

$$
\Delta X = m\dot u,\qquad \Delta Z = m(\dot w-qU_\infty),\qquad \Delta M = I_{yy}\dot q
$$

- **Lateral result**: $\Delta Y = m(\dot v+rU_\infty)$, $\Delta L = I_{xx}\dot p-I_{xz}\dot r$, $\Delta N = -I_{xz}\dot p+I_{zz}\dot r$.
- **Angles**: $\sin\theta\approx\theta$, $\cos\theta\approx1$, and $\alpha\approx w/U_\infty$.
- **Forces**: first-order Taylor series in the perturbations give the [[Aerodynamic Stability Derivatives]].
- Symmetry about the $xz$-plane ($I_{xy} = I_{yz} = 0$) is what allows the clean decoupling.

## Examples
- $X = m(\dot U+qW-rV)$ becomes $\Delta X = m\dot u$, because $\dot U_\infty = 0$ and $qw$, $rv$ are second order.
- The linearised model is valid only near its trim point. **Gain scheduling** re-linearises across the flight envelope ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]).

## Related
- [[State-Space Representation]] · [[Aerodynamic Stability Derivatives]] · [[Design and Analysis Principles]]

## Sources
- Lectures 1.03–1.04; Cook, Ch. 4

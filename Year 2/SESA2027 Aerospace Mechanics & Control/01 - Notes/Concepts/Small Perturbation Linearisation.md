---
title: "Small Perturbation Linearisation"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["linearisation", "small perturbations", "trim", "decoupling", "first-order approximation", "small-perturbation theory"]
tags: [sesa2027, concept, linearisation]
status: complete
parent_lectures: ["[[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[State-Space Representation]]", "[[Aerodynamic Stability Derivatives]]", "[[Euler Angles and Rotation Matrices]]"]
sources: ["02 - Sources/Lectures/Lecture 1.03.pdf", "02 - Sources/Lectures/Lecture 1.04.pdf", "Cook, Ch. 4"]
---

# Small Perturbation Linearisation

Small-perturbation linearisation writes every variable as a trim value plus a small perturbation and keeps only first-order terms:

$$
U = U_\infty+u,\quad V = v,\quad W = w,\quad p,q,r\ \text{small}.
$$

Products of perturbations such as $qw$ and $rv$ are dropped, so the nonlinear six-degree-of-freedom equations become linear and split into a longitudinal set ($u, w, q, \theta$) and a lateral set ($v, p, r, \phi, \psi$).

The trim point is an equilibrium, $0 = f(\bar{\mathbf x},\bar{\mathbf u})$, and stability axes put $x$ along $U_\infty$ so that $\bar V = \bar W = 0$. Taking $X = m(\dot U+qW-rV)$ as an example, $\dot U_\infty = 0$ and $qw$, $rv$ are second order, so it becomes $\Delta X = m\dot u$. Doing the same to all six equations gives

$$
\Delta X = m\dot u,\qquad \Delta Z = m(\dot w-qU_\infty),\qquad \Delta M = I_{yy}\dot q
$$

for the longitudinal set and $\Delta Y = m(\dot v+rU_\infty)$, $\Delta L = I_{xx}\dot p-I_{xz}\dot r$, $\Delta N = -I_{xz}\dot p+I_{zz}\dot r$ for the lateral set. The clean split relies on the aircraft being symmetric about its $xz$-plane, so that $I_{xy} = I_{yz} = 0$. Angles are small too ($\sin\theta\approx\theta$, $\cos\theta\approx1$, $\alpha\approx w/U_\infty$), and expanding the forces and moments as first-order Taylor series in the perturbations gives the [[Aerodynamic Stability Derivatives]].

The course takes the approximation as good for perturbations up to about ±10 % of trim. A linearised model is valid only near its own trim point, which is why gain scheduling re-linearises across the flight envelope ([[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]).

## Related

- All six equations linearised: [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion#Simplifications|A1]]
- [[State-Space Representation]] · [[Aerodynamic Stability Derivatives]] · [[Design and Analysis Principles]]
- Year 3: [[SESA3047 5.1 - State-Space Form and Linearisation]] · [[Linearisation about an Equilibrium Point]]

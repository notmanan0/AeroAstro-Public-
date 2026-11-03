---
title: "Flow Past a Cylinder"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["cylinder flow", "lifting cylinder", "non-lifting cylinder", "doublet in uniform flow"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Kutta-Joukowski Theorem]]", "[[D'Alembert's Paradox]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# Flow Past a Cylinder

Uniform flow plus a doublet of strength $\kappa = 2\pi V_\infty R^2$ gives the flow round a circular cylinder of radius $R$, and adding a vortex $\Gamma$ gives the lifting cylinder:

$$
\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi}\ln\frac rR .
$$

Differentiating gives the velocity field,

$$
V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right),\qquad V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r},
$$

and on the surface, $r = R$, $V_r = 0$ and $V_\theta = -2V_\infty\sin\theta-\Gamma/(2\pi R)$, so

$$
C_p = 1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2 .
$$

Without circulation this is $C_p = 1-4\sin^2\theta$, with stagnation points at $0$ and $\pi$ and $C_{p,min} = -3$ at the shoulders. Circulation moves the stagnation points to $\sin\theta = -\Gamma/(4\pi RV_\infty)$; they stay on the surface while $\Gamma\le4\pi RV_\infty$, and beyond that the stagnation point lifts off the body. Integrating the pressure gives $L' = \rho V_\infty\Gamma$ ([[Kutta-Joukowski Theorem]]) and $D' = 0$ ([[D'Alembert's Paradox]]), and with reference length $2R$ the lift coefficient is $c_l = \Gamma/(RV_\infty)$.

Two variations come up in exams. A half-cylinder on a wall, such as a hangar, uses the upper half of the solution directly, because the ground is the $\psi = 0$ symmetry line. A taller or flatter bump is modelled by picking a streamline $\psi>0$ above the cylinder, as in the river-dune problem.

![[pf_lifting_cylinder.png|520]]

Past-paper uses: a lifting cylinder with $c_l = -2.82$, giving $C_{p,min} = -5$ ([[SESA2022 Exam 2016-17 Solutions]] Q1); a semicircular hangar with 1620 N/m² suction ([[SESA2022 Exam 2018-19 Solutions]] Q1); the dune streamline and tidal power ([[SESA2022 Exam 2023-24 Solutions]] Q2).

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#7. Example 2: flow past a circular cylinder (uniform flow + doublet)|T3 §7]]
- [[Elementary Potential Flows]] · [[Kutta-Joukowski Theorem]] · [[D'Alembert's Paradox]] · [[Rankine Oval]]

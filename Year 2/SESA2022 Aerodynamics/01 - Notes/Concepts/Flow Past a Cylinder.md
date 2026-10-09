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
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Flow Past a Cylinder

## Definition

> [!note] Definition
> Uniform flow plus a doublet of strength $\kappa = 2\pi V_\infty R^2$ gives flow round a circular cylinder of radius $R$. Adding a vortex $\Gamma$ gives the **lifting cylinder**:
>
> $$\psi = V_\infty r\sin\theta\left(1-\frac{R^2}{r^2}\right)+\frac{\Gamma}{2\pi}\ln\frac rR$$

## Explanation
**Velocities**:

$$
V_r = V_\infty\cos\theta\left(1-\frac{R^2}{r^2}\right),\qquad V_\theta = -V_\infty\sin\theta\left(1+\frac{R^2}{r^2}\right)-\frac{\Gamma}{2\pi r}
$$

**On the surface** ($r = R$): $V_r = 0$ and $V_\theta = -2V_\infty\sin\theta-\dfrac{\Gamma}{2\pi R}$, so

$$
C_p = 1-\left(2\sin\theta+\frac{\Gamma}{2\pi RV_\infty}\right)^2
$$

- **Non-lifting**: $C_p = 1-4\sin^2\theta$. The stagnation points are at $0$ and $\pi$, and $C_{p,min} = -3$ at the shoulders.
- **Lifting**: the stagnation points move to $\sin\theta = -\Gamma/(4\pi RV_\infty)$, on the surface while $\Gamma\le4\pi RV_\infty$. Beyond that the stagnation point lifts off the body.
- Integrating the pressure gives $L' = \rho V_\infty\Gamma$ (see [[Kutta-Joukowski Theorem]]) and $D' = 0$ (see [[D'Alembert's Paradox]]). With reference length $2R$, $c_l = \Gamma/(RV_\infty)$.
- **Half-cylinder on a wall** (hangar): the ground is the $\psi = 0$ symmetry line, so the upper half of the solution applies directly.
- **Taller or flatter bumps**: pick a streamline $\psi>0$ above the cylinder, as in the river-dune problem.

![[pf_lifting_cylinder.png|520]]

## Examples
- Lifting cylinder with $c_l = -2.82$, giving $C_{p,min} = -5$: [[SESA2022 Exam 2016-17 Solutions]] Q1.
- Semicircular hangar with 1620 N/m² suction: [[SESA2022 Exam 2018-19 Solutions]] Q1.
- Dune streamline and tidal power: [[SESA2022 Exam 2023-24 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]]
- Related concepts: [[Elementary Potential Flows]], [[Kutta-Joukowski Theorem]], [[D'Alembert's Paradox]], [[Rankine Oval]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`

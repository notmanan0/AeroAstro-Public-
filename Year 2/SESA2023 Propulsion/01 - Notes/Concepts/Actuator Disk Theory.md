---
title: "Actuator Disk Theory"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["momentum theory", "Froude theory", "propeller", "advance ratio"]
tags: [sesa2023, concept, turbomachinery, propellers]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Propulsive Efficiency]]", "[[Velocity Triangles]]", "[[Thrust Equation]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf", "03 - Exams & Past Papers/SESA2023-202324-02-SESA2023.pdf"]
---
# Actuator Disk Theory

## Definition

> [!note] Definition
> Model a propeller as an infinitely thin disk of area $A$ that adds a uniform pressure jump $\Delta p$ to a streamtube, with no swirl and no losses. Then
>
> $$V_{disk} = \tfrac12(V_\infty+V_j),\qquad T = \dot m(V_j-V_\infty) = A\,\Delta p,\qquad\eta_P = \frac{2}{1+V_j/V_\infty}$$

## Explanation
**Derivation** (2023-24 Q4(iv)):
1. Continuity through the disk gives $\dot m = \rho AV_{disk}$. The velocity is continuous across the disk; the pressure jumps.
2. The momentum balance on the whole streamtube (with $p_\infty$ on its boundary) gives $T = \dot m(V_j-V_\infty)$.
3. Bernoulli upstream: $p_\infty+\tfrac12\rho V_\infty^2 = p_u+\tfrac12\rho V_{disk}^2$. Downstream: $p_d+\tfrac12\rho V_{disk}^2 = p_\infty+\tfrac12\rho V_j^2$.
4. So $\Delta p = p_d-p_u = \tfrac12\rho(V_j^2-V_\infty^2)$.
5. Setting $T = A\Delta p$: $\rho AV_{disk}(V_j-V_\infty) = \tfrac12\rho A(V_j-V_\infty)(V_j+V_\infty)$, which gives $V_{disk} = \tfrac12(V_\infty+V_j)$.

**Half the velocity increase happens upstream of the disk.**

**Distributions along the stream** (sketch, 2023-24 Q4(iii)):
- **Axial velocity** rises smoothly from $V_\infty$ to $V_{disk}$ at the disk, then on to $V_j$.
- **Static pressure** falls below $p_\infty$ ahead of the disk (the flow is accelerating), **jumps up** by $\Delta p$ at the disk, then falls back to $p_\infty$ far downstream.
- **Stagnation pressure** is constant ($p_{0\infty}$) upstream, **jumps** by $\Delta p$ at the disk, then stays constant.

**Advance ratio**: $J = V_\infty/(nD)$, with $n$ in rev/s. The tip speed is $U_{tip} = \pi nD = \pi V_\infty/J$.

**Blade-element velocity triangles** (cruise):
- The relative inlet velocity combines the axial $V_{disk}$ with the tangential $\Omega r$.
- The relative inlet angle from the **plane of rotation** is $\tan^{-1}(V_{disk}/\Omega r)$; from the **axial** direction it is $\tan^{-1}(\Omega r/V_{disk})$.
- The blade section is an aerofoil at a small incidence to the relative flow.
- The exit has a small swirl, removed in open rotors by a stator row.

## Examples
- 2023-24 Q4(v): $V_\infty = 100$, $V_j-V_\infty = 20$, $J = 1.1$. Then $V_{disk} = 110$ m/s and $U_{tip} = 285.6$ m/s, so the relative inlet flow angle is **68.9° from axial** (21.1° from the plane of rotation).

## Related
- [[Propulsive Efficiency]] · [[Velocity Triangles]] · [[Thrust Equation]]

## Sources
- 2023-24 exam Q4 (the propeller material is not in the Week 8–9 handouts; this is standard Froude momentum theory)

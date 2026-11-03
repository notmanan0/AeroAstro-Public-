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

Actuator disk theory models a propeller as an infinitely thin disk of area $A$ that adds a uniform pressure jump $\Delta p$ to a streamtube, with no swirl and no losses. It gives

$$
V_{disk} = \tfrac12(V_\infty+V_j),\qquad T = \dot m(V_j-V_\infty) = A\,\Delta p,\qquad\eta_P = \frac{2}{1+V_j/V_\infty} .
$$

The derivation was asked in 2023-24 Q4(iv):

1. Continuity through the disk gives $\dot m = \rho AV_{disk}$; the velocity is continuous across the disk and the pressure jumps.
2. A momentum balance on the whole streamtube, with $p_\infty$ on its boundary, gives $T = \dot m(V_j-V_\infty)$.
3. Bernoulli upstream gives $p_\infty+\tfrac12\rho V_\infty^2 = p_u+\tfrac12\rho V_{disk}^2$, and downstream $p_d+\tfrac12\rho V_{disk}^2 = p_\infty+\tfrac12\rho V_j^2$.
4. So $\Delta p = p_d-p_u = \tfrac12\rho(V_j^2-V_\infty^2)$.
5. Setting $T = A\Delta p$ gives $\rho AV_{disk}(V_j-V_\infty) = \tfrac12\rho A(V_j-V_\infty)(V_j+V_\infty)$, so $V_{disk} = \tfrac12(V_\infty+V_j)$.

Half the velocity increase therefore happens upstream of the disk. Along the stream (the sketch in 2023-24 Q4(iii)), the axial velocity rises smoothly from $V_\infty$ to $V_{disk}$ at the disk and on to $V_j$. The static pressure falls below $p_\infty$ ahead of the disk as the flow accelerates, jumps up by $\Delta p$ at the disk, then falls back to $p_\infty$ far downstream. The stagnation pressure is constant at $p_{0\infty}$ upstream, jumps by $\Delta p$ at the disk and stays constant after.

For blade-element work the advance ratio is $J = V_\infty/(nD)$, with $n$ in rev/s, and the tip speed $U_{tip} = \pi nD = \pi V_\infty/J$. In cruise the relative inlet velocity combines the axial $V_{disk}$ with the tangential $\Omega r$, at $\tan^{-1}(V_{disk}/\Omega r)$ from the plane of rotation or $\tan^{-1}(\Omega r/V_{disk})$ from the axial direction. The blade section is an aerofoil at a small incidence to that relative flow, and the small exit swirl is removed in open rotors by a stator row. In 2023-24 Q4(v), $V_\infty = 100$ m/s, $V_j-V_\infty = 20$ m/s and $J = 1.1$ give $V_{disk} = 110$ m/s and $U_{tip} = 285.6$ m/s, so the relative inlet flow is 68.9° from axial (21.1° from the plane of rotation).

## Related

- [[Propulsive Efficiency]] · [[Velocity Triangles]] · [[Thrust Equation]]

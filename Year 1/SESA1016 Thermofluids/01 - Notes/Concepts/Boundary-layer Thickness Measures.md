---
title: "Boundary-layer Thickness Measures"
module: "SESA1016 Thermofluids"
type: concept
stream: "Viscous Flow"
aliases: ["displacement thickness", "momentum thickness", "shape factor"]
tags: [sesa1016, concept, boundary-layer]
status: complete
parent_lectures: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
related_concepts: ["[[Skin-friction and Pressure Drag]]", "[[Reynolds Number]]", "[[Momentum Flux]]"]
sources: ["02 - Sources/Lectures/Chapter 14.pdf"]
---

# Boundary-layer Thickness Measures

The thickness of a boundary layer is measured in three ways: the 99 % thickness $\delta_{99}$ where $v_x$ reaches 99 % of $V_\infty$, the displacement thickness $\delta^*$ and the momentum thickness $\theta$.

$\delta_{99}$ is easy to picture but depends on an arbitrary threshold and is hard to measure, because the profile approaches $V_\infty$ very slowly. The two integral thicknesses avoid that by weighing the whole profile:

$$
\delta^*=\int_0^\infty\left(1-\frac{v_x}{V_\infty}\right)dy,\qquad
\theta=\int_0^\infty\frac{v_x}{V_\infty}\left(1-\frac{v_x}{V_\infty}\right)dy
$$

The displacement thickness is the distance by which the wall would have to be moved out, in an inviscid flow, to carry the same mass flow as the real slowed layer; equivalently, it is how far the outer streamlines are pushed away from the wall. The momentum thickness measures the momentum deficit: a control volume over one side of a flat plate shows that the drag per unit width is $D=\rho V_\infty^2\theta$, so $\theta$ grows exactly as fast as the plate accumulates drag.

Since the integrand of $\theta$ is the integrand of $\delta^*$ multiplied by $v_x/V_\infty\le1$, always $\theta<\delta^*<\delta_{99}$. The ratio $H=\delta^*/\theta$ is the **shape factor**: about 2.6 for a laminar flat-plate layer and about 1.3–1.4 for a fuller turbulent one. A rising $H$ warns that the profile is becoming less full near the wall, as it does approaching separation.

![[tf_bl_thickness_measures.png|760]]

## Related

- [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Displacement thickness|displacement thickness]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Momentum thickness and drag|momentum thickness and drag]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Worked example - displacement thickness from measurements|measured-profile example]]
- [[Skin-friction and Pressure Drag]] · [[Reynolds Number]] · [[Momentum Flux]]

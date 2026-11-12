---
title: "Control-volume Analysis Workflow"
module: "SESA1016 Thermofluids"
type: concept
stream: "Conservation Laws"
aliases: ["control volume workflow"]
tags: [sesa1016, concept, control-volume]
status: complete
parent_lectures: ["[[SESA1016 T11 - Conservation of Mass]]", "[[SESA1016 T12 - Conservation of Momentum]]", "[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
related_concepts: ["[[Mass Flow Rate]]", "[[Momentum Flux]]", "[[Steady-flow Energy Equation]]", "[[Closed System vs Control Volume]]"]
sources: ["02 - Sources/Lectures/Chapter 11.pdf", "02 - Sources/Lectures/Chapter 12.pdf", "02 - Sources/Lectures/Chapter 13.pdf"]
---

# Control-volume Analysis Workflow

The control-volume workflow is the common method for applying conservation of mass, momentum and energy to a region of space with flow across its boundary.

All three laws have the same structure: what is applied to the control volume (nothing for mass, forces for momentum, heat and work for energy) equals the rate of accumulation inside plus the net outflow across the surface. For steady flow the accumulation term drops out, leaving a balance between the net outflow and the forces or energy input.

The method is the same each time. Draw the control volume, cutting inlets and outlets normal to the flow where the conditions are known, and mark the outward normal $\vec n$ on every face. Write mass conservation first, $\sum\dot m_{out}=\sum\dot m_{in}$ in steady flow, because it usually fixes an unknown velocity. For momentum, list every force on the fluid in the control volume (pressure on the cut faces using gauge pressure where the outside is atmospheric, forces from walls, supports or vanes, weight if it matters) and equate their sum to $\dot{\vec M}_{out}-\dot{\vec M}_{in}$ component by component. For energy, use the [[Steady-flow Energy Equation]] with the signs $\dot Q$ into and $\dot W_x$ out of the fluid.

The common mistakes are mixing up the force on the fluid with the force on the device (equal and opposite), forgetting pressure forces on inlet and outlet faces, and losing the sign of a velocity component. Assuming every unknown force is positive in the axis direction and letting the algebra return its sign avoids most of them.

![[tf_control_volume_balances.png|760]]

## Related

- [[SESA1016 T11 - Conservation of Mass#4. Conservation of mass|mass]] · [[SESA1016 T12 - Conservation of Momentum#3. Conservation of momentum for a control volume|momentum]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#3. Conservation of energy for a control volume|energy]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#The three conservation laws together|all three together]]
- [[Mass Flow Rate]] · [[Momentum Flux]] · [[Steady-flow Energy Equation]] · [[Closed System vs Control Volume]]

---
title: "Momentum Flux"
module: "SESA1016 Thermofluids"
type: concept
stream: "Conservation Laws"
aliases: ["momentum flow rate"]
tags: [sesa1016, concept, momentum]
status: complete
parent_lectures: ["[[SESA1016 T12 - Conservation of Momentum]]"]
related_concepts: ["[[Mass Flow Rate]]", "[[Control-volume Analysis Workflow]]"]
sources: ["02 - Sources/Lectures/Chapter 12.pdf"]
---

# Momentum Flux

The momentum flow rate (momentum flux) through a surface is the momentum carried across it per unit time by the fluid, $\dot{\vec M}=\int_A\rho\vec V\,(\vec V\cdot\vec n)\,dA$, which is $\dot m\vec V$ for uniform flow.

Each kilogram crossing the surface carries momentum $\vec V$, and $\dot m$ kilograms cross per second, so the momentum flow rate is a vector in the direction of the velocity with magnitude $\dot mV$. The mass flow factor $\rho(\vec V\cdot\vec n)\,dA$ is a scalar that depends only on the normal component, while the momentum carried is the full vector; at an inclined outlet both components $\dot M_x=\dot mV_x$ and $\dot M_y=\dot mV_y$ are carried by the same mass flow.

In the momentum equation for a steady control volume the net force on the fluid equals the net momentum outflow:

$$
\sum\vec F=\dot{\vec M}_{out}-\dot{\vec M}_{in}=\dot m\left(\vec V_{out}-\vec V_{in}\right)
$$

A jet turned by a vane at constant speed still has a changing momentum flow, because its direction changes; the vane must push on the fluid to turn it and feels the equal and opposite reaction. Thrust works the same way: an engine that accelerates air from $V_\infty$ to $V_j$ feels a force $\dot m(V_j-V_\infty)$.

When the velocity varies across a section, the momentum flux is $\int\rho V^2dA$, larger than $\rho\bar V^2A$; for a linear profile the correction is a factor 4/3.

## Related

- [[SESA1016 T12 - Conservation of Momentum#2. Flow of momentum|T12 §2]] · [[SESA1016 T12 - Conservation of Momentum#One inlet, one outlet, uniform flow|one inlet, one outlet]] · [[SESA1016 T12 - Conservation of Momentum#Worked example - jet deflected by a vane|vane example]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Thrust from momentum conservation|thrust]]
- [[Mass Flow Rate]] · [[Control-volume Analysis Workflow]]

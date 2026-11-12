---
title: "Material Derivative"
module: "SESA1016 Thermofluids"
type: concept
stream: "Flow Kinematics"
aliases: ["substantial derivative", "particle derivative"]
tags: [sesa1016, concept, kinematics]
status: complete
parent_lectures: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
related_concepts: ["[[Streamline, Pathline and Streakline]]"]
sources: ["02 - Sources/Lectures/Chapter 9.pdf"]
---

# Material Derivative

The material derivative $D/Dt$ is the rate of change of a quantity following a fluid particle, made up of the local rate of change at a fixed point plus the convective change from moving through a non-uniform field.

In an Eulerian description properties are fields, such as $T(x,y,z,t)$, but the physical laws (Newton's second law, the first law) apply to particles. Following a particle for a time $dt$, it moves $u\,dt$, $v\,dt$, $w\,dt$, and the chain rule gives

$$
\frac{DT}{Dt}=\frac{\partial T}{\partial t}+u\frac{\partial T}{\partial x}+v\frac{\partial T}{\partial y}+w\frac{\partial T}{\partial z}
$$

The first term is non-zero only in unsteady flow. The others are non-zero whenever the particle moves through a gradient, even in steady flow: a thermometer fixed in a steady stream reads a constant temperature, while a particle swept from a cold region into a warm one heats up.

Applied to the velocity itself it gives the particle's acceleration. In steady flow through a nozzle the velocity at each point never changes, yet every particle accelerates as it moves into the narrower section; this convective acceleration $V\,\partial V/\partial s$ is what the pressure gradient must supply, and integrating it along a streamline gives the Bernoulli equation.

## Related

- [[SESA1016 T9 - Describing Flow and the Material Derivative#Following a particle - the material derivative|T9 material derivative]] · [[SESA1016 T10 - Euler and Bernoulli Equations#1. Acceleration of a fluid particle|particle acceleration]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Worked example - convective acceleration in a nozzle|nozzle example]]
- [[Streamline, Pathline and Streakline]] · [[Bernoulli Equation]]

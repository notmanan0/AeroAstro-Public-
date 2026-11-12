---
title: "Stagnation Pressure and Pitot Tube"
module: "SESA1016 Thermofluids"
type: concept
stream: "Inviscid Flow"
aliases: ["stagnation pressure", "total pressure", "Pitot tube"]
tags: [sesa1016, concept, pressure-measurement]
status: complete
parent_lectures: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
related_concepts: ["[[Bernoulli Equation]]", "[[Pressure Coefficient]]", "[[Pressure and Head]]"]
sources: ["02 - Sources/Lectures/Chapter 10.pdf"]
---

# Stagnation Pressure and Pitot Tube

The stagnation pressure $p_0$ is the pressure a flowing fluid reaches when it is brought to rest without losses, $p_0=p+\tfrac12\rho V^2$ in incompressible flow; a Pitot tube measures it by facing an open tube into the flow.

Along the streamline that ends on the nose of the tube the fluid slows to zero speed at the stagnation point. With Bernoulli between a point upstream (static pressure $p$, speed $V$) and the stagnation point,

$$
p_0=p+\tfrac12\rho V^2,
$$

so the stagnation pressure is the static pressure plus the dynamic pressure. Static pressure is read by taps flush with a surface parallel to the flow, where the fluid moves past without being slowed.

A Pitot-static tube combines both: a central hole facing the flow reads $p_0$, and holes in the side, a few diameters back, read $p$. Their difference is the dynamic pressure, which gives the speed:

$$
V=\sqrt{\frac{2(p_0-p)}{\rho}}
$$

This is how aircraft measure airspeed; with sea-level density in the formula the result is the equivalent airspeed rather than the true airspeed at altitude. The formula needs the density of the flowing fluid (air), not of the manometer liquid that reads $p_0-p$. Above a Mach number of about 0.3 compressibility makes $p_0-p$ larger than $\tfrac12\rho V^2$ and the compressible relation is needed.

![[tf_pitot_static.png|760]]

## Related

- [[SESA1016 T10 - Euler and Bernoulli Equations#The stagnation tube|stagnation tube]] · [[SESA1016 T10 - Euler and Bernoulli Equations#The Pitot-static tube|Pitot-static tube]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Worked example - Pitot-static flow meter|Pitot-static flow meter]]
- [[Bernoulli Equation]] · [[Pressure Coefficient]] · [[Pressure and Head]]

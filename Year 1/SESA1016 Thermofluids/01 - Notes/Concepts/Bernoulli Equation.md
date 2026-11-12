---
title: "Bernoulli Equation"
module: "SESA1016 Thermofluids"
type: concept
stream: "Inviscid Flow"
aliases: ["Bernoulli", "mechanical energy equation"]
tags: [sesa1016, concept, bernoulli]
status: complete
parent_lectures: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
related_concepts: ["[[Stagnation Pressure and Pitot Tube]]", "[[Pressure and Head]]", "[[Pressure Coefficient]]", "[[Steady-flow Energy Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 10.pdf"]
---

# Bernoulli Equation

The Bernoulli equation says that in steady, incompressible, inviscid flow the sum $p+\tfrac12\rho V^2+\rho gz$ is the same at every point of a streamline.

$$
p+\tfrac12\rho V^2+\rho gz=\text{const along a streamline}
$$

It is the Euler equation (Newton's second law for a particle with no shear stress) integrated along the particle's path. In the streamwise direction $\rho a_s=-\partial p/\partial s-\rho g\,\partial z/\partial s$; with steady flow $a_s=V\,\partial V/\partial s$, and with $\rho$ constant every term is an exact derivative along $s$, so their sum is constant. Each assumption is used once in that integration, which is why each one matters: viscosity would add a shear force, unsteadiness a $\partial V/\partial t$ term, and a varying density would stop $dp/\rho$ integrating to $p/\rho$.

Read term by term, it is a mechanical energy balance per unit volume: pressure work, kinetic energy and potential energy trade with one another and nothing is lost. Where a stream speeds up its pressure falls, which is how a contraction, a Venturi meter or an aerofoil's upper surface produce low pressure. Divided by $\rho g$ the terms become heads, $p/\rho g+V^2/2g+z$, which is the form used for pipes and tanks.

The equation stops holding wherever the flow loses mechanical energy or has it added: inside boundary layers and wakes, along a long pipe with friction, across a pump or turbine. There the [[Steady-flow Energy Equation]] or a head-loss term is needed. It also applies only along one streamline unless the flow upstream was uniform, in which case the constant is the same everywhere.

![[tf_bernoulli_contraction.png|760]]

## Related

- [[SESA1016 T10 - Euler and Bernoulli Equations#3. The Bernoulli equation|T10 §3]] (statement and derivation) · [[SESA1016 T10 - Euler and Bernoulli Equations#Heads|heads]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Worked example - draining tank and sluice|draining tank]]
- [[Stagnation Pressure and Pitot Tube]] · [[Pressure Coefficient]] · [[Pressure and Head]] · [[Steady-flow Energy Equation]]

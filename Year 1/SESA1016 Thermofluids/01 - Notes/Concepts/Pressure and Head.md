---
title: "Pressure and Head"
module: "SESA1016 Thermofluids"
type: concept
stream: "Fluid Fundamentals"
aliases: ["pressure head", "hydrostatic head"]
tags: [sesa1016, concept, pressure]
status: complete
parent_lectures: ["[[SESA1016 T8 - Hydrostatics]]", "[[SESA1016 T15 - Flow in Conduits]]"]
related_concepts: ["[[Bernoulli Equation]]", "[[Major and Minor Head Losses]]", "[[Stagnation Pressure and Pitot Tube]]"]
sources: ["02 - Sources/Lectures/Chapter 8.pdf"]
---

# Pressure and Head

Pressure is the normal force per unit area exerted by a fluid, the same in all directions at a point in a fluid at rest; a head is a pressure or energy per unit volume expressed as the height of a column of the working fluid, $p/\rho g$.

In a fluid at rest the vertical force balance on a thin slab gives Stevin's law, $dp/dz=-\rho g$. For a liquid of constant density this integrates to $p=p_0+\rho gh$ at depth $h$ below a free surface at pressure $p_0$, so pressure depends only on depth, not on the shape of the container. Absolute pressure is measured from vacuum and gauge pressure from the local atmosphere; the ideal-gas law needs absolute pressure, while force calculations on structures with atmosphere on the other side need only gauge.

Manometers and barometers measure pressure as a column height, which is where the idea of head comes from: 10.3 m of water or 760 mm of mercury is one atmosphere. In flowing fluids the Bernoulli equation divided by $\rho g$ gives three heads,

$$
\frac p{\rho g}+\frac{V^2}{2g}+z=H,
$$

pressure head, velocity (dynamic) head and elevation head, whose sum $H$ is the total head. It is constant along a streamline in ideal flow and falls by the head loss $h_L$ in a real pipe. Heads make pipe-system energy balances easy to picture as lines on a diagram.

## Related

- [[SESA1016 T8 - Hydrostatics#3. Stevin's law|Stevin]] · [[SESA1016 T8 - Hydrostatics#Integrating Stevin's law|liquids]] · [[SESA1016 T8 - Hydrostatics#7. The manometer|manometer]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Heads|heads in T10]]
- [[Bernoulli Equation]] · [[Major and Minor Head Losses]] · [[Stagnation Pressure and Pitot Tube]]

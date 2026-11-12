---
title: "Reynolds Number"
module: "SESA1016 Thermofluids"
type: concept
stream: "Similarity"
aliases: ["Re"]
tags: [sesa1016, concept, reynolds]
status: complete
parent_lectures: ["[[SESA1016 T6 - Dimensional Analysis and Similarity]]", "[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]", "[[SESA1016 T15 - Flow in Conduits]]"]
related_concepts: ["[[Newtonian Fluid and Viscosity]]", "[[Darcy Friction Factor]]", "[[Buckingham Pi Theorem]]", "[[Boundary-layer Thickness Measures]]"]
sources: ["02 - Sources/Lectures/Chapter 6.pdf", "02 - Sources/Lectures/Chapter 15.pdf"]
---

# Reynolds Number

The Reynolds number $Re=\rho VL/\mu=VL/\nu$ is the ratio of inertial to viscous effects in a flow, with $V$ and $L$ a characteristic speed and length.

It appears whenever viscosity is one of the variables in a dimensional analysis, as in sphere drag, $C_D=f(Re)$. Its physical meaning comes from comparing two time scales: momentum diffuses across a distance $L$ by viscosity in a time of order $L^2/\nu$, while the flow carries it past in $L/V$; their ratio is $VL/\nu$. At low $Re$ viscous diffusion wins and the flow is smooth and orderly; at high $Re$ disturbances are carried along faster than viscosity can damp them, and the flow becomes turbulent.

The critical values depend on the geometry and on the length chosen, so a quoted number is meaningful only with its definition. The usual values are $Re_D=\bar VD/\nu<2000$ for laminar pipe flow and above about 3000–4000 for turbulent, with transition between; $Re_x=V_\infty x/\nu\approx5\times10^5$ for transition on a flat plate, with $x$ measured from the leading edge.

Matching $Re$ between a model and full scale is the condition for dynamic similarity in incompressible flow. That is often impossible at the same fluid and speed, which is why wind tunnels are pressurised or use cryogenic nitrogen, and why some tests are done in water, whose $\nu$ is about 17 times smaller than air's.

## Related

- [[SESA1016 T6 - Dimensional Analysis and Similarity#Common dimensionless groups|T6 groups]] · [[SESA1016 T9 - Describing Flow and the Material Derivative#Laminar and turbulent|laminar and turbulent]] · [[SESA1016 T15 - Flow in Conduits#2. Reynolds' experiment|Reynolds experiment]] · [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Transition|flat-plate transition]]
- [[Newtonian Fluid and Viscosity]] · [[Darcy Friction Factor]] · [[Buckingham Pi Theorem]] · [[Boundary-layer Thickness Measures]]

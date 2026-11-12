---
title: "Mass Flow Rate"
module: "SESA1016 Thermofluids"
type: concept
stream: "Conservation Laws"
aliases: ["mass flux", "mdot"]
tags: [sesa1016, concept, continuity]
status: complete
parent_lectures: ["[[SESA1016 T11 - Conservation of Mass]]"]
related_concepts: ["[[Control-volume Analysis Workflow]]", "[[Momentum Flux]]", "[[Closed System vs Control Volume]]"]
sources: ["02 - Sources/Lectures/Chapter 11.pdf"]
---

# Mass Flow Rate

Mass flow rate $\dot m$ is the mass crossing a surface per unit time, $\dot m=\int_A\rho\,(\vec V\cdot\vec n)\,dA$, which reduces to $\dot m=\rho VA$ for uniform flow normal to the surface.

Only the velocity component normal to the surface carries fluid across it, which is why the dot product appears; flow parallel to a surface carries nothing through it. With the outward normal of a control volume, $\vec V\cdot\vec n$ is positive at an outlet and negative at an inlet, so the same integral over the whole control surface gives the net outflow.

When the velocity varies across the section, the area-averaged velocity $\bar V=\dot{\mathcal V}/A$ is defined so that $\dot{\mathcal V}=\bar VA$ still holds, and for constant density $\dot m=\rho\bar VA$. For a linear profile rising from zero, $\bar V$ is half the maximum; for laminar pipe flow it is also half the centreline value. When density varies across the section too, as in a hot gas survey, $\rho V$ must be integrated together.

Mass is conserved; volume need not be. In steady flow $\dot m$ is the same at every section of a duct, $\rho_1V_1A_1=\rho_2V_2A_2$, but if the gas is heated or compressed the volume flow rate changes. For a liquid, or a gas at low Mach number, $\rho$ is constant and $V_1A_1=V_2A_2$, so a contraction speeds the flow up in proportion to the area ratio.

![[tf_flow_rate_profiles.png|760]]

## Related

- [[SESA1016 T11 - Conservation of Mass#2. Mass flow rate|T11 §2]] · [[SESA1016 T11 - Conservation of Mass#The area-averaged velocity|area-averaged velocity]] · [[SESA1016 T11 - Conservation of Mass#Mass is conserved, volume is not|mass versus volume]] · [[SESA1016 T11 - Conservation of Mass#Worked example - numerical mass flow in an intercooler|intercooler survey]]
- [[Control-volume Analysis Workflow]] · [[Momentum Flux]] · [[Closed System vs Control Volume]]

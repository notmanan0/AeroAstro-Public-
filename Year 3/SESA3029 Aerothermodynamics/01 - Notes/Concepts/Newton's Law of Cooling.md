---
title: "Newton's Law of Cooling"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["heat transfer coefficient", "convective heat transfer coefficient", "convection coefficient", "film coefficient", "Newton's law of cooling", "rate of convective heat transfer"]
tags: [sesa3029, concept, heat-transfer, convection]
status: complete
parent_lectures: ["[[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy]]", "[[SESA3029 W09c - Critical Thickness of Insulation and Fins]]"]
related_concepts: ["[[Nusselt Number]]", "[[Thermal Boundary Layer]]", "[[Reynolds Analogy]]"]
sources: ["02 - Sources/Lectures/Lecture5.3.pdf", "02 - Sources/Lectures/Lecture5.4(1).pdf"]
---

# Newton's Law of Cooling

Newton's law of cooling gives the rate of convective heat transfer between a surface and a fluid as $\dot Q=hA_s(T_s-T_\infty)$, where $h$ is the heat transfer coefficient (W m⁻² K⁻¹), $A_s$ the wetted surface area, $T_s$ the surface temperature and $T_\infty$ the fluid temperature far from the surface.

The law defines $h$ rather than predicting it: all the dependence on the flow (velocity, fluid properties, geometry, laminar or turbulent boundary layer) sits inside $h$. At the wall the fluid is at rest, so the same heat flux is conducted into the fluid, and equating the two forms gives

$$
h=\frac{-k\,(\partial T/\partial y)_{y=0}}{T_s-T_\infty},
$$

with $k$ the fluid conductivity. A thin [[Thermal Boundary Layer|thermal boundary layer]] means a steep wall gradient and a large $h$. In practice $h$ comes from a correlation for the [[Nusselt Number]], $h=\mathrm{Nu}\,k/L$.

Where $h$ varies along a surface, $\dot Q$ uses the average $\bar h=\frac1L\int_0^Lh\,\mathrm dx$; on a laminar flat plate $\bar h=2h(L)$. In a thermal-resistance network the convection is the resistance $1/(hA_s)$, which falls as the area grows; that is the basis of both the critical radius of insulation and fins. With $T_s$ and $T_\infty$ fixed, the heat rate can be raised only by raising $h$ (more flow) or $A_s$ (extended surfaces).

Typical values: 2–25 W m⁻² K⁻¹ for free convection in gases, 25–250 for forced convection in gases, 50–20 000 for forced convection in liquids.

## Related

- Parent lectures: [[SESA3029 W09b - Convective Heat Transfer and the Reynolds Analogy#2. The thermal boundary layer|W09b §2]] · [[SESA3029 W09c - Critical Thickness of Insulation and Fins]]
- Related concepts: [[Nusselt Number]] · [[Thermal Boundary Layer]] · [[Critical Radius of Insulation]] · [[Fin Equation]]

## Sources

- L5.3 slides 7, 11, 13–15; L5.4 slide 6.

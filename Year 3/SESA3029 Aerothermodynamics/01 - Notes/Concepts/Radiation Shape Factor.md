---
title: "Radiation Shape Factor"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["view factor", "configuration factor", "angle factor", "reciprocity relation", "summation rule"]
tags: [sesa3029, concept, heat-transfer, radiation]
status: complete
parent_lectures: ["[[SESA3029 W09d - Thermal Radiation]]"]
related_concepts: ["[[Solid Angle]]", "[[Stefan-Boltzmann Law]]"]
sources: ["02 - Sources/Lectures/Lecture5.6(1).pdf"]
---

# Radiation Shape Factor

The shape factor $F_{i-j}$ (or $F_{ij}$) is the fraction of the radiation leaving surface $i$ that reaches surface $j$. It depends only on the sizes, spacing and orientation of the surfaces.

For diffuse surfaces it follows from the [[Solid Angle|solid angle]] each element of $j$ subtends at each element of $i$:

$$
F_{12}=\frac{1}{A_1}\int_{A_1}\!\int_{A_2}\frac{\cos\theta_1\cos\theta_2}{\pi R^2}\,\mathrm dA_2\,\mathrm dA_1 ,
$$

where $R$ is the distance between the elements and $\theta_1$, $\theta_2$ are the angles between the line joining them and each normal. The $\pi$ comes from the intensity of a diffuse emitter, $I=E_b/\pi$.

Two rules give most shape factors without integration. The **reciprocity relation** $A_iF_{ij}=A_jF_{ji}$ follows from zero net exchange between two black surfaces at equal temperatures, and also from the symmetry of the integral. The **summation rule** $\sum_{j=1}^NF_{ij}=1$ holds for each surface of an enclosure, since everything leaving $i$ lands somewhere, itself included; openings are treated as imaginary black surfaces at the temperature beyond them. A flat or convex surface has $F_{ii}=0$.

Examples: infinite parallel plates, $F_{12}=F_{21}=1$; a sphere inside a concentric sphere, $F_{12}=1$, $F_{21}=(r_1/r_2)^2$, $F_{22}=1-(r_1/r_2)^2$; the Earth seen from the Sun, $F_{S\to E}=R_E^2/(4d^2)$. The net exchange between black surfaces is $\dot Q_{1-2}=A_1F_{12}\sigma(T_1^4-T_2^4)$.

## Related

- Parent lecture: [[SESA3029 W09d - Thermal Radiation#9. The shape factor|W09d §§9–12]]
- Related concepts: [[Solid Angle]] · [[Stefan-Boltzmann Law]] · [[Emissivity]]

## Sources

- L5.6 slides 3–9, 11–12.

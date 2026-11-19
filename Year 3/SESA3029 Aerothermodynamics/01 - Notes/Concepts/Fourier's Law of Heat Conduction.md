---
title: "Fourier's Law of Heat Conduction"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["Fourier's law", "Fourier law", "conduction rate equation", "law of heat conduction"]
tags: [sesa3029, concept, heat-transfer, conduction, fourier-law]
status: complete
parent_lectures: ["[[SESA3029 W09a - Heat Conduction and Thermal Resistance]]"]
related_concepts: ["[[Thermal Conductivity]]", "[[Thermal Resistance]]", "[[Heat Equation]]", "[[Radial Conduction in Cylinders and Spheres]]"]
sources: ["02 - Sources/Lectures/Lecture5.1.pdf", "02 - Sources/Lectures/Lecture 5-1 (2025-26 version).txt", "02 - Sources/Lectures/Lecture5.2.pdf"]
---

# Fourier's Law of Heat Conduction

Fourier's law states that the rate of heat conduction through a surface is proportional to the area and to the temperature gradient normal to it, and flows down the gradient: in one dimension $\dot Q=-kA\,\mathrm dT/\mathrm dx$, with $k$ the [[Thermal Conductivity|thermal conductivity]].

It follows from three observations on a rod between two blocks: no heat flows when the blocks are at the same temperature, a longer rod passes less heat and a thicker one more. Hence $\dot Q=kA(T_1-T_2)/L$ for the whole rod, and applying this to a vanishingly short piece of rod gives the derivative form. The minus sign makes $\dot Q$ positive in the direction of decreasing temperature; a negative $\dot Q$ means the heat flows towards $-x$.

In three dimensions, for an isotropic material,

$$
\dot{\mathbf q}=-k\nabla T,\qquad \dot q_i=-k\frac{\partial T}{\partial x_i},
$$

so the heat flux is a vector pointing down the steepest temperature descent. In an anisotropic material such as a laminate, $k$ becomes a tensor. With an energy balance on a small volume, Fourier's law gives the [[Heat Equation]]; in steady 1-D conduction without heat generation it gives a linear profile in a plane wall, a logarithmic one in a cylinder and a $1/r$ one in a sphere ([[Radial Conduction in Cylinders and Spheres]]). Integrated across a layer, it becomes a [[Thermal Resistance|thermal resistance]].

![[at_w09a_fourier_sign.png|760]]

## Related

- Parent lectures: [[SESA3029 W09a - Heat Conduction and Thermal Resistance#2. Fourier's law of heat conduction|W09a §2]]
- Related concepts: [[Thermal Conductivity]] · [[Thermal Resistance]] · [[Heat Equation]] (MATH2048) · [[Radial Conduction in Cylinders and Spheres]]

## Sources

- Sources: L5.1 slides 10–11 and L5-1 (2025–26 recording), ll. 149–202; L5.2 slides 1, 3, 7 (written ahead).

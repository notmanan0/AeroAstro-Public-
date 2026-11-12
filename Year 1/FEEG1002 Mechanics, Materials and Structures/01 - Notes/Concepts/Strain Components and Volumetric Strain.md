---
title: "Strain Components and Volumetric Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["normal strain", "engineering shear strain", "tensor shear strain", "gamma_xy", "epsilon_xy", "volumetric strain", "dilatation", "microstrain"]
tags: [feeg1002, concept, statics-2, strain]
status: complete
parent_lectures: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Thermal Strain]]", "[[Generalised Hooke's Law]]", "[[Strain Gauge Rosettes]]", "[[Stress Transformation Equations]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 02 - Strain in Multiple Dimensions.pdf"]
---

# Strain Components and Volumetric Strain

Strain measures deformation: the normal strains $\varepsilon_{xx}=du_x/dx$, $\varepsilon_{yy}$, $\varepsilon_{zz}$ are the relative stretches along the axes, and the shear strains measure the loss of right angles, as the engineering shear strain $\gamma_{xy}=du_x/dy+du_y/dx$ or the tensor shear strain $\varepsilon_{xy}=\gamma_{xy}/2$.

Strain is built from displacement gradients, the differences in displacement between neighbouring points, so a rigid translation gives no strain. For shear, a rigid rotation turns the two edges of an element by equal and opposite gradients, which cancel in $\gamma_{xy}$. A positive shear strain closes the angle between the left and bottom faces of an element; a negative one opens it. The tensor shear strain is the angle by which each face turns inwards once the element's average rotation $\omega=\tfrac12(du_y/dx-du_x/dy)$ has been removed. The factor of two between the two shear measures is a common source of error: $\tau=G\gamma$ uses $\gamma_{xy}$, while the transformation equations, Mohr's circle for strain and the rosette formulas use $\varepsilon_{xy}$.

The volumetric strain is the relative change of volume. Expanding $(1+\varepsilon_{xx})(1+\varepsilon_{yy})(1+\varepsilon_{zz})-1$ and dropping products of small strains gives

$$
\varepsilon_{vol}=\frac{\Delta V}{V_0}\approx\varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}
$$

Shear strains do not appear, since shear changes shape but not volume, like a pack of cards pushed sideways. Combined with [[Generalised Hooke's Law]] this gives $\varepsilon_{vol}=\frac{1-2\nu}{E}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})$ and the bulk modulus $K=E/3(1-2\nu)$.

Strains in metals are small, so they are quoted in percent or microstrain, $1\ \mu\varepsilon=10^{-6}$: an aluminium alloy yields at about 0.0036, or 3600 με. In 3D there are six strain components, three normal and three shear, and like stresses they change with the orientation of the axes according to the same transformation equations.

![[s2_strain_definitions.png|800]]

## Related

- [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#1. Normal strains|normal and volumetric strain in B2]] · [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#2. Shear strain|shear strain in B2]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Why strain transforms like stress|strain transformation in B5]]
- [[Thermal Strain]] · [[Generalised Hooke's Law]] · [[Strain Gauge Rosettes]] · [[Stress Transformation Equations]]
- Year 2: [[Polar Strain-Displacement Relations]] and [[Strain Compatibility]] in [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]

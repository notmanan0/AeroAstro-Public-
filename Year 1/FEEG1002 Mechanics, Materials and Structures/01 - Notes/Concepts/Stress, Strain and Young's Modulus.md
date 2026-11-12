---
title: "Stress, Strain and Young's Modulus"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["engineering stress", "engineering strain", "Hooke's law 1D", "Poisson's ratio", "shear modulus", "axial stiffness"]
tags: [feeg1002, concept, statics, stress, strain, hookes-law]
status: complete
parent_lectures: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Stress Concentration Factor and Factor of Safety]]", "[[Generalised Hooke's Law]]"]
sources: ["Statics 1 Lectures 1-2"]
---

# Stress, Strain and Young's Modulus

**Stress** is force per unit area, $\sigma=F/A$ for a force normal to the area and $\tau=F/A$ for a force along it; **strain** is deformation per unit length, $\varepsilon=\Delta L/L$ for a change in length and the shear strain $\gamma$ for a change in angle. For a linear elastic material in uniaxial stress they are proportional, $\sigma=E\varepsilon$, with Young's modulus $E$ as the constant.

Normalising by area and length is what makes the quantities useful. A material fails at a certain stress whatever the size of the part, so a design check becomes a comparison of the working stress with an allowable stress, the failure stress divided by a safety factor. Likewise $E$ is a material property, independent of the bar it is measured on.

Putting the definitions together gives the bar as a spring:

$$
F=\frac{EA}{L}\Delta L
$$

with axial stiffness $k=EA/L$, combining a material property with the geometry. This is the step used for bolt preload, for the extension of truss bars and for bars sharing a load in parallel or series.

A bar stretched along its length also gets thinner. The lateral strain is $-\nu\varepsilon$, where $\nu$ is Poisson's ratio, about 0.3 for metals. In shear, $\tau=G\gamma$, and for an isotropic material the three constants are linked by $G=E/2(1+\nu)$. Tension is positive throughout. The one-dimensional law ignores the lateral coupling that matters when stress acts in more than one direction; for that, use [[Generalised Hooke's Law]]. Stress is also local: around a hole or notch it rises above the nominal $F/A$ by a stress concentration factor.

![[s1_stress_strain_definitions.png|860]]

## Related

- Topic notes: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#4. Stress|A1, stress]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#5. Strain and Hooke's law|A1, strain and Hooke's law]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#A bar is a spring|A1, a bar is a spring]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain#Poisson's ratio|A1, Poisson's ratio]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Stress Concentration Factor and Factor of Safety]] · [[Generalised Hooke's Law]] · [[Engineering Stress-Strain Properties]]
- Year 2: [[Strain Energy]] in [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · the bar element in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]
- Materials: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]

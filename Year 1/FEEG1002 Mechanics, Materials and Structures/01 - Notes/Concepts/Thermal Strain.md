---
title: "Thermal Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["thermal expansion", "coefficient of thermal expansion", "thermal stress", "alpha Delta T"]
tags: [feeg1002, concept, statics-2, thermal-strain, thermal-stress]
status: complete
parent_lectures: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]"]
related_concepts: ["[[Strain Components and Volumetric Strain]]", "[[Generalised Hooke's Law]]", "[[Stress, Strain and Young's Modulus]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 03 - Thermal Strains.pdf"]
---

# Thermal Strain

Thermal strain is the strain a material takes up when its temperature changes, $\varepsilon_T=\alpha(T-T_{ref})=\alpha\Delta T$, where $\alpha$ is the coefficient of thermal expansion in K⁻¹; for an isotropic material it is the same in every direction and has no shear part.

A uniformly heated body that is free to move becomes a scaled-up copy of itself, so thermal expansion on its own causes no stress. Stress appears when the expansion is resisted: by supports, by neighbouring parts that expand less, or by a temperature gradient that makes hot regions push against cold ones. The total strain is then the sum of a thermal part and a mechanical part, and only the mechanical part is related to stress by Hooke's law.

Constrained bar problems are solved by superposition. Each constraint is released and each part allowed to expand freely by $\delta_T=\alpha\Delta TL$; unknown forces, taken as tensile, are then applied, giving $\delta_F=FL/EA$; compatibility is imposed on the total deformations and equilibrium on the forces. Parts in series between walls carry the same force and their deformations sum to zero (or to a gap); parts bonded in parallel extend equally and their forces sum to zero. A bar fully held between walls carries $\sigma=-E\alpha\Delta T$, independent of its length and area. A plate held in both in-plane directions carries $\sigma=-E\alpha\Delta T/(1-\nu)$, larger because the compression in each direction also expands the material sideways (Poisson), which the restraint in the other direction must cancel as well.

In bonded assemblies the part with the larger $\alpha$ ends up in compression on heating and the other in tension. Typical values are about $11.7\times10^{-6}$ K⁻¹ for steel, $20.9\times10^{-6}$ for brass, $23.6\times10^{-6}$ for aluminium and $2.6\times10^{-6}$ for a silicon chip. Thermal compression rarely yields a steel rail but can buckle it, and thermal cycling fatigues solder joints in electronics.

![[s2_thermal_rail.png|800]]

## Related

- [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#3. Thermal strain|thermal strain and superposition in B2]] · [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Worked example - steel rail with a 3 mm gap|rail example]] · [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - chip held by solder joints|biaxial restraint in B3]]
- [[Strain Components and Volumetric Strain]] · [[Generalised Hooke's Law]] · [[Stress, Strain and Young's Modulus]]
- Year 2: [[Shrink Fit]] in [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] · [[Thermal Barrier Coatings]] in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]

---
title: "Newtonian Fluid and Viscosity"
module: "SESA1016 Thermofluids"
type: concept
stream: "Fluid Fundamentals"
aliases: ["Newtonian fluid", "dynamic viscosity", "kinematic viscosity"]
tags: [sesa1016, concept, viscosity]
status: complete
parent_lectures: ["[[SESA1016 T7 - Fluid Properties and Viscosity]]"]
related_concepts: ["[[Reynolds Number]]", "[[Skin-friction and Pressure Drag]]", "[[Darcy Friction Factor]]"]
sources: ["02 - Sources/Lectures/Chapter 7.pdf"]
---

# Newtonian Fluid and Viscosity

A Newtonian fluid is one whose shear stress is proportional to its rate of shear strain, $\tau=\mu\,dv/dy$; the constant of proportionality $\mu$ is the dynamic viscosity, and $\nu=\mu/\rho$ is the kinematic viscosity.

The defining experiment is Couette flow: fluid between a fixed plate and one dragged at speed $V$ a gap $h$ above it. The fluid sticks to both plates (no slip), the velocity varies linearly across the gap, and the force needed is $F=\mu AV/h$. A solid in the same arrangement would deform a fixed amount and stop; a fluid keeps deforming as long as the shear stress acts, which is the definition of a fluid.

Air, water and oils are Newtonian. Fluids whose apparent viscosity falls with shear rate are shear-thinning (ketchup, paint) and those whose viscosity rises are shear-thickening (corn starch in water); these are non-Newtonian and lie outside the course's equations.

Viscosity behaves differently in liquids and gases. In a liquid, intermolecular attraction resists shearing and weakens as the liquid warms, so $\mu$ falls with temperature. In a gas, viscosity comes from molecules carrying momentum between layers, which they do faster when hot, so $\mu$ rises with temperature; Sutherland's law models this for air. Water has about 55 times the dynamic viscosity of air, but air has about 17 times the kinematic viscosity of water, because it is so much less dense, and it is $\nu$ that sets how fast momentum diffuses.

![[tf_rheology_curves.png|640]]

## Related

- [[SESA1016 T7 - Fluid Properties and Viscosity#4. Viscosity|T7 §4]] · [[SESA1016 T7 - Fluid Properties and Viscosity#Kinematic viscosity|kinematic viscosity]] · [[SESA1016 T7 - Fluid Properties and Viscosity#Effect of temperature|temperature dependence]] · [[SESA1016 T7 - Fluid Properties and Viscosity#Worked example - plate sliding on a fluid film|sliding plate]]
- [[Reynolds Number]] · [[Skin-friction and Pressure Drag]] · [[Darcy Friction Factor]]

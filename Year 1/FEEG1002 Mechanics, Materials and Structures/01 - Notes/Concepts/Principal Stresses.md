---
title: "Principal Stresses"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["principal directions", "maximum in-plane shear stress", "sigma_I sigma_II", "principal planes", "principal strains"]
tags: [feeg1002, concept, statics-2, principal-stresses, failure]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]", "[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Mohr's Circle]]", "[[Stress Transformation Equations]]", "[[Tresca Yield Criterion]]", "[[Von Mises Yield Criterion]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 06 - Mohr's Circle.pdf", "02 - Sources/Statics 2/Lectures/Lecture 08 - Yield Criteria.pdf"]
---

# Principal Stresses

The principal stresses are the normal stresses on the planes through a point that carry no shear stress; in plane stress they are $\sigma_{I,II}=\sigma_{average}\pm R$, with $\sigma_I$ the larger, on two perpendicular principal directions.

Every plane stress state has such directions, because Mohr's circle always crosses the normal-stress axis twice. The angle $\theta_p$ from the $x$ axis to the direction of $\sigma_I$ satisfies $\cos2\theta_p=(\sigma_{xx}-\sigma_{yy})/2R$ and $\sin2\theta_p=\sigma_{xy}/R$; the familiar $\tan2\theta_p=2\sigma_{xy}/(\sigma_{xx}-\sigma_{yy})$ has two solutions 90° apart, so a sketch of the circle is the safest way to tell which belongs to $\sigma_I$. The derivative of the transformation equation, $d\sigma_{x'x'}/d\theta=2\sigma_{x'y'}$, shows that the principal stresses are the largest and smallest normal stresses on any plane through the point, which is why brittle materials are checked against $\sigma_I$. Mathematically they are the eigenvalues of the stress tensor and the principal directions its eigenvectors.

The maximum in-plane shear stress is the radius, $(\sigma_I-\sigma_{II})/2$, acting at 45° to the principal directions on planes that also carry the normal stress $\sigma_{average}$. In 3D there are three principal stresses on mutually perpendicular planes. In plane stress the third, normal to the plate, is $\sigma_{III}=0$, and when $\sigma_I$ and $\sigma_{II}$ have the same sign the largest shear acts on a plane through the thickness, $\sigma_I/2$, rather than in the plane. Both yield criteria in the course are written in principal stresses, which makes them independent of how the stress element was oriented.

For an isotropic material the principal strains lie in the same directions as the principal stresses, because Hooke's law makes zero shear stress and zero shear strain coincide. A shaft in torsion is in pure shear with $\sigma_{I,II}=\pm\sigma_{xy}$ at 45°, which is why gauges for measuring torque are mounted at ±45°; a pressure vessel wall is already aligned with its principal directions.

![[s2_mohr_pure_shear.png|800]]

## Related

- [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#5. Principal stresses and maximum shear|principal stresses in B4]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Principal strains|principal strains in B5]] · [[FEEG1002 B6 - Yield Criteria#Maximum shear stress in three dimensions|three principal stresses in B6]]
- [[Mohr's Circle]] · [[Stress Transformation Equations]] · [[Tresca Yield Criterion]] · [[Von Mises Yield Criterion]]
- Year 2: [[Characteristic Equation and Eigenvalues]] · [[Stress Intensity Factor]] (crack opening by the normal stress)

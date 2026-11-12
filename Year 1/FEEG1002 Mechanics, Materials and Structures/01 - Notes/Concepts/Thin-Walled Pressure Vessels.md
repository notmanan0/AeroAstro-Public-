---
title: "Thin-Walled Pressure Vessels"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["hoop stress", "longitudinal stress", "pR/t", "pR/2t", "thin cylinder", "thin sphere"]
tags: [feeg1002, concept, statics-2, pressure-vessels]
status: complete
parent_lectures: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]", "[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Stress Tensor and Stress Element]]", "[[Generalised Hooke's Law]]", "[[Von Mises Yield Criterion]]", "[[Lame Thick-Cylinder Solution]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf"]
---

# Thin-Walled Pressure Vessels

A thin-walled pressure vessel is a closed shell whose wall thickness $t$ is less than about a tenth of its radius $R$; under a pressure difference $p$ a cylinder carries a hoop stress $\sigma_{yy}=pR/t$ and a longitudinal stress $\sigma_{xx}=pR/2t$, and a sphere carries $pR/2t$ in every direction.

Both cylinder results come from cutting the vessel together with its contents. A cut along a diameter balances the pressure on the projected rectangle $2RL$ against the hoop stress on two wall sections of area $tL$; a cut across the axis balances the pressure on the disc $\pi R^2$ against the longitudinal stress on the wall annulus, approximated by $2\pi Rt$. Only the projected area matters, which is why the shape of the end caps does not affect the longitudinal stress, and integrating the pressure over the curved wall gives the same force. A sphere looks the same through every diametral cut, so its wall is in equal biaxial tension with no shear on any plane.

The radial stress varies from $p$ to zero through the wall and is at most $t/R$ of the hoop stress, so it is neglected and the wall is treated as being in plane stress. That lets the plane-stress form of [[Generalised Hooke's Law]] give the strains, for example $\varepsilon_{hoop}=\frac{pR}{tE}\left(1-\frac\nu2\right)$ in a cylinder, and lets the [[Von Mises Yield Criterion]] give $\sigma_{eq}=\frac{\sqrt3}{2}\frac{pR}{t}$ for the cylinder wall. Because both in-plane principal stresses are tensile, the Tresca criterion is governed by shear through the thickness and gives $\sigma_{eq}=pR/t$.

The hoop stress is twice the longitudinal stress, so overpressurised cylinders split along their length, and a sphere needs half the wall thickness of a cylinder of the same radius. Under external pressure $p$ is negative, the stresses are compressive and buckling can govern. For $t/R$ above about 0.1 the stresses vary through the wall and the Lamé thick-cylinder solution is needed.

![[s2_pressure_vessel_stresses.png|800]]

## Related

- [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#4. Thin-walled pressure vessels|derivation in B1]] · [[FEEG1002 B3 - Generalised Hooke's Law#Worked example - submersible hull at 100 m|vessel strains in B3]] · [[FEEG1002 B6 - Yield Criteria#Worked example - liquid hydrogen tank|vessel yield in B6]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - helical weld in a pressure vessel|helical weld in B4]]
- [[Stress Tensor and Stress Element]] · [[Generalised Hooke's Law]] · [[Von Mises Yield Criterion]] · [[Tresca Yield Criterion]]
- Year 2: [[Lame Thick-Cylinder Solution]] in [[SESA2028 S10 - Thick Cylinders and Shrink Fits]], whose hoop stress tends to $pR/t$ as $t\to0$

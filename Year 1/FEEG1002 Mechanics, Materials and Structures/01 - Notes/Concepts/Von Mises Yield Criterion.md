---
title: "Von Mises Yield Criterion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["von Mises criterion", "von Mises stress", "equivalent stress", "distortion energy criterion", "sigma_eq"]
tags: [feeg1002, concept, statics-2, yield, von-mises]
status: complete
parent_lectures: ["[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Tresca Yield Criterion]]", "[[Principal Stresses]]", "[[Strain Gauge Rosettes]]", "[[Thin-Walled Pressure Vessels]]", "[[Von Mises and Tresca Yield Criteria]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 08 - Yield Criteria.pdf"]
---

# Von Mises Yield Criterion

The von Mises criterion states that a ductile material yields when the equivalent stress $\sigma_{eq}=\sqrt{\tfrac12[(\sigma_I-\sigma_{II})^2+(\sigma_I-\sigma_{III})^2+(\sigma_{II}-\sigma_{III})^2]}$ reaches the uniaxial yield stress $\sigma_Y$; in plane stress $\sigma_{eq}=\sqrt{\sigma_{xx}^2+\sigma_{yy}^2-\sigma_{xx}\sigma_{yy}+3\sigma_{xy}^2}$.

It is built as the root mean square of the maximum shear stresses on the three principal planes, the radii of the three Mohr's circles, rather than the single largest one used by Tresca; it can also be associated with the strain energy of distortion. Calibrating with a tensile test, where the root mean square is $\sigma_Y/\sqrt6$ at yield, gives the equivalent stress above, which reduces to $\sigma_I$ in uniaxial tension. With $\sigma_{III}=0$ it becomes $\sqrt{\sigma_I^2+\sigma_{II}^2-\sigma_I\sigma_{II}}$, and substituting $\sigma_{I,II}=\sigma_{average}\pm R$ gives the form in $xy$ components, which needs no principal stresses and is the one used most.

In the $\sigma_I$–$\sigma_{II}$ plane the criterion is an ellipse through the corners of the Tresca hexagon. It predicts a shear yield stress of $\sigma_Y/\sqrt3=0.577\sigma_Y$, which torsion tests on aluminium alloys and stainless steel match closely, and it allows $\sigma_I$ up to $1.155\sigma_Y$ when $\sigma_{II}=\sigma_I/2$. In three dimensions the yield surface is a cylinder about the line $\sigma_I=\sigma_{II}=\sigma_{III}$, so a hydrostatic stress never causes yield; only differences between principal stresses do.

Because $\sigma_{eq}$ is one scalar that is independent of the orientation of the stress element, it is what finite element software plots as the "von Mises stress", and it gives the safety factor directly, $SF=\sigma_Y/\sigma_{eq}$, and in a linear analysis the load at first yield, $F_{max}=SF\cdot F$. It applies to ductile materials with equal yield stresses in tension and compression, not to brittle materials such as cast iron or concrete.

![[s2_yield_loci.png|700]]

## Related

- [[FEEG1002 B6 - Yield Criteria#2. The von Mises criterion|von Mises in B6]] · [[FEEG1002 B6 - Yield Criteria#4. Failure load and safety factor|safety factor]] · [[FEEG1002 B6 - Yield Criteria#Worked example - shaft under axial load and torque|Tutorial 7 example]]
- [[Tresca Yield Criterion]] · [[Principal Stresses]] · [[Strain Gauge Rosettes]] · [[Thin-Walled Pressure Vessels]]
- Year 2: [[Von Mises and Tresca Yield Criteria]] and von Mises contours in [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]

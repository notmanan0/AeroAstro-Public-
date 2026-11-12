---
title: "Mohr's Circle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["Mohr's circle for stress", "Mohr's circle for strain", "Mohr circle"]
tags: [feeg1002, concept, statics-2, mohrs-circle, principal-stresses]
status: complete
parent_lectures: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]", "[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Principal Stresses]]", "[[Strain Gauge Rosettes]]", "[[Tresca Yield Criterion]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 06 - Mohr's Circle.pdf"]
---

# Mohr's Circle

Mohr's circle is the curve traced in the plane of normal stress against shear stress by the stresses on an element as it is rotated; it is centred at $\sigma_{average}=(\sigma_{xx}+\sigma_{yy})/2$ with radius $R=\sqrt{((\sigma_{xx}-\sigma_{yy})/2)^2+\sigma_{xy}^2}$.

It follows from the double-angle transformation equations: moving $\sigma_{average}$ to the left, squaring both equations and adding removes the angle, leaving $(\sigma_{x'x'}-\sigma_{average})^2+\sigma_{x'y'}^2=R^2$. Every orientation of the element is a point on the circle. In FEEG1002 the normal stress is plotted to the right and the **shear stress positive downwards**; with that choice an anticlockwise rotation $\theta$ of the element moves the point anticlockwise by $2\theta$ on the page. Books that plot shear upwards rotate the other way, so check the convention before borrowing a figure.

To draw it, mark $\sigma_{xx}$ and $\sigma_{yy}$ on the normal axis, put the centre midway, plot the $x$-face point $(\sigma_{xx},\sigma_{xy})$ for $\theta=0$, and draw the circle through it. The $y$-face point $(\sigma_{yy},-\sigma_{xy})$ is diametrically opposite, because the two faces are 90° apart on the element. The crossings of the normal axis are the principal stresses, $\sigma_I=\sigma_{average}+R$ on the right and $\sigma_{II}=\sigma_{average}-R$ on the left, and the top and bottom of the circle are the maximum in-plane shear stresses $\pm R$, on planes at 45° to the principal planes where both faces carry $\sigma_{average}$. The angle from the $x$-face point to $\sigma_I$ is $2\theta_p$.

Three special shapes are worth recognising: uniaxial tension gives a circle through the origin, pure shear one centred on the origin, and equal biaxial stress a single point with no shear on any plane. The same construction works for strain with the tensor shear strain $\varepsilon_{xy}=\gamma_{xy}/2$ on the vertical axis. In 3D each pair of principal stresses has its own circle, and the largest of the three gives the maximum shear stress used by the Tresca criterion. Most mistakes come from the sign of $\sigma_{xy}$, which must be read from the right-hand face of the element.

![[s2_mohr_rotation.png|850]]

## Related

- [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#4. Mohr's circle|construction in B4]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Why shear is plotted downwards|why shear is plotted downwards]] · [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - sail element|sail example]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#4. Mohr's circle for strain|strain circle in B5]] · [[FEEG1002 B6 - Yield Criteria#Maximum shear stress in three dimensions|three circles in B6]]
- [[Stress Transformation Equations]] · [[Principal Stresses]] · [[Strain Gauge Rosettes]] · [[Tresca Yield Criterion]]
- Year 2: Mohr's circle for second moments of area, [[Principal Second Moments of Area]], in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]

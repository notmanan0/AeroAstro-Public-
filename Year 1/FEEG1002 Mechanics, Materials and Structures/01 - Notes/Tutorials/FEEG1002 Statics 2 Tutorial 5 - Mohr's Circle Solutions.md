---
title: "FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, mohrs-circle, principal-stresses]
sheet: "Statics-2 Tutorial problem sheet 5"
theory_notes: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
key_concepts: ["[[Mohr's Circle]]", "[[Principal Stresses]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 05 - Mohr's Circle.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 05 - Mohr's Circle - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions

> [!abstract] Sheet Info
> One question: the stress element in a sail. Answers reproduced ✔ ($\sigma_I = 4.3$, $\sigma_{II} = 0.70$ MPa, $\theta_p = -16.8^\circ$).

## Theory Links
- [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[Mohr's Circle]] · [[Principal Stresses]]

---

## Q1: Plane stress in a sail, $\sigma_{xx} = 4$ MPa, $\sigma_{yy} = 1$ MPa, shear 1 MPa
**Reading the shear sign.** On the right-hand ($+x$) face the shear arrow points **down**, and on the top face it points **left**. Both are negative directions on positive faces, so $\sigma_{xy} = \mathbf{-1}$ **MPa**.

### A) Mohr's circle
1. Centre: $\sigma_{avg} = \dfrac{4+1}{2} = 2.5$ MPa.
2. $x$-face point: $(4, -1)$. With the shear axis positive **downwards**, it plots **above** the axis.
3. $y$-face point: $(1, +1)$, diametrically opposite.

### B) Principal stresses

$$
R = \sqrt{\left(\frac{4-1}{2}\right)^2 + 1^2} = 1.80\ \text{MPa}
$$

$$
\sigma_I = 2.5 + 1.80 = \mathbf{4.30}\ \text{MPa},\qquad \sigma_{II} = 2.5 - 1.80 = \mathbf{0.70}\ \text{MPa}\ ✔
$$

The maximum in-plane shear is $R = 1.80$ MPa, on planes at 45° to the principal planes, where both normal stresses are 2.5 MPa.

### C) Principal orientation

$$
\tan2\theta = \frac{2|\sigma_{xy}|}{\sigma_{xx} - \sigma_{yy}} = \frac{2}{3}\;\Rightarrow\;|2\theta| = 33.7^\circ,\quad|\theta| = 16.8^\circ
$$

On the circle, moving from the $x$-face point (above the axis) to $\sigma_I$ is a **clockwise** rotation. So the element rotates **clockwise**: $\theta_p = \mathbf{-16.8^\circ}$. The $x'$ axis carries 4.3 MPa and the $y'$ axis 0.7 MPa, with **no shear**.

![[s2_mohr_t5_sail.png|940]]

> [!tip] Check with the transformation equation
> $\sigma_{x'x'}(\theta = -16.8^\circ) = 4(0.9164) + 1(0.0836) + 2(-1)(-0.2769) = 3.666 + 0.084 + 0.554 = 4.30$ ✔
> Both principal stresses are tensile, so the sail cloth never goes into compression, where it would wrinkle.

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 5

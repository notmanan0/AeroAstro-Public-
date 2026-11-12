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

> [!abstract] Sheet info
> One question: the stress element at a point in a sail. All answers match the official solution ($\sigma_I=4.3$ MPa, $\sigma_{II}=0.70$ MPa, $\theta_p=-16.8^\circ$), checked numerically.

## Q1 Plane stress element in a sail

*Taught in:* [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Constructing the circle]] and [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#5. Principal stresses and maximum shear]] · worked in full at [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - sail element]].

**Reading the element.** $\sigma_{xx}=4$ MPa and $\sigma_{yy}=1$ MPa. On the right-hand face the shear arrow points down and on the top face it points left: negative directions on faces with positive normals, so $\sigma_{xy}=-1$ MPa.

**A) Mohr's circle.** The centre is $\sigma_{average}=(4+1)/2=2.5$ MPa. With shear plotted positive downwards, the $x$-face point $(4,-1)$ lies above the axis; the $y$-face point $(1,+1)$ is diametrically opposite, below it.

**B) Principal stresses.**

$$
R=\sqrt{\left(\frac{4-1}{2}\right)^2+(-1)^2}=1.80\ \mathrm{MPa}
$$

$$
\sigma_I=2.5+1.80=4.30\ \mathrm{MPa},\qquad \sigma_{II}=2.5-1.80=0.70\ \mathrm{MPa}
$$

The maximum in-plane shear stress is $R=1.80$ MPa, on planes at 45° to the principal planes, where both normal stresses are 2.5 MPa.

**C) Principal element.**

$$
\tan|2\theta|=\frac{2|\sigma_{xy}|}{\sigma_{xx}-\sigma_{yy}}=\frac23\ \Rightarrow\ |2\theta|=33.7^\circ,\quad |\theta|=16.8^\circ
$$

Going from the $x$-face point, above the axis, down to $\sigma_I$ is a clockwise rotation on the circle, so the element turns clockwise: $\theta_p=-16.8^\circ$. The $x'$ axis then carries 4.3 MPa and the $y'$ axis 0.7 MPa, with no shear.

**Check.** $\sigma_{x'x'}(-16.8^\circ)=4(0.9164)+1(0.0836)+2(-1)(-0.2769)=4.30$ MPa. Both principal stresses are tensile, so the sail cloth is stretched in every direction at this point and does not wrinkle.

![[s2_mohr_t5_sail.png|900]]

## Sources

- `Tutorial Sheet 05 - Mohr's Circle.pdf` and its solutions.

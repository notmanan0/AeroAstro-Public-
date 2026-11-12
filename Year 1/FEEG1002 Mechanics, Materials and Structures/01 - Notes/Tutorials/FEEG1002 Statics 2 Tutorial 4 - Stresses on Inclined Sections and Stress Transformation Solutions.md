---
title: "FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, stress-transformation]
sheet: "Statics-2 Tutorial problem sheet 4"
theory_notes: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
key_concepts: ["[[Stress Transformation Equations]]", "[[Thin-Walled Pressure Vessels]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions

> [!abstract] Sheet info
> One question: the stresses on a helical weld in a cylindrical pressure vessel. Both answers match the official solution (107 MPa normal, 37.1 MPa shear), checked numerically and by Mohr's circle.

## Q1 Helical weld at 60 degrees to the axis

*Taught in:* [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#2. Plane-stress transformation]] · worked in full at [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#Worked example - helical weld in a pressure vessel]].

Data: diameter 1.2 m ($R=0.6$ m), wall 7 mm, internal pressure 2 MPa. With $x$ along the axis and $y$ round the circumference there is no shear:

$$
\sigma_{xx}=\frac{pR}{2t}=\frac{(2\times10^6)(0.6)}{2(0.007)}=85.7\ \mathrm{MPa},\qquad \sigma_{yy}=\frac{pR}{t}=171.4\ \mathrm{MPa},\qquad \sigma_{xy}=0
$$

The weld line is at 60° to the axis, so the normal to the weld plane is at $\theta=90^\circ-60^\circ=30^\circ$ to $x$:

$$
\sigma_{x'x'}=85.7\cos^230^\circ+171.4\sin^230^\circ+0=107\ \mathrm{MPa}
$$

$$
\sigma_{x'y'}=-(85.7-171.4)\sin30^\circ\cos30^\circ+0=37.1\ \mathrm{MPa}
$$

**Mohr's circle check.** The centre is 128.6 MPa and $R=42.9$ MPa; the $x$-face point is $\sigma_{II}=85.7$ MPa, and turning it through $2\theta=60^\circ$ gives a normal stress $128.6-42.9\cos60^\circ=107.1$ MPa and a shear stress $42.9\sin60^\circ=37.1$ MPa.

A weld wound the other way has its normal at $-30^\circ$: the normal stress is unchanged and the shear stress becomes $-37.1$ MPa, so the magnitude is what the question needs. A longitudinal seam would carry the full 171 MPa hoop stress across it, which is why spiral welding is used.

![[s2_mohr_t4_weld.png|900]]

## Sources

- `Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation.pdf` and its solutions.

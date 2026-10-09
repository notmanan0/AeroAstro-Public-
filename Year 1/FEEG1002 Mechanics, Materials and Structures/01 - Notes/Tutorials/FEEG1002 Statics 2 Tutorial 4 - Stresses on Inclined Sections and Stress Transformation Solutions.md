---
title: "FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, stress-transformation]
sheet: "Statics-2 Tutorial problem sheet 4"
theory_notes: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
key_concepts: ["[[Stress Transformation Equations]]", "[[Thin-Walled Pressure Vessels]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 04 - Stresses on Inclined Sections and Stress Transformation - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions

> [!abstract] Sheet Info
> One question: stresses on a helical weld. Answers reproduced ✔ (107 MPa normal, 37.1 MPa shear). The Mohr's circle below gives the same numbers graphically.

## Theory Links
- [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · [[Stress Transformation Equations]]

---

## Q1: Pressure vessel $D = 1.2$ m, $t = 7$ mm, $p = 2$ MPa, helical weld at $\alpha = 60^\circ$ to the axis
**Principal stresses** (no shear in the axial–hoop frame):

$$
\sigma_{xx} = \frac{pR}{2t} = \frac{(2\times10^6)(0.6)}{2(0.007)} = 85.7\ \text{MPa},\qquad \sigma_{yy} = \frac{pR}{t} = 171.4\ \text{MPa},\qquad \sigma_{xy} = 0
$$

**Which angle?** The weld **line** is at 60° to the axis, so the weld plane's **normal** is at $\theta = 90^\circ - 60^\circ = 30^\circ$ to $x$.

$$
\sigma_{x'x'} = 85.7\cos^230^\circ + 171.4\sin^230^\circ + 0 = \mathbf{107}\ \text{MPa}\ ✔
$$

$$
\sigma_{x'y'} = -(85.7 - 171.4)\sin30^\circ\cos30^\circ + 0 = \mathbf{37.1}\ \text{MPa}\ ✔
$$

**Mohr's circle check.** The centre is 128.6 and $R = 42.9$. The weld point sits $2\theta = 60^\circ$ from the $x$-face point:
- normal stress $128.6 - 42.9\cos60^\circ = 107.1$;
- shear stress $42.9\sin60^\circ = 37.1$ ✔

![[s2_mohr_t4_weld.png|920]]

> [!tip] Why helical welds are used
> The weld carries only 107 MPa normal stress, compared with 171 MPa for a longitudinal seam, which would carry the full hoop stress. Spiral-welded pipe exploits this: the normal stress across the weld is reduced at the cost of some shear.

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 4

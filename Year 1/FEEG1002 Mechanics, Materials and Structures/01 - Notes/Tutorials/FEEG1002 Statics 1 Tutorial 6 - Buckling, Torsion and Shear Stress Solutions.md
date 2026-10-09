---
title: "FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, buckling, torsion, shear-stress]
sheet: "Statics-1 Tutorial problem sheet 6"
theory_notes: ["[[FEEG1002 A7 - Euler Buckling of Struts]]", "[[FEEG1002 A8 - Torsion of Circular Shafts]]", "[[FEEG1002 A9 - Shear Stresses in Beams]]"]
key_concepts: ["[[Euler Buckling]]", "[[Effective Length]]", "[[Torsion of Circular Shafts]]", "[[Shear Stress Distribution in Beams]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions

> [!abstract] Sheet Info
> One question on each of the last three Statics 1 lectures. All answers are reproduced ✔ (9.0 kN; 64 mm and 58 MPa; 0.30 MPa and 16.7 cm).

## Theory Links
- [[FEEG1002 A7 - Euler Buckling of Struts]] · [[FEEG1002 A8 - Torsion of Circular Shafts]] · [[FEEG1002 A9 - Shear Stresses in Beams]]

---

## Q1: Stainless steel I-column, $L = 5$ m, $E = 213$ GPa, pin-ended
Section: flanges 40 × 10 mm, web 5 × 30 mm, total depth 50 mm. It is doubly symmetric, so the centroid is at the middle.

**(i) Minimum buckling load.** Compute **both** second moments; the column buckles about the weaker axis.

$$
I_{zz} = 2\left(\frac{40(10)^3}{12} + 400(20)^2\right) + \frac{5(30)^3}{12} = 3.38\times10^{-7}\ \text{m}^4
$$

$$
I_{yy} = 2\left(\frac{10(40)^3}{12}\right) + \frac{30(5)^3}{12} = 1.07\times10^{-7}\ \text{m}^4\quad(\text{smaller})
$$

$$
P_{cr} = \frac{\pi^2EI_{yy}}{L_e^2} = \frac{\pi^2(213\times10^9)(1.07\times10^{-7})}{5^2} = \mathbf{9.0}\ \text{kN}\ ✔
$$

Slenderness check: $r = \sqrt{I_{yy}/A} = \sqrt{1.07\times10^{-7}/950\times10^{-6}} = 10.6$ mm, so $L_e/r\approx470$. That is far above the transition slenderness, so buckling certainly governs. The Euler stress is only 9.5 MPa.

**(ii) Extra pinned support at midspan.** The lateral deflection is suppressed at midspan but rotation is still allowed, so the mode becomes a full sine wave with $L_e = L/2$:

$$
P_{cr}' = \frac{\pi^2EI}{(L/2)^2} = 4P_{cr}\quad(\text{factor } \mathbf 4)
$$

![[s1_buckling_mode_shapes.png|640]]

---

## Q2: Steel shaft inside an aluminium tube, $T = 3$ kN m, $D_o = 70$ mm
**(i) Bore for $\tau_{Al}\le150$ MPa.** The maximum stress is at the outer radius:

$$
\tau_{max} = \frac{TR_o}{J} = \frac{2TR_o}{\pi(R_o^4 - R_i^4)}\;\Rightarrow\; R_i = \left(R_o^4 - \frac{2TR_o}{\pi\tau_{max}}\right)^{1/4} = 0.0320\ \text{m}
$$

The inner diameter is **64 mm** ✔. The tube is only 3 mm thick ($n = 0.916$), which is a very efficient use of material.

**(ii) Stress in the steel shaft that just fits.** $R = R_i$, so

$$
\tau_{max,steel} = \frac{2T}{\pi R_i^3} = \frac{2(3000)}{\pi(0.032)^3} = \mathbf{58}\ \text{MPa}\ ✔
$$

Both parts carry the **same torque** in series, but the solid steel shaft has the smaller $J/R$. It still sits comfortably below typical steel shear limits.

![[s1_torsion_hollow_vs_solid.png|760]]

---

## Q3: Glued laminated beam, two 50 mm square timbers, $F = 2$ kN at midspan, total span $2L$ ($L = 1.5$ m)
**(i) Glue shear stress.** The glue line is on the **neutral axis**, where $\tau$ is largest. The shear force is $F/2$ throughout, only its sign changes. For a rectangle $K = 3/2$:

$$
\tau_{glue} = K\frac{Q}{A} = \frac32\cdot\frac{F/2}{2d^2} = \frac{1.5(2000)}{4(0.05)^2} = \mathbf{0.30}\ \text{MPa}\ ✔
$$

The span length does not enter: shear stress depends on $Q$, not $M$.

**(ii) Screw spacing.** Screw core 4 mm, $\tau_{allow} = 200$ MPa, friction ignored.
- One screw carries $F_s = \tau\,\pi D^2/4 = 2.51$ kN.
- The horizontal shear flow along the joint is $q = \tau_{glue}\,b = 0.3\times10^6(0.05) = 15$ kN/m.
- So $n = q/F_s = 5.96$ per metre. Round **up** to 6 per metre: spacing **16.7 cm** ✔

![[s1_beam_shear_stress.png|860]]

> [!tip] Bending would govern the timber itself
> $M_{max} = FL/2 = 1.5$ kN m on a 50 × 100 mm section gives $\sigma = 6M/bd^2 = 18$ MPa, which is 60× the glue shear stress, as expected from $\sigma/\tau\sim4L/d$. The glue line is still the weak link: glue shear strength is only a few MPa, and timber is weak in shear along the grain.

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 6

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

> [!abstract] Sheet info
> One question on each of the last three Statics 1 topics: the Euler load of a pin-ended I-section column, a steel shaft joined to an aluminium tube in torsion, and the shear stress in the glue line of a laminated timber beam. All printed answers (9.0 kN; 64 mm and 58 MPa; 0.30 MPa and 16.7 cm) are reproduced and every number was recomputed in Python. None of these three topics was examined in January.

Theory: [[FEEG1002 A7 - Euler Buckling of Struts]] · [[FEEG1002 A8 - Torsion of Circular Shafts]] · [[FEEG1002 A9 - Shear Stresses in Beams]]

---

## Q1 - Pin-ended I-section column

Taught in: [[FEEG1002 A7 - Euler Buckling of Struts#Worked example - pin-ended I-section column|A7, I-section column]] · [[FEEG1002 A7 - Euler Buckling of Struts#2. Direction of buckling|A7, direction of buckling]]

A stainless steel column of length 5 m, with $E=213$ GPa, has an I-section with flanges 40 mm wide and 10 mm thick and a web 5 mm thick and 30 mm deep, 50 mm deep overall. The section is doubly symmetric, so its centroid is at the middle.

**(i) Minimum buckling load.** The column buckles about the axis with the smaller second moment, so both are needed. About $z$, each flange centroid is 20 mm from the axis:

$$
I_{zz}=2\left(\frac{40(10)^3}{12}+400(20)^2\right)+\frac{5(30)^3}{12}=3.38\times10^{-7}\ \mathrm m^4
$$

About $y$, every part is centred on the axis:

$$
I_{yy}=2\left(\frac{10(40)^3}{12}\right)+\frac{30(5)^3}{12}=1.07\times10^{-7}\ \mathrm m^4
$$

$I_{yy}$ is the smaller, so with $L_e=L$ for a pin-ended strut:

$$
P_{crit}=\frac{\pi^2EI_{yy}}{L_e^2}=\frac{\pi^2(213\times10^9)(1.07\times10^{-7})}{5^2}=9.0\ \mathrm{kN}
$$

The section area is 950 mm², so the Euler stress is only 9.5 MPa, far below any yield stress. The column is very slender: $r=\sqrt{I_{yy}/A}=10.6$ mm and $L_e/r\approx470$, so buckling governs.

**(ii) Extra pinned support at midspan.** The support prevents lateral deflection at midspan but allows rotation, so the lowest mode becomes the second pin-ended mode, a full sine wave with a node at midspan. Each half buckles as a pin-ended strut of length $L/2$:

$$
P_{crit}'=\frac{\pi^2EI}{(L/2)^2}=4P_{crit}
$$

The load rises by a factor of 4, to 36 kN.

![[s1_buckling_mode_shapes.png|640]]

---

## Q2 - Steel shaft and aluminium tube

Taught in: [[FEEG1002 A8 - Torsion of Circular Shafts#Worked example - steel shaft and aluminium tube|A8, steel shaft and aluminium tube]] · [[FEEG1002 A8 - Torsion of Circular Shafts#The torsion equations|A8, torsion equations]]

A solid steel shaft and a hollow aluminium tube are joined end to end and transmit $T=3$ kN m. The tube's outer diameter is fixed at 70 mm, so $R_o=0.035$ m.

**(i) Bore of the tube for $\tau_{Al}\le150$ MPa.** The largest shear stress is at the outer radius, and $J=\tfrac{\pi}{2}(R_o^4-R_i^4)$ for a hollow shaft:

$$
\tau_{max}=\frac{TR_o}{J}=\frac{2TR_o}{\pi(R_o^4-R_i^4)}
$$

Rearranging for the inner radius:

$$
R_i=\left(R_o^4-\frac{2TR_o}{\pi\tau_{max}}\right)^{1/4}=0.0320\ \mathrm m
$$

The inner diameter is 64 mm. The tube wall is only 3 mm thick ($n=R_i/R_o=0.916$).

**(ii) Stress in a steel shaft that just fits the tube.** The steel shaft has $R=R_i=0.032$ m and $J=\pi R^4/2$:

$$
\tau_{max,steel}=\frac{2T}{\pi R^3}=\frac{2(3000)}{\pi(0.032)^3}=58\ \mathrm{MPa}
$$

Both parts carry the same torque, so their peak stresses go as $R/J$. The thin aluminium tube has the smaller $J/R$, $2.0\times10^{-5}$ m³ against $5.2\times10^{-5}$ m³ for the solid steel shaft, and therefore the higher stress: 150 MPa against 58 MPa.

![[s1_torsion_hollow_vs_solid.png|760]]

---

## Q3 - Glued timber beam

Taught in: [[FEEG1002 A9 - Shear Stresses in Beams#Worked example - glued timber beam|A9, glued timber beam]] · [[FEEG1002 A9 - Shear Stresses in Beams#5. The shear stress coefficient|A9, shear stress coefficient]]

Two square timbers of side $d=50$ mm are glued one on top of the other, making a 50 mm wide, 100 mm deep section. The beam spans $2L$ with $L=1.5$ m, simply supported, with $F=2$ kN at midspan.

**(i) Shear stress in the glue.** The glue line is on the neutral axis, where the shear stress is largest. The shear force has magnitude $F/2$ everywhere; only its sign changes at midspan. For a rectangle $K=3/2$, so

$$
\sigma_{yx}=K\frac{Q}{A}=\frac32\cdot\frac{F/2}{2d^2}=\frac{1.5(2000)}{4(0.05)^2}=0.30\ \mathrm{MPa}
$$

The span does not enter, because the shear stress depends on $Q$, not $M$.

**(ii) Screw spacing.** A single row of screws with a 4 mm core diameter and an allowable shear stress of 200 MPa replaces the glue, and friction is ignored. One screw carries

$$
F_s=\tau\frac{\pi D^2}{4}=200\times10^6\cdot\frac{\pi(0.004)^2}{4}=2.51\ \mathrm{kN}
$$

The horizontal shear force per unit length that the joint must carry is the glue stress times the width:

$$
q=\sigma_{yx}b=0.3\times10^6(0.05)=15\ \mathrm{kN/m}
$$

So $q/F_s=5.97$ screws are needed per metre. Rounding up to 6 per metre gives a spacing of 16.7 cm (exactly, $F_s/q=16.8$ cm is the largest spacing that works).

![[s1_beam_shear_stress.png|860]]

> [!check] Bending stress for comparison
> $M_{max}=(F/2)L=1.5$ kN m on the 50 × 100 mm section gives $\sigma=6M/(bh^2)=18$ MPa, 60 times the glue shear stress. That agrees with $\sigma/\sigma_{yx}=4L/h$ with $h=100$ mm. The glue line can still be the weak link, because glue shear strengths are a few MPa and timber is weak in shear along the grain.

## Sources

- Tutorial Sheet 06 and its official solutions: Q1 pp. 1–2, Q2 pp. 3–4, Q3 pp. 5–6.
- Q1(ii) has no printed answer on the problem sheet; the factor of 4 is from the official solution (p. 2).

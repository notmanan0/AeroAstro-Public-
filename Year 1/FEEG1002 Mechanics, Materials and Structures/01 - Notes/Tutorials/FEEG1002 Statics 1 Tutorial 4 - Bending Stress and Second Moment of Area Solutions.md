---
title: "FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part A: Statics 1"
tags: [feeg1002, tutorial-solutions, statics, bending-stress, second-moment-of-area]
sheet: "Statics-1 Tutorial problem sheet 4"
theory_notes: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]", "[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Engineer's Bending Theory]]", "[[Parallel Axis Theorem]]", "[[Second Moments of Area]]"]
status: complete
sources: ["02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area.pdf", "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 04 - Beams, Stress and 2nd Moment of Area - Solutions.pdf"]
---

# FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions

> [!abstract] Sheet Info
> Sizing a square beam, $I$ of an unequal I-section, a T-section hoist, three rods, a section with holes and a water channel. All answers are reproduced ✔.
> Workflow for every question: **(1)** BMD → $M_{max}$; **(2)** centroid → $I$; **(3)** $y_{max}$ on the critical side; **(4)** $\sigma = My/I$.

## Theory Links
- [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] · [[Parallel Axis Theorem]] · [[Engineer's Bending Theory]]

---

## Q1: Square beam, UDL on the overhang, $w = 6$ kN/m, $L = 3$ m, $\sigma_{allow} = 300$ MPa
- Reactions (resultant $wL$ at $L/2$; the pin is at $x = L$, the roller at $2L$): $R_a = \tfrac32wL = 27$ kN and $R_b = -\tfrac12wL = -9$ kN. The roller pulls **down**.
- SFD: falls linearly from 0 to $-wL$ at the pin, jumps to $+wL/2$, stays constant, and returns to zero at the roller.
- BMD: parabolic to $M_{max} = -\tfrac12(wL)L = -wL^2/2 = -27$ kN m over the support, then linear back to 0.

![[s1_t4_q1.png|720]]

Stress in a square $H\times H$ section: $\sigma_{max} = \dfrac{M(H/2)}{H^4/12} = \dfrac{6M}{H^3}$, so

$$
H = \sqrt[3]{\frac{6M_{max}}{\sigma_{max}}} = \sqrt[3]{\frac{3wL^2}{\sigma_{max}}} = \mathbf{0.0814}\ \text{m}\ ✔
$$

## Q2: Unequal I-section
Parts: bottom flange (1) 100 × 20, web (2) 15 × 40, top flange (3) 60 × 15 (mm).

**(i) $I_{yy}$ (bending about the vertical symmetry axis).** Every part is centred on this axis, so the parallel-axis terms are zero:
$$I_{yy} = \frac{20(100)^3}{12} + \frac{40(15)^3}{12} + \frac{15(60)^3}{12} = (1.667 + 0.011 + 0.270)\times10^{-6} = \mathbf{1.95\times10^{-6}}\ \text{m}^4\ ✔$$

**(ii) $I_{zz}$ (neutral axis not at mid-height).**
- Centroid from the base: $\bar y = \dfrac{2000(10) + 600(40) + 900(67.5)}{3500} = 29.93$ mm. It sits low, because the wide bottom flange dominates.
- Distances from the centroid: $h = 19.93$, $10.07$, $37.57$ mm.

| Part | $bd^3/12$ (mm⁴) | $Ah^2$ (mm⁴) | Total (m⁴) |
|---|---|---|---|
| 1 | 66 667 | 794 400 | $8.61\times10^{-7}$ |
| 2 | 80 000 | 60 840 | $1.41\times10^{-7}$ |
| 3 | 16 875 | 1 270 300 | $1.29\times10^{-6}$ |

$$I_{zz} = \mathbf{2.29\times10^{-6}}\ \text{m}^4\ ✔$$

## Q3: Inverted-T cantilever hoist, load 1.0 m from the wall, $\sigma_{allow} = 330$ MPa
- **Section**: web (1) 0.01 × 0.09 with centroid 0.055 m above the base; flange (2) 0.1 × 0.01 with centroid 0.005 m. Then $\bar y = \dfrac{9\times10^{-4}(0.055) + 10^{-3}(0.005)}{1.9\times10^{-3}} = 0.0287$ m.
- $I = \left[\tfrac{0.01(0.09)^3}{12} + 9\times10^{-4}(0.0263)^2\right] + \left[\tfrac{0.1(0.01)^3}{12} + 10^{-3}(0.0237)^2\right] = 1.80\times10^{-6}$ m⁴.
- **Moment**: $Q = F$ and $M = -F(L-x)$, so $|M_{max}| = FL$ at the wall (hogging, tension on top).
- **Critical fibre**: the **top** is $0.1 - 0.0287 = 0.0713$ m from the neutral axis. That is further than the base (0.0287 m), and it is in tension:
$$M_{max} = \frac{\sigma I}{y_{max}} = \frac{330\times10^6(1.8\times10^{-6})}{0.0713} = 8.33\ \text{kN m}\;\Rightarrow\; F = \mathbf{8.33}\ \text{kN}\ ✔$$

![[s1_bending_stress_tsection.png|860]]

> [!tip] Orientation matters
> Flip the T (flange on top) under the same hogging moment and the far fibre is the web tip in **compression**. For a material weaker in tension (cast iron, concrete), put the wide flange on the tension side.

---

## Extra Q1: Crane boom of three rods, $D = 0.1$ m, triangle height $H = 0.6$ m
- Centroid: taking moments about the line through rods 2 and 3, $3A\,h = AH$, so $h = H/3$.
- $I_1 = \dfrac{\pi D^4}{64} + \dfrac{\pi D^2}{4}\left(\dfrac23H\right)^2$ and $I_2 = I_3 = \dfrac{\pi D^4}{64} + \dfrac{\pi D^2}{4}\left(\dfrac13H\right)^2$.
$$I_{zz} = \pi\left(\frac{3D^4}{64} + \frac{D^2H^2}{6}\right) = \mathbf{0.0019}\ \text{m}^4\ ✔$$
The own-axis terms contribute only 0.8%. This is the parallel axis theorem in its purest form.

## Extra Q2: 60 × 80 mm block with two Ø22 mm holes at ±20 mm
Subtract the holes:
- $I_{zz} = \dfrac{60(80)^3}{12} - 2\left[\dfrac{\pi(22)^4}{64} + 380.13(20)^2\right] = \mathbf{2.23\times10^{-6}}$ m⁴ ✔
- $I_{yy} = \dfrac{80(60)^3}{12} - 2\dfrac{\pi(22)^4}{64} = \mathbf{1.42\times10^{-6}}$ m⁴ ✔ (the holes lie on this axis)

## Extra Q3: Sheet-metal water channel (400 × 200 mm, 3 mm thick), water 150 mm deep, $\sigma_{allow} = 35$ MPa
- Load: $w = \rho gA = 1000(9.81)(0.394)(0.15) = 579.8$ N/m, a UDL on a simply supported span, so $M_{max} = wL^2/8$.
- Section: walls 197 × 3 (591 mm² each) and base 400 × 3 (1200 mm²). Centroid $\bar y = 51.12$ mm above the base, and $I = 9.78\times10^{-6}$ m⁴.
- Critical fibre: the wall tops, $200 - 51.1 = 148.9$ mm from the neutral axis, in compression.
$$\frac{wL^2}{8}\cdot\frac{0.1489}{9.78\times10^{-6}}\le35\times10^6\;\Rightarrow\; L_{max} = \mathbf{5.63}\ \text{m}\ ✔$$

## Sources
- Source sheet and official solutions: Statics-1 Tutorial problem sheet 4
- Section properties recomputed in `Figures/generate_statics1_figures.py` (`section_gallery`)

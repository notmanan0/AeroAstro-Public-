---
title: "FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 4
tags: [feeg1002, statics, beams, bending-stress, second-moment-of-area, neutral-axis]
aliases: ["Statics 1 Lecture 7", "Statics 1 Lecture 8", "Bending stress", "M/I = sigma/y = E/R"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
next_topics: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
key_concepts: ["[[Engineer's Bending Theory]]", "[[Parallel Axis Theorem]]", "[[Second Moments of Area]]", "[[First Moment of Area]]", "[[Section Modulus]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 07 - Beams, Stress Due to Bending.pdf", "02 - Sources/Statics 1/Lectures/Lecture 08 - Beams, Second Moment of Area Continued.pdf"]
---

# FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area

> [!abstract] Summary
> Under pure bending, plane sections stay plane, so strain varies **linearly** through the depth: $\varepsilon_{xx} = y/R$.
> - Hooke's law makes the bending stress linear too.
> - **Force** equilibrium puts the neutral axis through the **centroid**.
> - **Moment** equilibrium brings in the geometric stiffness $I = \iint y^2\,dA$.
>
> Together these give engineer's bending theory:
>
> $$\frac{M}{I} = \frac{\sigma}{y} = \frac{E}{R}$$
>
> The **parallel axis theorem** $I_{z'z'} = I_{zz} + Ab^2$ builds $I$ for composite sections. It also explains why I-beams and tubes are so efficient: material far from the neutral axis is worth $b^2$.

## Key Concepts
- [[Engineer's Bending Theory]] · [[Parallel Axis Theorem]] · [[Second Moments of Area]] · [[First Moment of Area]] · [[Section Modulus]]

---

## 1. Deformation in pure bending (L7a)
The model assumes:
- plane cross-sections remain plane;
- the beam bends into a circular arc whose radius $R$ is much greater than the depth;
- stresses are longitudinal only;
- the material is linear elastic, with the same $E$ in tension and compression.

In a sagging beam the lower fibres ($A_2B_2$) stretch and the upper fibres ($A_1B_1$) shorten. Somewhere between them lies the **neutral surface**, whose length does not change. Where it cuts the cross-section is the **neutral axis**.

$$
\varepsilon_{xx} = \frac{(R+y)\,d\theta - R\,d\theta}{R\,d\theta} = \frac{y}{R}
$$

with $y$ measured **downwards** from the neutral surface.

- **Anticlastic curvature**: $\varepsilon_{yy} = \varepsilon_{zz} = -\nu\varepsilon_{xx}$ bends the cross-section the opposite way. It matters in bridge-deck camber.
- With $\sigma_{yy} = \sigma_{zz} = 0$, Hooke gives $\sigma_{xx} = Ey/R$. The stress is linear in $y$ and largest at the outer fibres.

## 2. Equilibrium gives the theory (L7b)

**Axial force:**

$$F = \iint\sigma_{xx}\,dA = \frac{E}{R}\iint y\,dA = 0\;\Rightarrow\;\iint y\,dA = 0$$

The first moment of area about the neutral axis is zero, so the **neutral axis passes through the centroid**. Picture the section balancing on a knife-edge.

**Moment:**

$$M = \iint\sigma_{xx}\,y\,dA = \frac{E}{R}\iint y^2\,dA = \frac{EI}{R}$$

$$
\boxed{\frac{M}{I} = \frac{\sigma}{y} = \frac{E}{R}}\qquad\Rightarrow\qquad \sigma = \frac{My}{I},\quad \sigma_{max} = \frac{M_{max}\,y_{max}}{I}
$$

The theory is strictly for pure bending ($Q = 0$). With shear present the error is negligible for slender beams.

## 3. Standard second moments of area (L7c, L8a)

| Section | $I$ about the centroidal axis |
|---|---|
| Rectangle $b\times d$ (bending about the axis parallel to $b$) | $\dfrac{bd^3}{12}$ |
| Solid circle | $\dfrac{\pi R^4}{4} = \dfrac{\pi D^4}{64}$ |
| Hollow circle | $\dfrac{\pi(D_o^4 - D_i^4)}{64}$ |
| Symmetric I (subtract the missing material) | $\dfrac{bd^3}{12} - \dfrac{(b-t_w)(d-2t_f)^3}{12}$ |

- For the rectangle, $I_{zz} = \int_{-d/2}^{d/2} y^2\,b\,dy$. For the circle, switch to polar coordinates with $dA = r\,dr\,d\theta$ and $y = r\sin\theta$.
- Only **depth** is cubed. Turning a plank on edge raises $I$ by $(d/b)^2$.

> [!example] L7 example 3: rectangular cantilever with end load $F$
> $M_{max} = -FL$ at the root, so
>
> $$\sigma_{max} = \frac{(-FL)(\mp d/2)}{bd^3/12} = \pm\frac{6FL}{bd^2}$$
>
> The top is in **tension** (hogging) and the bottom in compression.

**Superposition.** For a linear elastic beam, combined axial and bending stresses add: $\sigma = F/A + My/I$. An eccentric load does both.

## 4. Parallel axis theorem (L8b)

$$
I_{z'z'} = \underbrace{\iint y^2\,dA}_{I_{zz}} + 2b\underbrace{\iint y\,dA}_{=0} + b^2\underbrace{\iint dA}_{A} = I_{zz} + Ab^2
$$

- It applies only when the $z$-axis passes through the **centroid of the part**.
- The minimum $I$ of any family of parallel axes is the centroidal one.

> [!example] L8 I-beam: 60 × 5 flanges, 5 × 90 web, total depth 100 mm
> - Web: $5(90)^3/12 = 303\,750$ mm⁴.
> - Each flange: $60(5)^3/12 + 300(47.5)^2 = 625 + 676\,875 = 677\,500$ mm⁴.
> - Total $I_{zz} = 1.659\times10^{-6}$ m⁴.
>
> The flanges' $Ab^2$ terms are more than 1000× their own $bd^3/12$.

![[s1_parallel_axis_contributions.png|700]]

## 5. Sections with one axis of symmetry (L8c)
The neutral axis is no longer self-evident. Proceed in two steps:
1. Locate the centroid by **moments of area** about a convenient base: $A\bar y = \sum A_i y_i$.
2. Apply the parallel axis theorem to each part about the **whole-section** centroid.

> [!example] L8 channel: 120 × 50 mm, 5 mm walls
> - Areas: 250, 250, 550 mm², so $1050\,\bar d = 250(25)\times2 + 550(2.5)$, giving $\bar d = 13.21$ mm.
> - $I_{zz} = 2\left[\frac{5\cdot50^3}{12} + 250(11.79)^2\right] + \left[\frac{110\cdot5^3}{12} + 550(10.71)^2\right] = 237\,901$ mm⁴ $= 2.379\times10^{-7}$ m⁴.

![[s1_section_gallery.png|940]]

> [!warning] Unsymmetric sections: check both fibres
> When the neutral axis is off-centre, $y_{max}$ differs above and below it, so the extreme tensile and compressive stresses differ. In Tutorial 4 Q3 (inverted T, hogging) the **top** fibre, 71.3 mm from the neutral axis, governs, and $F_{max} = \sigma_{allow}I/(y_{max}L) = 8.33$ kN. For brittle materials such as concrete or cast iron, tension and compression have different allowables, so each must be checked separately.

![[s1_bending_stress_tsection.png|880]]

## 6. Strength design procedure (L7c)
1. Draw the BMD and find $M_{max}$ (including sign).
2. Find $y_{max}$ on the tension side and on the compression side.
3. Check $\sigma = My/I \le \sigma_{allow}$ for each. Equivalently use the section modulus $Z = I/y_{max}$, so that $\sigma_{max} = M/Z$ ([[Section Modulus]]).
4. Design ideas:
   - move material outwards (I-beams, box sections, hollow tubes);
   - taper the beam so that $I(x)/y_{max}(x) = M(x)/\sigma_{max}$;
   - weigh material efficiency against manufacturing cost.

## Year 2 bridge
| FEEG1002 (one symmetry axis, bending about $z$) | SESA2028 generalisation |
|---|---|
| $\sigma = My/I$, neutral axis perpendicular to the load | [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]: $I_{yz}\neq0$ couples the two bending planes and the [[Neutral Axis in Unsymmetrical Bending]] tilts |
| $I_{z'z'} = I_{zz} + Ab^2$ | Plus $I_{y'z'} = I_{yz} + A\,\Delta y\,\Delta z$ and the [[Principal Axes of a Section]] / [[Principal Second Moments of Area]] (a "Mohr's circle" for $I$) |
| Section chosen for $I/y_{max}$ | [[Section Modulus]] and [[Specific Stiffness and Strength]] (material indices $E^{1/2}/\rho$, $\sigma^{2/3}/\rho$) |
| $1/R = M/EI$ | [[Moment Curvature Relation]], then deflection in [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] and [[SESA2028 S2 - Beam Deflection and Bending Design]] |

> [!note] Axis names change between modules
> FEEG1002 calls the bending axis $z$ ($I_{zz} = \iint y^2 dA$, $y$ downwards). SESA2028 keeps $y$ and $z$ for the two section axes and writes $I_{yy} = \iint z^2 dA$, $I_{zz} = \iint y^2 dA$. Always read the axes off the figure before using a formula.

## Links
- Previous: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · Next: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]]

## Sources
- Statics 1 Lectures 7a–c (stress due to bending; engineer's bending theory; examples) and 8a–c (second moment of area; parallel axis theorem; neutral axis)

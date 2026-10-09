---
title: "FEEG1002 A8 - Torsion of Circular Shafts"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 8
tags: [feeg1002, statics, torsion, shafts, polar-second-moment]
aliases: ["Statics 1 Lecture 13", "Torsion", "T/J = tau/r = G theta/L"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 A9 - Shear Stresses in Beams]]"]
key_concepts: ["[[Torsion of Circular Shafts]]", "[[Saint-Venant Torsion]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 13 - Torsion.pdf"]
---

# FEEG1002 A8 - Torsion of Circular Shafts

> [!abstract] Summary
> In a circular shaft under torque $T$, cross-sections stay **plane** and radii stay **straight**. Each section simply rotates relative to its neighbours. The material is therefore in **pure shear**, with $\gamma = r\theta/L$, so the shear stress grows linearly from zero on the axis to a maximum at the surface. Integrating $\tau r\,dA$ over the section gives the torsion equation
> $$\frac{T}{J} = \frac{\tau}{r} = \frac{G\theta}{L}$$
> where the polar second moment of area is $J = \pi R^4/2 = \pi D^4/32$. It has the same structure as $M/I = \sigma/y = E/R$.

## Key Concepts
- [[Torsion of Circular Shafts]] · [[Saint-Venant Torsion]]

---

## 1. Kinematics (L13a)
- A torque twists the shaft. Examples: drive shafts, propeller shafts, rotating machinery.
- By symmetry and compatibility, the faces either side of any cut must fit together, so:
  - cross-sections stay **plane** (no warping or bulging);
  - radial lines stay **straight** and radial;
  - the shaft deforms only by one plane rotating relative to the next.
- This holds **only for circular (solid or hollow) sections**. Non-circular sections warp ([[Open-Section Torsion]]).

## 2. Strain and stress (L13b)
Unroll the surface. A surface element whose ends twist by $\theta$ over length $L$ is sheared through

$$
\gamma(r) = \tan\varphi = \frac{r\theta}{L},\qquad \tau(r) = G\gamma = \frac{G\theta}{L}r
$$

- The element is in **pure shear**: the length and diameter do not change.
- The stress is zero on the axis and a maximum at the outer radius.

## 3. Torque and the torsion equation (L13b)
A ring of area $r\,d\psi\,dr$ carries force $\tau r\,d\psi\,dr$ and torque $\tau r^2\,d\psi\,dr$:

$$
T = \int_0^R\int_0^{2\pi}\tau r^2\,d\psi\,dr = \frac{G\theta}{L}\int_0^R 2\pi r^3\,dr = \frac{G\theta}{L}\cdot\frac{\pi R^4}{2}
$$

$$
\boxed{\frac{T}{J} = \frac{\tau}{r} = \frac{G\theta}{L}},\qquad J_{solid} = \frac{\pi R^4}{2} = \frac{\pi D^4}{32},\qquad J_{hollow} = \frac{\pi(R_o^4 - R_i^4)}{2}
$$

| Bending | Torsion |
|---|---|
| $M/I = \sigma/y = E/R$ | $T/J = \tau/r = G\theta/L$ |
| $I = \iint y^2\,dA$ | $J = \iint r^2\,dA = I_{yy} + I_{zz}$ |
| stiffness $EI$ | torsional stiffness $GJ/L$ |

Do not confuse $I$ and $J$: for a circle, $J = 2I$.

## 4. Hollow vs solid shafts (L13c)
Material near the axis carries little stress, so remove it. For the **same torque and maximum shear stress**, write $n = R_i/R_o$:

$$
\frac{J_s}{R_s} = \frac{J_h}{R_o}\;\Rightarrow\; R_s = R_o(1-n^4)^{1/3},\qquad \frac{W_h}{W_s} = \frac{1-n^2}{(1-n^4)^{2/3}}
$$

| $n$ | $R_o/R_s$ | $W_h/W_s$ |
|---|---|---|
| 0.5 | 1.02 | 0.78 |
| 0.9 | 1.43 | 0.39 (a 61% saving) |

The trade-off is mass against size, plus the risk of the thin wall buckling.

![[s1_torsion_hollow_vs_solid.png|880]]

> [!example] Tutorial 6 Q2: steel shaft inside an aluminium tube, $T = 3$ kNm, $D_o = 70$ mm, $\tau_{allow,Al} = 150$ MPa
> - Tube: $\tau_{max} = \dfrac{2TR_o}{\pi(R_o^4 - R_i^4)}$ gives $R_i = \left(R_o^4 - \dfrac{2TR_o}{\pi\tau}\right)^{1/4} = 32.0$ mm, so the bore is **64 mm**.
> - Steel shaft that just fits the bore: $\tau_{max} = \dfrac{2T}{\pi R_i^3} = $ **58 MPa**.

## 5. Power transmission (useful extension)
Shafts transmit power $P = T\omega = 2\pi NT/60$ ($N$ in rpm). The same power at higher speed needs less torque and so a thinner shaft, which is why gearboxes reduce speed at the output. This links to rotational work in [[FEEG1002 D9 - Work and Energy for Rigid Bodies]].

## Year 2 bridge
- [[SESA2028 S4 - Torsion of Thin-Walled Sections]] §1 restates the circular result, then leaves it behind:
  - **open** thin sections ([[Open-Section Torsion]], $J = \tfrac13\sum bt^3$) are very flexible;
  - **closed** single-cell sections ([[Bredt-Batho Torsion]], $q = T/2A$) are very stiff;
  - **multi-cell** wing boxes ([[Multi-Cell Torsion]]).
- The general theory for any section is [[Saint-Venant Torsion]], where circular shafts are the one case with no warping.
- Combined shear from torsion and transverse load leads to shear flow ([[SESA2028 S3 - Shear Flow and Shear Centre]]).
- Pure shear $\tau$ on the surface is equivalent to principal stresses $\pm\tau$ at 45°. That is why brittle shafts fail on a helix and ductile ones shear flat ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]).

## Links
- Previous: [[FEEG1002 A7 - Euler Buckling of Struts]] · Next: [[FEEG1002 A9 - Shear Stresses in Beams]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]

## Sources
- Statics 1 Lecture 13a–c (introduction; torsion equations; hollow vs solid example)

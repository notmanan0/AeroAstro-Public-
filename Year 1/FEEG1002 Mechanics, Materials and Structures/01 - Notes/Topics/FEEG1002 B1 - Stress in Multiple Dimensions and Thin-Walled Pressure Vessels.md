---
title: "FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 10
tags: [feeg1002, statics-2, stress-tensor, pressure-vessels, hoop-stress]
aliases: ["Statics 2 Lecture 1", "Stress element", "Hoop stress", "Thin-walled pressure vessel"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A9 - Shear Stresses in Beams]]"]
next_topics: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
key_concepts: ["[[Stress Tensor and Stress Element]]", "[[Thin-Walled Pressure Vessels]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf"]
---

# FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels

> [!abstract] Summary
> Statics 1 only ever needed **one** stress component at a time: $F/A$, $My/I$, $Tr/J$. Statics 2 deals with points where several components act at once.
> The state of stress at a point is a single object, described by a small **stress element**: three normal and three shear components in 3D. Moment equilibrium of the element gives $\sigma_{xy} = \sigma_{yx}$.
> The first application is the **thin-walled pressure vessel**. A cylinder carries hoop stress $pR/t$ and longitudinal stress $pR/2t$, so it splits lengthwise. A sphere carries $pR/2t$ in every direction.

## Key Concepts
- [[Stress Tensor and Stress Element]] · [[Thin-Walled Pressure Vessels]]

---

## 1. Statics 2 roadmap
1. Stress and strain in 2D/3D (B1, B2).
2. **Generalised Hooke's law**: linking all the stresses to all the strains (B3).
3. Stresses and strains on planes in other directions: **transformation and Mohr's circle** (B4).
4. **Strain gauges**: measuring deformation (B5).
5. **Failure criteria** in 2D/3D (B6).

## 2. Internal forces become stresses (L1a)
Cut a loaded solid. The exposed face carries a distributed internal force $d\mathbf F$ exerted by the material on the other side. Split it into a component **normal** to the cut (normal stress) and components **in the plane** of the cut (shear stresses). Both the size and the direction of these depend on **where** you cut and at **what orientation**.

## 3. The stress element (L1b)

![[s2_stress_element_notation.png|880]]

- Notation: $\sigma_{ij}$ is the stress in direction $j$ on a face whose normal points in $i$.
  - $\sigma_{xx}$ is a normal stress;
  - $\sigma_{yx}$ acts in $y$ on the $x$-face, so it is a shear stress.
- **Signs**: normal stress is positive in tension. Shear stress is positive when it points in $+x$ or $+y$ on a face with a positive outward normal, and so in the negative direction on the opposite face.
- **Equilibrium**:
  - force balance: opposite faces carry equal and opposite stresses;
  - moment balance about the centre: $\sigma_{xy} = \sigma_{yx}$ (complementary shear).
- **3D**: six independent components, $\sigma_{xx}, \sigma_{yy}, \sigma_{zz}$ and $\sigma_{xy}, \sigma_{xz}, \sigma_{yz}$. Together they form the stress tensor.
- **Non-uniform stress**: the element must balance stress *gradients*, e.g. $\partial\sigma_{xx}/\partial x + \partial\sigma_{xy}/\partial y = 0$. That is exactly how beam shear stress was derived in [[FEEG1002 A9 - Shear Stresses in Beams]].

> [!note] Index order varies between textbooks
> Some books swap the meaning of $\sigma_{xy}$ and $\sigma_{yx}$ or write $\tau_{xy}$. Because $\sigma_{xy} = \sigma_{yx}$, the numbers do not change, but read each source's figure first.

## 4. Thin-walled pressure vessels (L1c)
Orient the element with $x$ along the axis (**longitudinal** stress $\sigma_{xx}$) and $y$ around the circumference (**hoop** stress $\sigma_{yy}$). The load is axisymmetric, so there is **no shear** in this orientation.

**Hoop.** Cut along the length $L$. Pressure on the projected area $2RL$ is balanced by the two wall cuts $2tL$:

$$
p(2RL) = \sigma_{yy}(2tL)\;\Rightarrow\;\boxed{\sigma_{yy} = \frac{pR}{t}}
$$

**Longitudinal.** Cut across the axis. Pressure on the disc $\pi R^2$ is balanced by the wall annulus $2\pi Rt$:

$$
p\pi R^2 = \sigma_{xx}(2\pi Rt)\;\Rightarrow\;\boxed{\sigma_{xx} = \frac{pR}{2t}}
$$

**Sphere.** Every diametral cut looks the same, so $\sigma_{xx} = \sigma_{yy} = \dfrac{pR}{2t}$. That is **half** the cylinder's hoop stress for the same $R$ and $t$.

![[s2_pressure_vessel_stresses.png|940]]

| Point | Detail |
|---|---|
| Validity | $t/R < 0.1$. The radial stress, of order $p$, is then negligible |
| Which radius? | The inner/outer difference is small; using the outer radius is the conservative choice |
| End caps | Their shape does not affect $\sigma_{xx}$: only the projected area $\pi R^2$ matters |
| Failure | Hoop is the larger stress, so cylinders crack **along** their length (think of an overcooked sausage) |
| External pressure | Stresses are compressive: risk of **buckling** (submarines, vacuum tanks) |

> [!example] Tutorial 1: bolted spherical vessel ($D = 400$ mm, $t = 6$ mm, $\sigma_{allow} = 180$ MPa, 24 bolts of 18 mm)
> - $p_{max} = 2t\sigma/R = 10.8$ MPa.
> - Equilibrium of a hemisphere: $p\pi R^2 = 24F_{bolt}$, so $F_{bolt} = 56.5$ kN and $\sigma_{bolt} = 222$ MPa.

## Year 2 bridge
- **Thick walls.** When $t/R\gtrsim0.1$ the stresses vary through the wall. [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] solves this with the [[Lame Thick-Cylinder Solution]] $\sigma_r = A - B/r^2$, $\sigma_\theta = A + B/r^2$. Letting $t\to0$ recovers $\sigma_\theta = pR/t$.
- **Cylindrical-coordinate equilibrium**, $\frac{d\sigma_r}{dr} + \frac{\sigma_r - \sigma_\theta}{r} = 0$ ([[Axisymmetric Equilibrium]]), is the differential version of the "cut the vessel" free body used here ([[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]).
- **Rotating parts** (discs, rims) replace pressure with centrifugal body force: [[SESA2028 S11 - Spinning Discs]].
- **Aerospace uses**: the pressurised fuselage, where hoop stress drives cracking along the longitudinal lap joints (cabin-pressure fatigue in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]; multiple-site cracking in the Aloha lap joint in [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]), rocket propellant tanks ([[SESA2024 Astronautics Hub]]) and LH₂ tanks ([[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]).

## Links
- Previous: [[FEEG1002 A9 - Shear Stresses in Beams]] · Next: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]]

## Sources
- Statics 2 Lecture 1a–c (internal forces; stress elements; pressure vessels)

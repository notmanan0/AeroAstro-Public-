---
title: "Bredt-Batho Theory"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, torsion]
status: complete
parent: ["[[SESA2028 S4 - Torsion of Thin-Walled Sections]]"]
---

# Bredt-Batho Theory

**What it is:** the theory of torsion of **thin-walled closed** sections (single cell). This note derives it; [[Bredt-Batho Torsion]] shows how to use it.

## 1. Shear flow is constant round the cell

Cut a small element of wall between two sections $dx$ apart and two points $s_1,s_2$ on the wall. Pure torsion means no axial stress, so axial force equilibrium gives $\tau_1t_1\,dx=\tau_2t_2\,dx$. Hence

$$
q=\tau t=\text{constant around the cell},
$$

even when the thickness varies. **Stress is highest where the wall is thinnest.**

## 2. Torque from the shear flow

The force on an element $ds$ is $q\,ds$ along the wall. Its moment about any point O is $q\,p\,ds$, where $p$ is the perpendicular distance from O to the tangent. Now $p\,ds=2\,dA$ (twice the area of the thin triangle from O). So

$$
T=\oint qp\,ds=2qA_m\quad\Longrightarrow\quad\boxed{q=\frac{T}{2A_m}},
$$

where $A_m$ is the area enclosed by the **median line** of the wall, not the material area.

## 3. Twist rate from energy

The strain energy per unit length is $\oint\dfrac{\tau^2}{2G}t\,ds=\dfrac{q^2}{2}\oint\dfrac{ds}{Gt}$. Equating it to the work per unit length, $\tfrac12T\,\dfrac{d\phi}{dx}$:

$$
\frac{d\phi}{dx}=\frac{T}{4A_m^2}\oint\frac{ds}{Gt}\qquad\Longrightarrow\qquad
J=\frac{4A_m^2}{\oint ds/t}.
$$

## Consequences

- Stiffness ∝ $A_m^2$: **enclosed area is everything**. A closed tube is typically hundreds of times stiffer in torsion than the same wall slit open ([[Open-Section Torsion]]).
- Assumptions: thin walls, closed cell, no restraint of warping, shape of cross-section maintained (diaphragms), linear elastic.

![Open versus closed torsion](../Figures/structures_open_vs_closed_torsion.png)

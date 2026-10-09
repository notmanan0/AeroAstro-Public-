---
title: "SESA2028 S4 - Torsion of Thin-Walled Sections"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 4
tags: [sesa2028, structures, torsion, thin-walled]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
next_topics: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]"]
key_concepts: ["[[Saint-Venant Torsion]]", "[[Bredt-Batho Theory]]", "[[Multi-Cell Torsion]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 3 - Torsion Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL4 Torsion 1 - Circular sections and Closed sections under torsion.pdf", "02 - Sources/Structures Lectures/SL5 Torsion 2 - Torsion in closed sections.pdf", "02 - Sources/Structures Lectures/Structures Additional session_torsion.pdf"]
---

# SESA2028 S4 - Torsion of Thin-Walled Sections

> [!abstract] Summary
> Closed cells carry torque through a circulating shear flow and are extraordinarily efficient. Open walls resist through local plate twisting, so their torsional constant scales with $t^3$. Cutting one slit in a tube can therefore increase twist by two orders of magnitude.

## 1. Circular shafts

For Saint-Venant torsion,

$$
\tau(r)=\frac{Tr}{J},\qquad
\frac{d\phi}{dx}=\frac{T}{GJ}.
$$

For a solid circle $J=\pi R^4/2$; for an annulus $J=\pi(R_o^4-R_i^4)/2$.

## 2. Thin-walled open sections

For flat wall segments of length $b_i$ and thickness $t_i$,

$$
J_{open}\approx\sum_i\frac{b_it_i^3}{3}.
$$

The maximum wall stress on segment $i$ is approximated by

$$
\tau_{max,i}\approx\frac{Tt_i}{J},
$$

with corner corrections neglected by the thin-strip model. The $t^3$ dependence is the central result: doubling thickness increases open-section $J$ roughly eightfold.

## 3. Single-cell closed sections

Bredt-Batho theory gives constant shear flow around a single cell:

$$
T=2A_mq,\qquad q=\frac{T}{2A_m},\qquad \tau(s)=\frac{q}{t(s)}.
$$

The twist rate is

$$
\frac{d\phi}{dx}=\frac{1}{2A_mG}\oint\frac{q}{t}\,ds
=\frac{T}{4A_m^2G}\oint\frac{ds}{t},
$$

so

$$
J_{closed}=\frac{4A_m^2}{\displaystyle\oint ds/t}.
$$

Use the area enclosed by the wall median line, not the outer area.

![[Figures/structures_open_vs_closed_torsion.png]]

## 4. Multi-cell sections

Assign one constant cell flow $q_i$ to each cell. A common wall carries the algebraic difference $q_i-q_j$. Solve:

$$
T=2\sum_i A_iq_i
$$

together with equal twist in every cell:

$$
2A_iG\frac{d\phi}{dx}=\oint_i\frac{q_{wall}}{t}\,ds.
$$

There is one torque equation plus one compatibility equation for each independent twist comparison.

## 5. Design lessons

- Place material far from the centre and preserve a closed load path.
- In a variable-thickness cell, $q$ is constant but $\tau=q/t$ is largest in the thinnest wall.
- A shared spar wall in a wing box can carry the difference between large cell flows.
- A manufacturing slit may be structurally much more serious than its removed area suggests.

## 6. Exam workflow

1. Decide whether the section is circular, open, single-cell closed or multi-cell.
2. Draw median lines and list every $b_i,t_i$.
3. Calculate $J$ with the model appropriate to that topology.
4. Obtain twist from $T/(GJ)$.
5. Calculate wall stress and check the thinnest segment.
6. If a shear load is eccentric, superpose the [[Shear Flow]] due to bending and torque.

## Year 1 foundation
- [[FEEG1002 A8 - Torsion of Circular Shafts]]: $T/J = \tau/r = G\theta/L$ for circular shafts, the one case with no warping.

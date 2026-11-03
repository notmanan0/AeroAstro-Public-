---
title: "SESA2028 S4 - Torsion of Thin-Walled Sections"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 4
tags: [sesa2028, structures, torsion, thin-walled]
date: 2026-10-30
status: lectured
coverage: "Circular-shaft mini-lecture and SL11 (2026-03-11, 2026-03-13), SL12 (2026-03-18), tutorial 3 (2026-03-16/17), torsion recap at the start of SL13 (2026-04-22)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
next_topics: ["[[SESA2028 S5 - Euler Buckling and Effective Length]]"]
key_concepts: ["[[Saint-Venant Torsion]]", "[[Bredt-Batho Theory]]", "[[Open-Section Torsion]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 3 - Torsion Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL4 Torsion 1 - Circular sections and Closed sections under torsion.pdf", "02 - Sources/Structures Lectures/SL5 Torsion 2 - Torsion in closed sections.pdf", "02 - Sources/Structures Lectures/Structures Additional session_torsion.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-11 - mini_lecture Torsion circular.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-13.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-18.txt"]
---

# SESA2028 S4 - Torsion of Thin-Walled Sections

> [!abstract] Summary
> A closed thin-walled section carries torque by a constant shear flow round its wall, $q=T/2A_m$, and twists at $d\phi/dx=T/GJ$ with $J=4A_m^2/\oint ds/t$ (the Bredt–Batho result). An open section cannot circulate shear flow round a loop, so each wall carries torque by shear stress varying linearly through its thickness, giving $J=\sum bt^3/3$ and $\tau_{max}=Tt_{max}/J$. Because $J$ then scales with $t^3$ instead of with enclosed area, cutting one slit along a thin tube with $R/t=10$ makes it 300 times more flexible in torsion.

> [!summary]- Exam use: quick path
> - **Use it when:** a closed tube, box or aerofoil cell, or an open angle, channel or slit tube, carries a torque.
> - **Assumptions:** thin walls ($t$ about a tenth of other dimensions or less), constant cross-section along the length, end or distributed torques only, ends free to warp, linear elastic.
> - **Method:** 1. Closed or open? 2. Closed: $A_m$ from the wall midline, $\tau_{max}=T/(2A_mt_{min})$, $J=4A_m^2/\oint ds/t$. 3. Open: $J=\sum b_it_i^3/3$, $\tau_{max}=Tt_{max}/J$. 4. $\phi=TL/GJ$. 5. Off-centre loads: move to the shear centre, add the torque, superpose.
> - **Common mistakes:** using the outer instead of the midline area; using $t_{max}$ for a closed section (it is $t_{min}$ that governs).
> - **Practise:** [[#A closed box and the same box with a slit]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q4 - Closed tube versus the same tube with a slit|Tutorial 3 Q4]]

Torsion arises whenever a shear load misses the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]) or a torque is applied directly, as in wings, fuselages, struts and drive shafts (2026-03-13, ll. 1–40). The course analyses arbitrary thin-walled sections rather than the solid circular shafts of statics; design comes in later years.

Compare a cardboard tube with the same tube slit along its length. The intact tube is stiff in torsion because shear flows all the way round it, and the flow at the far side of the tube has a long lever arm about the axis: the enclosed area does the work. Slit the tube and that circulation is broken at the cut; the only way left to resist torque is a tiny circulation within the wall thickness itself, up one face of the wall and back down the other, whose lever arm is only the wall thickness. The slit tube twists like a sheet of paper.

## 1. The circular shaft (review)

A mini-lecture video recaps the statics result for a circular shaft under torque $T$ (2026-03-11 mini-lecture; 2026-03-13, ll. 81–120):

$$
\tau=\frac{Tr}{J},
\qquad
\frac{d\phi}{dx}=\frac{T}{GJ},
\qquad
\phi=\frac{TL}{GJ},
\qquad
J=\frac{\pi R^4}{2}\ \text{(solid)},\quad J=\frac\pi2\left(R_e^4-R_i^4\right)\ \text{(hollow)}.
$$

Failure starts at the surface, where $r=R$, and torsion alone produces shear stress but no normal stress. The opening poll asked about a door handle of two circular bars fixed at A and loaded at B: the bar carrying the load bends, and the bar it is attached to both bends and twists, plus, as one student added, a small shear deformation usually neglected (2026-03-13, ll. 1–80).

## 2. Closed sections: constant shear flow

The assumptions are a section constant along the length, closed, with thickness that may vary round the wall but stays small compared with the other dimensions, so that the shear stress is uniform through the thickness; loading by end or distributed torques; and ends free to warp (ll. 161–190).

Take a wall element $dx$ by $ds$. With only shear stresses acting (no bending stress), force equilibrium in $x$ and $s$ gives

$$
\frac{\partial q}{\partial s}=0,
\qquad
\frac{\partial q}{\partial x}=0,
$$

so the shear flow is the same everywhere round the section (ll. 190–240). Under bending shear it varied ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]) because the changing bending stress $\partial\sigma_{xx}/\partial x$ fed the wall, as a student identified when asked. With constant thickness all points reach the same shear stress; with varying thickness the thinnest wall is worst.

The torque of the flow on an element $ds$ at perpendicular distance $p$ from any point O is $dT=pq\,ds$ (ll. 241–280). The triangle from O to the element has area $dA=\tfrac12p\,ds$, so

$$
T=\oint pq\,ds=q\oint p\,ds=2qA_m,
$$

where $A_m$ is the area enclosed by the midline of the wall. Hence

$$
q=\frac{T}{2A_m},
\qquad
\tau=\frac{T}{2A_mt},
\qquad
\tau_{max}=\frac{T_{max}}{2A_mt_{min}} .
$$

For the twist, the shear strain of the wall has an in-plane twisting part and an out-of-plane warping part (ll. 281–320):

$$
\gamma=\gamma_t+\gamma_w=p\frac{d\phi}{dx}+\frac{\partial u}{\partial s}.
$$

With $\gamma=\tau/G=T/(2A_mGt)$,

$$
\frac{T}{2A_mGt}=p\frac{d\phi}{dx}+\frac{\partial u}{\partial s}.
$$

Integrate round the closed wall. The warping term integrates to zero, because the axial displacement $u$ must return to its starting value after one circuit (continuity), and $\oint p\,ds=2A_m$ (ll. 321–360):

$$
\frac{T}{2A_mG}\oint\frac{ds}{t}=2A_m\frac{d\phi}{dx}
\quad\Longrightarrow\quad
\frac{d\phi}{dx}=\frac{T}{GJ},
\qquad
J=\frac{4A_m^2}{\oint ds/t}.
$$

The form $T/GJ$ is the same as for a circular shaft; only $J$ changes ([[Bredt-Batho Theory]]). For a constant thickness, $\oint ds/t$ is simply the perimeter over $t$; for a thin circular tube, $A_m=\pi R^2$ and $\oint ds/t=2\pi R/t$, so $J=2\pi R^3t$, which matches $\frac\pi2(R_e^4-R_i^4)$ for thin walls.

## 3. Open sections: rectangular strips

An open section has free edges where the shear flow must be zero, so it cannot circulate round the section (2026-03-18, ll. 1–90). Consider a thin rectangular strip of width $b$ and thickness $t\ll b$ (about a tenth or less). Its shear stress is no longer uniform through the thickness but varies linearly, zero at the mid-plane and maximum at the faces, running in opposite directions on the two faces so that it forms closed loops inside the strip (ll. 60–150). The section uses its whole thickness this way, putting the most stress where the lever arm is longest.

Treat each loop as a thin closed section. The loop at distance $y$ from the mid-plane, of thickness $dy$, encloses $A_m\approx2yb$ and carries stress $\tau(y)=\tau_{max}\,2y/t$ (ll. 150–180). As a closed section it resists

$$
dT=2A_m\tau\,dy=2(2yb)\,\tau_{max}\frac{2y}{t}\,dy .
$$

Integrate from 0 to $t/2$ (each loop already covers both faces):

$$
T=\frac{8b\tau_{max}}{t}\int_0^{t/2}y^2\,dy=\frac{8b\tau_{max}}{t}\cdot\frac{t^3}{24}=\frac{\tau_{max}}{t}\cdot\frac{bt^3}{3}.
$$

So, with $J=bt^3/3$,

$$
\tau_{max}=\frac{Tt}{J},
\qquad
\tau(y)=\frac{2Ty}{J}.
$$

For the twist, apply the closed-section result to each loop (ll. 210–270). For the loop at $y$, with $\oint ds\approx2b$ and $A_m=2yb$, the rate of twist gives $\tau(y)=2Gy\,d\phi/dx$; substituting into the torque integral gives

$$
\frac{d\phi}{dx}=\frac{T}{GJ},
\qquad
J=\frac{bt^3}{3},
$$

the same form again. A built-up open section (angle, T, channel, I) or a thin curved one (a slit tube, unrolled to its developed length) is an assembly of strips, all twisting through the same angle (ll. 270–300):

$$
J=\sum_i\frac{b_it_i^3}{3},
\qquad
\tau_{max}=\frac{Tt_{max}}{J},
\qquad
\phi=\frac{TL}{GJ}.
$$

For strips that are not very thin, the $\tfrac13$ is replaced by tabulated coefficients $\alpha$ and $\beta$ that depend on $b/t$, different for stress and twist ([[Open-Section Torsion]]; ll. 290–300).

## 4. Open against closed

For a thin tube of radius $R$ and thickness $t$ (2026-03-18, ll. 300–330),

$$
J_{closed}=2\pi R^3t,
\qquad
J_{open}=\frac{2\pi Rt^3}{3},
\qquad
\frac{\phi_{open}}{\phi_{closed}}=\frac{J_{closed}}{J_{open}}=3\left(\frac Rt\right)^2 .
$$

With $R/t=10$ the slit tube twists 300 times more, the answer to the lecture's opening poll. A slit cut through a closed aircraft section to pass a cable "will completely ruin the capability of carrying torsion".

Real members carry bending, shear and torsion together, about several axes. For linear elastic, small-deformation behaviour the stresses from each superpose at every point, and the critical point is found by combining the normal and shear stresses there (ll. 360–420). Superposition fails for material nonlinearity (plasticity, damage, cracks) or geometric nonlinearity (large deformation); Castigliano's theorem likewise relies on linearity ([[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]). The closing question, an angle loaded off its shear centre at the junction, combines bending at the root, bending shear and torsion shear in exactly this way.

## Worked examples

### A light-alloy strut

The SL11 example (2026-03-13, ll. 361–400; slide 27): a stabilising strut of a high-wing monoplane, 2 m long, has a section of two semicircular ends of radius 25 mm (wall 3 mm) joined by flat walls 50 mm long (wall 2 mm). Find the torque for $\tau_{max}=28$ MPa and the twist, with $G=27$ GPa.

The midline area and the thinnest wall:

$$
A_m=\pi\times25^2+50\times50=4463\text{ mm}^2,
\qquad
t_{min}=2\text{ mm}.
$$

$$
T=2A_mt_{min}\tau_{max}=2\times4463\times2\times28=5.00\times10^5\text{ N mm}=500\text{ N m}.
$$

Round the wall,

$$
\oint\frac{ds}{t}=\frac{2\times50}{2}+\frac{2\pi\times25}{3}=102.4,
\qquad
J=\frac{4A_m^2}{102.4}=7.79\times10^5\text{ mm}^4,
$$

$$
\phi=\frac{TL}{GJ}=\frac{5.00\times10^5\times2000}{27\,000\times7.79\times10^5}=0.0476\text{ rad}=2.7°.
$$

### Three strips

SL12 example 1 (2026-03-18, ll. 330–345; SL5 slide 22): an open section of three 3 mm strips, 40, 100 and 80 mm long, carries 30 N m; steel, $G=79$ GPa, 1 m long.

$$
J=\frac{(40+100+80)\times3^3}{3}=1980\text{ mm}^4,
\qquad
\tau_{max}=\frac{30\,000\times3}{1980}=45.5\text{ MPa},
$$

$$
\phi=\frac{30\,000\times1000}{79\,000\times1980}=0.192\text{ rad}=11.0°.
$$

### A closed box and the same box with a slit

SL12 example 2 (ll. 345–360; SL5 slide 23): a 35 × 75 mm rectangular tube, 2 mm thick, steel ($G=79$ GPa), carries 50 N m, first closed, then with a slit at one corner.

Closed: $A_m=35\times75=2625$ mm² and $\oint ds/t=2(35+75)/2=110$.

$$
\tau_{max}=\frac{50\,000}{2\times2625\times2}=4.76\text{ MPa},
\qquad
J=\frac{4\times2625^2}{110}=2.51\times10^5\text{ mm}^4,
\qquad
\frac{d\phi}{dx}=\frac{T}{GJ}=2.53\times10^{-3}\text{ rad/m}.
$$

Open: the developed length is 220 mm.

$$
J=\frac{220\times2^3}{3}=587\text{ mm}^4,
\qquad
\tau_{max}=\frac{50\,000\times2}{587}=170\text{ MPa},
\qquad
\frac{d\phi}{dx}=1.08\text{ rad/m}.
$$

The slit multiplies the stress by 36 and the twist by 427, all recomputed in Python.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S3 - Shear Flow and Shear Centre]]
- Next: [[SESA2028 S5 - Euler Buckling and Effective Length]]
- Concepts: [[Saint-Venant Torsion]] · [[Bredt-Batho Theory]] · [[Bredt-Batho Torsion]] · [[Open-Section Torsion]] · [[Multi-Cell Torsion]]
- Year 1 foundation: circular-shaft torsion in statics

![[structures_open_vs_closed_torsion.png|720]]

## Sources

- Structures slides `SL4 Torsion 1`, `SL5 Torsion 2` and `Structures Additional session_torsion.pdf`, with transcripts of the circular-torsion mini-lecture, `SESA2028 Lecture 2026-03-13.txt` (SL11) and `SESA2028 Lecture 2026-03-18.txt` (SL12); multi-cell sections were not lectured in 2025–26
- Worked examples recomputed in Python

## Self-study tasks

### Core

- [ ] Prove the shear flow is constant in a closed section under pure torque and derive $T=2qA_m$ and $J=4A_m^2/\oint ds/t$ (2026-03-13, ll. 190–360). → [[#2. Closed sections: constant shear flow]]
- [ ] The light-alloy strut ("have a go first", slide 27; ll. 361–400). → [[#A light-alloy strut]]
- [ ] Derive $J=bt^3/3$ for a thin strip and the 300:1 slit-tube ratio (2026-03-18, ll. 150–330). → [[#3. Open sections: rectangular strips]] · [[#4. Open against closed]]
- [ ] The three-strip section and the box with and without a slit (ll. 330–360). → [[#Three strips]] · [[#A closed box and the same box with a slit]]
- [ ] Structures tutorial 3, closed and open sections ("try to solve all the problems related to closed cross section", 2026-03-13, ll. 401–410). → [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q1 - Symmetric closed hexagon|Q1]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q3 - Open cruciform|Q3]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q6 - Eccentrically loaded L-section|Q6]]

### Further practice

- [ ] Find the critical point of the off-centre-loaded angle by superposing bending, bending shear and torsion (closing question, ll. 420–427). → [[#4. Open against closed]]

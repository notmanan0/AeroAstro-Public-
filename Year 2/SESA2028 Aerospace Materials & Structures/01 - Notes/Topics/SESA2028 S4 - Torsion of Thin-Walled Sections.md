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
> A closed thin-walled section carries torque by a constant shear flow round its wall, $q=T/2A_m$, and twists at $d\phi/dx=T/GJ$ with $J=4A_m^2/\oint ds/t$ (the Bredt–Batho result). An open section cannot circulate shear flow round a loop, so each wall carries torque by a shear stress varying linearly through its thickness, giving $J=\sum bt^3/3$ and $\tau_{max}=Tt_{max}/J$. Because $J$ then scales with $t^3$ instead of with the enclosed area, one slit along a thin tube with $R/t=10$ makes it 300 times more flexible in torsion.

> [!summary]- Exam use: quick path
> - **Use it when:** a closed tube, box or aerofoil cell, or an open angle, channel or slit tube, carries a torque, including the torque from a shear load that misses the shear centre.
> - **Assumptions:** thin walls ($t$ about a tenth of other dimensions or less), constant cross-section along the length, end or distributed torques only, ends free to warp, linear elastic.
> - **Method:** 1. Closed or open? 2. Closed: $A_m$ from the wall midline, $\tau_{max}=T/(2A_mt_{min})$, $J=4A_m^2/\oint ds/t$. 3. Open: $J=\sum b_it_i^3/3$, $\tau_{max}=Tt_{max}/J$. 4. $\phi=TL/GJ$. 5. Off-centre loads: move to the shear centre, add the torque, superpose.
> - **Common mistakes:** using the outer instead of the midline area; using $t_{max}$ for a closed section, where it is $t_{min}$ that governs.
> - **Practise:** [[#A closed box and the same box with a slit]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q4 - Closed tube versus the same tube with a slit|Tutorial 3 Q4]]

Torsion arises whenever a shear load misses the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]) or a torque is applied directly, as in wings, fuselages, struts and drive shafts. The solid circular shaft is the familiar case; thin-walled shapes, open or closed, carry torque in quite different ways.

A cardboard tube and the same tube slit along its length differ greatly in torsion. The intact tube is stiff in torsion because shear flows all the way round it, and the flow on the far side of the tube has a long lever arm about the axis: the enclosed area does the work. With the tube slit, that circulation is broken at the cut. The only way left to resist torque is a small circulation within the wall thickness itself, along one face of the wall and back along the other, whose lever arm is only the wall thickness. The slit tube twists like a sheet of paper.

## 1. The circular shaft (review)

For a circular shaft under a torque $T$, plane sections stay plane and radii stay straight, so the shear strain grows linearly with radius, $\gamma=r\,d\phi/dx$, and with $\tau=G\gamma$ the stress does too. The torque is the moment of that stress, $T=\int_A\tau r\,dA=G\frac{d\phi}{dx}\int_Ar^2\,dA=GJ\frac{d\phi}{dx}$, which gives

$$
\tau=\frac{Tr}{J},\qquad\frac{d\phi}{dx}=\frac{T}{GJ},\qquad\phi=\frac{TL}{GJ},
$$

with

$$
J=\frac{\pi R^4}{2}\ \text{(solid)},\qquad J=\frac\pi2\left(R_e^4-R_i^4\right)\ \text{(hollow)}.
$$

Failure starts at the surface, $r=R$, and torsion alone produces shear stress but no normal stress. Real members rarely carry torsion alone: a door handle of two circular bars, fixed at one end and loaded at the other, has the loaded bar bending while the bar it joins both bends and twists, with a small transverse shear deformation usually neglected.

## 2. Closed sections: constant shear flow

The assumptions are a closed section constant along the length, with a thickness that may vary round the wall but stays small compared with the other dimensions, so that the shear stress is uniform through the thickness; loading by end or distributed torques; and ends free to warp.

![[structures_s4_closed_and_open_setup.png|900]]

### The shear flow is constant

A wall element $dx$ long along the beam and $ds$ long round the wall carries no bending stress under pure torque, so only shear flows act on its edges: $q$ on the edges of length $dx$ and, by complementary shear, the same $q$ on the edges of length $ds$. Force equilibrium along $x$ involves the flows on the two $dx$ edges:

$$
\left(q+\frac{\partial q}{\partial s}ds\right)dx-q\,dx=0\quad\Longrightarrow\quad\frac{\partial q}{\partial s}=0 .
$$

Equilibrium along $s$ involves the flows on the two $ds$ edges in the same way, in a segment with no distributed torque, so that $T$ is constant:

$$
\left(q+\frac{\partial q}{\partial x}dx\right)ds-q\,ds=0\quad\Longrightarrow\quad\frac{\partial q}{\partial x}=0 .
$$

So the shear flow is the same everywhere round the section, and along the member too while the torque is constant. A distributed torque makes $T(x)$ vary, and $q$ with it, although $q$ stays constant round any one section. Under bending shear it varied ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]) because the changing bending stress $\partial\sigma_{xx}/\partial x$ fed the wall; with no bending stress there is nothing to change it. With a constant thickness every point reaches the same shear stress; with a varying thickness the thinnest wall is worst.

### Torque and shear flow

The force on an element of wall is $q\,ds$, along the wall. Its moment about any point O is $q\,ds$ times the perpendicular distance $p$ from O to the element's line of action:

$$
dT=p\,q\,ds .
$$

The triangle from O to the two ends of the element has base $ds$ and height $p$, so its area is $dA=\tfrac12p\,ds$, or $p\,ds=2\,dA$. Going once round the wall, the triangles fill the area enclosed by the midline, $A_m$. With $q$ constant:

$$
T=\oint p\,q\,ds=q\oint p\,ds=2qA_m .
$$

Hence

$$
\boxed{q=\frac{T}{2A_m},\qquad\tau=\frac{T}{2A_mt},\qquad\tau_{max}=\frac{T}{2A_mt_{min}}}
$$

The point O does not matter, as it should not for a pure couple.

### Rate of twist

The shear strain of the wall has an in-plane twisting part and an out-of-plane warping part. If the section rotates by $d\phi$ over a length $dx$, a point at perpendicular distance $p$ from the centre of twist moves $p\,d\phi$ along the wall, giving a strain $p\,d\phi/dx$; the axial (warping) displacement $u$ varying round the wall adds $\partial u/\partial s$:

$$
\gamma=\gamma_t+\gamma_w=p\frac{d\phi}{dx}+\frac{\partial u}{\partial s}.
$$

Hooke's law in shear gives $\gamma=\tau/G=q/Gt=T/(2A_mGt)$, so

$$
\frac{T}{2A_mGt}=p\frac{d\phi}{dx}+\frac{\partial u}{\partial s}.
$$

Integrate once round the closed wall:

$$
\frac{T}{2A_mG}\oint\frac{ds}{t}=\frac{d\phi}{dx}\oint p\,ds+\oint\frac{\partial u}{\partial s}\,ds .
$$

The last term is the change in $u$ over one circuit, which is zero because the wall is continuous and $u$ must return to its starting value. The middle integral is $2A_m$. So

$$
\frac{T}{2A_mG}\oint\frac{ds}{t}=2A_m\frac{d\phi}{dx}.
$$

Solve for the rate of twist:

$$
\frac{d\phi}{dx}=\frac{T}{4A_m^2G}\oint\frac{ds}{t}=\frac{T}{GJ},\qquad\boxed{J=\frac{4A_m^2}{\oint ds/t}}
$$

The form $T/GJ$ is the same as for a circular shaft; only $J$ changes ([[Bredt-Batho Theory]]). For a constant thickness, $\oint ds/t$ is just the midline perimeter divided by $t$.

> [!check] The thin circular tube
> For a tube of mean radius $R$ and thickness $t$, $A_m=\pi R^2$ and $\oint ds/t=2\pi R/t$, so $J=4\pi^2R^4t/2\pi R=2\pi R^3t$. With $R=50$ mm and $t=2$ mm this is $1.571\times10^6$ mm⁴, against the exact $\frac\pi2(51^4-49^4)=1.571\times10^6$ mm⁴: they differ by 0.04 %.

## 3. Open sections: rectangular strips

An open section has free edges where the shear flow must be zero, so it cannot circulate round the section. Consider a thin rectangular strip of width $b$ and thickness $t\ll b$ (about a tenth or less). Its shear stress is no longer uniform through the thickness but varies linearly, zero at the mid-plane and largest at the faces, running in opposite directions on the two faces so that it forms closed loops inside the strip. The strip uses its whole thickness this way, putting the most stress where the lever arm is longest.

### Torque in terms of the maximum stress

Treat each loop as a thin closed section. The loop at distance $y$ from the mid-plane, of thickness $dy$, encloses $A_m\approx2yb$ (the short ends are neglected because $t\ll b$) and carries the stress

$$
\tau(y)=\tau_{max}\frac{y}{t/2}=\tau_{max}\frac{2y}{t}.
$$

By the closed-section result $T=2qA_m$, a closed loop with shear flow $\tau\,dy$ resists a torque

$$
dT=2A_m\,\tau\,dy=2(2yb)\,\tau_{max}\frac{2y}{t}\,dy=\frac{8b\,\tau_{max}}{t}y^2\,dy .
$$

Integrate over the loops from the mid-plane to the face; each loop already covers both faces:

$$
T=\frac{8b\tau_{max}}{t}\int_0^{t/2}y^2\,dy=\frac{8b\tau_{max}}{t}\cdot\frac{t^3}{24}=\frac{\tau_{max}}{t}\cdot\frac{bt^3}{3}.
$$

So, with $J=bt^3/3$,

$$
\tau_{max}=\frac{Tt}{J},\qquad\tau(y)=\frac{2Ty}{J}.
$$

### Rate of twist of a strip

Apply the closed-section twist result to the loop at $y$. Its shear flow is $\tau(y)\,dy$, its wall thickness is $dy$, and its perimeter is $\oint ds\approx2b$:

$$
\frac{d\phi}{dx}=\frac{q_{loop}}{2A_mG}\oint\frac{ds}{t_{loop}}=\frac{\tau(y)\,dy}{2(2yb)G}\cdot\frac{2b}{dy}=\frac{\tau(y)}{2Gy}.
$$

Every loop twists through the same angle, so

$$
\tau(y)=2Gy\frac{d\phi}{dx},
$$

which confirms the linear profile. Put this into the torque integral:

$$
T=\int_0^{t/2}2(2yb)\left(2Gy\frac{d\phi}{dx}\right)dy=8bG\frac{d\phi}{dx}\cdot\frac{t^3}{24}=G\frac{d\phi}{dx}\cdot\frac{bt^3}{3}.
$$

Therefore

$$
\frac{d\phi}{dx}=\frac{T}{GJ},\qquad J=\frac{bt^3}{3},
$$

the same form again, and at the face $\tau_{max}=2G(t/2)\,d\phi/dx=Tt/J$ as before.

### Built-up open sections

A built-up open section (angle, T, channel, I) or a thin curved one (a slit tube, unrolled to its developed length) is an assembly of strips, all twisting through the same angle. The torques of the strips add, each strip carrying $T_i=GJ_i\,d\phi/dx$, so

$$
J=\sum_i\frac{b_it_i^3}{3},\qquad\tau_{max}=\frac{Tt_{max}}{J},\qquad\phi=\frac{TL}{GJ}.
$$

The thickest wall carries the highest stress. For strips that are not very thin, the $\tfrac13$ is replaced by tabulated coefficients $\alpha$ and $\beta$ that depend on $b/t$, different for stress and twist ([[Open-Section Torsion]]).

## 4. Open against closed

For a thin tube of mean radius $R$ and thickness $t$, closed and then slit along its length,

$$
J_{closed}=2\pi R^3t,\qquad J_{open}=\frac{(2\pi R)\,t^3}{3}.
$$

The twist under the same torque goes as $1/J$:

$$
\frac{\phi_{open}}{\phi_{closed}}=\frac{J_{closed}}{J_{open}}=\frac{2\pi R^3t}{2\pi Rt^3/3}=3\left(\frac Rt\right)^2 .
$$

With $R/t=10$ the slit tube twists 300 times more. The stresses compare as

$$
\frac{\tau_{open}}{\tau_{closed}}=\frac{Tt/J_{open}}{T/(2\pi R^2t)}=\frac{3T/(2\pi Rt^2)}{T/(2\pi R^2t)}=3\frac Rt,
$$

30 times more at $R/t=10$. A slit cut through a closed aircraft section to pass a cable destroys its torsional capability.

![[structures_open_vs_closed_torsion.png|640]]

Real members carry bending, shear and torsion together, about several axes. For linear elastic, small-deformation behaviour the stresses from each superpose at every point, and the critical point is found by combining the normal and shear stresses there. Superposition fails for material nonlinearity (plasticity, damage, cracks) and for geometric nonlinearity (large deformation); Castigliano's theorem relies on linearity in the same way ([[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]). An angle loaded at its free end off the shear centre, which sits at the junction of the legs, combines bending stress at the root, bending shear and torsion shear in exactly this way.

## Worked examples

### A light-alloy strut

A stabilising strut of a high-wing monoplane is 2 m long. Its section has two semicircular ends of radius 25 mm (wall 3 mm thick) joined by two flat walls 50 mm long (wall 2 mm thick), all dimensions to the midline. Find the torque for a maximum shear stress of 28 MPa and the twist of the strut, with $G=27$ GPa.

The midline encloses a circle (the two semicircles) and a 50 × 50 mm rectangle:

$$
A_m=\pi\times25^2+50\times50=1963+2500=4463\text{ mm}^2 .
$$

The shear flow is constant, so the thinnest wall, $t_{min}=2$ mm, has the highest stress. Rearranging $\tau_{max}=T/2A_mt_{min}$:

$$
T=2A_mt_{min}\tau_{max}=2\times4463\times2\times28=5.00\times10^5\text{ N mm}=500\text{ N m}.
$$

Round the wall, the flat walls and the semicircles contribute

$$
\oint\frac{ds}{t}=\frac{2\times50}{2}+\frac{2\pi\times25}{3}=50+52.4=102.4 .
$$

So

$$
J=\frac{4A_m^2}{\oint ds/t}=\frac{4\times4463^2}{102.4}=7.78\times10^5\text{ mm}^4,
$$

and

$$
\phi=\frac{TL}{GJ}=\frac{5.00\times10^5\times2000}{27\,000\times7.78\times10^5}=0.0476\text{ rad}=2.7° .
$$

> [!check] Stress in the thicker walls
> The same $q=T/2A_m=56$ N/mm runs through the 3 mm semicircles, giving 18.7 MPa there: two thirds of the flat-wall value, in the ratio of the thicknesses.

### Three strips

An open section of three 3 mm thick strips, 40, 100 and 80 mm long, carries 30 N m; it is steel, $G=79$ GPa, and 1 m long.

$$
J=\frac{(40+100+80)\times3^3}{3}=1980\text{ mm}^4 .
$$

$$
\tau_{max}=\frac{Tt}{J}=\frac{30\,000\times3}{1980}=45.5\text{ MPa}.
$$

$$
\phi=\frac{TL}{GJ}=\frac{30\,000\times1000}{79\,000\times1980}=0.192\text{ rad}=11.0° .
$$

### A closed box and the same box with a slit

A 35 × 75 mm rectangular tube (midline dimensions), 2 mm thick, in steel ($G=79$ GPa), carries 50 N m, first closed, then with a slit along one corner.

Closed: $A_m=35\times75=2625$ mm² and $\oint ds/t=2(35+75)/2=110$.

$$
\tau_{max}=\frac{T}{2A_mt}=\frac{50\,000}{2\times2625\times2}=4.76\text{ MPa},
$$

$$
J=\frac{4\times2625^2}{110}=2.51\times10^5\text{ mm}^4,\qquad\frac{d\phi}{dx}=\frac{T}{GJ}=\frac{50\,000}{79\,000\times2.51\times10^5}=2.53\times10^{-6}\text{ rad/mm}=2.53\times10^{-3}\text{ rad/m}.
$$

Open: the developed length of the wall is $2(35+75)=220$ mm.

$$
J=\frac{220\times2^3}{3}=587\text{ mm}^4,\qquad\tau_{max}=\frac{50\,000\times2}{587}=170\text{ MPa},\qquad\frac{d\phi}{dx}=\frac{50\,000}{79\,000\times587}=1.08\text{ rad/m}.
$$

The slit multiplies the stress by 36 and the twist by 427.

> [!check] Against the tube formulae
> If the box behaved like a circular tube, $J_{closed}/J_{open}=3(R/t)^2=427$ would give an equivalent radius $R=2\sqrt{427/3}=23.9$ mm. The tube's stress ratio $3R/t$ with that radius is $3\times23.9/2=35.8$, which matches the direct $170/4.76=36$: the two ratios are linked by the same geometry whatever the shape of the cell.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S3 - Shear Flow and Shear Centre]] · Next: [[SESA2028 S5 - Euler Buckling and Effective Length]]
- Concepts: [[Saint-Venant Torsion]] · [[Bredt-Batho Theory]] · [[Bredt-Batho Torsion]] · [[Open-Section Torsion]] · [[Multi-Cell Torsion]]
- Problems: [[SESA2028 Structures Tutorial 3 - Torsion Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Torsion strain energy: [[SESA2028 S7 - Strain Energy and Conservation of Energy#Torsion of a circular shaft|S7]]

## Sources

- Slides: `SL4 Torsion 1 - Circular sections and Closed sections under torsion.pdf` (closed-section derivation, the strut on slide 27), `SL5 Torsion 2 - Torsion in closed sections.pdf` (open sections, examples on slides 22–23) and `Structures Additional session_torsion.pdf`.
- Transcripts: the circular-torsion mini-lecture (`SESA2028 Lecture 2026-03-11 - mini_lecture Torsion circular.txt`), `SESA2028 Lecture 2026-03-13.txt` (SL11, closed sections) and `SESA2028 Lecture 2026-03-18.txt` (SL12, open sections); tutorial 3 recordings of 2026-03-16/17. Multi-cell sections were not lectured in 2025–26.
- All worked examples recomputed in Python. Figures: `generate_structures_s4_figures.py` (derivation set-up) and `generate_structures_figures.py` (open against closed, tutorial 3 Q4 ratios).

## Self-study tasks

### Core

- [ ] Prove the shear flow is constant in a closed section under pure torque and derive $T=2qA_m$ and $J=4A_m^2/\oint ds/t$ (2026-03-13, ll. 190–360). → [[#2. Closed sections: constant shear flow]]
- [ ] The light-alloy strut, "have a go first" on SL4 slide 27 (2026-03-13, ll. 361–400). → [[#A light-alloy strut]]
- [ ] Derive $J=bt^3/3$ for a thin strip and the 300:1 slit-tube ratio (2026-03-18, ll. 150–330). → [[#3. Open sections: rectangular strips]] · [[#4. Open against closed]]
- [ ] The three-strip section and the box with and without a slit, SL5 slides 22–23 (2026-03-18, ll. 330–360). → [[#Three strips]] · [[#A closed box and the same box with a slit]]
- [ ] Structures tutorial 3: all the closed-section problems were set after SL11 (2026-03-13, ll. 401–410), the open ones after SL12. → [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q1 - Symmetric closed hexagon|Q1]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q3 - Open cruciform|Q3]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q6 - Eccentrically loaded L-section|Q6]]

### Further practice

- [ ] Find the critical point of the off-centre-loaded angle by superposing bending, bending shear and torsion (closing question, 2026-03-18, ll. 420–427). → [[#4. Open against closed]] · [[SESA2028 Structures Tutorial 3 - Torsion Solutions#Q6 - Eccentrically loaded L-section|Tutorial 3 Q6]]
- [ ] Check the thin-tube $J=2\pi R^3t$ against the exact hollow-shaft $J$ for $R/t=5$ and $R/t=25$ (suggested, not lecturer-set). → [[#Rate of twist]]

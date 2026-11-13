---
title: "SESA2028 S10 - Thick Cylinders and Shrink Fits"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 10
tags: [sesa2028, structures, thick-cylinder, shrink-fit, pressure-vessel]
date: 2026-10-30
status: lectured
coverage: "SL16 part 2 (2026-05-06), SL17 (2026-05-08), continuum tutorial (2026-05-11), revision SL18 (2026-05-13)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
next_topics: ["[[SESA2028 S11 - Spinning Discs]]"]
key_concepts: ["[[Lame Thick-Cylinder Solution]]", "[[Shrink Fit]]", "[[Shrink Fit Superposition]]", "[[Compound Cylinder]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL22 - Continuum Mechanics 4 - Thick Walled Cylinders.pdf", "02 - Sources/Structures Lectures/SL23 - Continuum Mechanics 5 - Shrink Fit Assembly.pdf", "02 - Sources/Structures Lectures/Structures Additional session - thick wall cylinders.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-06 - SL16 (Part 2) Continuum mechanics.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-08.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-11.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-13.txt", "03 - Exams & Past Papers/FEEG2005-202425-02-FEEG2005.pdf"]
---

# SESA2028 S10 - Thick Cylinders and Shrink Fits

> [!abstract] Summary
> The Lamé solution $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$ with the pressure boundary conditions gives the radial and hoop stresses through a thick cylinder; the axial stress depends on how the ends are held (capped, free like a piston, or built in). The hoop stress peaks at the bore, so the outer material is under-used and yield (Tresca or von Mises) starts at the bore. A shrink fit, an outer tube heated and slipped over an inner one, puts the bore into residual compression and evens out the hoop stress; it is analysed with two Lamé solutions, four constants, and an interference condition converted from displacement to strain to stress.

> [!summary]- Exam use: quick path
> - **Use it when:** a thick tube, pressure vessel, jack cylinder, shaft-and-bush or compound cylinder carries pressure.
> - **Assumptions:** linear elastic, isotropic, axisymmetric; plane stress (thin discs, free ends) unless the ends are restrained; for a compound cylinder, the working pressure acts on the assembly as one cylinder.
> - **Method:** 1. $\sigma_{rr}=-p$ on each loaded surface (0 if free); solve for $A$, $B$. 2. $\sigma_{zz}$ from the end condition. 3. Check Tresca, $(\sigma_{\theta\theta}-\sigma_{rr})/2$, or von Mises at the bore. 4. Shrink fit: constants per tube, continuity of $\sigma_{rr}$ at the interface, and $\delta=r_m(\varepsilon_{\theta\theta}^{o}-\varepsilon_{\theta\theta}^{i})$. 5. Superpose the shrink and working-pressure stresses.
> - **Common mistakes:** a positive radial stress for a pressure; $B\neq0$ in a solid shaft.
> - **Practise:** [[#Single against compound cylinder]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q3 - Contact pressure in a shrink fit|Tutorial 5 Q3]]

Thick cylinders cover hydraulic jacks, pressure vessels and the hydrogen and fuel tanks of sustainable aviation, where several materials are often combined, for corrosion resistance as well as for strength.

When a thick cylinder is pressurised, the inner skin of the wall is stretched hardest round its circumference, because it must stretch the most to let the bore grow, while the outer surface is stretched much less, so the hoop stress falls off through the wall. Adding wall thickness therefore helps less and less: the extra material sits where the stress is already low. A shrink fit does better by pre-loading the tube, squeezing the inner layer in advance so that the working pressure first has to cancel that squeeze before it can stretch it.

## 1. Stresses in a pressurised cylinder

### Radial and hoop stresses

With an internal pressure $p_i$ on $r_i$ and an external pressure $p_o$ on $r_o$, the boundary conditions are

$$
\sigma_{rr}(r_i)=-p_i,\qquad\sigma_{rr}(r_o)=-p_o,
$$

the minus signs because $\sigma_{rr}$ was taken positive in tension while a pressure pushes on the wall. Substitute into $\sigma_{rr}=A-B/r^2$:

$$
A-\frac{B}{r_i^2}=-p_i,\qquad A-\frac{B}{r_o^2}=-p_o .
$$

Subtract the second from the first:

$$
B\left(\frac{1}{r_o^2}-\frac{1}{r_i^2}\right)=-(p_i-p_o)\quad\Longrightarrow\quad B=\frac{(p_i-p_o)r_i^2r_o^2}{r_o^2-r_i^2}.
$$

Back-substitute into the second equation, $A=B/r_o^2-p_o$:

$$
A=\frac{(p_i-p_o)r_i^2}{r_o^2-r_i^2}-p_o=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2}.
$$

The general form $A\mp B/r^2$ is combined with the boundary conditions afresh for each problem. With internal pressure only and $k=r_o/r_i$, the extremes are at the bore, $\sigma_{rr}=-p_i$ and $\sigma_{\theta\theta}=p_i(k^2+1)/(k^2-1)$ ([[Lame Thick-Cylinder Solution]]).

### Axial stress and the end conditions

The axial stress depends on how the ends are held. With end caps attached, cut the vessel across: the pressure on the cap, $p_i\pi r_i^2$, is resisted by the axial stress over the wall area, so for internal pressure only

$$
\sigma_{zz}\,\pi\left(r_o^2-r_i^2\right)=p_i\pi r_i^2\quad\Longrightarrow\quad\sigma_{zz}=\frac{p_ir_i^2}{r_o^2-r_i^2}=A .
$$

With free, piston-like ends nothing resists axially, so $\sigma_{zz}=0$ but the tube still changes length, $\varepsilon_{zz}=-\nu(\sigma_{rr}+\sigma_{\theta\theta})/E\neq0$: plane stress. Built in between rigid supports, the supports stop the tube changing length, $\varepsilon_{zz}=0$, so

$$
0=\frac1E\left[\sigma_{zz}-\nu\left(\sigma_{rr}+\sigma_{\theta\theta}\right)\right]\quad\Longrightarrow\quad\sigma_{zz}=\nu\left(\sigma_{rr}+\sigma_{\theta\theta}\right)=2\nu A,
$$

plane strain. In every case $\sigma_{zz}$ is uniform through the wall, because $\sigma_{rr}+\sigma_{\theta\theta}=2A$ is.

## 2. Failure criteria

For internal pressure, $\sigma_{\theta\theta}>0>\sigma_{rr}$ and, whatever the end condition, $\sigma_{zz}$ lies between them, so it is the intermediate principal stress. Tresca therefore depends only on the hoop and radial stresses. At the bore, with internal pressure only,

$$
\tau_{max}=\frac{\sigma_{\theta\theta}-\sigma_{rr}}{2}=\frac{\left(A+B/r_i^2\right)-\left(A-B/r_i^2\right)}{2}=\frac{B}{r_i^2}=\frac{p_ik^2}{k^2-1}.
$$

Yield occurs when $\tau_{max}=\sigma_Y/2$, which gives the largest safe pressure

$$
p_{i,max}=\frac{\sigma_Y}{2}\cdot\frac{k^2-1}{k^2}=\frac{\sigma_Y}{2}\left(1-\frac{1}{k^2}\right).
$$

Even an infinitely thick wall cannot exceed $\sigma_Y/2$. The von Mises criterion,

$$
\tfrac12\left[\left(\sigma_{\theta\theta}-\sigma_{rr}\right)^2+\left(\sigma_{rr}-\sigma_{zz}\right)^2+\left(\sigma_{zz}-\sigma_{\theta\theta}\right)^2\right]=\sigma_Y^2,
$$

does involve $\sigma_{zz}$, so its pressure limit differs for capped, piston and built-in ends ([[Von Mises and Tresca Yield Criteria]]).

> [!check] The three end conditions for $k=2$, $\nu=0.3$
> Tresca gives $p_{i,max}=0.375\,\sigma_Y$ for every end condition. Von Mises gives $0.433\,\sigma_Y$ capped (where $\sigma_{zz}=A$ sits exactly midway between $\sigma_{rr}$ and $\sigma_{\theta\theta}$, so the criterion reduces to $\sqrt3\,\tau_{max}=\sigma_Y$), $0.429\,\sigma_Y$ with piston ends and $0.432\,\sigma_Y$ built in. Tresca is the conservative one, by about 13 %.

## 3. Making better use of the material

Because the hoop stress falls from the bore to the outside, a plain thick cylinder uses its outer material poorly. Three remedies are used. A **compound cylinder** heats the outer tube and cools the inner one, assembles them and lets them return to room temperature; the outer tube then squeezes the inner, and the residual stresses, added to the working stresses, flatten the distribution. Pre-tensioned **wire or fibre winding** does the same from outside: modern tanks wind carbon fibre round an aluminium liner. **Autofrettage** pressurises the bore until it yields; on release, elastic recovery of the outer material leaves the bore in residual compression, and work hardening raises its yield stress. The cost is reduced ductility, which matters because a ductile part gives warning before failing and a brittle one does not.

## 4. Analysing a shrink fit

Each tube has its own Lamé constants: $A$, $B$ for the inner tube ($r_i\le r\le r_m$) and $C$, $D$ for the outer ($r_m\le r\le r_o$) ([[Shrink Fit]]). Four conditions fix them. The free or loaded surfaces carry their pressures (zero when unpressurised):

$$
\sigma^{i}_{rr}(r_i)=-p_i,\qquad\sigma^{o}_{rr}(r_o)=-p_o .
$$

The radial stress is continuous at the interface, where it equals minus the contact pressure $p_c$:

$$
\sigma^{i}_{rr}(r_m)=\sigma^{o}_{rr}(r_m)=-p_c .
$$

The fourth condition is the interference $\delta$: before assembly, the outer radius of the inner tube exceeds the inner radius of the outer tube by $\delta$. After assembly they meet, so the outer tube has moved out and the inner moved in by a total of $\delta$:

$$
\delta=u^{o}_r(r_m)-u^{i}_r(r_m).
$$

Convert displacement to strain with $u_r=r\varepsilon_{\theta\theta}$:

$$
\frac{\delta}{r_m}=\varepsilon^{o}_{\theta\theta}(r_m)-\varepsilon^{i}_{\theta\theta}(r_m),
$$

and strain to stress with Hooke's law in each material (plane stress):

$$
\frac{\delta}{r_m}=\frac{\sigma^{o}_{\theta\theta}-\nu_o\sigma^{o}_{rr}}{E_o}-\frac{\sigma^{i}_{\theta\theta}-\nu_i\sigma^{i}_{rr}}{E_i}\bigg|_{r_m}.
$$

The four equations are linear in $A$, $B$, $C$, $D$ and can be solved in matrix form. For a solid inner shaft, $B=0$ to keep the stress finite at the centre, so its stress is uniform, $\sigma_{rr}=\sigma_{\theta\theta}=-p_c$.

### Same material: a closed form for the contact pressure

If both tubes are the same material, the radial stresses at $r_m$ are equal ($-p_c$), so the $\nu$ terms cancel:

$$
\frac{\delta}{r_m}=\frac{\sigma^{o}_{\theta\theta}(r_m)-\sigma^{i}_{\theta\theta}(r_m)}{E}.
$$

The outer tube is a cylinder under internal pressure $p_c$, and the inner one a cylinder under external pressure $p_c$; from §1 their hoop stresses at $r_m$ are

$$
\sigma^{o}_{\theta\theta}(r_m)=p_c\frac{r_o^2+r_m^2}{r_o^2-r_m^2},\qquad\sigma^{i}_{\theta\theta}(r_m)=-p_c\frac{r_m^2+r_i^2}{r_m^2-r_i^2}.
$$

Subtract, over a common denominator:

$$
\frac{\delta}{r_m}=\frac{p_c}{E}\cdot\frac{\left(r_o^2+r_m^2\right)\left(r_m^2-r_i^2\right)+\left(r_m^2+r_i^2\right)\left(r_o^2-r_m^2\right)}{\left(r_o^2-r_m^2\right)\left(r_m^2-r_i^2\right)}.
$$

Expanding the numerator, the $r_m^4$ and $r_o^2r_i^2$ terms cancel and it reduces to $2r_m^2\left(r_o^2-r_i^2\right)$. So

$$
p_c=\frac{E\,\delta\left(r_m^2-r_i^2\right)\left(r_o^2-r_m^2\right)}{2r_m^3\left(r_o^2-r_i^2\right)}.
$$

Under working pressure, the total stress is the shrink-fit stress plus the stress from the pressure acting on the assembly as one thick cylinder, which is valid when both tubes have the same elastic constants ([[Shrink Fit Superposition]]).

## Worked examples

### A hydraulic-jack cylinder

An aircraft control jack works at $p_i=138$ bar $=13.8$ MPa in a 150 mm bore, and the hoop stress may not exceed 41.4 MPa. Find the wall thickness.

At the bore, $r_i=75$ mm, both stresses are known:

$$
A-\frac{B}{75^2}=-13.8,\qquad A+\frac{B}{75^2}=41.4 .
$$

Add and halve: $A=13.8$ MPa. Subtract and halve: $B/75^2=27.6$ MPa, so $B=27.6\times75^2=1.553\times10^5$ N. The outer surface is free:

$$
A-\frac{B}{r_o^2}=0\quad\Longrightarrow\quad r_o=\sqrt{\frac BA}=\sqrt{\frac{1.553\times10^5}{13.8}}=106.1\text{ mm},
$$

a wall $106.1-75=31.1$ mm thick. Equivalently, the bore hoop stress ratio $(k^2+1)/(k^2-1)=41.4/13.8=3$ gives $k^2=2$, $k=\sqrt2$.

### A steel shaft in a bronze bush

A solid steel shaft, 100 mm in diameter ($E=207$ GPa, $\nu=0.29$), is shrunk into a bronze bush 25 mm thick ($E=100$ GPa, $\nu=0.28$) to give a contact pressure of 69 MPa. Find the interference.

The shaft is uniformly compressed, $\sigma_{rr}=\sigma_{\theta\theta}=-69$ MPa, so at $r_m=50$ mm

$$
\varepsilon^{i}_{\theta\theta}=\frac{\sigma_{\theta\theta}-\nu\sigma_{rr}}{E}=\frac{-69+0.29\times69}{207\,000}=-2.37\times10^{-4}.
$$

The bush ($r_m=50$, $r_o=75$ mm, $k=1.5$) is a thick cylinder under internal pressure 69 MPa, whose bore hoop stress is

$$
\sigma^{o}_{\theta\theta}=69\times\frac{2.25+1}{2.25-1}=179.4\text{ MPa},
$$

with $\sigma^{o}_{rr}=-69$ MPa, so

$$
\varepsilon^{o}_{\theta\theta}=\frac{179.4+0.28\times69}{100\,000}=1.99\times10^{-3}.
$$

The interference is

$$
\delta=r_m\left(\varepsilon^{o}_{\theta\theta}-\varepsilon^{i}_{\theta\theta}\right)=50\left(1.99\times10^{-3}+2.37\times10^{-4}\right)=0.111\text{ mm}
$$

on the radius, 0.222 mm on the diameter. The bush takes 89 % of it, because bronze is half as stiff and the bush is the hoop-stressed part.

### Single against compound cylinder

A steel vessel ($E=207$ GPa) with a 200 mm bore and a 400 mm outside diameter carries 2070 bar $=207$ MPa, either as one tube or as two equal-thickness tubes shrunk together at 300 mm diameter with an interference of 0.1 mm. Compare the hoop stresses.

Taking the interference as radial, the same-material formula gives

$$
p_c=\frac{207\,000\times0.1\times\left(150^2-100^2\right)\left(200^2-150^2\right)}{2\times150^3\times\left(200^2-100^2\right)}=22.4\text{ MPa}.
$$

| Radius (mm) | Single tube $\sigma_{rr}$, $\sigma_{\theta\theta}$ (MPa) | Compound: shrink $\sigma_{\theta\theta}$ | Compound: total $\sigma_{\theta\theta}$ |
|---|---|---|---|
| 100 (bore) | −207, 345 | −80.5 | 264.5 |
| 150 (inner tube) | −53.7, 191.7 | −58.1 | 133.5 |
| 150 (outer tube) | −53.7, 191.7 | +79.9 | 271.5 |
| 200 (outside) | 0, 138 | +57.5 | 195.5 |

The peak hoop stress falls from 345 to 272 MPa, 21 % lower, and the two tubes now carry similar peaks: the material is used more evenly. If the 0.1 mm is diametral, $p_c$ halves.

![[structures_s10_compound_cylinder.png|800]]

> [!check] The interference is recovered
> Solving the four-constant system for $p_c=22.36$ MPa and evaluating $u^{o}_r(r_m)-u^{i}_r(r_m)$ with $\nu=0.3$ returns exactly 0.100 mm, confirming that Poisson's ratio drops out for one material.

### Past paper: a gas cylinder at 1000 bar

A thick-walled steel cylinder ($E=210$ GPa, $\nu=0.3$) holds gas at 1000 bar $=100$ MPa, with internal and external diameters of 250 mm and 500 mm. Find the radial and hoop stress distributions and the maximum normal stresses, and say whether the material is used efficiently (2024–25 paper, SQ3).

Here $r_i=125$ mm, $r_o=250$ mm, $k=2$:

$$
A=\frac{100\times125^2}{250^2-125^2}=33.3\text{ MPa},\qquad B=\frac{100\times125^2\times250^2}{250^2-125^2}=2.08\times10^6\text{ N},
$$

$$
\sigma_{rr}=33.3-\frac{2.08\times10^6}{r^2},\qquad\sigma_{\theta\theta}=33.3+\frac{2.08\times10^6}{r^2}\quad(r\text{ in mm}).
$$

At the bore $\sigma_{rr}=-100$ MPa and $\sigma_{\theta\theta}=166.7$ MPa; at the outside $\sigma_{rr}=0$ and $\sigma_{\theta\theta}=66.7$ MPa. The maximum normal stress is the bore hoop stress, 166.7 MPa. The material is not used efficiently: the outer surface works at only 40 % of the bore's hoop stress, so most of the wall is lightly loaded. A compound (shrink-fitted) cylinder, wire or fibre winding, or autofrettage would pre-compress the bore and even out the distribution.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · Next: [[SESA2028 S11 - Spinning Discs]]
- Concepts: [[Lame Thick-Cylinder Solution]] · [[Lame Equations]] · [[Shrink Fit]] · [[Shrink Fit Superposition]] · [[Compound Cylinder]] · [[Von Mises and Tresca Yield Criteria]]
- Problems: [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions]] · [[SESA2028 Past Paper Map]] · Formulae: [[SESA2028 Formula Sheet]]

## Sources

- Slides: `SL22 - Continuum Mechanics 4 - Thick Walled Cylinders.pdf` (boundary conditions, end conditions, failure, the jack on slide 18), `SL23 - Continuum Mechanics 5 - Shrink Fit Assembly.pdf` (shrink-fit analysis, examples 1 and 2) and `Structures Additional session - thick wall cylinders.pdf`.
- Transcripts: `SESA2028 Lecture 2026-05-06 - SL16 (Part 2) Continuum mechanics.txt`, `SESA2028 Lecture 2026-05-08.txt`, the tutorial `SESA2028 Lecture 2026-05-11.txt` and the revision lecture `SESA2028 Lecture 2026-05-13.txt` (ll. 150–215, the 1000 bar question); the question itself is SQ3 of `FEEG2005-202425-02-FEEG2005.pdf`.
- All examples recomputed in Python, including the four-constant shrink-fit system and the von Mises limits. Figures: `generate_structures_s10_figures.py`; the residual-stress sketch in `generate_structures_figures.py` (tutorial 5 Q3 geometry) is used by the concept notes.

## Self-study tasks

### Core

- [ ] Apply the boundary conditions to get $A$ and $B$, and the axial stress for each end condition (2026-05-06 part 2, ll. 1–175). → [[#1. Stresses in a pressurised cylinder]]
- [ ] The hydraulic-jack wall thickness, SL22 slide 18 (2026-05-08, ll. 80–135). → [[#A hydraulic-jack cylinder]]
- [ ] The shaft-and-bush interference and the single against compound cylinder, SL23 examples 1–2 (2026-05-08, ll. 301–390; solutions on Blackboard). → [[#A steel shaft in a bronze bush]] · [[#Single against compound cylinder]]
- [ ] Structures tutorial 5 (2026-05-11). → [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q1 - Thick cylinder under internal and external pressure|Q1]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q2 - Maximum pressure and diameter change|Q2]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q3 - Contact pressure in a shrink fit|Q3]]
- [ ] Past-paper thick cylinder at 1000 bar (revision, 2026-05-13, ll. 150–215). → [[#Past paper: a gas cylinder at 1000 bar]]

### Further practice

- [ ] Derive the Tresca pressure limit and compare it with von Mises for capped, piston and built-in ends (2026-05-08, ll. 1–80). → [[#2. Failure criteria]]
- [ ] Derive the same-material contact-pressure formula from the interference condition (suggested, not lecturer-set). → [[#Same material: a closed form for the contact pressure]]

## Transcript and slide slips

> [!warning] Transcript slip (2026-05-13, revision, past-paper question)
> Where: [[#Past paper: a gas cylinder at 1000 bar]].
>
> The innermost point is described as "r equals 250"; 250 mm is the internal diameter, so the bore radius is $r=125$ mm.

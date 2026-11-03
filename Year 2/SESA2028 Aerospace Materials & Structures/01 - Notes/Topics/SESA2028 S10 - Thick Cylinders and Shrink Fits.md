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
sources: ["02 - Sources/Structures Lectures/SL22 - Continuum Mechanics 4 - Thick Walled Cylinders.pdf", "02 - Sources/Structures Lectures/SL23 - Continuum Mechanics 5 - Shrink Fit Assembly.pdf", "02 - Sources/Structures Lectures/Structures Additional session - thick wall cylinders.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-06 - SL16 (Part 2) Continuum mechanics.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-08.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-11.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-05-13.txt"]
---

# SESA2028 S10 - Thick Cylinders and Shrink Fits

> [!abstract] Summary
> The Lamé solution $\sigma_{rr}=A-B/r^2$, $\sigma_{\theta\theta}=A+B/r^2$ with the pressure boundary conditions gives the radial and hoop stresses through a thick cylinder; the axial stress depends on how the ends are held (capped, free like a piston, or built in). The hoop stress peaks at the bore, so the outer material is under-used and yield (Tresca or von Mises) starts at the bore. A shrink fit, an outer tube heated and slipped over an inner one, puts the bore into residual compression and evens out the hoop stress; it is analysed with two Lamé solutions, four constants, and an interference condition converted from displacement to strain to stress.

> [!summary]- Exam use: quick path
> - **Use it when:** a thick tube, pressure vessel, jack cylinder, shaft-and-bush or compound cylinder carries pressure.
> - **Assumptions:** linear elastic, isotropic, axisymmetric; plane stress (thin discs, free ends) unless the ends are restrained.
> - **Method:** 1. $\sigma_{rr}=-p$ on each loaded surface (0 if free); solve for $A$, $B$. 2. $\sigma_{zz}$ from the end condition. 3. Check Tresca, $(\sigma_{\theta\theta}-\sigma_{rr})/2$, or von Mises at the bore. 4. Shrink fit: constants per tube, continuity of $\sigma_{rr}$ at the interface, and $\delta=r_m(\varepsilon_{\theta\theta}^{o}-\varepsilon_{\theta\theta}^{i})$. 5. Superpose shrink and working-pressure stresses.
> - **Common mistakes:** a positive radial stress for a pressure; $B\neq0$ in a solid shaft.
> - **Practise:** [[#Worked examples]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q3 - Contact pressure in a shrink fit|Tutorial 5 Q3]]

Thick cylinders cover hydraulic jacks, pressure vessels and the hydrogen and fuel tanks of sustainable aviation, where several materials are often combined, for corrosion resistance as well as strength (2026-05-06 part 2, ll. 160–180).

When a thick cylinder is pressurised, the inner skin of the wall is stretched hardest round its circumference because it must stretch the most to let the bore grow, while the outer surface is stretched much less, so the stress falls off through the wall. Adding wall thickness helps less and less. A shrink fit does better by pre-loading the tube, squeezing the inner layer in advance so that the working pressure first has to cancel that squeeze.

## 1. Stresses in a pressurised cylinder

With an internal pressure $p_i$ and external pressure $p_o$ on radii $r_i$ and $r_o$, the boundary conditions are (2026-05-06 part 2, ll. 70–110)

$$
\sigma_{rr}(r_i)=-p_i,
\qquad
\sigma_{rr}(r_o)=-p_o,
$$

the minus signs because $\sigma_{rr}$ was taken positive in tension while a pressure pushes inward on the wall (a question to the class, ll. 90–100). Substituting into $\sigma_{rr}=A-B/r^2$ and solving:

$$
A=\frac{p_ir_i^2-p_or_o^2}{r_o^2-r_i^2},
\qquad
B=\frac{(p_i-p_o)r_i^2r_o^2}{r_o^2-r_i^2}.
$$

The lecturer's advice is to remember only the form $A\mp B/r^2$ and apply the boundary conditions each time (ll. 101–115). With internal pressure only and $k=r_o/r_i$, the maxima are at the bore, $\sigma_{rr}=-p_i$ and $\sigma_{\theta\theta}=p_i(k^2+1)/(k^2-1)$ ([[Lame Thick-Cylinder Solution]]).

The axial stress depends on the ends (ll. 1–70, 115–175). With end caps attached, axial equilibrium of a cut through the vessel gives, for internal pressure only,

$$
\sigma_{zz}\pi\left(r_o^2-r_i^2\right)=p_i\pi r_i^2
\quad\Longrightarrow\quad
\sigma_{zz}=\frac{p_ir_i^2}{r_o^2-r_i^2}=A .
$$

With free piston-like ends, nothing resists axially: $\sigma_{zz}=0$ but $\varepsilon_{zz}=-\nu(\sigma_{rr}+\sigma_{\theta\theta})/E\neq0$, plane stress. Built in between rigid supports, $\varepsilon_{zz}=0$ and so $\sigma_{zz}=\nu(\sigma_{rr}+\sigma_{\theta\theta})=2\nu A$, plane strain. When asked, part of the class expected no axial stress between rigid supports; there is one, because the supports stop the tube lengthening.

## 2. Failure criteria

Whatever the end condition, $\sigma_{zz}$ is the intermediate principal stress, so Tresca depends only on the hoop and radial stresses (2026-05-08, ll. 1–60). At the bore, with internal pressure only,

$$
\tau_{max}=\frac{\sigma_{\theta\theta}-\sigma_{rr}}{2}=\frac{B}{r_i^2}=\frac{p_ik^2}{k^2-1},
$$

and yield ($\tau_{max}=\sigma_Y/2$) gives the largest safe pressure

$$
p_{i,max}=\frac{\sigma_Y}{2}\left(1-\frac{1}{k^2}\right).
$$

Even an infinitely thick wall cannot exceed $\sigma_Y/2$. The von Mises criterion, $\tfrac12[(\sigma_{\theta\theta}-\sigma_{rr})^2+(\sigma_{rr}-\sigma_{zz})^2+(\sigma_{zz}-\sigma_{\theta\theta})^2]=\sigma_Y^2$, does involve $\sigma_{zz}$, so its pressure limit differs for capped, piston and built-in ends (ll. 60–80; [[Von Mises and Tresca Yield Criteria]]).

## 3. Making better use of the material

Because the hoop stress falls from bore to outside, a plain thick cylinder uses its outer material poorly (ll. 136–200). Three remedies were described. A compound cylinder heats the outer tube and cools the inner one, assembles them and lets them return to room temperature; the outer tube then squeezes the inner, and the residual stresses, added to the working stresses, flatten the distribution. Pre-tensioned wire or fibre winding does the same from outside: modern tanks wind carbon fibre round an aluminium liner. Autofrettage pressurises the bore until it yields; on release, elastic recovery leaves the bore in residual compression and work hardening raises its yield stress, at the cost of reduced ductility, which matters because a ductile part gives warning before failing and a brittle one does not.

## 4. Analysing a shrink fit

Each tube has its own Lamé constants: $A$, $B$ for the inner tube ($r_i\le r\le r_m$) and $C$, $D$ for the outer ($r_m\le r\le r_o$) (2026-05-08, ll. 201–300; [[Shrink Fit]]). Four conditions fix them. The surfaces carry their pressures (zero when unpressurised):

$$
\sigma^{i}_{rr}(r_i)=-p_i,
\qquad
\sigma^{o}_{rr}(r_o)=-p_o .
$$

The radial stress is continuous at the interface, the contact pressure $p_c$:

$$
\sigma^{i}_{rr}(r_m)=\sigma^{o}_{rr}(r_m)=-p_c .
$$

The fourth is the interference $\delta$, the difference between the outer radius of the inner tube and the inner radius of the outer one before assembly: after assembly the outer tube has moved out and the inner moved in by a total of $\delta$,

$$
\delta=u^{o}_r(r_m)-u^{i}_r(r_m).
$$

Convert displacement to strain with $u_r=r\varepsilon_{\theta\theta}$,

$$
\frac{\delta}{r_m}=\varepsilon^{o}_{\theta\theta}(r_m)-\varepsilon^{i}_{\theta\theta}(r_m),
$$

and strain to stress with Hooke's law in each material (plane stress):

$$
\frac{\delta}{r_m}=\frac{\sigma^{o}_{\theta\theta}-\nu_o\sigma^{o}_{rr}}{E_o}-\frac{\sigma^{i}_{\theta\theta}-\nu_i\sigma^{i}_{rr}}{E_i}\bigg|_{r_m}.
$$

The four linear equations in $A$, $B$, $C$, $D$ are conveniently solved in matrix form. For a solid inner shaft, $B=0$ to keep the stress finite at the centre, so its stress is uniform, $\sigma_{rr}=\sigma_{\theta\theta}=-p_c$. Under working pressure, the total stress is the shrink-fit stress plus the stress from the pressure acting on the assembly as one thick cylinder of the same material ([[Shrink Fit Superposition]]).

## Worked examples

All recomputed in Python.

### A hydraulic-jack cylinder

SL22 slide 18 (2026-05-08, ll. 80–135): an aircraft control jack works at $p_i=138$ bar = 13.8 MPa in a 150 mm bore; the hoop stress may not exceed 41.4 MPa; find the wall thickness. At the bore,

$$
A-\frac{B}{75^2}=-13.8,
\qquad
A+\frac{B}{75^2}=41.4,
$$

so $A=13.8$ MPa and $B=27.6\times75^2=1.553\times10^5$ N. The outer surface is free:

$$
A-\frac{B}{r_o^2}=0
\quad\Longrightarrow\quad
r_o=\sqrt{\frac BA}=106.1\text{ mm},
$$

a wall 31.1 mm thick. Equivalently $(k^2+1)/(k^2-1)=3$ gives $k=\sqrt2$.

### A steel shaft in a bronze bush

SL23 example 1 (ll. 301–390): a solid steel shaft, 100 mm diameter ($E=207$ GPa, $\nu=0.29$), is shrunk into a bronze bush 25 mm thick ($E=100$ GPa, $\nu=0.28$) to give a contact pressure of 69 MPa; find the interference. The shaft is uniformly compressed, so at $r_m=50$ mm

$$
\varepsilon^{i}_{\theta\theta}=\frac{-69+0.29\times69}{207\,000}=-2.37\times10^{-4}.
$$

The bush ($r_m=50$, $r_o=75$, $k=1.5$) is a thick cylinder with internal pressure 69 MPa, whose bore hoop stress is $69(2.25+1)/(2.25-1)=179.4$ MPa:

$$
\varepsilon^{o}_{\theta\theta}=\frac{179.4+0.28\times69}{100\,000}=1.99\times10^{-3}.
$$

So

$$
\delta=50\left(1.99\times10^{-3}+2.37\times10^{-4}\right)=0.111\text{ mm}
$$

on the radius (0.222 mm on the diameter).

### Single against compound cylinder

SL23 example 2: a steel vessel ($E=207$ GPa) with bore 200 mm and outside 400 mm carries 2070 bar = 207 MPa, either as one tube or as two equal tubes shrunk together at 300 mm diameter with interference 0.1 mm. Taking the interference as radial, for one material the contact pressure is

$$
p_c=\frac{E\delta\left(r_m^2-r_i^2\right)\left(r_o^2-r_m^2\right)}{2r_m^3\left(r_o^2-r_i^2\right)}=22.4\text{ MPa}.
$$

| Radius (mm) | Single tube $\sigma_{rr}$, $\sigma_{\theta\theta}$ (MPa) | Compound: shrink $\sigma_{\theta\theta}$ | Compound: total $\sigma_{\theta\theta}$ |
|---|---|---|---|
| 100 (bore) | −207, 345 | −80.5 | 264.5 |
| 150 (inner tube) | −53.7, 191.7 | −58.1 | 133.5 |
| 150 (outer tube) | −53.7, 191.7 | +79.9 | 271.5 |
| 200 (outside) | 0, 138 | +57.5 | 195.5 |

The peak hoop stress falls from 345 to 272 MPa and the two tubes now carry similar peaks: the material is used more evenly. (If the 0.1 mm is diametral, $p_c$ halves.)

The revision lecture's first past-paper question is the same kind: a steel thick cylinder holding gas at 1000 bar, asking for the stress distributions, the maximum normal stresses, and whether the material is used effectively, the answer being no, for the reason above (2026-05-13, ll. 150–215).

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]
- Next: [[SESA2028 S11 - Spinning Discs]]
- Concepts: [[Lame Thick-Cylinder Solution]] · [[Lame Equations]] · [[Shrink Fit]] · [[Shrink Fit Superposition]] · [[Compound Cylinder]]

![[structures_shrink_fit_residual_stress.png|700]]

## Sources

- Structures slides SL22, SL23 and the thick-wall additional session, with transcripts `SESA2028 Lecture 2026-05-06 - SL16 (Part 2)`, `SESA2028 Lecture 2026-05-08.txt`, the tutorial `SESA2028 Lecture 2026-05-11.txt` and the revision lecture `SESA2028 Lecture 2026-05-13.txt`
- Examples recomputed in Python

## Self-study tasks

### Core

- [ ] Apply the boundary conditions to get $A$ and $B$ and the axial stress for each end condition (2026-05-06 part 2, ll. 1–175). → [[#1. Stresses in a pressurised cylinder]]
- [ ] The hydraulic-jack wall thickness (2026-05-08, ll. 80–135). → [[#A hydraulic-jack cylinder]]
- [ ] The shaft-and-bush interference and the single against compound cylinder (ll. 301–390; solutions on Blackboard). → [[#A steel shaft in a bronze bush]] · [[#Single against compound cylinder]]
- [ ] Structures tutorial 5 (2026-05-11). → [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q1 - Thick cylinder under internal and external pressure|Q1]] · [[SESA2028 Structures Tutorial 5 - Continuum Mechanics Solutions#Q2 - Maximum pressure and diameter change|Q2]]
- [ ] Past-paper thick cylinder at 1000 bar (revision, 2026-05-13, ll. 150–215). → [[#Worked examples]]

### Further practice

- [ ] Derive the Tresca pressure limit and compare it with von Mises for capped, piston and built-in ends (2026-05-08, ll. 1–80). → [[#2. Failure criteria]]

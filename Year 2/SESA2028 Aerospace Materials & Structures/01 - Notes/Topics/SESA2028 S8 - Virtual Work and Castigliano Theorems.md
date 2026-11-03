---
title: "SESA2028 S8 - Virtual Work and Castigliano Theorems"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 8
tags: [sesa2028, structures, virtual-work, castigliano, energy-methods]
date: 2026-10-30
status: lectured
coverage: "SL3 (2026-02-04, ll. 240–482), SL4 (2026-02-11), SL5 (2026-02-13), SL6 and the recorded L-frame video (2026-02-18)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
next_topics: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
key_concepts: ["[[Principle of Virtual Work]]", "[[Unit Load Method]]", "[[Castigliano Theorem]]", "[[Castigliano Second Theorem]]", "[[Complementary Energy]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL9 - Energy methods 2 - Virtual Work and Strain Energy Solutions.pdf", "02 - Sources/Structures Lectures/SL15 - EnergyMethods 2 - The Pricinple of Virtual Work 1.pdf", "02 - Sources/Structures Lectures/SL16 - EnergyMethods 3 - The Pricinple of Virtual Work 2.pdf", "02 - Sources/Structures Lectures/SL17 - EnergyMethods 4 - The Pricinple of Virtual Work 3.pdf", "02 - Sources/Structures Lectures/SL18 - EnergyMethods 5 - Castigilianos Theorems.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-11 - SL4 Energy Method. General virtual work.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-13 - SL5 Energy method. Castigliano.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-18 - SL6 Energy method. Asymmetric beams.txt"]
---

# SESA2028 S8 - Virtual Work and Castigliano Theorems

> [!abstract] Summary
> Conservation of energy gives a deflection only where a load acts and in its direction. The principle of virtual work removes that limit: apply a virtual (usually unit) load where the displacement is wanted, and the external virtual work of that load through the real displacement equals the internal virtual work of its member forces or moments through the real deformations, giving $1\cdot u=\sum P_i^*P_iL_i/E_iA_i$ for a truss and $\int M^*M/EI\,dx$ for a beam. Castigliano's theorems express the same idea as derivatives: the force is $\partial U/\partial u$, the displacement $\partial C/\partial F$ of the complementary energy, which for a linear structure is $\partial U/\partial F$; a dummy load, set to zero after differentiating, gives displacements where no load acts.

> [!summary]- Exam use: quick path
> - **Use it when:** you need a deflection or rotation at a point or in a direction where no load acts, or a deflection of a frame, curved member or truss.
> - **Assumptions:** linear elastic, small displacements, quasi-static; axial and shear energy of beams neglected unless stated.
> - **Method:** 1. Real system: $M(x)$ or member forces $P_i$. 2. Virtual system: unit load (or unit moment) at the point and direction wanted, giving $M^*(x)$ or $P_i^*$. 3. $u=\int M^*M/EI\,dx$ or $\sum P_i^*P_iL_i/E_iA_i$, member by member. 4. Or Castigliano: $U(F,Q)$, $u=\partial U/\partial Q$ at $Q=0$. 5. Indeterminate: set the redundant's displacement or rotation to zero.
> - **Common mistakes:** inconsistent sign conventions between real and virtual systems; using Castigliano on a nonlinear structure.
> - **Practise:** [[#Worked examples]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q2 - Quarter-circular cantilever|Tutorial 1 Q2]]

Virtual work was introduced half-way through SL3 to answer a question conservation of energy could not: how far does the truss joint move horizontally under a vertical load (2026-02-04, ll. 200–240)? The lectures then generalised it (SL4), derived Castigliano's theorems (SL5) and applied both to frames, beams and rings (SL6). The lecturer stresses that "there are in principle three to four theories", and the many worked examples on Blackboard, each linked to its solution, are applications of them (2026-02-27, ll. 290–320).

Conservation of energy only balances the work done at the load point, so it gives the deflection there and nowhere else. Virtual work imagines a tiny extra force at the point of interest and asks how much work it would do while the structure deforms under the real loads; since that work must equal what the imagined force's own internal forces do through the real strains, it measures the real displacement there. The imagined force never exists; it only labels the displacement you want to read.

## 1. The principle of virtual work

A particle is in equilibrium under a system of forces with resultant $\mathbf F_R=\mathbf 0$ (2026-02-04, ll. 241–330). Give it any virtual displacement $\boldsymbol\delta^*$, a displacement that need not actually happen but must be geometrically possible, during which the real forces stay constant and parallel to their original lines. The virtual work is

$$
W^*=\mathbf F_R\cdot\boldsymbol\delta^*=0,
$$

and conversely, if the virtual work is zero for every virtual displacement, the particle is in equilibrium. A deformable body in equilibrium has every particle in equilibrium, so summing over all particles, both external and internal forces, the total virtual work is zero, which splits into

$$
W^*_{ext}=W^*_{int}:
$$

for any admissible virtual deformation, the work put in by the external loads equals the work absorbed internally by the stresses ([[Principle of Virtual Work]]). In general form (SL4), with real displacements $u$ and strains $\boldsymbol\varepsilon$ and virtual loads $T^*$ and stresses $\boldsymbol\sigma^*$,

$$
\sum T^*u=\int_V\boldsymbol\sigma^*:\boldsymbol\varepsilon\,dV .
$$

## 2. The truss: deriving the unit-load formula

The truss carries a real load $F$; we want the horizontal displacement $u_x$ of its loaded joint (2026-02-04, ll. 330–480). Add a virtual force $F^*$ there in the $x$ direction. Each member then carries $P_i+P_i^*$, the real force plus the force due to $F^*$ alone.

Apply $F^*$ first, then $F$. The external work has three parts:

$$
W_e=\tfrac12F^*u_x^*+\tfrac12Fu_y+F^*u_x .
$$

The last term has no half: $F^*$ is already at full value while $F$ makes the joint move $u_x$, so it does work at constant force. The internal energy uses the total member forces:

$$
U=\sum_i\frac{\left(P_i+P_i^*\right)^2L_i}{2E_iA_i}=\sum_i\frac{P_i^2L_i}{2E_iA_i}+\sum_i\frac{P_i^{*2}L_i}{2E_iA_i}+\sum_i\frac{P_i^*P_iL_i}{E_iA_i}.
$$

The first term equals $\tfrac12Fu_y$ (the real problem alone) and the second $\tfrac12F^*u_x^*$ (the virtual problem alone), so they cancel against the external work, leaving

$$
F^*u_x=\sum_i\frac{P_i^*P_iL_i}{E_iA_i}.
$$

Choose $F^*=1$ N, so no division is needed, and

$$
u_x=\sum_i\frac{p_iP_iL_i}{E_iA_i},
$$

with $p_i$ the member forces due to the unit load: the unit-load method ([[Unit Load Method]]). Any value of $F^*$ gives the same answer once divided out. In practice two truss problems are solved side by side, one with the real load and one with the unit load (2026-02-11, ll. 80–140). A slide in SL4 labels one member "AB" where it should read "BC" (2026-02-11, l. 70).

## 3. Beams and frames

For bending, the internal virtual work of the unit load's stresses $\sigma^*=M^*y/I$ through the real strains $\varepsilon=My/EI$ is, integrating over the section first,

$$
\int_V\sigma^*\varepsilon\,dV=\int_0^L\frac{M^*M}{EI^2}\int_Ay^2\,dA\,dx=\int_0^L\frac{M^*M}{EI}\,dx,
$$

so the displacement in the direction of a unit load is

$$
1\cdot u=\int_0^L\frac{M^*(x)M(x)}{EI}\,dx,
$$

and a unit moment gives the rotation (2026-02-18, ll. 41–90). Frames are integrated member by member. Axial and shear energy are usually neglected, being far smaller than bending in slender members. Every problem needs four pieces of information: the loading, the boundary conditions, any compatibility conditions (for an indeterminate structure), and the constitutive law, without which no deflection can be found (ll. 27–48). Moments and forces are stress resultants, the integrated effect of the internal stresses.

## 4. Castigliano's theorems

Strain energy as a function of displacement. For an elastic structure, linear or not, the work to reach displacement $u$ is $U=\int_0^uF\,du$, so $dU/du=F$ (2026-02-13, ll. 1–92). For a truss with loads $F_1$, $F_2$, impose a virtual increment $\delta u_1$ with $\delta u_2=0$; subtracting the energy balances before and after gives

$$
F_1\,\delta u_1=\sum_iP_i\,\delta\Delta_i=\delta U,
$$

and since $\delta U=\frac{\partial U}{\partial u_1}\delta u_1$ when the other displacements are held,

$$
F_j=\frac{\partial U}{\partial u_j}:
$$

the force at a joint is the derivative of the strain energy with respect to the displacement there ([[Castigliano Theorem]]).

Complementary energy. On the force–displacement curve, the area beneath is $U$ and the area to its left, up to the force axis, is the complementary energy $C$, with $U+C=Fu$ (ll. 93–160; [[Complementary Energy]]). Then $C=\int_0^Fu\,dF$, so $dC/dF=u$, and the same perturbation argument applied to forces gives

$$
u_j=\frac{\partial C}{\partial F_j}.
$$

Asked what $C$ means physically, the lecturer described it as the area that completes the rectangle $Fu$; its use is that its force-derivative gives displacement.

For a linear structure the two areas are equal, $C=U$, and the second result becomes Castigliano's second theorem (ll. 241–300; [[Castigliano Second Theorem]]):

$$
\boxed{u_j=\frac{\partial U}{\partial F_j}}
$$

It holds only for linear behaviour. The same argument gives rotations from moments, $\theta_j=\partial U/\partial M_j$, and twists from torques. For a beam, with $U=\int M^2/2EI\,dx$,

$$
u=\frac{\partial U}{\partial F}=\int_0^L\frac{M}{EI}\frac{\partial M}{\partial F}\,dx,
$$

which is the unit-load formula again, since $\partial M/\partial F$ is the moment due to a unit $F$.

Castigliano applies directly only where a load acts. For a displacement elsewhere, add a dummy load $Q$ there in the wanted direction, write $U(F,Q)$, differentiate with respect to $Q$, then set $Q=0$ (ll. 291–320, 441–480). A student asked whether the dummy load could go at the real load's point: it must go where, and in the direction in which, the displacement is wanted.

## 5. Indeterminate structures

When equilibrium alone cannot fix the internal forces, a compatibility condition supplies the missing equation, and energy methods express it as a derivative set to zero (2026-02-18, ll. 290–440). In the diametrically loaded ring below, the moment at the cut is unknown, but symmetry says the section there does not rotate, so $\partial U/\partial M_0=0$ fixes it. The recorded "redundant" video applies the same idea to the L-frame.

## Worked examples

### Concentric tubes

Two concentric tubes, an inner aluminium one and an outer unidirectional carbon-fibre one, are bonded to rigid end plates and pushed together by $\delta=0.1$ mm; find the force (2026-02-13, ll. 200–240). Both shorten by $\delta$, like springs in parallel, so each carries $P_i=E_iA_i\delta/L$ and stores $P_i^2L/2E_iA_i$:

$$
U=\sum_i\frac{E_iA_i}{2L}\delta^2,
\qquad
F=\frac{\partial U}{\partial\delta}=\frac{\delta}{L}\left(E_1A_1+E_2A_2\right).
$$

With the slide's moduli and areas this gives the force directly; the first theorem is the right one because the energy is written in terms of displacement.

### Truss deflection without quadratics

For SL5's multi-member truss, finding the loaded joint's deflection by compatibility means three successive pairs of quadratic equations, joint by joint (ll. 321–400). By Castigliano, write every member force as a multiple of the load $P$ by the method of joints, sum $U=\sum N_i^2L_i/2A_iE_i$ (original lengths), and differentiate with respect to $P$. For the horizontal movement of another joint, add a horizontal dummy force $Q$ there, find the member forces in terms of $P$ and $Q$, differentiate with respect to $Q$ and set $Q=0$ (ll. 401–480).

### The L-frame "pet house"

An L-shaped frame, clamped at its base D, has a horizontal arm with the house and pet idealised as one load $F_c$ at its midpoint B; the deflection of the arm's free end A is wanted, to keep the floor's slope comfortable, for two candidate sections (2026-02-18, ll. 1–180). The load and the wanted displacement are at different points, so use virtual work. Real moments: zero from A to B, $F_c$ times the distance from B along B–C, and constant along the vertical leg C–D (the arm's axial force into the leg is neglected). Unit load at A: a moment growing linearly from A to C, then constant down C–D. Then

$$
u_A=\int_{BC}\frac{M^*M}{EI}\,dx+\int_{CD}\frac{M^*M}{EI}\,dx .
$$

The lecture's numbers give 2.9 mm for the first section and much less for the stiffer 75 × 75 mm one, which is the better choice.

### Midspan deflection under a uniform load

A simply supported beam under $w$ has no point load at midspan (ll. 200–250). Add a dummy load $F$ there. Each half has $M=\frac{wL}{2}x-\frac{wx^2}{2}+\frac F2x$ for $0\le x\le L/2$, so

$$
v=\frac{\partial U}{\partial F}\bigg|_{F=0}=2\int_0^{L/2}\frac{1}{EI}\left(\frac{wL}{2}x-\frac{wx^2}{2}\right)\frac x2\,dx=\frac{5wL^4}{384EI},
$$

the familiar result, without a separate unit-load problem.

### Stiffness of a ring

A thin ring of radius $R$ is squeezed by two forces $F$ along a diameter; find its stiffness $F/\delta$ (2026-02-18, ll. 290–440). Cut it on the diameter perpendicular to the loads. By symmetry each cut carries $F/2$ along the load direction and an unknown moment $M_0$. At angle $\phi$ from the cut,

$$
M(\phi)=M_0-\frac F2R\left(1-\cos\phi\right).
$$

The ring is quarter-symmetric, so with $ds=R\,d\phi$,

$$
U=4\int_0^{\pi/2}\frac{M^2}{2EI}R\,d\phi .
$$

The section at the cut does not rotate:

$$
\frac{\partial U}{\partial M_0}=\frac{4R}{EI}\int_0^{\pi/2}M\,d\phi=0
\quad\Longrightarrow\quad
M_0\frac\pi2=\frac{FR}{2}\left(\frac\pi2-1\right)
\quad\Longrightarrow\quad
M_0=\frac{FR}{2}\left(1-\frac2\pi\right).
$$

Then Castigliano with respect to $F$ (SymPy):

$$
\delta=\frac{\partial U}{\partial F}=\frac{FR^3}{EI}\left(\frac\pi4-\frac2\pi\right)=0.149\frac{FR^3}{EI},
\qquad
k=\frac F\delta=6.72\frac{EI}{R^3}.
$$

Castigliano is used twice, first for the moment, then for the force; the same approach handles any curved beam, and the principles extend to plates, shells and composite structures.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S7 - Strain Energy and Conservation of Energy]]
- Next: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]
- Concepts: [[Principle of Virtual Work]] · [[Unit Load Method]] · [[Castigliano Theorem]] · [[Castigliano Second Theorem]] · [[Complementary Energy]] · [[Maxwell-Betti Reciprocity]]
- The unsymmetrical stress field for energy methods: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]

![[structures_virtual_work_moment_fields.png|720]]

## Sources

- Structures slides SL9 and SL15–SL18 (energy methods, virtual work and Castigliano), with transcripts `SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt` (ll. 240–482), `SESA2028 Lecture 2026-02-11 - SL4 Energy Method. General virtual work.txt`, `SESA2028 Lecture 2026-02-13 - SL5 Energy method. Castigliano.txt` and `SESA2028 Lecture 2026-02-18 - SL6 Energy method. Asymmetric beams.txt`
- Ring and uniform-load results checked with SymPy; Maxwell–Betti reciprocity was not lectured in 2025–26

## Self-study tasks

### Core

- [ ] Derive the unit-load formula for a truss from the three-term external work (2026-02-04, ll. 330–480). → [[#2. The truss: deriving the unit-load formula]]
- [ ] Derive $F=\partial U/\partial u$, $u=\partial C/\partial F$ and Castigliano's second theorem (2026-02-13, ll. 1–300). → [[#4. Castigliano's theorems]]
- [ ] The L-frame, the uniform-load beam and the ring ("try to solve these problems yourself", 2026-02-18, ll. 240–280; detailed solutions on Blackboard). → [[#Worked examples]]
- [ ] Structures tutorial 1 (quarter-circular cantilever, L-shaped cantilever, slope and displacement at B). → [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q3 - L-shaped cantilever|Q3]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q4 - Slope and displacement at B|Q4]]

### Further practice

- [ ] Repeat the ring for a quarter-ring cantilever loaded at its tip (suggested in the lecture, ll. 401–440). → [[#Stiffness of a ring]]

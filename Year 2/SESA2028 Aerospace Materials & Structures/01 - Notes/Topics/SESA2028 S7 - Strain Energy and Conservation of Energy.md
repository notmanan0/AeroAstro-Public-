---
title: "SESA2028 S7 - Strain Energy and Conservation of Energy"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 7
tags: [sesa2028, structures, strain-energy, energy-methods]
date: 2026-10-30
status: lectured
coverage: "SL1 (2026-01-28), SL2 (2026-01-30), SL3 (2026-02-04, ll. 1–240)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
next_topics: ["[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
key_concepts: ["[[Strain Energy]]", "[[Complementary Energy]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL1 Introduction, motivation & Review.pdf", "02 - Sources/Structures Lectures/SL8 - Energy Methods 1 - Conservation of Energy.pdf", "02 - Sources/Structures Lectures/SL14 - EnergyMethods 1 - Strain Energy Review.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-01-28 - SL1 Intro and Energy Methods.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-01-30.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt"]
---

# SESA2028 S7 - Strain Energy and Conservation of Energy

> [!abstract] Summary
> For a structure loaded slowly (quasi-statically), the work done by the external loads equals the strain energy stored in it, $W_e=U$. External work is $\tfrac12F\delta$, $\tfrac12M\theta$ or $\tfrac12T\phi$ for a load rising from zero, and the strain energy is the integral of the energy density $\tfrac12\sigma_{ij}\varepsilon_{ij}$, which for slender members gives $P^2L/2EA$ (axial), $\int M^2/2EI\,dx$ (bending), $T^2L/2GJ$ (torsion) and a shear term. Equating the two gives the deflection under a single load directly, and because energy is a scalar, contributions from every member and every mechanism simply add, which is what makes the method efficient for trusses and frames.

> [!summary]- Exam use: quick path
> - **Use it when:** a structure carries a single load and you want the deflection or rotation at that load, in its direction.
> - **Assumptions:** linear elastic, quasi-static loading (no kinetic energy), small deflections.
> - **Method:** 1. External work $W_e=\tfrac12F\delta$ (or $\tfrac12M\theta$, $\tfrac12T\phi$). 2. Internal forces: member forces $P_i$, or $M(x)$, $T$, $Q$. 3. $U=\sum P_i^2L_i/2E_iA_i+\int M^2/2EI\,dx+\dots$ 4. Set $W_e=U$. 5. Solve for $\delta$.
> - **Common mistakes:** the factor $\tfrac12$ on a load that is not ramped from zero; trying to get a deflection where no load acts (that needs virtual work, [[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]).
> - **Practise:** [[#Worked examples]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q1 - Simply supported beam with a point moment|Tutorial 1 Q1]]

The structures half of SESA2028 opened with why analytical methods still matter (2026-01-28, ll. 1–330). Structural design checks strength, stability (buckling) and stiffness, which also governs vibration. Building and validating a finite-element model of a whole aircraft takes years of iteration with testing; an idealised beam model gives the cross-section, deflection and stresses in days and the physical insight that tells you whether an FE answer makes sense, so industry idealises first and models in detail later. The course covers energy methods, unsymmetrical bending, shear and torsion of thin-walled beams, buckling and continuum mechanics; assessment is 50 % coursework (quizzes at 3 % each, the structures lab 10 %, corrosion 5 %, fatigue 20 %) and 50 % exam.

When you stretch a spring, the work you put in is stored in it and comes back when you let go. A structure is a collection of springs, axial, bending, twisting and shearing, and the energy you put in at the load point is shared among them all. Counting the stored energy of every part and setting it equal to the work done at the load gives the deflection there, without ever tracking how every joint moves.

## 1. Why energy methods

The recap problem at the end of SL1 found the deflection of a two-bar truss by statics and compatibility: member forces by the method of joints, extensions $PL/AE$, then two quadratic equations for the new position of the loaded joint so that both bars fit (2026-01-28, ll. 370–440). With more members that becomes "a nightmare". Energy methods replace the geometry with a scalar balance (2026-01-30, ll. 1–80). Structural analysis uses equilibrium, compatibility (geometric constraints, needed for indeterminate structures) and constitutive laws (Hooke's law); conservation of energy is a fourth tool.

## 2. Conservation of energy

The work done by the external forces equals the strain energy stored (ll. 81–160):

$$
W_e=U .
$$

This holds only for quasi-static loading, applied slowly enough that no kinetic energy is generated; under impact, part of the work becomes kinetic energy and the balance must include it (ll. 156–180).

For a bar under a tensile force $F$, the stress $\sigma_{xx}=F/A$ and strain $\varepsilon_{xx}=u/L$ are uniform. A small element carries force $\sigma_{xx}\,dy\,dz$ through an extension $\varepsilon_{xx}\,dx$ as both rise from zero, so it stores $\tfrac12\sigma_{xx}\varepsilon_{xx}\,dx\,dy\,dz$ and the bar stores

$$
U=\tfrac12\sigma_{xx}\varepsilon_{xx}V=\tfrac12\cdot\frac FA\cdot\frac uL\cdot AL=\tfrac12Fu,
$$

which equals the external work. The strain energy density is $\bar U=\tfrac12\sigma_{xx}\varepsilon_{xx}$ ([[Strain Energy]]).

For a spring, $F=kx$; raising the extension by $dx$ does work $kx\,dx$, so

$$
W=\int_0^xkx\,dx=\tfrac12kx^2 .
$$

A solid is a multi-dimensional spring (ll. 181–240). Summing the products of every stress and strain component,

$$
\bar U=\tfrac12\left(\sigma_{xx}\varepsilon_{xx}+\sigma_{yy}\varepsilon_{yy}+\sigma_{zz}\varepsilon_{zz}+2\sigma_{xy}\varepsilon_{xy}+2\sigma_{yz}\varepsilon_{yz}+2\sigma_{zx}\varepsilon_{zx}\right)=\tfrac12\boldsymbol\sigma:\boldsymbol\varepsilon,
$$

where bold denotes the stress and strain tensors and the colon means multiply matching components and sum. With tensor shear strains the shear terms appear twice; in engineering strains, $\gamma=2\varepsilon$, they are $\tau\gamma$. The total is $U=\int_V\tfrac12\boldsymbol\sigma:\boldsymbol\varepsilon\,dV$, kept inside the integral because the stresses usually vary. Energy is a scalar, so all components and all members simply add.

## 3. External work

For a load ramped from zero to $F$ while its point moves $u$ in its direction (ll. 241–330),

$$
W_e=\int_0^uF\,du=\tfrac12Fu .
$$

Likewise for a moment turning through $\theta$, $W_e=\tfrac12M\theta$, and for a torque twisting through $\phi$, $W_e=\tfrac12T\phi$ (a torque is a couple of forces $F$ at radius $d/2$, each moving $\tfrac d2\,d\phi$).

## 4. Strain energy of slender members

Each loading mode keeps only its own stress component (ll. 321–440).

Axial force $P$: with $\sigma_{xx}=P/A$ and $\varepsilon_{xx}=\sigma_{xx}/E$,

$$
U=\frac{\sigma_{xx}^2}{2E}AL=\frac{P^2L}{2EA}.
$$

Pure shear $\tau$: $U=\int\tau^2/2G\,dV$.

Bending moment $M_z(x)$: $\sigma_{xx}=M_zy/I_z$ varies along the beam, so it cannot come outside the integral (as a student pointed out when asked). Write $dV=dA\,dx$:

$$
U=\int_0^L\int_A\frac{\sigma_{xx}^2}{2E}\,dA\,dx=\int_0^L\frac{M_z^2}{2EI_z^2}\int_Ay^2\,dA\,dx=\int_0^L\frac{M_z^2}{2EI_z}\,dx .
$$

Torsion of a circular shaft, $\tau=Tr/J$:

$$
U=\int_0^L\int_A\frac{\tau^2}{2G}\,dA\,dx=\int_0^L\frac{T^2}{2GJ^2}\int_Ar^2\,dA\,dx=\frac{T^2L}{2GJ},
$$

valid as written only for circular sections; for thin-walled sections use the $J$ of [[SESA2028 S4 - Torsion of Thin-Walled Sections|S4]]. Equating $\tfrac12T\phi=T^2L/2GJ$ recovers $\phi=TL/GJ$ (ll. 441–450).

## 5. Deflection of a truss in the load direction

For a truss with a single load $F$, the member forces $P_i$ come from the method of joints or sections, and each member stores $\tfrac12P_i\delta_i=P_i^2L_i/2E_iA_i$ (2026-02-04, ll. 161–240). So

$$
\tfrac12Fu=\sum_{i=1}^n\frac{P_i^2L_i}{2E_iA_i},
$$

giving the displacement of the loaded joint in the load's direction without solving any quadratics; keep tension positive and compression negative consistently (the square removes the sign here). What this cannot give is the displacement in a direction where no load acts, the horizontal movement of the joint under a vertical load, because no external work is done in that direction. That gap leads to virtual work ([[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]; ll. 200–240).

## Worked examples

### Rotation and deflection of beams

SL3 opened with three examples (2026-02-04, ll. 1–160). A cantilever of length $L$ has a moment $M$ at its free end, so $M_z=M$ everywhere:

$$
\tfrac12M\theta=\int_0^L\frac{M^2}{2EI}\,dx=\frac{M^2L}{2EI}
\quad\Longrightarrow\quad
\theta=\frac{ML}{EI}.
$$

A simply supported beam with a central load $F$ has $M=Fx/2$ on each half, so the integral is taken in two halves:

$$
\tfrac12Fv=2\int_0^{L/2}\frac{(Fx/2)^2}{2EI}\,dx=\frac{F^2}{4EI}\cdot\frac{(L/2)^3}{3}=\frac{F^2L^3}{96EI}
\quad\Longrightarrow\quad
v=\frac{FL^3}{48EI}.
$$

### Shear deflection of a cantilever

The transverse deflection of a tip-loaded cantilever of rectangular section $b\times h$ has a bending part, $FL^3/3EI$ by the same method, and a shear part (ll. 41–165). The shear force is $F$ along the whole beam, and the shear stress over the depth is parabolic ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]):

$$
\tau=\frac{F}{2I}\left(\frac{h^2}{4}-y^2\right).
$$

The shear strain energy splits into three integrals:

$$
U_s=\int\frac{\tau^2}{2G}\,dV=\frac{F^2}{8GI^2}\int_0^Ldx\int_{-b/2}^{b/2}dz\int_{-h/2}^{h/2}\left(\frac{h^2}{4}-y^2\right)^2dy=\frac{F^2Lb}{8GI^2}\cdot\frac{h^5}{30}.
$$

With $I=bh^3/12$, $I^2=b^2h^6/144$:

$$
U_s=\frac{144F^2Lbh^5}{240\,Gb^2h^6}=\frac{0.6F^2L}{Gbh}.
$$

Equate to $\tfrac12Fv_s$:

$$
v_s=\frac{1.2FL}{GA}=\frac65\frac{FL}{GA}.
$$

The ratio to the bending deflection is $v_s/v_b=0.3(E/G)(h/L)^2$; with $E/G=2.6$ and $L=10h$ it is under 1 %, which is why slender beams neglect shear.

> [!warning] Slide typo (2026-02-04, ll. 141–165)
> A student spotted that the slide's coefficient in the shear-energy integral should be 4, not 8; the lecturer agreed it is a typo and would re-upload the slides.

### Choosing a bumper material

SL2's closing problem (2026-01-30, ll. 451–480): a bumper must absorb the kinetic energy of a 2 m/s collision, a low-velocity, quasi-static impact, and spring back without permanent deformation; which of three materials is cheapest? The energy a volume $V$ can store elastically is

$$
U=\tfrac12\sigma_Y\frac{\sigma_Y}{E}V=\frac{\sigma_Y^2}{2E}V,
$$

so the volume needed for an energy $U$ is $V=2EU/\sigma_Y^2$, and the cost, at $c$ per kilogram, is

$$
C=c\rho V=\frac{2c\rho E}{\sigma_Y^2}\,U .
$$

The best material minimises $c\rho E/\sigma_Y^2$, which combines the table's yield strength, modulus, density and relative cost (the slide's values are not reproduced in the transcript).

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]
- Next: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
- Concepts: [[Strain Energy]] · [[Complementary Energy]]
- The same principle in FEA: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]

![[structures_bending_strain_energy_density.png|700]]

## Sources

- Structures slides `SL1 Introduction, motivation & Review.pdf`, `SL8 - Energy Methods 1 - Conservation of Energy.pdf` and `SL14 - EnergyMethods 1 - Strain Energy Review.pdf`, with transcripts `SESA2028 Lecture 2026-01-28 - SL1 Intro and Energy Methods.txt`, `SESA2028 Lecture 2026-01-30.txt` and `SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt` (ll. 1–240)
- Shear-deflection integral checked symbolically

## Self-study tasks

### Core

- [ ] Derive the strain energy of a bar, a beam in bending and a circular shaft in torsion (2026-01-30, ll. 321–450). → [[#4. Strain energy of slender members]]
- [ ] The three beam examples, including the shear deflection with the corrected coefficient (2026-02-04, ll. 1–165). → [[#Worked examples]]
- [ ] The bumper material selection (2026-01-30, ll. 451–480). → [[#Choosing a bumper material]]
- [ ] Structures tutorial 1, energy methods. → [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q1 - Simply supported beam with a point moment|Q1]]

### Further practice

- [ ] Solve SL1's two-bar truss by compatibility, then again by energy for the vertical deflection, and compare the effort (2026-01-28, ll. 370–440; 2026-02-04, ll. 200–240). → [[#5. Deflection of a truss in the load direction]]
- [ ] The offset crank: safety factor against yield under combined bending and torsion (SL1, ll. 420–445, solution on Blackboard).

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
> For a structure loaded slowly (quasi-statically), the work done by the external loads equals the strain energy stored in it, $W_e=U$. External work is $\tfrac12F\delta$, $\tfrac12M\theta$ or $\tfrac12T\phi$ for a load rising from zero, and the strain energy is the volume integral of the energy density $\tfrac12\boldsymbol\sigma:\boldsymbol\varepsilon$, which for slender members becomes $P^2L/2EA$ (axial), $\int M^2/2EI\,dx$ (bending), $T^2L/2GJ$ (torsion) and $\int\tau^2/2G\,dV$ (shear). Equating the two gives the deflection under a single load, in its direction, and because energy is a scalar the contributions of every member and every mechanism add.

> [!summary]- Exam use: quick path
> - **Use it when:** a structure carries a single load and you want the deflection or rotation at that load, in its direction; or you need the energy a component can absorb elastically.
> - **Assumptions:** linear elastic, quasi-static loading (no kinetic energy), small deflections; shear energy neglected in slender beams unless asked for.
> - **Method:** 1. External work $W_e=\tfrac12F\delta$ (or $\tfrac12M\theta$, $\tfrac12T\phi$). 2. Internal forces: member forces $P_i$, or $M(x)$, $T$, $Q$, segment by segment. 3. $U=\sum P_i^2L_i/2E_iA_i+\int M^2/2EI\,dx+\dots$ 4. Set $W_e=U$. 5. Solve for $\delta$.
> - **Common mistakes:** dropping the $\tfrac12$ on a load ramped from zero; trying to get a deflection where no load acts, which needs virtual work ([[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]).
> - **Practise:** [[#Shear deflection of a cantilever]] · [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q1 - Simply supported beam with a point moment|Tutorial 1 Q1]]

Structural design checks strength, stability (buckling) and stiffness, which also governs vibration. A finite-element model of a whole aircraft takes years of iteration with testing, whereas an idealised beam model gives the cross-section, deflections and stresses in days, together with the physical insight that tells you whether a later FE answer makes sense. So industry idealises first and models in detail later. The idealised methods are energy methods, unsymmetrical bending, shear and torsion of thin-walled beams, buckling, and continuum mechanics in cylindrical coordinates.

Every structural problem is solved with three tools: equilibrium (free-body diagrams give the internal forces), geometric compatibility (the deformed pieces must still fit together) and the constitutive law (Hooke's law turns stress into strain). For a truss of two bars this already means two quadratic equations for the new position of the loaded joint; for a truss of ten bars it is hours of algebra. Conservation of energy is a fourth tool that sidesteps the geometry.

The work done in stretching a spring is stored in it and comes back on release. A structure is a collection of springs, axial, bending, twisting and shearing, and the work done at the load point is shared among all of them. Counting the energy stored in every part and setting it equal to the work done at the load gives the deflection there, without tracking how every joint moves.

## 1. Conservation of energy

The work done by the external forces equals the elastic strain energy stored in the structure:

$$
W_e=U .
$$

When the load is removed the structure springs back to its undeformed state, releasing the stored energy. The balance holds only for quasi-static loading, applied slowly enough that no kinetic energy is generated. Under impact, or a load suddenly applied at full value, part of the work becomes kinetic energy and the balance must include it.

### Spring and bar

For a linear spring, $F=kx$. Raising the extension from $x$ to $x+dx$ does work

$$
dW=F\,dx=kx\,dx .
$$

The total work is the area under the force–extension line:

$$
W=\int_0^xkx\,dx=\tfrac12kx^2=\tfrac12Fx .
$$

A bar of length $L$, area $A$ and modulus $E$ is a spring with $k=EA/L$, since $u=FL/EA$. Integrating the work as the load rises,

$$
W=\int_0^uF\,du=\int_0^u\frac{AE}{L}u\,du=\frac{AE}{L}\frac{u^2}{2}=\frac12\left(\frac{AEu}{L}\right)u=\tfrac12Fu .
$$

The same result holds for a point force acting anywhere on a linear elastic structure, with $k$ the structure's stiffness at that point, so $W=\int_0^\delta k\delta\,d\delta=\tfrac12F\delta$ whenever the force is ramped from zero.

### Strain energy in three dimensions

Inside the bar, stress and strain are uniform: $\sigma_{xx}=F/A$ and $\varepsilon_{xx}=u/L$. A small element $dx\,dy\,dz$ carries the force $\sigma_{xx}\,dy\,dz$ through the extension $\varepsilon_{xx}\,dx$, both rising from zero, so it stores $\tfrac12\sigma_{xx}\varepsilon_{xx}\,dx\,dy\,dz$. Over the whole bar:

$$
U=\tfrac12\sigma_{xx}\varepsilon_{xx}V=\tfrac12\cdot\frac FA\cdot\frac uL\cdot AL=\tfrac12Fu=W .
$$

A solid is a multi-dimensional spring: Hooke's law in 3D links every stress component to the strains. Over a small volume $dv$, where stress and strain can be taken as constant, the stored energy is the sum of the products of each stress component and its matching strain:

$$
dU=\tfrac12\left(\sigma_{xx}\varepsilon_{xx}+\sigma_{yy}\varepsilon_{yy}+\sigma_{zz}\varepsilon_{zz}+2\sigma_{xy}\varepsilon_{xy}+2\sigma_{xz}\varepsilon_{xz}+2\sigma_{yz}\varepsilon_{yz}\right)dv=\tfrac12\boldsymbol\sigma:\boldsymbol\varepsilon\,dv .
$$

The colon means multiply matching components and sum. The shear terms appear twice because the tensor shear strains $\varepsilon_{xy}=\varepsilon_{yx}$ both contribute; in engineering shear strain, $\gamma_{xy}=2\varepsilon_{xy}$, they become $\sigma_{xy}\gamma_{xy}$. Integrating over the body,

$$
U=\frac12\int_V\left(\sigma_{xx}\varepsilon_{xx}+\sigma_{yy}\varepsilon_{yy}+\sigma_{zz}\varepsilon_{zz}+\sigma_{xy}\gamma_{xy}+\sigma_{xz}\gamma_{xz}+\sigma_{yz}\gamma_{yz}\right)dv .
$$

The stresses usually vary through the body, so they stay inside the integral. The energy per unit volume is the **strain energy density** ([[Strain Energy]]),

$$
U_\rho=\frac UV=\tfrac12\boldsymbol\sigma:\boldsymbol\varepsilon ,
$$

with units of J/m³. Since 1 MPa $=10^6$ N/m² $=10^6$ J/m³, stresses in MPa give $U_\rho$ in MJ/m³, and $U$ in MPa·m³ is in megajoules ($1\ \text{MPa·m}^3=10^6$ J). Energy is a scalar, so all components and all members add, which is what makes the method efficient.

## 2. External work of forces and moments

A force ramped from zero to $F$ while its point moves $u$ in its direction does work

$$
W_e=\int_0^uF\,du=\tfrac12Fu .
$$

A moment $M$ can be replaced by a couple, two forces $F$ a distance $d$ apart with $M=Fd$. When the couple turns through a small angle $d\theta$, each force moves $\tfrac d2\,d\theta$, so

$$
dW=2F\frac d2\,d\theta=Fd\,d\theta=M\,d\theta .
$$

For a linear elastic structure, where $M$ rises in proportion to $\theta$,

$$
W_e=\int_0^\theta M\,d\theta=\tfrac12M\theta ,
$$

and a torque twisting through $\phi$ does $W_e=\tfrac12T\phi$ by the same argument.

## 3. Strain energy of slender members

The method is the same in every case: keep only the stress components the loading produces, substitute Hooke's law, and split the volume integral into an integral over the section and an integral along the length.

### Axial force

With uniaxial stress only $\sigma_{xx}\varepsilon_{xx}$ survives, and $\sigma_{xx}=P/A$ is constant:

$$
U=\frac12\int_V\sigma_{xx}\varepsilon_{xx}\,dv=\frac12\sigma_{xx}\varepsilon_{xx}V .
$$

Substitute $\varepsilon_{xx}=\sigma_{xx}/E$ and $V=AL$:

$$
U=\frac{\sigma_{xx}^2}{2E}AL=\frac{P^2}{2EA^2}AL=\frac{P^2L}{2EA}.
$$

### Pure shear

With only $\sigma_{xy}$ and $\gamma_{xy}$, and $\sigma_{xy}=G\gamma_{xy}$:

$$
U=\frac12\int_V\sigma_{xy}\gamma_{xy}\,dv=\int_V\frac{\tau^2}{2G}\,dv ,
$$

which is $\tau^2V/2G=\tfrac12G\gamma^2V$ when the shear stress is uniform.

### Bending

The bending stress varies over the section and, through $M_z(x)$, along the beam, so it cannot come outside the integral:

$$
U=\frac12\int_V\sigma_{xx}\varepsilon_{xx}\,dv=\frac12\int_V\frac{\sigma_{xx}^2}{E}\,dv .
$$

Substitute $\sigma_{xx}=M_zy/I_{zz}$:

$$
U=\frac12\int_V\frac{M_z^2y^2}{EI_{zz}^2}\,dv .
$$

Split $dv=dA\,dx$. At a given $x$, $M_z$, $E$ and $I_{zz}$ are constant over the section:

$$
U=\frac12\int_0^L\frac{M_z^2}{EI_{zz}^2}\left(\int_Ay^2\,dA\right)dx .
$$

The bracket is $I_{zz}$:

$$
\boxed{U=\int_0^L\frac{M_z^2}{2EI_{zz}}\,dx}
$$

This cannot be simplified further because $M_z$ depends on $x$: find $M_z(x)$ from a free body cut at $x$ and integrate, segment by segment.

### Torsion of a circular shaft

The shear stress is $\tau=Tr/J$, and $\tau=G\gamma$:

$$
U=\frac12\int_V\tau\gamma\,dv=\frac12\int_V\frac{\tau^2}{G}\,dv=\frac12\int_0^L\int_A\frac{T^2r^2}{GJ^2}\,dA\,dx .
$$

For a uniform shaft under a constant torque, nothing depends on $x$:

$$
U=\frac{T^2}{2GJ^2}\int_0^Ldx\int_Ar^2\,dA=\frac{T^2}{2GJ^2}\cdot L\cdot J=\frac{T^2L}{2GJ}.
$$

This holds as written only for circular sections, for which $J=\int r^2\,dA$ is the polar second moment of area; thin-walled sections use the torsion constant of [[SESA2028 S4 - Torsion of Thin-Walled Sections|S4]]. Equating to the external work recovers the familiar twist:

$$
\tfrac12T\phi=\frac{T^2L}{2GJ}\quad\Longrightarrow\quad\phi=\frac{TL}{GJ}.
$$

![[structures_bending_strain_energy_density.png|700]]

The bending energy density goes as $M^2$, so the energy is concentrated where the moment is largest, near the support of a cantilever or under the load of a simply supported beam.

## 4. Deflection of a truss in the load direction

For a truss with a single load $F$, the member forces $P_i$ come from the method of joints or sections, and each member stores $\tfrac12P_i\Delta_i=P_i^2L_i/2E_iA_i$. Equating the external work to the total strain energy:

$$
\tfrac12Fu=\sum_{i=1}^n\frac{P_i^2L_i}{2E_iA_i}\quad\Longleftrightarrow\quad Fu=\sum_{i=1}^nP_i\Delta_i .
$$

This gives the displacement of the loaded joint, in the load's direction, with no quadratics. Keep tension positive and compression negative consistently: the square removes the sign here, but it matters as soon as two load cases are combined. For the three-bay truss of [[SESA2028 S8 - Virtual Work and Castigliano Theorems#Example: the three-bay truss|S8]] (10 kN at D, every member 1000 mm² and 200 GPa), $\sum P_i\Delta_i=12.66$ kN·mm, so $v_D=12.66/10=1.27$ mm.

What this cannot give is the displacement in a direction where no load acts, such as the horizontal movement of that joint under its vertical load, because no external work is done in that direction. And with two or more loads, the left-hand side contains several unknown displacements but there is only one equation. A dummy unit load, as in virtual work ([[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]]), removes both limits.

## Worked examples

### Rotation of a cantilever under an end moment

A cantilever of length $L$ carries a moment $M$ at its free end, so $M_z=M$ everywhere. Equate the external work to the bending energy:

$$
\tfrac12M\theta=\int_0^L\frac{M^2}{2EI}\,dx=\frac{M^2L}{2EI}.
$$

Divide by $\tfrac12M$:

$$
\theta=\frac{ML}{EI}.
$$

### Central load on a simply supported beam

A beam of span $L$ carries $F$ at midspan. Each reaction is $F/2$, so measuring $x$ from either support, $M=Fx/2$ on each half. The two halves store equal energy:

$$
U=2\int_0^{L/2}\frac{(Fx/2)^2}{2EI}\,dx=\frac{F^2}{4EI}\int_0^{L/2}x^2\,dx .
$$

Integrate:

$$
U=\frac{F^2}{4EI}\cdot\frac{(L/2)^3}{3}=\frac{F^2L^3}{96EI}.
$$

Equate to the external work and solve:

$$
\tfrac12Fv=\frac{F^2L^3}{96EI}\quad\Longrightarrow\quad v=\frac{FL^3}{48EI}.
$$

### Shear deflection of a cantilever

A cantilever of rectangular section $b\times h$ and length $L$ carries $F$ at its tip. Show that the bending deflection is $FL^3/3EI$, the shear deflection is $6FL/5bhG$, and the total is their sum.

The bending part is the bending energy of section 3 with $M=-Fx$ measured from the tip:

$$
\tfrac12Fv_b=\int_0^L\frac{F^2x^2}{2EI}\,dx=\frac{F^2L^3}{6EI}\quad\Longrightarrow\quad v_b=\frac{FL^3}{3EI}.
$$

For the shear part, the shear force is $F$ along the whole beam, and over the depth the shear stress is parabolic ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]), zero at the free top and bottom faces:

$$
\tau(y)=\frac{F}{2I}\left(\frac{h^2}{4}-y^2\right).
$$

![[structures_s7_shear_deflection.png|900]]

The shear strain energy is

$$
U_s=\int_V\frac{\tau^2}{2G}\,dV=\frac{F^2}{8GI^2}\int_0^Ldx\int_{-b/2}^{b/2}dz\int_{-h/2}^{h/2}\left(\frac{h^2}{4}-y^2\right)^2dy .
$$

The first two integrals give $L$ and $b$. For the third, expand the square:

$$
\int_{-h/2}^{h/2}\left(\frac{h^4}{16}-\frac{h^2y^2}{2}+y^4\right)dy=\frac{h^5}{16}-\frac{h^2}{2}\cdot\frac{h^3}{12}+\frac{h^5}{80}=h^5\left(\frac{15-10+3}{240}\right)=\frac{h^5}{30}.
$$

So

$$
U_s=\frac{F^2Lb}{8GI^2}\cdot\frac{h^5}{30}=\frac{F^2Lbh^5}{240\,GI^2}.
$$

Substitute $I=bh^3/12$, so $I^2=b^2h^6/144$:

$$
U_s=\frac{144F^2Lbh^5}{240\,Gb^2h^6}=\frac{0.6\,F^2L}{Gbh}.
$$

Equate to the external work of the shear deflection, $\tfrac12Fv_s$:

$$
v_s=\frac{1.2\,FL}{Gbh}=\frac65\frac{FL}{GA}.
$$

Bending and shear energies add, so

$$
v_{total}=\frac{FL^3}{3EI}+\frac{6FL}{5bhG}.
$$

> [!check] When does shear matter?
> The ratio is $v_s/v_b=\dfrac{1.2FL}{Gbh}\cdot\dfrac{Ebh^3}{4FL^3}=0.3\dfrac EG\left(\dfrac hL\right)^2$. For a metal, $E/G=2(1+\nu)=2.6$, and at $L=10h$ the ratio is $0.3\times2.6\times0.01=0.78\,\%$; at $L=3h$ it is still under 9 %. That is why slender beams neglect shear and use the Euler–Bernoulli model.

The factor $6/5$ comes from the parabolic stress: the same shear force spread uniformly over the section would store less energy, because the energy goes as $\tau^2$ and the parabola concentrates stress at mid-depth.

### Choosing a bumper material

A car bumper must absorb the kinetic energy of a 2 m/s collision and spring back without permanent deformation. Which material is the most cost-effective?

| Material | $\sigma_y$ (MPa) | $E$ (GPa) | $\rho$ (kg/m³) | Relative cost/kg |
|---|---|---|---|---|
| Mild steel | 200 | 200 | 7800 | 1.0 |
| Polypropylene | 50 | 1.2 | 910 | 1.25 |
| Nylon | 75 | 2 | 1150 | 5.0 |

A low-speed impact can be treated as quasi-static, so the kinetic energy $U$ must be stored as elastic strain energy without the stress exceeding yield. At yield the energy density is

$$
U_\rho=\tfrac12\sigma_y\varepsilon_y=\tfrac12\sigma_y\frac{\sigma_y}{E}=\frac{\sigma_y^2}{2E},
$$

so the volume needed is

$$
V=\frac{U}{U_\rho}=\frac{2EU}{\sigma_y^2}.
$$

At relative cost $c$ per kilogram, the cost is

$$
C=c\rho V=\frac{2c\rho E}{\sigma_y^2}\,U .
$$

The energy $U$ is fixed by the car, so the best material minimises the index $c\rho E/\sigma_y^2$. With $E$ in MPa:

| Material | $\sigma_y^2/2E$ (MJ/m³) | $c\rho E/\sigma_y^2$ |
|---|---|---|
| Mild steel | 0.10 | 39 000 |
| Polypropylene | 1.04 | 546 |
| Nylon | 1.41 | 2 040 |

Polypropylene is the cheapest by a factor of 3.7 over nylon and 71 over steel. Nylon stores the most energy per unit volume, but it costs four times as much per kilogram; steel is cheap per kilogram but its high stiffness means it stores ten times less energy per unit volume before yielding.

![[structures_s7_bumper_selection.png|860]]

> [!tip] Stiff is not the same as good at absorbing energy
> For a given yield stress, a stiffer material reaches yield at a smaller strain and so stores less energy. Energy absorption rewards a high $\sigma_y^2/E$, the opposite of what a stiffness-limited design wants.

### Offset crank: combined bending and torsion

An offset crank in a gas-turbine control system is a hollow titanium shaft ABC (outer diameter 10 mm, wall 1 mm, so inner diameter 8 mm) joined at C to a rigid link CD of 10 mm offset. A vertical load of 500 N acts at D. Bearings at A and B, 20 mm apart, act as simple supports, and C is a further 20 mm beyond B; A is restrained against rotation about the shaft axis. With $\sigma_y=800$ MPa, what is the safety factor against yield (Tresca)?

The load at D is 10 mm off the shaft axis, so moving it onto the axis at C adds a torque $T=500\times10=5000$ N·mm, carried from C back to the restraint at A. The vertical 500 N at C, 20 mm beyond B, makes the shaft an overhanging beam. Taking moments about A gives $R_B=1000$ N up and $R_A=500$ N down, and the largest bending moment is at B:

$$
M_B=500\times20=10\,000\text{ N·mm}.
$$

The section properties are

$$
I=\frac{\pi}{64}\left(10^4-8^4\right)=289.8\text{ mm}^4,\qquad J=2I=579.6\text{ mm}^4 .
$$

At the top or bottom of the shaft at B ($r=5$ mm), the bending and torsional stresses are

$$
\sigma=\frac{M_By}{I}=\frac{10\,000\times5}{289.8}=172.5\text{ MPa},\qquad\tau=\frac{Tr}{J}=\frac{5000\times5}{579.6}=43.1\text{ MPa}.
$$

The principal stresses are

$$
\sigma_{1,2}=\frac\sigma2\pm\sqrt{\left(\frac\sigma2\right)^2+\tau^2}=86.3\pm96.4=182.7,\ -10.2\text{ MPa}.
$$

Tresca compares the greatest difference of principal stresses with $\sigma_y$:

$$
n=\frac{\sigma_y}{\sigma_1-\sigma_2}=\frac{800}{192.9}=4.1 .
$$

Von Mises, $n=\sigma_y/\sqrt{\sigma^2+3\tau^2}=800/188.0=4.3$, is slightly less conservative.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]] · Next: [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]
- Concepts: [[Strain Energy]] · [[Complementary Energy]]
- Problems: [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- The same principle in finite elements: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]

## Sources

- Slides: `SL1 Introduction, motivation & Review.pdf` (course scope, statics review, offset crank), `SL8 - Energy Methods 1 - Conservation of Energy.pdf` and `SL14 - EnergyMethods 1 - Strain Energy Review.pdf` (work, strain energy, examples 1–4 including the bumper).
- Transcripts: `SESA2028 Lecture 2026-01-28 - SL1 Intro and Energy Methods.txt`, `SESA2028 Lecture 2026-01-30.txt` (SL2) and `SESA2028 Lecture 2026-02-04 - SL3 Energy Method. Virtual work.txt` (ll. 1–240).
- The shear-energy integral was checked symbolically (SymPy); the bumper indices and the crank stresses were recomputed in Python. Figures: `generate_structures_s7_figures.py` and `generate_structures_figures.py` (energy density).

## Self-study tasks

### Core

- [ ] Derive the strain energy of a bar, a beam in bending and a circular shaft in torsion (2026-01-30, ll. 321–450). → [[#3. Strain energy of slender members]]
- [ ] SL8 examples 2–4: end-moment rotation, central-load deflection and the shear deflection, with the corrected coefficient (SL3, 2026-02-04, ll. 1–165). → [[#Rotation of a cantilever under an end moment]] · [[#Central load on a simply supported beam]] · [[#Shear deflection of a cantilever]]
- [ ] SL8 example 1, the bumper material (2026-01-30, ll. 451–480). → [[#Choosing a bumper material]]
- [ ] Structures tutorial 1, Q1. → [[SESA2028 Structures Tutorial 1 - Energy Methods Solutions#Q1 - Simply supported beam with a point moment|Q1]]

### Further practice

- [ ] The offset crank: safety factor against yield under combined bending and torsion; full solution on Blackboard (SL1, 2026-01-28, ll. 420–445). → [[#Offset crank: combined bending and torsion]]
- [ ] Solve SL1's two-bar truss by compatibility (two quadratics for the loaded joint), then by energy for the vertical deflection, and compare the effort (2026-01-28, ll. 376–425). → [[#4. Deflection of a truss in the load direction]]

## Transcript and slide slips

> [!warning] Slide typo: shear-energy coefficient (2026-02-04, ll. 141–165)
> Where: [[#Shear deflection of a cantilever]].
>
> The coefficient printed in the shear-energy integral was 8 where it should be 4; the slip was confirmed in the lecture and the slides were to be re-uploaded. The working above carries the factor through from $\tau^2/2G$ with $\tau=F(h^2/4-y^2)/2I$.

> [!warning] Slide slip: crank diameters (SL1 slide 35)
> Where: [[#Offset crank: combined bending and torsion]].
>
> The text gives "inner and outer diameters 10.0 mm and 8.0 mm respectively"; the drawing (OD 10.0 mm, wall 1.0 mm) shows these are the outer and inner diameters.

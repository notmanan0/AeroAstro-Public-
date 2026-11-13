---
title: "SESA2029 B5 - Euler-Bernoulli Beam Element"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 16
tags: [sesa2029, fea, beam-element]
aliases: ["Beam FE formulation", "Beam stiffness matrix", "Hermite beam element", "FEA Lecture 7"]
date: 2026-10-30
status: lectured
coverage: "FEA week 4 (2026-02-20 09:59)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]"]
next_topics: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
key_concepts: ["[[Euler-Bernoulli Beam Element]]", "[[Shape Functions]]", "[[Global Stiffness Matrix Assembly]]", "[[Boundary Conditions and Rigid Body Modes]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-20 - 0959.txt"]
---

# SESA2029 B5 - Euler-Bernoulli Beam Element

> [!abstract] Summary
> Long, slender aerospace structures are modelled with beam elements, which carry bending. Engineer's bending theory, $M/I=\sigma/y=E/R$, turns the strain energy into $U=\tfrac12\int EI\rho^2\,dx$ with curvature $\rho=d^2v/dx^2$. A two-node beam has a deflection and a rotation at each node, four unknowns, so its displacement is a cubic polynomial; differentiating the cubic shape functions twice and applying minimum potential energy gives the $4\times4$ beam stiffness matrix. The matrix is given in the exam; assembling it for a multi-element beam and applying the boundary conditions is the skill to practise.

> [!summary]- Exam use: quick path
> - **Use it when:** a beam problem asks for element matrices, the global equilibrium equation, or the reduced system after boundary conditions.
> - **Assumptions:** Euler–Bernoulli (plane sections remain plane, no shear deformation), long slender beam, small deflections, nodes at supports and loads.
> - **Method:** 1. Put nodes at ends, supports and point loads. 2. Write each $[K]^e=\frac{EI}{L^3}[\dots]$ with DOF order $(v_1,\theta_1,v_2,\theta_2)$. 3. Overlap the element blocks at shared nodes in the global matrix. 4. Clamp: $v=\theta=0$; simple support: $v=0$ only. 5. Strike out the constrained rows and columns, solve, back-substitute for reactions.
> - **Common mistakes:** ordering the forces as $(F_1,F_2,M_1,M_2)$ against a matrix built for $(F_1,M_1,F_2,M_2)$; fixing the rotation at a simple support.
> - **Practise:** [[#Worked example: a propped cantilever with an overhang]] · [[SESA2029 FEA Worked Examples]]

The matrix displacement and minimum-potential-energy methods are applied here to the beam (2026-02-20 09:59).

A ruler bent between the hands has its outside fibres stretched and its inside fibres shortened, in proportion to the distance from the middle and to how sharply it is bent. All the stored energy is in that bending, so the beam's energy depends only on its curvature. A short beam element can bend into a gentle S-shape, which a straight line cannot describe; that is why it needs a cubic, and why each node needs a slope as well as a deflection so that neighbouring elements join smoothly.

## 1. Beams in aerospace

Wings, fuselages and space trusses are long and thin, with high aspect ratios, and they are thin-walled because weight matters. Both beam and shell elements include bending in their formulation; a bar element only stretches. A beam element is a line between two (or three) nodes, with the cross-section described by constants such as the second moments of area about two axes, so any section can be represented, including one that varies along a wing's span; lab 1 chose among standard sections. Shell elements describe a curved surface with thickness at the nodes and are covered in [[SESA2029 B6 - 2D and 3D Elements|B6]].

Beam theory assumes plane sections remain plane, which requires a high aspect ratio. In a low-aspect-ratio structure such as a fan blade, shear and bending are coupled, and plate or solid models are needed.

## 2. Bending theory and the beam's strain energy

Engineer's bending theory applies to long, slender beams of linear elastic material. Plane sections remain plane and perpendicular to the neutral axis, so the beam deforms into a circular arc of radius $R$. The only strain is axial, varying linearly from the surfaces to zero at the neutral axis, and so is the only stress. Equilibrium, compatibility and the constitutive law combine into

$$
\frac MI=\frac\sigma y=\frac ER,
$$

This is the relation to remember for estimating the deflection and stress of a wing or a bridge.

The beam element neglects shear strain from the shear force, consistent with plane sections staying perpendicular to the axis, so only bending stresses and strains store energy. The strain energy is the energy density integrated over the volume, which here means over the cross-section and along the length:

$$
U=\int_0^L\int_A\tfrac12\sigma\varepsilon\,dA\,dx .
$$

The bending theory simplifies the inner integral. The curvature is the reciprocal of the radius, and for small slopes it is the second derivative of the deflection:

$$
\rho=\frac1R=\frac{d^2v}{dx^2}.
$$

From $M/I=E/R$, the moment–curvature relation is

$$
M=EI\rho .
$$

The moment on a section is the stress times the area times the lever arm, integrated over the section:

$$
M=\int_A\sigma y\,dA .
$$

The strain at height $y$ is $\varepsilon=y/R=y\rho$, so $y=\varepsilon/\rho$. Substitute:

$$
M=\int_A\sigma\frac{\varepsilon}{\rho}\,dA
\quad\Longrightarrow\quad
M\rho=\int_A\sigma\varepsilon\,dA .
$$

The section integral in $U$ is therefore $M\rho$:

$$
U=\frac12\int_0^LM\rho\,dx .
$$

Replace $M$ by $EI\rho$:

$$
U=\frac12\int_0^LEI\rho^2\,dx .
$$

The strain energy now depends only on $E$, $I$ and the curvature along the beam.

## 3. Degrees of freedom and cubic shape functions

The beam element lies along $x$ with deflection $v$ in $y$. Each node is loaded by a shear force $F$ and a bending moment $M$, and has two DOF: the transverse deflection $v$ and the rotation

$$
\theta=\frac{dv}{dx}.
$$

There is no axial DOF in this element; adding one per node turns it into a frame element, with a $3\times3$ block per node instead of $2\times2$. The rotational DOF are what distinguish beams (and plates and shells) from bars and solids, whose nodes have only translations: a solid represents rotation through the relative movement of several nodes. The element displacement vector is

$$
\{d\}=\{v_1\ \ \theta_1\ \ v_2\ \ \theta_2\}^T .
$$

Four unknowns call for a polynomial with four coefficients, a cubic:

$$
v=a+bx+cx^2+dx^3,
\qquad
\theta=b+2cx+3dx^2 .
$$

The generalised boundary conditions at $x=0$ are $v=v_1$ and $\theta=\theta_1$, which give at once

$$
a=v_1,
\qquad
b=\theta_1 .
$$

At $x=L$, $v=v_2$ and $\theta=\theta_2$:

$$
v_2=v_1+\theta_1L+cL^2+dL^3,
\qquad
\theta_2=\theta_1+2cL+3dL^2 .
$$

Multiply the first by $3/L$ and subtract the second to eliminate $d$:

$$
\frac{3v_2}{L}-\theta_2=\frac{3v_1}{L}+2\theta_1+cL
\quad\Longrightarrow\quad
c=\frac{3(v_2-v_1)}{L^2}-\frac{2\theta_1+\theta_2}{L}.
$$

Multiply the first by $2/L$ and subtract the second to eliminate $c$:

$$
\frac{2v_2}{L}-\theta_2=\frac{2v_1}{L}+\theta_1-dL^2
\quad\Longrightarrow\quad
d=\frac{2(v_1-v_2)}{L^3}+\frac{\theta_1+\theta_2}{L^2}.
$$

Substitute $a$, $b$, $c$, $d$ into $v=a+bx+cx^2+dx^3$:

$$
v=v_1+\theta_1x+\left[\frac{3(v_2-v_1)}{L^2}-\frac{2\theta_1+\theta_2}{L}\right]x^2+\left[\frac{2(v_1-v_2)}{L^3}+\frac{\theta_1+\theta_2}{L^2}\right]x^3.
$$

Collect the terms multiplying each nodal DOF. For $v_1$: $1-3x^2/L^2+2x^3/L^3$. For $\theta_1$: $x-2x^2/L+x^3/L^2$. For $v_2$: $3x^2/L^2-2x^3/L^3$. For $\theta_2$: $-x^2/L+x^3/L^2$. Writing $\xi=x/L$, this is $v=[N]\{d\}$ with

$$
N_1=1-3\xi^2+2\xi^3,
\qquad
N_2=L\left(\xi-2\xi^2+\xi^3\right),
$$

$$
N_3=3\xi^2-2\xi^3,
\qquad
N_4=L\left(-\xi^2+\xi^3\right).
$$

![[dam_beam_hermite_shape_functions.png|900]]

The shape functions are the basic deformations of the beam: each is the deflected shape when its own DOF is one and the other three are zero. $N_1$ and $N_3$ carry unit deflections with zero end slopes; $N_2$ and $N_4$ carry unit slopes with zero end deflections. These cubic Hermite functions are specific to this beam element; other elements have their own.

## 4. The stiffness matrix by minimum potential energy

Differentiate $v=[N]\{d\}$ twice to get the curvature:

$$
\rho=\frac{d^2v}{dx^2}=\frac{d^2[N]}{dx^2}\{d\}=[B]\{d\},
$$

$$
[B]=\begin{bmatrix}-\dfrac{6}{L^2}+\dfrac{12x}{L^3}&\ -\dfrac4L+\dfrac{6x}{L^2}&\ \dfrac{6}{L^2}-\dfrac{12x}{L^3}&\ -\dfrac2L+\dfrac{6x}{L^2}\end{bmatrix}.
$$

Since $\rho$ is a scalar, $\rho^2=\rho^T\rho=\{d\}^T[B]^T[B]\{d\}$. The nodal displacements do not depend on $x$, so they come outside the integral:

$$
U=\frac12\{d\}^T\left(\int_0^L[B]^TEI[B]\,dx\right)\{d\}.
$$

The work potential of the nodal loads is force times deflection plus moment times rotation:

$$
V=-\left(F_1v_1+M_1\theta_1+F_2v_2+M_2\theta_2\right)=-\{d\}^T\{F\}.
$$

Minimise $\Pi=U+V$ with respect to each of the four DOF:

$$
\frac{\partial\Pi}{\partial\{d\}}=\left(\int_0^L[B]^TEI[B]\,dx\right)\{d\}-\{F\}=0,
$$

so $\{F\}=[K]\{d\}$ with $[K]=\int_0^L[B]^TEI[B]\,dx$. Each entry is an integral of a product of two linear functions. For example, with $\xi=x/L$, $B_1=(12\xi-6)/L^2$ and

$$
K_{11}=EI\int_0^L B_1^2\,dx=\frac{EI}{L^3}\int_0^1(12\xi-6)^2\,d\xi=\frac{EI}{L^3}(48-72+36)=\frac{12EI}{L^3}.
$$

The rotation entries work the same way. With $B_2=(6\xi-4)/L$,

$$
K_{12}=EI\int_0^LB_1B_2\,\mathrm dx=\frac{EI}{L^2}\int_0^1(12\xi-6)(6\xi-4)\,\mathrm d\xi=\frac{EI}{L^2}\left(24-42+24\right)=\frac{6EI}{L^2}=\frac{EI}{L^3}\,6L,
$$

$$
K_{22}=EI\int_0^LB_2^2\,\mathrm dx=\frac{EI}{L}\int_0^1(6\xi-4)^2\,\mathrm d\xi=\frac{EI}{L}\left(12-24+16\right)=\frac{4EI}{L}=\frac{EI}{L^3}\,4L^2.
$$

The other entries follow in the same way, giving

$$
[K]=\frac{EI}{L^3}\begin{bmatrix}12&6L&-12&6L\\6L&4L^2&-6L&2L^2\\-12&-6L&12&-6L\\6L&2L^2&-6L&4L^2\end{bmatrix}.
$$

It is symmetric, and each column is the set of nodal forces and moments needed to hold one DOF at unit value with the others at zero. This matrix will be given in the exam; it does not have to be memorised. More accuracy needs more nodes per element and a higher-order polynomial, with six generalised boundary conditions for three nodes instead of four. This matrix applies to anything modelled as a two-node Euler–Bernoulli beam; bars, shells and solids have their own matrices.

## Worked examples

### Worked example: a propped cantilever with an overhang

The exercise: a uniform beam, $EI=10^7$ N m², is clamped at node 1 ($x=0$), simply supported at node 2 ($x=2$ m), and carries 10 kN downward at its free end, node 3 ($x=3$ m). Discretise with two elements, write the equilibrium equation in the six global DOF, then apply the boundary conditions to reduce it to three unknowns. Nodes go at the ends and at the support, so element 1 spans 2 m and element 2 spans 1 m.

For element 1, $EI/L^3=10^7/8=1.25\times10^6$ N/m:

$$
[K]^{(1)}=1.25\times10^6\begin{bmatrix}12&12&-12&12\\12&16&-12&8\\-12&-12&12&-12\\12&8&-12&16\end{bmatrix}.
$$

For element 2, $EI/L^3=10^7$ N/m $=8\times1.25\times10^6$:

$$
[K]^{(2)}=1.25\times10^6\begin{bmatrix}96&48&-96&48\\48&32&-48&16\\-96&-48&96&-48\\48&16&-48&32\end{bmatrix}.
$$

The global vector is $(v_1,\theta_1,v_2,\theta_2,v_3,\theta_3)$, so element 1 fills rows and columns 1–4 and element 2 fills 3–6; the blocks overlap at node 2:

$$
\begin{Bmatrix}F_1\\M_1\\F_2\\M_2\\F_3\\M_3\end{Bmatrix}=1.25\times10^6\begin{bmatrix}12&12&-12&12&0&0\\12&16&-12&8&0&0\\-12&-12&12+96&-12+48&-96&48\\12&8&-12+48&16+32&-48&16\\0&0&-96&-48&96&-48\\0&0&48&16&-48&32\end{bmatrix}\begin{Bmatrix}v_1\\\theta_1\\v_2\\\theta_2\\v_3\\\theta_3\end{Bmatrix}.
$$

Keep the order $(v,\theta)$ at each node, with forces $(F,M)$ in the same order; otherwise rows and columns of the element matrix must be swapped.

The clamp gives $v_1=\theta_1=0$; the simple support stops deflection but allows rotation, so $v_2=0$ with $\theta_2$ free. The only applied load is $F_3=-10^4$ N, with $M_2=M_3=0$. Striking out rows and columns 1, 2 and 3 leaves

$$
\begin{Bmatrix}0\\-10^4\\0\end{Bmatrix}=1.25\times10^6\begin{bmatrix}48&-48&16\\-48&96&-48\\16&-48&32\end{bmatrix}\begin{Bmatrix}\theta_2\\v_3\\\theta_3\end{Bmatrix}.
$$

That leaves three equations in three unknowns. Divide each row by $1.25\times10^6\times16$; the load becomes $-10^4/(2\times10^7)=-5\times10^{-4}$ in the middle row, which with its common factor 3 removed reads

$$
3\theta_2-3v_3+\theta_3=0,
\qquad
-\theta_2+2v_3-\theta_3=-1.667\times10^{-4},
\qquad
\theta_2-3v_3+2\theta_3=0.
$$

The first gives $\theta_3=3v_3-3\theta_2$. Put that into the third:

$$
\theta_2-3v_3+6v_3-6\theta_2=0
\quad\Longrightarrow\quad
\theta_2=0.6\,v_3,
\qquad
\theta_3=1.2\,v_3.
$$

The second row then gives $(-0.6+2-1.2)v_3=0.2v_3=-1.667\times10^{-4}$, so

$$
\theta_2=-5.0\times10^{-4}\text{ rad},
\qquad
v_3=-0.833\text{ mm},
\qquad
\theta_3=-1.0\times10^{-3}\text{ rad}.
$$

Back-substituting into the struck-out rows gives the reactions $F_1=-7.5$ kN, $M_1=-5.0$ kN m and $F_2=+17.5$ kN. Check the statics: vertical forces $-7.5+17.5-10=0$, and moments about node 1, taking anticlockwise positive, $-5+17.5\times2-10\times3=0$.

> [!check] The overhang as a cantilever from the prop
> The 1 m overhang is a cantilever built in at node 2, which itself rotates by $\theta_2$. Its tip therefore drops by the rigid rotation plus its own bending, $v_3=\theta_2a-\tfrac{Pa^3}{3EI}=-5.0\times10^{-4}\times1-\tfrac{10^4\times1}{3\times10^7}=-5.0\times10^{-4}-3.33\times10^{-4}=-8.33\times10^{-4}$ m, and its tip slope is $\theta_3=\theta_2-\tfrac{Pa^2}{2EI}=-5\times10^{-4}-5\times10^{-4}=-1.0\times10^{-3}$ rad. Both match the FE values.

![[dam_beam_example_deflection.png|900]]

The span between the supports lifts: the overhang load see-saws the beam about the prop, and the clamp has to pull down. The two-element FE curve lies on the exact beam-theory curve, because with only point loads at nodes the exact Euler–Bernoulli deflection between nodes is itself cubic, so cubic elements reproduce it exactly. Distributed loads would need finer meshes or consistent nodal loads to match between the nodes.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]
- Next: [[SESA2029 B6 - 2D and 3D Elements]]
- Concepts: [[Euler-Bernoulli Beam Element]] · [[Shape Functions]] · [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]]
- Beam loads in the lab: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- APDL scripting: [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]

## Sources

- FEA Lecture 7 slides, `Lecture_7_ FE_Beam_final.pdf` (worked example on slides 19–24), with transcript `SESA2029 Lecture 2026-02-20 - 0959.txt` (Dr J. Yuan)
- Shape functions and stiffness matrix derived with SymPy; example solved by hand and with NumPy. Figures: `01 - Notes/Figures/generate_dam_b5_figures.py`

## Self-study tasks

### Core

- [ ] Derive the beam strain energy $U=\tfrac12\int EI\rho^2\,dx$ from bending theory (2026-02-20 09:59, ll. 101–170). → [[#2. Bending theory and the beam's strain energy]]
- [ ] Derive the cubic shape functions from the four generalised boundary conditions (ll. 166–200). → [[#3. Degrees of freedom and cubic shape functions]]
- [ ] The two-element beam exercise: global equation in six DOF, then boundary conditions (exam-style, ll. 306–385). → [[#Worked example: a propped cantilever with an overhang]]
- [ ] Lab 2: recompute your stress concentration factors with a bulk stress of 120 MPa, not 83 MPa (correction announced at ll. 386–400). → [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]

### Further practice

- [ ] Finish the worked example: solve the reduced system and check the reactions by statics. → [[#Worked example: a propped cantilever with an overhang]]
- [ ] Evaluate $K_{12}$ and $K_{22}$ by integrating $[B]^T[B]$ (suggested, not lecturer-set). → [[#4. The stiffness matrix by minimum potential energy]]

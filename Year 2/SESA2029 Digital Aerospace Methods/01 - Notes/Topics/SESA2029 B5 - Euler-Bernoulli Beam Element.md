---
title: "SESA2029 B5 - Euler-Bernoulli Beam Element"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 16
tags:
  - sesa2029
  - fea
  - beam-element
aliases: ["Beam FE formulation", "Beam stiffness matrix", "Hermite beam element"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]"]
next_topics: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
key_concepts: ["[[Euler-Bernoulli Beam Element]]", "[[Shape Functions]]", "[[Global Stiffness Matrix Assembly]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B5 - Euler-Bernoulli Beam Element

> [!abstract] Summary
> Long, slender aerospace structures (wings, fuselages, space trusses) are modelled with **beam elements**, which carry bending.
>
> **Engineer's bending theory** (plane sections remain plane) gives $M/I = \sigma/y = E/R$. The strain energy is therefore $U = \tfrac12\int EI\,\rho^2dx$, where the curvature is $\rho = v''$.
>
> A 2-node beam has **2 DOF per node**: deflection $v$ and rotation $\theta = dv/dx$. That is 4 unknowns, so the displacement is a **cubic** (Hermite) polynomial. Differentiating twice gives $[B]$, and the PMPE gives
>
> $$[K] = \int[B]^TEI[B]\,dx = \frac{EI}{L^3}\begin{bmatrix}12&6L&-12&6L\\6L&4L^2&-6L&2L^2\\-12&-6L&12&-6L\\6L&2L^2&-6L&4L^2\end{bmatrix}$$
>
> This matrix is given in the exam. What you must be able to do is assemble it and apply BCs.

## Key Concepts
- [[Euler-Bernoulli Beam Element]] · [[Shape Functions]] · [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]]

---

## 1. Beams and shells in aerospace (L7)
- **Beam elements**: line elements between 2 (or 3) nodes. The section is described by constants: area, second moments $I_{yy}$ and $I_{zz}$, torsion constant. Any cross-section can be represented if its section properties are known, including one that varies along a wing's span. The FE preprocessor can compute them from geometry.
- **Shell elements**: a curved surface with a thickness at the nodes, for thin walls ([[Plate, Shell and Membrane Elements]]).

Beam theory assumes a **high aspect ratio**. Low-aspect-ratio parts such as fan blades couple shear and bending, so they need plate, shell or solid models.

## 2. Bending theory recap (L7)
**Plane sections remain plane** and perpendicular to the neutral axis, so the beam bends to a circular arc of radius $R$.
- The only strain is **axial**, $\varepsilon_x = y/R$, and the only stress is axial, $\sigma_x$.
- Both vary **linearly** through the depth and are zero at the neutral axis.
- Shear deformation is **neglected**, which is valid for long, slender beams.

$$
\boxed{\frac MI = \frac\sigma y = \frac ER}\qquad\text{("the most important statement you'll ever remember")}
$$

**Curvature** $\rho = 1/R\approx d^2v/dx^2$ for small slopes. The moment–curvature relation is $M = EI\rho$. Since $\varepsilon = y\rho$ and $M = \int_A\sigma y\,dA$:

$$
M\rho = \int_A\sigma\varepsilon\,dA
$$

**Strain energy**. Integrating over the section first removes the awkward through-depth integral:

$$
U = \int_L\int_A\tfrac12\sigma\varepsilon\,dA\,dx = \frac12\int_0^LM\rho\,dx = \frac12\int_0^LEI\rho^2\,dx
$$

## 3. DOF and interpolation (L7)
Each node carries the transverse deflection $v$ and the rotation $\theta = dv/dx$. There is no axial DOF in the pure bending element; adding one gives a frame element. Loads are nodal shear forces $F$ and moments $M$.

**Rotational DOF distinguish beams (and plates and shells) from bar and solid elements**, which have translations only.

$$
v = a+bx+cx^2+dx^3,\qquad\theta = b+2cx+3dx^2
$$

With the generalised BCs $v(0) = v_1$, $\theta(0) = \theta_1$, $v(L) = v_2$, $\theta(L) = \theta_2$, the first two give $a = v_1$ and $b = \theta_1$, and the other two give $c$ and $d$. Writing $\xi = x/L$:

$$
v = [N]\{d\},\quad\{d\} = \begin{Bmatrix}v_1\\\theta_1\\v_2\\\theta_2\end{Bmatrix},\quad
\begin{aligned}N_1 &= 1-3\xi^2+2\xi^3, & N_2 &= L(\xi-2\xi^2+\xi^3),\\ N_3 &= 3\xi^2-2\xi^3, & N_4 &= L(-\xi^2+\xi^3)\end{aligned}
$$

![[dam_beam_hermite_shape_functions.png|640]]

$N_1$ and $N_3$ carry the unit deflections; $N_2$ and $N_4$ carry the unit slopes. Each shape function is the deformed shape when its own DOF = 1 and all others = 0.

## 4. Stiffness matrix by PMPE (L7)
**Curvature from nodal DOF**: $\rho = \dfrac{d^2v}{dx^2} = \dfrac{d^2[N]}{dx^2}\{d\} = [B]\{d\}$, with

$$
[B] = \begin{bmatrix}-\dfrac{6}{L^2}+\dfrac{12x}{L^3}&\;-\dfrac4L+\dfrac{6x}{L^2}&\;\dfrac{6}{L^2}-\dfrac{12x}{L^3}&\;-\dfrac2L+\dfrac{6x}{L^2}\end{bmatrix}
$$

**Energy**. Since $\rho^2 = \{d\}^T[B]^T[B]\{d\}$ and $\{d\}$ does not depend on $x$:

$$
U = \frac12\{d\}^T\left(\int_0^L[B]^TEI[B]\,dx\right)\{d\},\qquad V = -\{d\}^T\{F\},\quad\{F\} = \{F_1\ M_1\ F_2\ M_2\}^T
$$

The work potential is force × displacement and moment × rotation.

$$
\frac{\partial\Pi}{\partial\{d\}} = \left(\int_0^L[B]^TEI[B]\,dx\right)\{d\}-\{F\} = 0\;\Rightarrow\;\{F\} = [K]\{d\}
$$

Evaluating the integral gives the matrix in the summary. It is **symmetric**. Each column is the set of nodal forces needed to impose a unit value of one DOF with the others held at zero.

> [!tip] Order matters
> Write the DOF as $(v_1,\theta_1,v_2,\theta_2)$ and the forces as $(F_1,M_1,F_2,M_2)$ in exactly that order, because the matrix is only valid for that ordering. Don't reorder to $(F_1,F_2,M_1,M_2)$ without permuting rows and columns.

## 5. Worked example: propped cantilever by MDM (L7)
Clamped at node 1 ($x = 0$), simply supported at node 2 ($x = 2$ m), with a 10 kN downward load at the free end, node 3 ($x = 3$ m). $EI = 10^4$ kN m² $= 10^7$ N m². Use 2 elements with 6 global DOF $(v_1,\theta_1,v_2,\theta_2,v_3,\theta_3)$.

**Element 1** ($L = 2$ m, $EI/L^3 = 1.25\times10^6$):

$$
[K]^{(1)} = 1.25\times10^6\begin{bmatrix}12&12&-12&12\\12&16&-12&8\\-12&-12&12&-12\\12&8&-12&16\end{bmatrix}
$$

**Element 2** ($L = 1$ m, $EI/L^3 = 10^7 = 1.25\times10^6\times8$):

$$
[K]^{(2)} = 1.25\times10^6\begin{bmatrix}96&48&-96&48\\48&32&-48&16\\-96&-48&96&-48\\48&16&-48&32\end{bmatrix}
$$

**Assemble**. Element 2 overlaps element 1 at DOF $(v_2,\theta_2)$:

$$
[K] = 1.25\times10^6\begin{bmatrix}12&12&-12&12&0&0\\&16&-12&8&0&0\\&&12+96&-12+48&-96&48\\&&&16+32&-48&16\\&\text{sym}&&&96&-48\\&&&&&32\end{bmatrix}
$$

**BCs**: $v_1 = \theta_1 = 0$ (clamp) and $v_2 = 0$ (support; $\theta_2$ is free). The loads are $F_3 = -10^4$ N and $M_2 = M_3 = 0$. **Delete rows and columns 1, 2, 3**:

$$
\begin{Bmatrix}0\\-10^4\\0\end{Bmatrix} = 1.25\times10^6\begin{bmatrix}48&-48&16\\-48&96&-48\\16&-48&32\end{bmatrix}\begin{Bmatrix}\theta_2\\v_3\\\theta_3\end{Bmatrix}
$$

**Solution** (checked in Python):
- $\theta_2 = -5.0\times10^{-4}$ rad;
- $v_3 = -0.833$ mm;
- $\theta_3 = -1.0\times10^{-3}$ rad.

**Reactions** by back-substitution: $F_1 = -7.5$ kN, $M_1 = -5.0$ kN m, $F_2 = +17.5$ kN.

**Statics check**: $\sum F = -7.5+17.5-10 = 0$ ✓, and moments about node 1: $-5+17.5(2)-10(3) = 0$ ✓.

![[dam_beam_example_deflection.png|640]]

The span between the supports **lifts** (the overhang load see-saws it about the prop). The 2-element FE curve lies exactly on the beam-theory curve. With only nodal point loads the exact Euler–Bernoulli solution is cubic between nodes, so Hermite elements are **exact**. Distributed loads would need finer meshes, or consistent nodal loads, to match between nodes.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]] · Next: [[SESA2029 B6 - 2D and 3D Elements]]
- APDL beam workflows (point, uniform and elliptical loads): [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- Beam bending theory (structures): SESA2028

## Sources
- FEA Lecture 7, `02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf`; transcript `FEA.txt`
- Example solution verified with NumPy (`scripts/make_figures.py`)

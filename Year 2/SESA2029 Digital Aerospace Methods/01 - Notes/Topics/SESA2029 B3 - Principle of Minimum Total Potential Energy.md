---
title: "SESA2029 B3 - Principle of Minimum Total Potential Energy"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 14
tags: [sesa2029, fea, energy-methods, stress-concentration]
aliases: ["PMPE", "Minimum potential energy", "Weak form", "FEA Lecture 5"]
date: 2026-10-30
status: lectured
coverage: "FEA week 3 (2026-02-13, ll. 1–388)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
next_topics: ["[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]"]
key_concepts: ["[[Principle of Minimum Total Potential Energy]]", "[[Strong and Weak Forms]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-13.txt", "Pilkey, Peterson's Stress Concentration Factors"]
---

# SESA2029 B3 - Principle of Minimum Total Potential Energy

> [!abstract] Summary
> The strong form of equilibrium, a second-order differential equation in the displacement that must hold at every point, is rarely solvable for real geometry, so finite elements work with weak (integral) forms that hold on average and need only first derivatives. The principle of minimum total potential energy is one such form: of all displacement fields that satisfy the displacement boundary conditions, the equilibrium one minimises $\Pi=U+V$, the strain energy plus the potential of the loads. Setting $\partial\Pi/\partial d_i=0$ for every degree of freedom gives $\{F\}=[K]\{d\}$, the same bar matrix as the matrix displacement method by a route that generalises to any element. It also gives the stress concentration factor needed for lab 2.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to derive an element stiffness matrix by energy, to explain strong and weak forms, or to compute a stress concentration factor or factor of safety.
> - **Assumptions:** linear elastic, conservative loads, small displacements; displacement boundary conditions satisfied by the trial field.
> - **Method:** 1. Strain energy $U=\tfrac12k\,\Delta L^2$ with $\Delta L=u_j-u_i$. 2. Load potential $V=-\sum F_id_i$. 3. $\Pi=U+V$. 4. $\partial\Pi/\partial d_i=0$ for each DOF. 5. Collect into matrix form.
> - **Common mistakes:** writing $V=+Fu$ (the load potential falls as the load moves); taking the minimum stress in the plate as the bulk stress for $K_t$.
> - **Practise:** [[#4. The two-node bar by minimum potential energy]] · [[#Worked example: the two-bar structure by energy]]

Minimum potential energy underlies the Rayleigh–Ritz method and shape functions of [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions|B4]], the general route that FE software implements (2026-02-13, ll. 1–20).

A loaded elastic body settles into the shape that minimises its total potential energy, as a ball settles at the bottom of a bowl. The body can be imagined in any shape that respects its supports; for each shape there is a total potential energy, made of the energy stored in the deformed material and the potential the loads have lost by moving. Stretching further stores more strain energy but lets the load fall further. The body comes to rest where the two trade off exactly, at the bottom of the energy bowl, so finding equilibrium becomes finding a minimum, which only needs first derivatives.

## 1. Strong and weak forms

Real systems are governed by ordinary or partial differential equations with boundary conditions, and for dynamics initial conditions (ll. 11–40). The aeroelastic equation of motion, with mass, damping and stiffness matrices on the left and an aerodynamic force depending on displacement and velocity on the right, is one example; the Navier–Stokes equations of Part A are another. For a structure, equilibrium is first written in derivatives of stress, then, through the strain–displacement and stress–strain laws, as second-order differential equations in the displacement. This is the strong form: the second derivative of the displacement must exist and be continuous at every point in the body. Corners, changes of section and boundary conditions often make that impossible, and solutions exist for only the simplest configurations ([[Strong and Weak Forms]]).

The way round is to restate the equations as integrals that need only be satisfied on average, the weak form, which also imposes some boundary conditions weakly (ll. 41–90). A weighted-residual method such as Galerkin's substitutes an approximate trial displacement into the differential equation, multiplies the residual (the amount by which the equation is not satisfied) by weighting functions and integrates to zero, so the error is minimised in a weighted-average sense. The finite element approximation then describes the trial displacement through values at a finite number of nodes and interpolating shape functions, turning infinitely many unknowns into a finite set of linear (or nonlinear) algebraic equations. The weak form loses nothing in principle (§3); the accuracy lost is that of the finite-element approximation, while speed and generality rise enormously.

Weighted-residual and minimum-potential-energy methods both belong to the variational methods, built on the calculus of variations, which studies small changes $\delta$ in functionals (functions of functions) to find their stationary values (ll. 66–75).

## 2. Strain energy and the potential of the loads

A bar of stiffness $k=EA/L$ is extended by $u$ under a force that grows with the extension, $F=ku$ (ll. 126–150). The work done in a further small extension $du$ is

$$
dW=F\,du=ku\,du.
$$

Integrate from zero to the final extension:

$$
W=\int_0^u ku\,du=\tfrac12ku^2.
$$

Linear elastic deformation is conservative, so this work is stored as strain energy,

$$
U=\tfrac12ku^2,
$$

the triangle under the force–extension line. Dividing by the volume $AL$, with $F=\sigma A$ and $u=\varepsilon L$, gives the strain energy density

$$
\bar U=\tfrac12\sigma\varepsilon,
$$

the area under the stress–strain line. For the uniform bar the stress and strain are constant; in general they vary, and $\bar U$ must be integrated over the volume, which lab 1's stress and strain results would allow.

Perturb the equilibrium position by a small virtual displacement $\delta u$ (ll. 151–175). The load is effectively constant during so small a movement and does virtual work

$$
\delta W=F\,\delta u.
$$

In a conservative system that work is stored as strain energy, $\delta U=\delta W$. The work the load does is a loss of its potential to do work, so define the potential of the loads $V$ by $\delta V=-\delta W$. Then the energy balance is

$$
\delta U+\delta V=\delta(U+V)=0.
$$

The sum $\Pi=U+V$, a functional of the displacement field, is the total potential energy. For the bar, $U=\tfrac12ku^2$ and $V=-Fu$.

## 3. The principle

Of all the deformations an elastic body can take that satisfy its displacement boundary conditions, the one in equilibrium makes the total potential energy stationary, and for stable equilibrium a minimum ([[Principle of Minimum Total Potential Energy]]; ll. 176–190):

$$
\delta\Pi=\delta U+\delta V=0.
$$

The exact strong-form solution also minimises $\Pi$, so nothing is lost in principle (ll. 111–125). The benefits are that it is far less demanding than the strong form, only first derivatives need be finite, the force boundary conditions are satisfied automatically because the loads enter through $V$, and the trial displacement need only satisfy the displacement boundary conditions, which the shape functions of an element are built to do.

For the single-DOF bar (ll. 186–215),

$$
\Pi(u)=\tfrac12ku^2-Fu .
$$

Differentiate:

$$
\frac{d\Pi}{du}=ku-F.
$$

Set it to zero:

$$
F=ku,
$$

the bar's equilibrium equation again. In the figure, $U$ rises as a parabola, $V$ falls linearly, and their sum has its minimum at $u=F/k$.

![[dam_total_potential_energy.png|560]]

With $n$ degrees of freedom, $\Pi=\Pi(d_1,\dots,d_n)$, and minimising with respect to each one,

$$
\frac{\partial\Pi}{\partial d_i}=0,
\qquad
i=1,\dots,n,
$$

gives $n$ linear algebraic equations, which collect into $\{F\}=[K]\{d\}$ (ll. 216–225). This is an alternative, and much more general, way of obtaining the element equations.

### Two degrees of freedom: the stepped bar

The stepped bar of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method|B1]] is fixed at node 1 ($u_1=0$), with stiffnesses $k_1$ and $k_2$ and a load $F$ at node 3. Element 1 stretches by $u_2$ and element 2 by $u_3-u_2$, and only node 3 carries a load, so

$$
\Pi(u_2,u_3)=\tfrac12k_1u_2^2+\tfrac12k_2(u_3-u_2)^2-Fu_3.
$$

Differentiate with respect to each free DOF:

$$
\frac{\partial\Pi}{\partial u_2}=k_1u_2-k_2(u_3-u_2)=0,
\qquad
\frac{\partial\Pi}{\partial u_3}=k_2(u_3-u_2)-F=0.
$$

In matrix form these are

$$
\begin{bmatrix}k_1+k_2&-k_2\\-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_2\\u_3\end{Bmatrix}=\begin{Bmatrix}0\\F\end{Bmatrix},
$$

exactly the reduced system B1 obtained by assembling and striking out row and column 1. The second equation gives $k_2(u_3-u_2)=F$; substituted into the first, $k_1u_2=F$, so $u_2=F/k_1$ and $u_3=F/k_1+F/k_2$.

![[dam_energy_bowl.png|760]]

With $k_1=2k$ and $k_2=k$ the energy surface is the bowl in the figure, its lowest point at $u_2=0.5F/k$, $u_3=1.5F/k$. The contours are tilted ellipses because $\Pi$ contains the cross term $-k_2u_2u_3$: the two DOF are coupled through element 2, which is what the off-diagonal $-k_2$ in the matrix expresses.

### The minimum value

For any linear structure, $\Pi=\tfrac12\{d\}^T[K]\{d\}-\{F\}^T\{d\}$. At equilibrium $[K]\{d\}=\{F\}$, so the strain energy is $U=\tfrac12\{d\}^T\{F\}$, and

$$
\Pi_{min}=\tfrac12\{F\}^T\{d\}-\{F\}^T\{d\}=-\tfrac12\{F\}^T\{d\}=-U.
$$

At equilibrium the loads have lost twice the energy the structure has stored; the other half is the area above the force–extension line, the work the loads would have done had they been applied at full value from the start.

> [!check] The stepped bar's minimum
> With $k_1=2k$, $k_2=k$ and $u_3=1.5F/k$: $U=\tfrac12(2k)(0.5F/k)^2+\tfrac12k(F/k)^2=0.25F^2/k+0.5F^2/k=0.75F^2/k$, and $V=-F\times1.5F/k=-1.5F^2/k$. So $\Pi=-0.75F^2/k=-U$, the value marked in the figure.

## 4. The two-node bar by minimum potential energy

A bar of length $L$ and axial stiffness $k=AE/L$ has nodes $i$ and $j$ with displacements $u_{xi}$, $u_{xj}$ and nodal forces $F_{xi}$, $F_{xj}$. Minimum potential energy gives the matrix displacement method's equation (ll. 226–270; an example-sheet 2 and exam skill). The extension is

$$
\Delta L=u_{xj}-u_{xi}.
$$

The strain energy is

$$
U=\tfrac12k(u_{xj}-u_{xi})^2=\tfrac12k\left(u_{xj}^2-2u_{xi}u_{xj}+u_{xi}^2\right).
$$

The potential of the two nodal loads is

$$
V=-F_{xi}u_{xi}-F_{xj}u_{xj}.
$$

So

$$
\Pi=\tfrac12k\left(u_{xj}^2-2u_{xi}u_{xj}+u_{xi}^2\right)-F_{xi}u_{xi}-F_{xj}u_{xj}.
$$

Differentiate with respect to $u_{xi}$; only the last two terms of the bracket and the first load term contain it:

$$
\frac{\partial\Pi}{\partial u_{xi}}=\tfrac12k\left(-2u_{xj}+2u_{xi}\right)-F_{xi}=0
\quad\Longrightarrow\quad
F_{xi}=ku_{xi}-ku_{xj}.
$$

Differentiate with respect to $u_{xj}$:

$$
\frac{\partial\Pi}{\partial u_{xj}}=\tfrac12k\left(2u_{xj}-2u_{xi}\right)-F_{xj}=0
\quad\Longrightarrow\quad
F_{xj}=-ku_{xi}+ku_{xj}.
$$

In matrix form,

$$
\begin{Bmatrix}F_{xi}\\F_{xj}\end{Bmatrix}=\frac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}\begin{Bmatrix}u_{xi}\\u_{xj}\end{Bmatrix},
$$

exactly the result of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method|B1]]. The sign of the extension does not matter once it is squared.

## 5. Stress concentration and factor of safety

A plate with a hole, like a fuselage panel or wing rib, shows how close a hole can be placed to an edge before yield, what the stress concentration factor is, how the number of elements affects it (a convergence study), and how hole size and position affect the maximum stress and the factor of safety (lab 2; ll. 271–365; [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)|C3]]).

A local discontinuity, a hole, a step or a sharp corner, causes a highly localised rise in stress (ll. 291–310). How much depends on the global configuration, the location of the discontinuity and its geometry and size, and the more abrupt the change, the larger the rise. At the step between two diameters of a shaft, neither $F/A_1$ nor $F/A_2$ gives the stress at the junction; a fillet radius reduces the concentration, a sharp corner increases it ([[Stress Concentration Factor and Factor of Safety]]). The stress concentration factor is

$$
K_t=\frac{\sigma_{max}}{\sigma_{bulk}},
$$

the maximum local stress (usually von Mises from the FE results) over the bulk stress far from the concentration (ll. 311–320). It can be measured, expensively, or computed by FE with a mesh refined where the stress is high, since without a converged mesh the peak is not accurate.

For an elliptical hole at the centre of a large plate, with semi-axis $a$ across the load and $b$ along it,

$$
K_t=1+\frac{2a}{b},
$$

which gives $K_t=3$ for a circle (ll. 321–330). The formula assumes a hole far from any edge; for a hole near a boundary, or of arbitrary size and position, FE gives the answer. In the FE example with $a=2b$, the far-field stress is about 100 MPa and the peak at the end of the hole 503.7 MPa, so $K_t=5.037$ against the analytical 5, a very good validation. The full stress field round a circular hole is the Kirsch solution:

![[dam_kirsch_hole_stress.png|740]]

The factor of safety against yield is

$$
FoS=\frac{\sigma_Y}{\sigma_{max}},
$$

and design standards usually require 1.5 or 2 (ll. 346–360). If it is too low, reduce the hole size, increase the plate thickness or reduce the load. In the lab-2 example the maximum von Mises stress is about 436 MPa against a yield stress of 460 MPa (Lecture 5 slide 27), so

$$
FoS=\frac{460}{436}=1.055,
$$

too low for either standard. Because the analysis is linear and the in-plane stresses in a plate of thickness $t$ scale as $1/t$ for a fixed load, reaching $FoS=1.5$ needs the peak stress down to $460/1.5=307$ MPa: a thickness increase, or a load reduction, by a factor $436/307=1.42$.

> [!warning] Choosing the bulk stress (ll. 351–360)
> Take the bulk stress on the loaded boundary, well away from the hole, where force equilibrium fixes it at the applied traction. It is not the minimum stress anywhere in the plate: the example has a low-stress region beside the hole at about 37 MPa, and using that would inflate $K_t$ by a factor of about three.

## Worked example: the two-bar structure by energy

The clamped two-bar problem of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method#Worked example: two bars clamped at both ends|B1]] can be reworked by minimum potential energy: bar 1 has $k_1=2AE/L$, bar 2 has $k_2=AE/L$, $u_1=u_3=0$ and load $P$ at node 2. Only $u_2$ is free, and both bars extend or shorten by $u_2$ in magnitude:

$$
\Pi=\tfrac12k_1u_2^2+\tfrac12k_2u_2^2-Pu_2 .
$$

Differentiate and set to zero:

$$
\frac{d\Pi}{du_2}=(k_1+k_2)u_2-P=0.
$$

Substitute the stiffnesses:

$$
u_2=\frac{P}{3AE/L}=\frac{PL}{3AE},
$$

as before, without assembling any matrix. Putting it back gives the minimum value

$$
\Pi_{min}=-\frac{P^2L}{6AE}=-\tfrac12Pu_2 ,
$$

a general result for linear structures: at equilibrium the strain energy is $\tfrac12Pu_2$ and the load potential $-Pu_2$, so $\Pi=-U$.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Next: [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]
- Concepts: [[Principle of Minimum Total Potential Energy]] · [[Strong and Weak Forms]] · [[Stress Concentration Factor and Factor of Safety]]
- Lab 2: [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]
- Equations of motion and modal analysis: [[SESA2029 B8 - Modal Analysis]]

## Sources

- FEA Lecture 5 slides, `Lecture_5_Mimimum_Potnetial_Energy.pdf`, with transcript `SESA2029 Lecture 2026-02-13.txt`, ll. 1–388 (Dr J. Yuan)
- Kirsch (1898) for the circular hole; Pilkey, *Peterson's Stress Concentration Factors*
- Worked examples checked with SymPy. Figures: `01 - Notes/Figures/generate_dam_b3_figures.py`

## Self-study tasks

### Core

- [ ] Derive the two-node bar matrix by minimum potential energy (flagged as examinable, 2026-02-13, ll. 226–275). → [[#4. The two-node bar by minimum potential energy]]
- [ ] Example sheet 2, four questions on the energy method (ll. 271–275, 625–635). → [[SESA2029 FEA Worked Examples]]
- [ ] Explain strong form, weak form and why FE uses the weak form (ll. 11–90). → [[#1. Strong and weak forms]]
- [ ] Lab 2: stress concentration factor, factor of safety, and their sensitivity to hole size and position (ll. 276–365). → [[#5. Stress concentration and factor of safety]]

### Further practice

- [ ] Rework B1's stepped bar (fixed at node 1, loaded at node 3) by minimum potential energy with two unknowns. → [[#Two degrees of freedom: the stepped bar]]
- [ ] Show that $\Pi_{min}=-U$ for any linear structure under fixed loads (suggested, not lecturer-set). → [[#The minimum value]]

## Transcript and slide slips

> [!warning] Lecture slips (2026-02-13, ll. 166–175 and 391–395)
> Where: [[#3. The principle]].
>
> The work potential is first stated as "F times U"; it is $-Fu$, as the lecture itself uses at l. 196. Recapping in the second lecture, equilibrium is described as where "the total potential energy is equal to zero"; it is where $\Pi$ is stationary (a minimum), which is where its first derivative is zero.

> [!warning] Slide slips (Lecture 5 slides 15, 20 and 27)
> Where: [[#3. The principle]] and [[#5. Stress concentration and factor of safety]].
>
> Slide 15 writes the stationarity condition as $\delta\Pi=\delta W+\delta U=0$; with $\Pi=U+V$ it is $\delta V+\delta U=0$ (slide 14 has it right), and $\delta W=-\delta V$. Slide 20 defines the extension as $\Delta L=u_i-u_j$ rather than $u_j-u_i$; the sign disappears when it is squared, so the matrix is unaffected. Slide 27 rounds $460/436$ to 1.056; it is 1.055.

---
title: "SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 15
tags: [sesa2029, fea, shape-functions, rayleigh-ritz]
aliases: ["Rayleigh-Ritz", "Interpolation functions", "Shape function matrix", "FEA Lecture 6"]
date: 2026-10-30
status: lectured
coverage: "FEA week 3 (2026-02-13, ll. 389–639)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]"]
next_topics: ["[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
key_concepts: ["[[Rayleigh-Ritz Method]]", "[[Shape Functions]]", "[[h- and p-Refinement]]", "[[Principle of Minimum Total Potential Energy]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-13.txt"]
---

# SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions

> [!abstract] Summary
> A continuous body has infinitely many degrees of freedom because its displacement is unknown at every point. The Rayleigh–Ritz method assumes a form for the displacement, usually a polynomial with a few unknown coefficients fixed by the boundary conditions, and minimum potential energy then determines them. The finite element method applies Rayleigh–Ritz to each small element instead of the whole structure; rewriting the element polynomial in terms of nodal displacements gives the shape functions, $u=[N]\{d\}$, each equal to one at its own node and zero at the others. Accuracy is improved by smaller elements (h-refinement) or higher polynomial order (p-refinement).

> [!summary]- Exam use: quick path
> - **Use it when:** asked to derive shape functions for a bar element, to explain Rayleigh–Ritz, or to distinguish h- and p-methods.
> - **Assumptions:** 1D bar of constant $A$ and $E$, $\varepsilon=du/dx$, polynomial displacement within each element.
> - **Method:** 1. Assume $u=a+bx$ (or $a+bx+cx^2$). 2. Apply the nodal values as generalised boundary conditions. 3. Solve for the coefficients. 4. Collect the terms multiplying each nodal displacement: these are $N_i$. 5. Check $N_i=1$ at node $i$ and 0 at the others.
> - **Common mistakes:** forgetting to check the nodal values of each $N_i$; calling a three-node element "three elements".
> - **Practise:** [[#Quadratic interpolation with three nodes]] · [[#Worked example: a bar under distributed load]]

This lecture took minimum potential energy from [[SESA2029 B3 - Principle of Minimum Total Potential Energy|B3]] to the general method that FE software implements, still using the bar; the beam follows in [[SESA2029 B5 - Euler-Bernoulli Beam Element|B5]] (2026-02-13, ll. 381–400).

Rayleigh–Ritz is curve fitting guided by an energy principle. The real displacement of a bar is some smooth curve with infinitely many values. Rayleigh–Ritz replaces it by a curve of a chosen family, a straight line or a parabola, with only a few adjustable numbers, and lets the energy principle pick the member of the family that comes closest. Finite elements make the family flexible by using a separate simple curve on each short piece, joined at the nodes, so that even a straight line per element can follow a complicated shape if there are enough elements.

## 1. Strain energy needs the displacement everywhere

The strain energy density $\bar U=\tfrac12\sigma\varepsilon$ holds at any point of any elastic body (ll. 401–420). In general the stress and strain vary, so the total strain energy is an integral over the volume:

$$
U=\int_V\bar U\,dV.
$$

That needs the displacement, and hence the strain and stress, at every point: infinitely many degrees of freedom, which is too expensive. The Rayleigh–Ritz method reduces the problem to a finite number of DOF by writing the displacement as a mathematical function of the spatial coordinates with a limited number of unknown coefficients, which become the DOF (ll. 416–425). Polynomials are the most common choice.

## 2. Rayleigh–Ritz for the two-node bar

Take a bar of constant area $A$ (ll. 421–490). With $\sigma=E\varepsilon$, and $dV=A\,dx$,

$$
U=\int_0^L\tfrac12\sigma\varepsilon\,A\,dx=\frac{AE}{2}\int_0^L\varepsilon^2\,dx.
$$

The 1D strain is the derivative of the displacement, $\varepsilon=du/dx$:

$$
U=\frac{AE}{2}\int_0^L\left(\frac{du}{dx}\right)^2dx .
$$

The strain energy now depends only on $u(x)$, which is unknown. In B3 it was taken as linear without comment; here that becomes an explicit assumption:

$$
u=a+bx .
$$

The generalised boundary conditions are the nodal displacements. At $x=0$, $u=u_{xi}$:

$$
a=u_{xi}.
$$

At $x=L$, $u=u_{xj}$:

$$
u_{xi}+bL=u_{xj}
\quad\Longrightarrow\quad
b=\frac{u_{xj}-u_{xi}}{L}.
$$

So the displacement anywhere is

$$
u=u_{xi}+\frac{u_{xj}-u_{xi}}{L}x,
$$

and its derivative is constant:

$$
\frac{du}{dx}=\frac{u_{xj}-u_{xi}}{L}.
$$

Substitute and integrate a constant over the length:

$$
U=\frac{AE}{2}\left(\frac{u_{xj}-u_{xi}}{L}\right)^2L=\frac{AE}{2L}(u_{xj}-u_{xi})^2 .
$$

This is the strain energy used in B3, and with $V=-F_{xi}u_{xi}-F_{xj}u_{xj}$ minimum potential energy gives the same bar matrix. The difference is that the linear variation is now a stated assumption, which for other elements need not hold (ll. 441–450).

## 3. From Rayleigh–Ritz to finite elements

Rayleigh–Ritz applied to a complete structure needs one function valid everywhere that satisfies all the boundary conditions, which is possible only for simple geometry and simple boundary conditions (ll. 486–500). The finite element method gets round this by applying Rayleigh–Ritz to simple, finite sub-volumes, the elements, each with its own low-order function, and assembling the element models into a global model of the whole structure.

Interpolation is the technique of evaluating an unknown quantity anywhere in a domain from its known values at other locations (ll. 496–505). In finite elements it defines the displacement throughout an element in terms of a finite number of nodal displacements, and the interpolation functions are called shape functions ([[Shape Functions]]).

## 4. Linear shape functions

In standard FE numbering, node 1 is at $x=0$ and node 2 at $x=L$ (ll. 506–545). From section 2,

$$
u=u_1+\frac{u_2-u_1}{L}x.
$$

Group the terms multiplying each nodal displacement:

$$
u=\left(1-\frac xL\right)u_1+\frac xL\,u_2 .
$$

In matrix form,

$$
u=\begin{bmatrix}N_1&N_2\end{bmatrix}\begin{Bmatrix}u_1\\u_2\end{Bmatrix}=[N]\{d\},
\qquad
N_1=1-\frac xL,
\qquad
N_2=\frac xL .
$$

$[N]$ is the shape function matrix, and $u=[N]\{d\}$ is on the exam equation sheet (ll. 526–535). $N_1$ is 1 at node 1 and 0 at node 2; $N_2$ is the reverse. Every shape function has the value one at its own degree of freedom and zero at the others (ll. 536–545). They also sum to one everywhere, so a rigid-body translation, $u_1=u_2$, is represented exactly. The continuous bar with infinitely many DOF has become a two-DOF problem, with everything between the nodes interpolated.

The lecture stops at the shape functions; the step to the stiffness matrix follows directly. The strain is

$$
\varepsilon=\frac{du}{dx}=\frac{d[N]}{dx}\{d\}=[B]\{d\},
\qquad
[B]=\begin{bmatrix}-\dfrac1L&\dfrac1L\end{bmatrix},
$$

and the strain energy $U=\tfrac12\int_V\{d\}^T[B]^TE[B]\{d\}\,dV$ minimised over $\{d\}$ gives

$$
[K]^e=\int_V[B]^TE[B]\,dV=AL\,E\begin{bmatrix}\tfrac1{L^2}&-\tfrac1{L^2}\\-\tfrac1{L^2}&\tfrac1{L^2}\end{bmatrix}=\frac{AE}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}.
$$

The same formula, with the appropriate $[B]$ and material matrix, builds the beam, plate, shell and solid elements.

## Quadratic interpolation with three nodes

The next polynomial order is quadratic, $u=a+bx+cx^2$, with three unknown constants, so the element needs three nodes: one at each end and one in the middle (ll. 546–600). Putting the origin at the middle node makes the algebra easier, with nodes 1, 2, 3 at $x=-L/2$, $0$, $L/2$ (using $0$, $L/2$, $L$ also works). The three generalised boundary conditions are

$$
u_1=a-\frac{bL}{2}+\frac{cL^2}{4},
\qquad
u_2=a,
\qquad
u_3=a+\frac{bL}{2}+\frac{cL^2}{4}.
$$

The middle equation gives $a$ directly:

$$
a=u_2 .
$$

Subtract the first equation from the third:

$$
u_3-u_1=bL
\quad\Longrightarrow\quad
b=\frac{u_3-u_1}{L}.
$$

Add the first and third and use $a=u_2$:

$$
u_1+u_3=2u_2+\frac{cL^2}{2}
\quad\Longrightarrow\quad
c=\frac{2(u_1-2u_2+u_3)}{L^2}.
$$

The lecture leaves this as a matrix inversion and shows only the result. Substitute into $u=a+bx+cx^2$:

$$
u=u_2+\frac{u_3-u_1}{L}x+\frac{2(u_1-2u_2+u_3)}{L^2}x^2 .
$$

Collect the coefficient of each nodal displacement (checked with SymPy):

$$
N_1=\frac{2x^2}{L^2}-\frac xL,
\qquad
N_2=1-\frac{4x^2}{L^2},
\qquad
N_3=\frac{2x^2}{L^2}+\frac xL .
$$

Check node 1, $x=-L/2$: $N_1=\tfrac12+\tfrac12=1$, $N_2=1-1=0$, $N_3=\tfrac12-\tfrac12=0$. The pattern holds at every node.

![[dam_bar_shape_functions.png|760]]

The quadratic shape functions are curved, and $N_1$ and $N_3$ dip slightly below zero between nodes, but each is still exactly one or zero at the nodes (ll. 576–595). Because the strain is the derivative, a two-node element has constant strain and a three-node element linearly varying strain.

> [!warning] Lecture slip (2026-02-13, ll. 549–552)
> The quadratic case is introduced as "if a bar has three elements". It is one element with three nodes.

## 5. h- and p-refinement

There are two ways to make a finite element model more accurate (ll. 600–625; [[h- and p-Refinement]]). The h-method refines the mesh, reducing the characteristic element size $h$ while keeping the same shape functions; it is the most common approach and what lab 1's convergence study does with linear BEAM188 elements. The p-method raises the polynomial order $p$ of the shape functions, from two-node linear to three-node quadratic and beyond. Both add degrees of freedom. Mainstream FE packages such as ANSYS and Abaqus mainly use the h-method, while some CAD packages with built-in FE (SolidWorks is the lecture's example) use p-methods with polynomial orders up to 8 or 9, depending on how complex the displacement is.

The element libraries offer lower- and higher-order versions of each element, and lab 3 compares a four-node and an eight-node shell, whose difference is exactly their shape functions: higher order is more accurate (ll. 616–625).

## Worked example: a bar under distributed load

This example is not in the lecture; it shows Rayleigh–Ritz giving an approximate answer and improving as the trial function grows. A bar of length $L$ hangs from $x=0$ and carries a uniform axial load $q$ per unit length (for example its own weight), with the far end free. The total potential energy is

$$
\Pi=\frac{AE}{2}\int_0^L\left(\frac{du}{dx}\right)^2dx-\int_0^Lq\,u\,dx .
$$

The trial function must satisfy the displacement boundary condition $u(0)=0$; the free-end force condition is satisfied automatically. First try $u=bx$. Then $du/dx=b$ and

$$
\Pi=\frac{AE}{2}b^2L-\frac{qbL^2}{2}.
$$

Minimise over $b$:

$$
\frac{d\Pi}{db}=AEbL-\frac{qL^2}{2}=0
\quad\Longrightarrow\quad
b=\frac{qL}{2AE}.
$$

The tip displacement $u(L)=qL^2/(2AE)$ is exact, but the strain is constant at $qL/(2AE)$, whereas the true strain at the root is $qL/(AE)$, so the root stress is underestimated by half. Now try $u=bx+cx^2$. Minimising over both coefficients (SymPy) gives

$$
u=\frac{q}{2AE}\left(2Lx-x^2\right),
$$

which is the exact solution, with root strain $qL/(AE)$. The minimum energies are $-q^2L^3/(8AE)$ for the linear trial and $-q^2L^3/(6AE)$ for the quadratic: the better trial function reaches a lower total potential energy, as the principle requires. A finite element model would reach the same improvement either by p-refinement (quadratic elements) or by h-refinement (more linear elements).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- Next: [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Concepts: [[Rayleigh-Ritz Method]] · [[Shape Functions]] · [[h- and p-Refinement]] · [[Principle of Minimum Total Potential Energy]]
- The CFD counterpart of polynomial fitting: [[Convective Interpolation Schemes]] · [[Taylor Table Method]]

## Sources

- FEA Lecture 6 slides, `Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf`, with transcript `SESA2029 Lecture 2026-02-13.txt`, ll. 389–639 (Dr J. Yuan)
- Quadratic shape functions and the worked example checked with SymPy

## Self-study tasks

### Core

- [ ] Derive the linear shape functions of a two-node bar and check their nodal values (2026-02-13, ll. 506–545; the shape-function equation "needs to be used" in the example sheet). → [[#4. Linear shape functions]]
- [ ] Derive the quadratic shape functions for a three-node bar (ll. 546–595). → [[#Quadratic interpolation with three nodes]]
- [ ] Example sheet 2 questions on Rayleigh–Ritz and shape functions ("there are four questions there", ll. 626–635). → [[SESA2029 FEA Worked Examples]]
- [ ] Explain the h- and p-methods and which elements in the labs are linear or quadratic (ll. 600–625). → [[#5. h- and p-refinement]]

### Further practice

- [ ] Repeat the distributed-load example with two linear elements and compare with the one-element quadratic answer (suggested, not lecturer-set). → [[#Worked example: a bar under distributed load]]

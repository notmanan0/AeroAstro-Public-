---
title: "SESA2029 A10 - Grids and Pressure-Based Solution Algorithms"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 10
tags: [sesa2029, cfd, grids, solvers]
aliases: ["CFD grids", "SIMPLE algorithm", "Pressure-based solver", "CFD Lecture 11"]
date: 2026-10-30
status: lectured
coverage: "Week 6 (2025-11-06)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A9 - Finite Volume Method]]"]
next_topics: ["[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]"]
key_concepts: ["[[Structured, Unstructured and Hybrid Grids]]", "[[Pressure-Velocity Coupling and SIMPLE]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L11, pp. 143–164)", "02 - Sources/Lectures/SESA2029 Lecture 2025-11-06.txt", "Blazek, Computational Fluid Dynamics: Principles and Applications (grid figures)"]
---

# SESA2029 A10 - Grids and Pressure-Based Solution Algorithms

> [!abstract] Summary
> Structured grids, indexed $(i,j,k)$ in H, O or C topologies or in blocks, are fast and accurate but hard to build round complex shapes; unstructured grids mesh anything at the press of a button but are less accurate and less efficient; the modern compromise for viscous flow is a hybrid grid with inflation layers on the walls. In incompressible flow continuity is a constraint, not an evolution equation, so taking the divergence of the momentum equation gives a Poisson equation for pressure that must be solved together with momentum, either segregated (SIMPLE, SIMPLEC, PISO) with under-relaxation, or coupled.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to compare grid types, choose a topology, explain what the pressure-based solver does, or compare segregated and coupled solvers.
> - **Assumptions:** constant density for the pressure equation; implicit (backward Euler) time stepping or pseudo-time towards a steady state.
> - **Method:** 1. Write momentum in index form with the right side at $n+1$. 2. Take $\partial/\partial x_i$ of every term. 3. Use $\partial(\rho u_i)/\partial x_i=0$ at both levels to remove the time terms. 4. What remains is $\nabla^2p=$ source, elliptic. 5. Describe the SIMPLE loop: momentum predictor, pressure correction, velocity correction, repeat.
> - **Common mistakes:** treating pressure as if it had its own evolution equation in incompressible flow; blaming yourself for a poor drag coefficient on a coarse inviscid grid.
> - **Practise:** [[#3. The pressure equation]] · [[#Why under-relaxation helps]]

This and the following lecture were given back to back to fill in what the course had not yet covered: the grids, the numerical method behind Fluent's pressure-based option, and (in [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality|A11]]) how to verify and validate the results (2025-11-06, ll. 1–30). The end of this lecture went through the coursework report template.

Grid design is a question of where to put a limited number of points. The accuracy depends mostly on how dense the grid is where the flow is difficult, near walls, round leading edges and in wakes, and every point placed where nothing happens, in the uniform free stream, is wasted. Structured grids make the computer's job easy but force points where they are not needed; unstructured grids put points anywhere but cost more per point. The pressure problem is a different kind of constraint: in incompressible flow pressure is not carried along by the flow but is whatever field keeps the velocity divergence-free everywhere at once, so every pressure update reaches the whole domain.

## 1. Cell types and structured grids

In 2D the cells are triangles or quadrilaterals; in 3D, tetrahedra ("tets"), hexahedra ("hexes"), prisms (wedges), pyramids to join hex and tet regions, and arbitrary polyhedra (ll. 41–55). The boundary-layer lab uses stretched quadrilaterals.

> [!warning] Lecture slip (2025-11-06, ll. 41–55)
> The 2D options are given as "triangles ... or prisms which would just be quadrilateral elements", and in 3D "prisms, which would be hex cells". A prism has triangular ends and is not a hexahedron; the stretched boundary-layer cells the lecture means are quadrilaterals in 2D and hexahedra or prisms (wedges) in 3D.

In a structured grid the grid lines of one family never cross each other and cross each line of the other family once, so every cell has an index $(i,j)$ or $(i,j,k)$ and a fixed set of neighbours, four in 2D and six in 3D (ll. 56–100). Loops over $i$ run through consecutive memory, which compilers and vector processors handle efficiently, and the matrix has a regular structure that fast solvers can exploit. Structured grids are also usually more accurate. Their drawbacks are that complex geometries are "horrible" to grid (structured gridding of a complete aircraft is a full-time job in an aerodynamics department) and that point distribution is hard to control: the clustering needed at an aerofoil surface carries dense lines far into the free stream where $u=U_\infty$ and nothing is happening.

Three topologies are common round aerofoils (ll. 101–135):

| Topology | Shape of the grid lines | Good for |
|---|---|---|
| H-grid | one family runs streamwise, through the gap between blades | turbomachinery cascades |
| O-grid | closed loops round the body, the other family radial | inviscid aerofoils; the wake is poorly resolved |
| C-grid | lines wrap round the leading edge and continue downstream as a wake | viscous aerofoils, where the wake matters |

Each maps to a rectangular block in computational space, with the boundary conditions applied along its edges: for the H-grid, no-slip on the blade segments and outflow at the downstream edge. For a C-grid the $\xi$ index runs from the bottom of the wake round the leading edge to the top, and $\eta$ runs away from the wall.

A complete aircraft is gridded in blocks, possibly a hundred, each structured (ll. 136–175). A student asked whether grid density changes as abruptly between blocks as on the slide. Block interfaces may be point-matched or may need interpolation, and interpolation errors in an important region of the flow are "bad news", so interfaces belong where little is happening. Overset (chimera) grids overlap and interpolate between each other, which suits moving parts such as a helicopter blade mesh rotating over a fuselage mesh.

## 2. Unstructured, viscous and adapted grids

Unstructured cells have no ordering and any number of neighbours (ll. 146–160). They fit any shape, refine easily and are generated automatically, as in the wing lab's single "generate mesh" click. In exchange the connectivity has to be stored explicitly and memory access jumps about, so the code is slower and vectorises badly, and triangles in a boundary layer give high truncation errors (ll. 31–40). As long as the flux leaving each cell enters its neighbour, conservation over the domain still holds.

A viscous grid is a different object from an inviscid one (ll. 176–205). After the boundary-layer lab you know how thin the layer is and how strongly the cells must be stretched to fit enough of them inside it; the wing lab's inviscid mesh is nowhere near the $y_1^+$ needed ([[First-Cell Height and y-plus]]). The popular answer is a hybrid grid: inflation layers of stretched cells on the walls, an unstructured fill outside, where there may not be much fluid mechanics going on.

The wing lab's optional grid adaptation shows where the automatic grid is short of points (ll. 206–265). Most students' lift was within about 5 % of the lifting-line prediction and the pitching moment also agreed well; the drag was poor, and several emailed thinking they had made a mistake. Prof Sandham's answer is that it may not be their fault. At small angles the induced drag is small, and with about ten cells across the section thickness and up to a million cells overall the CFD cannot resolve it; the lifting-line theory has limitations of its own, reducing the wing to a line. After three rounds of adaptation the solver had added cells round the leading edge and, above all, in the wake: the original grid was not resolving the trailing vortex sheet, so the downwash and the induced drag were wrong. The grid study in the report should show which coefficients are grid-sensitive; a 10-million-cell run on Iridis would test whether more cells fix the drag.

## 3. The pressure equation

In incompressible flow the density equation does nothing, leaving four unknowns $u$, $v$, $w$, $p$, three momentum equations of the form $\partial(\cdot)/\partial t=\dots$, and continuity, which is only a constraint that the velocity be divergence-free at every step (ll. 266–285). That is why Fluent's pressure-based option is needed. Write the momentum equation in index form with backward Euler, the right side at $n+1$ (ll. 286–300):

$$
(\rho u_i)^{n+1}-(\rho u_i)^n=\Delta t\left(-\frac{\partial(\rho u_iu_j)}{\partial x_j}-\frac{\partial p}{\partial x_i}+\frac{\partial\tau_{ij}}{\partial x_j}\right)^{n+1}.
$$

Here $i$ and $j$ each run independently over 1, 2, 3, so $\partial\tau_{ij}/\partial x_j$ stands for nine terms (ll. 301–320). Differentiate every term with respect to $x_i$ (summing over $i$):

$$
\frac{\partial(\rho u_i)^{n+1}}{\partial x_i}-\frac{\partial(\rho u_i)^n}{\partial x_i}=\Delta t\left(-\frac{\partial^2(\rho u_iu_j)}{\partial x_i\,\partial x_j}-\frac{\partial^2p}{\partial x_i\,\partial x_i}+\frac{\partial^2\tau_{ij}}{\partial x_i\,\partial x_j}\right)^{n+1}.
$$

Continuity makes both terms on the left zero:

$$
0=-\frac{\partial^2(\rho u_iu_j)}{\partial x_i\,\partial x_j}-\frac{\partial^2p}{\partial x_i\,\partial x_i}+\frac{\partial^2\tau_{ij}}{\partial x_i\,\partial x_j}.
$$

Move the pressure term to the left:

$$
\frac{\partial^2p}{\partial x_i\,\partial x_i}=\frac{\partial^2}{\partial x_i\,\partial x_j}\left(\tau_{ij}-\rho u_iu_j\right)^{n+1}.
$$

The left side is $\partial^2p/\partial x^2+\partial^2p/\partial y^2+\partial^2p/\partial z^2=\nabla^2p$, a Laplacian, and the right side is non-zero, so this is a Poisson equation for pressure. It is elliptic, like the steady heat equation, which is why the iterative solvers of [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|A3]] matter. The catch is that its right side needs the velocity at $n+1$, while the velocity at $n+1$ needs the pressure: momentum and pressure form one coupled system.

## 4. SIMPLE and the segregated and coupled solvers

By the end of the 1960s the question was how to solve this coupled nonlinear system at all (ll. 321–335). SIMPLE (Semi-Implicit Method for Pressure-Linked Equations) "was an attempt to make it simple, which isn't very simple". Its loop is:

1. Start from the previous velocity field, which is divergence-free.
2. Solve the momentum equations for a provisional velocity using the current pressure.
3. Solve the pressure (correction) equation built from the provisional velocity.
4. Correct the velocities and face mass fluxes with the new pressure.
5. Repeat from step 2 until converged; the pressure and velocity then satisfy the original equations.

SIMPLE, SIMPLEC and PISO are variants of this idea, all segregated algorithms: the $u$, $v$ and $w$ momentum equations, then the pressure equation, then any extra equations such as $k$ and $\varepsilon$ are solved one at a time in sequence, and the loop repeats if not converged (ll. 334–350). SIMPLE needs under-relaxation; SIMPLEC is a consistent variant that tolerates larger factors; PISO adds corrector steps and needs no under-relaxation (ll. 386–395).

A coupled solver instead solves the three momentum equations and the pressure equation together as one large matrix, then the turbulence equations separately (ll. 351–380). Asked for the advantage, the class suggested correctly that it needs fewer iterations; the disadvantage is about four times the storage and four times the matrix size. Which works better is problem-dependent: a set-up that suits a wing may not suit a supersonic intake, so switching between them is one of the things to try when convergence stalls.

| | Segregated (SIMPLE family) | Coupled |
|---|---|---|
| Order of solution | $u$, $v$, $w$, pressure, then turbulence, in turn | momentum and pressure together, then turbulence |
| Memory | low | about four times higher |
| Iterations | more | fewer, each more work |

Under-relaxation is the opposite of the SOR over-relaxation of A3 (ll. 376–395):

$$
\phi_{new}=\phi_{old}+\alpha\,\Delta\phi,
\qquad
\alpha<1,
$$

accepting only part of each computed change. Fluent's panel shows eight separate factors (its defaults include about 0.3 for pressure, 0.7 for momentum and 0.8 for the turbulence quantities). If residuals oscillate or diverge, lower them, or lower the order of the turbulence equations as in [[SESA2029 A9 - Finite Volume Method|A9]].

Pressure-based methods were developed for incompressible flow; density-based methods, which march $\partial\rho/\partial t$ and get pressure from the equation of state, for supersonic flow (ll. 391–410). Both have since been extended, so pressure-based solvers handle transonic flow and density-based solvers reach lower Mach numbers, but hypersonic problems such as re-entry still need a density-based solver. Pressure-based is the default starting point unless the flow is around Mach 4 or above. The fourth-year Applications of CFD module covers the algorithms in depth.

## 5. Coursework report guidance

The last fifteen minutes went through the CFD report template (ll. 431–650). Keep to the boxes, the margins, an easily read font of at least 11 pt, and the 10-page limit. The front page is one good picture of the OpenVSP wing, with name, ID and the Python parameters; if the original NACA section broke the CAD-to-ANSYS import (an amber rather than green tick), give both the original and the section actually used. Marks run at roughly ten per page, and perhaps half to 60 % of the space will be figures; "a figure in an AIAA journal paper is worth 200 words".

The wing sections are: grid generation (screenshots, a table of the coarse, medium and fine meshes with cell counts, and any improvement made with the mesh and face-sizing parameters); the convergence study, both grid convergence of $C_L$, $C_D$ and $C_m$ and convergence of the residuals, with one example residual plot; and the aerodynamic study, plotting $C_L$ against $\alpha$, $C_D$ against $C_L$ and $C_m$ against $\alpha$, and comparing the lift slope and aerodynamic centre with theory. The minimum is five runs: three meshes at one angle and three angles on one mesh, sharing a case. A case run with walls on the upper and lower far-field boundaries would show the sensitivity to the boundary condition.

The boundary-layer sections need the grid and residual convergence again, then the laminar profile compared with Blasius on one set of axes, $u/U_e$ against $y/\delta^*$ with Blasius as a line and CFD as symbols, and for the turbulent case the $y_1^+$ achieved and the profile against the log law in semi-log axes, or a power law. The final discussion is about what CFD has been good and bad at in these problems, followed by the AI declaration. Write concisely: "a typical criticism ... is that we're just saying the same thing over and over again".

## Worked examples

### Why under-relaxation helps

Take a one-variable fixed-point iteration $\phi\leftarrow g(\phi)$ with $g(\phi)=2-1.5\phi$, whose solution is $\phi=0.8$. With under-relaxation the update is

$$
\phi_{new}=\phi_{old}+\alpha\left(g(\phi_{old})-\phi_{old}\right).
$$

The error $e=\phi-0.8$ is multiplied each step by

$$
1+\alpha\left(g'-1\right)=1-2.5\alpha.
$$

Starting from $\phi=0$, recomputed in Python:

| $\alpha$ | Factor | First five iterates |
|---|---|---|
| 1 (no relaxation) | −1.5 | 2.0, −1.0, 3.5, −3.25, 6.875: diverges |
| 0.5 | −0.25 | 1.0, 0.75, 0.8125, 0.7969, 0.8008 |
| 0.4 | 0 | 0.8 in one step |

The raw iteration overshoots by more each time, the oscillating residual a too-aggressive solver shows; taking only part of each change turns it into a converging one. The real solvers have one such factor per equation.

### Aerodynamic centre from three CFD cases

The template asks how to get the aerodynamic centre from the pitching moments (ll. 541–570). The aerodynamic centre is where the moment does not change with lift, so with moments about the leading edge,

$$
\frac{x_{ac}}{c}=-\frac{dC_{m,LE}}{dC_L}.
$$

For illustrative results $C_L=0.22$, 0.44, 0.66 and $C_{m,LE}=-0.058$, $-0.113$, $-0.168$, a least-squares line has slope $-0.250$, so $x_{ac}=0.25c$, as thin-aerofoil theory predicts. The centre of pressure, $x_{cp}/c=-C_{m,LE}/C_L$, moves from $0.264c$ to $0.255c$ over the same range, which is why it is the slope and not the ratio that locates the aerodynamic centre ([[Aerodynamic Centre and Centre of Pressure]]).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A9 - Finite Volume Method]]
- Next: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Concepts: [[Structured, Unstructured and Hybrid Grids]] · [[Pressure-Velocity Coupling and SIMPLE]] · [[Jacobi, Gauss-Seidel and SOR Iteration]]
- Wall resolution: [[First-Cell Height and y-plus]]
- FEA meshing counterpart: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]

## Sources

- `All_lectures_as_delivered.pdf`, L11, pp. 143–164 (grid figures after Blazek), with transcript `SESA2029 Lecture 2025-11-06.txt` (Prof N. Sandham)
- Fluent default under-relaxation factors from the solver panel
- Worked examples recomputed in Python; the aerodynamic-centre data are illustrative, not from the lecture

## Self-study tasks

### Core

- [ ] Derive the pressure Poisson equation from the implicit momentum equation (2025-11-06, ll. 286–320). → [[#3. The pressure equation]]
- [ ] Compare structured and unstructured grids and sketch H, O and C grids round an aerofoil, saying what each is good for (ll. 56–175). → [[#1. Cell types and structured grids]]
- [ ] Explain the SIMPLE loop and the trade-off between segregated and coupled solvers (ll. 321–380). → [[#4. SIMPLE and the segregated and coupled solvers]]
- [ ] Wing report: grid study of $C_L$, $C_D$, $C_m$, one residual plot, and the aerodynamic centre from the slope of $C_m$ against $C_L$ (ll. 491–570). → [[#5. Coursework report guidance]] · [[#Aerodynamic centre from three CFD cases]]

### Further practice

- [ ] Optional lab extension: adapt the wing grid and see where the cells go; discuss what that says about the induced drag (ll. 206–265). → [[#2. Unstructured, viscous and adapted grids]]
- [ ] Repeat the under-relaxation example with $g(\phi)=2-3\phi$ and find the range of $\alpha$ that converges (suggested, not lecturer-set). → [[#Why under-relaxation helps]]

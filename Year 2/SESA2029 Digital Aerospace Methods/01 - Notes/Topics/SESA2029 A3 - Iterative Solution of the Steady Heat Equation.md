---
title: "SESA2029 A3 - Iterative Solution of the Steady Heat Equation"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 3
tags: [sesa2029, cfd, heat-equation, iterative-methods, residual]
aliases: ["Steady heat equation", "Jacobi Gauss-Seidel SOR", "CFD Lectures 4-5"]
date: 2026-10-30
status: lectured
coverage: "Weeks 2–3 (2025-10-10; 2025-10-16, ll. 1–240)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
next_topics: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
key_concepts: ["[[Jacobi, Gauss-Seidel and SOR Iteration]]", "[[Residual vs Solution Error]]", "[[Finite Difference Approximations]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L4–L5)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-10.txt", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-16.txt"]
---

# SESA2029 A3 - Iterative Solution of the Steady Heat Equation

> [!abstract] Summary
> An energy balance on a thin slab gives the heat equation $\partial T/\partial t=\alpha\,\partial^2T/\partial x^2$, the first of several conservation laws derived this way. At steady state it becomes $T''=0$, and the central difference turns it into a tridiagonal linear system. Direct solution by Gaussian elimination is exact but far too expensive for CFD-sized grids, so codes iterate: Jacobi, Gauss–Seidel, successive over-relaxation, and library Krylov solvers such as conjugate gradients and GMRES. Convergence is measured by the residual, which shows how well the discrete equations balance, not how close the answer is to the truth.

> [!summary]- Exam use: quick path
> - **Use it when:** you must discretise a steady diffusion problem, write an iterative update, or explain residuals and convergence.
> - **Assumptions:** uniform grid; Dirichlet (fixed-temperature) boundaries; constant properties.
> - **Method:** 1. Discretise $T''=0$ as $T_{j-1}-2T_j+T_{j+1}=0$ at interior points. 2. Add boundary rows. 3. Jacobi: $T_j^{n+1}=\tfrac12(T_{j-1}^n+T_{j+1}^n)$. 4. Gauss–Seidel: use $T_{j-1}^{n+1}$ already computed; SOR: $T_j^{n+1}=(1-\omega)T_j^n+\omega\tilde T_j$. 5. Residual $R=\sqrt{\sum(T_{j-1}-2T_j+T_{j+1})^2}$; stop on the quantity of interest.
> - **Common mistakes:** reading the iteration superscript $n$ as a power; treating a small residual as proof of an accurate answer.
> - **Practise:** [[#Jacobi, Gauss-Seidel and SOR on the capsule wall]] · [[SESA2029 CFD Worked Examples#Q4: Steady heat equation: set-up and first iterations|CFD worked examples Q4]]

The model problem is the wall of a re-entry capsule: very hot outside, and to be kept at a sensible temperature inside for electronics or crew (2025-10-10, ll. 31–60). It is simple enough to have an exact solution, which makes it ideal for testing numerical methods, and it introduces the control-volume derivation used later for the Euler and Navier–Stokes equations.

The physical picture of an iterative method is information spreading. Start with the outer wall at 1200 K and everything else at 300 K, and let each interior point repeatedly take the average of its neighbours. On the first sweep only the point next to the hot wall changes; on the next, its neighbour starts to warm; the influence of the boundary creeps across the grid one point per sweep until the whole profile settles into the straight line that conduction requires. The better methods make that information travel faster.

## 1. The heat equation from a control volume

Take a slab of thickness $\delta x$ and unit area in the other two directions (ll. 31–125). A heat flux $\dot q$ (W/m²) enters on the left. One Taylor term gives the flux leaving on the right, $\dot q+\frac{\partial\dot q}{\partial x}\delta x$, which is enough as $\delta x\to0$. Energy conservation says the rate of change of internal energy in the slab equals heat in minus heat out. With $e$ the internal energy per unit mass (aerodynamicists keep $u$ for velocity),

$$
\frac{\partial(\rho e)}{\partial t}\delta x=\dot q-\left(\dot q+\frac{\partial\dot q}{\partial x}\delta x\right).
$$

Cancel $\dot q$ and divide by $\delta x$:

$$
\frac{\partial(\rho e)}{\partial t}=-\frac{\partial\dot q}{\partial x}.
$$

Two closures complete the model. Fourier's law says heat flows down the temperature gradient, $\dot q=-k\,\partial T/\partial x$, with $k$ the thermal conductivity. For an incompressible substance the density is constant, $c_p=c_v=c$, and $de=c\,dT$ by the definition of specific heat. Substituting both,

$$
\rho c\frac{\partial T}{\partial t}=k\frac{\partial^2T}{\partial x^2}
\quad\Longrightarrow\quad
\boxed{\frac{\partial T}{\partial t}=\alpha\frac{\partial^2T}{\partial x^2},\qquad\alpha=\frac{k}{\rho c}}
$$

where $\alpha$, in m²/s, is the thermal diffusivity. In 2D and 3D the right-hand side gains $\partial^2T/\partial y^2$ and $\partial^2T/\partial z^2$, the Laplacian, the same operator as in Laplace's equation for potential flow (2025-10-16, ll. 1–30). The same control-volume method applied to mass and momentum gives the Euler equations ([[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]]).

## 2. The steady problem and its discretisation

At steady state the time derivative vanishes, leaving an ordinary differential equation (ll. 126–180):

$$
\frac{d^2T}{dx^2}=0,\quad0<x<1,\qquad T(0)=1200\ \mathrm K,\quad T(1)=300\ \mathrm K.
$$

Integrating twice and fitting the boundary values gives the straight line $T=1200-900x$. Numerically, take $N=8$ intervals, $h=0.125$, and replace $T''$ at each interior point by the central difference. The right-hand side is zero, so the $h^2$ multiplies out:

$$
T_{j-1}-2T_j+T_{j+1}=0,\qquad j=1,\dots,7.
$$

That step from a continuous equation to discrete ones is discretisation. With the two boundary rows $T_0=1200$ and $T_8=300$, there are nine equations for nine unknowns (ll. 181–240):

$$
\begin{bmatrix}1&&&&\\1&-2&1&&\\&\ddots&\ddots&\ddots&\\&&1&-2&1\\&&&&1\end{bmatrix}
\begin{Bmatrix}T_0\\T_1\\\vdots\\T_7\\T_8\end{Bmatrix}
=\begin{Bmatrix}1200\\0\\\vdots\\0\\300\end{Bmatrix}.
$$

The boundary rows could be substituted in to leave a $7\times7$ system, but for a thousand unknowns the saving is negligible and the algebra risks mistakes, so modern practice is to "keep things simple" and code it directly (ll. 211–245).

## 3. Direct solution

Excel can invert the matrix and multiply by the right-hand side, but inverting a matrix is expensive and should never be done to solve a system (ll. 241–300). The direct method is Gaussian elimination. Forward elimination zeroes the entries below the diagonal: to clear $A_{21}$, subtract $A_{21}/A_{11}$ times row 1 from row 2, apply the same operation to the right-hand side, and continue down and across until the matrix is upper triangular. Back substitution then solves the last row, which has a single unknown, and works upwards.

Its cost grows roughly as the cube of the number of unknowns, and the coursework grids already have up to half a million cells: a $500\,000\times500\,000$ matrix is out of reach in time and memory (ll. 300–310). CFD therefore uses iterative methods, which start from a guess and improve it.

## 4. Iterative methods

The simplest iteration rearranges the discrete equation for the unknown at point $j$ and updates it from values already known (ll. 300–360):

$$
T_j^{n+1}=\tfrac12\left(T_{j-1}^n+T_{j+1}^n\right).
$$

This is the (point) Jacobi method. The superscript $n$ is the iteration counter, not a power (2025-10-16, ll. 31–60). Each point becomes the average of its neighbours. Jacobi is simple, and still used as a "smoother" inside multigrid methods, so some form of it is probably inside Fluent (2025-10-10, ll. 331–345).

In the spreadsheet demonstration the first sweep turns $T_1$ into $(1200+300)/2=750$ K and leaves the rest at 300 K; the change spreads one point per sweep (ll. 391–420). In 2D the update is the average of the four neighbours, and in 3D of the six; Excel's iterative-calculation option can then solve the 2D heat (Laplace) equation directly on a grid of coloured cells (ll. 451–480).

> [!warning] Lecture slip (2025-10-10, ll. 466–470)
> The 3D update is described as "dividing by eight neighbours", then listed as up, down, left, right, front and back. There are six, and the update divides by 6.

Gauss–Seidel is a practical improvement (2025-10-16, ll. 61–90). Looping upwards in $j$, the value at $j-1$ has already been updated in this sweep, so use it:

$$
T_j^{n+1}=\tfrac12\left(T_{j-1}^{n+1}+T_{j+1}^n\right).
$$

It is also easier to program than Jacobi, which needs a second array to hold the old values.

Successive over-relaxation (SOR) takes a bigger step in the direction the iteration is already going (ll. 91–125). With $\tilde T_j$ the Gauss–Seidel value and a relaxation factor $\omega$,

$$
T_j^{n+1}=(1-\omega)T_j^n+\omega\tilde T_j.
$$

$\omega=1$ is Gauss–Seidel. Over-relaxation, $1<\omega<2$, speeds a smooth, steady approach. Under-relaxation, $\omega<1$, damps an iteration that zig-zags or diverges, and that is exactly what the under-relaxation factors in Fluent's solution controls do. When a CFD run will not converge, the usual remedies, in order, are to check the grid, drop to first-order discretisation to get started, and reduce the under-relaxation factors (ll. 105–125).

The state of the art is a field of its own, packaged in libraries (ll. 121–155). Conjugate gradient methods minimise along two well-chosen directions at once, like descending a mountain diagonally to the chalet rather than straight down the steepest face; GMRES (generalised minimum residual) is the robust general alternative. Fluent calls such routines whenever it solves a matrix.

## 5. Residual versus error

The residual measures how well the current values satisfy the discrete equations (2025-10-10, ll. 361–425):

$$
R^n=\sqrt{\sum_j\left(T^n_{j-1}-2T^n_j+T^n_{j+1}\right)^2}.
$$

The error measures the distance from the exact solution of the original equation. They are different things: once the iteration has converged the residual is zero, but on a coarse grid the discrete solution can still differ from the true one. "If you converge it successfully to get the residual down to zero, you'll probably still have the wrong lift, drag and pitching moment"; the grid must also be refined (ll. 386–395).

Residual plots are the first thing a CFD code shows, and for real problems they fall and then flatten instead of reaching zero (ll. 481–510). Prof Sandham's advice is to judge convergence by the quantity of interest: watch how the lift, drag and pitching moment settle as iterations proceed. A sensitive pitching moment may need a much lower residual than the lift does.

## Worked examples

### Jacobi, Gauss-Seidel and SOR on the capsule wall

Starting from 1200 K at the outer wall and 300 K everywhere else, with $N=8$, the iterations needed to bring the residual below $10^{-5}$ K, recomputed in Python:

| Method | Iterations | $T_4$ (exact 750 K) |
|---|---|---|
| Jacobi | 215 | 750.0000 |
| Gauss–Seidel | 105 | 750.0000 |
| SOR, $\omega=1.4$ | 35 | 750.0000 |
| SOR, $\omega=1.5$ | 26 | 750.0000 |

After 50 iterations the lecture's comparison showed Jacobi at 739.6 K at the midpoint, Gauss–Seidel at 749.8 K and SOR at 749.999 K, while GMRES gave the exact answer directly (2025-10-16, ll. 151–210). Gauss–Seidel halves the Jacobi count, and a well-chosen $\omega$ gains another factor of four or more; the best $\omega$ has to be found by tuning.

![[dam_heat_iterative_residuals.png|620]]

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Next: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] (the unsteady version, second half of 2025-10-16)
- Concepts: [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Residual vs Solution Error]] · [[Finite Difference Approximations]]
- The same linear system in FEA: [[Matrix Displacement Method]]
- Laplace's equation in aerodynamics: [[Streamfunction and Velocity Potential]]

## Sources

- `All_lectures_as_delivered.pdf`, L4–L5, with transcripts `SESA2029 Lecture 2025-10-10.txt` (derivation, direct solution, Jacobi, spreadsheet demonstrations, residuals) and `SESA2029 Lecture 2025-10-16.txt`, ll. 1–240 (Gauss–Seidel, SOR, Krylov solvers, Python demonstration)
- The spreadsheet and Python codes are on Blackboard; iteration counts recomputed in Python

## Self-study tasks

### Core

- [ ] Example sheet Q2: modify the spreadsheet or code to implement your own iterative method (set at the end of 2025-10-10, ll. 511–520). → [[#4. Iterative methods]] · [[SESA2029 CFD Worked Examples#Q4: Steady heat equation: set-up and first iterations|Worked examples Q4]]
- [ ] Derive the heat equation from an energy balance on a control volume (2025-10-10, ll. 31–125). → [[#1. The heat equation from a control volume]]
- [ ] Explain the difference between the residual and the error, and how you would judge convergence of a wing calculation (ll. 361–510). → [[#5. Residual versus error]]

### Further practice

- [ ] Download the Python codes and compare Jacobi, Gauss–Seidel, SOR and GMRES yourself; find the best $\omega$ (2025-10-16, ll. 151–210). → [[#Jacobi, Gauss-Seidel and SOR on the capsule wall]]
- [ ] Set up the 2D Laplace equation in Excel with iterative calculation enabled (2025-10-10, ll. 451–480). → [[#4. Iterative methods]]
- [ ] Carry out Gaussian elimination by hand on a small tridiagonal system. → [[#3. Direct solution]]

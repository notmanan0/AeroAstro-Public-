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
> An energy balance on a thin slab gives the heat equation $\partial T/\partial t=\alpha\,\partial^2T/\partial x^2$, and the same control-volume method gives the other conservation laws. At steady state it becomes $T''=0$, and the central difference turns it into a tridiagonal linear system. Direct solution by Gaussian elimination is exact but its cost grows as the cube of the number of unknowns, so CFD codes iterate: Jacobi, Gauss–Seidel, successive over-relaxation, and library Krylov solvers such as conjugate gradients and GMRES. Convergence is measured by the residual, which shows how well the discrete equations balance, not how close the answer is to the truth.

> [!summary]- Exam use: quick path
> - **Use it when:** you must discretise a steady diffusion problem, write an iterative update, carry out a few sweeps by hand, or explain residuals and convergence.
> - **Assumptions:** uniform grid; Dirichlet (fixed-temperature) boundaries; constant properties; no heat sources.
> - **Method:** 1. Discretise $T''=0$ as $T_{j-1}-2T_j+T_{j+1}=0$ at interior points. 2. Add boundary rows. 3. Jacobi: $T_j^{n+1}=\tfrac12(T_{j-1}^n+T_{j+1}^n)$. 4. Gauss–Seidel: use $T_{j-1}^{n+1}$ already computed; SOR: $T_j^{n+1}=(1-\omega)T_j^n+\omega\tilde T_j$. 5. Residual $R=\sqrt{\sum(T_{j-1}-2T_j+T_{j+1})^2}$; judge convergence on the quantity of interest.
> - **Common mistakes:** reading the iteration superscript $n$ as a power; treating a small residual as proof of an accurate answer.
> - **Practise:** [[#First sweeps by hand]] · [[SESA2029 CFD Worked Examples#Q4: Steady heat equation: set-up and first iterations|CFD worked examples Q4]]

The model problem is the wall of a re-entry capsule: very hot outside, and to be kept at a sensible temperature inside for electronics or crew (L4 slide 3). It is simple enough to have an exact solution, which makes it ideal for testing numerical methods, and its control-volume derivation carries over to the Euler and Navier–Stokes equations.

The physical picture of an iterative method is information spreading. With the outer wall at 1200 K and everything else at 300 K, each interior point repeatedly takes the average of its neighbours. On the first sweep only the point next to the hot wall changes; on the next, its neighbour starts to warm. The influence of the boundary creeps across the grid one point per sweep until the whole profile settles into the straight line that conduction requires. Better methods make that information travel faster, and the factor by which they shrink the error on each sweep is what separates them.

## 1. The heat equation from a control volume

A slab of thickness $\delta x$ and unit length in $y$ and $z$ (L4 slide 4) receives a heat flux $\dot q$ (W/m², heat per unit area per unit time) on its left face. One Taylor term gives the flux leaving on the right, $\dot q+\frac{\partial\dot q}{\partial x}\delta x$, which is enough as $\delta x\to0$. Energy conservation says the rate of change of internal energy in the slab equals heat in minus heat out. With $e$ the internal energy per unit mass (aerothermodynamics keeps $u$ for velocity), the energy in the slab is $\rho e\,\delta x$ per unit area, so

$$
\frac{\partial(\rho e)}{\partial t}\delta x=\dot q-\left(\dot q+\frac{\partial\dot q}{\partial x}\delta x\right).
$$

Cancel $\dot q$ on the right:

$$
\frac{\partial(\rho e)}{\partial t}\delta x=-\frac{\partial\dot q}{\partial x}\delta x.
$$

Divide by $\delta x$:

$$
\frac{\partial(\rho e)}{\partial t}=-\frac{\partial\dot q}{\partial x}.
$$

Two closures complete the model. Fourier's law says heat flows down the temperature gradient,

$$
\dot q=-k\frac{\partial T}{\partial x},
$$

with $k$ the thermal conductivity in W/(m K). For an incompressible substance the density is constant and all the specific heats are equal, $c_p=c_v$, so $\mathrm de=c_p\,\mathrm dT$. Substitute both, with $k$ constant:

$$
\rho c_p\frac{\partial T}{\partial t}=-\frac{\partial}{\partial x}\left(-k\frac{\partial T}{\partial x}\right)=k\frac{\partial^2T}{\partial x^2}.
$$

Divide by $\rho c_p$:

$$
\boxed{\frac{\partial T}{\partial t}=\alpha\frac{\partial^2T}{\partial x^2},\qquad\alpha=\frac{k}{\rho c_p}}
$$

where $\alpha$, in m²/s, is the thermal diffusivity. The variables depend on both $x$ and $t$, hence the partial derivatives. In 2D and 3D the right-hand side gains $\partial^2T/\partial y^2$ and $\partial^2T/\partial z^2$, the Laplacian, so the steady equation is Laplace's equation, the same operator as for potential flow in SESA2022. The same control-volume method applied to mass and momentum gives the Euler equations ([[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]]).

## 2. The steady problem and its discretisation

At steady state the time derivative vanishes, leaving an ordinary differential equation (L4 slide 5):

$$
\frac{\mathrm d^2T}{\mathrm dx^2}=0,\quad0<x<1,\qquad T(0)=1200\ \mathrm K,\quad T(1)=300\ \mathrm K.
$$

Integrate once, $\mathrm dT/\mathrm dx=C_1$, and again, $T=C_1x+C_2$. The left boundary gives $C_2=1200$; the right gives $C_1+1200=300$, so $C_1=-900$ and

$$
T=1200-900x.
$$

Numerically, take $N=8$ intervals, $h=0.125$, and replace $T''$ at each interior point by the central difference of [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]]:

$$
\frac{T_{j-1}-2T_j+T_{j+1}}{h^2}=0.
$$

The right-hand side is zero, so multiplying by $h^2$ removes the spacing:

$$
T_{j-1}-2T_j+T_{j+1}=0,\qquad j=1,\dots,7.
$$

That step from a continuous equation to a set of algebraic ones is discretisation. With the two boundary rows $T_0=1200$ and $T_8=300$ there are nine equations for nine unknowns (L4 slide 6):

$$
\begin{bmatrix}
1&0&0&0&0&0&0&0&0\\
1&-2&1&0&0&0&0&0&0\\
0&1&-2&1&0&0&0&0&0\\
0&0&1&-2&1&0&0&0&0\\
0&0&0&1&-2&1&0&0&0\\
0&0&0&0&1&-2&1&0&0\\
0&0&0&0&0&1&-2&1&0\\
0&0&0&0&0&0&1&-2&1\\
0&0&0&0&0&0&0&0&1
\end{bmatrix}
\begin{Bmatrix}T_0\\T_1\\T_2\\T_3\\T_4\\T_5\\T_6\\T_7\\T_8\end{Bmatrix}
=\begin{Bmatrix}1200\\0\\0\\0\\0\\0\\0\\0\\300\end{Bmatrix}.
$$

The boundary rows could be substituted into the first and last interior rows to leave a $7\times7$ system. For a thousand unknowns the saving is negligible and the extra algebra invites mistakes, so in practice the boundary rows are kept and coded directly. The matrix is tridiagonal: each row couples a point only to its two neighbours, which is what makes iterative methods cheap per sweep.

> [!check] The discrete solution is exact here
> The central difference has error $-\tfrac{h^2}{12}T''''$, and the exact solution is a straight line with $T''''=0$, so the discrete equations are satisfied exactly by $T_j=1200-900jh$: the constant parts give $1200-2400+1200=0$ and the linear parts give $-900h\left[(j-1)-2j+(j+1)\right]=0$. On this problem every error left after convergence is iteration error, none is discretisation error. That is unusual, and in A4 the unsteady problem loses this property.

## 3. Direct solution by Gaussian elimination

A spreadsheet can invert the matrix and multiply by the right-hand side, but inverting a matrix is expensive and is never the way to solve a system. The direct method is Gaussian elimination with back substitution (L4 slides 7–8). Forward elimination turns $\mathbf A$ into an upper triangular matrix $\mathbf U$: to clear $A_{21}$, subtract $A_{21}/A_{11}$ times row 1 from row 2, apply the same operation to the right-hand side, treat $A_{31},\dots,A_{n1}$ the same way, then repeat on the next column. Back substitution solves the last equation, which has a single unknown, and works upwards.

On the $7\times7$ interior system, substituting $T_0=1200$ and $T_8=300$ moves them to the right-hand side:

$$
-2T_1+T_2=-1200,\qquad T_{j-1}-2T_j+T_{j+1}=0\ (j=2,\dots,6),\qquad T_6-2T_7=-300.
$$

Row 2 is $T_1-2T_2+T_3=0$. The multiplier is $A_{21}/A_{11}=1/(-2)=-\tfrac12$; subtracting $-\tfrac12\times$ row 1 means adding half of row 1:

$$
\left(-2+\tfrac12\right)T_2+T_3=0+\tfrac12(-1200)
\quad\Longrightarrow\quad
-\tfrac32T_2+T_3=-600.
$$

Row 3 has multiplier $1/(-\tfrac32)=-\tfrac23$:

$$
\left(-2+\tfrac23\right)T_3+T_4=\tfrac23(-600)
\quad\Longrightarrow\quad
-\tfrac43T_3+T_4=-400.
$$

The pattern continues: after elimination row $k$ reads $-\tfrac{k+1}{k}T_k+T_{k+1}=-1200/k$, giving $-\tfrac54T_4+T_5=-300$, $-\tfrac65T_5+T_6=-240$ and $-\tfrac76T_6+T_7=-200$. The last row, $T_6-2T_7=-300$, has multiplier $1/(-\tfrac76)=-\tfrac67$:

$$
\left(-2+\tfrac67\right)T_7=-300+\tfrac67(-200)
\quad\Longrightarrow\quad
-\tfrac87T_7=-\tfrac{3300}{7}
\quad\Longrightarrow\quad
T_7=412.5\ \mathrm K.
$$

Back substitution then climbs the rows: $T_6=(-200-T_7)/(-\tfrac76)=525$, $T_5=(-240-525)/(-\tfrac65)=637.5$, and so on up to $T_1=1087.5$ K, every value on the exact line.

The cost of elimination on a full matrix grows roughly as the cube of the number of unknowns (L4 slide 9). The coursework grids already have up to half a million cells, and a $500\,000\times500\,000$ system is out of reach in both time and memory. CFD therefore uses iterative methods, which start from a guess and improve it.

## 4. Iterative methods

### Jacobi

The simplest iteration rearranges the discrete equation for the unknown at point $j$,

$$
2T_j=T_{j-1}+T_{j+1},
$$

and updates it from the values of the previous sweep (L4 slide 9):

$$
T_j^{n+1}=\tfrac12\left(T_{j-1}^n+T_{j+1}^n\right).
$$

This is the (point) Jacobi method. The superscript $n$ is the iteration counter, not a power: read $T_j^{n+1}$ as the temperature at grid point $j$ at iteration level $n+1$. Each point becomes the average of its neighbours. Jacobi is simple, and it is still used as a smoother inside multigrid methods, so some form of it is probably inside Fluent.

![[dam_heat_jacobi_spreading.png|900]]

The figure shows the information spreading. After one sweep only $T_1$ has moved, to $(1200+300)/2=750$ K; after two, $T_2$ follows; after eight sweeps the warm front has crossed the wall, and it then takes over a hundred more for the profile to straighten.

In 2D, with equal spacing $h$ in $x$ and $y$, the steady equation is $\partial^2T/\partial x^2+\partial^2T/\partial y^2=0$. Use the central difference in each direction:

$$
\frac{T_{i-1,j}-2T_{i,j}+T_{i+1,j}}{h^2}+\frac{T_{i,j-1}-2T_{i,j}+T_{i,j+1}}{h^2}=0.
$$

Multiply by $h^2$ and collect $T_{i,j}$:

$$
4T_{i,j}=T_{i-1,j}+T_{i+1,j}+T_{i,j-1}+T_{i,j+1},
$$

so the update is the average of the four neighbours. In 3D the same steps give the average of six: up, down, left, right, front and back. A spreadsheet with iterative calculation enabled solves the 2D problem directly on a grid of coloured cells (L4 slide 9, example (c)).

![[dam_laplace_2d.png|900]]

> [!check] The 2D centre temperature
> With one edge at 1200 K and three at 300 K, superposition of the four rotated one-hot-edge problems shows the centre must sit at the average of the edges, $(1200+3\times300)/4=525$ K. The 20×20 Gauss–Seidel solution in the figure gives 525.00 K.

### Gauss–Seidel

Gauss–Seidel is a practical improvement. Looping upwards in $j$, the value at $j-1$ has already been updated in this sweep, so use it:

$$
T_j^{n+1}=\tfrac12\left(T_{j-1}^{n+1}+T_{j+1}^n\right).
$$

It uses better information, since $T_{j-1}^{n+1}$ is already improved, and it is easier to program than Jacobi, which needs a second array to hold the old values; in Gauss–Seidel the array is overwritten in place.

### Successive over-relaxation

When the iteration is approaching the answer smoothly, it can take a bigger step in the direction it is already going. With $\tilde T_j$ the provisional Gauss–Seidel value and a relaxation factor $\omega$,

$$
T_j^{n+1}=(1-\omega)T_j^n+\omega\tilde T_j.
$$

Rewriting as $T_j^{n+1}=T_j^n+\omega(\tilde T_j-T_j^n)$ shows the meaning: $\omega$ scales the Gauss–Seidel correction. $\omega=1$ is Gauss–Seidel itself. Over-relaxation, $1<\omega<2$, speeds a smooth approach. Under-relaxation, $\omega<1$, damps an iteration that zig-zags or diverges, which is the role of the under-relaxation factors in Fluent's solution controls. When a CFD run will not converge, the usual remedies are, in order: check the grid, drop to first-order discretisation to get started, and reduce the under-relaxation factors.

### Library solvers

More advanced solvers are packaged in libraries. Steepest descent moves along the steepest slope towards a minimum; conjugate gradient methods choose each new search direction conjugate to the previous ones, so that progress made along earlier directions is not undone. GMRES (generalised minimum residual) is the robust general alternative, and in practice both are tried to see which works for a given problem. Fluent calls such routines whenever it solves a matrix.

## 5. Residual versus error

The residual measures how well the current values satisfy the discrete equations (L4 slide 10):

$$
R^n=\sqrt{\sum_j\left(T^n_{j-1}-2T^n_j+T^n_{j+1}\right)^2}.
$$

It should fall to zero when the iteration has converged. The error measures the distance from the exact solution of the original differential equation. They are different things. The residual being zero says the discrete equations balance; it says nothing about whether the grid is fine enough for the discrete solution to match the true one. Even with the residual converged to machine zero, the lift, drag and pitching moment of a wing will still carry discretisation error, and only grid refinement reveals it ([[Residual vs Solution Error]]).

The two can also disagree during the iteration. After 50 Jacobi sweeps on the capsule wall, $R=4.65$ K while the largest error is 10.4 K at the midpoint; after 50 Gauss–Seidel sweeps they are 0.057 K and 0.17 K. The residual understates the remaining error by a factor of two or three here. The residual is the discrete second difference of the error, and the slowly converging error is a smooth hump whose second difference is small, so a small residual can hide a sizeable error.

Residual plots are the first thing a CFD code shows, and for real problems they fall and then flatten instead of reaching zero. What level is acceptable depends on the quantity of interest and on how accurately it is needed (L4 slide 10): watch how the lift, drag, pitching moment or heat flux settle as the iterations proceed. A sensitive pitching moment may need a much lower residual than the lift.

## Worked examples

### First sweeps by hand

The iteration starts from $T_0=1200$ K and $T_1,\dots,T_8=300$ K, with $T_8$ fixed.

Jacobi, sweep 1: every update uses the old values.

$$
T_1^1=\tfrac12(1200+300)=750,\qquad T_2^1=\tfrac12(300+300)=300,\ \dots
$$

so only $T_1$ changes. The residual comes only from rows 1 and 2: $1200-1500+300=0$ at $j=1$ and $750-600+300=450$ at $j=2$, so $R^1=450$ K.

Jacobi, sweep 2: $T_1^2=\tfrac12(1200+300)=750$, $T_2^2=\tfrac12(750+300)=525$, the rest unchanged; $R^2=318.2$ K.

Gauss–Seidel, sweep 1: each update uses the newest value on its left.

$$
T_1=\tfrac12(1200+300)=750,\quad T_2=\tfrac12(750+300)=525,\quad T_3=\tfrac12(525+300)=412.5,
$$

$$
T_4=356.25,\quad T_5=328.13,\quad T_6=314.06,\quad T_7=307.03,
$$

and $R^1=259.8$ K. One Gauss–Seidel sweep carries the boundary information all the way across, because each point sees its updated left neighbour.

SOR with $\omega=1.4$, sweep 1: the first provisional value is $\tilde T_1=750$, so

$$
T_1=(1-1.4)\times300+1.4\times750=-120+1050=930.
$$

Then $\tilde T_2=\tfrac12(930+300)=615$ and $T_2=-0.4\times300+1.4\times615=741$, and so on, giving $R^1=120.3$ K.

### Iteration counts on the capsule wall

With the same start, the iterations needed to bring the residual below $10^{-5}$ K:

| Method | Iterations | $T_4$ after 50 sweeps (exact 750 K) | Residual ratio per sweep |
|---|---|---|---|
| Jacobi | 215 | 739.63 | 0.924 |
| Gauss–Seidel | 105 | 749.83 | 0.854 |
| SOR, $\omega=1.4$ | 35 | 750.0000 | — |
| SOR, $\omega=1.5$ | 26 | 750.0000 | — |

GMRES gives the exact answer directly. Gauss–Seidel halves the Jacobi count, and a well-chosen $\omega$ gains another factor of four. A scan of $\omega$ in steps of 0.01 finds the minimum, 23 iterations, near $\omega=1.45$–$1.47$, so the best $\omega$ has to be found by tuning.

![[dam_heat_iterative_residuals.png|900]]

> [!check] Why Gauss–Seidel takes half as many sweeps
> Once the start-up transient has passed, each Jacobi sweep multiplies the residual by 0.924 and each Gauss–Seidel sweep by 0.854. Since $0.924^2=0.854$, one Gauss–Seidel sweep does the work of two Jacobi sweeps, which is exactly the factor of two in the iteration counts (105 against 215).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Next: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]] (the unsteady version)
- Concepts: [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Residual vs Solution Error]] · [[Finite Difference Approximations]]
- The same linear system in FEA: [[Matrix Displacement Method]]
- Laplace's equation in aerodynamics: [[Streamfunction and Velocity Potential]]

## Sources

- `All_lectures_as_delivered.pdf`, L4 (slides 1–11; delivered twice, so pages 44–64 repeat), with transcripts `SESA2029 Lecture 2025-10-10.txt` (derivation, direct solution, Jacobi, spreadsheet demonstrations, residuals) and `SESA2029 Lecture 2025-10-16.txt`, ll. 1–240 (Gauss–Seidel, SOR, Krylov solvers, Python demonstration)
- The spreadsheet and Python codes are on Blackboard. Elimination by exact fractions, hand sweeps, iteration counts, residual ratios and the 2D solution recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a3_figures.py`

## Self-study tasks

### Core

- [ ] Example sheet Q2: modify the spreadsheet or code to implement your own iterative method (set at the end of 2025-10-10, ll. 511–520). → [[#4. Iterative methods]] · [[SESA2029 CFD Worked Examples#Q4: Steady heat equation: set-up and first iterations|Worked examples Q4]]
- [ ] Derive the heat equation from an energy balance on a control volume (L4 slide 4; 2025-10-10, ll. 31–125). → [[#1. The heat equation from a control volume]]
- [ ] Discretise the steady heat equation and extend it to 2D and 3D (L4 slide 11). → [[#2. The steady problem and its discretisation]] · [[#Jacobi]]
- [ ] Explain the difference between the residual and the error, and how you would judge convergence of a wing calculation (L4 slides 10–11). → [[#5. Residual versus error]]
- [ ] Do the first Jacobi, Gauss–Seidel and SOR sweeps by hand. → [[#First sweeps by hand]]

### Further practice

- [ ] Download the Python codes and compare Jacobi, Gauss–Seidel, SOR and GMRES yourself; find the best $\omega$ (2025-10-16, ll. 151–210). → [[#Iteration counts on the capsule wall]]
- [ ] Set up the 2D Laplace equation in Excel with iterative calculation enabled (L4 slide 9). → [[#Jacobi]]
- [ ] Carry out Gaussian elimination by hand on the $7\times7$ system (L4 slides 7–8). → [[#3. Direct solution by Gaussian elimination]]

## Transcript and slide slips

> [!warning] Lecture slip: neighbours in 3D (2025-10-10, ll. 466–470)
> Where: [[#Jacobi]].
>
> The 3D update is described as "dividing by eight neighbours", then listed as up, down, left, right, front and back. There are six, and the update divides by 6.

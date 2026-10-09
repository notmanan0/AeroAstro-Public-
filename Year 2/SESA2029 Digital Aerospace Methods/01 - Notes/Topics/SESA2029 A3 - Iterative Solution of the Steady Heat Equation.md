---
title: "SESA2029 A3 - Iterative Solution of the Steady Heat Equation"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 3
tags:
  - sesa2029
  - cfd
  - numerical-methods
  - iterative-methods
aliases: ["Heat equation iterative methods", "Jacobi Gauss-Seidel SOR"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
next_topics: ["[[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]"]
key_concepts: ["[[Jacobi, Gauss-Seidel and SOR Iteration]]", "[[Residual vs Solution Error]]", "[[Finite Difference Approximations]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L4, pp. 44–64; L5 pp. 65–70)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A3 - Iterative Solution of the Steady Heat Equation

> [!abstract] Summary
> **Model problem:** 1D conduction through a re-entry-capsule wall.
>
> An energy balance on a control volume gives the **heat equation** $\partial T/\partial t = \alpha\,\partial^2T/\partial x^2$. At steady state this is $T''=0$. Discretising with the central second difference gives a tridiagonal linear system $\mathbf A\mathbf T = \mathbf b$.
>
> **Direct solution** (Gaussian elimination) is exact but costs roughly $N^3$ operations, which is prohibitive in 2D and 3D. CFD therefore **iterates**, each method faster than the last:
> - **Jacobi**;
> - **Gauss–Seidel**, which uses the freshest values;
> - **SOR**, which takes bigger (or, when unstable, smaller) steps;
> - Krylov solvers (**CG, GMRES**).
>
> Convergence is monitored through the **residual** (how well the *discrete* equation balances). The residual is not the same thing as the error against the true solution.

## Key Concepts
- [[Jacobi, Gauss-Seidel and SOR Iteration]] · [[Residual vs Solution Error]] · [[Finite Difference Approximations]]

---

## 1. Physics: deriving the heat equation (L4)
Take a slab of thickness $\delta x$ with unit area in $y$ and $z$. Heat flux $\dot q$ enters on the left, and $\dot q+\frac{\partial\dot q}{\partial x}\delta x$ leaves on the right (the first Taylor term is enough as $\delta x\to0$). Energy conservation says the rate of change of internal energy equals heat in minus heat out:

$$
\frac{\partial(\rho e)}{\partial t}\delta x = \dot q-\left(\dot q+\frac{\partial\dot q}{\partial x}\delta x\right)\;\Rightarrow\;\frac{\partial(\rho e)}{\partial t} = -\frac{\partial\dot q}{\partial x}
$$

Two closures complete the model:
- **Fourier's law**: $\dot q = -k\,\partial T/\partial x$ (heat flows down the temperature gradient).
- **Incompressible substance**: $\rho$ is constant, $c_p = c_v = c$ and $de = c\,dT$.

$$
\boxed{\frac{\partial T}{\partial t} = \alpha\frac{\partial^2T}{\partial x^2},\qquad \alpha = \frac{k}{\rho c}\ \ [\mathrm{m^2/s}]}
$$

This control-volume argument is exactly the one reused for mass, momentum and energy in [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]].

## 2. Steady problem and discretisation (L4)
Solve $d^2T/dx^2 = 0$ on $0<x<1$ with $T(0) = 1200$ K (outer skin) and $T(1) = 300$ K (cabin). The exact solution is the straight line $T = 1200-900x$.

Use $N = 8$ intervals ($h = 0.125$) and the central difference. Since the right-hand side is zero, the $h^2$ cancels:

$$
T_{j-1}-2T_j+T_{j+1} = 0,\qquad j = 1,\dots,7
$$

The two boundary equations and seven interior equations give a $9\times9$ system:

$$
\begin{bmatrix}1&&&&\\1&-2&1&&\\&\ddots&\ddots&\ddots&\\&&1&-2&1\\&&&&1\end{bmatrix}\begin{Bmatrix}T_0\\T_1\\\vdots\\T_7\\T_8\end{Bmatrix} = \begin{Bmatrix}1200\\0\\\vdots\\0\\300\end{Bmatrix}
$$

You could substitute the boundary rows to leave a $7\times7$ system. At large $N$ that saving is negligible, so modern practice is to "keep it simple and code it" rather than do algebra by hand.

## 3. Direct solution: Gaussian elimination (L4)
- **Forward elimination**: to zero $A_{21}$, subtract $(A_{21}/A_{11})\times$ row 1 from row 2. Repeat down the column, then for each later column, until $\mathbf A$ becomes upper-triangular $\mathbf U$. Apply the same row operations to $\mathbf b$.
- **Back substitution**: the last row has one unknown. Solve it, then work upwards.
- **Never form $\mathbf A^{-1}$**: inverting the matrix is far more expensive than elimination.

Direct cost scales like $n^3$ for $n$ unknowns. A CFD grid has $10^5$–$10^8$ cells, so direct methods are impossible there: memory and time both blow up.

## 4. Iterative methods (L4–L5)
Rearrange the discrete equation to update one unknown at a time. $n$ is the iteration counter, a superscript index, **not a power**.

| Method | Update | Idea |
|---|---|---|
| **Jacobi** | $T_j^{n+1} = \tfrac12\left(T_{j-1}^{n}+T_{j+1}^{n}\right)$ | uses only old values; needs two arrays |
| **Gauss–Seidel** | $T_j^{n+1} = \tfrac12\left(T_{j-1}^{\color{red}{n+1}}+T_{j+1}^{n}\right)$ | looping $j$ upwards, $T_{j-1}$ is already updated, so use it |
| **SOR** | $T_j^{n+1} = (1-\omega)T_j^n+\omega\tilde T_j^{n+1}$ | $\tilde T$ is the Gauss–Seidel value; $\omega>1$ over-relaxes (bigger steps) |

- $\omega = 1$ is plain Gauss–Seidel.
- $1<\omega<2$ **over-relaxes**: use it when convergence is smooth and monotonic.
- $0<\omega<1$ **under-relaxes**: use it when iterates zig-zag or diverge. This is exactly the "under-relaxation factor" in commercial CFD solvers (see [[Pressure-Velocity Coupling and SIMPLE]]).

**In 2D** Jacobi updates each point to the average of its **4 neighbours** (up, down, left, right). In 3D it uses the average of its 6 neighbours. That is the 2D Laplace equation from potential flow (SESA2022), solvable even in a spreadsheet.

**State of the art.** Solvers minimise along cleverly chosen search directions, the way you would descend a mountain diagonally rather than straight down the steepest face:
- **Conjugate gradient** (symmetric systems);
- **BiCGSTAB**;
- **GMRES** (generalised minimum residual; robust and general). These Krylov methods sit inside commercial codes as black-box library calls.

## 5. Residual vs error (L4)

$$
R^n = \sqrt{\sum_j\left(T^n_{j-1}-2T^n_j+T^n_{j+1}\right)^2}
$$

- The **residual** measures how well the **discrete** equation is satisfied. It goes to zero when the *iteration* has converged.
- The **error** $\lVert T^n-T_{exact}\rVert$ measures distance from the **true** PDE solution. It includes the discretisation error, which is non-zero even when $R = 0$ if the grid is too coarse.

So a fully converged residual on a coarse grid can still give the wrong lift. You need **both** iterative convergence **and** a grid study. Judge convergence by the **quantity you care about**: lift, drag, pitching moment or heat flux. A sensitive pitching moment may need a lower residual than lift does. See [[Residual vs Solution Error]].

## 6. Performance (L5 demonstration, recomputed)
Start from $T = 300$ K inside with $T_0 = 1200$ K. Iterations needed to reach $R<10^{-5}$ K:

| Method | Iterations | $T_4$ (exact 750 K) |
|---|---|---|
| Jacobi | 215 | 750.0000 |
| Gauss–Seidel | 105 | 750.0000 |
| SOR $\omega = 1.4$ | 35 | 750.0000 |
| SOR $\omega = 1.5$ | 26 | 750.0000 |
| GMRES (library) | "black box" | exact |

![[dam_heat_iterative_residuals.png|600]]

Gauss–Seidel roughly halves the Jacobi count. A well-tuned $\omega$ gives another factor of 4–8. Real CFD residual histories are messier: they drop and then plateau, and you must decide when to stop.

> [!tip] If a CFD run won't converge, try in this order
> 1. **The grid.** Poor cells are the usual culprit.
> 2. **Drop to first order** (upwind) to get started, then switch back to second order.
> 3. **Reduce the under-relaxation factors.**

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] · Next: [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]
- The same $\mathbf K\mathbf d = \mathbf F$ linear-algebra problem appears in FEA: [[Matrix Displacement Method]]
- Laplace equation in aerodynamics: [[Streamfunction and Velocity Potential]]

## Sources
- CFD Lectures 4–5, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 44–70; transcript `CFD.txt` (spreadsheet and Python demonstrations)
- Iteration counts recomputed in Python (`scripts/make_figures.py`)

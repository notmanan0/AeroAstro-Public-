---
title: "SESA2029 A9 - Finite Volume Method"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 9
tags: [sesa2029, cfd, finite-volume]
aliases: ["FVM", "Finite volumes", "CFD Lecture 10"]
date: 2026-10-30
status: lectured
coverage: "Week 5 (2025-10-31)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]", "[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
next_topics: ["[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
key_concepts: ["[[Finite Volume Method]]", "[[Convective Interpolation Schemes]]", "[[CFD Boundary Conditions]]", "[[Conservation Form of the Governing Equations]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L10, pp. 130–142)", "02 - Sources/Lectures/SESA2029 Lecture 2025-10-31.txt", "Ferziger, Perić & Street, Computational Methods for Fluid Dynamics, Ch. 4"]
---

# SESA2029 A9 - Finite Volume Method

> [!abstract] Summary
> The finite volume method discretises the integral form of the conservation laws: the domain is split into cells, the unknowns sit at cell centres, and each cell's contents change only by the fluxes through its faces. Because the flux leaving one cell is the flux entering its neighbour, mass, momentum and energy are conserved exactly over the whole grid, on any cell shape. Taking the flux at the face centre times the face area is already second order, but the face value must be interpolated from the cell centres, by upwind, central or QUICK schemes, and that choice trades stability against accuracy.

> [!summary]- Exam use: quick path
> - **Use it when:** asked how a CFD code discretises the equations, the order of the midpoint rule, an interpolation formula, or what a boundary condition does.
> - **Assumptions:** Cartesian cells with compass notation; flow from W to E for the upwind formulas; uniform spacing for the simplified coefficients.
> - **Method:** 1. Write the integral balance for one cell. 2. Sum the face fluxes, each $\approx f_e\,\Delta y$ (midpoint rule, second order). 3. Interpolate $\phi_e$: UDS $\phi_P$, second-order upwind $\tfrac12(3\phi_P-\phi_W)$, CDS $\tfrac12(\phi_P+\phi_E)$, QUICK $\tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$. 4. Volume integrals $\approx q_P\Delta V$. 5. Apply boundary conditions through the boundary faces or ghost cells.
> - **Common mistakes:** taking the upwind value from the wrong side when the flow reverses (unstable); calling an inviscid wall different from a symmetry plane (they are the same condition).
> - **Practise:** [[#Interpolating a face value]] · [[SESA2029 CFD Worked Examples#Q11: QUICK coefficients|CFD worked examples Q11]] · [[SESA2029 CFD Worked Examples#Q12: Midpoint-rule surface integral error|Q12]]

Finite elements are the standard tool for solid mechanics (Part B); for fluids the standard is the finite volume method, built from the finite-difference tools of A2 to A6. Fluent is a finite volume code, and knowing its notation helps when choosing options, especially when a case will not converge.

The finite volume method gives the control volume of [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes|A7]] a finite size. Each cell stores how much of each conserved quantity it holds; what one cell exports through a face is the amount its neighbour imports through the same face, so however crude the estimate of that flux, nothing is created or lost between cells. Summed over the grid, the internal fluxes cancel in pairs and only the boundary fluxes remain, just as the exact equations require. That built-in conservation is also a safety feature: a scheme that balances momentum against applied forces in every cell is less likely to diverge.

## 1. The integral conservation law

For a volume $V$ bounded by a surface $S$ with outward unit normal $\mathbf n$, mass conservation reads

$$
\frac{\partial}{\partial t}\int_V\rho\,dV+\int_S\rho\,\mathbf v\cdot\mathbf n\,dS=0,
$$

rate of increase of mass in the volume plus net mass flow out; momentum and energy take the same form. Gauss's divergence theorem converts the surface integral to a volume integral,

$$
\int_S\mathbf F\cdot\mathbf n\,dS=\int_V\nabla\cdot\mathbf F\,dV,
$$

so with $\mathbf F=\rho\mathbf v$ both terms sit inside one volume integral:

$$
\int_V\left(\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf v)\right)dV=0.
$$

This holds for every volume, however small, so the integrand itself is zero, which is the differential form of A7. Finite differences discretise the differential form; finite volumes work with the integral form, with rates of change of cell contents and fluxes across cell faces, but use the same numerical tools.

## 2. The procedure and the notation

The method runs as follows:

1. Divide the domain into a finite number of cells: the automatic triangles or tetrahedra of the wing lab, or quadrilaterals, hexahedra, prisms.
2. Apply the integral conservation equations to each cell.
3. Store the unknowns ($\rho$, $u$, $v$, $w$, $p$) at the cell centre.
4. Approximate the surface and volume integrals.
5. Apply the boundary conditions.
6. Solve the resulting sparse system, typically with library iterative solvers such as GMRES ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation|A3]]).

Neighbours are named by compass points. The cell centre is P; its neighbours are N, S, E and W, then NE, NW, SE, SW, and further out EE, WW. Lower-case letters mark the faces: e is the centre of the east face, n of the north face, and so on, with corners ne, nw, se, sw. The main task is to find the flux through each face.

![[dam_fv_compass_stencil.png|820]]

For steady mass conservation on the Cartesian cell P of the figure (unit depth), the integral law becomes a sum over the four faces, with the outward normal $+x$ on e, $-x$ on w, $+y$ on n and $-y$ on s:

$$
\int_S\rho\mathbf v\cdot\mathbf n\,\mathrm dS\approx(\rho u)_e\Delta y-(\rho u)_w\Delta y+(\rho v)_n\Delta x-(\rho v)_s\Delta x=0.
$$

Divide by the cell area $\Delta x\,\Delta y$:

$$
\frac{(\rho u)_e-(\rho u)_w}{\Delta x}+\frac{(\rho v)_n-(\rho v)_s}{\Delta y}=0,
$$

which on a uniform grid is the central difference of $\partial(\rho u)/\partial x+\partial(\rho v)/\partial y$ across the cell: on Cartesian cells the two methods meet. The difference shows when cells are added together. For P and its east neighbour E, the face shared by both appears as $+(\rho u)_e\Delta y$ in P's balance and $-(\rho u)_e\Delta y$ in E's, because the outward normals are opposite. Adding the two balances cancels it exactly, whatever value was used for $(\rho u)_e$, and summing over every cell leaves only the boundary faces. The discrete total is conserved by construction, on any cell shape.

## 3. Surface integrals and the midpoint rule

Put the origin at the east-face centre e, with $y$ along the face of length $\Delta y$. The flux $f$ (convective $\rho\phi\,\mathbf v\cdot\mathbf n$ or diffusive $\Gamma\nabla\phi\cdot\mathbf n$) varies along the face but only $f_e$ will be known. Expand about e:

$$
f(y)=f_e+y\left(\frac{\partial f}{\partial y}\right)_e+\frac{y^2}{2}\left(\frac{\partial^2f}{\partial y^2}\right)_e+\dots
$$

Integrate term by term over the face:

$$
\int_{-\Delta y/2}^{\Delta y/2}f\,dy=\Big[f_ey\Big]+\left[\frac{y^2}{2}\right]\left(\frac{\partial f}{\partial y}\right)_e+\left[\frac{y^3}{6}\right]\left(\frac{\partial^2f}{\partial y^2}\right)_e+\dots
$$

The first bracket is $\Delta y$. The second is zero, because $y^2$ takes the same value at both ends. The third is $2\times(\Delta y/2)^3/6=\Delta y^3/24$:

$$
\int_{-\Delta y/2}^{\Delta y/2}f\,dy=f_e\,\Delta y+\frac{\Delta y^3}{24}\left(\frac{\partial^2f}{\partial y^2}\right)_e+\dots
$$

Keeping only the first term, the midpoint rule $\int_{S_e}f\,dS\approx f_e\,\Delta y$, leaves an error of order $\Delta y^3$ per face, which is second-order accuracy. Most finite volume codes are therefore second order: on any cell shape, they take the value at the middle of each face and multiply by its area. Fourth order would need extra information along the face, such as values at ne and se.

The unknowns are at cell centres, not face centres, so $f_e$ must still be interpolated. Volume integrals are easier, since the centre value times the cell volume, $\int_Vq\,dV\approx q_P\,\Delta V$, is already second order.

## 4. Interpolating the face values

Expanding about P gives $\phi_e=\phi_P+(x_e-x_P)(\partial\phi/\partial x)_P+\dots$; keeping only the first term is the simplest choice.

The upwind differencing scheme (UDS) takes the value from the side the flow comes from:

$$
\phi_e=\begin{cases}\phi_P & (\mathbf v\cdot\mathbf n)_e>0\\ \phi_E & (\mathbf v\cdot\mathbf n)_e<0.\end{cases}
$$

It is first order, bounded and the most stable choice. The donor is set by the sign of the face-normal velocity, so for the east face it is P or E even when the flow arrives at an angle. Looking in the wrong direction makes the scheme unstable, as in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]]. Upwinding is necessary but not sufficient for stability: with explicit time stepping it still needs a Courant number $C\le1$. Switching Fluent from second-order to first-order upwind is a standard way to get a difficult case to converge. The cost in code is an `if` on the flow direction, and branches are slow on modern processors.

The second-order upwind scheme draws a straight line through W and P and extends it to e. On a uniform grid e is half a spacing beyond P and W is a whole spacing behind it:

$$
\phi_e=\phi_P+\tfrac12(\phi_P-\phi_W)=\tfrac12(3\phi_P-\phi_W).
$$

On a non-uniform grid the coefficients differ and have to be derived for the actual spacings, the same Taylor-table work as for finite differences.

The central differencing scheme (CDS) interpolates linearly between P and E:

$$
\phi_e=\lambda_e\phi_E+(1-\lambda_e)\phi_P,
\qquad
\lambda_e=\frac{x_e-x_P}{x_E-x_P},
$$

which is $\tfrac12(\phi_P+\phi_E)$ on a uniform grid. It is second order and independent of flow direction, and stable with implicit time stepping, but it can produce oscillations and converge less easily. Fluent's standard set-up uses either this or second-order upwind. Diffusive fluxes use the central gradient $(\partial\phi/\partial x)_e\approx(\phi_E-\phi_P)/(x_E-x_P)$.

QUICK (Leonard's quadratic upstream interpolation for convective kinematics, also called quadratic upwind interpolation) fits a parabola through two upstream nodes and one downstream. For flow to the right those are W, P and E; for flow to the left, EE, E and P. With D, U and UU the downstream, upstream and second-upstream nodes,

$$
\phi_e=\phi_U+g_1(\phi_D-\phi_U)+g_2(\phi_U-\phi_{UU}),
$$

$$
g_1=\frac{(x_e-x_U)(x_e-x_{UU})}{(x_D-x_U)(x_D-x_{UU})},
\qquad
g_2=\frac{(x_e-x_U)(x_D-x_e)}{(x_U-x_{UU})(x_D-x_{UU})}.
$$

On a uniform grid with spacing $h$, $x_e-x_U=h/2$, $x_e-x_{UU}=3h/2$, $x_D-x_U=h$, $x_D-x_{UU}=2h$, $x_U-x_{UU}=h$, so

$$
g_1=\frac{(h/2)(3h/2)}{h\cdot2h}=\frac38,
\qquad
g_2=\frac{(h/2)(h/2)}{h\cdot2h}=\frac18.
$$

Substitute and collect:

$$
\phi_e=\phi_P+\tfrac38(\phi_E-\phi_P)+\tfrac18(\phi_P-\phi_W)=\tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W.
$$

### Accuracy of the four interpolations

Expand each node value about the face centre e on a uniform grid, where P is $h/2$ behind e, E is $h/2$ ahead and W is $3h/2$ behind (primes are $x$-derivatives at e):

$$
\phi_P=\phi_e-\tfrac h2\phi'+\tfrac{h^2}{8}\phi''-\tfrac{h^3}{48}\phi'''+\dots
$$

$$
\phi_E=\phi_e+\tfrac h2\phi'+\tfrac{h^2}{8}\phi''+\tfrac{h^3}{48}\phi'''+\dots
$$

$$
\phi_W=\phi_e-\tfrac{3h}2\phi'+\tfrac{9h^2}{8}\phi''-\tfrac{27h^3}{48}\phi'''+\dots
$$

UDS takes $\phi_P$, so its error is $-\tfrac h2\phi'$: first order. CDS averages P and E; the odd terms cancel:

$$
\tfrac12(\phi_P+\phi_E)=\phi_e+\tfrac{h^2}{8}\phi''+\dots
$$

Second-order upwind combines P and W:

$$
\tfrac12(3\phi_P-\phi_W)=\phi_e+\tfrac12\left(-\tfrac{3h}{2}+\tfrac{3h}{2}\right)\phi'+\tfrac12\left(\tfrac{3h^2}{8}-\tfrac{9h^2}{8}\right)\phi''+\dots=\phi_e-\tfrac{3h^2}{8}\phi''+\dots
$$

QUICK combines all three, $\tfrac18(6\phi_P+3\phi_E-\phi_W)$. The $\phi'$ coefficient is $\tfrac18\left(-3h+\tfrac{3h}2+\tfrac{3h}2\right)=0$, the $\phi''$ coefficient is $\tfrac18\left(\tfrac{6}{8}+\tfrac38-\tfrac98\right)h^2=0$, and the $\phi'''$ coefficient is $\tfrac18\left(-\tfrac{6}{48}+\tfrac{3}{48}+\tfrac{27}{48}\right)h^3=\tfrac{h^3}{16}$, so

$$
\tfrac18(6\phi_P+3\phi_E-\phi_W)=\phi_e+\tfrac{h^3}{16}\phi'''+\dots
$$

The QUICK interpolation is third order, exact for any parabola. Combined with the midpoint rule, whose error is $O(\Delta y^3)$ per face, the flux is still second order overall. The leading coefficients also explain why CDS beats second-order upwind at the same order: $\tfrac18$ against $\tfrac38$, because e sits between P and E but beyond P and W.

![[dam_advection_upwind_vs_central.png|900]]

The figure shows the trade-off on the convection equation: first-order upwind stays bounded but smears a pulse out (numerical diffusion), while a second-order central-type scheme keeps it sharp but trails wiggles.

### Choosing schemes in Fluent

A typical solver panel mixes orders: second-order upwind for momentum, where accuracy in Newton's second law matters most, second order for pressure, and first-order upwind for the turbulence kinetic energy and dissipation rate. The balance is between convergence and grid dependence. With second order everywhere, doubling the grid in every direction should cut the error by four, which is what a grid study wants; dropping equations to first order helps the residuals fall but slows convergence with grid refinement. Fluent's defaults are the starting point, the turbulence equations are the first to relax since their model error is larger anyway, and the cause of poor convergence is often the grid, which is the first place to look.

## 5. Boundary conditions

At an inflow, the fluxes $\rho u$, $\rho v$, $\rho w$ are specified on the inflow faces and dotted with the normal. At a no-slip wall the velocity components are set to zero on the wall face. A ghost cell is a fictitious cell outside the domain, filled by extrapolation from inside (for a south boundary, linearly from N and P), so the interior stencil can be used unchanged at the boundary; codes often surround the whole domain with them.

A symmetry plane mirrors the flow. The velocity component normal to the plane changes sign across it, so it must be zero on it; the tangential component is the same on both sides, so its normal derivative is zero. For a plane $y=0$:

$$
v=0,
\qquad
\frac{\partial u}{\partial y}=0.
$$

This is the image method of aerodynamics: mirror the velocity vector. A pressure outlet fixes the static pressure and extrapolates everything else from the interior.

The coursework conditions all fit this list. The inviscid wall of the wing lab has zero normal velocity and zero normal gradient of the tangential velocity, which is the same as a symmetry condition, and that is also why a "free-stream" boundary on which the normal velocity is set to zero in an incompressible simulation behaves as a wall: the conditions are identical. The boundary-layer lab uses an inflow, an outlet and a symmetry plane, and its upper boundary can alternatively be set to zero stress, a separate free-stream condition for the Navier–Stokes equations ([[CFD Boundary Conditions]]).

The examinable points are: a CFD solver solves the integral conservation laws; how the surface integrals are built; why interpolation is needed, with QUICK as the common second-order scheme; and the common boundary conditions used in the coursework.

## Worked examples

### Interpolating a face value

*(Suggested, not lecturer-set.)* The function $\phi=e^x$ is sampled at $x_W=-h$, $x_P=0$, $x_E=h$, and $\phi_e$ at $x_e=h/2$ is required for flow to the right. The exact values are $e^{0.05}=1.051271$ for $h=0.1$ and $e^{0.025}=1.025315$ for $h=0.05$:

| Scheme | $\phi_e$ ($h=0.1$) | Error ($h=0.1$) | Error ($h=0.05$) | Ratio | Order |
|---|---|---|---|---|---|
| UDS | 1.000000 | $-5.13\times10^{-2}$ | $-2.53\times10^{-2}$ | 2.0 | 1 |
| second-order upwind | 1.047581 | $-3.69\times10^{-3}$ | $-9.30\times10^{-4}$ | 4.0 | 2 |
| CDS | 1.052585 | $+1.31\times10^{-3}$ | $+3.20\times10^{-4}$ | 4.1 | 2 |
| QUICK | 1.051334 | $+6.33\times10^{-5}$ | $+7.86\times10^{-6}$ | 8.1 | 3 |

Halving $h$ divides each error by $2^p$, confirming the orders.

> [!check] The leading terms predict the errors
> With every derivative of $e^x$ equal to $e^{0.05}=1.0513$ at e and $h=0.1$, the leading terms of [[#Accuracy of the four interpolations]] give $-\tfrac h2\phi'=-5.26\times10^{-2}$ (UDS), $-\tfrac{3h^2}{8}\phi''=-3.94\times10^{-3}$ (second-order upwind), $\tfrac{h^2}{8}\phi''=+1.31\times10^{-3}$ (CDS) and $\tfrac{h^3}{16}\phi'''=+6.57\times10^{-5}$ (QUICK). Each matches the table to within the size of the next term, and the signs all agree.

For the midpoint rule, integrating $f=\cos y$ over a face of $\Delta y=0.2$ centred on $y=0$ gives $f_e\Delta y=0.2$ against the exact $2\sin0.1=0.199667$. The difference is $3.33\times10^{-4}$, and the derived error term $\tfrac{\Delta y^3}{24}f''_e=\tfrac{0.008}{24}\times(-1)=-3.33\times10^{-4}$ predicts both its size and its sign (the midpoint rule overestimates here because $\cos$ curves downwards).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]
- Next: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Concepts: [[Finite Volume Method]] · [[Convective Interpolation Schemes]] · [[CFD Boundary Conditions]] · [[Conservation Form of the Governing Equations]]
- Thermofluids foundation: [[SESA1016 T11 - Conservation of Mass]] · [[SESA1016 T12 - Conservation of Momentum]]
- Symmetry and image flows: [[Method of Images]]
- The finite element counterpart: [[Strong and Weak Forms]]

## Sources

- `All_lectures_as_delivered.pdf`, L10, pp. 130–142, with transcript `SESA2029 Lecture 2025-10-31.txt` (Prof N. Sandham; ll. 451–541 are the start of the examples class)
- Ferziger, Perić & Street, *Computational Methods for Fluid Dynamics*, Ch. 4
- Worked examples recomputed in Python. Figures: `01 - Notes/Figures/generate_dam_a9_figures.py`

## Self-study tasks

### Core

- [ ] Show that the midpoint rule for a face integral is second order (2025-10-31, ll. 121–200). → [[#3. Surface integrals and the midpoint rule]] · [[SESA2029 CFD Worked Examples#Q12: Midpoint-rule surface integral error|Worked examples Q12]]
- [ ] Check the QUICK coefficients on a uniform grid ("there is a question on the example sheet where you can double check", ll. 301–310). → [[#4. Interpolating the face values]] · [[SESA2029 CFD Worked Examples#Q11: QUICK coefficients|Worked examples Q11]]
- [ ] Derive the second-order upwind formula by Taylor series or a straight line through W and P (ll. 276–285). → [[#4. Interpolating the face values]]
- [ ] Explain the inflow, no-slip wall, inviscid wall, symmetry and pressure-outlet conditions used in the coursework (ll. 376–420). → [[#5. Boundary conditions]]
- [ ] Finish example-sheet question 1, the Taylor tables (ll. 451–541). → [[SESA2029 CFD Worked Examples#Q1: Two-point forward difference by Taylor table|Worked examples Q1]]

### Further practice

- [ ] Repeat the interpolation table for a non-uniform grid and derive the second-order upwind coefficients there (suggested, not lecturer-set). → [[#Interpolating a face value]]

## Transcript and slide slips

> [!warning] Lecture overstatement (2025-10-31, ll. 241–250)
> Where: [[#4. Interpolating the face values]].
>
> First-order upwind with an explicit Euler step is described as stable for any time step. Explicit upwind is stable only for a Courant number $C\le1$ ([[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers|A5]]).

> [!warning] Examples-class slip (2025-10-31, ll. 461–535)
> Where: [[#Core]] (example-sheet question 1).
>
> Working example-sheet question 1, the form was written as $f_j'=(af_{j+1}-bf_j)/h$, but the Taylor-table row was entered as $-bf_j$ and then changed to $+b$, giving $a=b=1$ "assuming there was going to be a minus sign there". Keep the sign consistent between the formula and the table: with $f_j'=(af_{j+1}+bf_j)/h$ the result is $a=1$, $b=-1$; either way the scheme is $(f_{j+1}-f_j)/h$ with error $-\tfrac h2f_j''$, first order. The full method is in [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|A2]].

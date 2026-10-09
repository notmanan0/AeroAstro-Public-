---
title: "SESA2029 A9 - Finite Volume Method"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 9
tags:
  - sesa2029
  - cfd
  - finite-volume
aliases: ["FVM", "Finite volumes"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]", "[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
next_topics: ["[[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]"]
key_concepts: ["[[Finite Volume Method]]", "[[Convective Interpolation Schemes]]", "[[CFD Boundary Conditions]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L10, pp. 130–142)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A9 - Finite Volume Method

> [!abstract] Summary
> The FVM discretises the **integral** form of the conservation laws. The domain is divided into control volumes (cells) with unknowns stored at the cell centres. Each cell's balance says: rate of change of the volume integral = sum of the **face fluxes**.
>
> Because a flux leaving one cell enters its neighbour, mass, momentum and energy are conserved **exactly** over the whole domain, on any cell shape. This also helps stability.
>
> Two approximations are needed:
> 1. **Surface integrals**: flux at the face centroid × face area. This is already second order.
> 2. **Interpolation** of face values from the cell centres: upwind (UDS, stable, 1st order), second-order upwind, central (CDS, 2nd order, may oscillate) or **QUICK** (quadratic upwind).
>
> Boundary conditions (inflow, wall, symmetry, pressure outlet) are imposed through face fluxes or ghost cells.

## Key Concepts
- [[Finite Volume Method]] · [[Convective Interpolation Schemes]] · [[CFD Boundary Conditions]] · [[Conservation Form of the Governing Equations]]

---

## 1. Integral conservation law (L10)
Rate of increase of mass in the CV + net mass flow out = 0:

$$
\frac{\partial}{\partial t}\int_V\rho\,dV+\int_S\rho\,\mathbf v\cdot\mathbf n\,dS = 0\qquad\text{(integral form)}
$$

Apply **Gauss's divergence theorem**, $\int_S\mathbf F\cdot\mathbf n\,dS = \int_V\nabla\cdot\mathbf F\,dV$, and let the CV shrink to a point. This recovers the differential form $\partial\rho/\partial t+\nabla\cdot(\rho\mathbf v) = 0$ from A7.

- **Finite difference** thinking discretises the differential form.
- **Finite volume** thinking works with volume integrals (cell averages) and face fluxes.

## 2. The FVM procedure (L10)
1. Subdivide the domain into a finite number of small control volumes (triangles and quads in 2D; tets, hexes and prisms in 3D).
2. Apply the integral conservation equation to **each** CV.
3. Store the unknowns at the **computational node** (the cell centre).
4. Approximate the **surface and volume integrals**. The result depends on the approximation used.
5. Apply boundary conditions.
6. Solve the resulting algebraic system, usually a sparse matrix, iteratively ([[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]).

**Compass notation** for a Cartesian cell $P$:
- neighbouring nodes N, S, E, W (then NE, NW, SE, SW, and EE, WW further out);
- face centres use lower case: n, s, e, w, with corners ne, nw, se, sw.

## 3. Surface integrals (L10)
The net flux is the sum over the 4 faces in 2D (6 in 3D): $\int_Sf\,dS = \sum_k\int_{S_k}f\,dS$. Here $f$ is the convective ($\rho\phi\,\mathbf v\cdot\mathbf n$) or diffusive ($\Gamma\nabla\phi\cdot\mathbf n$) flux component.

On the east face (height $\Delta y$, origin at $e$), expand $f$ about the face centroid:

$$
f = f_e+\left(\frac{\partial f}{\partial y}\right)_ey+\left(\frac{\partial^2f}{\partial y^2}\right)_e\frac{y^2}{2}+H
$$

$$
\int_{-\Delta y/2}^{\Delta y/2}f\,dy = f_e\Delta y+\left(\frac{\partial^2f}{\partial y^2}\right)_e\frac{(\Delta y)^3}{24}+H
$$

The odd term integrates to zero over a symmetric face. So the **midpoint rule** $\int_{S_e}f\,dS\approx f_e\Delta y$ has an $O(\Delta y^3)$ face error: **second order**. That is why most FV codes are second order, whatever the cell shape. Fourth order needs extra points (e.g. ne and se) along the face.

**But the problem is not solved yet.** The unknowns live at the nodes, not on faces, so $f_e$ has to be **interpolated**.

**Volume integrals** are easy: $\int_Vq\,dV\approx q_P\,\Delta V$, which is second order with no interpolation.

## 4. Face interpolation schemes (L10)
Expand about $P$: $\phi_e = \phi_P+(x_e-x_P)(\partial\phi/\partial x)_P+\tfrac12(x_e-x_P)^2(\partial^2\phi/\partial x^2)_P+H$.

| Scheme | $\phi_e$ (uniform grid, flow left→right) | Order | Behaviour |
|---|---|---|---|
| **UDS** (1st-order upwind) | $\phi_P$ if $(\mathbf v\cdot\mathbf n)_e>0$, else $\phi_E$ | 1 | always bounded and stable; **numerically diffusive** |
| **2nd-order upwind** | $\tfrac12(3\phi_P-\phi_W)$ (linear fit through W, P) | 2 | less diffusive; can converge less easily |
| **CDS** (linear) | $\lambda_e\phi_E+(1-\lambda_e)\phi_P$ with $\lambda_e = \dfrac{x_e-x_P}{x_E-x_P}$ | 2 | independent of flow direction; **may oscillate** (unbounded) |
| **QUICK** | $\phi_U+g_1(\phi_D-\phi_U)+g_2(\phi_U-\phi_{UU})$, i.e. $\tfrac68\phi_P+\tfrac38\phi_E-\tfrac18\phi_W$ | 2 (3 locally) | parabola through 2 upstream + 1 downstream nodes |

For QUICK on a general grid:

$$
g_1 = \frac{(x_e-x_U)(x_e-x_{UU})}{(x_D-x_U)(x_D-x_{UU})},\qquad g_2 = \frac{(x_e-x_U)(x_D-x_e)}{(x_U-x_{UU})(x_D-x_{UU})}
$$

D, U and UU are the downstream, first-upstream and second-upstream nodes. They are E, P, W for flow to the right, or P, E, EE for flow to the left.

**Diffusive fluxes** use the CDS gradient: $(\partial\phi/\partial x)_e\approx(\phi_E-\phi_P)/(x_E-x_P)$.

**Coding note**: upwinding needs an `if` on the flow direction, and branches are slow on vector hardware.

![[dam_advection_upwind_vs_central.png|680]]

The figure shows the trade-off on the convection equation. First-order upwind stays bounded but smears a sharp pulse (numerical diffusion). A second-order central-type scheme keeps the pulse sharp but generates wiggles (dispersion). The upwind face value is **exactly** the stability-giving backward difference analysed in [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]].

> [!tip] Choosing schemes in a commercial solver
> - **Start from the solver defaults.** They are usually the best first try.
> - Aim for **2nd order** on momentum and pressure, so that the error falls 4× per grid doubling in a grid study.
> - If the case won't converge, dropping **turbulence** equations ($k$, $\varepsilon$/$\omega$) to 1st-order upwind is a common, defensible compromise, since the model error there is larger anyway.
> - Dropping momentum to first order spoils the grid-convergence rate.
> - Before any of this, **look at the grid**: poor cells are the usual cause.

## 5. Boundary conditions (L10)
| Boundary | Treatment |
|---|---|
| **Inflow** | apply known (convective) fluxes at the inflow faces |
| **Wall (no-slip, viscous)** | $u_s = w_s = 0$ at the wall face; no convective flux through it; from continuity the normal viscous diffusive flux $F^d_s = 0$ |
| **Inviscid (slip) wall** | zero normal velocity; zero normal gradient of the tangential velocity (same as symmetry) |
| **Symmetry plane** | normal velocity = 0; normal derivatives of the other components = 0 (fluxes zero or extrapolated) |
| **Pressure outlet** | specify static pressure; extrapolate the other quantities from the interior |
| **Free stream (viscous)** | zero-stress condition at the far boundary |

**Ghost cells**: fictitious cells outside the domain, filled by extrapolating from the interior (e.g. linear from N and P). The interior stencil can then be used unchanged at the boundary.

**Dirichlet** conditions fix a value; **Neumann** conditions fix a gradient. See [[CFD Boundary Conditions]].

> [!note] Why an incompressible "free-stream" far-field boundary can behave like a wall
> For inviscid incompressible flow, a far boundary with zero normal velocity and zero tangential gradient is mathematically identical to a symmetry plane or slip wall. That is why placing the far field **too close** changes the lift: the "tunnel walls" constrain the flow. A domain-size sensitivity test checks this.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] · Next: [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]
- Thermofluids foundation: [[SESA1016 T11 - Conservation of Mass]] · [[SESA1016 T12 - Conservation of Momentum]] · [[SESA1016 T13 - Conservation of Energy and Propulsion]]
- Symmetry and image flows in aerodynamics: [[Method of Images]]
- FE counterpart (weighted-average rather than flux balance): [[Strong and Weak Forms]]

## Sources
- CFD Lecture 10, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 130–142; transcript `CFD.txt`
- Ferziger, Perić & Street, *Computational Methods for Fluid Dynamics*, Ch. 4

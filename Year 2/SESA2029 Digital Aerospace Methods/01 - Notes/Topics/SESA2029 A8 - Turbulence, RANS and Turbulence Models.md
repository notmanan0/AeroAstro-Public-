---
title: "SESA2029 A8 - Turbulence, RANS and Turbulence Models"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 8
tags:
  - sesa2029
  - cfd
  - turbulence
  - rans
aliases: ["RANS equations", "Turbulence modelling", "Closure problem"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]"]
next_topics: ["[[SESA2029 A9 - Finite Volume Method]]"]
key_concepts: ["[[Reynolds Averaging and the Closure Problem]]", "[[Eddy-Viscosity Turbulence Models]]", "[[First-Cell Height and y-plus]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L9, pp. 113–129; L2 pp. 28–31)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A8 - Turbulence, RANS and Turbulence Models

> [!abstract] Summary
> Turbulence takes energy at large scales, cascades it to smaller eddies by vortex stretching, and dissipates it as heat at the Kolmogorov scale.
>
> **RANS**: split every variable into a mean and a fluctuation, $u = \bar u+u'$, and time-average the Navier–Stokes equations. New unknowns appear: the **Reynolds stresses** $\overline{u_i'u_j'}$, six of them in 3D. There are now more unknowns than equations. This is the **closure problem**, and it cannot be escaped by deriving more equations.
>
> **Eddy-viscosity models** relate the Reynolds stress to the mean strain rate through $\nu_t$. Spalart–Allmaras uses 1 equation; $k$–$\varepsilon$, $k$–$\omega$ and SST use 2. Reynolds-stress models solve 7 equations. No model is universal, so turbulence and transition modelling remain the biggest physical uncertainty in CFD.
>
> **Near-wall grids** must put the first cell either in the viscous sublayer ($y_1^+\lesssim1$–5) or in the log layer with a wall function ($30<y_1^+\lesssim200$). Never put it in the buffer layer.

## Key Concepts
- [[Reynolds Averaging and the Closure Problem]] · [[Eddy-Viscosity Turbulence Models]] · [[First-Cell Height and y-plus]] · [[Law of the Wall]]

---

## 1. Phenomenology (L9)
- **Production**: turbulence energy is produced at the **large scales**, by flow instabilities or by Reynolds stresses working against the mean-flow gradients.
- **Cascade**: energy passes to smaller scales through vortex interaction, especially **vortex stretching**. The vortices are sometimes coherent structures, such as hairpins in boundary layers.
- **Dissipation**: the smallest eddies, at the **Kolmogorov microscale**, dissipate energy into heat through viscosity.

A turbulent jet shows this clearly: big eddies at the jet width, a lateral spread downstream, and a passive scalar (dye) mixed ever finer.

## 2. The turbulent boundary layer in wall units (L9, L2)

$$
u_\tau = \sqrt{\tau_w/\rho},\qquad u^+ = \frac{u}{u_\tau},\qquad y^+ = \frac{yu_\tau}{\nu}
$$

Measured profiles from different $x$ stations, and even different pressure gradients, **collapse** in these variables:
- **viscous sublayer**: $u^+ = y^+$ for $y^+\lesssim5$–8;
- **buffer layer**: roughly $8<y^+<30$;
- **log law**: $u^+ = 2.5\ln y^++5.24$, i.e. $1/\kappa$ with $\kappa\approx0.4$;
- **outer (wake) region**: depends on the pressure-gradient history.

This is an empirical fact rather than a derived theory. Details and constants are in [[Law of the Wall]].

![[dam_law_of_the_wall_y1plus.png|640]]

**Two near-wall strategies**:
| Strategy | First cell | Physics captured | Typical models |
|---|---|---|---|
| **Wall-resolved** | $y_1^+\lesssim1$–5 (ideally $\approx1$) | the viscous sublayer is resolved | SA ($y_1^+<5$), $k$–$\omega$ / SST ($y_1^+\lesssim1$) |
| **Wall function** | $30<y_1^+\lesssim200$ | the model assumes the log law between the wall and cell 1 | $k$–$\varepsilon$ (standard) |

Avoid $8<y_1^+<30$: neither assumption holds there. You still want **10–20 cells across the boundary layer**, so $y_1^+$ cannot be arbitrarily large (hundreds is the limit). **Always post-process the actual $y_1^+$** and refine if needed. The sizing procedure is in [[First-Cell Height and y-plus]].

## 3. Reynolds averaging (L9)
In a statistically steady flow:

$$
\phi(x_i,t) = \bar\phi(x_i)+\phi'(x_i,t),\qquad\bar\phi(x_i) = \lim_{T\to\infty}\frac1T\int_0^T\phi(x_i,t)\,dt
$$

$T$ must be long compared with the eddy time scale. In simulations, averaging over a periodic direction (a space average) is also used.

![[dam_reynolds_decomposition.png|680]]

**Averaging rules**:
- $\overline{\phi'} = 0$ and $\overline{\bar\phi} = \bar\phi$;
- $\overline{c\phi} = c\bar\phi$;
- $\overline{\bar\phi\bar\psi} = \bar\phi\bar\psi$;
- $\overline{\phi+\psi} = \bar\phi+\bar\psi$;
- $\overline{\partial\phi/\partial s} = \partial\bar\phi/\partial s$ (differentiation and averaging commute);
- $\overline{\bar\phi\psi'} = 0$.

But $\overline{\phi'\psi'}\neq0$ **unless the fluctuations are uncorrelated**. Turbulence is organised, so they are correlated.

## 4. The closure problem (L9)
Substitute $u = \bar u+u'$ etc. into the 2D $x$-momentum equation and average. For example

$$
\overline{\frac{\partial(uv)}{\partial y}} = \frac{\partial}{\partial y}\left(\bar u\bar v+\underbrace{\overline{\bar uv'}}_{0}+\underbrace{\overline{u'\bar v}}_{0}+\overline{u'v'}\right)
$$

This gives

$$
\frac{\partial\bar u}{\partial t}+\frac{\partial(\bar u\bar u)}{\partial x}+\color{red}{\frac{\partial\overline{u'u'}}{\partial x}}+\frac{\partial(\bar u\bar v)}{\partial y}+\color{red}{\frac{\partial\overline{u'v'}}{\partial y}}+\frac1\rho\frac{\partial\bar p}{\partial x} = \nu\left(\frac{\partial^2\bar u}{\partial x^2}+\frac{\partial^2\bar u}{\partial y^2}\right)
$$

The two red terms are **Reynolds stresses**: multiplied by $-\rho$ they have units of stress. In 3D there are **6 independent** Reynolds stresses (the tensor is symmetric).

Count the unknowns: 4 equations (continuity + 3 momentum) but 10 unknowns ($\bar u,\bar v,\bar w,\bar p$ and 6 stresses). Writing transport equations for the stresses introduces triple correlations, then quadruple ones, and so on. The system **never closes**. Some physical modelling assumption is unavoidable, so turbulence remains unsolved: no amount of machine learning removes the closure step. This is why CFD still needs expert users.

## 5. Eddy-viscosity hypothesis (L9)
By analogy with molecular viscosity (a Newtonian stress–strain law), relate the Reynolds stress to the mean strain rate. For the main boundary-layer stress:

$$
-\frac{\partial\overline{u'v'}}{\partial y} = \frac{\partial}{\partial y}\left(\nu_t\frac{\partial\bar u}{\partial y}\right)
$$

where $\nu_t$ is the **kinematic eddy viscosity**. It is a property of the flow, not of the fluid. The whole problem is now **finding a model for $\nu_t$**. See [[Eddy-Viscosity Turbulence Models]].

## 6. The models (L9)
| Model | Equations | $\nu_t$ | Strengths | Weaknesses | Near wall |
|---|---|---|---|---|---|
| **Spalart–Allmaras** (Boeing, early 1990s) | 1 (for $\tilde\nu$) | from $\tilde\nu$ | built for external aero; robust; cheap; good attached flow and separation *location*; systematically built up (new terms vanish for the old calibration cases) | free shear layers, reattachment | $y_1^+<5$ (some versions have wall functions for $y_1^+>30$) |
| **$k$–$\varepsilon$** (Launder–Spalding, late 1960s) | 2: $k$, $\varepsilon$ | $C_\mu k^2/\varepsilon$, $C_\mu = 0.09$ | most widely used historically; cheap; good for external flow away from walls; insensitive to free-stream values | strong pressure gradients, streamline curvature, separation; the $\varepsilon$ equation is largely "made up" | wall functions, $y_1^+>30$ |
| **$k$–$\omega$** (1980s) | 2: $k$, $\omega$ | $k/\omega$ | good boundary layers with pressure gradient and separation; well behaved at the wall | sensitive to inflow and free-stream $\omega$ | $y_1^+\lesssim1$ |
| **SST** (Menter) | 2 | blended | $k$–$\omega$ near the wall, $k$–$\varepsilon$ in the free stream; the most-developed 2-equation model | cost is still 2 equations | $y_1^+\lesssim1$ |
| **Reynolds stress (RSM)** | 7 (6 stresses + dissipation) | none: stresses solved directly | strong curvature and **swirl** | expensive (≈10 stored variables vs 4 for SA); slow or unstable convergence | wall-resolved |

- $k = \tfrac12\left(\overline{u'^2}+\overline{v'^2}+\overline{w'^2}\right)$ is the turbulence kinetic energy.
- $\varepsilon$ is its dissipation rate.
- $\omega\propto\varepsilon/k$ is the specific dissipation rate.

For aerodynamic work, the practical shortlist is **SA or $k$–$\omega$ SST**.

> [!warning] Never change a model's constants
> The coefficients were calibrated together against a set of canonical flows (NASA Langley Turbulence Modeling Resource). "Tuning" one constant for your case breaks the model for the flat plate, the jet and everything else it was calibrated on.

**Other options in solver menus**:
- **transition models** ($k$–$k_l$–$\omega$, Transition SST): they work in high-disturbance turbomachinery but poorly for external aerodynamics;
- **scale-resolving methods** (SAS, DES, LES): see [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]].

## 7. Need-to-know (L9)
- Explain the mean/fluctuation decomposition and how the Reynolds stresses arise.
- Explain why there is a closure problem.
- Define the eddy viscosity for a simple boundary layer.
- Explain how SA, $k$–$\varepsilon$, $k$–$\omega$/SST and RSM each try to close the system.
- Expect different models to give different answers for the same flow. **Turbulence** and **transition** modelling are the two big physical unknowns in flight-vehicle CFD.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · Next: [[SESA2029 A9 - Finite Volume Method]]
- Boundary layers: [[SESA2022 T2 - Boundary Layers]] · [[Law of the Wall]] · [[Boundary Layer Separation]]

## Sources
- CFD Lecture 9, `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 113–129 (and L2 pp. 28–31 on $y^+$); transcript `CFD.txt`
- NASA Langley Turbulence Modeling Resource (model definitions)

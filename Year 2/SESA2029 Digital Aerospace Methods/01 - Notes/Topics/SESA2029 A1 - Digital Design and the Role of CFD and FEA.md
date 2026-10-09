---
title: "SESA2029 A1 - Digital Design and the Role of CFD and FEA"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part A: Computational Fluid Dynamics"
order: 1
tags:
  - sesa2029
  - cfd
  - digital-design
aliases: ["Digital design environment", "Role of CFD and FEA"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: []
next_topics: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
key_concepts: ["[[Digital Twin and Digital Thread]]", "[[Verification and Validation]]", "[[First-Cell Height and y-plus]]"]
tutorial_sheets: ["[[SESA2029 CFD Worked Examples]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L1–L2, pp. 1–32)", "02 - Sources/CFD/CFD.txt"]
---

# SESA2029 A1 - Digital Design and the Role of CFD and FEA

> [!abstract] Summary
> Aircraft design is a loop of **synthesis → analysis → decision**. Since about 1980, computation has replaced a large share of wind-tunnel hours in the analysis step.
> - **CFD** solves the conservation laws for the fluid.
> - **FEA** solves equilibrium for the structure.
>
> Together they close the aerostructural loop: aerodynamic loads deform the wing, the deformation changes the loads, and so on. Digitalisation does three jobs:
> - it **supports** the traditional design approach;
> - it enables **new** approaches such as multidisciplinary design optimisation (MDO);
> - it improves **operations** through digital twins.
>
> The rest of Part A opens the CFD "black box": accuracy, iteration, stability, the governing equations, turbulence modelling, finite volumes, grids and validation.

## Key Concepts
- [[Digital Twin and Digital Thread]] · [[Verification and Validation]] · [[First-Cell Height and y-plus]]

---

## 1. The design cycle (L1)
1. **Synthesis**: brainstorming, knowledge, experience and bias produce several conceptual designs that meet the requirements.
2. **Analysis**: test concepts against requirements, gather information, weigh pros and cons. This step includes wind-tunnel and flight tests.
3. **Decision making**: ideally based on the customer's assessment. In practice cost, schedule, performance, alternatives and the contractor's track record all count.

**The role of experiments.** Wind-tunnel hours per aircraft programme rose steadily until about 1980 and then fell. Computing power had become good enough for CFD to take over much of the routine analysis. Experiments did not disappear: they became the **validation** data for the codes (see [[Verification and Validation]]).

**Wing aerostructural design loop.** Start with an initial wing. Run the aerodynamic analysis and the structural analysis, and couple them into the aerostructural behaviour. Ask "OK?". If not, the designer or an optimiser proposes a new wing and the loop repeats.

## 2. Three uses of digitalisation (L1)
| Use | Example |
|---|---|
| Support the traditional approach | computational methods complement or replace physical tests |
| New approaches to design | multidisciplinary design optimisation (MDO) |
| Operations and maintenance | digital twins detect problems early and predict when maintenance is due |

A **digital design environment** contains:
- geometry;
- pre-processing (discretisation);
- links to the analyses of each discipline, and the coupling between them;
- search methods (optimisation);
- post-processing.

See [[Digital Twin and Digital Thread]].

## 3. CFD workflow in a commercial package
1. Create the geometry in CAD. Here: a parametric wing, built from span, taper ratio, sweep and a NACA section.
2. Import it into a meshing tool and generate the mesh. Label the boundaries (inlet, outlet, wall, symmetry, far field).
3. Import the mesh into the solver. Set models, boundary conditions and numerics, then run and post-process.

Every step introduces error: geometry cleaning, mesh resolution, model choice and iteration convergence. Section A11 ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]) is about managing those errors.

> [!warning] CAD-to-mesh translation can fail
> Importing a CAD surface into a mesher sometimes gives an incomplete ("amber") geometry with gaps between surfaces. Industry fixes this with dedicated geometry-repair tools before meshing. The lesson: check the geometry is **watertight** before blaming the mesher or the solver.

## 4. Background aerodynamics used to judge CFD results (L2)
CFD answers need an independent sanity check. For wings, the benchmark is lifting-line theory (SESA2022, see [[SESA2022 T5 - Finite Wing Theory]]).

**Wing nomenclature**:
- span $b$, semi-span $s = b/2$, mean chord $\bar c$;
- area $S = b\bar c$;
- aspect ratio $AR = b/\bar c$; the half-wing aspect ratio is $AR_s = s/\bar c$;
- taper ratio $\lambda = c_{tip}/c_{root}$;
- sweep is measured on the quarter-chord line.

**Finite-wing results**:

$$
a = \frac{dC_L}{d\alpha} = \frac{a_0}{1+\dfrac{a_0}{\pi AR}(1+\tau)}\quad(<a_0\text{ until }AR\to\infty),\qquad C_{D_i} = \frac{C_L^2}{\pi e AR},\quad e = \frac{1}{1+\delta}\le1
$$

Here $\delta$ is the span-efficiency correction; $e$ is linked in [[Oswald Efficiency Factor]] and [[Downwash and Induced Drag]]. Thin aerofoil theory gives $a_0 = 2\pi$ per radian.

**Discretised lifting-line equation.** Collocate at $N$ spanwise stations $\theta_{0,j}$ ($y_0 = -\tfrac b2\cos\theta_0$):

$$
\sum_{n=1}^{N}B_n\sin(n\theta_{0,j})\left[\frac{4b}{a_0c(\theta_{0,j})}+\frac{n}{\sin\theta_{0,j}}\right] = \alpha(\theta_{0,j})-\alpha_{L=0}(\theta_{0,j}),\qquad j = 1,\dots,N
$$

This is an $N\times N$ linear system $[e_{jn}]\{B_n\} = \{f_j\}$. It gives $C_L$, $C_{D_i}$ and $\delta$, and larger $N$ gives higher accuracy. It is itself a small numerical method: discretise, then solve a matrix system.

> [!tip] What to expect when comparing CFD with lifting line
> An inviscid (Euler) CFD solution with a moderately fine grid usually gets the **lift slope** and **aerodynamic centre** within a few per cent, because they depend on the pressure field only. **Induced drag** is much harder:
> - it depends on resolving the trailing-vortex wake, and automatically generated unstructured grids put few cells there;
> - both methods carry their own assumptions (lifting line puts everything on one line; Euler has no boundary layer).
>
> A drag mismatch is therefore not automatically a mistake. It is something to discuss, backed by a grid study (see [[Mesh Convergence and Grid Independence]]).

**Aerodynamic centre from CFD.** Plot the pitching moment about a reference point (e.g. the root leading edge) against $C_L$ for several angles of attack. The slope $dC_{M}/dC_L$ gives the distance of the aerodynamic centre from that point. For a straight wing it should sit near the quarter chord. See [[Aerodynamic Centre and Centre of Pressure]].

## 5. Resolving a boundary layer (L2)
Viscous (RANS) solutions need **10–20 points inside the boundary layer** and a controlled first-cell height $y_1$.

- **Laminar flat plate**: $\delta = 4.91x\,Re_x^{-1/2}$ and $C_f = 0.664\,Re_x^{-1/2}$.
- **Turbulent flat plate**: $\delta = 0.38x\,Re_x^{-1/5}$ and $C_f = 0.059\,Re_x^{-1/5}$.

$$
\tau_w = \tfrac12C_f\rho U_\infty^2,\qquad u_\tau = \sqrt{\tau_w/\rho},\qquad y_1 = \frac{y_1^+\,\nu}{u_\tau}
$$

**Choose $y_1^+$**:
- $\approx1$ resolves the viscous sublayer (costly);
- $>30$ puts the first cell in the log layer, so a wall function is used;
- **never** in the buffer layer, $8<y_1^+<30$.

After running, always **check the actual $y_1^+$** and adjust the grid. Full detail in [[First-Cell Height and y-plus]] and [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]].

> [!example] First-cell height estimate
> Air with $\nu = 1.5\times10^{-5}$ m²/s and $U_\infty = 30$ m/s, at $x = 1$ m, gives $Re_x = 2\times10^6$ (turbulent).
>
> $C_f = 0.059(2\times10^6)^{-1/5} = 0.00324$, so $\tau_w/\rho = \tfrac12(0.00324)(900) = 1.46$ m²/s², $u_\tau = 1.21$ m/s, and $y_1 = 1\times1.5\times10^{-5}/1.21 \approx 12\,\mu$m for $y_1^+ = 1$.
>
> For comparison, $\delta = 0.38\,(1)(2\times10^6)^{-1/5}\approx 21$ mm. So a boundary-layer mesh needs strong growth: an inflation layer with a stretching ratio of about 1.1–1.2.

## 6. What the module covers
| Part | Content |
|---|---|
| **A: CFD** (A2–A11) | numerical methods (accuracy, iteration, stability, RK4) → governing equations and turbulence → finite volume, grids, algorithms, V&V |
| **B: FEA** (B1–B10) | matrix displacement method → energy methods and shape functions → beam, 2D and 3D elements → meshing, modal, nonlinear, V&V |
| **C: APDL** (C1–C6) | scripted ANSYS Mechanical APDL workflows for the structural problems in Part B |

Prerequisite maths: Taylor series, complex exponentials, ODEs (MATH2048). Python (numpy/scipy/matplotlib) is used for all the demonstrations.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Next: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Aerodynamics background: [[SESA2022 T5 - Finite Wing Theory]] · [[Law of the Wall]] · [[Displacement and Momentum Thickness]]
- Structural side of the same loop: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]

## Sources
- CFD lectures L1 (Introduction) and L2 (background aerodynamics), `02 - Sources/CFD/All_lectures_as_delivered.pdf` pp. 1–32; lecture transcript `CFD.txt`
- Chapra & Canale, *Numerical Methods for Engineers*; Ferziger, Perić & Street, *Computational Methods for Fluid Dynamics*

---
title: "SESA2029 Digital Aerospace Methods Hub"
module: "SESA2029 Digital Aerospace Methods"
type: hub
tags: [sesa2029, hub, moc]
status: complete
---

# SESA2029 Digital Aerospace Methods Hub

> [!abstract] Module at a glance
> This module opens the two "black boxes" of digital aerospace design:
> - **CFD** (Part A, Prof N. Sandham): how numerical methods turn the Navier–Stokes equations into numbers, and when to distrust them.
> - **FEA** (Part B, Dr J. Yuan): how structures become $\{F\} = [K]\{d\}$, and how to build, mesh, check and validate FE models.
> - **APDL** (Part C): scripted ANSYS Mechanical APDL workflows for the structural problems.
>
> One thread runs through all of it. Every simulation is **discretise → solve → verify → validate**. The errors come from the model, the grid and the iteration, and each needs its own check.
>
> Quick reference: [[SESA2029 Formula Sheet]] · Worked examples: [[SESA2029 CFD Worked Examples]] · [[SESA2029 FEA Worked Examples]]

## Topic map

### Part A: Computational Fluid Dynamics (L1–L12)
1. [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]: design cycle, digital twin and thread, CFD workflow, lifting-line and boundary-layer sanity checks, $y_1$ sizing
2. [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]: forward, backward and central differences; order of accuracy; Taylor tables
3. [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]: heat equation from a CV, Gaussian elimination, Jacobi / Gauss–Seidel / SOR / GMRES, residuals
4. [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]: explicit vs implicit Euler, Neumann BC, stability vs accuracy
5. [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]: gain $G$, $F\le\tfrac12$, $C\le1$
6. [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]: BDF2, RK2, RK4, stability regions, Blasius by shooting
7. [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]: conservation form, incompressibility, Newtonian fluid, NSE
8. [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]: Reynolds stresses, closure, SA / $k$–$\varepsilon$ / $k$–$\omega$ / SST / RSM, $y^+$
9. [[SESA2029 A9 - Finite Volume Method]]: integral form, surface integrals, UDS / CDS / QUICK, boundary conditions
10. [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]: structured / unstructured / hybrid, H / O / C grids, SIMPLE, segregated vs coupled
11. [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]: error types, V&V, skewness / aspect ratio / orthogonality, grid independence, DNS / LES / DES

### Part B: Finite Element Analysis (L1–L12)
12. [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]: bar element, assembly, BCs, back-substitution
13. [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]: assumptions, workflow, rigid-body modes, over-constraint, symmetry, von Mises vs Tresca
14. [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]: strong vs weak form, PMPE, 2-node bar derivation, SCF and FoS
15. [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]: Rayleigh–Ritz, $[N]$ and $[B]$, quadratic shape functions, h/p refinement
16. [[SESA2029 B5 - Euler-Bernoulli Beam Element]]: bending theory, Hermite cubics, beam $[K]$, propped-cantilever example
17. [[SESA2029 B6 - 2D and 3D Elements]]: plane stress / strain, membrane, plate, shell, solids, element summary
18. [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]: error types, meshing plan, refinement, convergence, singularities, quality checks
19. [[SESA2029 B8 - Modal Analysis]]: eigenproblem, mode shapes, participation factor, effective mass
20. [[SESA2029 B9 - Nonlinear FE Analysis]]: geometric, material and contact nonlinearity; direct substitution vs Newton–Raphson
21. [[SESA2029 B10 - FE Verification, Validation and Model Updating]]: accuracy checks, free–free, unit displacement and unit gravity checks, model updating

### Part C: APDL workflows (own scripts, generalised)
22. [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]: processor cycle, command glossary, `*GET` / `*DO` / `*VWRITE`, pitfalls
23. [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]: tip, uniform and elliptical loads with hand checks
24. [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]: $K_t$, FoS, element order
25. [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]: spline section, skin mesh, pressures, mass, modes
26. [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]: master `.inp` + case `.mac`, convergence and design sweeps
27. [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]: free–free modal, unit gravity, unit displacement, mass and reactions

### Deep dive (for fun, and for really understanding CFD)
28. [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]: derive NS from a control volume, dissect every term, discretise each one (Taylor, modified equation, projection, MAC grid), build a 2D solver and verify it against Ghia et al.

## Concept notes

| Part A: numerics | Part A: flow physics | Part A: CFD practice | Part B: theory | Part B: practice |
|---|---|---|---|---|
| [[Finite Difference Approximations]] | [[Conservation Form of the Governing Equations]] | [[Finite Volume Method]] | [[Matrix Displacement Method]] | [[Plane Stress and Plane Strain]] |
| [[Truncation Error and Order of Accuracy]] | [[Navier-Stokes Equations]] | [[Convective Interpolation Schemes]] | [[Global Stiffness Matrix Assembly]] | [[Plate, Shell and Membrane Elements]] |
| [[Taylor Table Method]] | [[Newtonian Fluid and Strain-Rate Tensor]] | [[CFD Boundary Conditions]] | [[Boundary Conditions and Rigid Body Modes]] | [[Solid Elements (Tetrahedra and Hexahedra)]] |
| [[Jacobi, Gauss-Seidel and SOR Iteration]] | [[Reynolds Averaging and the Closure Problem]] | [[Structured, Unstructured and Hybrid Grids]] | [[Strong and Weak Forms]] | [[Stress Singularities]] |
| [[Residual vs Solution Error]] | [[Eddy-Viscosity Turbulence Models]] | [[Pressure-Velocity Coupling and SIMPLE]] | [[Principle of Minimum Total Potential Energy]] | [[FE Element Quality Checks]] |
| [[Explicit and Implicit Time Integration]] | [[First-Cell Height and y-plus]] | [[CFD Mesh Quality Metrics]] | [[Rayleigh-Ritz Method]] | [[Natural Frequencies and Mode Shapes]] |
| [[Von Neumann Stability Analysis]] | [[Shooting Method and the Blasius Solution]] | [[DNS, LES and Scale-Resolving Simulation]] | [[Shape Functions]] | [[Participation Factor and Effective Mass]] |
| [[CFL and Fourier Numbers]] | [[Digital Twin and Digital Thread]] | | [[h- and p-Refinement]] | [[Sources of Nonlinearity in FEA]] |
| [[Runge-Kutta Methods]] | | | [[Euler-Bernoulli Beam Element]] | [[Direct Substitution and Newton-Raphson]] |
| | | | [[Von Mises and Tresca Yield Criteria]] | [[FE Model Verification Checks]] |
| | | | [[Stress Concentration Factor and Factor of Safety]] | [[Model Updating]] |

Shared across both parts: [[Mesh Convergence and Grid Independence]] · [[Verification and Validation]]

Linked from other modules: [[Law of the Wall]] · [[Displacement and Momentum Thickness]] · [[D'Alembert's Paradox]] · [[Oswald Efficiency Factor]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]]

## Figures
Every figure in `01 - Notes/Figures` (`dam_*.png`, 25 in total) is generated from first principles by the module's `scripts/make_figures.py` and `scripts/ns_cavity_solver.py` (a 2D MAC-grid Navier–Stokes solver for the deep dive), and none is digitised. That includes a small Q4 plane-stress solver for the singularity study. Re-run the script to regenerate any of them. Each was checked visually against the vault `AGENTS.md` figure checklist.

## Assessment and exam
> [!info] Format (from the lecturers)
> - **Final exam: 40%**. One hour, in person, **short questions**.
>   - Section A (CFD): about 8–10 questions.
>   - Section B (FEA): about 8 questions.
>   - Roughly 30 minutes per part.
> - **Key equations and element matrices are provided**, e.g. the beam stiffness matrix and the shape-function equation. Practise *using* them.
> - Lecture content (including anything demonstrated in the computer sessions) is examinable.
> - No past papers exist (the module is new in Year 2). A **mock paper** is released before the revision lectures. Use the example sheets, the lecture summary ("need-to-know") slides and the worked examples here.

> [!tip] Likely question types
> **CFD**:
> 1. Derive a finite-difference scheme with a Taylor table and state its order.
> 2. Discretise a PDE (heat or convection) explicitly and implicitly; say which needs a matrix solve.
> 3. Von Neumann analysis for a given scheme, giving the $F$ or CFL limit.
> 4. Residual vs error; Jacobi / Gauss–Seidel / SOR updates; under-relaxation.
> 5. Euler vs Navier–Stokes; compressible vs incompressible; Newtonian fluid; expand the index notation.
> 6. RANS: where Reynolds stresses come from, the closure problem, eddy viscosity, choosing SA / $k$–$\varepsilon$ / SST, and $y^+$ strategy.
> 7. FVM: surface-integral order, the need for interpolation, UDS / CDS / QUICK, boundary conditions.
> 8. Grids (structured / unstructured / C / O / H), SIMPLE, segregated vs coupled; error types; V&V; mesh metrics; DNS cost scaling.
>
> **FEA**:
> 1. MDM: element matrices, assembly, BCs, displacement and reactions.
> 2. Derive the bar matrix by PMPE.
> 3. Derive shape functions (linear or quadratic) from generalised BCs.
> 4. Beam-element MDM with the given matrix.
> 5. Explain interpolation and shape functions, element choice, plane stress vs strain, shell rules.
> 6. Meshing strategy, convergence, singularities, aspect ratio.
> 7. Modal: eigenproblem, what changes the frequencies, participation factor and effective mass.
> 8. Sources of nonlinearity; direct substitution vs Newton–Raphson; V&V checks; model updating.

## All notes
```dataview
TABLE type, stream, status, file.mtime AS "Updated"
FROM "Year 2/SESA2029 Digital Aerospace Methods"
WHERE type
SORT type ASC, file.name ASC
```

## Build status
> [!todo] Remaining items (tick when done)
> - [x] Part A topic notes A1–A11
> - [x] Part B topic notes B1–B10
> - [x] Part C APDL workflow notes C1–C6
> - [x] 48 concept notes (`01 - Notes/Concepts`)
> - [x] 25 figures (`01 - Notes/Figures`, generated by `scripts/make_figures.py` and `scripts/ns_cavity_solver.py`)
> - [x] Navier–Stokes deep dive: [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]
> - [x] [[SESA2029 CFD Worked Examples]] (`01 - Notes/Tutorials`)
> - [x] [[SESA2029 FEA Worked Examples]] (`01 - Notes/Tutorials`)
> - [x] [[SESA2029 Formula Sheet]] (`01 - Notes`)
> - [x] Link and format audit (`scripts/audit_notes.py`): 80 notes, all links and figures resolve
> - [ ] Optional later: add the mock-paper solutions to `03 - Exams & Past Papers` once the paper is in the vault

## Builds on / feeds into
- **From** [[SESA1016 Thermofluids Hub]]: the material derivative, Newtonian viscosity and integral mass/momentum balances become the Euler and Navier–Stokes equations and the finite-volume method; boundary-layer theory supplies CFD sanity checks.
- **From** [[SESA2022 Aerodynamics Hub]]: boundary layers, potential flow, lifting-line theory. These are the sanity checks for CFD.
- **From** [[SESA2027 Aerospace Mechanics & Control Hub]]: eigenvalues, modes, $\omega_n$ and $\zeta$ (used in stability analysis and modal FEA).
- **From** SESA2028 Materials & Structures: bending theory, stress transformation, yield.
- **From** MATH2048: Taylor series, ODEs, linear algebra, vector calculus.
- **Into** Year 3 and 4: SESA3029 Aerothermodynamics (compressible NSE), SESA3043 (boundary layers), FEEG6005 Applications of CFD, SESA6082 Computational Aerodynamics, aircraft structural design and aeroelasticity.

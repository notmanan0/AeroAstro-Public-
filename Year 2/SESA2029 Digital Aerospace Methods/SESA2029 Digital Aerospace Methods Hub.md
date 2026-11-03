---
title: "SESA2029 Digital Aerospace Methods Hub"
module: "SESA2029 Digital Aerospace Methods"
type: hub
tags: [sesa2029, hub, moc]
status: lectured
date: 2026-10-30
---

# SESA2029 Digital Aerospace Methods Hub

> [!abstract] Module at a glance
> SESA2029 opens the two "black boxes" of digital aerospace design. Part A (CFD, Prof N. Sandham) is a short course in numerical analysis that ends with how Fluent solves the Navier–Stokes equations and when to distrust it; Part B (FEA, Dr J. Yuan) derives $\{F\}=[K]\{d\}$ by the matrix displacement and energy methods and then covers element choice, meshing, modal, nonlinear analysis and validation, practised in three ANSYS Mechanical APDL labs (Part C). One thread runs through both: every simulation is discretise, solve, verify, validate, and the errors from the model, the grid and the iteration each need their own check.
>
> Quick reference: [[SESA2029 Formula Sheet]] · Worked examples: [[SESA2029 CFD Worked Examples]] · [[SESA2029 FEA Worked Examples]] · Sources: [[SESA2029 Transcript Index]]

## Coverage

Every topic note was rebuilt from the lecture transcripts on 30 October 2026 and is at status `lectured`.

| Part | Notes | Lectured | Transcripts |
|---|---|---|---|
| A, CFD | A1–A11 | 2 Oct – 7 Nov 2025 (Thursdays and Fridays, weeks 1–6) | `SESA2029 Lecture 2025-10-02` to `2025-11-07`, plus the CW1 and CW4–6 coursework videos |
| B, FEA | B1–B10 | 30 Jan – 6 Mar 2026 (Fridays, two lectures each) | `SESA2029 Lecture 2026-01-30` to `2026-03-06` |
| C, labs | C1–C6 | lab videos and the 30 Jan briefing | `Software_Intro`, `Computer lab1` (spring, cantilever), `lab2` (plane stress), `lab3` (wing) |
| Revision | — | 12 and 13 May 2026 | `2026-05-12` (CFD), `2026-05-13` (FEA) |

## Topic map

### Part A: Computational Fluid Dynamics

1. [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]: design cycle, digital twin and thread, CFD workflow, lifting-line and boundary-layer sanity checks, first-cell sizing
2. [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]: forward, backward and central differences, order of accuracy, Taylor tables
3. [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]: heat equation from a control volume, Gaussian elimination, Jacobi, Gauss–Seidel, SOR, GMRES, residuals
4. [[SESA2029 A4 - Time Marching - Explicit and Implicit Methods]]: explicit and implicit Euler, Neumann boundaries, stability against accuracy
5. [[SESA2029 A5 - Numerical Stability - Von Neumann Analysis, Fourier and CFL Numbers]]: gain $G$, $F\le\tfrac12$, $c\le1$
6. [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]]: three-point backward, RK2, RK4, stability regions, Blasius by shooting
7. [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]: conservation form, incompressibility, Newtonian fluid, Navier–Stokes
8. [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]]: Reynolds stresses, closure, eddy viscosity, SA, $k$–$\varepsilon$, $k$–$\omega$, SST, Reynolds-stress models, $y^+$
9. [[SESA2029 A9 - Finite Volume Method]]: integral form, midpoint rule, UDS, CDS and QUICK, boundary conditions
10. [[SESA2029 A10 - Grids and Pressure-Based Solution Algorithms]]: structured, unstructured and hybrid grids, pressure Poisson equation, SIMPLE, segregated and coupled solvers, report guidance
11. [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]: error types, V&V, mesh metrics, grid independence, DNS cost, LES and DES, exam format

### Part B: Finite Element Analysis

12. [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]: FEA procedure, bar element, assembly, boundary conditions, back-substitution, assessment
13. [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]: assumptions, rigid-body modes, over-constraint, symmetry, von Mises and Tresca
14. [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]: strong and weak forms, minimum potential energy, two-node bar, stress concentration and factor of safety
15. [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]: Rayleigh–Ritz, linear and quadratic shape functions, h- and p-refinement
16. [[SESA2029 B5 - Euler-Bernoulli Beam Element]]: bending strain energy, cubic shape functions, beam stiffness matrix, two-element example
17. [[SESA2029 B6 - 2D and 3D Elements]]: plane stress and strain, membranes, plates, shells, solids
18. [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]: error types, meshing plan, refinement, convergence, singularities, quality checks, lab 3 briefing
19. [[SESA2029 B8 - Modal Analysis]]: eigenproblem, what controls the frequencies, participation factor and effective mass
20. [[SESA2029 B9 - Nonlinear FE Analysis]]: geometric, material and boundary nonlinearity; direct substitution and Newton–Raphson
21. [[SESA2029 B10 - FE Verification, Validation and Model Updating]]: accuracy checks, free–free and unit checks, model updating, exam format

### Part C: the FEA labs in APDL

22. [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]: access, processors, parameters, scripts, pitfalls, coursework structure
23. [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]: lab 1 springs and spar, tip, uniform and elliptical loads
24. [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]: lab 2, $K_t$, factor of safety, convergence
25. [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]: lab 3, shell wing, pressures, mass, modes
26. [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]: scripted sweeps and batch mode
27. [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]: the B10 checks as commands

### Deep dive

28. [[SESA2029 Deep Dive - Navier-Stokes from First Principles to a Working Solver]]: Navier–Stokes from a control volume, every term discretised, a 2D MAC-grid solver verified against Ghia et al.

## Concept map

The numerical thread of Part A runs from Taylor series ([[Finite Difference Approximations]], [[Taylor Table Method]], [[Truncation Error and Order of Accuracy]]) through solving the resulting systems ([[Jacobi, Gauss-Seidel and SOR Iteration]], [[Residual vs Solution Error]]) and marching in time ([[Explicit and Implicit Time Integration]], [[Von Neumann Stability Analysis]], [[CFL and Fourier Numbers]], [[Runge-Kutta Methods]]). The physics thread runs from [[Conservation Form of the Governing Equations]] and [[Newtonian Fluid and Strain-Rate Tensor]] to the [[Navier-Stokes Equations]], then [[Reynolds Averaging and the Closure Problem]] and [[Eddy-Viscosity Turbulence Models]], with [[Shooting Method and the Blasius Solution]] and [[First-Cell Height and y-plus]] tying it to the boundary-layer labs. The two threads meet in Fluent: [[Finite Volume Method]], [[Convective Interpolation Schemes]], [[CFD Boundary Conditions]], [[Structured, Unstructured and Hybrid Grids]], [[Pressure-Velocity Coupling and SIMPLE]], [[CFD Mesh Quality Metrics]] and [[DNS, LES and Scale-Resolving Simulation]].

Part B starts from the [[Matrix Displacement Method]] and [[Global Stiffness Matrix Assembly]], with [[Boundary Conditions and Rigid Body Modes]] deciding whether a model can be solved at all. The energy route goes through [[Strong and Weak Forms]], the [[Principle of Minimum Total Potential Energy]], the [[Rayleigh-Ritz Method]] and [[Shape Functions]] to the [[Euler-Bernoulli Beam Element]], and on to element choice ([[Plane Stress and Plane Strain]], [[Plate, Shell and Membrane Elements]], [[Solid Elements (Tetrahedra and Hexahedra)]], [[h- and p-Refinement]]). Results are judged with [[Von Mises and Tresca Yield Criteria]] and [[Stress Concentration Factor and Factor of Safety]], made trustworthy through [[Stress Singularities]], [[FE Element Quality Checks]], [[FE Model Verification Checks]] and [[Model Updating]], and extended by [[Natural Frequencies and Mode Shapes]], [[Participation Factor and Effective Mass]], [[Sources of Nonlinearity in FEA]] and [[Direct Substitution and Newton-Raphson]].

Shared by both parts: [[Mesh Convergence and Grid Independence]] · [[Verification and Validation]] · [[Digital Twin and Digital Thread]]

Linked from other modules: [[Law of the Wall]] · [[Displacement and Momentum Thickness]] · [[D'Alembert's Paradox]] · [[Oswald Efficiency Factor]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]]

## Figures

The 25 figures in `01 - Notes/Figures` (`dam_*.png`) are generated from first principles by `04 - Labs & Coursework/scripts/make_figures.py` and `ns_cavity_solver.py` (a 2D MAC-grid Navier–Stokes solver for the deep dive); none is digitised. No new figures were needed in the rebuild.

## Assessment and exam

The module is 40 % exam, 30 % CFD coursework and 30 % FEA coursework (2026-01-30 10:00, ll. 61–70). The exam is one hour, in person: Section A on CFD and Section B on FEA, about eight short questions each and about 30 minutes per part, with 25 marks for the FEA half (2025-11-07, ll. 511–567; 2026-03-06 10:55, ll. 331–360). Questions ask for explanations of terms and physical reasoning and for short calculations; there is no coding. Key formulae and element matrices are given at the end of the paper. There are no past papers because the module is new in Year 2 (the RAeS and IMechE wanted CFD and FEA compulsory); a mock paper was released before the May revision lectures.

The CFD questions to practise are: deriving a finite-difference scheme with a Taylor table and stating its order; discretising the heat or convection equation explicitly and implicitly; a von Neumann analysis for a stability limit; residuals and Jacobi, Gauss–Seidel and SOR updates; Euler against Navier–Stokes, incompressibility, the Newtonian fluid and index notation; Reynolds stresses, closure, eddy viscosity, model choice and $y^+$; the finite volume method's midpoint rule, interpolation and boundary conditions; grids, SIMPLE, error types, V&V, mesh metrics and DNS cost.

The FEA questions to practise are: matrix-displacement assembly with boundary conditions, displacements and reactions; the bar matrix by minimum potential energy; shape functions from generalised boundary conditions; beam assembly with the given matrix; element choice, plane stress and strain and shell rules; meshing, convergence and singularities; the modal eigenproblem, participation factors and effective mass; sources of nonlinearity, solution methods, V&V checks and model updating.

## Sources

- CFD: `02 - Sources/CFD/All_lectures_as_delivered.pdf` (L1–L12) and the transcripts listed in [[SESA2029 Transcript Index]]
- FEA: `02 - Sources/FEM Lectures/Lecture_3` to `Lecture_12` slides (Lectures 1–2 have no separate deck) and the 2026 transcripts
- Labs: the lab videos and sheets on Blackboard; transcripts in `02 - Sources/Lectures`

## All notes

```dataview
TABLE type, stream, status, file.mtime AS "Updated"
FROM "Year 2/SESA2029 Digital Aerospace Methods"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on and feeds into

- From [[SESA1016 Thermofluids Hub]]: the material derivative, Newtonian viscosity and integral mass and momentum balances become the Euler and Navier–Stokes equations and the finite volume method.
- From [[SESA2022 Aerodynamics Hub]]: boundary layers, potential flow and lifting-line theory, the sanity checks for CFD.
- From [[SESA2027 Aerospace Mechanics & Control Hub]]: eigenvalues, modes, $\omega_n$ and $\zeta$, used in stability analysis and modal FEA.
- From SESA2028 Aerospace Materials & Structures: bending theory, stress transformation, yield.
- From MATH2048: Taylor series, ODEs, linear algebra, vector calculus.
- Into Year 3 and 4: SESA3029 Aerothermodynamics (compressible flow), SESA3043 (boundary layers), the fourth-year Applications of CFD module, SESA6082 Computational Aerodynamics, aircraft structural design and aeroelasticity.

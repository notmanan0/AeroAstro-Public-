---
title: "FEEG1002 Mechanics, Materials and Structures Hub"
module: "FEEG1002 Mechanics, Materials and Structures"
type: hub
tags: [feeg1002, hub, statics, materials, dynamics]
status: complete
---

# FEEG1002 Mechanics, Materials and Structures Hub

> [!abstract] Module at a glance
> Four strands share one habit: **draw the free-body diagram first**.
> - **Statics 1**: forces in equilibrium → stress and strain in bars, trusses, beams, struts and shafts.
> - **Statics 2**: stress and strain as 2D/3D tensors → transformation (Mohr) → measurement (rosettes) → failure (yield criteria).
> - **Materials**: *why* materials have the $E$, $\sigma_Y$ and toughness the Statics strands assume. Atomic bonding → crystals and defects → phase diagrams → fracture, fatigue, creep and corrosion.
> - **Dynamics**: equilibrium is replaced by $\sum F = ma$, integrated over time (impulse–momentum) and over distance (work–energy), then applied to vibration and rigid bodies.
>
> Quick reference: [[FEEG1002 Formula Sheet]]

## Topic map

### Part A: Statics 1
1. [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]: FBDs, supports, direct stress and strain, Hooke's law, stress concentrations
2. [[FEEG1002 A2 - Pin-Jointed Trusses]]: joints and sections, determinacy, Williot displacement diagrams
3. [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]: sign convention, $dQ/dx = -w$, $dM/dx = Q$
4. [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]: $M/I = \sigma/y = E/R$, $I$, the parallel axis theorem
5. [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]: $EIv'' = -M$, singularity functions, standard cases
6. [[FEEG1002 A6 - Statically Indeterminate Beams]]: compatibility, superposition, propped and fixed beams
7. [[FEEG1002 A7 - Euler Buckling of Struts]]: $P_{cr} = \pi^2EI/L_e^2$, end conditions
8. [[FEEG1002 A8 - Torsion of Circular Shafts]]: $T/J = \tau/r = G\theta/L$, hollow vs solid
9. [[FEEG1002 A9 - Shear Stresses in Beams]]: $\tau = QA\bar y/Ib$

### Part B: Statics 2
1. [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]
2. [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]
3. [[FEEG1002 B3 - Generalised Hooke's Law]]
4. [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]
5. [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
6. [[FEEG1002 B6 - Yield Criteria]]

### Part C: Materials
Source overview: [[FEEG1002 Materials Contact Sheet Index]]

1. [[FEEG1002 C1 - Atoms and Bonding]]: valence, bond-energy curves, ionic/covalent/metallic/secondary bonds
2. [[FEEG1002 C2 - Crystal Structures and Crystallography]]: FCC/BCC/HCP, packing, polymorphism, Miller indices
3. [[FEEG1002 C3 - Diffusion]]: vacancy/interstitial motion, Fick's laws, Arrhenius temperature dependence
4. [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]: tensile properties, defects, slip and alloying
5. [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]: work/solution/grain/precipitation strengthening; recovery and recrystallisation
6. [[FEEG1002 C6 - Phase Diagrams]]: tie lines, lever rule, solidification, eutectics and microstructure
7. [[FEEG1002 C7 - Steels and Precipitation Hardening]]: iron-carbon eutectoid, pearlite, solution treatment and ageing
8. [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]: ductile/brittle surfaces, Griffith, $K_{IC}$ and DBTT
9. [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]: S-N and Paris, creep rate, galvanic cells and protection
10. [[FEEG1002 C10 - Polymers - Structure and Mechanics]]: $T_g$, crystallinity, thermoplastics/thermosets/elastomers and viscoelasticity
11. [[FEEG1002 C11 - Ceramics and Composites]]: ionic structures, glass, flaw statistics and composite micromechanics

### Part D: Dynamics
1. [[FEEG1002 D1 - Linear Motion of Particles]]: kinematics, Newton's laws, typical forces, pulleys
2. [[FEEG1002 D2 - Curvilinear Motion]]: projectiles, $n$–$t$ coordinates, $v^2/\rho$
3. [[FEEG1002 D3 - Work, Energy and Power]]: work, potential energy, conservation, power and efficiency
4. [[FEEG1002 D4 - Linear Impulse and Momentum]]: impulse, conservation, restitution, impacts
5. [[FEEG1002 D5 - Angular Impulse and Momentum]]: $\mathbf H = \mathbf r\times m\mathbf v$, central forces, orbits
6. [[FEEG1002 D6 - Single Degree of Freedom Vibration]]: $\omega_n$, $\zeta$, log decrement, FRFs
7. [[FEEG1002 D7 - Kinematics of Rigid Bodies]]: rotation, relative velocity, IC, rolling
8. [[FEEG1002 D8 - Kinetics of Rigid Bodies]]: $I$, $\sum M_G = I_G\alpha$, rolling with slip
9. [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]: $KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2$, work of couples

## Core concept notes

| Statics 1 | Statics 2 | Dynamics: particles | Dynamics: vibration and rigid bodies |
|---|---|---|---|
| [[Free Body Diagram and Equilibrium]] | [[Stress Tensor and Stress Element]] | [[Kinematic Relations for Rectilinear Motion]] | [[Damping Ratio and Natural Frequency]] |
| [[Stress, Strain and Young's Modulus]] | [[Thin-Walled Pressure Vessels]] | [[Newton's Laws of Motion]] | [[Equivalent Spring Stiffness]] |
| [[Method of Joints and Method of Sections]] | [[Strain Components and Volumetric Strain]] | [[Coulomb Friction]] | [[Logarithmic Decrement]] |
| [[Static Determinacy]] | [[Thermal Strain]] | [[Dependent Motion and Pulley Constraints]] | [[Frequency Response Function]] |
| [[Williot Displacement Diagram]] | [[Generalised Hooke's Law]] | [[Projectile Motion]] | [[Relative Velocity Equation for Rigid Bodies]] |
| [[Shear Force and Bending Moment Relations]] | [[Stress Transformation Equations]] | [[Normal and Tangential Coordinates]] | [[Instantaneous Centre of Rotation]] |
| [[Engineer's Bending Theory]] | [[Mohr's Circle]] | [[Work-Energy Principle]] | [[Rolling Without Slip]] |
| [[Parallel Axis Theorem]] | [[Principal Stresses]] | [[Conservative Forces and Potential Energy]] | [[Mass Moment of Inertia and Radius of Gyration]] |
| [[Macaulay's Method]] | [[Strain Gauge Rosettes]] | [[Power and Efficiency]] | [[Planar Rigid-Body Equations of Motion]] |
| [[Standard Beam Deflections]] | [[Von Mises and Tresca Yield Criteria]] | [[Principle of Linear Impulse and Momentum]] | [[Kinetic Energy of a Rigid Body]] |
| [[Superposition for Indeterminate Beams]] | | [[Coefficient of Restitution]] | |
| [[Torsion of Circular Shafts]] | | [[Principle of Angular Impulse and Momentum]] | |
| [[Shear Stress Distribution in Beams]] | | | |

### Materials concepts

| Structure and processing | Mechanical behaviour | Failure and non-metals |
|---|---|---|
| [[Atomic Bonding and Interatomic Potential]] | [[Engineering Stress-Strain Properties]] | [[Griffith Criterion and Fracture Toughness]] |
| [[Crystal Structures and Atomic Packing Factor]] | [[Dislocations and Slip Systems]] | [[Ductile-to-Brittle Transition]] |
| [[Miller Indices for Planes and Directions]] | [[Strengthening Mechanisms in Metals]] | [[S-N Curves and Paris Law]] |
| [[Fick's Laws and Arrhenius Diffusion]] | [[Annealing of Cold-Worked Metals]] | [[Creep]] |
| [[Tie Lines and Lever Rule]] | [[Precipitation Hardening]] | [[Galvanic Corrosion and Passivation]] |
| [[Eutectic and Eutectoid Reactions]] | [[Iron-Carbon Phase Diagram]] | [[Polymer Glass Transition and Viscoelasticity]] |
| | [[Composite Rule of Mixtures]] | [[Ceramic Flaw Sensitivity]] |

## Tutorial sheets: full worked solutions

| Sheet | Solution note |
|---|---|
| Statics 1, sheet 1 | [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]] |
| Statics 1, sheet 2 | [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]] |
| Statics 1, sheet 3 | [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]] |
| Statics 1, sheet 4 | [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]] |
| Statics 1, sheet 5 | [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]] |
| Statics 1, sheet 6 | [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]] |
| Statics 2, sheet 1 | [[FEEG1002 Statics 2 Tutorial 1 - Stresses in Multiple Dimensions and Pressure Vessels Solutions]] |
| Statics 2, sheet 2 | [[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]] |
| Statics 2, sheet 3 | [[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]] |
| Statics 2, sheet 4 | [[FEEG1002 Statics 2 Tutorial 4 - Stresses on Inclined Sections and Stress Transformation Solutions]] |
| Statics 2, sheet 5 | [[FEEG1002 Statics 2 Tutorial 5 - Mohr's Circle Solutions]] |
| Statics 2, sheet 6 | [[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]] |
| Statics 2, sheet 7 | [[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]] |
| Statics 2, sheet 8 | [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]] |
| Materials, sheet 1 | [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] |
| Materials, sheet 2 | [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]] |
| Materials, sheet 3 | [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]] |
| Materials, sheet 4 | [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]] |
| Materials, sheet 5 | [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]] |
| Dynamics, sheet 1 | [[FEEG1002 Dynamics Tutorial 1 - Linear Motion Solutions]] |
| Dynamics, sheet 2 | [[FEEG1002 Dynamics Tutorial 2 - Curvilinear Motion Solutions]] |
| Dynamics, sheet 3 | [[FEEG1002 Dynamics Tutorial 3 - Work, Energy and Power Solutions]] |
| Dynamics, sheet 4 | [[FEEG1002 Dynamics Tutorial 4 - Linear Impulse and Momentum Solutions]] |
| Dynamics, sheet 5 | [[FEEG1002 Dynamics Tutorial 5 - Angular Impulse and Momentum Solutions]] |
| Dynamics, sheet 6 | [[FEEG1002 Dynamics Tutorial 6 - SDOF Free Vibration Solutions]] |
| Dynamics, sheet 7 | [[FEEG1002 Dynamics Tutorial 7 - Kinematics of Rigid Bodies Solutions]] |
| Dynamics, sheet 8 | [[FEEG1002 Dynamics Tutorial 8 - Kinetics of Rigid Bodies Solutions]] |
| Dynamics, sheet 9 | [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]] |

> [!info] How the solutions were checked
> - Every tutorial answer was reproduced numerically.
> - Statics 1 and 2, and Dynamics sheets 3–9, print official answers; all of them are matched.
> - Dynamics sheets 1–2 and Materials sheets 1–5 print no answer key, so their solutions were derived independently; graph readings were checked against high-resolution renders.
> - Where the sources contain a slip (e.g. the Galilean-cannon rebound height on Dynamics Lecture 4, slide 37), the note says so.

## Recommended study route
1. Read the topic note once for the physical model and its assumptions.
2. Attempt the tutorial sheet **before** opening the solution note.
3. Compare the **FBD and sign convention**, not just the final number. Most lost marks in this module are sign errors.
4. Use [[FEEG1002 Formula Sheet]] for a one-page equation map.

## All notes

```dataview
TABLE type, stream, status, file.mtime AS "Updated"
FROM "Year 1/FEEG1002 Mechanics, Materials and Structures"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **Builds on**: A-level mechanics (vectors, $F = ma$, moments), calculus, and [[SESA1016 Thermofluids Hub]] (energy, momentum balances).

| Later module | Bridge from FEEG1002 | Continue with |
|---|---|---|
| SESA2028 Aerospace Materials & Structures (structures) | bending, deflection, buckling, torsion, energy | [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]] · [[SESA2028 S2 - Beam Deflection and Bending Design]] · [[SESA2028 S3 - Shear Flow and Shear Centre]] · [[SESA2028 S4 - Torsion of Thin-Walled Sections]] · [[SESA2028 S5 - Euler Buckling and Effective Length]] · [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]] · [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] |
| SESA2028 (continuum) | stress and strain tensors, Hooke, pressure vessels, rotating bodies | [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] · [[SESA2028 S10 - Thick Cylinders and Shrink Fits]] · [[SESA2028 S11 - Spinning Discs]] |
| SESA2028 (materials) | Part C foundations | [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]] · [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]] · [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]] · [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] |
| [[SESA2027 Aerospace Mechanics & Control Hub]] | $\sum F = ma$ in rotating frames, SDOF vibration → poles, transfer functions, FRFs | [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]] · [[SESA2027 A5 - Frequency Response and Bode Plots]] · [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design]] |
| [[SESA2024 Astronautics Hub]] | angular momentum, gravity, orbital energy, inertia | [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · [[SESA2024 06 - Attitude Control]] |
| [[SESA2029 Digital Aerospace Methods Hub]] | beams, stress, energy principles → finite elements and modal analysis | [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] · [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]] · [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]] |

> [!tip] The cleanest progression
> - The Statics beam results are the special symmetric case of SESA2028's unsymmetrical bending, shear flow and thin-walled torsion.
> - The Dynamics SDOF oscillator is the physical model behind every pole, damping ratio and Bode plot in SESA2027.
> - The mass moment of inertia becomes the inertia matrix of spacecraft attitude control.

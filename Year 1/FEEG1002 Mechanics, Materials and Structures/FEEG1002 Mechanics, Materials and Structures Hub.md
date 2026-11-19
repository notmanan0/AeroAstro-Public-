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
All nine notes are `lectured` (Lectures 1–14, Oct 2024 – Jan 2025). Buckling, torsion and shear stresses (A7–A9) were not in the January exam.

1. [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]: free body diagrams, equilibrium and the choice of moment point, lever rule, stress, safety factor, stress concentration, strain, $k=EA/L$, Poisson's ratio, shear modulus
2. [[FEEG1002 A2 - Pin-Jointed Trusses]]: method of joints, method of sections, zero-force members, the counting test $2j=m+r$, bar extensions and the displacement diagram
3. [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]: supports, internal forces, sign convention ($Q$ down on the right face, $M$ sagging), $dQ/dx=-w$, $dM/dx=Q$, sketching, the largest moment
4. [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]: $M/I_{zz}=\sigma_{xx}/y=E/R$, neutral axis at the centroid, $I$ of standard sections, parallel axis theorem, singly symmetric sections
5. [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]: $EI\,v''=-M$ with $v$ down, double integration, off-centre point load, Macaulay brackets, standard results
6. [[FEEG1002 A6 - Statically Indeterminate Beams]]: counting reactions, propped cantilever by double integration and by superposition
7. [[FEEG1002 A7 - Euler Buckling of Struts]]: $v''+n^2v=0$, $P_{crit}=\pi^2EI/L_e^2$, modes, direction of buckling, effective lengths, truss braces
8. [[FEEG1002 A8 - Torsion of Circular Shafts]]: $T/J=\tau/r=G\theta/L$, $J=\pi D^4/32$, solid against hollow shafts
9. [[FEEG1002 A9 - Shear Stresses in Beams]]: complementary shear, $\sigma_{yx}=QA_sy_c/(bI)$, parabolic distribution, shear stress coefficient $K$, bending against shear

### Part B: Statics 2
1. [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]: stress element, $\sigma_{xy}=\sigma_{yx}$, 3D stress state, hoop $pR/t$ and longitudinal $pR/2t$, spheres
2. [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]: strain as displacement gradient, $\gamma_{xy}$ and $\varepsilon_{xy}=\gamma_{xy}/2$, volumetric strain, $\alpha\Delta T$, series and parallel thermal problems
3. [[FEEG1002 B3 - Generalised Hooke's Law]]: 3D and plane-stress Hooke's law and inverses, $G$ and $K$, incompressibility, plane strain
4. [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]: wedge derivation, Mohr's circle (shear down), principal stresses, maximum in-plane shear
5. [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]: gauges, Wheatstone bridge, strain transformation, strain circle, 0/45/90 and 0/60/120 rosettes
6. [[FEEG1002 B6 - Yield Criteria]]: Tresca and von Mises, equivalent stress, hexagon and ellipse, safety factor and failure load

### Part C: Materials

1. [[FEEG1002 C1 - Atoms and Bonding]]: electron shells and valence, the bond force and energy curve ($E\approx S_0/r_0$), ionic, covalent, metallic and secondary bonds, the three material classes
2. [[FEEG1002 C2 - Crystal Structures and Crystallography]]: unit cells, close-packed stacking (FCC, HCP) and BCC, atoms per cell, $a(R)$, APF, polymorphism, Miller indices
3. [[FEEG1002 C3 - Diffusion]]: vacancy and interstitial mechanisms, steady-state flux and Fick's first law, Arrhenius $D(T)$ and time–temperature trade-offs
4. [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]: engineering and true stress–strain, 0.2 % offset, UTS, ductility, resilience, dislocations, slip systems, solid solutions
5. [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]: work hardening, Hall–Petch, coherent and incoherent precipitates, recovery, recrystallisation and grain growth
6. [[FEEG1002 C6 - Phase Diagrams]]: tie lines and the lever rule (Cu–Ni), coring, the Pb–Sn eutectic, microstructures on cooling, primary and total amounts
7. [[FEEG1002 C7 - Steels and Precipitation Hardening]]: Fe–Fe₃C, eutectoid and pearlite, hypo- and hypereutectoid steels, carbon and properties, Al–Cu age hardening and the ageing curve
8. [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]: ductile and brittle surfaces, stress concentrations, Griffith, $K$ and $K_{IC}$, fracture against yield, the DBTT and Charpy
9. [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]: S–N curves, $\Delta K$ and the Paris law with integrated life, the creep curve and $\dot\varepsilon_s$, emf series, passivation and protection
10. [[FEEG1002 C10 - Polymers - Structure and Mechanics]]: chain architectures, $\bar M_n$ and $\bar M_w$, crystallinity and $T_g$, thermoplastics, elastomers and thermosets, cold drawing, stress relaxation and $E_r$
11. [[FEEG1002 C11 - Ceramics and Composites]]: radius ratio and coordination, glasses and viscosity points, ceramic brittleness and strength statistics, pre-stressing, rule of mixtures (isostrain and isostress)

### Part D: Dynamics
1. [[FEEG1002 D1 - Linear Motion of Particles]]: kinematics and the choice of integral, Newton's laws, friction, springs, drag, buoyancy, pulleys
2. [[FEEG1002 D2 - Curvilinear Motion]]: projectiles, $n$–$t$ coordinates, $v^2/\rho$, radius of curvature, relative motion
3. [[FEEG1002 D3 - Work, Energy and Power]]: work, potential energy, work–energy principle, conservation, power and efficiency
4. [[FEEG1002 D4 - Linear Impulse and Momentum]]: impulse, conservation, central impact, coefficient of restitution, Galilean cannon
5. [[FEEG1002 D5 - Angular Impulse and Momentum]]: $\mathbf H_O = \mathbf r\times m\mathbf v$, $\sum M_O = \dot H_O$, central forces, orbits
6. [[FEEG1002 D6 - Single Degree of Freedom Vibration]]: $\omega_n$, damping regimes, log decrement, FRF, unbalance
7. [[FEEG1002 D7 - Kinematics of Rigid Bodies]]: rotation, absolute motion, relative velocity, IC, rolling without slip
8. [[FEEG1002 D8 - Kinetics of Rigid Bodies]]: $I$, parallel axis, $\sum M_G = I_G\alpha$, rolling with slip, rigid-body impulse–momentum
9. [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]: $KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2$, work of a couple, energy methods for mechanisms

## Coverage

Every topic note is `lectured`. The tables give each note's lectures and sources.

### Statics 1 coverage

| Note | Lectures | Dates | Status | Source of scope |
|---|---|---|---|---|
| A1 | L1, L2 | 7–8 Oct 2024 | lectured | transcripts L1 ll. 33–856, L2 ll. 6–579; decks 1–2 |
| A2 | L3, L4 | Oct 2024 | lectured | transcripts L3 ll. 12–761, L4 ll. 1–848; decks 3–4 |
| A3 | L5, L6 | 28 Oct, 4 Nov 2024 | lectured | transcripts L5 ll. 20–702, L6 ll. 10–849; L6c video (no transcript) from deck 6, slides 23–34 |
| A4 | L7, L8 | 11, 18 Nov 2024 | lectured | transcripts L7 ll. 1–869, L8 ll. 1–757; decks 7–8 |
| A5 | L9, L10 | 25 Nov 2024 | lectured | transcript L9 ll. 17–848; L10 (Macaulay) recorded videos with no transcript, written from deck 10 and the L11 recap (ll. 13–93) |
| A6 | L11 | 2 Dec 2024 | lectured | transcript L11 ll. 1–823; deck 11 |
| A7 | L12 | 9 Dec 2024 | lectured | transcript L12 ll. 10–631; deck 12 |
| A8 | L13 | 10 Dec 2024 | lectured | transcript L13 ll. 3–563; deck 13 |
| A9 | L14 | 6 Jan 2025 | lectured | transcript L14 ll. 10–616; deck 14 |

### Statics 2 coverage

| Note | Status | Scope | Sources |
|---|---|---|---|
| [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels\|B1]] | lectured | Internal forces, stress element and notation, complementary shear, 3D stress, thin-walled cylinders and spheres | Lecture 1 (27 Jan 2025), slides L01, Tutorial 1 |
| [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain\|B2]] | lectured | Normal, shear and volumetric strain, rotation removed, thermal strain, constrained bars in series and parallel | Lectures 2–3 (3 and 10 Feb 2025), slides L02–L03, Tutorial 2 |
| [[FEEG1002 B3 - Generalised Hooke's Law\|B3]] | lectured | Plane-stress, 3D and plane-strain Hooke's law with inverses, $G=E/2(1+\nu)$ proof, bulk modulus, thermal term | Lecture 4 (17 Feb 2025), slides L04, Tutorials 3 and 8 (Q2) |
| [[FEEG1002 B4 - Stress Transformation and Mohr's Circle\|B4]] | lectured | Inclined sections, wedge derivation, double-angle form, Mohr's circle, principal stresses and maximum shear | Lectures 5–6 (24 Feb and 3 Mar 2025), slides L05–L06, Tutorials 4, 5 and 8 (Q4) |
| [[FEEG1002 B5 - Strain Measurement and Strain Rosettes\|B5]] | lectured | Gauge factor, Wheatstone bridge, strain transformation and circle, torsion gauges, rosettes, DIC | Lecture 7 (10 Mar 2025), slides L07, Tutorials 6 and 8 (Q1, Q3) |
| [[FEEG1002 B6 - Yield Criteria\|B6]] | lectured | Tresca (3D and plane stress), von Mises (RMS shear, equivalent stress), comparison, yield surface, safety factor | Lecture 8 (17 Mar 2025), slides L08, Tutorials 7 and 8 (Q1, Q3) |

Lecture 9 (12 May 2025) is a revision lecture and is cited in every B note.

### Materials coverage

| Note | Status | Scope | Lectures (transcripts) | Slides and sheet |
|---|---|---|---|---|
| [[FEEG1002 C1 - Atoms and Bonding]] | lectured | atoms, bond curve, primary and secondary bonds | L1, 11 Oct 2024 | decks 01–02 |
| [[FEEG1002 C2 - Crystal Structures and Crystallography]] | lectured | FCC/BCC/HCP, APF, polymorphism, Miller indices | L2, 14 Oct 2024 | deck 03; Tutorial 1 |
| [[FEEG1002 C3 - Diffusion]] | lectured | mechanisms, Fick's first law, Arrhenius | L3, 15 Oct 2024 | deck 04; Tutorial 1 |
| [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]] | lectured | tensile properties, dislocations, slip, alloying | L4, 21 Oct; L5, 22 Oct 2024 | decks 05–06; Tutorial 2 |
| [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]] | lectured | work hardening, Hall–Petch, precipitates, annealing | L6, 28 Oct 2024 | deck 07; Tutorial 2 |
| [[FEEG1002 C6 - Phase Diagrams]] | lectured | tie lines, lever rule, Cu–Ni, Pb–Sn eutectic | L7, 29 Oct; L8, 4 Nov 2024 | decks 08–09; Tutorial 3 |
| [[FEEG1002 C7 - Steels and Precipitation Hardening]] | lectured | Fe–Fe₃C, pearlite, steels, age hardening | L9, 5 Nov; L10, 11 Nov 2024 | decks 10–11; Tutorial 3 |
| [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]] | lectured | Griffith, $K_{IC}$, design, DBTT | L11, 12 Nov; L12, 18 Nov 2024 | decks 12–13; Tutorial 4 |
| [[FEEG1002 C9 - Fatigue, Creep and Corrosion]] | lectured | S–N, Paris law, creep, corrosion | L13, 19 Nov; L14, 25 Nov 2024 | decks 14–15; Tutorial 4 |
| [[FEEG1002 C10 - Polymers - Structure and Mechanics]] | lectured | chains, $T_g$, stress–strain, viscoelasticity | L15, 26 Nov; L16, 2 Dec 2024 | decks 16–17; Tutorial 5 |
| [[FEEG1002 C11 - Ceramics and Composites]] | lectured | ceramic structure and strength, rule of mixtures | L17, 3 Dec; L18, 9 Dec; L19, 13 Dec 2024 (repeat of L18) | decks 18–19; Tutorial 5 |

### Dynamics coverage

| Note | Status | Scope | Sources |
|---|---|---|---|
| [[FEEG1002 D1 - Linear Motion of Particles\|D1]] | lectured | Rectilinear kinematics and integral forms, SUVAT, Newton's laws and inertial frames, gravitation and escape velocity, Coulomb friction, springs, ropes, drag and terminal velocity, buoyancy, dependent motion and mechanical advantage | Lecture 01 slides pp. 1–63; L01, L02b; DAMS1-1 to DAMS1-4, DAMS1-Ex1, DAMS1-Ex2; L12 (ship with linear drag) |
| [[FEEG1002 D2 - Curvilinear Motion\|D2]] | lectured | Rectangular components, projectiles (drag qualitative), $n$–$t$ acceleration and its derivation, radius of curvature, binormal, circular motion, $n$–$t$ equations of motion, relative motion of particles, pendulum | Lecture 02 slides pp. 1–45; L03, L04; DAMS2-1, DAMS2-1-1, DAMS2-2, DAMS2-3 (relative motion only), DAMS2-4, DAMS2-Ex1, DAMS2-Ex2 |
| [[FEEG1002 D3 - Work, Energy and Power\|D3]] | lectured | Work of weight, gravity, springs, friction; conservative forces and potentials; work–energy principle; conservation; friction and heat; systems; power and efficiency; loop, incline, motor, collar past paper | Lecture 03 slides pp. 1–43; L05, L05b, L06; L11 (collar), L12 (pendulum); DAMS3-1 to DAMS3-3 |
| [[FEEG1002 D4 - Linear Impulse and Momentum\|D4]] | lectured | Impulse–momentum, average force, impulsive forces, systems, conservation, central impact, restitution, energy loss, Newton's cradle, Galilean cannon; oblique impact summarised (not assessed) | Lecture 04 slides pp. 1–46; L07, L07b, L08, L08b; DAMS4-1 to DAMS4-3 |
| [[FEEG1002 D5 - Angular Impulse and Momentum\|D5]] | lectured | Moments of vectors, angular momentum, $\sum M_O = \dot H_O$, angular impulse, conservation and central forces, ride, orbit, fun-fair game | Lecture 05 slides pp. 1–33; L10b, L11; DAMS6-1 to DAMS6-3 (live theory lecture of 26 Feb 2025 not recorded) |
| [[FEEG1002 D6 - Single Degree of Freedom Vibration\|D6]] | lectured | SDOF model, equivalent springs, undamped and damped free vibration (all three regimes), log decrement, phasors and FRF, stiffness/damping/mass-controlled regions, unbalance; gantry, speed camera, wheel hop | Lecture 06 slides pp. 1–62; L13, L14, L14b, L15, L16; S6-1 to S6-3b |
| [[FEEG1002 D7 - Kinematics of Rigid Bodies\|D7]] | lectured | Planar motion types, fixed-axis rotation, absolute motion (rolling, cam), relative velocity equation, IC; relative acceleration summarised (not assessed) | Lecture 07 slides pp. 1–48; L17b, L18b (ll. 1–255); DAMS7-1 to DAMS7-4 |
| [[FEEG1002 D8 - Kinetics of Rigid Bodies\|D8]] | lectured | Centre of mass, $I$ by integration, parallel axis (proved), radius of gyration, planar equations of motion (derived), translation, fixed-axis rotation, rolling with/without slip, rigid-body impulse–momentum, driven-wheel mock question | Lecture 08 slides pp. 1–52; L17b, L18b (ll. 248–791), Mock; DAMS8-1a to DAMS8-3a; DAMS10-1 to DAMS10-4b (no slides) |
| [[FEEG1002 D9 - Work and Energy for Rigid Bodies\|D9]] | lectured | Rigid-body kinetic energy (derived), work of forces and couples, forces doing no work, rolling, slip and rolling resistance, internal forces, energy methods; disc, rod-in-slots, rod-and-spring, rolling race | Lecture 09 slides pp. 1–52; DAMS9-1 to DAMS9-5; L18b (race). No live 2025 lecture covered this chapter |

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
| [[Standard Beam Deflections]] | [[Tresca Yield Criterion]] | [[Principle of Linear Impulse and Momentum]] | [[Kinetic Energy of a Rigid Body]] |
| [[Superposition for Indeterminate Beams]] | [[Von Mises Yield Criterion]] | [[Coefficient of Restitution]] | |
| [[Torsion of Circular Shafts]] | | [[Principle of Angular Impulse and Momentum]] | |
| [[Shear Stress Distribution in Beams]] | | | |
| [[Euler Buckling]] (Year 2) | | | |
| [[Effective Length]] (Year 2) | | | |

[[Damping Ratio and Natural Frequency]] and [[Frequency Response Function]] are Year 2 (SESA2027) notes; [[Euler Buckling]] and [[Effective Length]] are Year 2 (SESA2028) notes that A7 builds on. The Year 2 [[Von Mises and Tresca Yield Criteria]] note continues B6.

### Materials concepts

| Structure and processing | Mechanical behaviour | Failure and non-metals |
|---|---|---|
| [[Atomic Bonding and Interatomic Potential]] | [[Engineering Stress-Strain Properties]] | [[Griffith Criterion and Fracture Toughness]] |
| [[Crystal Structures and Atomic Packing Factor]] | [[Dislocations and Slip Systems]] | [[Ductile-to-Brittle Transition]] |
| [[Miller Indices for Planes and Directions]] | [[Strengthening Mechanisms in Metals]] | [[S-N Curves and Paris Law]] |
| [[Fick's Laws and Arrhenius Diffusion]] | [[Annealing of Cold-Worked Metals]] | [[Creep]] |
| [[Tie Lines and Lever Rule]] | [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening\|Precipitation Hardening]] | [[Galvanic Corrosion and Passivation]] |
| [[Eutectic and Eutectoid Reactions]] | [[Composite Rule of Mixtures]] | [[Polymer Glass Transition and Viscoelasticity]] |
| [[Iron-Carbon Phase Diagram]] | | [[Ceramic Flaw Sensitivity]] |

### Concept map

**Statics 1 concept map.** [[Free Body Diagram and Equilibrium]] → internal forces by cutting: in trusses through [[Method of Joints and Method of Sections]] (limited by [[Static Determinacy]]), in beams through [[Shear Force and Bending Moment Relations]]. Bar forces → [[Stress, Strain and Young's Modulus]] → bar extensions → [[Williot Displacement Diagram]]. Bending moment → [[Engineer's Bending Theory]] (with [[Parallel Axis Theorem]] for $I$) → stress; and → $EI\,v''=-M$ → [[Macaulay's Method]] and [[Standard Beam Deflections]] → [[Superposition for Indeterminate Beams]]. Shear force → [[Shear Stress Distribution in Beams]]. Torque → [[Torsion of Circular Shafts]]. Compression of slender members → [[Euler Buckling]] with [[Effective Length]] (Year 2 concept notes, shared).

**Statics 2 concept map.**

- [[Stress Tensor and Stress Element]] → [[Thin-Walled Pressure Vessels]] (first application)
- [[Strain Components and Volumetric Strain]] + [[Thermal Strain]] → [[Generalised Hooke's Law]] (links stress and strain)
- [[Stress Transformation Equations]] → [[Mohr's Circle]] → [[Principal Stresses]]
- [[Strain Gauge Rosettes]] (strain transformation + Hooke) → [[Von Mises Yield Criterion]] / [[Tresca Yield Criterion]] → safety factor

**Materials concept map.**

- Bonding → stiffness and melting point: [[Atomic Bonding and Interatomic Potential]] → [[Engineering Stress-Strain Properties]]
- Structure → slip → strength: [[Crystal Structures and Atomic Packing Factor]] → [[Miller Indices for Planes and Directions]] → [[Dislocations and Slip Systems]] → [[Strengthening Mechanisms in Metals]]
- Diffusion drives every heat treatment: [[Fick's Laws and Arrhenius Diffusion]] → [[Annealing of Cold-Worked Metals]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] · [[Creep]]
- Phase diagrams → microstructure: [[Tie Lines and Lever Rule]] → [[Eutectic and Eutectoid Reactions]] → [[Iron-Carbon Phase Diagram]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]]
- Flaws → failure: [[Griffith Criterion and Fracture Toughness]] → [[Ductile-to-Brittle Transition]] · [[S-N Curves and Paris Law]] · [[Ceramic Flaw Sensitivity]]
- Non-metals: [[Polymer Glass Transition and Viscoelasticity]] · [[Ceramic Flaw Sensitivity]] → [[Composite Rule of Mixtures]]

**Dynamics concept map.**

- Newton's laws → integrated over distance → [[Work-Energy Principle]] → [[Kinetic Energy of a Rigid Body]] (D9)
- Newton's laws → integrated over time → [[Principle of Linear Impulse and Momentum]] (D4) → [[Principle of Angular Impulse and Momentum]] (D5) → rigid-body impulse (D8)
- Spring force (D1) → [[Equivalent Spring Stiffness]] → SDOF vibration and [[Logarithmic Decrement]] (D6)
- Circular motion and [[Normal and Tangential Coordinates]] (D2) → rotation of rigid bodies (D7) → [[Planar Rigid-Body Equations of Motion]] (D8)

## Exam skills

### Statics 1

- Draw a free body diagram with every support reaction in an assumed direction, and choose the moment point that removes the most unknowns ([[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|A1]]).
- Find a bar force in one equation with the method of sections, and spot zero-force members before calculating ([[FEEG1002 A2 - Pin-Jointed Trusses|A2]]).
- Sketch SFD and BMD from $dQ/dx=-w$ and $dM/dx=Q$, and check every candidate for the largest $|M|$ ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams|A3]]).
- Locate the centroid of a built-up section, find $I$ by the parallel axis theorem, and check the extreme fibre on each side ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]]).
- Write a single Macaulay expression for $M$, including cancelling UDLs, integrate without expanding brackets, and apply the boundary conditions ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]]).
- Solve a propped cantilever by double integration or by superposition of standard cases ([[FEEG1002 A6 - Statically Indeterminate Beams|A6]]).
- (Not in the January exam) Euler load with the right effective length and the weaker axis; torsion of solid and hollow shafts; shear stress at the neutral axis and fastener spacing ([[FEEG1002 A7 - Euler Buckling of Struts|A7]]–[[FEEG1002 A9 - Shear Stresses in Beams|A9]]).

### Statics 2

- Read $\sigma_{xx}$, $\sigma_{yy}$ and the sign of $\sigma_{xy}$ from a drawn element (sign from the right-hand face). → [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#Sign convention|B1]]
- Hoop and longitudinal stresses, maximum pressure, wall thickness and bolt loads for thin cylinders and spheres. → [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels#4. Thin-walled pressure vessels|B1]]
- Constrained thermal expansion by superposition: release, expand, push back, impose compatibility and equilibrium. → [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Superposition for constrained assemblies|B2]]
- Plane-stress Hooke's law both ways, including changes of length, diameter and thickness; choose plane stress or plane strain correctly. → [[FEEG1002 B3 - Generalised Hooke's Law|B3]]
- Stresses on an inclined plane (welds, glue lines) with $\theta$ measured to the plane's normal. → [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#2. Plane-stress transformation|B4]]
- Mohr's circle with shear positive down: centre, radius, principal stresses, $\theta_p$ with the right sense, maximum shear and its normal stress. → [[FEEG1002 B4 - Stress Transformation and Mohr's Circle#4. Mohr's circle|B4]]
- Rosette readings to $\varepsilon_{xx}$, $\varepsilon_{yy}$, $\varepsilon_{xy}$ (using $\varepsilon_{xy}$, not $\gamma_{xy}$), then to stresses. → [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#6. Strain gauge rosettes|B5]]
- Von Mises equivalent stress, safety factor and maximum load by linear scaling; Tresca including the out-of-plane shear in vessel walls. → [[FEEG1002 B6 - Yield Criteria|B6]]

### Materials

- Count atoms per cell, write $a(R)$ for FCC and BCC, and derive the APF (0.74, 0.68); predict the volume change on an FCC↔BCC change. → [[FEEG1002 C2 - Crystal Structures and Crystallography]]
- Index cubic directions (head minus tail) and planes (reciprocals of intercepts), and test whether a direction lies in a plane. → [[FEEG1002 C2 - Crystal Structures and Crystallography#5. Miller indices]]
- Steady-state flux and mass through a membrane; $Q$ from two diffusion coefficients; time at a new temperature from $D_1t_1=D_2t_2$. → [[FEEG1002 C3 - Diffusion]]
- Read $E$, $\sigma_{0.2}$, UTS, %EL and resilience from a tensile curve; elastic extension and Poisson contraction of a bar; true stress at the UTS. → [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]
- Hall–Petch constants from two grain sizes; elastic recovery on unloading a work-hardened bar; $Q$ for recrystallisation from two rates. → [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]
- Tie line and lever rule at a point; primary phase and eutectic just above, total phases just below the eutectic; sketch microstructures on cooling. → [[FEEG1002 C6 - Phase Diagrams]]
- Proeutectoid and pearlite fractions for hypo- and hypereutectoid steels; choose an alloy and treatment for precipitation hardening and explain the ageing curve. → [[FEEG1002 C7 - Steels and Precipitation Hardening]]
- Fast fracture against general yield from $K_{IC}=Y\sigma\sqrt{\pi a}$, with $a$ = half an internal crack; critical flaw size; Griffith strength of glass; explain how strengthening moves the DBTT. → [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]
- Read fatigue limit, life and strength off an S–N curve; $\Delta K$ with a compressive minimum; integrate the Paris law for life; $n$ and rate changes in steady-state creep; cell voltage and which metal corrodes. → [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]
- Stress–strain curves of a thermoplastic below $T_g$, between $T_g$ and $T_m$, and near $T_m$; $\tau$ and $\sigma(t)$ in stress relaxation; $E_r$ against $T$ for amorphous and crystalline polymers. → [[FEEG1002 C10 - Polymers - Structure and Mechanics]]
- Coordination number from $r_C/r_A$; why ceramics are brittle and why design is statistical; longitudinal and transverse moduli and fibre load fraction of an aligned composite. → [[FEEG1002 C11 - Ceramics and Composites]]

### Dynamics

- Draw the free-body diagram and the kinetic diagram first; most questions award marks for them.
- Decide what $a$ depends on ($t$, $s$ or $v$) before integrating; use SUVAT only for constant acceleration.
- Never write $F_s = \mu_sN$ in an equation of motion: find static friction from the equations, then check it.
- Pick the principle from the quantities: forces–speeds–distances → work–energy; forces–speeds–times or impacts → impulse–momentum; moments about a fixed point or a centre of attraction → angular momentum.
- Name the point when claiming conservation of angular momentum.
- For vibration, compare $\omega$ with $\omega_n$ first and use the matching approximation of $X/F$; keep $\omega$ (rad/s) and $f$ (Hz) apart.
- For rigid bodies, take moments about a fixed pivot ($I_O$) or a contact point to remove unknown reactions; for rolling, assume no slip, then check $F \le \mu_sN$.
- Give units with every numerical answer and check answers dimensionally.

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
> - Every tutorial answer was reproduced numerically (Python).
> - Statics 1 sheets 1–6 and Statics 2 sheets 1–8 come with official worked solutions; Dynamics sheets 3–9 print final answers only. All are matched, with rounding or interpretation differences noted under the question (e.g. Dynamics 4 Q6, Dynamics 7 Q3(d), Dynamics 9 Q4).
> - Dynamics sheets 1–2 and Materials sheets 1–5 print no answer key, so their solutions were derived independently; graph readings were taken from the sheets' figures.
> - Where the sources contain a slip (e.g. the Galilean-cannon rebound height on Dynamics Lecture 4, slide 37), the topic note lists it in its "Transcript and slide slips" section.

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

## Sources

### Statics 1

- Statics 1: lecture slide decks 1–14 in `02 - Sources/Statics 1/Lectures/`; transcripts of Lectures 1–9 and 11–14 in `02 - Sources/Lectures/` (Lecture 10 and the Lecture 6c example were videos with no transcript); tutorial sheets 1–6 with official solutions in `02 - Sources/Statics 1/Tutorials/`. Figures: `01 - Notes/Figures/generate_statics1_figures.py` (shared Year 3 style, 55 `s1_*.png`).

### Statics 2

- Transcripts (`02 - Sources/Lectures/`): `FEEG1002 Lecture 1 - Statics 2 - …` to `FEEG1002 Lecture 9 - Statics 2 - Revision - …` (27 Jan – 12 May 2025; Lecture 9 is revision).
- Slides (`02 - Sources/Statics 2/Lectures/`): `Lecture 01 - Stress in Multiple Dimensions and Pressure Vessels.pdf` to `Lecture 08 - Yield Criteria.pdf`.
- Tutorial sheets with official solutions (`02 - Sources/Statics 2/Tutorials/`): sheets 01–08; solution notes in `01 - Notes/Tutorials/FEEG1002 Statics 2 Tutorial 1–8`, every answer re-checked numerically and linked to the teaching section.
- Figures: `01 - Notes/Figures/generate_statics2_figures.py` (shared `vault_style`), outputs `s2_*.png`.

### Materials

- Slides: `02 - Sources/Materials/Lectures/` decks 01–19 (01–02 bonding; 03 crystallography; 04 diffusion; 05–06 mechanical properties and plastic deformation; 07 strengthening and annealing; 08–09 phase diagrams; 10 steels; 11 precipitation hardening; 12–15 failure of materials; 16–17 polymers; 18 ceramics; 19 composites).
- Transcripts: `02 - Sources/Lectures/` Materials L1–L19 (`FEEG1002 Lecture 2024-10-11.txt` is L1; L2–L9 and L11–L14 carry topic names; L10 and L15–L19 are `FEEG1002 Lecture N.txt`; L19 repeats L18).
- Tutorial sheets: `02 - Sources/Materials/Tutorials/Tutorial Sheet 01`–`05` (no answer keys; solutions in the five Materials tutorial notes were computed independently).
- Figures: `01 - Notes/Figures/generate_materials_figures.py` (55 figures, prefix `m`, shared Year 3 style).

### Dynamics

- Slides: `02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf` … `Lecture 09 - Work and Energy for Rigid Bodies.pdf`.
- Tutorial sheets: `02 - Sources/Dynamics/Tutorials/Tutorial Sheet 01 - Linear Motion.pdf` … `Tutorial Sheet 09 - Work and Energy for Rigid Bodies.pdf` (sheets 1–2 print no answers; sheets 3–9 print final answers but no worked solutions).
- Live 2025 lectures (G. Squicciarini; T. Waters for vibration), in `02 - Sources/Lectures/`: 29–30 Jan (D1), 5–6 Feb (D2), 12–13 Feb (D3), 19–20 Feb (D4), 27 Feb (D5), 5–6 Mar revision (D1–D5 past papers), 12–20 Mar (D6), 26–27 Mar (D7–D8), 15 May mock walkthrough (D8). See [[FEEG1002 Transcript Index]].
- Pre-recorded 2020–22 videos: DAMS-1 to DAMS-10 and Section 6 (vibration), in the same folder.

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

## Cambridge practice

- [[FEEG1002 Cambridge Part IIA Practice]]: third-year Cambridge questions (Part IIA) that revise this module, listed under each topic note.

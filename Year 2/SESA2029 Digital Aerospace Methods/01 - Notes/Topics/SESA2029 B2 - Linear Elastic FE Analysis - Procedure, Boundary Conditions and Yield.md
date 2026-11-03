---
title: "SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 13
tags: [sesa2029, fea, linear-elastic, yield]
aliases: ["Linear elastic FEA", "FE procedure", "Yield criteria in FEA", "FEA Lecture 4"]
date: 2026-10-30
status: lectured
coverage: "FEA week 2 (2026-02-06 11:01)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
next_topics: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]"]
key_concepts: ["[[Boundary Conditions and Rigid Body Modes]]", "[[Von Mises and Tresca Yield Criteria]]", "[[Stress Concentration Factor and Factor of Safety]]", "[[Mesh Convergence and Grid Independence]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-06 - 1101.txt"]
---

# SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield

> [!abstract] Summary
> Linear elastic FEA assumes a linear elastic material and small deformations, so the stiffness matrix is constant and every result scales in proportion to the load. That covers most design analysis, but it cannot predict buckling or plastic deformation, only the load at first yield. The supports must remove all rigid-body modes without over-constraining the model, symmetry can shrink it, and the von Mises (or, more conservatively, Tresca) stress from one elastic run gives the yield load directly.

> [!summary]- Exam use: quick path
> - **Use it when:** asked whether linear FEA is adequate, how to support a model, what symmetry allows, or for the load at first yield from one analysis.
> - **Assumptions:** stress below yield everywhere; displacements small enough that $[K]$ does not change; consistent units.
> - **Method:** 1. Check the two assumptions and whether buckling or plasticity matter. 2. Constrain the 6 rigid-body modes in 3D (3 in 2D) and no more. 3. Use symmetry planes with zero normal displacement where possible. 4. Read $\sigma_{e,max}$ (von Mises) or $SI_{max}$ (Tresca). 5. Scale: $P_Y=P\,\sigma_Y/\sigma_{max}$, then apply a safety factor.
> - **Common mistakes:** fixing every bottom node in both directions (over-constraint and false corner stresses); trusting a peak stress from a single coarse mesh.
> - **Practise:** [[#Worked example: nozzle yield pressure and the two criteria]] · [[SESA2029 FEA Worked Examples]]

All three labs are linear elastic analyses, so this lecture sets out the assumptions, limits and practical pitfalls of the method (2026-02-06 11:01, ll. 1–10).

"Linear" means the structure behaves like a single spring: double the load and every displacement, strain and stress doubles. That requires the material to stay on the straight part of its stress–strain curve, and the structure to deform so little that its geometry, and therefore its stiffness, is effectively unchanged. Under those conditions one analysis answers every load level, which is what makes linear FEA cheap, reliable and scalable, and why Airbus and Rolls-Royce still size structures with it before any nonlinear work (ll. 26–35).

## 1. The two assumptions and their limits

The first assumption is a linear elastic material: stress proportional to strain with constant Young's modulus $E$, and stress kept below the yield or brittle-fracture stress, so the properties do not change through yielding, creep or crack growth (ll. 1–50). Once a material yields, $E$ alone no longer describes it. Aluminium, steel and titanium are used in their linear range in normal service; viscous materials behave differently.

The second is small-deformation theory: the deformation is small enough not to change the structural response, so the stiffness matrix stays constant (ll. 11–25). With large deformations the stiffness depends on the amplitude of the response, which affects both stress and dynamic predictions. Lightweight composite structures that flex a lot need nonlinear procedures, an active research area and the subject of [[SESA2029 B9 - Nonlinear FE Analysis|B9]].

> [!warning] Lecture slip (2026-02-06 11:01, ll. 21–25)
> "The A350 and A380 [are] made by the composite materials." The A350 airframe is about half composite by weight, but the A380 is mostly aluminium (composites roughly a quarter); the B787 is the other composite-intensive example.

Whether linear analysis is sufficient depends on three questions (ll. 61–95). Where is the analysis in the design cycle? Early on, hand sizing with closed-form solutions for beams, cylinders and spheres may be more appropriate than any FEA. Is the structure likely to buckle? Small-deformation theory does not pick up buckling, yet it is a main failure mode of aerospace structures: wing skins are divided into panels between stiffeners precisely to prevent it, and if buckling is the mode to avoid, a buckling analysis is needed. Will the material deform plastically? Linear FEA cannot model plasticity, but it does give the load at which first yield occurs.

## 2. The procedure in practice

The three stages from [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method|B1]] each hide choices (ll. 96–245).

Geometry can be built in the FE program or imported from SolidWorks or CATIA. Element choice is a trade-off between accuracy and cost: the lab beam can use BEAM188 or BEAM189, which differ in number of nodes and in how well they represent the theoretical deformation (ll. 121–135). The example bracket uses 10-node tetrahedra, with nodes at the corners and mid-edges, which mesh irregular shapes easily ([[Solid Elements (Tetrahedra and Hexahedra)]]). Each tetrahedral node has three translational DOF and no rotations, because rotation is represented by the relative translations of several nodes (ll. 171–185).

Linear stress analysis needs $E$ and Poisson's ratio $\nu$; modal analysis also needs the density. Material choice is driven by cost (aluminium cheapest, then steel, then composites), manufacturability (metals are easy, composites are laid up ply by ply), performance and availability (ll. 141–170). Composites drive modern aerospace through their high specific stiffness: a composite fan blade is lighter, so its centrifugal load is lower and a larger fan diameter becomes possible. (The lecture cites the "Trent 7000 XWB" here, ll. 156–160; the Trent XWB and Trent 7000 actually use hollow titanium blades, and composite fans are found on GE's GEnx and GE9X and Rolls-Royce's UltraFan demonstrator.)

The software has no units; it multiplies numbers. Geometry, material properties and loads must therefore use one consistent set: SI (m, N, Pa, kg/m³), or mm, N, MPa with density in tonne/mm³ (ll. 51–60, 166–170). Mixing millimetre geometry with $E$ in pascals is a classic error.

Supports are applied as prescribed displacements at nodes, fixed in some or all of $x$, $y$, $z$; the bracket's back face is fully fixed as if bonded to a rigid foundation (ll. 166–190). Loads go on directly as nodal forces or element pressures, or indirectly on the solid model's faces and edges, from which the program transfers them to the mesh. APDL can script any load function, so a CFD pressure map can be applied to a wing; since the deformed wing changes the CFD boundary, the two are iterated in an aeroelastic analysis at a later design stage (ll. 191–210).

The solution step assembles and solves $\{F\}=[K]\{d\}$, then back-calculates strains, stresses and reactions; for linear analysis it is fully automatic (ll. 211–220).

Post-processing starts with the deformed shape, automatically scaled to be visible, which is the first check that the supports are right; then displacement contours, then stress contours of the three normal, three shear or three principal stresses, or the von Mises equivalent stress (ll. 221–265). A common lab mistake is forgetting to read the results file before plotting, so nothing seems to change when the thickness is changed. Exporting results to Excel or Python is often more flexible than the GUI. The highest stress usually sits at a sharp change of geometry, so the fillet radius there is a design choice ([[Stress Concentration Factor and Factor of Safety]]; a perfectly sharp corner is a singularity, [[Stress Singularities]]).

### The answer is approximate

More elements give a better approximation, and a graduated mesh puts more of them where the stress is high (ll. 266–295). In the lecture's T-section example the peak normal stress rises from 393.6 MPa on a uniform coarse mesh to 417.1 MPa with a graded mesh refined round the fillet, so a single coarse mesh underestimates the peak. A convergence study is part of every stress analysis; the plate with a hole in lab 2 is where it is practised ([[Mesh Convergence and Grid Independence]]).

> [!warning] Lecture slip (2026-02-06 11:01, ll. 281–290)
> The refined value is read out as 470 MPa. The slide's contour legend gives a maximum of 417.1 MPa for the refined mesh (and 393.6 MPa for the coarse one).

## 3. Rigid-body motion and over-constraint

If the model is not constrained, it can move through space undeformed and strain-free; $[K]$ is singular and the solver usually fails (ll. 321–335). Try solving the lab beam without its clamp: there is no answer, because the structure just floats. A 3D body has six rigid-body modes, three translations and three rotations; a 2D body has three. Removing them all without over-constraining the model is harder than it sounds ([[Boundary Conditions and Rigid Body Modes]]).

The lecture's example is a 2D block resting on a surface with pressure on top (ll. 331–350). Fixing $u_y=0$ at the bottom nodes prevents translation in $y$ and rotation about $z$, but not sliding in $x$, so a rigid-body mode remains. Fixing both $u_x$ and $u_y$ at every bottom node stops the rigid-body motion but over-constrains the model: as the block is squashed, Poisson's effect makes it want to expand sideways, and the fixed bottom cannot, so false stress concentrations appear at the bottom corners instead of the uniform stress of the real block. The right answer is $u_y=0$ along the bottom and $u_x=0$ at a single point, or on a line of symmetry. Choosing constraints needs thought before the model is built, and sometimes trial and error.

### Symmetry

When geometry, loads and supports are symmetric about one or more planes, only part of the structure need be modelled (ll. 346–375). The symmetry condition reproduces the effect of the missing half: nodes on the symmetry plane cannot move normal to it, but can move in it. In the block example a vertical symmetry plane through the middle, with $u_x=0$ on it, removes the sliding mode without over-constraint, and halves the model. A wing analysis models one wing, and a bladed disc (blisk) in an aero-engine is analysed as one sector with cyclic symmetry, so thousands of DOF replace millions; Rolls-Royce's in-house tools and ANSYS both offer this.

## 4. Yield criteria

Which combination of the six stress components causes yield? Two criteria are used in industry, both written in the principal stresses $\sigma_1$, $\sigma_2$, $\sigma_3$ (ll. 291–325; [[Von Mises and Tresca Yield Criteria]]). Tresca (maximum shear stress) predicts yield when

$$
\max\left(|\sigma_1-\sigma_2|,\ |\sigma_2-\sigma_3|,\ |\sigma_3-\sigma_1|\right)=\sigma_Y,
$$

and von Mises (distortion energy) when

$$
\sigma_e=\sqrt{\tfrac12\left[(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2\right]}=\sigma_Y .
$$

Tresca is usually regarded as conservative compared with tests, though there is very limited multiaxial test evidence; von Mises is thought to predict yield more accurately but is not always conservative. Von Mises is the usual choice in practice and is what the lab beam's equivalent stress plot shows. ANSYS calls the Tresca quantity the stress intensity, $SI=2\tau_{max}$.

Because the analysis is linear, stress is proportional to load, and the load that causes first yield follows from one run:

$$
P_Y=P\,\frac{\sigma_Y}{\sigma_{max}} .
$$

In service the load is kept well below $P_Y$ by a safety factor that covers manufacturing variation and scatter in material properties (ll. 311–320).

## Worked example: nozzle yield pressure and the two criteria

The lecture's nozzle intersection has $\sigma_Y=340$ MPa and is analysed at $P=2.5$ MPa (ll. 306–325).

With von Mises, the maximum equivalent stress is $\sigma_{e,max}=238.6$ MPa, so

$$
P_Y=2.5\times\frac{340}{238.6}=3.56\text{ MPa}.
$$

With Tresca, the maximum stress intensity is $SI_{max}=256.1$ MPa, so

$$
P_Y=2.5\times\frac{340}{256.1}=3.32\text{ MPa},
$$

lower, so Tresca is the conservative choice here. With a safety factor of 1.5 on the von Mises result, the allowable working pressure would be $3.56/1.5=2.37$ MPa.

> [!warning] Slide slip (Lecture 4, slide 18; 2026-02-06 11:01, l. 319)
> The slide and the lecture give the Tresca yield pressure as 3.20 MPa; $2.5\times340/256.1=3.32$ MPa.

Why is Tresca the more conservative? For a plane-stress state $\sigma_1=200$ MPa, $\sigma_2=100$ MPa, $\sigma_3=0$, Tresca gives the largest difference, 200 MPa, while von Mises gives $\sqrt{\tfrac12(100^2+100^2+200^2)}=173.2$ MPa. For pure shear, $\sigma_1=150$, $\sigma_2=-150$, $\sigma_3=0$, the two give 300 and 259.8 MPa. The Tresca stress always lies between 1 and $2/\sqrt3\approx1.155$ times the von Mises stress, so it predicts yield at an equal or lower load (values checked in Python).

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]
- Next: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- Concepts: [[Boundary Conditions and Rigid Body Modes]] · [[Von Mises and Tresca Yield Criteria]] · [[Stress Concentration Factor and Factor of Safety]] · [[Mesh Convergence and Grid Independence]]
- Meshing and units in practice: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- The whole workflow in APDL: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]

## Sources

- FEA Lecture 4 slides, `Lecture_4_Linear_elastic_FEA_Final_2.pdf` (stress values read from the slide contour legends), with transcript `SESA2029 Lecture 2026-02-06 - 1101.txt` (Dr J. Yuan)
- Worked example recomputed in Python

## Self-study tasks

### Core

- [ ] State the two assumptions of linear elastic FEA and when linear analysis is not sufficient (2026-02-06 11:01, ll. 1–95). → [[#1. The two assumptions and their limits]]
- [ ] Explain the block-on-a-surface constraint problem and the correct supports (ll. 331–350). → [[#3. Rigid-body motion and over-constraint]]
- [ ] Compute the yield pressure by von Mises and Tresca for the nozzle (ll. 306–325). → [[#Worked example: nozzle yield pressure and the two criteria]]
- [ ] Finish lab 1 and the second example-sheet question ("please independently for a second example", ll. 371–380). → [[SESA2029 FEA Worked Examples]]

### Further practice

- [ ] Lab 2: refine the mesh round the hole and see how the peak stress changes (ll. 286–295). → [[#The answer is approximate]] · [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]
- [ ] Show that the Tresca stress is between 1 and $2/\sqrt3$ times the von Mises stress (suggested, not lecturer-set). → [[#Worked example: nozzle yield pressure and the two criteria]]

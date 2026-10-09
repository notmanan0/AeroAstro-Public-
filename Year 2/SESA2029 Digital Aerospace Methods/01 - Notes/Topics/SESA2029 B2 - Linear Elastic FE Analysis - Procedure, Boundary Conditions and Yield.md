---
title: "SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 13
tags:
  - sesa2029
  - fea
  - linear-elastic
  - yield
aliases: ["Linear elastic FEA", "FE procedure", "Yield criteria in FEA"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]"]
next_topics: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]"]
key_concepts: ["[[Boundary Conditions and Rigid Body Modes]]", "[[Von Mises and Tresca Yield Criteria]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield

> [!abstract] Summary
> **Linear elastic FEA** assumes (i) a **linear elastic material** (no yield, creep or cracking) and (ii) **small deformations**, so the stiffness matrix does not change as the structure deforms. It covers most design analysis, with three caveats: it cannot predict **buckling** or **plasticity**, although it does give the **load at first yield**.
>
> **Workflow**: pre-process (geometry, material, mesh, BCs) → solve (automatic) → post-process (deformed shape, contour plots).
>
> **Boundary conditions**:
> - must suppress all 6 **rigid-body modes** (3D);
> - must not **over-constrain** the model, which creates spurious local stresses;
> - can exploit **symmetry** to shrink the model.
>
> **Yield checks** use von Mises (accurate, usual) or Tresca (conservative). In a linear analysis the yield load **scales proportionally** from a single run.

## Key Concepts
- [[Boundary Conditions and Rigid Body Modes]] · [[Von Mises and Tresca Yield Criteria]] · [[Stress Concentration Factor and Factor of Safety]] · [[Mesh Convergence and Grid Independence]]

---

## 1. Assumptions and scope (L4)
| Assumption | Meaning | Breaks down when |
|---|---|---|
| Linear elastic material | $\sigma = E\varepsilon$; properties don't change (no yield, creep, crack growth); stress below yield or fracture stress | plasticity, composites and rubbers, high temperature |
| Small-deformation theory | the deformation does not change the structural response, so $[K]$ is constant | large deflection of light, flexible wings (e.g. B787-class), follower loads |

**Is linear FEA the right tool?**
- **Early in design**: hand sizing (beams, cylinders, spheres) is often better.
- **Buckling**: small-deformation FEA **does not pick it up**. Thin skins are split into panels between stiffeners precisely to avoid buckling. If buckling is a possible failure mode, run a buckling analysis.
- **Plasticity**: linear FEA does not model it, but it does tell you the load at **first yield**.

Nonlinear analysis comes later in design and costs 10–100× more ([[SESA2029 B9 - Nonlinear FE Analysis]]).

## 2. Procedure (L4)
1. **Pre-processing**:
   - **Geometry**: created in the FE program or imported from CAD (e.g. SolidWorks, CATIA). In FE terms, geometry points are *key points* and mesh points are *nodes*.
   - **Material**: $E$ and $\nu$, plus density $\rho$ for modal or mass work. Material choice is driven by cost, manufacturability, performance and availability.
   - **Discretisation (meshing)**: e.g. 10-node tetrahedra, which mesh irregular shapes easily ([[Solid Elements (Tetrahedra and Hexahedra)]]).
   - **Boundary conditions**: supports (prescribed displacements) and loads (forces or pressures).
2. **Solution**: build $[K]$, solve for the nodal displacements, then compute strain and stress. For linear analysis this step is fully automatic.
3. **Post-processing**:
   - deformed-shape plots (automatically **scaled** to be visible);
   - displacement contours;
   - stress contours: 3 normal, 3 shear, 3 principal, or derived stresses such as **von Mises**.

   Exporting results to Python or Excel is often more flexible than the GUI.

> [!warning] Units must be consistent
> FE software has no unit system; it just multiplies numbers. Common consistent sets:
> - **SI**: m, N, Pa, kg/m³;
> - **mm-N-MPa**: mm, N, MPa, and **tonne/mm³** for density.
>
> Mixing geometry in mm with $E$ in Pa is a classic user error ([[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]).

**The FE answer is approximate.** A finer mesh gives a better approximation, especially near stress raisers. Use a **graded mesh**: fine where stress gradients are high, coarse elsewhere. In one lecture example the peak stress rose from 319 MPa (coarse) to 470 MPa (refined): **a mesh convergence study is mandatory** for stress results.

## 3. Rigid-body motion and constraint (L4)
- A 3D body has **6 rigid-body modes**: 3 translations and 3 rotations. In 2D there are 3.
- If any mode is unconstrained, the body can move without straining, $[K]$ is singular, and the solver fails.
- Applying enough supports without **over-constraining** is not trivial.

**Block-on-a-surface example (2D, pressure on top)**:
- Fixing only $u_y$ on the bottom nodes stops translation in $y$ and rotation about $z$. It does **not** stop sliding in $x$: rigid-body motion remains.
- Fixing both $u_x$ and $u_y$ on the bottom nodes stops the rigid-body motion, but it is **over-constrained**. The bottom cannot expand laterally as the block is squashed (Poisson effect), so you get spurious high corner stresses instead of the expected uniform stress.
- **Correct**: fix $u_y$ along the bottom and $u_x$ at **one** point (or on a symmetry line).

**Symmetry BCs**. If geometry, loads and supports are symmetric about a plane:
- model **half** (or a quarter, or one **sector**);
- set the normal displacement on the symmetry plane to zero. In-plane displacement stays free, and the rotations about in-plane axes are zero (for beams and shells).

This both shrinks the model and removes rigid-body modes without over-constraint. Examples: one half-wing instead of two; one fan-blade sector with **cyclic symmetry** instead of 360°.

See [[Boundary Conditions and Rigid Body Modes]].

**Loads**:
- apply them **directly** as nodal forces or element pressures;
- or **indirectly** on geometry (areas, lines), and the program transfers them to the mesh.

Scripting allows arbitrary load functions, such as a CFD pressure map mapped onto a wing. Full aeroelastic coupling iterates: structure deforms → new CFD boundary → new loads.

## 4. Yield criteria (L4)
For principal stresses $\sigma_1,\sigma_2,\sigma_3$:

$$
\text{Tresca: }\max\left(|\sigma_1-\sigma_2|,|\sigma_2-\sigma_3|,|\sigma_3-\sigma_1|\right) = \sigma_Y,\qquad\text{von Mises: }\frac{1}{\sqrt2}\sqrt{(\sigma_1-\sigma_2)^2+(\sigma_2-\sigma_3)^2+(\sigma_3-\sigma_1)^2} = \sigma_Y
$$

- **Tresca** (max shear) is usually **conservative** compared with tests. The multiaxial evidence is limited.
- **von Mises** (distortion energy) is generally more **accurate**, but not always conservative. It is the industry default and the usual contour plotted (`S,EQV` in APDL). The "stress intensity" in ANSYS is the Tresca measure, $2\tau_{max}$.

See [[Von Mises and Tresca Yield Criteria]].

**Yield load from one elastic run.** In a linear analysis, stress ∝ load, so

$$
P_Y = P\,\frac{\sigma_Y}{\sigma_{e,max}}
$$

> [!example] Nozzle intersection (L4)
> Take $\sigma_Y = 340$ MPa and an applied pressure $P = 2.5$ MPa.
> - von Mises: $\sigma_{e,max} = 238.6$ MPa, so $P_Y = 2.5\times340/238.6 = \mathbf{3.56}$ **MPa**.
> - Tresca: stress intensity $SI_{max} = 256.1$ MPa, so $P_Y = 2.5\times340/256.1 = \mathbf{3.32}$ **MPa**, which is lower and therefore conservative.
>
> ⚠ The slide prints 3.20 MPa for the Tresca case; the arithmetic gives 3.32 MPa.
>
> A safety factor (typically 1.5–2 on yield) is then applied, to cover manufacturing variation and material scatter.

## 5. Stress concentrations (L4–L5)
Sharp geometry changes (holes, fillets, steps) amplify stress locally. The peak usually sits at the discontinuity, so designers add **fillet radii**. Quantified by $K_t = \sigma_{max}/\sigma_{bulk}$ ([[Stress Concentration Factor and Factor of Safety]]). A **sharp** re-entrant corner has theoretically infinite stress: a singularity ([[Stress Singularities]]).

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] · Next: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- APDL implementation of the whole workflow: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]

## Sources
- FEA Lecture 4, `02 - Sources/FEM Lectures/Lecture_4_Linear_elastic_FEA_Final_2.pdf`; transcript `FEA.txt`

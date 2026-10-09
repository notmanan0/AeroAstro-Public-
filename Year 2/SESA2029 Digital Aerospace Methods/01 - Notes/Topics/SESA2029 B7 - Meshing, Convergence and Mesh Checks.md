---
title: "SESA2029 B7 - Meshing, Convergence and Mesh Checks"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 18
tags:
  - sesa2029
  - fea
  - meshing
  - convergence
aliases: ["FE meshing", "Mesh convergence study", "Mesh refinement"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
next_topics: ["[[SESA2029 B8 - Modal Analysis]]"]
key_concepts: ["[[Mesh Convergence and Grid Independence]]", "[[Stress Singularities]]", "[[FE Element Quality Checks]]", "[[h- and p-Refinement]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B7 - Meshing, Convergence and Mesh Checks

> [!abstract] Summary
> FE results carry four kinds of error: **numerical** (precision), **discretisation** (mesh), **modelling** (assumptions) and **user** (units, missing supports).
>
> A **meshing plan** has three steps:
> 1. Choose the element **category and order** to suit the physics.
> 2. Choose the **density** to suit the quantity wanted. Loads need the coarsest mesh, stress the finest, displacement sits between.
> 3. **Refine** (global h, local h, p) until the result converges, then **check quality** (aspect ratio, angles, warping).
>
> Peak stresses at **singularities** (sharp re-entrant corners, point loads or constraints) **never converge**: they grow as the mesh is refined. Converge on stresses *away* from the singularity, or remove it with fillets and distributed loads.

## Key Concepts
- [[Mesh Convergence and Grid Independence]] · [[Stress Singularities]] · [[FE Element Quality Checks]] · [[h- and p-Refinement]]

---

## 1. Errors in FE analysis (L9)
| Error | Example | Mitigation |
|---|---|---|
| **Numerical** | limited significant digits. Exporting $[K]$ with 8 rather than 16 digits gave wrong eigenvalues in an external eigen-solve | double precision; export full precision; sensible units (m vs mm changes the magnitudes) |
| **Discretisation** | piecewise-polynomial approximation of the displacement field | convergence study; element order |
| **Modelling** | assumptions of the element or maths model: beam theory on a low-aspect-ratio part; plane sections | choose elements that match the physics |
| **User** | forgotten supports, BCs in the wrong direction, mixed units (mm geometry with Pa material) | verification checks ([[SESA2029 B10 - FE Verification, Validation and Model Updating]]) |

## 2. Meshing plan: element type (L9)
**What do you want?** Displacement, strain, stress, natural frequency or mode shapes. Each needs a different density.

**Which dimension?**
- 1D: beams for slender members; very fast for parametric studies.
- 2D: plane stress/strain or shells.
- 3D: only if the through-thickness stress matters.

**Choose elements that capture every significant stress** the loading, geometry and BCs can produce:
- a slender beam → beam elements;
- a thick beam (shear significant) → quadrilateral plane stress/strain elements.

An element type that is best for one problem may not be for another.

**Mixing element types** is legitimate when physics allows. Example: a rotor model uses beam elements for the slender shaft and spring elements for the bearings, instead of a nonlinear 3D solid that could not be solved.

**Order**: at equal density, quadratic PLANE183 gave 100% of the target stress where linear PLANE182 gave 96–98% (see [[SESA2029 B6 - 2D and 3D Elements]]).

## 3. Mesh density by purpose (L9)
| Model type | Extracts | Density |
|---|---|---|
| **Load model** (global FEM) | internal and free-body loads, stiffness | coarse: loads are insensitive to mesh |
| **Displacement model** (intermediate) | deflections (and dynamics: velocities) | intermediate |
| **Stress model** (detailed FEM) | peak stresses in high gradients | fine: many shell or solid elements locally |

Modal analysis (frequencies and mode shapes) usually needs a much **coarser** mesh than stress analysis.

## 4. Refinement strategies (L9)
- **Global size reduction** (h-refinement everywhere): simple, but it wastes DOF far from the region of interest.
- **Local refinement**: refine near known stress raisers (select lines or areas and set a finer size). It must be **gradual**: adjacent elements of similar size, never a millimetre cell next to a metre cell.
- **Higher element order** (p-refinement).
- **Manual adjustment**, or **automatic adaptive refinement** in some codes (e.g. COMSOL).

**Cost**: solution time grows roughly with (number of DOF)².

**Choosing sizes: a procedure**:
1. Predict the behaviour. Where are the maximum deflection and the curvature changes?
2. Mesh finer in high-gradient regions and coarser elsewhere, checking quality.
3. Run a simple load case. If nonlinearity is expected, use a smaller load or apply it incrementally.
4. Plot the deflected shape (and mode shapes for modal or buckling runs) to spot critical areas.
5. Verify against hand calculations, then refine.

## 5. Mesh convergence (L9)
Run the analysis on successively refined meshes. The result is **converged** when further refinement changes it negligibly. For peak stress this is essential, because coarse meshes miss the gradient. **Define the peak stress location carefully**: it can move between meshes.

**Stress singularities.** At a sharp re-entrant corner, a crack tip, or a point load or constraint ($\sigma = F/A$ with $A\to0$), elasticity predicts **infinite** stress. Refining the mesh makes the peak **keep rising** instead of flattening. A frequent sign is "stress increases as I decrease the mesh size" at a sharp wing root or trailing edge.

> [!example] L-shaped plate: own Q4 plane-stress solver (see `scripts/make_figures.py`)
> An L-plate is clamped on its left edge, with a tip shear on the lower arm. The mesh is refined 4 → 128 elements per unit length, and the von Mises stress is normalised by its coarsest-mesh value:
>
> | $n$ | 4 | 8 | 16 | 32 | 64 | 128 |
> |---|---|---|---|---|---|---|
> | peak at the 90° re-entrant corner | 1.00 | 1.41 | 1.95 | 2.66 | 3.62 | 4.94 |
> | stress at a point away from the corner | 1.00 | 0.881 | 0.846 | 0.836 | 0.833 | 0.831 |
>
> The corner value grows by about 1.37 per halving of $h$, matching the elasticity prediction $\sigma\propto h^{-0.456}$ for a 270° wedge. The remote value converges.

![[dam_mesh_convergence_singularity.png|620]]

**Dealing with singularities**: see [[Stress Singularities]] and [[SESA2029 B10 - FE Verification, Validation and Model Updating]].
- Spread forces or constraints over an area or line instead of a single node.
- Add **fillets** to sharp corners, as real parts have.
- Judge convergence at a location **away** from the singularity.
- Model contact properly instead of over-constraining.

## 6. Element quality checks (L9)
- **Aspect ratio** = longest / shortest dimension. For good accuracy keep $b/h\lesssim2$–4 in 2D stress regions. Solids: ≤ 3 linear, ≤ 5 quadratic.
- Bad shapes:
  - triangle-like quadrilaterals;
  - near-degenerate triangles;
  - highly skewed cells;
  - large-aspect-ratio skewed cells;
  - off-centre midside nodes;
  - curved sides.
- **Angles between element sides must not approach 0° or 180°**, or the shape-function mapping breaks down.
- In ANSYS use Meshing → Check Mesh → Individual Elements → *Plot Warning/Error Elements*. The shape-testing summary lists how many elements violate the warning limits. Warnings are not always fatal, but they compromise accuracy; errors must be fixed.
- Sharp **trailing edges** and **warped** skins are the usual offenders on wings. Switching linear → quadratic elements relaxes the aspect-ratio limit (roughly 5 → 7 in practice).

**Why refined meshes sometimes crash**:
- (i) too many DOF for memory or the licence limit;
- (ii) refinement created distorted elements (e.g. at a trailing edge) that generate an ill-conditioned or singular $[K]$.

Check the elements before solving. See [[FE Element Quality Checks]].

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B6 - 2D and 3D Elements]] · Next: [[SESA2029 B8 - Modal Analysis]]
- CFD equivalents: [[CFD Mesh Quality Metrics]] · [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Automating a convergence study in APDL: [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]

## Sources
- FEA Lecture 9, `02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf`; transcript `FEA.txt`
- Williams (1952) corner-singularity exponent: $\lambda = 0.5445$ for a 270° wedge, giving $\sigma\propto r^{\lambda-1}$

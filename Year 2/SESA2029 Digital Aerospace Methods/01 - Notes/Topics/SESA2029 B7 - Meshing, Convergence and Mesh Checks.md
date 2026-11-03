---
title: "SESA2029 B7 - Meshing, Convergence and Mesh Checks"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 18
tags: [sesa2029, fea, meshing, convergence]
aliases: ["FE meshing", "Mesh convergence study", "Mesh refinement", "FEA Lecture 9"]
date: 2026-10-30
status: lectured
coverage: "FEA week 5 (2026-02-27 09:59)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
next_topics: ["[[SESA2029 B8 - Modal Analysis]]"]
key_concepts: ["[[Mesh Convergence and Grid Independence]]", "[[Stress Singularities]]", "[[FE Element Quality Checks]]", "[[h- and p-Refinement]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_9_Meshing_2_final(1).pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-27 - 0959.txt", "Williams (1952), corner singularity exponents"]
---

# SESA2029 B7 - Meshing, Convergence and Mesh Checks

> [!abstract] Summary
> FE results carry numerical, discretisation, modelling and user errors, and the mesh controls the second. A meshing plan chooses the element category and order to suit the physics, the density to suit the quantity wanted (loads need the coarsest mesh, stresses the finest), and a refinement strategy (global, local or higher order) applied until the result converges, followed by element quality checks. Peak stresses at singularities, such as sharp re-entrant corners or point loads, never converge: they keep rising as the mesh is refined, so convergence must be judged away from them or the singularity removed.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to plan a mesh, explain a convergence study, classify FE errors, or explain why a stress keeps rising with refinement.
> - **Assumptions:** linear static analysis; a fixed location (or a tracked peak) for the convergence quantity.
> - **Method:** 1. Decide the output: loads, displacements or stresses. 2. Choose element category and order. 3. Mesh finer in high-gradient regions, gradually. 4. Refine and replot the output until it stops changing. 5. Check aspect ratios and angles; investigate any value that grows without limit.
> - **Common mistakes:** refining the whole domain when only the hole needs it; reporting a converged peak stress at a sharp corner.
> - **Practise:** [[#Worked example: a cantilever with several element types]] · [[#5. Convergence and singularities]]

With the theory done, this week turns to practice: how to choose and mesh elements, which determines both the accuracy and the cost of a model, the difference between a run of minutes and one of hours that makes a parametric study impossible (2026-02-27 09:59, ll. 1–20).

As in CFD, the computing cost rises steeply with the number of degrees of freedom, so they should go where the results of interest need them. A displacement is an average over the whole structure and settles on a coarse mesh; a peak stress is a local maximum of a steep gradient and needs many small elements just there. And some peaks are not real: at a perfectly sharp internal corner the exact elastic stress is infinite, so refining the mesh only makes the computed peak grow.

## 1. Errors in FE analysis

An FE model can do what analytical solutions cannot, but its user must know what errors it carries (ll. 21–95).

Numerical errors come from the limited number of significant digits the computer keeps and from the tolerance on the iterative solution. Units matter here too: the same structure in metres or millimetres gives numbers of very different size. Dr Yuan's own PhD example: exporting the ANSYS stiffness matrix with 8 rather than 16 digits and computing eigenvalues in MATLAB and Python gave results completely different from the analytical solution; 16 digits fixed it.

Discretisation error is the piecewise-polynomial approximation of the displacement field, set by the element type (two or three nodes, say) and the number of elements; a continuum cannot be represented exactly at finite cost.

Modelling error comes from the assumptions of the mathematical model. The beam element assumes plane sections stay plane and bend into circular arcs; for a low-aspect-ratio part those assumptions fail and a different formulation is needed, which is why the structure and its boundary conditions must be understood before choosing elements.

User errors are mistakes seen in the labs: forgotten boundary conditions, constraints in the wrong direction, and geometry in millimetres with material properties in SI units. The checks of [[SESA2029 B10 - FE Verification, Validation and Model Updating|B10]] are aimed at them.

## 2. Choosing the element

The first part of a meshing plan is the element (ll. 101–180). Decide the quantity of interest first, displacement, strain, stress, natural frequency or mode shape, since each needs a different mesh. Then decide the dimension. A spar can be modelled in 3D, but as a beam it runs fast enough for parametric studies; 2D plane elements suit thin plates, with plane stress for thin parts and plane strain for thick ones; 3D solids are needed only if the stress varies significantly through the thickness. The rule is to choose an element type appropriate to the loading and stress conditions, one that captures every significant stress the loading, geometry and boundary conditions can produce.

An element type best for one problem may not be best for another. The slide-9 cantilever ($E=10^4$, $\nu=0.3$, $L=10$, depth 2, tip load $P=20$) has a beam-theory root stress of 300 and tip deflection 1.031, matched by a single beam element, while some plane-element meshes are far off (see the worked example). For a slender structure, beam elements are both accurate and cheap.

Element types can also be mixed when the physics allows. Dr Yuan's fan-blade and rotor project cannot be solved as a nonlinear 3D solid model because of blade-tip rub and bearing nonlinearities; the shaft is modelled with beam elements, being slender, and the bearings with spring elements constrained in some directions (ll. 151–165).

Element order matters at the same mesh density (slide 10, ll. 165–180). A tapered cantilever with target stresses of 8333 psi at mid-length and 7407 psi at the fixed end gives:

| Element | Mid-length (psi) | Ratio | Fixed end (psi) | Ratio |
|---|---|---|---|---|
| PLANE182 (4-node) | 8164 | 0.980 | 7151 | 0.965 |
| PLANE183 (8-node) | 8364 | 1.004 | 7409 | 1.000 |

The higher-order element is more accurate on the same mesh and less sensitive to distorted elements. (The lecture reads the PLANE182 fixed-end ratio as 92 %; the slide gives 96.5 %.)

## 3. Mesh density depends on the purpose

The density follows from what is to be extracted (ll. 181–200):

| Model | Extracts | Density |
|---|---|---|
| Load model | internal forces and moments, aerodynamic loads | coarsest |
| Displacement model | deflections, and velocities in dynamics | intermediate |
| Stress model | peak stresses in high gradients | finest, often with shells or solids locally |

Natural frequencies and mode shapes need only a coarse mesh compared with stress analysis, a point Dr Yuan, a dynamics specialist, emphasises.

## 4. Refinement strategies

There are four ways to refine (ll. 200–280; [[h- and p-Refinement]]). Global element size reduction (h-refinement everywhere) is the simplest, but it spends elements in the far field of the plate with a hole without improving the stress at the hole. Local refinement selects the lines or areas round a known stress raiser and sets a finer size there, as in lab 2. Raising the element order (PLANE182 to PLANE183) is p-refinement. Manual adjustment, or automatic adaptive refinement in some codes such as COMSOL, completes the list; newer commercial packages increasingly automate meshing. The methods can be combined, and refinement continues until the results change very little from one mesh to the next. The cost rises with the number of degrees of freedom.

The lecture's procedure for choosing sizes (ll. 246–265):

1. Predict how the model will behave and where the maximum deflection and changes in curvature will be.
2. Mesh finely where the stress gradient is high and the deflection changes, coarsely in less critical areas, and check the mesh quality.
3. Run a simple load case at a small fraction of the expected load, applied incrementally if nonlinear behaviour is expected.
4. Plot the deflected shape (and mode shapes, for modal or buckling analyses) to find the critical areas.
5. Verify against an analytical solution, such as beam theory, and refine.

Refinement must be gradual, with neighbouring elements of similar size: never a millimetre element next to a metre one, though most tools grade the transition automatically (ll. 266–275).

## 5. Convergence and singularities

A mesh convergence study runs the analysis on successively finer meshes; the result is converged when further refinement no longer changes it significantly (ll. 276–295; [[Mesh Convergence and Grid Independence]]). It is essential for peak stresses and strains, which a coarse mesh cannot capture. The location of the peak can move as the mesh changes, so define carefully where the stress is read, possibly at a fixed point.

Sometimes the stress does not flatten but keeps rising as elements shrink (ll. 286–305). That is a stress singularity: at a sharp re-entrant corner or a crack tip, and likewise under a point load or point constraint where $F/A$ has $A\to0$, linear elasticity predicts infinite stress, and refinement simply samples closer to it ([[Stress Singularities]]). The remedies are to read the stress away from the sharp feature, to add a fillet as a real part would have, and to spread forces and constraints over an area rather than a node.

The module's own figure shows the effect with a small Q4 plane-stress solver on an L-shaped plate, clamped on one edge with a shear load on the lower arm (generated by `scripts/make_figures.py`). Normalised by the coarsest mesh, refining from 4 to 128 elements per unit length gives

| Elements per unit length | 4 | 8 | 16 | 32 | 64 | 128 |
|---|---|---|---|---|---|---|
| von Mises at the 90° re-entrant corner | 1.00 | 1.41 | 1.95 | 2.66 | 3.62 | 4.94 |
| von Mises at a point away from the corner | 1.00 | 0.881 | 0.846 | 0.836 | 0.833 | 0.831 |

The corner value grows by a factor of about 1.37 each time $h$ halves, consistent with Williams' elasticity solution for a 270° wedge, $\sigma\propto r^{-0.456}$, while the remote value converges.

![[dam_mesh_convergence_singularity.png|620]]

## 6. Element quality checks

For accuracy, elements should have a low aspect ratio, below about 2 to 4 for plane elements (ll. 306–325; solids from B6: at most 3 linear, 5 quadratic). Poor shapes include quadrilaterals that are nearly triangles, highly skewed elements, large aspect ratios, curved sides and off-centre mid-side nodes. The angles between element sides must not approach 0° or 180°, otherwise the shape-function mapping breaks down and the coefficients of the interpolating polynomial cannot be found ([[FE Element Quality Checks]]).

Wings are the usual offenders: twist and a sharp trailing edge produce warnings about aspect ratio and warping. Warnings are not necessarily fatal, and the analysis can continue, but accuracy may suffer; errors must be fixed. After meshing, the mesh check reports, for example, "4 of the 183 newly modified elements violate shape warning limits", with details in the output window, and plotting the warning elements shows where they are (ll. 316–330).

## 7. Lab 3 briefing

The last lab models a uniform wing with an aerofoil section, in static and modal analysis, and needs only one model whose element type and thickness are changed (ll. 331–405; [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]]). The tasks are to compare four-node SHELL181 (linear, efficient for large models with mild curvature) with eight-node SHELL281 (quadratic, better for curvature, more tolerant of aspect ratio, more expensive); to assess the effect of skin thickness on the factor of safety, stress and wing weight; and to find the minimum skin thickness for the same factor of safety with a different material, and its effect on weight. The aerofoil file is in SI units, unlike the millimetre units of labs 1 and 2, so everything else must be in SI too.

For the weight, treating the skin as two rectangular plates is a rough first estimate; better, Preprocessor → Modeling → Operate → Calculate Geometry Items gives the area of the selected surfaces (and second moments of area, useful for building an equivalent beam model), which times the shell thickness and density gives the mass (ll. 366–395).

## Worked example: a cantilever with several element types

The slide-9 cantilever has $E=10^4$, $\nu=0.3$, length $L=10$, depth $h=2$ and unit thickness, with tip load $P=20$. The section properties are

$$
I=\frac{bh^3}{12}=\frac{1\times8}{12}=0.667,
\qquad
A=2,
\qquad
G=\frac{E}{2(1+\nu)}=3846 .
$$

Bending deflection:

$$
\frac{PL^3}{3EI}=\frac{20\times1000}{3\times10^4\times0.667}=1.000 .
$$

Shear deflection, with the factor $6/5$ for a rectangle:

$$
\frac65\frac{PL}{AG}=\frac{1.2\times20\times10}{2\times3846}=0.031 .
$$

So $v_C=1.031$, and the root bending stress is

$$
\sigma=\frac{Mc}{I}=\frac{20\times10\times1}{0.667}=300 .
$$

These match the slide, recomputed in Python. Against them, the FE results on the slide (Cook's textbook comparison) include a single two-node beam element, $v_C=1.031$, exact; constant-strain triangles, $v_C=0.264$, about a quarter of the true value because they are far too stiff in bending; a rectangular Q4 mesh, $v_C=0.693$; the same Q4 mesh distorted, $\sigma=190$ and $v_C=0.502$; linear-strain triangles, $\sigma=254$, $v_C=0.987$, and 250 and 0.924 when distorted; and the higher-order quadrilateral meshes, $\sigma$ of 270 to 300 and $v_C$ of 0.98 to 1.035. Low-order elements are stiff in bending and suffer badly from distortion; higher-order ones, or the right element (a beam), do not.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B6 - 2D and 3D Elements]]
- Next: [[SESA2029 B8 - Modal Analysis]]
- Concepts: [[Mesh Convergence and Grid Independence]] · [[Stress Singularities]] · [[FE Element Quality Checks]] · [[h- and p-Refinement]]
- The CFD equivalents: [[CFD Mesh Quality Metrics]] · [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Automating a convergence study: [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]

## Sources

- FEA Lecture 9 slides, `Lecture_9_Meshing_2_final(1).pdf` (cantilever comparison on slide 9, PLANE182/183 table on slide 10), with transcript `SESA2029 Lecture 2026-02-27 - 0959.txt` (Dr J. Yuan)
- Williams (1952) for the corner-singularity exponent ($\lambda=0.5445$ for a 270° wedge, $\sigma\propto r^{\lambda-1}$)
- Beam-theory numbers recomputed in Python; the L-plate table from the module's `scripts/make_figures.py`

## Self-study tasks

### Core

- [ ] Name the four sources of FE error with an example of each (2026-02-27 09:59, ll. 21–95). → [[#1. Errors in FE analysis]]
- [ ] Explain how mesh density depends on whether loads, displacements or stresses are wanted (ll. 181–200). → [[#3. Mesh density depends on the purpose]]
- [ ] Explain why a stress can keep rising under refinement and what to do about it (ll. 286–305). → [[#5. Convergence and singularities]]
- [ ] Lab 3: compare SHELL181 and SHELL281, the effect of thickness and of material on factor of safety and weight (ll. 341–405). → [[#7. Lab 3 briefing]] · [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]

### Further practice

- [ ] Recompute the slide-9 beam-theory deflection and stress, then compare each FE result as a percentage error. → [[#Worked example: a cantilever with several element types]]
- [ ] Revisit your lab 2 convergence study: was the refinement local, and did the peak move? (suggested, not lecturer-set) → [[#4. Refinement strategies]]

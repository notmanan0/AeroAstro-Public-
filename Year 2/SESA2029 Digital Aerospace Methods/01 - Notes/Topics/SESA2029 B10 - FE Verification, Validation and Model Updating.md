---
title: "SESA2029 B10 - FE Verification, Validation and Model Updating"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 21
tags: [sesa2029, fea, validation, model-updating]
aliases: ["FE V&V", "FE model checks", "Model updating", "FEA Lecture 12"]
date: 2026-10-30
status: lectured
coverage: "FEA week 6 (2026-03-06 10:55)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
next_topics: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]"]
key_concepts: ["[[Verification and Validation]]", "[[FE Model Verification Checks]]", "[[Stress Singularities]]", "[[Model Updating]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-03-06 - 1055.txt"]
---

# SESA2029 B10 - FE Verification, Validation and Model Updating

> [!abstract] Summary
> Verification asks whether the FE analysis was carried out correctly (units, elements, mesh, boundary conditions, hand checks); validation asks whether its predictions reflect reality, by comparison with tests under the same loads and boundary conditions. The lecture's three steps are accuracy checks on the model, checks of its mathematical soundness (a free–free modal analysis should give exactly six rigid-body modes; unit displacement, unit gravity and thermal checks), and correlation with experiments, closing any gap by deterministic or stochastic model updating. Certification needs validated methods: an unvalidated model is of no use in design.

> [!summary]- Exam use: quick path
> - **Use it when:** asked to distinguish verification from validation, list model checks, or explain model updating.
> - **Assumptions:** a linear model for the soundness checks; test data under matching loads and boundary conditions for validation.
> - **Method:** 1. Check units, dimensions, elements, materials and orientations, mesh, normals, coincident nodes. 2. Free–free modal: six zero-frequency modes, no more. 3. Unit enforced displacement: rigid motion with zero element forces; unit gravity: smooth response, reactions equal the weight. 4. Compare frequencies (within about 5 %) and mode shapes (MAC above about 0.8) with test. 5. Update the most sensitive parameters, or their distributions.
> - **Common mistakes:** calling a mesh convergence study "validation"; trusting a beam model for stresses at a sharp change of section.
> - **Practise:** [[#Worked example: what the free–free check sees]]

The final FEA lecture covers what makes a model usable (2026-03-06 10:55, ll. 1–10). Every method used to design an aircraft or engine must itself be certified before the aircraft can be, so verification and validation are central to FE in aerospace.

Verification asks whether the model was built correctly: right units, right element, right supports, a mesh fine enough. Validation asks whether the model describes the real object at all. A verified model can still be wrong about reality, and agreement with a test can hide compensating mistakes, so both are needed, and each is checked in its own way.

## 1. Verification and validation

Verification ensures the FE analysis is executed correctly: the right units, a good mesh, the right method and elements to reflect the physical system (ll. 11–20). It examines the deformed shape, the deformation values (against analytical solutions where possible), the reaction forces and the stress levels, and includes hand calculations. Validation ascertains whether the simulation results are a true reflection of the real world, by comparing the verified model with experiments under identical or similar loads and boundary conditions, then iterating and refining the model (ll. 16–40). The refinement, model updating, adjusts the geometry for manufacturing tolerances, the material properties within their range (aluminium's $E$ may be anywhere from 65 to 75 GPa), and the boundary conditions and loads, which in aerospace are often uncertain and unsteady, as gusts are ([[Verification and Validation]]).

The lecture's procedure has three steps (ll. 36–50): verification of accuracy, the checks that the model correctly represents the physical system; validation of mathematical soundness, the checks that the model is mathematically well formed and its elements' assumptions represent the real deformation; and physical validation against experiment.

## 2. Step 1: verification of accuracy

The checklist (ll. 51–70) covers dimensions, element properties and above all units, the most common source of error; proper element use; mesh quality; material properties, including the orthotropic constants $E_1$, $E_2$ of composites, and material orientation, since fibres in an aircraft skin are aligned with the load paths; free edges and faces, and coincident nodes and elements, which ANSYS can find; the local coordinate systems used for loads and constraints; beam orientation and offsets; and the total mass.

Formulation errors come from elements whose assumptions do not match the behaviour (ll. 66–95). A plane element only deforms in its plane, while a shell also bends and twists. If the stress varies linearly over a cross-section, four-node elements can capture it; if it varies nonlinearly, eight-node (Q8) elements are needed. Beam elements assume a slender, high-aspect-ratio member; for a low aspect ratio, use shells or plane elements. A beam element also assumes the load acts through the shear centre; if it does not, the section twists as it bends, and since the shear centre of an aerofoil is hard to locate, shells, which can take loads anywhere, may be the better choice.

Over-simplification is the opposite risk (ll. 96–125). Suppressing small details saves time and can avoid artificial singularities, but a detail on the load path can strongly affect the stresses and must stay. So must a detail whose removal would significantly shift the neutral axis of bending and so change the bending stiffness; a very rigid attachment can be represented as a mass with an offset rather than modelled in detail. Whether a simplification is acceptable depends on the output: asked whether a beam model of an airship is reasonable, most of the class said no, and for stresses at its sharp changes of section they were right, but for natural frequencies and mode shapes a slender airship modelled as beams with varying section properties is fine.

Singularities, where the stress cannot converge, come from point loads and point constraints, sharp corners and edges, over-constraint from improper boundary conditions, and contact with sharp edges (ll. 126–155; [[Stress Singularities]]). Mitigate them by spreading forces and displacements over an area and constraints over a line or area, adding fillets, reading results away from the singularity, and modelling contact properly; the L-shaped plate of [[SESA2029 B7 - Meshing, Convergence and Mesh Checks|B7]] is the example.

The software also offers computer-aided checks (ll. 151–185; [[FE Element Quality Checks]]). Coincident nodes, more than one node at a point, should be merged, with redundant key points removed after modelling and before meshing. Coincident elements appear when an area is meshed twice. Wrong connections arise especially when mixing element types: the displacement must be continuous within and across element boundaries, and where it is not, strains blow up between elements, the potential energy gains a spurious contribution, and gaps or cracks open when the model is loaded. Element distortion, from aspect ratio and warping, is common with shells at a sharp trailing edge; a four-node shell might be valid only for aspect ratios below about 5 where the eight-node version tolerates about 7, so raising the order is a remedy.

## 3. Step 2: mathematical soundness

Four checks confirm that the model is mathematically sound (ll. 186–225; [[FE Model Verification Checks]]):

| Check | Procedure | Pass criterion | Detects |
|---|---|---|---|
| Free–free modal | modal analysis with no constraints | exactly six modes at zero frequency (three translations, three rotations), then the flexible modes | parts not properly connected |
| Unit enforced displacement | move the model one unit along each axis and rotate it one radian about each, one at a time | it moves as a rigid body, with zero element and grid-point forces | illegal grounding by wrong single- or multi-point constraints |
| Unit gravity | three load cases of 1 g in $x$, $y$ and $z$ | smooth, sensible displacements | loosely connected nodes: DOF with tiny stiffness from bad spring elements, constraint equations or boundary conditions |
| Thermal equilibrium | uniform temperature change, unconstrained | free expansion without stress | spurious constraints |

The free–free check is the easiest and the most effective. If an engine is not properly attached to the wing, it shows up immediately: twelve rigid-body modes, six for the airframe and six for the loose engine, instead of six. On the slide's wing, a free–free modal solve over 0–200 Hz gives modes 1 to 6 at 0, 0, $3.5\times10^{-4}$, $4.6\times10^{-4}$, $7.4\times10^{-4}$ and $8.9\times10^{-4}$ Hz, numerically zero, so the model is one connected body. The APDL versions of these checks are in [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks|C6]].

> [!warning] Lecture slip (2026-03-06 10:55, ll. 206–215)
> The unit enforced displacement check is introduced as "a verification process [that] ensures the model only exhibits six rigid body modes", which describes the free–free check. Its purpose, as the next sentence says, is to find illegal grounding: under a rigid translation or rotation, no element should carry force.

## 4. Step 3: correlation with tests and model updating

"All models are wrong, but some are useful", and the useful ones are experimentally validated: validation tells you over what range of loads, frequencies and amplitudes the model can be trusted (ll. 221–235). Evidence is built up a test pyramid, from coupon tests and structural details through components, panels and large-scale assemblies to full-scale tests, and the material properties in the model must be supported by material tests too.

Models and tests disagree because material properties are uncertain (suppliers quote ranges, which depend on heat treatment and environment), boundary conditions are simplified (critical in dynamics), joints are idealised, damping is assumed, and experiments have noise (ll. 236–250). Model updating, or calibration, adjusts parameters such as Young's modulus and density until the predictions match the measurements ([[Model Updating]]). For dynamics in aerospace, the target is natural frequencies within about 5 % and mode shapes with a modal assurance criterion (MAC) above about 0.8 (ll. 251–260).

Deterministic updating finds single best values (ll. 256–280). Direct optimisation treats the problem as a nonlinear optimisation over the FE parameters with a flexible objective, such as matching deformations, but it is very expensive because every evaluation is a full FE run. Sensitivity-based updating replaces the model by a first-order Taylor expansion, a kind of surrogate, ranks the parameters (say twenty of them) by how sensitive the discrepancy is to each, and adjusts the most sensitive. It is efficient and physically interpretable for small calibrations.

Stochastic updating, increasingly used, treats the parameters as random variables (or imprecise probabilities), for example a normally distributed Young's modulus, and matches the distribution of the predictions to the distribution of the measurements (ll. 281–320). The experimental data shrink the uncertainty space, and forward uncertainty quantification gives parameter distributions and confidence levels. In Dr Yuan's example with a PhD student, the two stiffness parameters of a structure in limit-cycle oscillation, one linear and one nonlinear, were identified this way, and the mean predicted response, with its confidence band, captured the test points. Methods include Bayesian sampling, approximate inference and deep generative probabilistic models. Run backwards, the same process identifies damage, for structural health monitoring and digital twins ([[Digital Twin and Digital Thread]]). Model validation is the next step after modelling in any Airbus or Rolls-Royce FE internship.

## 5. The FEA part of the exam

The mock paper is on Blackboard, and a revision lecture in May covers it (ll. 331–365). The one-hour exam has eight questions in Section A (CFD) and eight in Section B (FEA), about 30 minutes each. The FEA questions include explanations of terms, such as interpolation and shape functions or typical nonlinearities in FEA, and calculations from the theory weeks: the matrix displacement method and minimum potential energy derivations, sketching boundary conditions and the related calculations. General formulae and element matrices are given at the end of the paper, so they need not be memorised. The coursework deadline was 16 March.

## Worked example: what the free–free check sees

Not from the lecture: a one-dimensional version shows why the free–free check counts connections. Take the stepped bar of [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method|B1]] with $k_1=2$ and $k_2=1$ (units of $AE/L$) and lumped masses 0.5, 1 and 0.5 at the three nodes, with no supports. In 1D there is one rigid-body mode, a translation. Solving $([K]-\omega^2[M])\{\phi\}=0$ with SciPy gives

$$
\omega^2=0,\ 2.44,\ 6.56,
$$

one zero, so the bar is one connected body. The unit enforced displacement check gives the same message from the other side: for $\{d\}=\{1\ 1\ 1\}^T$,

$$
[K]\{d\}=\begin{Bmatrix}2-2\\-2+3-1\\-1+1\end{Bmatrix}=\begin{Bmatrix}0\\0\\0\end{Bmatrix},
$$

no forces under rigid motion, so nothing is grounded. Now make the classic error: mesh the two bars separately so that they have four nodes and do not share node 2. The free–free solve gives $\omega^2=0,\ 0,\ 4,\ 8$: two zero modes, one per disconnected piece, exactly as the loose engine gives twelve modes instead of six.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B9 - Nonlinear FE Analysis]]
- Next: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]
- Concepts: [[Verification and Validation]] · [[FE Model Verification Checks]] · [[Stress Singularities]] · [[Model Updating]]
- The CFD counterpart: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Calibrated models in operation: [[Digital Twin and Digital Thread]]

## Sources

- FEA Lecture 12 slides, `Lecture_12_Validation and Verification_final(1).pdf` (free–free wing frequencies; stochastic updating example after McGurk et al., *AIAA J.* 2024), with transcript `SESA2029 Lecture 2026-03-06 - 1055.txt` (Dr J. Yuan)
- Worked example computed with SciPy

## Self-study tasks

### Core

- [ ] Define verification and validation and give checks for each (2026-03-06 10:55, ll. 11–50). → [[#1. Verification and validation]]
- [ ] Describe the four mathematical-soundness checks and what each detects (ll. 186–225, "probably you need to be aware of this, it's quite important", ll. 321–330). → [[#3. Step 2: mathematical soundness]]
- [ ] Explain when a simplified (beam) model is acceptable, using the airship (ll. 111–125). → [[#2. Step 1: verification of accuracy]]
- [ ] Attempt the FEA half of the mock paper (ll. 331–360). → [[SESA2029 FEA Worked Examples]]

### Further practice

- [ ] Run a free–free modal check on your lab 3 wing in APDL. → [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]
- [ ] Explain the difference between deterministic and stochastic model updating (ll. 256–320). → [[#4. Step 3: correlation with tests and model updating]]

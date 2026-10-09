---
title: "SESA2029 B10 - FE Verification, Validation and Model Updating"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 21
tags:
  - sesa2029
  - fea
  - validation
  - model-updating
aliases: ["FE V&V", "FE model checks", "Model updating"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
next_topics: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]"]
key_concepts: ["[[Verification and Validation]]", "[[FE Model Verification Checks]]", "[[Stress Singularities]]", "[[Model Updating]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B10 - FE Verification, Validation and Model Updating

> [!abstract] Summary
> - **Verification**: was the FEA executed correctly? Check deformed shapes, magnitudes, reactions, stress levels and hand calculations.
> - **Validation**: do the results reflect reality? Compare with experiments under the same loads and BCs, then refine.
>
> Three steps:
> 1. **Verification of accuracy**: dimensions, units, element choice, mesh quality, materials and orientation, free edges, coincident nodes, shell normals, beam orientation and offsets, mass, formulation errors, over-simplification, singularities.
> 2. **Mathematical soundness**:
>    - **free–free modal** (exactly 6 near-zero rigid-body modes);
>    - **unit enforced displacement**;
>    - **unit gravity**;
>    - thermal equilibrium checks.
> 3. **Correlation with tests**, closing the gap by **model updating**:
>    - deterministic: direct optimisation or sensitivity-based;
>    - **stochastic**: Bayesian and other uncertainty methods.
>
> Certification requires every analysis method to be validated. An unvalidated model is of no use to design.

## Key Concepts
- [[Verification and Validation]] · [[FE Model Verification Checks]] · [[Stress Singularities]] · [[Model Updating]]

---

## 1. Verification vs validation (L12)
| | Verification | Validation |
|---|---|---|
| Question | was the FE analysis executed correctly? | are the predictions a true reflection of reality? |
| Checks | deformed shape; deformation values; reaction forces (sum = applied loads); stress levels; **hand calculations** | experiments under identical or similar loading and BCs; iterate and refine geometry, mesh, material properties, BCs and loads |
| Outcome | a correct numerical model | a trusted, calibrated model with a known range of validity |

"All models are wrong, but some are useful": validation tells you **over what range** (loads, frequencies, amplitudes) the model is useful.

## 2. Step 1: verification of accuracy (L12)
**Checklist**:
- dimensions, element properties and **units**;
- proper element use;
- 2D/3D mesh quality;
- material properties and **material orientation** (composite fibre directions follow the load paths);
- **free edges and faces**, which reveal unintended gaps;
- **coincident nodes and elements** (merge unintended duplicates, but keep intentional ones such as spring connections);
- local coordinate systems used for loads and constraints;
- **consistent shell normals**;
- beam orientation and **offsets**;
- total **mass**.

**Formulation errors**: you must understand how the structure behaves and what each element can represent.
- If stress varies **linearly**, 4-node Q4 elements can capture it. If it varies **quadratically**, use Q8.
- Check the beam theory. Is $\sigma = My/I$ valid for wide flanges?
- If the load does not act through the **shear centre**, an open section (e.g. a channel) **twists**. A simple beam element assumes shear-centre loading, so use shells, or beams with offsets.

**Over-simplification**:
- Removing small details saves time, but details on the **load path** or near a **sharp discontinuity** can change the stresses a lot.
- Keep details whose removal would significantly change the **neutral axis** of bending: a shorter neutral axis means a stiffer structure.
- Very stiff attachments can be modelled as lumped masses with offsets.
- Whether a simplified model is acceptable depends on the output. A beam-stick model of an airship is fine for **frequencies and mode shapes**, but useless for **stress** at a shape change.

**Singularities**. Sources:
- point loads and point constraints;
- sharp corners and edges;
- over-constraint from improper BCs;
- contact with sharp corners.

How to avoid them:
- apply forces or displacements over an **area**, not a single node;
- distribute constraints over a line or area;
- add **fillets**;
- read results **away** from the singularity;
- model contact properly.

See [[Stress Singularities]] and the convergence evidence in [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]].

**Computer-aided accuracy checks**:
- coincident nodes (merge them after modelling and before meshing; redundant key points cause trouble);
- coincident elements (from meshing twice);
- **wrong connections**: displacements must be continuous within and across element boundaries. A discontinuity opens gaps or cracks under load and adds spurious energy;
- element distortion: aspect ratio, internal angles, **warping** (e.g. at trailing edges).

If linear elements fail the shape checks, **switch to quadratic**, which tolerates higher aspect ratios. See [[FE Element Quality Checks]].

## 3. Step 2: mathematical soundness (L12)
| Check | Procedure | Pass criterion | Detects |
|---|---|---|---|
| **Free–free modal** | modal analysis with **no constraints** | exactly **6** modes at ≈0 Hz (rigid body) before the first flexible mode | improper connections: an engine not properly attached to the wing gives 12 rigid modes (6 + 6), and the loose part moves on its own |
| **Unit enforced displacement** | translate 1 unit in $x$, $y$, $z$ and rotate 1 rad about each axis | the model moves as a rigid body, with zero element forces and zero grid-point forces | illegal grounding: wrong single-point or multi-point constraints |
| **Unit gravity** | three load cases, 1 g in $X$, $Y$ and $Z$ | sensible, smooth displacements; reactions = weight | loosely connected nodes: DOF with tiny stiffness from bad springs, MPCs or BCs |
| **Thermal equilibrium** | uniform temperature change on an unconstrained model | free expansion, zero stress | spurious constraints, mismatched materials |

> [!example] Free–free wing check (L12)
> An unconstrained wing modal solve over 0–200 Hz gives modes 1–6 at 0, 0, $3.5\times10^{-4}$, $4.6\times10^{-4}$, $7.4\times10^{-4}$ and $8.9\times10^{-4}$ Hz. These are numerically zero: 6 rigid-body modes, so the model is connected. The first *flexible* mode follows.

APDL implementations of these checks: [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]].

## 4. Step 3: correlation and model updating (L12)
Validation evidence is built up the **test pyramid**: coupon → structural detail → component → panel → large-scale → full-scale. Material properties must be backed by coupon tests too.

**Why models and tests disagree**:
- uncertain material properties (e.g. aluminium $E$ from 65 to 75 GPa);
- simplified BCs (joints are never perfectly clamped);
- idealised joints and connections;
- damping assumptions;
- experimental noise.

**Model updating (calibration)**. With the FE model $y_{sim} = M(x)$ and measurements $y_{obs} = M(x)+\varepsilon$, find the parameters $x$ (material, stiffness, BCs) such that $y_{sim}(x)\approx y_{obs}$.

Typical targets for dynamics:
- natural frequencies within about **5%**;
- mode shapes with **MAC ≳ 0.8**.

**Deterministic updating**:
- **Direct optimisation**: a nonlinear optimisation over the FE parameters. The objective is flexible and no analytical sensitivities are needed, but it is computationally **very expensive**.
- **Sensitivity-based**: a first-order Taylor linearisation, a kind of surrogate. Rank the parameters by their sensitivity to the discrepancy and adjust the most sensitive. It is efficient and interpretable for small calibrations, but struggles with strong nonlinearity and is sensitive to noise and ill-conditioning.

**Stochastic updating**:
- treat the parameters as **random variables** (or imprecise probabilities), e.g. $E\sim\mathcal N(\mu,\sigma^2)$;
- match the *distribution* of predictions to the *distribution* of measurements;
- this narrows the uncertainty space and gives **confidence intervals**.

Methods: Bayesian sampling, approximate inference, deep generative probabilistic models. Example: calibrating the stiffness and nonlinear parameters of a structure exhibiting LCO, with a confidence band enclosing the test data. The same inverse process detects **damage** for structural health monitoring and digital twins.

## 5. FEA part of the exam (L12)
- One hour covering CFD + FEA, about 30 minutes each. The FE section is about 8 short questions.
- Expect:
  - **explain** questions: interpolation and shape functions, sources of nonlinearity, V&V checks, element choice, singularities;
  - **calculations**: MDM assembly with BCs; a PMPE derivation; sketching BCs.
- **Element matrices and key formulae are provided**. Practise *using* them.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B9 - Nonlinear FE Analysis]] · Next: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]
- CFD counterpart: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Digital twins (operations use of calibrated models): [[Digital Twin and Digital Thread]]

## Sources
- FEA Lecture 12, `02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf` (stochastic updating example after McGurk et al., *AIAA J.* 2024); transcript `FEA.txt`

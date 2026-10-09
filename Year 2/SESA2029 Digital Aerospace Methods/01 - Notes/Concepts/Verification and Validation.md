---
title: "Verification and Validation"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Parts A & B: CFD and FEA"
aliases: ["V&V", "verification", "validation", "code verification", "method of manufactured solutions"]
tags: [sesa2029, concept, validation]
status: complete
parent_lectures: ["[[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]", "[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
related_concepts: ["[[Mesh Convergence and Grid Independence]]", "[[FE Model Verification Checks]]", "[[Model Updating]]", "[[Residual vs Solution Error]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)", "02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/CFD/CFD.txt"]
---

# Verification and Validation

## Definition

> [!note] Definition
> - **Verification** asks "are we solving the equations right?" It confirms that the code and model solve the mathematical model correctly: discretisation and iteration errors, bugs, set-up mistakes.
> - **Validation** asks "are we solving the right equations?" It compares predictions with reality (experiments) to quantify the **modelling** error.

## Explanation

- **CFD**:
  - verify with exact solutions or the **method of manufactured solutions**, grid and iteration studies, and mesh metrics;
  - validate against experiments, such as the RAE 2822 shock position. An Euler solution misplaces the shock, which is a modelling error.
- **FEA**:
  - verify the accuracy (units, elements, mesh, materials, BCs, singularities);
  - verify mathematical soundness (free–free modal, unit displacement, unit gravity);
  - then correlate with tests and **update** the model.
- Experiments carry errors and uncertain boundary conditions too, so validation often compares two imperfect methods (e.g. lifting line against Euler CFD).
- Commercial codes are closed-source, so code verification is the vendor's job. Solution verification is always yours.
- Certification demands validated methods. A model is valid only over the range of loads, frequencies and amplitudes it was validated for.

## Examples

- The CFD simulation life-cycle loops geometry → mesh → quality check → solve → V&V, returning to the solver settings or the mesh until the checks pass ([[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]).

## Related

- Parent lectures: [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]] · [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Related concepts: [[Mesh Convergence and Grid Independence]] · [[FE Model Verification Checks]] · [[Model Updating]] · [[Residual vs Solution Error]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L12)
- 02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf
- 02 - Sources/CFD/CFD.txt

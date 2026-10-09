---
title: "Sources of Nonlinearity in FEA"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["geometric nonlinearity", "material nonlinearity", "contact nonlinearity", "boundary nonlinearity", "follower force"]
tags: [sesa2029, concept, fea, nonlinear]
status: complete
parent_lectures: ["[[SESA2029 B9 - Nonlinear FE Analysis]]"]
related_concepts: ["[[Direct Substitution and Newton-Raphson]]", "[[Von Mises and Tresca Yield Criteria]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Sources of Nonlinearity in FEA

## Definition

> [!note] Definition
> A problem is **nonlinear** when the stiffness and/or the loads depend on the displacements: $[K(\{d\})]\{d\} = \{F(\{d\})\}$. There are three sources: **geometric** (large deformation), **material** (nonlinear constitutive law) and **boundary/contact** (deformation-dependent loads or constraints).

## Explanation

| Source | Origin | Examples |
|---|---|---|
| Geometric | geometry change enters equilibrium and strain–displacement; $[B]$ depends on $\{d\}$ | very flexible wings, slender structures, cables, membranes, follower pressure loads |
| Material | $\sigma(\varepsilon)$ nonlinear or history-dependent | plasticity (plastic hinge), creep (hot turbine blades), viscoelastic damping patches, rubbers |
| Force BC | loads depend on deformation | aerodynamic and hydrostatic pressure; twist changing the angle of attack |
| Displacement BC / contact | constraints depend on deformation | bolted and clamped joints (micro-slip), friction dampers, impact, blade–casing rubs |

- **Consequences**: amplitude-dependent stiffness, frequencies and mode shapes; multiple equilibria; limit-cycle oscillations (e.g. about 20% below the linear flutter speed); chaos.
- **Cost**: 10–100× a linear solve, so use linear analysis for early sizing and nonlinear analysis when fidelity demands it.
- **Physical signs**: permanent set, local yielding, buckling or crippling, necking, shear bands, temperatures near melting.

## Examples

- Plastic-hinge beam: the nonlinear run took about 3× the CPU of the linear one, and gave different displacements.
- A fishing rod behaves linearly for a small load and stiffens nonlinearly (quadratic or cubic) under a big fish.

## Related

- Parent lectures: [[SESA2029 B9 - Nonlinear FE Analysis]]
- Related concepts: [[Direct Substitution and Newton-Raphson]] · [[Von Mises and Tresca Yield Criteria]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_11_Nonlinear_FEA_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt

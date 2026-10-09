---
title: "Euler-Bernoulli Beam Element"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["beam element", "beam stiffness matrix", "Hermite beam", "2-node beam"]
tags: [sesa2029, concept, fea, beam-element]
status: complete
parent_lectures: ["[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
related_concepts: ["[[Shape Functions]]", "[[Global Stiffness Matrix Assembly]]", "[[Principle of Minimum Total Potential Energy]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Euler-Bernoulli Beam Element

## Definition

> [!note] Definition
> The 2-node bending element with DOF $(v_1,\theta_1,v_2,\theta_2)$, based on engineer's bending theory ($M/I = \sigma/y = E/R$):
> $$[K] = \frac{EI}{L^3}\begin{bmatrix}12&6L&-12&6L\\6L&4L^2&-6L&2L^2\\-12&-6L&12&-6L\\6L&2L^2&-6L&4L^2\end{bmatrix}$$

## Explanation

- **Assumptions**: plane sections remain plane and perpendicular to the neutral axis, so shear deformation is neglected. The beam must be long and slender. Stress and strain vary linearly through the depth.
- **Strain energy**: $U = \tfrac12\int EI\rho^2dx$, with curvature $\rho = v''$. The moment–curvature relation is $M = EI\rho$.
- **Cubic displacement**: 4 DOF mean 4 coefficients; the Hermite shape functions follow. $\rho = [B]\{d\}$ with $[B] = d^2[N]/dx^2$.
- PMPE gives $[K] = \int_0^L[B]^TEI[B]\,dx$, the matrix above. It is given in the exam; assemble it and apply BCs.
- With only nodal loads, the Hermite element reproduces the exact Euler–Bernoulli solution. Distributed loads need consistent nodal loads or refinement.
- Commercial BEAM188 is a **Timoshenko** element (it includes shear) with 6 DOF per node in 3D.

## Examples

- Propped cantilever ($L = 2+1$ m, $EI = 10^7$ N m², 10 kN at the tip): $\theta_2 = -5\times10^{-4}$ rad, $v_3 = -0.833$ mm, $\theta_3 = -10^{-3}$ rad.

![[dam_beam_example_deflection.png|520]]

## Related

- Parent lectures: [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Related concepts: [[Shape Functions]] · [[Global Stiffness Matrix Assembly]] · [[Principle of Minimum Total Potential Energy]]
- APDL: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_7_ FE_Beam_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt

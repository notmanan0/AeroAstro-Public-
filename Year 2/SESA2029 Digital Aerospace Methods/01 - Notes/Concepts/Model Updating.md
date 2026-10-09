---
title: "Model Updating"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["model calibration", "FE model updating", "stochastic model updating", "Bayesian updating", "sensitivity-based updating"]
tags: [sesa2029, concept, fea, validation]
status: complete
parent_lectures: ["[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
related_concepts: ["[[Verification and Validation]]", "[[FE Model Verification Checks]]", "[[Natural Frequencies and Mode Shapes]]", "[[Digital Twin and Digital Thread]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Model Updating

## Definition

> [!note] Definition
> Adjusting uncertain FE model parameters $x$ (material properties, joint stiffness, BCs) so that the simulated outputs match measurements:
>
> $$y_{sim} = M(x),\qquad y_{obs} = M(x)+\varepsilon,\qquad\text{find }x\text{ such that }y_{sim}(x)\approx y_{obs}$$

## Explanation

- **Why models disagree with tests**: uncertain properties (e.g. $E_{Al}$ from 65 to 75 GPa), simplified BCs, idealised joints, damping assumptions, experimental noise, manufacturing tolerances.
- **Typical dynamic targets**: frequencies within about 5%, mode shapes with MAC ≳ 0.8.
- **Deterministic**:
  - *direct optimisation* (flexible objective; no gradients needed; expensive);
  - *sensitivity-based* (first-order Taylor surrogate; adjust the most sensitive parameters; efficient and interpretable, but struggles with strong nonlinearity, noise and ill-conditioning).
- **Stochastic**: parameters are random variables, and you match the output *distribution* to the test distribution. This gives parameter distributions and confidence intervals (Bayesian sampling, approximate inference, deep generative models).
- Updated models underpin digital twins and **damage detection** (an inverse problem).

## Examples

- A nonlinear structure with limit-cycle oscillation: stochastic updating identified its stiffness and nonlinear parameters, and the model's mean response and confidence band enclosed the measured LCO amplitudes.

## Related

- Parent lectures: [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Related concepts: [[Verification and Validation]] · [[FE Model Verification Checks]] · [[Natural Frequencies and Mode Shapes]] · [[Digital Twin and Digital Thread]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt

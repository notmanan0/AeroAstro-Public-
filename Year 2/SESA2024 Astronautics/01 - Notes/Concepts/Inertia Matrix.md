---
title: "Inertia Matrix"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["inertia tensor", "products of inertia", "moments of inertia", "principal axes"]
tags: [sesa2024, concept, attitude-control]
status: complete
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Spacecraft Stabilisation Types]]", "[[Momentum Bias and Gyroscopic Rigidity]]"]
sources: ["02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf"]
---

# Inertia Matrix

## Definition

> [!note] Definition
>
> $$\mathbf H = [\mathbf I]\boldsymbol\omega,\qquad[\mathbf I] = \begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix}$$
>
> - **Moments of inertia**: $I_{xx} = \int(y^2+z^2)\,dm$.
> - **Products of inertia**: $I_{xy} = \int xy\,dm$.
> Both are taken about the centre of mass.

## Explanation
- **Diagonal terms** are always positive and measure resistance to angular acceleration (a tennis ball against a flywheel).
- **Off-diagonal terms** measure **unbalance**. They cause **cross-coupling**: a torque or rate about one axis produces angular momentum about another.
  - A symmetric cylinder has $I_{xy} = 0$, because mass at $(x,y)$ cancels mass at $(-x,y)$.
  - An asymmetric mass gives $I_{xy}\neq0$.
- **Principal axes**: the axes in which $[\mathbf I]$ is diagonal (its eigenvectors). Only about a principal axis are $\mathbf H$ and $\boldsymbol\omega$ parallel.
- It is important because $d([\mathbf I]\boldsymbol\omega)/dt = \mathbf T$: torquer sizing and control response depend on it directly.
- **Ideal spinner** (spin about $z$): diagonal, with equal transverse moments ($I_{xx} = I_{yy}$) and $I_{zz}$ the **maximum**.
- **Gravity-gradient**: a long thin body (one small moment, two large).

## Examples
- 2024/25 A4: $[\mathbf I]$ with products of −550, −125 and −650 kg m² is not a spinner or dual-spinner design, so it is **3-axis stabilised**. (Its eigenvalues are 556, 1698 and 2996 kg m².)
- Workbook Ch6 Q3 and Q11.
- Exam 2014/15 and 2019/20: "what are the product of inertia terms?" (2 marks).

## Related
- [[Spacecraft Stabilisation Types]] · [[Momentum Bias and Gyroscopic Rigidity]]
- Rotation matrices and body axes: [[Euler Angles and Rotation Matrices]] (SESA2027)

## Year 1 foundation
- Planar mass moment of inertia, radius of gyration and the parallel axis theorem: [[FEEG1002 D8 - Kinetics of Rigid Bodies]].

## Sources
- Chapter 6 pre-recorded material, slides 6–13

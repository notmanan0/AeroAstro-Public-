---
title: "Streamfunction and Velocity Potential"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["stream function", "velocity potential", "psi", "phi"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Method of Images]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Streamfunction and Velocity Potential

## Definition

> [!note] Definition
> For 2D incompressible flow the **streamfunction** $\psi$ satisfies continuity automatically. For irrotational flow the **velocity potential** $\phi$ satisfies irrotationality automatically:
> $$u = \frac{\partial\psi}{\partial y} = \frac{\partial\phi}{\partial x},\quad v = -\frac{\partial\psi}{\partial x} = \frac{\partial\phi}{\partial y};\qquad u_r = \frac1r\frac{\partial\psi}{\partial\theta} = \frac{\partial\phi}{\partial r},\quad u_\theta = -\frac{\partial\psi}{\partial r} = \frac1r\frac{\partial\phi}{\partial\theta}$$

## Explanation
- **Streamlines** are lines of constant $\psi$. The volume flow between two streamlines is $\psi_2-\psi_1$.
- **Equipotentials** ($\phi = $ const) cross streamlines at right angles.
- $\psi$ exists whenever $\nabla\cdot\mathbf V = 0$. $\phi$ exists whenever $\nabla\times\mathbf V = 0$. In potential flow both exist and both satisfy **Laplace's equation**, $\nabla^2\psi = \nabla^2\phi = 0$. Laplace is **linear**, so solutions superpose.
- **Any streamline can be a wall**, since there is no flow across it. That is the basis for modelling bodies, dunes, walls and hangars.

**Standard checks**
- Irrotational? Compute $\omega_z = \frac1r\partial_r(ru_\theta)-\frac1r\partial_\theta u_r$.
- Incompressible? Compute $\frac1r\partial_r(ru_r)+\frac1r\partial_\theta u_\theta$.
- To find $\psi$ or $\phi$ from velocities, integrate one component, then fix the arbitrary function using the other.

## Examples
- Irrotationality and divergence tests: [[SESA2022 Exam 2013-14 Solutions]] Q1 and [[SESA2022 Exam 2014-15 Solutions]] Q1.
- Corner flow, $\psi = 2r^2\sin2\theta$ with $\phi = 2r^2\cos2\theta$: [[SESA2022 Exam 2019-20 Solutions]] Q1.
- Wedge and corner flow plus a source: [[SESA2022 Exam 2024-25 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]]
- Related concepts: [[Elementary Potential Flows]], [[Method of Images]], [[Kutta-Joukowski Theorem]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`

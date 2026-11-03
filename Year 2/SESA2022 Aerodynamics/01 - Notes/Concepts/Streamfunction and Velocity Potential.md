---
title: "Streamfunction and Velocity Potential"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["stream function", "velocity potential", "psi", "phi", "Laplace equation potential flow"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Method of Images]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# Streamfunction and Velocity Potential

In two-dimensional incompressible flow the **streamfunction** $\psi$ satisfies continuity automatically, and in irrotational flow the **velocity potential** $\phi$ satisfies irrotationality automatically:

$$
u = \frac{\partial\psi}{\partial y} = \frac{\partial\phi}{\partial x},\quad v = -\frac{\partial\psi}{\partial x} = \frac{\partial\phi}{\partial y};\qquad u_r = \frac1r\frac{\partial\psi}{\partial\theta} = \frac{\partial\phi}{\partial r},\quad u_\theta = -\frac{\partial\psi}{\partial r} = \frac1r\frac{\partial\phi}{\partial\theta} .
$$

Lines of constant $\psi$ are streamlines, and the volume flow between two of them is $\psi_2-\psi_1$; equipotentials, $\phi = $ const, cross them at right angles. $\psi$ exists whenever $\nabla\cdot\mathbf V = 0$ and $\phi$ whenever $\nabla\times\mathbf V = 0$. In potential flow both exist and both satisfy Laplace's equation, $\nabla^2\psi = \nabla^2\phi = 0$, which is linear, so solutions can be superposed. Since nothing crosses a streamline, any streamline can be replaced by a wall, which is how bodies, dunes, walls and hangars are modelled.

Three checks come up repeatedly. A flow is irrotational if $\omega_z = \frac1r\partial_r(ru_\theta)-\frac1r\partial_\theta u_r = 0$, and incompressible if $\frac1r\partial_r(ru_r)+\frac1r\partial_\theta u_\theta = 0$ ([[SESA2022 Exam 2013-14 Solutions]] Q1, [[SESA2022 Exam 2014-15 Solutions]] Q1). To find $\psi$ or $\phi$ from the velocities, integrate one component and fix the arbitrary function with the other, as for the corner flow $\psi = 2r^2\sin2\theta$, $\phi = 2r^2\cos2\theta$ in [[SESA2022 Exam 2019-20 Solutions]] Q1 and the wedge plus source in [[SESA2022 Exam 2024-25 Solutions]] Q2.

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#2. Governing equations|T3 §2]]
- [[Elementary Potential Flows]] · [[Method of Images]] · [[Kutta-Joukowski Theorem]]

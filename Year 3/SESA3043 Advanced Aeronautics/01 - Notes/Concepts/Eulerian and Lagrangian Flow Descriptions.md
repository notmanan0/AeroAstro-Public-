---
title: "Eulerian and Lagrangian Flow Descriptions"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["Eulerian framework", "Lagrangian framework", "Eulerian description", "Lagrangian description", "Eulerian specification", "Lagrangian specification"]
tags: [sesa3043, concept, fluid-kinematics]
status: complete
parent_lectures: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]"]
related_concepts: ["[[Material Derivative]]", "[[Reynolds Transport Theorem]]"]
sources: ["02 - Sources/Lectures/L1 - SESA3043.txt"]
---

# Eulerian and Lagrangian Flow Descriptions

A **Lagrangian** description follows the same material particle, or system, as it moves and deforms. An **Eulerian** description watches fields such as $\rho(\mathbf x,t)$ and $\mathbf u(\mathbf x,t)$ at fixed positions, or inside a fixed control volume.

The two are linked by the [[Material Derivative]]. For any scalar $\phi$ carried by the flow,

$$
\frac{D\phi}{Dt}=\frac{\partial\phi}{\partial t}+\mathbf u\cdot\nabla\phi,
$$

which turns an Eulerian field into the rate of change a Lagrangian particle would see. The [[Reynolds Transport Theorem]] does the same job for extensive quantities in a finite system and control volume.

The lecture's river example puts numbers on it: a probe fixed to the bank reads $+1.00$ K/h while a drifting buoy reads $-0.44$ K/h in the same water ([[SESA3043 1.1 - Mathematical Tools and Flow Description#9.1 Two thermometers in a river (suggested)|SESA3043 1.1 §9.1]]).

## Related

- [[Material Derivative]] · [[Reynolds Transport Theorem]]

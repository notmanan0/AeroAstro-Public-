---
title: "Eulerian and Lagrangian Flow Descriptions"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 1: Conservation Laws"
aliases: ["Eulerian framework", "Lagrangian framework"]
tags: [sesa3043, concept, fluid-kinematics]
status: complete
parent_lectures: ["[[SESA3043 1.1 - Mathematical Tools and Flow Description]]"]
related_concepts: ["[[Material Derivative]]", "[[Reynolds Transport Theorem]]"]
sources: ["02 - Sources/Lectures/L1 - SESA3043.txt"]
---

# Eulerian and Lagrangian Flow Descriptions

## Definition

> [!note] Lagrangian
> Follow the same material particle or system as it moves and deforms.

> [!note] Eulerian
> Observe fields such as $\rho(\mathbf x,t)$ and $\mathbf u(\mathbf x,t)$ at fixed positions or within a fixed control volume.

## Connection

For any scalar $\phi$ carried by the flow,

$$
\frac{D\phi}{Dt}=\frac{\partial\phi}{\partial t}+\mathbf u\cdot\nabla\phi.
$$

The [[Material Derivative]] converts an Eulerian field into the rate seen by a Lagrangian particle. The [[Reynolds Transport Theorem]] performs the corresponding conversion for extensive quantities in a finite system and control volume.

## Related

- [[Material Derivative]] · [[Reynolds Transport Theorem]]


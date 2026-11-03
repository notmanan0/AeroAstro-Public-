---
title: "Method of Images"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 3: Potential Flow"
aliases: ["image vortex", "image source", "mirror images", "ground effect model"]
tags: [sesa2022, concept, potential-flow]
status: complete
parent_lectures: ["[[SESA2022 T3 - Potential Flow]]"]
related_concepts: ["[[Elementary Potential Flows]]", "[[Streamfunction and Velocity Potential]]"]
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf", "02 - Sources/Lectures/SESA2022 Lecture 11.txt … Lecture 16.txt (2025-26 transcripts)"]
---

# Method of Images

To model a flow element near a plane wall, the method of images adds a mirror-image element on the other side of the wall. The pair's combined flow has zero normal velocity on the wall, so the wall becomes a streamline.

| Real element | Image across the wall |
|---|---|
| Source $\Lambda$ | source $+\Lambda$ (same sign) |
| Vortex $\Gamma$ | vortex $-\Gamma$ (a mirror reverses the rotation) |
| Doublet pointing along the wall | same direction |
| Doublet pointing towards the wall | reversed |

A 90° corner between two walls needs three images: a mirror in each wall plus a diagonal image of an image. For a vortex the diagonal image has the same sign as the real one, because two reflections restore the sense of rotation. The check on any image system is that the $\psi$ contributions cancel on the wall (or the log arguments are equal there), so $\psi$ is constant along it. The method models ground effect (a wing vortex and its image reduce the downwash), wind-tunnel wall corrections, a fan near a wall, a starting vortex near the ground, and rounded bumps made from a vortex pair in a uniform stream.

Past-paper uses: a vortex in a 90° corner ([[SESA2022 Exam 2020-21 Solutions]] Part C); a rounded wall from a vortex and its image with $\Pi = \Gamma/(\pi Ua)$ ([[SESA2022 Exam 2021-22 Solutions]] Part C Q2); a fan (doublet) near a vertical wall ([[SESA2022 Exam 2022-23 Solutions]] Q2); a vortex pair in a stream ([[SESA2022 Exam 2013-14 Solutions]] Q2).

## Related

- Full derivation and worked examples: [[SESA2022 T3 - Potential Flow#11. Method of images|T3 §11]]
- [[Elementary Potential Flows]] · [[Streamfunction and Velocity Potential]]

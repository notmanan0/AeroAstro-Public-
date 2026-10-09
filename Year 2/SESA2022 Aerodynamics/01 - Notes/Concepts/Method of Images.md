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
sources: ["02 - Sources/PF/Topic 3 Potential Flow.pdf"]
---

# Method of Images

## Definition

> [!note] Definition
> To model a flow element near a **plane wall**, add a mirror-image element on the other side of the wall. The pair's combined flow has **zero normal velocity on the wall**, so the wall becomes a streamline.

## Explanation

| Real element | Image across the wall |
|---|---|
| Source $\Lambda$ | source $+\Lambda$ (same sign) |
| Vortex $\Gamma$ | vortex $-\Gamma$ (a mirror reverses the rotation) |
| Doublet pointing **along** the wall | same direction |
| Doublet pointing **towards** the wall | reversed |

- **Corner (two walls at 90°)**: three images are needed, one mirror in each wall plus one diagonal "image of an image". The diagonal image has the **same** sign as the real element for a vortex, because two reflections restore the sense of rotation.
- **Check**: on the wall, the $\psi$ contributions cancel (or the log arguments are equal), so $\psi = $ const.
- **Applications**:
  - Ground effect: a wing vortex plus its image reduces downwash.
  - Wind-tunnel wall corrections.
  - A fan near a wall.
  - A starting vortex near the ground.
  - Rounded bumps (a vortex pair in a uniform stream).

## Examples
- Vortex in a 90° corner: [[SESA2022 Exam 2020-21 Solutions]] Part C.
- Rounded wall from a vortex and its image with $\Pi = \Gamma/(\pi Ua)$: [[SESA2022 Exam 2021-22 Solutions]] Part C Q2.
- Fan (doublet) near a vertical wall: [[SESA2022 Exam 2022-23 Solutions]] Q2.
- Vortex pair in a stream: [[SESA2022 Exam 2013-14 Solutions]] Q2.

## Related
- Parent lectures: [[SESA2022 T3 - Potential Flow]]
- Related concepts: [[Elementary Potential Flows]], [[Streamfunction and Velocity Potential]]

## Sources
- `02 - Sources/PF/Topic 3 Potential Flow.pdf`

---
title: "Parallel Axis Theorem"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["parallel axis theorem", "Steiner's theorem", "transfer formula"]
tags: [feeg1002, concept, statics, beams, second-moment-of-area]
status: complete
parent_lectures: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
related_concepts: ["[[Engineer's Bending Theory]]", "[[Second Moments of Area]]", "[[First Moment of Area]]", "[[Principal Axes of a Section]]"]
sources: []
---

# Parallel Axis Theorem

## Definition

> [!note] Definition
> The second moment of area about any axis $z'$ parallel to a **centroidal** axis $z$, a distance $b$ away:
>
> $$I_{z'z'} = I_{zz} + Ab^2$$
>
> The cross term $2b\iint y\,dA$ vanishes only because $z$ passes through the centroid.

## Explanation

- **Composite sections**:
  1. locate the overall centroid, $\bar y = \sum A_iy_i/\sum A_i$;
  2. for each part, add its own centroidal $I_i$ to $A_ih_i^2$, where $h_i$ is its distance from the **overall** centroid.
- **Subtraction** works too: a solid block minus holes or missing corners, applying the theorem to each piece.
- The minimum $I$ in a family of parallel axes is about the centroid.
- $Ab^2$ usually dominates for flanges, often by more than 1000×. That is the whole case for I-beams, box beams and hollow tubes.
- The same theorem applies to mass moments of inertia: $I_O = I_G + md^2$ ([[FEEG1002 D8 - Kinetics of Rigid Bodies]]).

## Examples

- L8 I-beam: web 303 750 mm⁴; each flange $625 + 676\,875$ mm⁴; total $1.659\times10^{-6}$ m⁴.
- L8 channel: $\bar d = 13.21$ mm and $I = 2.379\times10^{-7}$ m⁴.

![[s1_parallel_axis_contributions.png|640]]

## Related

- Topic notes: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]
- Concepts: [[Engineer's Bending Theory]] · [[Second Moments of Area]] · [[First Moment of Area]] · [[Principal Axes of a Section]]
- Year 2: Extended to the product of area $I_{y'z'} = I_{yz} + A\,\Delta y\,\Delta z$ and [[Principal Axes of a Section]] in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]

## Sources

- Statics 1 Lecture 8b–c

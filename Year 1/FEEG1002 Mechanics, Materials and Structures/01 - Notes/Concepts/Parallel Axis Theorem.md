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
sources: ["Statics 1 Lecture 8"]
---

# Parallel Axis Theorem

The parallel axis theorem gives the second moment of area of a shape about any axis parallel to an axis through its own centroid, a distance $h$ away:

$$
I=I_c+Ah^2
$$

where $I_c$ is the second moment about the centroidal axis and $A$ the area.

The proof is one line of algebra. With $y$ measured from the centroidal axis, a point is $y+h$ from the parallel axis, so $\int(y+h)^2\,dA=\int y^2\,dA+2h\int y\,dA+h^2A$. The middle term vanishes because $\int y\,dA=0$ about a centroidal axis, which is why the theorem holds only when the starting axis passes through the centroid. It also shows that, of a family of parallel axes, the centroidal one gives the smallest second moment.

For a composite section the theorem is used part by part. First find the centroid of the whole section, $\bar y=\sum A_iy_i/\sum A_i$, which is where the neutral axis lies. Then add up each part's own centroidal second moment plus its area times the square of its distance from that overall centroid. Holes and cut-outs are handled the same way with negative area.

In an I-section the $Ah^2$ terms of the flanges dwarf their own $bd^3/12$ terms, often by a factor of a thousand, which is why putting material far from the neutral axis is such an efficient way to build a stiff, strong beam. The same theorem, with mass in place of area, transfers mass moments of inertia: $I_O=I_G+md^2$.

![[s1_parallel_axis_contributions.png|760]]

## Related

- Topic notes: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#5. The parallel axis theorem|A4, the parallel axis theorem]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Why the flanges matter|A4, why the flanges matter]] · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Locating the neutral axis|A4, locating the neutral axis]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 4 - Bending Stress and Second Moment of Area Solutions]]
- Concepts: [[Engineer's Bending Theory]] · [[Second Moments of Area]] · [[First Moment of Area]]
- Mass moments of inertia: [[FEEG1002 D8 - Kinetics of Rigid Bodies]]
- Year 2: the product of area and [[Principal Axes of a Section]] in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]

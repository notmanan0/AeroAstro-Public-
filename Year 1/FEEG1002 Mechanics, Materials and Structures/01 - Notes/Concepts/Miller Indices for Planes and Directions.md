---
title: "Miller Indices for Planes and Directions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["Miller indices", "crystal directions", "crystal planes", "[uvw]", "(hkl)", "families of planes"]
tags: [feeg1002, concept, materials, crystallography]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
related_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Dislocations and Slip Systems]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 03 - Crystals and Crystallography.pdf", "02 - Sources/Materials/Tutorials/Tutorial Sheet 01 - Crystal Structures, Planes and Directions.pdf"]
---

# Miller Indices for Planes and Directions

Miller indices are the three-integer labels for directions $[uvw]$ and planes $(hkl)$ in a cubic unit cell, measured in units of the lattice parameter $a$ along the cell's $x$, $y$ and $z$ edges.

A direction is a vector. Put its tail at the origin (moving the origin if necessary), read the coordinates of its head minus those of its tail in units of $a$, clear any fractions to the smallest integers, and write them in square brackets, with a bar over a negative index: from the origin to $(a,a,0)$ is $[110]$, and from $(a,0,0)$ to $(0,a,0)$ is $[\bar110]$. A plane is labelled by its intercepts. Choose an origin not on the plane, find where the plane cuts the three axes in units of $a$ (a plane parallel to an axis cuts it at infinity), take the reciprocals, clear fractions and write them in round brackets: intercepts $1,1,1$ give $(111)$, and intercepts $\infty,1,\infty$ give $(010)$.

![[m2_miller_planes.png|900]]

The two rules are easy to confuse, and that is the most common error: directions use the end points directly, planes use reciprocals. In cubic crystals the direction $[hkl]$ is perpendicular to the plane $(hkl)$, which is a useful check. Curly brackets $\{hkl\}$ denote a family of planes that are equivalent by the cube's symmetry (all six faces are $\{100\}$) and angle brackets $\langle uvw\rangle$ a family of directions.

The indices matter because slip runs on the close-packed planes and directions: $\{111\}\langle110\rangle$ in FCC, giving $4\times3=12$ slip systems. HCP needs a four-index system, which is not covered here.

## Related

- [[FEEG1002 C2 - Crystal Structures and Crystallography#5. Miller indices|Miller indices]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Directions|directions]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Planes|planes]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Close-packed planes and slip systems|close-packed planes and slip systems]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Worked example - the past exam question|the past exam question]]
- [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions#Q7 - Directions and planes|Tutorial 1, Q7]]
- [[Crystal Structures and Atomic Packing Factor]] · [[Dislocations and Slip Systems]]

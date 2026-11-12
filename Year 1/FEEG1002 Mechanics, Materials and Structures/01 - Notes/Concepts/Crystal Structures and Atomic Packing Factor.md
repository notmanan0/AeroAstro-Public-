---
title: "Crystal Structures and Atomic Packing Factor"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["APF", "atomic packing factor", "FCC", "BCC", "HCP", "unit cell", "close packing", "lattice parameter", "polymorphism"]
tags: [feeg1002, concept, materials, crystallography]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
related_concepts: ["[[Miller Indices for Planes and Directions]]", "[[Dislocations and Slip Systems]]", "[[Atomic Bonding and Interatomic Potential]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 03 - Crystals and Crystallography.pdf"]
---

# Crystal Structures and Atomic Packing Factor

A crystal is a regular three-dimensional array of atoms built by repeating a small unit cell; the atomic packing factor (APF) is the fraction of the unit cell's volume filled by its atoms, treated as hard spheres of radius $R$.

$$
\mathrm{APF}=\frac{n\cdot\tfrac43\pi R^3}{a^3}
$$

where $n$ is the number of atoms per cell and $a$ the cubic lattice parameter. Counting uses the share of each atom inside the cell: a corner atom counts $\tfrac18$, a face atom $\tfrac12$ and a body-centre atom 1. The lattice parameter comes from the direction in which the spheres touch: along the face diagonal in FCC, $a\sqrt2=4R$, and along the body diagonal in BCC, $a\sqrt3=4R$.

| Structure | Stacking | Atoms per cell | $a$ | APF | Examples |
|---|---|---:|---|---:|---|
| FCC | ABCABC | 4 | $2\sqrt2R$ | 0.74 | Al, Cu, Ni, austenite |
| BCC | not close-packed | 2 | $4R/\sqrt3$ | 0.68 | ferrite, Cr, W |
| HCP | ABAB | 6 | – | 0.74 | Mg, Ti |

FCC and HCP are both made by stacking close-packed layers, so both reach 0.74, the densest possible packing of equal spheres; they differ only in whether the third layer sits over the first (HCP) or in the remaining hollows (FCC). BCC has no close-packed planes and leaves more space empty.

![[m2_unit_cells.png|900]]

The structure matters for two reasons. Some elements change structure with temperature (polymorphism), and the change in packing changes the volume: iron switching from FCC to BCC expands because 0.68 < 0.74, which is what drives the shrinking-wire demonstration and the volume change on transformation in steel. And the close-packed planes and directions are where slip happens, so the structure decides how ductile a metal is.

## Related

- [[FEEG1002 C2 - Crystal Structures and Crystallography#2. Building solids by stacking close-packed layers|stacking close-packed layers]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Atoms per unit cell|atoms per unit cell]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Lattice parameter in terms of the atomic radius|lattice parameter]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Atomic packing factor|atomic packing factor]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#4. Polymorphism|polymorphism]] · [[FEEG1002 C2 - Crystal Structures and Crystallography#Worked example - the shrinking iron wire|the shrinking iron wire]]
- [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]] (Q1–Q6)
- [[Miller Indices for Planes and Directions]] · [[Dislocations and Slip Systems]] · [[Atomic Bonding and Interatomic Potential]]

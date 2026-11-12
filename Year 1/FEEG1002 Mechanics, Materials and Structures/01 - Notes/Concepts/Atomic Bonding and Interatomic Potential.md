---
title: "Atomic Bonding and Interatomic Potential"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["bond energy curve", "bonding energy", "interatomic force", "equilibrium spacing", "primary bonds", "secondary bonds", "ionic bonding", "covalent bonding", "metallic bonding", "van der Waals bonding"]
tags: [feeg1002, concept, materials, bonding]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C1 - Atoms and Bonding]]"]
related_concepts: ["[[Crystal Structures and Atomic Packing Factor]]", "[[Engineering Stress-Strain Properties]]", "[[Polymer Glass Transition and Viscoelasticity]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 01 - Introduction, Atoms and Bonding.pdf", "02 - Sources/Materials/Lectures/Lecture 02 - Atoms and Bonding.pdf"]
---

# Atomic Bonding and Interatomic Potential

The interatomic potential is the net energy $E_N(r)$ of a pair of atoms as a function of their separation $r$: an attractive term that pulls them together and a repulsive term that grows sharply when their electron clouds overlap. The net force is $F_N=dE_N/dr$, which is zero at the equilibrium spacing $r_0$, where the energy has its minimum $-E_0$, the bonding energy.

$$
E_N(r)=-\frac{A}{r^m}+\frac{B}{r^n},\qquad F_N=\frac{dE_N}{dr},\qquad F_N(r_0)=0
$$

with $n>m$ so that repulsion wins at short range. Two properties follow from the shape of this curve. The depth $E_0$ is the energy needed to pull the atoms apart, so a deep well means a high melting temperature. The curvature at the bottom of the well, equivalently the slope of the force curve where it crosses zero, is the stiffness of the bond, so a narrow, steep well means a high Young's modulus. Modelling the bond as a spring of stiffness $S_0=(d^2E_N/dr^2)_{r_0}$ gives Young's modulus $E\approx S_0/r_0$, and for the pair potential above $E\approx mnE_0/r_0^3$ (here $E$ without a subscript is the modulus).

![[m1_bond_force_energy.png|900]]

Primary bonds are strong: ionic bonds between ions of opposite charge (non-directional, ceramics such as NaCl and MgO), covalent bonds that share electrons in fixed directions (diamond, silicon, the backbone of polymer chains) and metallic bonds, in which positive ion cores sit in a sea of delocalised electrons (non-directional, so planes of atoms can slide). Secondary bonds, van der Waals and hydrogen bonds between dipoles, are far weaker. They are what hold polymer chains to one another, so a polymer's stiffness and softening temperature are set by its weakest bonds, not by the covalent chains.

The three material classes follow from this. Metals have non-directional bonds and can deform plastically; ceramics have strong ionic or covalent bonds with high melting points and stiffness but cannot slip easily, so they are brittle; polymers have covalent chains joined by secondary bonds and are compliant with low melting points.

## Related

- [[FEEG1002 C1 - Atoms and Bonding#2. The bond force and energy curve|the bond force and energy curve]] · [[FEEG1002 C1 - Atoms and Bonding#Why the curve sets melting point and stiffness|melting point and stiffness]] · [[FEEG1002 C1 - Atoms and Bonding#Linking well depth to stiffness|well depth and stiffness]] · [[FEEG1002 C1 - Atoms and Bonding#3. Primary bonds|primary bonds]] · [[FEEG1002 C1 - Atoms and Bonding#4. Secondary bonding|secondary bonding]] · [[FEEG1002 C1 - Atoms and Bonding#6. Bonding explains the three material classes|the three material classes]]
- [[Stress, Strain and Young's Modulus]] · [[Engineering Stress-Strain Properties]] · [[Crystal Structures and Atomic Packing Factor]] · [[Polymer Glass Transition and Viscoelasticity]]

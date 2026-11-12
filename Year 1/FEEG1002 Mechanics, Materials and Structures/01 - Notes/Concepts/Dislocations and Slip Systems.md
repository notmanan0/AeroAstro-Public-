---
title: "Dislocations and Slip Systems"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["dislocation", "edge dislocation", "screw dislocation", "Burgers vector", "slip", "slip system", "slip plane", "slip direction", "twinning"]
tags: [feeg1002, concept, materials, plasticity]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
related_concepts: ["[[Strengthening Mechanisms in Metals]]", "[[Miller Indices for Planes and Directions]]", "[[Ductile-to-Brittle Transition]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 06 - Plastic Deformation and Alloying.pdf"]
---

# Dislocations and Slip Systems

A dislocation is a line defect in a crystal, the edge of an extra half-plane of atoms (edge dislocation) or a spiral step through the lattice (screw dislocation); plastic deformation in metals happens by dislocations gliding on particular planes and in particular directions, a combination called a slip system.

Shearing a perfect crystal would mean breaking every bond across a plane at once, which needs a stress far above what real metals yield at. A dislocation lets the plane slip one row of bonds at a time, like moving a ruck along a carpet, so the stress needed is small. The displacement it carries, the Burgers vector $\mathbf b$, is perpendicular to the line for an edge dislocation and parallel to it for a screw. When a dislocation leaves the crystal it leaves a step one Burgers vector high at the surface; many of them make the slip lines seen on a polished specimen.

![[m4_edge_dislocation_slip.png|900]]

Slip is easiest on the most densely packed planes in the most densely packed directions. FCC has four $\{111\}$ planes each with three $\langle110\rangle$ directions, $4\times3=12$ slip systems spread in every orientation, so whatever the loading some system is well aligned: FCC metals (aluminium, copper, austenitic stainless steel) are soft, ductile and little affected by temperature. BCC has no close-packed planes, so slip needs thermal help and its yield stress rises steeply in the cold, the root of the ductile-to-brittle transition in ferritic steel. HCP has close-packed planes but only the one basal set, so few easy systems; titanium and magnesium are hard to form. Twinning, a mirror-image shear of part of a grain, is the alternative when slip systems are scarce.

The stress field around a dislocation (compression above an edge dislocation's slip plane, tension below) is what lets it interact with solute atoms, other dislocations, grain boundaries and precipitates, which is the basis of every strengthening mechanism.

## Related

- [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Edge and screw dislocations|edge and screw dislocations]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Slip|slip]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Slip systems|slip systems]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Temperature and the yield stress|temperature and the yield stress]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Twinning|twinning]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#The stress field of an edge dislocation|stress field]]
- [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q3 - Obstacles to dislocation motion|Tutorial 2, Q3]]
- [[Strengthening Mechanisms in Metals]] · [[Miller Indices for Planes and Directions]] · [[Ductile-to-Brittle Transition]] · [[Crystal Structures and Atomic Packing Factor]]

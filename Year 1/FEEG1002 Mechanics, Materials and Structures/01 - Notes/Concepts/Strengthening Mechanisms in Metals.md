---
title: "Strengthening Mechanisms in Metals"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["work hardening", "strain hardening", "cold work", "grain-boundary strengthening", "grain refinement", "Hall–Petch", "solid-solution strengthening", "solution hardening"]
tags: [feeg1002, concept, materials, strengthening]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]", "[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
related_concepts: ["[[Dislocations and Slip Systems]]", "[[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening]]", "[[Annealing of Cold-Worked Metals]]", "[[Hall-Petch Relation]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 07 - Strengthening Mechanisms and Annealing.pdf", "02 - Sources/Materials/Lectures/Lecture 06 - Plastic Deformation and Alloying.pdf"]
---

# Strengthening Mechanisms in Metals

A metal yields when dislocations can move, so every way of strengthening it puts obstacles in their path: solute atoms (solid-solution strengthening), other dislocations (work hardening), grain boundaries (grain-boundary strengthening) and fine particles of a second phase (precipitation hardening).

Solute atoms of a different size distort the lattice around them, and that strain field interacts with the strain field of a dislocation: a small substitutional atom sits comfortably in the compressed region above an edge dislocation, a large one in the stretched region below, and either way the dislocation is held back. Interstitial carbon in iron pins dislocations in the same way and gives low-carbon steel its upper and lower yield points.

Work hardening uses plastic deformation itself. Straining multiplies the dislocations, their density rises steeply, and dislocations on intersecting slip systems tangle and repel each other, so each increment of strain needs more stress. Unload a work-hardened bar and it springs back elastically along a line of slope $E$; reload it and it stays elastic up to the stress it had reached, so the yield strength has risen, while the ductility left has fallen by the plastic strain already used. The amount of cold work is the percentage reduction in area from $A_0$ to $A_d$, $\%CW=(A_0-A_d)/A_0\times100$.

![[m5_hall_petch.png|900]]

Grain boundaries stop slip because the slip planes change direction across them. Dislocations pile up behind a boundary and concentrate stress there until slip starts in the next grain; small grains give short pile-ups that concentrate less stress, so a higher applied stress is needed. That gives the Hall–Petch relation

$$
\sigma_y=\sigma_0+k_yd^{-1/2}
$$

with $d$ the average grain diameter and $\sigma_0$, $k_y$ material constants. Grain refinement raises strength without much loss of toughness, and it is the one mechanism that lowers the ductile-to-brittle transition temperature, where the others raise it. Fine grains are a drawback at high temperature, though, where their boundaries speed up creep. Precipitation hardening has its own note, [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]].

## Related

- [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Solid-solution strengthening|solid-solution strengthening]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Interstitial carbon and the yield point of steel|interstitial carbon]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#2. Work hardening|work hardening]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Unloading and reloading|unloading and reloading]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#The Hall–Petch relation|the Hall–Petch relation]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Worked example - Hall–Petch from two grain sizes|Hall–Petch example]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Strengthening moves the transition|strengthening and the DBTT]]
- [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q5 - Effects of work hardening|Tutorial 2, Q5]]
- [[Dislocations and Slip Systems]] · [[Year 1/FEEG1002 Mechanics, Materials and Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] · [[Annealing of Cold-Worked Metals]] · [[Ductile-to-Brittle Transition]]
- Year 2: [[Hall-Petch Relation]] in SESA2028

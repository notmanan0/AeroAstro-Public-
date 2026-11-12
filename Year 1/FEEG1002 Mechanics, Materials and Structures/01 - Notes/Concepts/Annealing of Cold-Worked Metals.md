---
title: "Annealing of Cold-Worked Metals"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["annealing", "recovery", "recrystallisation", "recrystallization", "grain growth", "process annealing"]
tags: [feeg1002, concept, materials, heat-treatment]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
related_concepts: ["[[Strengthening Mechanisms in Metals]]", "[[Fick's Laws and Arrhenius Diffusion]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 07 - Strengthening Mechanisms and Annealing.pdf"]
---

# Annealing of Cold-Worked Metals

Annealing is heating a cold-worked metal, typically to around half its absolute melting temperature, $T\approx0.5T_m$, and holding it there, so that diffusion can undo the effects of work hardening: the strength falls back and the ductility returns.

It happens in three stages, all driven by diffusion. In recovery the tangled dislocations rearrange into low-angle walls, with the compressive field of each beside the tensile field of its neighbour; internal stresses are relieved but the grains and the mechanical properties barely change. In recrystallisation new, strain-free, equiaxed grains nucleate in the dislocation-free regions and grow, sweeping away the old dislocations until the whole worked structure is replaced; this is where the strength falls and the ductility rises steeply. In grain growth, if the metal is held longer or hotter, large grains consume small ones because the total grain-boundary energy falls, and the strength keeps falling slowly as the Hall–Petch contribution shrinks.

![[m5_annealing_properties.png|900]]

The final grain size can be controlled. More prior cold work stores more energy and gives more nucleation sites, so the recrystallised grains are finer; a higher annealing temperature speeds diffusion and gives coarser grains. Because the new grains are fine, a recrystallised metal keeps part of its strength through grain-boundary strengthening while most of its ductility comes back; a blacksmith reheating a bar in the fire between bouts of hammering is doing the same thing.

Each stage is thermally activated, so its rate follows the Arrhenius form, $r=A\exp(-Q/RT)$, and the time to reach a given state is proportional to $1/r$. Two (rate, temperature) pairs give $Q$, and $Q$ then gives the temperature needed for a target time or rate.

## Related

- [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#5. Annealing|annealing]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Recovery|recovery]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Recrystallisation|recrystallisation]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Grain growth|grain growth]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Properties against annealing temperature|properties against temperature]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Recrystallisation as a thermally activated process|thermal activation]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Worked example - activation energy for recrystallisation|worked example]]
- [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q6 - Restoring the properties by annealing|Tutorial 2, Q6]] · [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions#Q7 - Growth velocity of recrystallised grains|Q7]]
- [[Strengthening Mechanisms in Metals]] · [[Fick's Laws and Arrhenius Diffusion]]

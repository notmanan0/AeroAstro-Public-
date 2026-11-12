---
title: "Ductile-to-Brittle Transition"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["DBTT", "ductile-to-brittle transition temperature", "ductile–brittle transition", "Charpy test", "impact energy", "toughness against temperature"]
tags: [feeg1002, concept, materials, fracture]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]"]
related_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Dislocations and Slip Systems]]", "[[Strengthening Mechanisms in Metals]]", "[[Ductile-Brittle Transition]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 12 - Failure of Materials 1 - Brittle vs Ductile and Griffiths.pdf"]
---

# Ductile-to-Brittle Transition

The ductile-to-brittle transition is the change, on cooling, of a BCC metal such as ferritic steel from failing by plastic deformation to failing by brittle fracture; the temperature at which it happens is the ductile-to-brittle transition temperature (DBTT).

It comes from two competing stresses. The brittle fracture stress $\sigma_f$ depends on $E$, $\gamma_s$ and the flaw size, none of which changes much with temperature, so $\sigma_f$ is roughly constant. The yield stress depends on how easily dislocations move. FCC metals have many close-packed slip systems always well oriented to the load, so their yield stress hardly changes with temperature and stays below $\sigma_f$: they always yield first and are tough even at cryogenic temperatures. BCC metals have no close-packed planes, so dislocation motion needs thermal help and the yield stress rises as the temperature falls. Where it crosses $\sigma_f$, the metal reaches its fracture stress before it can yield and breaks with almost no plastic deformation.

![[m8_dbtt_mechanism.png|900]]

Anything that moves either curve moves the crossing. Work hardening, precipitation hardening and solid-solution strengthening raise $\sigma_y$ but not $\sigma_f$, so they raise the DBTT and make the metal more brittle. Grain refinement raises $\sigma_y$ but raises $\sigma_f$ more, because a cleavage crack must change direction at every grain boundary, so it lowers the DBTT: the metal ends up both stronger and tougher.

The transition is measured with the Charpy impact test, where a pendulum breaks a notched bar and the energy absorbed is read from the height of its swing after impact. BCC steels show a high upper shelf, a sharp drop through the transition and a low lower shelf; FCC metals stay high; HCP metals are low and rise gradually. This toughness, the energy absorbed to fracture, is not the same quantity as the fracture toughness $K_{IC}$. The *Titanic*'s hull steel, near or below its transition in near-freezing water, is the classic case.

## Related

- [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#5. The ductile-to-brittle transition|the ductile-to-brittle transition]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Two competing stresses|two competing stresses]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Strengthening moves the transition|strengthening moves the transition]] · [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics#Toughness and the Charpy test|toughness and the Charpy test]] · [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation#Temperature and the yield stress|temperature and the yield stress]]
- [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q1 - Toughness against temperature|Tutorial 4, Q1]]
- [[Griffith Criterion and Fracture Toughness]] · [[Dislocations and Slip Systems]] · [[Strengthening Mechanisms in Metals]]
- Year 2: [[Ductile-Brittle Transition]] in SESA2028

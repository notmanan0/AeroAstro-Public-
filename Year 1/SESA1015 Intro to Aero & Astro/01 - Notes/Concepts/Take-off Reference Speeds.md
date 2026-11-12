---
title: "Take-off Reference Speeds"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["V1 VR VLOF V2", "Take-off critical speeds", "Decision speed", "Take-off safety speed", "Screen speed"]
tags: [sesa1015, concept, takeoff]
status: complete
parent_lectures: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
related_concepts: ["[[Take-off Ground Run]]", "[[Wing Loading]]"]
sources: ["Mechanics of Flight Course Notes §7.3–7.3.1, pp. 38–40", "Mechanics of Flight Lecture Slides v2, pp. 154–155"]
---

# Take-off Reference Speeds

The take-off reference speeds are the speeds an aircraft passes through on take-off: the decision speed $V_1$, the rotation speed $V_R$, the lift-off speed $V_{LOF}$ and the take-off safety (screen) speed $V_2$, reached at a screen height of 35 ft (10.7 m).

Below $V_1$ an engine failure means stopping: the aircraft can still decelerate to rest in the runway remaining. Above $V_1$ it must continue, and aerodynamic controls alone must be adequate. At $V_R$ the pilot raises the nose and the lift rises quickly; at $V_{LOF}$ the aircraft unsticks; a transition then curves the path into a steady climb, and $V_2$ is the speed at the screen. The take-off distance is the ground run $s_1$ plus the airborne distance $s_2$ to the screen.

The speeds are tied to the stall speed in the take-off configuration $V_s$ and to three limiting speeds: the minimum unstick speed $V_{mu}$, and the minimum control speeds in the air $V_{mca}$ and on the ground $V_{mcg}$ with the critical engine failed. The conditions are $V_R>V_1$ and $V_R\ge1.05V_{mca}$; $V_{LOF}\ge1.1V_{mu}$ with all engines or $1.05V_{mu}$ with one out; and $V_2\ge1.1V_{mca}$ with $V_2\ge1.2V_s$ for a jet or $1.15V_s$ for a piston aircraft.

Ground-run calculations assume acceleration stops at lift-off, so $V_2\approx V_{LOF}=1.2V_s$ and the ground run is the distance to reach $V_2$. A margin of 1.2 on speed is a margin of $1.2^2=1.44$ on dynamic pressure, which is where the 1.44 in the ground-run formula comes from; it also means that a wing held at $C_{L_{max}}$ would carry 1.44 times its weight at $V_2$, so on the run the wing is held at a lower $C_L$.

## Related

- Topic: [[SESA1015 M09 - Take-off and Landing Performance]] (take-off profile figure, engine-failure example)
- Concepts: [[Take-off Ground Run]] · [[Wing Loading]] · [[Aerofoil Stall]]

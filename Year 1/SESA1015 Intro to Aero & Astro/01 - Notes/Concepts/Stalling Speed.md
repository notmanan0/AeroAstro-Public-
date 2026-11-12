---
title: "Stalling Speed"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["stall speed", "V_S", "V stall", "1-g stall speed", "equivalent stalling speed"]
tags: [sesa1015, concept, stall, level-flight]
status: complete
parent_lectures: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
related_concepts: ["[[Wing Loading]]", "[[Airspeed Measures]]", "[[Aerofoil Stall]]", "[[Take-off Ground Run]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.2, pp. 19–20)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 75–76)"]
---

# Stalling Speed

The stalling speed is the minimum speed of steady level flight: the speed at which the lift coefficient needed for $L=W$ reaches $C_{L\max}$, so $V_S=\sqrt{2W/\rho SC_{L\max}}=\sqrt{2w/\rho C_{L\max}}$.

It follows from setting $C_L=C_{L\max}$ in the lift balance $W=\tfrac12\rho V^2SC_L$. Below $V_S$ the wing cannot make enough lift at any angle, and the aircraft descends. The aerodynamic stall is a different statement: past $C_{L\max}$ the flow separates and lift falls as the angle rises, which can happen at any speed if the angle is pushed high enough. The stalling speed is the speed at which the two coincide in level flight, and it holds only for $L=W$; in a turn or pull-up at load factor $n$ the stall comes at $\sqrt n\,V_S$ ([[Load Factor and Turn Performance]]).

The formula gives every trend at once. $V_S$ goes as $\sqrt W$, so it falls as fuel is burned, $V_{S1}/V_{S2}=\sqrt{W_1/W_2}$. It goes as $\sqrt w$, so a heavily loaded wing stalls fast ([[Wing Loading]]). It goes as $1/\sqrt{C_{L\max}}$, so flaps and slats, which can more than double $C_{L\max}$ from about 1.2 clean, cut the landing speed by 29% or more. And it goes as $1/\sqrt\rho$, so the true stalling speed rises with altitude: $\sigma=0.75$ raises it by $1/\sqrt{0.75}=1.155$.

In equivalent airspeed the altitude effect disappears. Since $\rho V^2=\rho_0V_e^2$, $V_{e,S}=\sqrt{2W/\rho_0SC_{L\max}}$, with no altitude-dependent term: for a given weight and configuration the stall occurs at a fixed dynamic pressure $w/C_{L\max}$, and the airspeed indicator, which senses dynamic pressure, shows the same stalling speed at every height ([[Airspeed Measures]]). For example, $w=4981$ N/m² and $C_{L\max}=1.75$ give 68.2 m/s EAS at every height, which is 78.7 m/s true at $\sigma=0.75$ ([[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]]).

The stalling speed sets the take-off and landing speeds through fixed margins, typically $V_2=1.2V_S$ for a jet ([[SESA1015 M09 - Take-off and Landing Performance]]), and a required landing speed becomes a maximum wing loading in [[SESA1015 M12 - Aircraft Constraint Analysis|constraint analysis]].

## Related

- Topics: [[SESA1015 M04 - Steady Level Flight and Stall]] ([[SESA1015 M04 - Steady Level Flight and Stall#2. Stalling speed|stalling speed]]) · [[SESA1015 M09 - Take-off and Landing Performance]] · [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]
- Solutions: [[SESA1015 T01 - Stall and Level-Flight Solutions]] · [[SESA1015 T02 - Take-off and Landing Solutions#Question 40]]
- Concepts: [[Wing Loading]] · [[Airspeed Measures]] · [[Aerofoil Stall]] · [[Load Factor and Turn Performance]] · [[Take-off Ground Run]]
- Sources: Course Notes §4.2 (pp. 19–20); Lecture Slides v2, pp. 75–76.

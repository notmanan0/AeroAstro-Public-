---
title: "Power Specific Fuel Consumption"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Power-specific fuel consumption", "Brake specific fuel consumption", "BSFC", "c_p", "Piston engine SFC"]
tags: [sesa1015, concept, propulsion, range, propeller]
date: 2026-11-07
status: complete
parent_lectures: ["[[SESA1015 M07 - Propeller Aircraft Range and Endurance]]"]
related_concepts: ["[[Thrust Specific Fuel Consumption]]", "[[Breguet Range Equation]]", "[[Propulsive Efficiency]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§6.2)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 68, 123–126)"]
---

# Power Specific Fuel Consumption

Power specific fuel consumption, $c_p$ (written $s'$ in the course notes), is the weight of fuel an engine uses per unit time to produce unit shaft power, in newtons of fuel per second per watt (N s⁻¹ W⁻¹, equivalently newtons per joule).

It is the natural measure for engines that deliver shaft power, whose output is roughly independent of flight speed: piston engines and turboprops, and, with the battery's specific energy $E^*$ in place of $g/c_p$, electric motors. It is usually quoted per kilowatt hour and must be converted before use: $2.7$ N/(kW h) $=2.7/(1000\times3600)=7.5\times10^{-7}$ N s⁻¹ W⁻¹. Engine data are often given on a mass basis (brake specific fuel consumption, kg per kW h), which is $c_p/g$.

The engine must supply the drag power through the propeller and transmission, $P'=DV/\eta$, so the weight falls at $dW/dt=-c_pDV/\eta$. Per unit distance this is $-c_pD/\eta$, with no speed in it, which gives the propeller Breguet range $R=\frac{\eta}{c_p}\frac{L}{D}\ln\frac{W_1}{W_2}$, best at $(L/D)_{max}$, and the endurance $E=\frac{\eta}{c_p}\frac{C_L^{3/2}}{C_D}\sqrt{2\rho S}\left(W_2^{-1/2}-W_1^{-1/2}\right)$, best at minimum power. The ratio $\eta/c_p$ has the dimensions of length.

It differs from the jet's thrust-specific consumption $c_t$ (N s⁻¹ N⁻¹, that is s⁻¹; [[Thrust Specific Fuel Consumption]]). Thrust power is thrust times speed, so a propeller engine of constant $c_p$ behaves like a jet whose $c_t=c_pV/\eta$ rises in proportion to speed. That is why every propeller optimum (range at $V_{MD}$, endurance at $V_{MP}$) sits one step slower than the corresponding jet optimum ([[Minimum Drag and Minimum Power]]).

Worked value: an 8000 N (dry) aircraft with $\eta=0.85$, $c_p=2.7$ N/(kW h) and $(L/D)_{max}=11.95$ needs 684 N of fuel for 1112 km ([[SESA1015 M07 - Propeller Aircraft Range and Endurance]]).

## Related

- Topics: [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] (power available)
- Concepts: [[Thrust Specific Fuel Consumption]] · [[Breguet Range Equation]] · [[Propulsive Efficiency]] · [[Calorific Value]]
- Solutions: [[SESA1015 T04 - Range and Endurance Solutions#Question 27]]

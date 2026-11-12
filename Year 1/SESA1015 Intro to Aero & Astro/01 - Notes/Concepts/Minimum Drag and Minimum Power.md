---
title: "Minimum Drag and Minimum Power"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["V_MD and V_MP", "Performance Optima", "Minimum drag speed", "Minimum power speed"]
tags: [sesa1015, concept, minimum-drag, minimum-power, performance]
date: 2026-09-27
status: complete
parent_lectures: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
related_concepts: ["[[Parabolic Drag Polar]]", "[[Maximum Lift-to-Drag Ratio]]", "[[Breguet Range Equation]]", "[[Power Specific Fuel Consumption]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.4–4.6)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 79–104)"]
---

# Minimum Drag and Minimum Power

The minimum drag speed $V_{MD}$ is the level-flight speed at which the drag, and so the thrust required, is least; the minimum power speed $V_{MP}$ is the speed at which the power required, $DV$, is least.

In level flight with a parabolic polar $C_D=C_{D0}+KC_L^2$, the drag is $D=AV^2+B/V^2$ with $A=\tfrac12\rho SC_{D0}$ and $B=2KW^2/(\rho S)$: a profile part rising with speed and an induced part falling with it. Setting $dD/dV=0$ gives $AV^4=B$, so the two parts are equal at the minimum, $C_{D0}=KC_L^2$. Setting $dP/dV=0$ for $P=AV^3+B/V$ gives $3AV^4=B$, so at minimum power the induced drag is three times the profile drag, $KC_L^2=3C_{D0}$. The full derivations, including the route through the coefficient ratios $C_L/C_D$ and $C_L^{3/2}/C_D$, are in [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]].

| | minimum drag | minimum power |
|---|---|---|
| condition | profile $=$ induced, max $C_L/C_D$ | induced $=3\times$ profile, max $C_L^{3/2}/C_D$ |
| $C_L$ | $\sqrt{C_{D0}/K}$ | $\sqrt{3C_{D0}/K}=\sqrt3\,C_{L,MD}$ |
| $C_D$ | $2C_{D0}$ | $4C_{D0}$ |
| speed | $V_{MD}=\sqrt{2W/(\rho SC_{L,MD})}$ | $V_{MP}=3^{-1/4}V_{MD}=0.760\,V_{MD}$ |
| drag | $D_{min}=2W\sqrt{KC_{D0}}$ | $1.155\,D_{min}$ |
| effect of altitude | $D_{min}$ unchanged; $V_{MD}\propto1/\sqrt\sigma$ | $P_{min}\propto1/\sqrt\sigma$ |

The minimum drag is independent of density, so it is the same at every height and occurs at the same equivalent airspeed; only the true airspeed rises as the air thins. The minimum power is not: the same drag is overcome at a higher true airspeed, so $P_{min,alt}=P_{min,SL}/\sqrt\sigma$. Geometrically, $V_{MD}$ is where the tangent from the origin touches the $C_L$–$C_D$ polar, and also where the tangent from the origin touches the power-required curve, since $P/V=D$; $V_{MP}$ is the lowest point of the power curve.

The two speeds matter because engines burn fuel in proportion to different things. A jet's fuel flow follows thrust, so its endurance is best at $V_{MD}$ and its range at a higher speed ($3^{1/4}V_{MD}$ at constant altitude). A propeller engine's fuel flow follows power, so its endurance is best at $V_{MP}$ and its range at $V_{MD}$ ([[SESA1015 M06 - Jet Aircraft Range and Endurance]], [[SESA1015 M07 - Propeller Aircraft Range and Endurance]]). In gliding flight $V_{MD}$ gives the flattest glide and $V_{MP}$ the least sink rate ([[SESA1015 M08 - Glide and Climb Performance]]).

Worked values (Slides v2 example, 1350 kg, $S=16.25$ m², $AR=7$, $e=0.95$, $C_{D0}=0.028$): $(L/D)_{max}=13.66$, $D_{min}=969$ N, $V_{MD}=41.6$ m/s at sea level and 48.4 m/s at 3050 m (both $V_e=41.6$ m/s), $V_{MP}=31.6$ and 36.8 m/s, $P_{min}=35.4$ and 41.2 kW.

> [!warning] Feasibility
> Minimum drag is not minimum drag coefficient, and an optimum is only usable if it is flyable: $C_{L,MP}=\sqrt3\,C_{L,MD}$ can lie close to or above $C_{L,max}$, and both speeds must be checked against the stall speed and the thrust or power available.

## Related

- Topics: [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]] · [[SESA1015 M06 - Jet Aircraft Range and Endurance]] · [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] · [[SESA1015 M08 - Glide and Climb Performance]]
- Concepts: [[Parabolic Drag Polar]] · [[Airspeed Measures]] · [[Maximum Lift-to-Drag Ratio]] · [[Cruise-Climb]] · [[Power Specific Fuel Consumption]]
- Solutions: [[SESA1015 T01 - Stall and Level-Flight Solutions]] (Revision Q14, Q15)

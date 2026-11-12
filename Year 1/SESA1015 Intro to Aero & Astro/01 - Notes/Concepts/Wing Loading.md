---
title: "Wing Loading"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["W over S", "W/S", "wing loading w"]
tags: [sesa1015, concept, wing-loading, aircraft-design]
status: complete
parent_lectures: ["[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]", "[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
related_concepts: ["[[Stalling Speed]]", "[[Aircraft Constraint Diagram]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§4.1–4.2, pp. 19–20)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 41–42, 75)"]
---

# Wing Loading

Wing loading is the aircraft's weight divided by its reference (gross) wing area, $w=W/S$, in N/m²: the average lift each square metre of wing must carry in level flight.

Dividing the level-flight lift balance $W=\tfrac12\rho V^2SC_L$ by $S$ gives $w=qC_L$, so the wing loading is the dynamic pressure multiplied by the lift coefficient the wing must work at. Rearranged, $V=\sqrt{2w/\rho C_L}$: at a given density and lift coefficient the flight speed goes as $\sqrt w$. At $C_{L\max}$ this is the stalling speed, $V_S=\sqrt{2w/\rho C_{L\max}}$ ([[Stalling Speed]]), so a 21% rise in wing loading raises the stalling speed by $\sqrt{1.21}=1.10$, 10%, and a 14% cut in stalling speed needs the wing loading cut to $0.86^2=0.74$ of its value ([[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]]). Two aircraft with the same stalling speed at the same density need maximum lift coefficients in the ratio of their wing loadings.

The choice of wing loading is a trade. A small wing for its weight (high $w$) has less wetted area and so less profile drag and structure, and it cruises at a sensible $C_L$ of 0.2 to 0.5 at high speed; at a cruise point of Mach 0.61 at 11 km with $C_L=0.23$ the wing loading comes out at 1352 N/m² ([[SESA1015 T01 - Stall and Level-Flight Solutions#Question 30]]). A large wing (low $w$) gives low stalling, take-off and landing speeds, tighter turns and a higher ceiling. Light aircraft sit near 500 to 1000 N/m² and airliners near 5000 to 7000 N/m². Wing loading is the horizontal axis of the [[Aircraft Constraint Diagram]], on which each performance requirement becomes a limit on $w$ or on the thrust-to-weight ratio.

Two slips are common: using the mass in kilograms instead of the weight in newtons, and using a net or wetted area instead of the gross reference area that the coefficients are based on.

## Related

- Topics: [[SESA1015 M04 - Steady Level Flight and Stall]] · [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]] · [[SESA1015 M09 - Take-off and Landing Performance]] · [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]] · [[SESA1015 M12 - Aircraft Constraint Analysis]]
- Concepts: [[Stalling Speed]] · [[Aircraft Constraint Diagram]] · [[Dynamic Pressure and Aerodynamic Coefficients]]
- Sources: Course Notes §4.1–4.2 (pp. 19–20); Lecture Slides v2, pp. 41–42 and 75.

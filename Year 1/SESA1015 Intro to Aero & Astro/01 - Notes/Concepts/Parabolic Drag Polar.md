---
title: "Parabolic Drag Polar"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Drag Polar", "C_D = C_D0 + K C_L^2", "parabolic polar", "profile and induced drag"]
tags: [sesa1015, concept, drag-polar, induced-drag]
status: complete
parent_lectures: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]", "[[SESA1015 M04 - Steady Level Flight and Stall]]", "[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
related_concepts: ["[[Downwash and Induced Drag]]", "[[Oswald Efficiency Factor]]", "[[Maximum Lift-to-Drag Ratio]]", "[[Minimum Drag and Minimum Power]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§3.2, pp. 13–14; §4.3, p. 21)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 51–57, 62–63, 78)"]
---

# Parabolic Drag Polar

The parabolic drag polar models an aircraft's drag coefficient as a constant profile part plus an induced part proportional to the square of the lift coefficient, $C_D=C_{D0}+KC_L^2$ with the induced drag factor $K=1/\pi eAR$.

The profile drag coefficient $C_{D0}$ is the drag at zero lift: skin friction on the wetted surface and form drag from the boundary layer, plus interference and excrescence drag. It is about 0.01 to 0.025 for a streamlined aircraft in the cruise configuration and up to 0.055 with a fixed undercarriage. The induced part comes from the downwash of the trailing vortices, which tilts the lift back by the induced angle; since that angle is itself proportional to $C_L$, the drag it produces goes as $C_L^2$. For an elliptic wing $C_{Di}=C_L^2/\pi AR$, and any other planform is worse by a factor $1+\delta\ge1$, so $K=(1+\delta)/\pi AR=1/\pi eAR$ (Slides v2, p. 51), with the span (Oswald) efficiency $e=1/(1+\delta)$, typically 0.6 to 1 ([[Oswald Efficiency Factor]]). The same polar is written $kC_L^2$ with $k=K/\pi A$ in the course notes, where their $K$ is a planform factor equal to $1/e$ and $A$ is the aspect ratio, so their $k$ is the $K$ used here. A typical polar is $C_D=0.02+0.055C_L^2$.

Plotted against $C_L^2$ the polar is a straight line, with intercept $C_{D0}$ and slope $K$, which is how its constants are read from wind-tunnel data. Two readings are enough: subtracting $C_{D1}=C_{D0}+KC_{L1}^2$ from $C_{D2}=C_{D0}+KC_{L2}^2$ gives $K=(C_{D2}-C_{D1})/(C_{L2}^2-C_{L1}^2)$, and then $C_{D0}=C_{D1}-KC_{L1}^2$. The drag at the lowest test angle is not $C_{D0}$ unless the lift there is zero ([[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 12]]).

In level flight $C_L=2W/\rho V^2S$, so the polar turns into a drag curve in speed, $D=AV^2+B/V^2$ with $A=\tfrac12\rho SC_{D0}$ and $B=2KW^2/\rho S$: profile drag rising as $V^2$, induced drag falling as $1/V^2$. Their sum has a minimum where the two parts are equal, $KC_L^2=C_{D0}$, at $C_L=\sqrt{C_{D0}/K}$, which is also where $C_L/C_D$ is greatest, $(L/D)_{max}=1/(2\sqrt{KC_{D0}})$, and where a line from the origin touches the polar ([[Minimum Drag and Minimum Power]], [[Maximum Lift-to-Drag Ratio]]).

The parabola is a model of attached, subsonic flow. Near the stall the real polar curls away from it, at high subsonic Mach number wave drag adds to it, and each configuration (flaps, slats, undercarriage) has its own constants. A clean $C_{D0}$ does not go with a landing $C_{L\max}$.

## Related

- Topics: [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] ([[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar#The parabolic drag polar|the polar]]) · [[SESA1015 M04 - Steady Level Flight and Stall]] · [[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]
- Solutions: [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]] · [[SESA1015 T01 - Stall and Level-Flight Solutions]]
- Concepts: [[Downwash and Induced Drag]] · [[Oswald Efficiency Factor]] · [[Maximum Lift-to-Drag Ratio]] · [[Minimum Drag and Minimum Power]] · [[Lift-Curve Slope]]
- Sources: Course Notes §3.2 (pp. 13–14) and §4.3 (p. 21); Lecture Slides v2, pp. 51–57, 62–63 and 78.

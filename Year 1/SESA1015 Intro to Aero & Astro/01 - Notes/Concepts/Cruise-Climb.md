---
title: "Cruise-Climb"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Cruise climb", "Drift-up", "Breguet cruise"]
tags: [sesa1015, concept, range, jet, cruise]
date: 2026-11-07
status: complete
parent_lectures: ["[[SESA1015 M06 - Jet Aircraft Range and Endurance]]"]
related_concepts: ["[[Breguet Range Equation]]", "[[Minimum Drag and Minimum Power]]", "[[Thrust Specific Fuel Consumption]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§5.3–5.4)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 117–121)"]
---

# Cruise-Climb

A cruise-climb is a jet cruise flown at constant true airspeed and constant angle of attack, in which the aircraft climbs slowly as it burns fuel so that the falling air density keeps the lift equal to the falling weight.

With $V$ and $C_L$ fixed, $W=\tfrac12\rho_{SL}\sigma V^2SC_L$ makes the relative density proportional to the weight, $\sigma_2/\sigma_1=W_2/W_1$. In the stratosphere a jet's thrust at a fixed throttle setting is roughly proportional to $\sigma$, and the drag $W\,C_D/C_L$ is proportional to $W$, so thrust and drag fall together and stay equal with no throttle movement. The speed of sound is constant there, so constant true airspeed is constant Mach number: the aircraft holds its Mach number and drifts up.

Because $V$ and $L/D$ are both constant, the cruise-climb is exactly the condition under which the jet's range integrates to the Breguet form, $R=\frac{V}{c_t}\frac{L}{D}\ln\frac{W_1}{W_2}$ ([[Breguet Range Equation]]). It gives more range than a cruise at constant altitude and constant $C_L$ from the same starting state, by the factor $\ln(W_1/W_2)\big/\big[2(1-\sqrt{W_2/W_1})\big]$, since at constant altitude the aircraft has to slow down as it lightens. The height gained in the isothermal stratosphere is $\Delta h=\frac{RT_s}{g}\ln\frac{W_1}{W_2}$, about 6.34 km times the log of the weight ratio; the slide-example jet burning 24.5 % of its weight climbs 1784 m.

The best speed depends on what fixes it. At a fixed engine setting ($T/\sigma$ constant) the speed is tied to $C_D$ by $V^2C_D=$ constant, the range factor is $C_L/C_D^{3/2}$, and the optimum is $C_L=C_{L,MD}/\sqrt2$, $V=2^{1/4}V_{MD}$, with profile drag twice the induced drag. If the speed is instead fixed from the starting weight and height, the factor is $C_L^{1/2}/C_D$ and the optimum is $3^{1/4}V_{MD}$, as at constant altitude. In practice compressibility caps the Mach number below either value, and air-traffic control allows the gradual climb on the main long-haul routes but not indefinitely; airliners approximate it with step climbs.

## Related

- Topics: [[SESA1015 M06 - Jet Aircraft Range and Endurance]] (derivations and worked examples) · [[SESA1015 M07 - Propeller Aircraft Range and Endurance]] (compressibility and the summary of cruise techniques)
- Concepts: [[Breguet Range Equation]] · [[Thrust Specific Fuel Consumption]] · [[Minimum Drag and Minimum Power]] · [[International Standard Atmosphere]]

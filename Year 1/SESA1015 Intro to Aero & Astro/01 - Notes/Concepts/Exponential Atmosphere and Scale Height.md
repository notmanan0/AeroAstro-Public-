---
title: "Exponential Atmosphere and Scale Height"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Scale height", "Exponential atmosphere", "Barometric formula", "Diffusive separation"]
tags: [sesa1015, concept, astronautics, atmosphere]
status: complete
parent_lectures: ["[[SESA1015 A02 - Space Environment]]"]
related_concepts: ["[[International Standard Atmosphere]]", "[[Atomic Oxygen Erosion]]", "[[Space Environment Hazards]]"]
sources: ["Astronautics Part 2 (Environment), pp. 14–20, equations (2.1)–(2.2)"]
---

# Exponential Atmosphere and Scale Height

In an isothermal layer of gas under constant gravity, density falls exponentially with height, $\rho=\rho_0e^{-(h-h_0)/H}$, and the **scale height** $H=RT/(Mg)$ is the height over which it falls by a factor $e$.

The result comes from two equations. Hydrostatic balance on a thin slab says $dp=-\rho g\,dh$; the ideal gas law with the universal gas constant and the molar mass says $p=\rho RT/M$, so at constant $T$, $dp=(RT/M)\,d\rho$. Eliminating $dp$ gives $d\rho/\rho=-(Mg/RT)\,dh$, which integrates to the exponential. Above about 100 km turbulent mixing stops and each gas settles in its own balance (diffusive equilibrium), so equation (2.1) of Part 2 applies species by species: $\rho_i=\rho_{i0}\exp[-gM_i(h-h_0)/(RT)]$, with $H_i=RT/(M_ig)$.

Because $H_i\propto T/M_i$, light gases thin out slowly. At 1000 K and $g=9.0$ m/s², $H$ is 33 km for N$_2$, 58 km for O, 231 km for He and 924 km for H. The ratio of two species then changes exponentially with height, which is why atomic oxygen overtakes molecular nitrogen near 190 to 200 km and helium overtakes oxygen several hundred kilometres higher. Temperature enters linearly: when the thermosphere heats from about 700 K at solar minimum to 1500 K at solar maximum, every scale height roughly doubles, the density at a fixed LEO altitude rises by about an order of magnitude, and drag and orbital decay rise with it.

In the lower atmosphere the same formula with $T\approx250$ K and $M=0.029$ kg/mol gives $H\approx7.3$ km. That is the scale used in the max-q estimate of [[SESA1015 A03 - Launch Environment]], where a vertical climb at constant acceleration reaches maximum dynamic pressure at $h=H$. The exponential is only a local fit: the real temperature varies with height (the troposphere lapse rate of the [[International Standard Atmosphere]], the steep thermosphere rise), so $H$ itself varies, and the single-$H$ form of equation (2.2) works only over a limited band.

## Related

- Topics: [[SESA1015 A02 - Space Environment]] (§3) · [[SESA1015 A03 - Launch Environment]] (§4) · [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]
- Concepts: [[International Standard Atmosphere]] · [[Atomic Oxygen Erosion]] · [[Space Environment Hazards]]
- Later: [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]
- Sources: Astronautics Part 2, pp. 14–20

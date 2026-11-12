---
title: "Gravity and Drag Losses"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Gravity Loss", "Drag Loss", "Ascent Losses", "Delta-V Losses"]
tags: [sesa1015, concept, astronautics, rocket]
status: complete
parent_lectures: ["[[SESA1015 A04 - Rocket Equation and Launch Performance]]"]
related_concepts: ["[[Tsiolkovsky Rocket Equation]]", "[[Rocket Mass Fractions]]", "[[Dynamic Pressure and Aerodynamic Coefficients]]"]
sources: ["02 - Sources/Astronautics/Astronautics - Part 3 - Launch Vehicles.pdf (pp. 13–21)"]
---

# Gravity and Drag Losses

Gravity loss and drag loss are the parts of a launch vehicle's ideal velocity change that are spent holding the vehicle up against gravity and pushing it through the air rather than adding to its speed: $\Delta V=\Delta V_{ideal}-\Delta V_g-\Delta V_D$, equation (3.3) of Part 3.

With thrust along the velocity, the equation of motion along the path is

$$
\frac{dV}{dt}=-V_{ex}\frac{1}{M}\frac{dM}{dt}-g\sin\gamma-\frac{D}{M},
$$

and integrating over the burn gives

$$
\Delta V=V_{ex}\ln\frac{M_0}{M_b}-\int_0^tg\sin\gamma\,dt-\int_0^t\frac{D}{M}\,dt ,
$$

where $\gamma$ is the flight-path angle and $D=\frac12\rho V^2SC_D$. The two integrals are the gravity loss $\Delta V_g$ and the drag loss $\Delta V_D$. Typical values are $\Delta V_g\approx0.75$–$1.5$ km/s and $\Delta V_D\approx0.2$–$0.3$ km/s, which raise the 7.8 km/s needed for LEO to about 8.75 km/s.

The two pull in opposite directions. Gravity loss accumulates for as long as the vehicle thrusts with a vertical component; for a vertical burn at constant $g$ it is $g t_b=V_{ex}(1-M_b/M_0)/(T/M_0g)$, so a high thrust-to-weight ratio and an early turn towards the horizontal both reduce it. Drag loss grows with $\rho V^2$, so it is large if the vehicle gains speed while low in dense air, which is what high thrust and an early turn produce. A real ascent rises steeply out of the dense atmosphere, then lets gravity bend the path over (the gravity turn, from $MV\dot\gamma=L-Mg\cos\gamma$ with $L=0$) and builds horizontal speed above it. Gravity loss is normally several times larger than drag loss.

The common mistake is to compare a launcher's ideal $\Delta V$ directly with the orbital speed: the losses must be added to the requirement first, and the eastward speed of the launch site (up to 0.465 km/s at the equator) can be subtracted for an eastward launch.

## Related

- Topics: [[SESA1015 A04 - Rocket Equation and Launch Performance]] ([[SESA1015 A04 - Rocket Equation and Launch Performance#5. Gravity loss and drag loss|derivation and loss trade]]) · [[SESA1015 A06 - Launch Vehicles, Systems and Interfaces]] · [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Concepts: [[Tsiolkovsky Rocket Equation]] · [[Rocket Mass Fractions]] · [[Multistage Rocket Performance]] · [[Dynamic Pressure and Aerodynamic Coefficients]]
- Sources: Astronautics Part 3, pp. 13–21.

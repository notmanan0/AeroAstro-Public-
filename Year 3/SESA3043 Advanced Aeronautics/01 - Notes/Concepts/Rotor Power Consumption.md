---
title: "Rotor Power Consumption"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["rotor power required", "parasite power", "helicopter power curve", "induced plus parasite plus profile power"]
tags: [sesa3043, concept, rotor, forward-flight, power]
status: complete
parent_lectures: ["[[SESA3043 4.3 - Rotor in Forward Flight]]"]
related_concepts: ["[[Disc Tilt]]", "[[Induced Velocity in Forward Flight]]", "[[Autorotation]]", "[[Minimum Drag and Minimum Power]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Rotor Power Consumption

The power a rotor needs in forward flight is the sum of the induced power, the parasite power and the profile power.

Actuator disc theory gives the first two, from the thrust acting on air crossing the disc at $V_z+v_i$:

$$
P=Tv_i+TV_z.
$$

The induced power $Tv_i$ makes the thrust; it is largest in hover and falls roughly as $T^2/(2\rho AV)$ at speed. The parasite power $TV_z$ overcomes the fuselage drag: in level flight $T\sin\gamma=D$, so $TV_z=DV=\tfrac12\rho V^3f$, rising as $V^3$. The disc has no blades, so the profile power, the work against the blade sections' own drag, comes from blade element theory ([[SESA3043 4.1 - Rotor in Hover|4.1]]), $P_{profile}=\tfrac18\rho V_T^3NcRC_D$ at its hover value. In coefficients, $C_P=C_T(\lambda_i+\mu_z)+\tfrac14sC_{D0}$.

The falling induced power and rising parasite power give the power curve a minimum, as for a fixed-wing aircraft ([[Minimum Drag and Minimum Power]]). For the Lynx at 5330 kg with an assumed drag area of 1.5 m², solidity 0.08 and $C_{D0}=0.010$, the total is 838 kW in hover, 508 kW at 60 m/s (144.5 induced, 198.5 parasite, 164.9 profile) and a minimum of about 438 kW near 42 m/s. The same split holds in axial flight, where $TV_C$ (climb power) takes the place of $TV_z$.

## Related

- Parent lecture: [[SESA3043 4.3 - Rotor in Forward Flight]] · axial flight: [[SESA3043 4.2 - Rotor in Axial Flight]]
- Related concepts: [[Disc Tilt]] · [[Induced Velocity in Forward Flight]] · [[Autorotation]] · [[Minimum Drag and Minimum Power]] (SESA1015)

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 47, 66, 88.
- Notes: written ahead from the slides, 17 Nov 2026.

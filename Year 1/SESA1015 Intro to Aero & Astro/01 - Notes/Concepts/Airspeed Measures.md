---
title: "Airspeed Measures"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["True airspeed", "Equivalent airspeed", "Indicated airspeed", "TAS", "EAS", "IAS", "IAS CAS EAS TAS", "Relative density"]
tags: [sesa1015, concept, airspeed, atmosphere]
status: complete
parent_lectures: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]"]
related_concepts: ["[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Stagnation Pressure and Pitot Tube]]", "[[International Standard Atmosphere]]", "[[Speed of Sound and Mach Number]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.2, pp. 5–7)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 22–24)"]
---

# Airspeed Measures

The true airspeed $V$ is the speed of an aircraft relative to the air; the equivalent airspeed $V_E$ is the speed at sea-level density that gives the same dynamic pressure, so $\tfrac12\rho_{SL}V_E^2=\tfrac12\rho V^2$ and $V_E=V\sqrt\sigma$ with $\sigma=\rho/\rho_{SL}$ the relative density.

A pitot-static tube measures $p_0-p=\tfrac12\rho V^2$ (at low Mach number). Turning that into a speed needs a density. With the local density the result is the true airspeed, $V=\sqrt{2(p_0-p)/\rho}$; the airspeed indicator does not know $\rho$, so it uses the sea-level value and shows $V_E=\sqrt{2(p_0-p)/\rho_{SL}}$. Equating the two expressions for $p_0-p$ gives

$$
V=\frac{V_E}{\sqrt\sigma} .
$$

Above sea level in the ISA $\sigma<1$ and the true airspeed is the larger: at 1000 m ($\sigma=0.907$) by 5%, at 11 km ($\sigma=0.297$) by 83%.

The two speeds answer different questions. Every aerodynamic force is $\tfrac12\rho V^2SC=\tfrac12\rho_{SL}V_E^2SC$, so loads, stall speed and handling are fixed in equivalent airspeed at any altitude: an aircraft that stalls at $V_E=50$ m/s stalls at $V=50/\sqrt{0.75}=57.7$ m/s where $\sigma=0.75$. Distance, flight time and Mach number need the true airspeed, $M=V/a$ with $a=\sqrt{\gamma RT}$ at altitude.

The instrument reading itself is the indicated airspeed $V_{ind}$. It equals $V_E$ only if the true static pressure reaches the instrument, but the static pressure sensed depends on where the vent is, on the angle of attack and on the flap setting; this course takes $V_{ind}=V_E$ unless a correction is given. In industry the chain has one more step: indicated airspeed corrected for instrument and position errors is the calibrated airspeed (CAS), and CAS corrected for compressibility is EAS. The compressibility correction exists because a real pitot tube reads $p_0-p=\tfrac12\rho V^2(1+M^2/4+\cdots)$, 2.3% high at $M=0.3$ and 17% high at $M=0.8$. Adding the wind to the true airspeed gives the ground speed, which is what navigation uses.

| Speed | Definition | Used for |
|---|---|---|
| indicated, $V_{ind}$ | instrument reading | cockpit; taken as $V_E$ in SESA1015 |
| calibrated (CAS) | $V_{ind}$ corrected for instrument and position error | industry intermediate step |
| equivalent, $V_E$ | $\sqrt{2(p_0-p)/\rho_{SL}}=V\sqrt\sigma$ | dynamic pressure, loads, stall |
| true, $V$ | $\sqrt{2(p_0-p)/\rho}$ | Mach number, range, time, kinematics |
| ground speed | $V$ plus the wind | navigation |

Worked example (Slides v2, p. 24): at 1000 m, $p=89\,852$ Pa and $\rho=1.116$ kg/m³; a total pressure of 95 435 Pa gives $p_0-p=5583$ Pa, so $V=\sqrt{2\times5583/1.116}=100.0$ m/s and $V_E=\sqrt{2\times5583/1.23}=95.3$ m/s.

The common trap is to correct in the wrong direction. At altitude the true airspeed must come out larger than the equivalent airspeed, so divide by $\sqrt\sigma$ to go from $V_E$ to $V$.

## Related

- Topics: [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (derivations, worked examples)
- Concepts: [[Dynamic Pressure and Aerodynamic Coefficients]] · [[Stagnation Pressure and Pitot Tube]] · [[International Standard Atmosphere]] · [[Speed of Sound and Mach Number]] · [[Compressible Pitot Probe]]
- Practice: [[SESA1015 T01 - Stall and Level-Flight Solutions#Question 1]] (true stall speed at altitude)

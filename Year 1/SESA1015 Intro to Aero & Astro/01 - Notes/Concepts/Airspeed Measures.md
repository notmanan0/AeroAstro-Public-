---
title: "Airspeed Measures"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, airspeed, atmosphere]
aliases: ["IAS CAS EAS TAS", "Equivalent Airspeed"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf"]
---

# Airspeed Measures

> [!abstract] Core idea
> Different airspeeds answer different questions. IAS is what the instrument shows; CAS corrects installation error; EAS represents dynamic pressure; TAS is motion through the air mass; ground speed adds wind.

$$\frac12\rho_0V_{EAS}^2=\frac12\rho V_{TAS}^2$$

so

$$\boxed{V_{TAS}=V_{EAS}\sqrt{\frac{\rho_0}{\rho}}}.$$

| Speed | Main use |
|---|---|
| IAS | cockpit handling reference |
| CAS | corrected pressure-system reading |
| EAS | aerodynamic loading and low-speed performance |
| TAS | kinematics and Mach calculation |
| ground speed | navigation and elapsed distance |

At sea-level standard density, EAS and TAS coincide. At altitude, TAS is normally higher for the same EAS.

> [!warning] Compressibility
> The simple pressure–speed conversion assumes low Mach. EAS includes a compressibility correction to CAS; supersonic Pitot measurement needs shock relations.

**Quick check:** if $\rho/\rho_0=0.49$, then $V_{TAS}=V_{EAS}/0.7$.

See also [[Dynamic Pressure and Aerodynamic Coefficients]] and [[Speed of Sound and Mach Number]].


---
title: "Dynamic Pressure and Aerodynamic Coefficients"
module: "SESA1015 Intro to Aero & Astro"
type: concept
tags: [sesa1015, dynamic-pressure, aerodynamic-coefficients]
aliases: ["Dynamic Pressure", "Aerodynamic Coefficients"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]", "[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf"]
---

# Dynamic Pressure and Aerodynamic Coefficients

$$\boxed{q=\frac12\rho V^2}$$

Dynamic pressure supplies the natural aerodynamic force scale:

$$L=qSC_L,\qquad D=qSC_D,\qquad M=qS\bar cC_m.$$

Coefficients separate size and operating condition from aerodynamic behaviour, but remain functions of variables such as $\alpha$, $Re$, $M$, surface roughness and configuration.

### Interpretation

- Holding $C_L$ and $S$ fixed, equal $q$ gives equal lift.
- Doubling speed at fixed density quadruples $q$.
- A coefficient is dimensionless only when its reference area and length are defined.

### Data reduction

Given measured force and state,

$$C_L=\frac{L}{qS},\qquad C_D=\frac{D}{qS}.$$

The uncertainty in $V$ enters twice because $q\propto V^2$.

> [!warning] Do not call $q$ pressure in the thermodynamic sense
> It has pressure units but represents a kinetic-energy density/flow scale. Static pressure and dynamic pressure play different roles.


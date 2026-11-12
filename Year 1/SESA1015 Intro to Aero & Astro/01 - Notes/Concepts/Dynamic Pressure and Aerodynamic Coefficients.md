---
title: "Dynamic Pressure and Aerodynamic Coefficients"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Dynamic pressure", "Aerodynamic coefficients", "Lift coefficient", "Drag coefficient", "Pitching moment coefficient", "CL CD CM"]
tags: [sesa1015, concept, dynamic-pressure, aerodynamic-coefficients]
status: complete
parent_lectures: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]", "[[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]]"]
related_concepts: ["[[Airspeed Measures]]", "[[Wing Planform Geometry]]", "[[Reynolds Number]]", "[[Pressure Coefficient]]", "[[Wing Loading]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf (§2.2, §2.4)", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf (pp. 19, 45–48)"]
---

# Dynamic Pressure and Aerodynamic Coefficients

The dynamic pressure $q=\tfrac12\rho V^2$ is the kinetic energy per unit volume of the oncoming air and the natural scale of every aerodynamic force; an aerodynamic coefficient is a force or moment divided by $q$ and a reference area (and length), for example $C_L=L/(qS)$.

Dimensional analysis forces this form. If the lift depends on $\rho$, $V$, a length $l$, the angle of attack and the shape, the only force that can be built from $\rho$, $V$ and $l$ is $\rho V^2l^2$, so $L=\tfrac12\rho V^2SC_L$ with $C_L$ a function of the dimensionless quantities only. Including viscosity and compressibility adds two more groups, so

$$
C_L=f(\alpha,\ Re,\ M,\ \text{shape}),\qquad Re=\frac{\rho Vl}{\mu},\qquad M=\frac Va .
$$

The same holds for the drag and the pitching moment:

$$
L=qSC_L,\qquad D=qSC_D,\qquad M=qS\bar{\bar c}\,C_M ,
$$

with $S$ the gross wing area and $\bar{\bar c}$ the mean aerodynamic chord ([[Wing Planform Geometry]]). Section (two-dimensional) coefficients use the chord in place of the area: $C_l=L'/(qc)$ for the lift per unit span, $C_m=M'/(qc^2)$. Surface stresses use $q$ alone: $C_p=(p-p_\infty)/q$, $C_f=\tau_w/q$.

The dynamic pressure is also what a pitot-static tube measures at low Mach number, $p_0-p=q$, which is why the equivalent airspeed, defined by $q=\tfrac12\rho_{SL}V_E^2$, fixes the loads ([[Airspeed Measures]]). It has the units of pressure but is not a pressure acting on a surface; it is the rise in pressure when the flow is brought to rest without losses. Doubling the speed at fixed density quadruples it, and the same true airspeed at 11 km ($\sigma=0.297$) gives less than a third of the sea-level value.

Coefficients make wind-tunnel data, flight data and different aircraft comparable. Two geometrically similar bodies at the same $\alpha$, $Re$ and $M$ have the same coefficients whatever their size. Below the stall, $C_L$ at a given $\alpha$ is almost independent of $Re$ for subsonic flow, while $C_D$ depends on $Re$ through skin friction and separation. In data reduction, $C_L=L/(qS)$ inherits twice the relative error in $V$, because $q\propto V^2$.

Worked example: a light aircraft of weight 10 791 N and wing area 16.2 m² flying level at 60 m/s where $\rho=1.0065$ kg/m³ has $q=1811.7$ Pa and $C_L=10\,791/(1811.7\times16.2)=0.368$; with $C_D=0.035$ its drag is $qSC_D=1027$ N.

The common trap is to use a coefficient with the wrong reference area: a $C_L$ quoted on the gross area and multiplied by the net area underestimates the lift.

## Related

- Topics: [[SESA1015 M02 - Aircraft Geometry, Forces and Coefficients]] (dimensional analysis, coefficient table, similarity) · [[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]] (dynamic pressure and the pitot tube) · [[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]] (how $C_L$ and $C_D$ vary with $\alpha$)
- Concepts: [[Airspeed Measures]] · [[Wing Planform Geometry]] · [[Reynolds Number]] · [[Pressure Coefficient]] · [[Buckingham Pi Theorem]] · [[Wing Loading]]
- Practice: [[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions#Question 9]] (coefficients from balance readings)

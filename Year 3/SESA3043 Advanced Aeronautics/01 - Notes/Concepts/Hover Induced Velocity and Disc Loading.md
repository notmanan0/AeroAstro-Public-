---
title: "Hover Induced Velocity and Disc Loading"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["hover induced velocity", "induced velocity", "v0", "downwash velocity", "disc loading", "disk loading", "induced power", "ideal induced power", "rotor efficiency", "power loading", "wake contraction", "rotor momentum theory"]
tags: [sesa3043, concept, rotor, hover, actuator-disc]
status: complete
parent_lectures: ["[[SESA3043 4.1 - Rotor in Hover]]"]
related_concepts: ["[[Actuator Disk Theory]]", "[[Rotor Thrust and Power Coefficients]]", "[[Induced Power Factor]]", "[[Figure of Merit]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Hover Induced Velocity and Disc Loading

The induced velocity is the downward velocity a hovering rotor gives the air passing through its disc. For an actuator disc of area $A$ carrying thrust $T$ in still air its hover value is $v_0=\sqrt{T/2\rho A}$, set entirely by the disc loading $T/A$.

The result comes from applying Bernoulli separately above and below the disc, which gives $T=\tfrac12\rho v_2^2A$, and a momentum balance on the streamtube, which gives $T=\rho Av_iv_2$. Together they force $v_2=2v_i$: half the wake velocity is reached at the disc, and the far wake contracts to half the disc area. Then $T=2\rho Av_i^2$ and $v_i=v_0=\sqrt{T/2\rho A}$ ([[SESA3043 4.1 - Rotor in Hover#3. Hover induced velocity v0|4.1 §3]]).

The power the rotor must supply to keep up that flow is the ideal induced power,

$$
P_i=Tv_0=\frac{T^{3/2}}{\sqrt{2\rho A}},
$$

equal to the kinetic energy given to the wake per second. The thrust per unit induced power, $T/P_i=1/v_0$, is the rotor efficiency (power loading). Both depend on the disc loading only through $\sqrt{T/A}$, so lifting a given weight is cheapest with the largest possible disc. The Westland Lynx at maximum take-off (5330 kg, $R=6.4$ m) has $T/A=406$ N/m², $v_0=12.9$ m/s and $P_i=673$ kW; a Harrier, lifting on a jet of far smaller area, has an induced velocity of order 200 m/s.

The hover $v_0$ is also the reference velocity for axial and forward flight: climb, descent and forward-flight inflow are all written as multiples of $v_0$ ([[SESA3043 4.2 - Rotor in Axial Flight|4.2]], [[SESA3043 4.3 - Rotor in Forward Flight|4.3]]).

## Related

- Parent lecture: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Actuator Disk Theory]] (SESA2023, propeller form) · [[Rotor Thrust and Power Coefficients]] · [[Induced Power Factor]] · [[Figure of Merit]] · [[Rotor Ground Effect]]

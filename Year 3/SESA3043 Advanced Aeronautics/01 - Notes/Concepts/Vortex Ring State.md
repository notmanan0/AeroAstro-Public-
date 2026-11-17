---
title: "Vortex Ring State"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["VRS", "vortex-ring state", "settling with power"]
tags: [sesa3043, concept, rotor, descent]
status: complete
parent_lectures: ["[[SESA3043 4.2 - Rotor in Axial Flight]]"]
related_concepts: ["[[Rotor Working States in Axial Flight]]", "[[Induced Velocity in Axial Flight]]", "[[Windmill Brake State]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Vortex Ring State

The vortex ring state is the flow of a rotor in slow axial descent, roughly $0<V_D<1.5v_0$, in which the tip vortices collect into a ring around the disc edge and the air recirculates through the disc instead of leaving as a wake.

In hover the wake carries the tip vortices away below the disc. In a slow descent the upward relative wind $V_D$ opposes the downwash, so the vortices are held near the disc and pile up into a doughnut-shaped ring. Air goes down through the inner part of the disc, up outside the tips and back in from above. There is no streamtube with a single flow direction, so actuator disc theory has no solution here: the climb equation's flow picture is wrong for any descent, and the descent equation $\bar v_i^2-\bar V_D\bar v_i+1=0$ has real roots only for $\bar V_D\geq2$.

Averaged test data show the downwash rising to about $2.4v_0$ near $\bar V_D\approx1.5$, and the power, $P=T(-V_D+v_i)$, staying close to the hover value instead of falling. The flow is unsteady, the thrust fluctuates and control is degraded. Adding collective to arrest the descent strengthens the ring, so recovery is by flying out of it with forward speed (see [[SESA3043 4.3 - Rotor in Forward Flight|4.3]]). For the Lynx at 5330 kg ($v_0=12.9$ m/s) the band covers vertical descents up to about 20 m/s; at 15 m/s the simple model $v_i=v_0$ would predict power extracted, whereas the measured downwash gives about $+Tv_0$.

## Related

- Parent lecture: [[SESA3043 4.2 - Rotor in Axial Flight]]
- Related concepts: [[Rotor Working States in Axial Flight]] · [[Induced Velocity in Axial Flight]] · [[Windmill Brake State]] · [[Autorotation]]

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 60–61, 65–66.
- Notes: written ahead from the slides, 17 Nov 2026.

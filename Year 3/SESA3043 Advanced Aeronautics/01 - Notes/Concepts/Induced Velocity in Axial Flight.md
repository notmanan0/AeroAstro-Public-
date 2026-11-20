---
title: "Induced Velocity in Axial Flight"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["climb induced velocity", "descent induced velocity", "normalised downwash", "axial momentum theory", "rotor in climb", "rotor in descent", "climb velocity", "descent velocity"]
tags: [sesa3043, concept, rotor, actuator-disc, axial-flight]
status: complete
parent_lectures: ["[[SESA3043 4.2 - Rotor in Axial Flight]]"]
related_concepts: ["[[Rotor Working States in Axial Flight]]", "[[Windmill Brake State]]", "[[Vortex Ring State]]", "[[Autorotation]]", "[[Actuator Disk Theory]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf", "02 - Sources/Lectures/20 November 2026 at 14_51_19.txt"]
---

# Induced Velocity in Axial Flight

The induced velocity $v_i$ of a rotor climbing at $V_C$ or descending at $V_D$ along its axis, found from actuator disc theory and normalised by the hover value $v_0=\sqrt{T/2\rho A}$ of the same rotor at the same thrust.

Bernoulli on each side of the disc and a momentum balance on the streamtube give $v_2=2v_i$ in climb and in descent, exactly as in hover. Putting that back into $T=\dot mv_2$ gives a quadratic for each case, with $\bar v_i=v_i/v_0$:

$$
\text{climb: }\ \bar v_i^2+\bar V_C\bar v_i-1=0,\qquad \text{descent: }\ \bar v_i^2-\bar V_D\bar v_i+1=0.
$$

In climb the physical root is the positive one, $\bar v_i=-\bar V_C/2+\sqrt{\bar V_C^2/4+1}$, which equals 1 in hover and tends to $1/\bar V_C$ in a fast climb; the negative root would make the mass flow through the disc upward. In descent the roots are real only for $\bar V_D\geq2$, both are positive, and the physical one is the smaller, $\bar V_D/2-\sqrt{\bar V_D^2/4-1}$, because the larger one reverses the far wake ($V_D-2v_i<0$). Writing descent as $\bar V_C=-\bar V_D$ puts both on one plot against $\bar V_C$.

The two equations leave a gap, $-2<\bar V_C<0$, where neither applies: the climb equation's flow picture is wrong for any descent, and the descent equation has no real root. That band is the vortex ring and turbulent wake region, where the measured downwash rises to about $2.4v_0$ ([[Rotor Working States in Axial Flight]]). The power follows from the same control volume: $P=T(V_C+v_i)$ in climb and $P=T(-V_D+v_i)$ in descent.

For the Lynx at 5330 kg ($v_0=12.88$ m/s), a 5 m/s climb gives $\bar v_i=0.8245$ and $v_i=10.62$ m/s; a 30 m/s descent gives $\bar v_i=0.567$ and $v_i=7.30$ m/s ([[SESA3043 4.2 - Rotor in Axial Flight#8. Worked examples|4.2 §8]]).

## Related

- Parent lecture: [[SESA3043 4.2 - Rotor in Axial Flight]] · hover: [[SESA3043 4.1 - Rotor in Hover]]
- Related concepts: [[Rotor Working States in Axial Flight]] · [[Windmill Brake State]] · [[Autorotation]] · [[Induced Velocity in Forward Flight]] · [[Actuator Disk Theory]] (SESA2023)

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 43–56, 64, 67–68.
- Notes: written ahead from the slides, 17 Nov 2026; the climb and descent equations lectured Fri 20 Nov 2026 (`20 November 2026 at 14_51_19.txt`, ll. 391–590).

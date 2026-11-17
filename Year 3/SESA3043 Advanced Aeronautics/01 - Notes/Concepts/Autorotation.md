---
title: "Autorotation"
module: "SESA3043 Advanced Aeronautics"
type: concept
stream: "Chapter 4: Rotor Aerodynamics"
aliases: ["ideal autorotation", "autorotative descent", "zero total power descent"]
tags: [sesa3043, concept, rotor, descent]
status: complete
parent_lectures: ["[[SESA3043 4.2 - Rotor in Axial Flight]]"]
related_concepts: ["[[Rotor Working States in Axial Flight]]", "[[Induced Velocity in Axial Flight]]", "[[Vortex Ring State]]", "[[Windmill Brake State]]"]
sources: ["02 - Sources/Lectures/CH4 Rotor Aerodynamics.pdf"]
---

# Autorotation

Autorotation is a descent in which the rotor needs zero total power: the upward flow of air through the disc keeps it turning and carries the weight, with no engine.

In axial flight the induced-plus-descent power is $P=T(-V_D+v_i)$, so ideal autorotation (profile power left out) needs $v_i=V_D$, i.e. $\bar v_i=\bar V_D$. Momentum theory cannot give this point: substituting $\bar v_i=\bar V_D$ into the descent equation $\bar v_i^2-\bar V_D\bar v_i+1=0$ leaves $1=0$, and the climb equation gives $-1=0$. Zero net flow through the disc is exactly the condition under which no slipstream exists, so autorotation lies in the turbulent wake state, and its descent rate comes from test data: $\bar V_D\approx1.7$ for ideal and $\bar V_D\approx1.8$ for real autorotation, where the rotor must also supply its profile power, $V_D-v_i=P_{profile}/T>0$.

Treating the rotor as a drag-producing plate of disc area $A$ gives the same numbers. With $T=D=\tfrac12\rho V_D^2AC_D$ and $T=2\rho Av_0^2$,

$$
\bar V_D=\frac{2}{\sqrt{C_D}},
$$

and a bluff-plate $C_D$ of 1.23–1.38 gives 1.80–1.70. For the Lynx at 5330 kg ($v_0=12.9$ m/s) a vertical autorotation would descend at about 23 m/s, which is why real autorotations are flown with forward speed, near the minimum-power speed of [[Rotor Power Consumption]].

## Related

- Parent lecture: [[SESA3043 4.2 - Rotor in Axial Flight]]
- Related concepts: [[Rotor Working States in Axial Flight]] · [[Induced Velocity in Axial Flight]] · [[Windmill Brake State]] · [[Rotor Power Consumption]] · [[Glide Angle and Rate of Descent]] (SESA1015, the fixed-wing counterpart)

## Sources

- Sources: CH4 Rotor Aerodynamics, slides 52, 56, 65–66.
- Notes: written ahead from the slides, 17 Nov 2026.

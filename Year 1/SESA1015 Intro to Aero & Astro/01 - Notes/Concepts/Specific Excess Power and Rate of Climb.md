---
title: "Specific Excess Power and Rate of Climb"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Rate of climb", "Specific excess thrust", "Specific excess power", "Climb angle", "Best rate of climb"]
tags: [sesa1015, concept, climb]
status: complete
parent_lectures: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
related_concepts: ["[[Glide Angle and Rate of Descent]]", "[[Minimum Drag and Minimum Power]]", "[[Aircraft Constraint Diagram]]"]
sources: ["Mechanics of Flight Course Notes §7.2, pp. 37–38", "Mechanics of Flight Lecture Slides v2, pp. 133–141"]
---

# Specific Excess Power and Rate of Climb

The specific excess thrust $(T-D)/W$ is the sine of the steady climb angle, and the specific excess power $(T-D)V/W=(P_{av}-P_{req})/W$ is the steady rate of climb.

With climb angle $\theta$ and thrust inclined at $\gamma$ to the flight path, Newton's law along the path is $m\,dV/dt=T\cos\gamma-D-W\sin\theta$. Multiplying by $V/W$ and using $dh/dt=V\sin\theta$ gives the energy form

$$
\frac{(T\cos\gamma-D)V}{W}=\frac{dh}{dt}+\frac Vg\frac{dV}{dt},
$$

so excess power can be spent on climbing, on accelerating or on both, and with none at all height and speed can still be exchanged: $\Delta h=(V_1^2-V_2^2)/(2g)$, 229 m for slowing from 90 to 60 m s⁻¹. In a steady climb $\sin\theta=(T\cos\gamma-D)/W$ and $dh/dt=V(T\cos\gamma-D)/W$. For a shallow climb the speed and $C_L$ come from $L\approx W$, and for small angles $\theta\approx(T-D)/W$ in radians.

The best angle and the best rate come at different speeds. At constant thrust (a jet), $\sin\theta$ is largest where drag is least, so $(\sin\theta)_{max}=T/W-1/(L/D)_{max}$ at $V_{MD}$. The rate $V(T-D)/W$ also rewards speed, and is greatest at the lift coefficient

$$
C_{L_{\dot h_{max}}}=\frac{-(T/W)+\sqrt{(T/W)^2+12KC_{D0}}}{2K},
$$

which for a powerful jet is far below $C_{L_{MD}}$, so the best-rate speed is high: the Slides v2 jet with $T/W=0.429$ climbs fastest at 62.5 m s⁻¹ at 234 m s⁻¹ ($15.5^\circ$) and steepest at $19.8^\circ$ at 129 m s⁻¹. With constant power available, as for a propeller aircraft, the best rate is at the minimum-power speed.

The usual mistakes are dividing excess power by mass instead of weight, using degrees in $\theta\approx(T-D)/W$, and keeping $L\approx W$ for climbs steep enough that $\cos\theta$ is no longer close to 1.

## Related

- Topic: [[SESA1015 M08 - Glide and Climb Performance]] (derivations and worked examples) · Solutions: [[SESA1015 T05 - Climb and Glide Solutions]]
- Concepts: [[Glide Angle and Rate of Descent]] · [[Minimum Drag and Minimum Power]] · [[Parabolic Drag Polar]] · [[Aircraft Constraint Diagram]] (the climb constraint)
- Later: [[Phugoid Mode]] (the dynamic exchange of height and speed)

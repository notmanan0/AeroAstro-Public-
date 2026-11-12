---
title: "Glide Angle and Rate of Descent"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Glide ratio", "Glide angle", "Minimum sink", "Sink rate", "Best glide"]
tags: [sesa1015, concept, glide]
status: complete
parent_lectures: ["[[SESA1015 M08 - Glide and Climb Performance]]"]
related_concepts: ["[[Minimum Drag and Minimum Power]]", "[[Specific Excess Power and Rate of Climb]]", "[[Parabolic Drag Polar]]"]
sources: ["Mechanics of Flight Course Notes §7.1, pp. 36–37", "Mechanics of Flight Lecture Slides v2, pp. 142–144"]
---

# Glide Angle and Rate of Descent

In a steady glide without thrust the glide angle $\theta$ below the horizontal satisfies $\tan\theta=D/L$, and the rate of descent is $-dh/dt=V\sin\theta=DV/W$, the power required divided by the weight.

Both results come from resolving the weight along and normal to the flight path: $L=W\cos\theta$ and $D=W\sin\theta$. The angle depends only on the lift-to-drag ratio flown, so the distance covered from a height $h$ in still air is $hL/D$, the glide ratio times the height. It is greatest at $(L/D)_{max}$, the minimum-drag condition, where $C_L=\sqrt{C_{D0}/K}$, $C_D=2C_{D0}$ and $\theta_{min}\approx2\sqrt{KC_{D0}}$. Weight and altitude do not change this angle, only the speed at which it is flown.

The sink rate is a different optimum. With $L\approx W$ it is $\sqrt{2W/(\rho S)}\,C_D/C_L^{3/2}$, least at the minimum-power condition $C_L=\sqrt{3C_{D0}/K}$, $C_D=4C_{D0}$, where the angle is $(4/\sqrt3)\sqrt{KC_{D0}}$, 15 % steeper than the best glide, the speed is $3^{-1/4}V_{MD}=0.76V_{MD}$, and

$$
-\dot h_{min}=1.755\sqrt{\frac{2W}{\rho S}}\left(C_{D0}K^3\right)^{1/4}.
$$

Best glide gives the most distance, minimum sink the most time in the air. For the 15-tonne jet of Slides v2 ($C_D=0.013+0.157C_L^2$, $S=50$ m²) at sea level these are 11.63 m s⁻¹ at 129 m s⁻¹ and 10.19 m s⁻¹ at 98 m s⁻¹. An airliner with $(L/D)_{max}=18.1$ that loses its engines at 975 m glides $975\times18.1=17.6$ km.

The common trap is to fly minimum sink to reach a distant runway, or best glide to stay up longest; each answers the other question.

## Related

- Topic: [[SESA1015 M08 - Glide and Climb Performance]] (derivations, hodograph, worked examples)
- Concepts: [[Minimum Drag and Minimum Power]] · [[Specific Excess Power and Rate of Climb]] · [[Parabolic Drag Polar]] · [[Maximum Lift-to-Drag Ratio]]

---
title: "SESA1015 M08 - Glide and Climb Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 8
tags: [sesa1015, glide, climb, excess-power]
aliases: ["SESA1015 Mechanics 8", "Gliding and Climbing Flight"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
next_topics: ["[[SESA1015 M09 - Take-off and Landing Performance]]"]
key_concepts: ["[[Minimum Drag and Minimum Power]]"]
tutorial_sheets: ["[[SESA1015 T05 - Climb and Glide Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M08 - Glide and Climb Performance

> [!abstract] Summary
> A glide exchanges gravitational potential energy for the work needed to overcome drag; a climb uses propulsion to add potential energy. Force balance makes glide angle depend on $L/D$, while power balance makes sink rate depend on power required. In climb, excess thrust determines angle and excess power determines vertical speed. These pairs must not be mixed.

## 1. Steady glide

For a straight glide at constant speed with negligible thrust,

$$L=W\cos\gamma,\qquad D=W\sin\gamma$$

where $\gamma$ is the downward flight-path angle. Divide:

$$\boxed{\tan\gamma=\frac DL}.$$

For a shallow glide,

$$\frac{\text{horizontal distance}}{\text{height lost}}\approx\frac LD.$$

Thus maximum $L/D$ gives the shallowest angle and maximum still-air distance from a given height.

## 2. Sink rate

Vertical speed is

$$V_{sink}=V\sin\gamma\approx V\frac DL=\frac{DV}{W}=\frac{P_R}{W}.$$

Minimum sink therefore occurs at minimum power, not at minimum drag. It uses a lower speed and higher $C_L$ than best glide.

## 3. Wind effect

The aerodynamic optimum controls motion relative to the air. Ground range depends on wind:

- fly faster into a headwind to reduce exposure time;
- fly slower with a tailwind, subject to stall and handling limits.

The still-air best-glide ratio is not itself a ground-distance ratio in wind.

## 4. Steady climb

Resolve along and normal to the flight path:

$$T-D-W\sin\gamma=0,$$

$$L-W\cos\gamma=0.$$

Therefore

$$\boxed{\sin\gamma=\frac{T-D}{W}}.$$

For small $\gamma$, $\gamma\approx(T-D)/W$ in radians. Maximum climb angle occurs where excess thrust $T-D$ is greatest.

Multiply by speed:

$$W(V\sin\gamma)=TV-DV.$$

Hence

$$\boxed{ROC=\frac{P_A-P_R}{W}}.$$

Maximum rate of climb occurs where excess power is greatest.

## 5. Ceiling

As altitude rises, propulsion and aerodynamic performance change. The maximum rate of climb generally falls.

- At the **service ceiling**, maximum ROC equals a specified small positive value.
- At the **absolute ceiling**, maximum ROC is zero and the available and required curves are tangent.

## 6. Worked climb check

For $T=15.0\ \mathrm{kN}$, $D=4.0\ \mathrm{kN}$ and $W=42.0\ \mathrm{kN}$,

$$\sin\gamma=\frac{11}{42}=0.2619,$$

so $\gamma\approx15.2^\circ$. The small-angle estimate gives $0.2619$ rad $=15.0^\circ$, close here but no longer exact.

At $V=70\ \mathrm{m,s^{-1}}$,

$$ROC=70\sin(15.2^\circ)\approx18.3\ \mathrm{m,s^{-1}}.$$

## 7. Revision workflow

1. Draw the flight-path axes and assign the sign of $\gamma$.
2. Decide whether thrust can be neglected.
3. Use force balance for angle; use power balance for vertical speed.
4. If an angle exceeds roughly a few tens of degrees, avoid a small-angle approximation.
5. Check whether the stated speed is TAS.

> [!failure] Common errors
> - Using maximum $L/D$ for minimum sink.
> - Dividing excess power by mass instead of weight.
> - Entering degrees into a relation derived for radians.
> - Forgetting that $L<W$ in a finite glide or climb because $L=W\cos\gamma$.

## Year 2 bridge

- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] replaces constant available thrust/power with engine maps.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] treats accelerated climb and phugoid energy exchange.


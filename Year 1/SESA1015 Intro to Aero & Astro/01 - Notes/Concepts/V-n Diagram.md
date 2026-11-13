---
title: "V-n Diagram"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["V–n diagram", "Manoeuvre envelope", "Flight envelope", "V-n envelope"]
tags: [sesa1015, concept, load-factor, flight-envelope]
date: 2026-11-07
status: complete
parent_lectures: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
related_concepts: ["[[Load Factor and Turn Performance]]", "[[Wing Loading]]"]
sources: ["Mechanics of Flight Lecture Slides v2, pp. 178–179"]
---

# V-n Diagram

A V–n diagram plots the load factor an aircraft may pull against airspeed, for one weight and altitude (usually gross take-off weight with full payload and fuel). Its boundary is the flight envelope: inside it the aircraft can manoeuvre without stalling or overstressing the structure.

The left-hand boundaries are aerodynamic. The most lift available at speed $V$ is $\tfrac12\rho V^2SC_{L,max}$, so the largest load factor is

$$
n=\pm\frac{\tfrac12\rho V^2SC_{L,max}}{W},
$$

a parabola through the origin; the negative branch here uses the same magnitude of $C_{L,max}$, although real wings reach a smaller magnitude at negative incidence. Read the other way, $V=\sqrt{2nW/(\rho SC_{L,max})}$ is the stall speed at load factor $n$, which crosses $n=1$ at the ordinary stall speed. The horizontal boundaries are structural: the limit load factors $n_{max}$ and $n_{min}$ fixed by the certification authority, roughly $-1.5\le n\le3.8$ for transport aircraft and $-10\le n\le12$ for military aircraft. The right-hand boundary is a maximum speed, $V_{NE}$ in service; in the worked example it is the level-flight maximum speed from $T=D$ with the parabolic polar, $V_{max}^2=\big(T+\sqrt{T^2-4AB}\big)/(2A)$ with $A=\tfrac12\rho SC_{D0}$ and $B=2KW^2/(\rho S)$.

The positive stall parabola meets $n_{max}$ at the corner speed

$$
V_A=\sqrt{\frac{2n_{max}W}{\rho SC_{L,max}}}=V_S\sqrt{n_{max}}.
$$

Below $V_A$ the wing stalls before the structure reaches its limit, so a full pull cannot overstress the aircraft; above it the structure is the limit. In a level turn the same point gives the smallest turn radius and the fastest instantaneous turn rate ([[Load Factor and Turn Performance]]). The diagram says nothing about whether a load factor can be sustained: that depends on thrust, and is a separate limit inside the envelope.

For the military aircraft of Slides v2 p. 179 ($W/S=1500$ N/m², $S=8$ m², $C_{L,max}=2$, $n$ from $-10$ to 12, $T=15$ kN, $C_{D0}=0.015$, $K=0.06$, sea level), $V_{stall}=35.0$ m/s, the corners are at 121.2 m/s ($n=12$) and 110.7 m/s ($n=-10$), and $V_{max}=451.6$ m/s. That last value is Mach 1.33, beyond the incompressible drag model that produced it.

![[mof_m10_vn_diagram.png|850]]

## Related

- Topic: [[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]
- Concepts: [[Load Factor and Turn Performance]] · [[Wing Loading]] · [[Parabolic Drag Polar]]
- Later: [[Manoeuvre Point and Manoeuvre Margin]] (SESA2022)

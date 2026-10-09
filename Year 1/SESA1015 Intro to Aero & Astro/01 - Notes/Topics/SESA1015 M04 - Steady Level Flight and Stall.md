---
title: "SESA1015 M04 - Steady Level Flight and Stall"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 4
tags: [sesa1015, level-flight, stall, performance]
aliases: ["SESA1015 Mechanics 4", "Level Flight and Stall"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
next_topics: ["[[SESA1015 M05 - Minimum Drag, Power and Performance Curves]]"]
key_concepts: ["[[Wing Loading]]", "[[Parabolic Drag Polar]]"]
tutorial_sheets: ["[[SESA1015 T01 - Stall and Level-Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M04 - Steady Level Flight and Stall

> [!abstract] Summary
> In steady level flight, vertical and horizontal force balance reduce to $L=W$ and $T=D$. Lift balance converts speed into required $C_L$; the stall boundary occurs when that requirement reaches $C_{L,max}$. Combining lift balance with the parabolic drag polar produces the U-shaped thrust-required curve and allows one, two or no level-flight speeds for a specified available thrust.

## 1. Equilibrium

For unaccelerated, level flight with thrust aligned with the flight path,

$$\boxed{L=W},\qquad \boxed{T=D}.$$

Hence

$$C_L=\frac{W}{qS}=\frac{2W}{\rho V^2S}.$$

As speed falls, required $C_L$ rises as $1/V^2$.

## 2. Stall speed

The lowest speed supported by the available maximum lift coefficient satisfies

$$W=\frac12\rho V_s^2SC_{L,max}.$$

Therefore

$$\boxed{V_s=\sqrt{\frac{2W}{\rho SC_{L,max}}}=\sqrt{\frac{2(W/S)}{\rho C_{L,max}}}}.$$

This compact result exposes every first-order trend:

- $V_s\propto\sqrt W$: fuel burn reduces stall speed.
- $V_s\propto1/\sqrt\rho$: true stall speed rises with altitude.
- $V_s\propto1/\sqrt{C_{L,max}}$: high-lift devices reduce stall speed.
- $V_s\propto\sqrt{W/S}$: high wing loading raises stall speed.

> [!important] Stall is an angle-of-attack limit
> A given speed is not intrinsically a stall speed. The formula states the speed at which level-flight lift demand reaches $C_{L,max}$ for a particular weight, density and configuration.

## 3. Drag in level flight

Use $C_D=C_{D0}+kC_L^2$ and $C_L=2W/(\rho V^2S)$:

$$\boxed{D(V)=\frac12\rho V^2SC_{D0}+\frac{2kW^2}{\rho V^2S}}.$$

The first term grows with $V^2$; the second falls with $V^2$. Their sum is the thrust required for steady level flight.

![[mof_thrust_required_speed.png|760]]

At low speed, induced drag dominates; at high speed, parasite drag dominates. The minimum is where the two components are equal.

## 4. Level-flight speed for a given thrust

Let $x=V^2$. From $T_A=D$,

$$\frac12\rho SC_{D0}x^2-T_Ax+\frac{2kW^2}{\rho S}=0.$$

Thus

$$x=\frac{T_A\pm\sqrt{T_A^2-4kC_{D0}W^2}}{\rho SC_{D0}}.$$

and $V=\sqrt x$. The discriminant explains the physical cases:

- $T_A>D_{min}$: two mathematical speeds, one on each side of minimum drag.
- $T_A=D_{min}$: one tangency speed.
- $T_A<D_{min}$: no steady level-flight solution.

The low-speed root may be below stall and therefore physically unavailable.

## 5. Maximum level speed

Maximum level speed is found from the **high-speed** intersection of thrust available and thrust required. For a jet, thrust may be approximated constant only over a restricted condition. For a propeller aircraft, it is often better to compare power available and required.

## 6. Worked stall comparison

Two aircraft at the same density and stall speed have

$$\frac{C_{L,max,B}}{C_{L,max,A}}=\frac{(W/S)_B}{(W/S)_A}.$$

If their wing loadings are $4306$ and $3077\ \mathrm{N,m^{-2}}$,

$$\frac{C_{L,max,B}}{C_{L,max,A}}=1.3994.$$

Aircraft B therefore requires about 40% greater $C_{L,max}$. This is Revision Question 40; see [[SESA1015 T02 - Take-off and Landing Solutions]].

## 7. Solution workflow

1. Convert mass to weight.
2. Identify density, wing area and configuration.
3. Use lift balance to obtain required $C_L$.
4. Compare with $C_{L,max}$ before accepting a speed.
5. Use the drag polar to find $D=T_R$.
6. Compare with the appropriate thrust- or power-available model.

> [!failure] Common errors
> - Using mass in newtons or weight in kilograms.
> - Reporting the low-speed quadratic root without checking stall.
> - Assuming IAS and TAS are interchangeable at altitude.
> - Treating $C_{L,max}$ as the $C_L$ used at every speed.

## Year 2 bridge

- [[SESA2022 T2 - Boundary Layers]] explains why separation creates $C_{L,max}$.
- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] couples the drag curve to real engine behaviour and altitude.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] relaxes the steady, unaccelerated assumption.


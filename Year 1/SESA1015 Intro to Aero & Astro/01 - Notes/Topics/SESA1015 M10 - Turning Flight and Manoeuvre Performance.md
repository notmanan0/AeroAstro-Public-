---
title: "SESA1015 M10 - Turning Flight and Manoeuvre Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 10
tags: [sesa1015, turning-flight, bank-angle, load-factor]
aliases: ["SESA1015 Mechanics 10", "Turning Flight"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
next_topics: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
key_concepts: ["[[Load Factor and Turn Performance]]", "[[Wing Loading]]"]
tutorial_sheets: ["[[SESA1015 T06 - Turning Flight Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M10 - Turning Flight and Manoeuvre Performance

> [!abstract] Summary
> Banking tilts lift. Its vertical component must still support weight in a level turn, so total lift and load factor rise. The horizontal component supplies centripetal acceleration. This gives exact relations among bank angle, load factor, turn radius and turn rate, while the increased lift demand raises stall speed and drag. The tightest sustainable turn is limited jointly by lift, structure and thrust.

## 1. Coordinated level turn

Resolve lift at bank angle $\phi$:

$$L\cos\phi=W,$$

$$L\sin\phi=\frac{mV^2}{R}.$$

The load factor is

$$\boxed{n=\frac LW=\frac{1}{\cos\phi}}.$$

Divide the force equations:

$$\tan\phi=\frac{V^2}{gR}.$$

Therefore

$$\boxed{R=\frac{V^2}{g\tan\phi}=\frac{V^2}{g\sqrt{n^2-1}}}.$$

Turn rate is

$$\boxed{\dot\psi=\frac VR=\frac{g\tan\phi}{V}=\frac{g\sqrt{n^2-1}}{V}}.$$

![[mof_turn_radius.png|760]]

## 2. Accelerated stall

Required lift is $nW$. At $C_{L,max}$,

$$nW=\frac12\rho V_{s,n}^2SC_{L,max}.$$

Compare with the 1-g stall condition:

$$\boxed{V_{s,n}=V_s\sqrt n}.$$

At $60^\circ$ bank, $n=2$ and stall speed rises by $\sqrt2\approx1.414$.

![[mof_load_factor_bank.png|760]]

## 3. Drag in a turn

At a fixed speed, the lift coefficient becomes

$$C_L=\frac{nW}{qS}.$$

Then

$$D=qSC_{D0}+qSkC_L^2
=qSC_{D0}+\frac{k(nW)^2}{qS}.$$

Induced drag grows with $n^2$. A bank angle allowed by lift or structure may not be sustainable with the available thrust.

## 4. Three limits

1. **Aerodynamic:** $C_L\le C_{L,max}$.
2. **Structural:** $n\le n_{limit}$.
3. **Propulsive:** $D(V,n)\le T_A(V,h)$.

The achievable load factor at a given speed is the smallest value allowed by the three. This is the logic behind a manoeuvre or V–n envelope.

## 5. Minimum radius is not always at minimum speed

For fixed $n$, $R\propto V^2$, suggesting a slower turn is tighter. But slow speed reduces the maximum lift-limited $n$. Near stall, increasing speed can enable a much greater $n$. Find the true optimum from the active constraints rather than applying one trend outside its domain.

## 6. Worked bank-angle check

For a coordinated level turn at $\phi=45^\circ$ and $V=80\ \mathrm{m,s^{-1}}$,

$$n=\frac{1}{\cos45^\circ}=1.414,$$

$$R=\frac{80^2}{9.81\tan45^\circ}\approx652\ \mathrm m,$$

$$\dot\psi=\frac{9.81}{80}=0.1226\ \mathrm{rad,s^{-1}}=7.02^\circ\mathrm{/s}.$$

If the 1-g stall speed is $40\ \mathrm{m,s^{-1}}$, the turn stall speed is $40\sqrt{1.414}=47.6\ \mathrm{m,s^{-1}}$, so the chosen speed clears the lift boundary.

## 7. Workflow

1. Confirm whether the turn is level, coordinated and steady.
2. Convert bank angle to load factor.
3. Apply radius/rate relations.
4. Check accelerated stall.
5. Check structural $n$.
6. Evaluate drag/thrust if the turn must be sustained.

> [!failure] Common errors
> - Using $L=W$ in a banked level turn.
> - Using degrees in calculator trig while set to radians or vice versa.
> - Treating instantaneous lift limit as a sustained-turn result.
> - Forgetting that turn rate uses radians per second before conversion.

## Year 2 bridge

- [[SESA2022 T5 - Finite Wing Theory]] explains the induced-drag cost of the higher lift.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] generalises to non-level and time-varying manoeuvres.
- [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] shows how static flight conditions differ from dynamic modal response.

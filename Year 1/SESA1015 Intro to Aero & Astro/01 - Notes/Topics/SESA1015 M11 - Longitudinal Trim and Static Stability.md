---
title: "SESA1015 M11 - Longitudinal Trim and Static Stability"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 11
tags: [sesa1015, trim, static-stability, pitching-moment]
aliases: ["SESA1015 Mechanics 11", "Longitudinal Stability"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
next_topics: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
key_concepts: ["[[Static Margin and Tail Volume]]", "[[Neutral Point and Static Margin]]"]
tutorial_sheets: ["[[SESA1015 T07 - Trim and Static Stability Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M11 - Longitudinal Trim and Static Stability

> [!abstract] Summary
> **Trim** means zero net pitching moment at a chosen operating point; **static stability** asks whether a small angle-of-attack disturbance initially creates a restoring moment. They are separate requirements. A conventional tail supplies a moment arm that lets the aircraft trim and moves the neutral point aft. The centre of gravity must remain ahead of that neutral point for positive static margin, but excessive margin increases control force and trim demand.

## 1. Trim versus stability

For a linear moment model,

$$C_m=C_{m0}+C_{m_\alpha}\alpha+C_{m_{\delta_e}}\delta_e.$$

Trim requires $C_m=0$:

$$\boxed{\alpha_{trim}=-\frac{C_{m0}+C_{m_{\delta_e}}\delta_e}{C_{m_\alpha}}}.$$

Static stability requires

$$\boxed{C_{m_\alpha}<0}.$$

An aircraft can be stable but not trimmed at the current control setting, or trimmed but unstable.

![[mof_static_stability.png|760]]

## 2. Disturbance test

If $\alpha$ increases slightly:

- stable: $\Delta C_m<0$, a nose-down restoring tendency;
- neutral: $\Delta C_m=0$;
- unstable: $\Delta C_m>0$, a nose-up amplifying tendency.

This is an initial tendency only. Dynamic stability also depends on inertia and damping.

## 3. Wing moment and centre of gravity

Moving the CG changes the moment arm of lift. A forward CG generally increases static stability but requires more tail/elevator moment to trim. An aft CG reduces trim drag and control force but erodes the restoring tendency.

Moment transfer gives the basic relation

$$C_{m,CG}=C_{m,AC}+C_L\left(\frac{x_{CG}-x_{AC}}{\bar c}\right)$$

for the compatible sign convention. Differentiate with respect to $\alpha$ to see how CG location affects $C_{m_\alpha}$.

## 4. Tail volume

The horizontal-tail volume coefficient is

$$\boxed{V_H=\frac{S_Tl_T}{S\bar c}}.$$

It packages tail area and moment arm relative to wing size. The tail contribution to moment scales roughly with $V_HC_{L_T}$, modified by tail efficiency and downwash.

A longer arm can produce the same moment with less tail force, but geometry, structure, mass and packaging constrain it.

## 5. Neutral point and static margin

The neutral point is the CG position at which $C_{m_\alpha}=0$. Define

$$\boxed{SM=\frac{x_{NP}-x_{CG}}{\bar c}}.$$

- $SM>0$: CG ahead of neutral point, statically stable.
- $SM=0$: neutral.
- $SM<0$: unstable.

A useful linear identity is

$$C_{m_\alpha}\approx-C_{L_\alpha}SM.$$

The exact neutral-point model includes wing-body aerodynamics, tail lift-curve slope, downwash, tail efficiency and volume.

## 6. Trim force balance

For straight flight,

$$L_W+L_T=W$$

under the simple vertical-force model. Moment balance about the CG can be written schematically as

$$M_{ac,W}+L_W(x_{CG}-x_{ac,W})-L_Tl_T=0$$

with signs chosen from the sketch. Solve force and moment equations together: assuming $L_W=W$ while also using a nonzero tail force double-counts the vertical balance.

## 7. Elevator and trim drag

Elevator deflection changes tail lift and shifts the $C_m$ line, allowing a new trim point. A tail force implies additional lift demand and induced drag. This is why CG location and trim schedule affect performance.

## 8. Worked linear-model check

If

$$C_m=0.06-0.80\alpha-1.10\delta_e$$

with angles in radians, and $\delta_e=-2^\circ=-0.03491\ \mathrm{rad}$, then

$$\alpha_{trim}=-\frac{0.06-1.10(-0.03491)}{-0.80}=0.1230\ \mathrm{rad}=7.05^\circ.$$

Since $C_{m_\alpha}=-0.80<0$, this trim point is statically stable within the linear range.

## 9. Workflow

1. Write the coefficient sign conventions.
2. Solve force balance and moment balance together.
3. Set $C_m=0$ for trim.
4. Inspect $dC_m/d\alpha$ for static stability.
5. Locate CG relative to neutral point.
6. Check control authority and plausible deflection.

> [!failure] Common errors
> - Calling $C_m=0$ “stable”.
> - Ignoring the tail contribution to total lift.
> - Mixing dimensional moment with $C_m$ without $qS\bar c$.
> - Moving a moment between points with an unexamined sign.

## Year 2 bridge

- [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]] derives trim, downwash, stick-fixed/free neutral points and manoeuvre stability.
- [[Neutral Point and Static Margin]] provides the more complete second-year relation.
- [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]] turns static derivatives into a state-space model.
- [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]] distinguishes static stability from the phugoid and short-period modes.

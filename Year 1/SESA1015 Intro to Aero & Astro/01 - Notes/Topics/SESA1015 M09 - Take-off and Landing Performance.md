---
title: "SESA1015 M09 - Take-off and Landing Performance"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 9
tags: [sesa1015, takeoff, landing, ground-run]
aliases: ["SESA1015 Mechanics 9", "Take-off and Landing"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M04 - Steady Level Flight and Stall]]"]
next_topics: ["[[SESA1015 M10 - Turning Flight and Manoeuvre Performance]]"]
key_concepts: ["[[Take-off Ground Run]]", "[[Wing Loading]]"]
tutorial_sheets: ["[[SESA1015 T02 - Take-off and Landing Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M09 - Take-off and Landing Performance

> [!abstract] Summary
> The take-off ground roll is a variable-acceleration problem. Thrust accelerates the aircraft; drag and rolling friction oppose it; growing lift unloads the wheels and reduces friction. Lift-off speed is tied to stall speed, so density, wing loading and $C_{L,max}$ affect both the target speed and the forces available on the way there. Landing reverses the energy problem: approach margins, touchdown kinetic energy, aerodynamic drag, braking and runway condition determine distance.

## 1. Take-off phases

1. Ground roll from rest to rotation.
2. Rotation and lift-off.
3. Transition to climb.
4. Climb to the obstacle/reference height.

Do not call the ground run the complete take-off distance unless the source defines it that way.

## 2. Ground-roll force balance

Along a level runway,

$$m\dot V=T-D-F_R$$

with rolling resistance

$$F_R=\mu N=\mu(W-L).$$

Therefore

$$\boxed{m\dot V=T-D-\mu(W-L)}.$$

Use

$$L=\frac12\rho V^2SC_L,\qquad D=\frac12\rho V^2SC_D.$$

The acceleration is not constant because lift and drag grow with $V^2$, and thrust may vary with speed.

## 3. Distance integral

Since $\dot V=V\,dV/ds$,

$$ds=\frac{mV\,dV}{T-D-\mu(W-L)}.$$

For constant $T,C_L,C_D$, define

$$A=T-\mu W,\qquad B=\frac12\rho S(C_D-\mu C_L).$$

Then

$$s_g=\int_0^{V_{LOF}}\frac{mV\,dV}{A-BV^2}
=\boxed{\frac{m}{2B}\ln\left(\frac{A}{A-BV_{LOF}^2}\right)}.$$

If the assumptions are not credible, integrate numerically using speed-dependent thrust and coefficients.

![[mof_takeoff_ground_run.png|760]]

## 4. Lift-off speed

$$V_s=\sqrt{\frac{2W}{\rho SC_{L,max}}},\qquad V_{LOF}=K_{LOF}V_s$$

where $K_{LOF}$ is supplied by the question or operating rule. Because distance grows roughly with target speed squared when acceleration is comparable, even a modest speed increase can strongly lengthen the roll.

## 5. Parameter effects

| Change | First-order effect |
|---|---|
| higher weight | higher lift-off speed; more inertia; longer distance |
| lower density | higher TAS at lift-off; often less engine thrust; longer distance |
| larger $C_{L,max}$ | lower lift-off speed; usually shorter distance |
| larger wing area | lower wing loading and speed; may add drag/structure |
| runway upslope | adds opposing component of weight |
| headwind | lowers ground speed/distance to reach required airspeed |
| wet/contaminated runway | changes rolling/braking behaviour and safety margins |

## 6. Landing model

The approach speed is tied to stall speed by a margin. After touchdown, kinetic energy is

$$KE=\frac12mV_{TD}^2.$$

Brakes, aerodynamic drag, reverse thrust and runway slope dissipate this energy. Lift after touchdown reduces wheel normal force and may delay full braking; spoilers deliberately dump lift.

A constant-deceleration estimate is

$$s\approx\frac{V_{TD}^2}{2a_{dec}}$$

but certification distances incorporate operational margins and failure cases beyond this simple mechanics model.

## 7. Comparing high-lift systems

From the stall equation,

$$C_{L,max}=\frac{2(W/S)}{\rho V_s^2}.$$

For equal density and stall speed,

$$\frac{C_{L,max,B}}{C_{L,max,A}}=\frac{(W/S)_B}{(W/S)_A}.$$

This is a powerful comparison because mass and area need not be separated if wing loading is supplied.

## 8. Solution workflow

1. Determine $V_s$ and the required lift-off/approach factor.
2. Write the runway-axis force balance including the correct normal force.
3. Decide whether a constant-acceleration estimate is explicitly permitted.
4. Otherwise integrate $mV/(\text{net force})$ over speed.
5. Separate ground roll from airborne/obstacle distance.
6. Perform trend checks for weight, density and $C_{L,max}$.

> [!failure] Common errors
> - Taking rolling resistance as $\mu W$ after lift has developed.
> - Using stall speed itself as lift-off speed when a margin is stated.
> - Mixing airspeed and ground speed in wind.
> - Holding acceleration constant without declaring the approximation.

## Year 2 bridge

- [[SESA2022 T2 - Boundary Layers]] explains separation and high-lift behaviour.
- [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] supplies thrust lapse and density-altitude effects.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] provides the transient equations for rotation and transition.


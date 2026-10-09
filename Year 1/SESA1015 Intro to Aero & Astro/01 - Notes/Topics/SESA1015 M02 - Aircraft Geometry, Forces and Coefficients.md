---
title: "SESA1015 M02 - Aircraft Geometry, Forces and Coefficients"
module: "SESA1015 Intro to Aero & Astro"
type: topic
stream: "Mechanics of Flight"
order: 2
tags: [sesa1015, aircraft-geometry, forces, coefficients]
aliases: ["SESA1015 Mechanics 2", "Aircraft Forces and Coefficients"]
date: 2026-09-27
status: complete
parent: ["[[SESA1015 Intro to Aero & Astro Hub]]"]
prerequisites: ["[[SESA1015 M01 - Atmosphere, Airspeed and Mach Number]]"]
next_topics: ["[[SESA1015 M03 - Aerodynamic Characteristics and the Drag Polar]]"]
key_concepts: ["[[Dynamic Pressure and Aerodynamic Coefficients]]", "[[Wing Loading]]"]
tutorial_sheets: ["[[SESA1015 T03 - Wind-Tunnel Data Reduction Solutions]]"]
sources: ["02 - Sources/Mechanics of Flight/Mechanics of Flight - Course Notes.pdf", "02 - Sources/Mechanics of Flight/Mechanics of Flight - Lecture Slides version 2.pdf"]
---

# SESA1015 M02 - Aircraft Geometry, Forces and Coefficients

> [!abstract] Summary
> Flight mechanics separates a vehicle into geometry, state and dimensionless aerodynamic behaviour. Geometry supplies reference area $S$, span $b$ and chord $\bar c$; the state supplies $q$; coefficients encode shape, attitude and flow regime. A correct free-body diagram then turns those ingredients into force and moment balance. This separation makes wind-tunnel models and full-scale aircraft comparable.

## 1. Reference geometry

| Quantity | Definition | Why it matters |
|---|---|---|
| Planform area $S$ | projected wing area | reference for lift and drag |
| Span $b$ | tip-to-tip distance | induced drag and roll scale |
| Mean aerodynamic chord $\bar c$ | representative chord | moment and CG reference |
| Aspect ratio $AR$ | $b^2/S$ | finite-wing efficiency |
| Taper ratio $\lambda$ | $c_t/c_r$ | loading and structure |
| Sweep $\Lambda$ | reference-line angle | compressibility and stability |
| Dihedral $\Gamma$ | wing tilt from horizontal | lateral stability |

The wing area convention must match the stated coefficients. Gross planform area often includes the portion inside the fuselage; wetted area is a different quantity used in drag estimation.

## 2. Coordinate systems and angles

- **Body axes** are fixed to the aircraft: $x$ forward, $y$ starboard, $z$ downward in the common aerospace convention.
- **Wind axes** align $x$ with the relative wind; lift is perpendicular and drag parallel to the flight path.
- Angle of attack $\alpha$ lies between body/chord direction and relative wind.
- Sideslip $\beta$ measures lateral misalignment.
- Flight-path angle $\gamma$ lies between velocity and the horizontal.
- Pitch attitude satisfies $\theta=\alpha+\gamma$ for the usual planar convention.

> [!warning] A sign convention is part of the model
> Draw the axes and positive moments before writing an equation. A memorised pitching-moment equation can change sign when the $z$ axis or elevator convention changes.

## 3. Forces and moments

The four familiar forces are weight $W$, lift $L$, drag $D$ and thrust $T$. Their directions are not automatically perpendicular pairs:

- Weight is vertical in an inertial frame.
- Lift and drag follow the wind axes.
- Thrust follows the engine installation line.

The aerodynamic resultant can be resolved into lift and drag, or normal and axial forces. Pitching moment depends on the reference point.

## 4. Non-dimensional coefficients

[[Dynamic Pressure and Aerodynamic Coefficients|Dynamic pressure]] gives the natural force scale:

$$L=qSC_L,\qquad D=qSC_D.$$

Moment needs an extra length:

$$M=qS\bar c\,C_m.$$

Similarly, rolling and yawing moments use $qSb$:

$$\mathcal L=qSbC_l,\qquad N=qSbC_n.$$

The same $C_L$ does not guarantee the same lift unless $q$ and $S$ also match. Conversely, a wind-tunnel model and an aircraft can have comparable coefficients when their relevant similarity parameters match.

## 5. Reynolds and Mach similarity

$$Re=\frac{\rho Vc}{\mu},\qquad M=\frac{V}{a}.$$

- Reynolds number compares inertial and viscous effects; it influences boundary layers, separation and profile drag.
- Mach number compares flow speed with acoustic propagation; it controls compressibility effects.

Matching both $Re$ and $M$ in a small low-speed tunnel may be impossible. Engineering data therefore always carry a test-condition envelope.

## 6. Centre of pressure and aerodynamic centre

The centre of pressure is the point where the resultant aerodynamic force produces zero pitching moment. Its position can move strongly as $C_L$ changes.

The aerodynamic centre is more useful: pitching moment about it is approximately independent of $\alpha$ over the linear range.

Moment transfer between two chordwise points gives

$$M_2=M_1+L(x_2-x_1)$$

with the algebraic sign determined by the adopted axes. In coefficient form,

$$C_{m,2}=C_{m,1}+C_L\frac{x_2-x_1}{\bar c}.$$

This relation is the bridge from measured aerofoil moments to aircraft trim.

## 7. Wing loading

$$\boxed{\frac WS}$$

is a compact design variable. At a given $q$,

$$C_L=\frac{W/S}{q}.$$

High wing loading tends to increase stall and take-off speed but can reduce sensitivity to gusts and wing area. Low wing loading generally helps low-speed performance but requires more wing structure and wetted area.

## 8. Worked coefficient check

For $m=1200\ \mathrm{kg}$, $S=16\ \mathrm{m^2}$, $V=55\ \mathrm{m,s^{-1}}$ and $\rho=1.0\ \mathrm{kg,m^{-3}}$ in level flight,

$$q=1512.5\ \mathrm{Pa},\qquad C_L=\frac{1200(9.81)}{1512.5(16)}\approx0.486.$$

If $C_D=0.036$, then

$$D=qSC_D\approx871\ \mathrm N.$$

The dimensions and state disappear from $C_L$ and $C_D$, but return when forces are required.

## 9. Free-body workflow

1. Choose axes suited to the motion.
2. Place every external force at its line of action.
3. Mark $\alpha$, $\gamma$, bank and control deflections.
4. Write force balance before substituting coefficient models.
5. Take moments about the point that removes the most unknowns.
6. Check the limiting case: level flight should reduce to $L=W$, $T=D$.

## Year 2 bridge

- [[SESA2022 T3 - Potential Flow]] explains how pressure fields create forces.
- [[SESA2022 T4 - Thin Aerofoil Theory]] derives lift slope and aerodynamic-centre behaviour.
- [[SESA2022 T5 - Finite Wing Theory]] connects aspect ratio to induced drag and downwash.
- [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] turns static free-body diagrams into six-degree-of-freedom dynamics.


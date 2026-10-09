---
title: "SESA1016 T10 - Euler and Bernoulli Equations"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part C: Fluid Motion and Inviscid Flow"
order: 10
tags: [sesa1016, euler-equation, bernoulli, pitot, pressure-coefficient]
aliases: ["Bernoulli Equation"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T9 - Describing Flow and the Material Derivative]]"]
next_topics: ["[[SESA1016 T11 - Conservation of Mass]]"]
key_concepts: ["[[Bernoulli Equation]]", "[[Stagnation Pressure and Pitot Tube]]", "[[Pressure Coefficient]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]]", "[[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 10.pdf"]
---

# SESA1016 T10 - Euler and Bernoulli Equations

> [!abstract] Summary
> Newton's second law applied to an inviscid fluid particle gives Euler's equation. For steady, incompressible flow, integrating along a streamline yields Bernoulli: static pressure, kinetic-energy density and gravitational potential-energy density trade with one another. It is a mechanical-energy relation with strict assumptions, not a universal pressure formula.

## 1. Acceleration along a streamline

For steady one-dimensional motion along coordinate $s$:

$$
a_s=V\frac{dV}{ds}.
$$

The flow can accelerate even though the field is steady because neighbouring locations have different speeds.

## 2. Euler equation

Balance pressure and gravity against inertia along a streamline:

$$
\boxed{\rho V\,dV=-dp-\rho g\,dz}.
$$

This neglects viscous shear. It is valid in an inviscid region outside boundary layers and wakes, or as an approximation when losses are negligible.

## 3. Bernoulli equation

For constant $\rho$, integrate Euler:

$$
\boxed{p+\frac12\rho V^2+\rho gz=\mathrm{constant\ along\ a\ streamline}}
$$

Equivalent head form:

$$
\frac p{\rho g}+\frac{V^2}{2g}+z=H.
$$

![[tf_bernoulli_contraction.png|720]]

### Assumption gate

Before using Bernoulli, check:

1. steady flow;
2. incompressible or negligible density change;
3. inviscid along the path;
4. no pump/turbine work or heat-driven density effects between chosen points;
5. same streamline, unless the flow is irrotational.

If any fail, use the steady-flow energy equation with work and loss terms.

## 4. Static, dynamic and stagnation pressure

At a stagnation point $V_0=0$ at the same elevation:

$$
\boxed{p_0=p+\frac12\rho V^2}.
$$

- static pressure $p$: thermodynamic pressure moving with the flow;
- dynamic pressure $q=\tfrac12\rho V^2$: kinetic-energy density scale;
- stagnation pressure $p_0$: pressure after ideal deceleration to rest.

See [[Stagnation Pressure and Pitot Tube]].

## 5. Pressure measurement

- **Pressure tap** aligned with a wall measures static pressure if it does not disturb the flow.
- **Stagnation tube** facing the flow measures $p_0$.
- **Pitot-static tube** measures $p_0-p$ and therefore

$$
V=\sqrt{\frac{2(p_0-p)}\rho}.
$$

## 6. Pressure coefficient

$$
\boxed{C_p=\frac{p-p_\infty}{\tfrac12\rho V_\infty^2}}
$$

In incompressible inviscid flow at the same height:

$$
C_p=1-\left(\frac V{V_\infty}\right)^2.
$$

$C_p=1$ at an ideal stagnation point; $C_p<0$ where local speed exceeds freestream speed.

## 7. Typical pairings

Bernoulli alone often lacks a velocity. Combine it with:

- continuity $A_1V_1=A_2V_2$ for an incompressible streamtube;
- hydrostatics to convert a manometer height into pressure difference;
- a known free-surface pressure and negligible reservoir speed;
- an imposed pressure coefficient.

## Links

- Concepts: [[Bernoulli Equation]] · [[Stagnation Pressure and Pitot Tube]] · [[Pressure Coefficient]]
- Tutorials: [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]] · [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]
- Continues in Aerodynamics/CFD: [[SESA2022 T3 - Potential Flow]] · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]]
- Next: [[SESA1016 T11 - Conservation of Mass]]

## Sources

- `02 - Sources/Lectures/Chapter 10.pdf`, §§10.1-10.6.

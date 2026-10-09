---
title: "SESA1016 T11 - Conservation of Mass"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 11
tags: [sesa1016, continuity, mass-flow, control-volume]
aliases: ["Conservation of Mass", "Continuity"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T10 - Euler and Bernoulli Equations]]"]
next_topics: ["[[SESA1016 T12 - Conservation of Momentum]]"]
key_concepts: ["[[Mass Flow Rate]]", "[[Control-volume Analysis Workflow]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 11.pdf"]
---

# SESA1016 T11 - Conservation of Mass

> [!abstract] Summary
> Mass can accumulate inside a control volume or cross its boundary, but it cannot be created. Flow rate is a surface flux: integrate the normal velocity over an area. For steady one-dimensional ports, continuity becomes the familiar statement that total inlet mass flow equals total outlet mass flow.

## 1. Volume flow rate

For velocity normal to a differential area:

$$
d\dot V=V_n\,dA.
$$

Therefore

$$
\boxed{\dot V=\int_A\mathbf V\cdot\mathbf n\,dA}.
$$

If the velocity is uniform, $\dot V=VA$. For a nonuniform profile define area-mean velocity

$$
\bar V=\frac1A\int_AV_n\,dA
$$

so that $\dot V=\bar VA$ remains exact by definition.

## 2. Mass flow rate

$$
\boxed{\dot m=\int_A\rho\mathbf V\cdot\mathbf n\,dA}.
$$

For uniform density and velocity:

$$
\dot m=\rho VA.
$$

For compressible nonuniform flow, $\rho$ must remain inside the integral. See [[Mass Flow Rate]].

## 3. General control-volume balance

With outward normal $\mathbf n$:

$$
\boxed{\frac{d}{dt}\int_{CV}\rho\,dV+int_{CS}\rho\mathbf V\cdot\mathbf n\,dA=0}.
$$

- first term: mass accumulation inside the control volume;
- second term: net outward mass flow across the control surface.

## 4. Steady flow

No mass accumulates:

$$
\boxed{\sum\dot m_{in}=\sum\dot m_{out}}.
$$

For a single incompressible streamtube:

$$
A_1V_1=A_2V_2.
$$

A contraction therefore accelerates the flow. Density changes modify this to $\rho_1A_1V_1=\rho_2A_2V_2$.

## 5. Multiple ports

Assign each port an inlet or outlet role based on $\mathbf V\cdot\mathbf n$. For a tee:

$$
\dot m_1=\dot m_2+\dot m_3.
$$

Do not conserve volume flow when streams have different densities; conserve mass.

![[tf_control_volume_balances.png|760]]

## 6. Velocity-profile integration

For a two-dimensional channel of width $b$ and profile $u(y)$:

$$
\dot V=b\int u(y)\,dy,qquad \dot m=b\int\rho(y)u(y)\,dy.
$$

For an axisymmetric pipe:

$$
\dot V=2\pi\int_0^Ru(r)r\,dr.
$$

The area element is $dA=2\pi r\,dr$, not $dr$.

## 7. Workflow

1. Draw the control volume.
2. Label port area, density, mean normal velocity and flow direction.
3. Decide whether storage is zero.
4. Write the general balance, then reduce it.
5. Check that mass units are $\mathrm{kg/s}$.

## Links

- Concepts: [[Mass Flow Rate]] · [[Control-volume Analysis Workflow]]
- Tutorial: [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]]
- Continues in CFD: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[SESA2029 A9 - Finite Volume Method]]
- Next: [[SESA1016 T12 - Conservation of Momentum]]

## Sources

- `02 - Sources/Lectures/Chapter 11.pdf`, §§11.1-11.4.

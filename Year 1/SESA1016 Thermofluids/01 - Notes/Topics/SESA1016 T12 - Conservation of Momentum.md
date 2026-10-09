---
title: "SESA1016 T12 - Conservation of Momentum"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 12
tags: [sesa1016, momentum, force, control-volume, thrust]
aliases: ["Conservation of Momentum"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T11 - Conservation of Mass]]"]
next_topics: ["[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
key_concepts: ["[[Momentum Flux]]", "[[Control-volume Analysis Workflow]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 12.pdf"]
---

# SESA1016 T12 - Conservation of Momentum

> [!abstract] Summary
> Momentum is a vector. A control volume gains momentum through accumulation or net momentum flux, and external forces cause that change. The hardest part is rarely the formula; it is drawing the correct free-body diagram, retaining pressure forces and reporting the force on the requested object rather than its equal-and-opposite partner.

## 1. Momentum flux

Mass flow $\dot m$ carrying velocity $\mathbf V$ transports momentum at rate

$$
\dot{\mathbf M}=\dot m\mathbf V.
$$

The general flux integral is

$$
\int_{CS}\rho\mathbf V(\mathbf V\cdot\mathbf n)\,dA.
$$

See [[Momentum Flux]].

## 2. Control-volume momentum equation

In an inertial frame:

$$
\boxed{\sum\mathbf F=\frac{d}{dt}\int_{CV}\rho\mathbf V\,dV+
\int_{CS}\rho\mathbf V(\mathbf V\cdot\mathbf n)\,dA}.
$$

For steady uniform ports:

$$
\boxed{\sum\mathbf F=\sum_{out}\dot m\mathbf V-sum_{in}\dot m\mathbf V}.
$$

Write separate $x$, $y$ and $z$ component equations.

## 3. External forces to include

- pressure force $-p\mathbf nA$ at every cut port;
- wall/support reaction on the fluid;
- weight of fluid within the control volume;
- imposed body forces where relevant;
- atmospheric pressure, or use gauge pressure consistently so it cancels.

> [!warning] Reaction direction
> The momentum equation usually gives the force **of the pipe/support/body on the fluid**. The force of the fluid on the hardware is its negative.

## 4. Jets and thrust

For a steady single jet with inlet and exit velocities aligned:

$$
F=\dot m(V_e-V_i)+(p_e-p_a)A_e.
$$

If $p_e=p_a$, pressure thrust is zero. A stationary rocket test stand still experiences thrust because exhaust momentum leaves the control volume.

## 5. Impinging jet

If a jet is brought to rest in its incoming direction, the target must supply approximately

$$
F=\dot mV=\rho AV^2
$$

in that direction, neglecting pressure and gravity. If the flow is turned rather than stopped, use vector outlet momentum.

## 6. Pipe bend

For a 90-degree bend:

1. calculate $\dot m$ from continuity;
2. write $\mathbf V_1$ and $\mathbf V_2$ in components;
3. draw pressure forces on inlet/outlet faces;
4. include fluid weight if requested;
5. solve for wall force on fluid;
6. reverse sign for fluid force on bend/support.

## 7. Nonuniform profiles

Momentum flux involves $u^2$, not $(\bar u)^2$:

$$
\int_A\rho u^2\,dA=\beta\rho A\bar V^2,
$$

where $\beta$ is the momentum correction factor. For uniform profiles $\beta=1$; for fully developed laminar circular-pipe flow $\beta=4/3$.

## 8. Wake drag

For a two-dimensional wake with equal far-upstream and far-downstream static pressure:

$$
D'=\rho\int u(U_\infty-u)\,dy.
$$

The momentum deficit captures the total drag responsible for the wake.

## Links

- Concepts: [[Momentum Flux]] · [[Control-volume Analysis Workflow]]
- Tutorial: [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]
- Continues in Propulsion/CFD: [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · [[Thrust Equation]] · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[SESA2029 A9 - Finite Volume Method]]
- Next: [[SESA1016 T13 - Conservation of Energy and Propulsion]]

## Sources

- `02 - Sources/Lectures/Chapter 12.pdf`, §§12.1-12.6.

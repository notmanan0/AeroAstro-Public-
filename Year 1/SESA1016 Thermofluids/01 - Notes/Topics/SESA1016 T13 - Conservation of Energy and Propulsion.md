---
title: "SESA1016 T13 - Conservation of Energy and Propulsion"
module: "SESA1016 Thermofluids"
type: topic
stream: "Part D: Control-volume Conservation Laws"
order: 13
tags: [sesa1016, energy, sfee, propulsion, reynolds-transport]
aliases: ["Conservation of Energy for Flow", "SFEE"]
date: 2026-09-25
status: complete
parent: ["[[SESA1016 Thermofluids Hub]]"]
prerequisites: ["[[SESA1016 T12 - Conservation of Momentum]]"]
next_topics: ["[[SESA1016 T14 - Boundary Layers and the Origin of Drag]]"]
key_concepts: ["[[Steady-flow Energy Equation]]", "[[Control-volume Analysis Workflow]]"]
tutorial_sheets: ["[[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 13.pdf"]
---

# SESA1016 T13 - Conservation of Energy and Propulsion

> [!abstract] Summary
> Flow carries internal, kinetic and potential energy. Pressure work combines with internal energy to form enthalpy, which is why $h+V^2/2+gz$ is the natural transported energy per unit mass. The steady-flow energy equation balances that transport against heat and shaft work and is the correct tool for nozzles, compressors, turbines, heaters and complete propulsion systems.

## 1. Energy carried by moving fluid

Per unit mass:

$$
e=u+\frac{V^2}{2}+gz.
$$

Fluid crossing a control surface must push surrounding fluid out of the way. Adding flow work $pv$ gives enthalpy:

$$
h=u+pv.
$$

Thus the transported total energy per unit mass is

$$
e_t=h+\frac{V^2}{2}+gz.
$$

## 2. General control-volume energy balance

$$
\frac{d}{dt}\int_{CV}\rho\left(u+\frac{V^2}{2}+gz\right)dV
=\dot Q-\dot W_s+
\sum_{in}\dot m e_t-
\sum_{out}\dot m e_t.
$$

$\dot W_s$ excludes flow work because flow work is already contained in $h$.

## 3. Steady-flow energy equation

At steady state:

$$
\boxed{\dot Q-\dot W_s=
\sum_{out}\dot m\left(h+\frac{V^2}{2}+gz\right)
-\sum_{in}\dot m\left(h+\frac{V^2}{2}+gz\right)}.
$$

For one inlet and one outlet, divide by $\dot m$:

$$
q-w_s=(h_2-h_1)+\frac{V_2^2-V_1^2}{2}+g(z_2-z_1).
$$

See [[Steady-flow Energy Equation]].

![[tf_control_volume_balances.png|760]]

## 4. Device reductions

| Device | Dominant conversion | Common assumptions |
|---|---|---|
| nozzle | $h\to V^2/2$ | adiabatic, $w_s=0$, $\Delta z\approx0$ |
| diffuser | $V^2/2\to h$ | same as nozzle |
| turbine | $h\to w_s$ | adiabatic, small $\Delta KE,\Delta PE$ |
| compressor/pump | $w_s\to h$ | adiabatic, small $\Delta KE,\Delta PE$ |
| heat exchanger/heater | $q\leftrightarrow h$ | no shaft work |
| throttle | pressure drop at $h\approx$ const | adiabatic, no work, small KE change |

### Nozzle equation

For an ideal gas with negligible inlet speed:

$$
V_2=\sqrt{2c_p(T_1-T_2)}.
$$

Temperature falls because enthalpy becomes directed kinetic energy.

## 5. Reynolds transport theorem

For any extensive property $B$ with specific value $b=B/m$:

$$
\frac{dB_{system}}{dt}=
\frac{d}{dt}\int_{CV}\rho b\,dV+
\int_{CS}\rho b(\mathbf V\cdot\mathbf n)\,dA.
$$

Choose $b=1$, $\mathbf V$ or $u+V^2/2+gz$ to obtain mass, momentum or energy balances.

## 6. Turbojet chain

1. **Diffuser/intake** slows and compresses the incoming stream.
2. **Compressor** receives shaft work and raises stagnation pressure/temperature.
3. **Combustor** adds heat approximately at constant pressure.
4. **Turbine** extracts work to drive the compressor.
5. **Nozzle** converts remaining enthalpy into jet kinetic energy.

The complete engine creates thrust through momentum change; it does not create energy. Fuel chemical energy supplies the rise in flow stagnation enthalpy.

## 7. Assumption discipline

Cross out terms only after naming the reason. “Nozzle” is not itself a reason to assume adiabatic, though it is often a good approximation. A hair dryer, for example, intentionally includes heat/electrical power and can have non-negligible velocity changes.

## Links

- Concept: [[Steady-flow Energy Equation]]
- Tutorial: [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]]
- Continues in Propulsion: [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[SESA2024 07 - Spacecraft Propulsion]]
- Continues in CFD: [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[SESA2029 A9 - Finite Volume Method]]
- Next: [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]

## Sources

- `02 - Sources/Lectures/Chapter 13.pdf`, §§13.1-13.5.

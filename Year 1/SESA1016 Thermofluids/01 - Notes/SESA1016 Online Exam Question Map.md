---
title: "SESA1016 Online Exam Question Map"
module: "SESA1016 Thermofluids"
type: revision
tags: [sesa1016, exam-prep, question-map]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 01 - Basic Concepts.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 02 - Work and Heat.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 03 - Heat Engines and Entropy.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 04 - Heat Engine Models.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 05 - Dimensional Analysis.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 07 - Describing Flow and the Euler Equation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 09 - Momentum and Energy Conservation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 10 - Drag and Its Sources - External Flows.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 11 - Flows in Conduits.pdf", "02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter 3.pdf", "02 - Sources/Lectures/Chapter 4.pdf", "02 - Sources/Lectures/Chapter 5.pdf", "02 - Sources/Lectures/Chapter 6.pdf", "02 - Sources/Lectures/Chapter 7.pdf", "02 - Sources/Lectures/Chapter 8.pdf", "02 - Sources/Lectures/Chapter 9.pdf", "02 - Sources/Lectures/Chapter 10.pdf", "02 - Sources/Lectures/Chapter 11.pdf", "02 - Sources/Lectures/Chapter 12.pdf", "02 - Sources/Lectures/Chapter 13.pdf", "02 - Sources/Lectures/Chapter 14.pdf", "02 - Sources/Lectures/Chapter 15.pdf"]
---

# SESA1016 Online Exam Question Map

> [!abstract] What this map is - and is not
> There are no SESA1016 past papers because this was the module's first delivery and the assessment was online. This map therefore uses **source evidence**, not invented frequency claims: 15 chapters, their worked examples, and 11 sheets containing 81 numbered problems. It identifies the modelling moves that recur across those sources.

## Coverage matrix

| Block | Source practice | High-value question forms |
|---|---|---|
| State and ideal gas | PS1 Q1-5 | choose system, convert units, use $pV=mRT$, moving piston equilibrium |
| First law | PS2 Q1-5 | construct process path, boundary work, $Q-W=\Delta U$, compare isothermal/adiabatic |
| Engines and entropy | PS3 Q1-6 | close a cycle, efficiency, second-law feasibility, entropy change/generation |
| Ideal cycles | PS4 Q1-6 | state table, process-by-process $T,p,v$, cycle work and efficiency |
| Dimensional analysis | PS5 Q1-5 | form $\Pi$ groups, interpret exponents, transfer model results to prototype |
| Properties/hydrostatics | PS6 Q1-9 | viscosity-temperature trends, buoyancy, manometer pressure walks, gates/tanks |
| Flow kinematics/Euler | PS7 Q1-6 | streamlines, material acceleration, pressure gradients, Mach number |
| Bernoulli/continuity | PS8 Q1-11 | choose points, couple mass conservation with Bernoulli, numerical integration |
| Momentum/energy | PS9 Q1-11 | draw a control volume, include pressure forces, thrust, bends, SFEE |
| External viscous flow | PS10 Q1-7 | profile integrals, wall stress, transition, pressure/friction drag corrections |
| Conduits | PS11 Q1-10 | velocity profiles, flow regime, friction/minor loss, pumping power, iterate for $V$ |

## The seven modelling decisions most likely to decide a mark

1. **System or control volume?** Fixed mass suggests closed-system thermodynamics; fluid crossing the boundary suggests a control volume.
2. **Absolute or gauge pressure?** The ideal-gas law needs absolute pressure. Atmospheric pressure can cancel in a force balance only after it has been included consistently.
3. **What is positive?** State heat/work signs and coordinate directions before substitution.
4. **Which energy terms survive?** Do not discard heat, shaft work, kinetic energy or potential energy without a physical reason.
5. **Where does Bernoulli hold?** Same streamline unless the flow is irrotational; steady, inviscid and incompressible; no loss or machinery between points.
6. **Which velocity is meant?** Local, maximum, area-mean and mass-mean velocities are not interchangeable.
7. **What creates the loss?** External flow: wall shear and separation. Internal flow: distributed wall friction and local fittings.

## Fast online-exam workflow

### 1. Model box (about 30 seconds)

Write: system/CV, steady/unsteady, ideal gas/incompressible, adiabatic/inviscid, 1D/uniform ports, sign convention.

### 2. Symbolic equation first

Reduce the general law before inserting numbers. This catches omitted terms and makes unit checking possible.

### 3. Numerical evaluation

- Convert bar/kPa/mm/litre before calculating.
- Keep at least four significant figures internally.
- Report a sensible final precision with units and direction.

### 4. Physical check

- Expansion work should be positive under the course convention.
- A passive device cannot create stagnation enthalpy.
- Pump power and head loss cannot be negative.
- A heat-engine efficiency must satisfy $0\le\eta<1$ and cannot exceed Carnot.
- A computed boundary-layer thickness or pipe velocity should fit the geometry.

## Mixed practice route

| Session | Questions | Purpose |
|---|---|---|
| A | PS1 Q4, PS2 Q5, PS3 Q4, PS4 Q1 | closed-system process chain |
| B | PS5 Q1, Q3, Q5; PS6 Q3, Q6, Q8 | scaling and hydrostatics |
| C | PS7 Q2-3, PS8 Q1, Q3, Q7 | material acceleration, Euler, Bernoulli and continuity |
| D | PS9 Q2-5, Q9, Q11 | control-volume momentum and energy |
| E | PS10 Q1-3, Q5-7; PS11 Q6, Q9-10 | viscous losses and corrections |

## Failure-mode checklist

> [!warning] Common traps
> - using Celsius in $pV=mRT$ or entropy relations;
> - using $c_p$ for a rigid closed container ($c_v$ applies);
> - treating $Q=0$ as $\Delta T=0$;
> - applying Bernoulli through a pump, heater, wake or viscous pipe without adding work/loss terms;
> - omitting outlet pressure forces in momentum balances;
> - reporting the force on the fluid when the question asks for the support force;
> - confusing Darcy and Fanning friction factors (the course uses Darcy in $h_f=f(L/D)V^2/(2g)$);
> - using $V_{max}$ where a correlation requires $\bar V$;
> - forgetting both wetted sides of a plate or aerofoil.

## Formula links

- Master reference: [[SESA1016 Formula Sheet]]
- Complete solutions: [[SESA1016 Thermofluids Hub#Problem sheets - full worked solutions]]

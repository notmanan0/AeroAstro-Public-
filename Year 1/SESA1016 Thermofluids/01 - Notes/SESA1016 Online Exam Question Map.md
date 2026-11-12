---
title: "SESA1016 Online Exam Question Map"
module: "SESA1016 Thermofluids"
type: revision
tags: [sesa1016, exam-prep, question-map]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet 01 - Basic Concepts.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 02 - Work and Heat.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 03 - Heat Engines and Entropy.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 04 - Heat Engine Models.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 05 - Dimensional Analysis.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 06 - Fluid Properties and Hydrostatics.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 07 - Describing Flow and the Euler Equation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 08 - The Bernoulli Equation and Mass Conservation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 09 - Momentum and Energy Conservation.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 10 - Drag and Its Sources - External Flows.pdf", "02 - Sources/Tutorial Sheets/Problem Sheet 11 - Flows in Conduits.pdf", "02 - Sources/Lectures/SESA1016 Lecture 2025-05-13.txt", "02 - Sources/Lectures/Chapter 1.pdf", "02 - Sources/Lectures/Chapter 2.pdf", "02 - Sources/Lectures/Chapter 3.pdf", "02 - Sources/Lectures/Chapter 4.pdf", "02 - Sources/Lectures/Chapter 5.pdf", "02 - Sources/Lectures/Chapter 6.pdf", "02 - Sources/Lectures/Chapter 7.pdf", "02 - Sources/Lectures/Chapter 8.pdf", "02 - Sources/Lectures/Chapter 9.pdf", "02 - Sources/Lectures/Chapter 10.pdf", "02 - Sources/Lectures/Chapter 11.pdf", "02 - Sources/Lectures/Chapter 12.pdf", "02 - Sources/Lectures/Chapter 13.pdf", "02 - Sources/Lectures/Chapter 14.pdf", "02 - Sources/Lectures/Chapter 15.pdf"]
---

# SESA1016 Online Exam Question Map

There are no SESA1016 past papers: this was the module's first delivery and the assessment was online. The map is therefore built from what the course itself set, namely the fifteen chapters and their worked examples, the 81 numbered problems on the eleven sheets, and the three-question mock exam worked on 13 May 2025. It picks out the modelling moves that recur across them rather than claiming any frequency.

## Coverage matrix

| Block | Sheet practice | Typical question forms | Worked in |
|---|---|---|---|
| State and ideal gas | PS1 Q1–5 | choose the system, convert to absolute units, $pV=mRT$, piston equilibrium | [[SESA1016 T1 - Thermodynamic Systems, Properties and State#Worked examples\|T1]] |
| First law | PS2 Q1–5 | build the process path, boundary work, $\Delta U=Q-W$, isothermal against adiabatic | [[SESA1016 T2 - Work, Heat and the First Law#Worked examples\|T2]] |
| Engines and entropy | PS3 Q1–6 | close a cycle, efficiency, second-law feasibility, entropy change and generation | [[SESA1016 T3 - Heat Engines and the Second Law#Worked examples\|T3]] · [[SESA1016 T4 - Entropy and Isentropic Relations#Worked examples\|T4]] |
| Ideal cycles | PS4 Q1–6; mock Q1 | state table, $T$, $p$, $v$ process by process, cycle work and efficiency, Carnot limits | [[SESA1016 T5 - Ideal Heat Engine Models#Worked examples\|T5]] |
| Dimensional analysis | PS5 Q1–5 | form pi groups, read a dimensionless curve, transfer model results | [[SESA1016 T6 - Dimensional Analysis and Similarity#Worked examples\|T6]] |
| Properties and hydrostatics | PS6 Q1–9 | viscous shear, buoyancy, manometer pressure walks, layered tanks, atmosphere | [[SESA1016 T7 - Fluid Properties and Viscosity#Worked examples\|T7]] · [[SESA1016 T8 - Hydrostatics#Worked examples\|T8]] |
| Kinematics and Euler | PS7 Q1–6 | streamlines, particle acceleration, pressure gradients, Mach number | [[SESA1016 T9 - Describing Flow and the Material Derivative#Worked examples\|T9]] · [[SESA1016 T10 - Euler and Bernoulli Equations#Worked examples\|T10]] |
| Bernoulli and continuity | PS8 Q1–11 | choose points, couple continuity with Bernoulli, integrate a measured profile | [[SESA1016 T10 - Euler and Bernoulli Equations#Worked examples\|T10]] · [[SESA1016 T11 - Conservation of Mass#Worked examples\|T11]] |
| Momentum and energy | PS9 Q1–11; mock Q2 | draw a control volume, pressure forces, thrust, bends, wakes, SFEE | [[SESA1016 T12 - Conservation of Momentum#Worked examples\|T12]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Worked examples\|T13]] |
| External viscous flow | PS10 Q1–7 | profile integrals, wall shear, transition, pressure and friction drag | [[SESA1016 T14 - Boundary Layers and the Origin of Drag#Worked examples\|T14]] |
| Conduits | PS11 Q1–10; mock Q3 | velocity profiles, regime, friction and minor losses, pump power, iterate for $\bar V$ | [[SESA1016 T15 - Flow in Conduits#Worked examples\|T15]] |

## Modelling decisions that decide the mark

Most lost marks in these problems come from a modelling choice made before any algebra, not from arithmetic.

- System or control volume: a fixed mass calls for closed-system thermodynamics; fluid crossing the boundary calls for a control volume.
- Absolute or gauge pressure: the ideal-gas law needs absolute pressure, while atmospheric pressure cancels from a force balance only if it acts all round.
- Signs: state the heat and work convention and the coordinate directions before substituting.
- Energy terms: drop heat, shaft work, kinetic or potential energy only with a physical reason.
- Where Bernoulli holds: along a streamline, steady, inviscid and incompressible, with no machine or loss between the points (and across streamlines only if the upstream flow is uniform).
- Which velocity: local, maximum and area-averaged velocities are not interchangeable.
- What creates the loss: in external flow, wall shear and separation; in internal flow, wall friction along the pipe and local fittings.

## Working an online question

Write a one-line model first: system or control volume, steady or not, ideal gas or incompressible, adiabatic or inviscid, uniform ports, sign convention. Reduce the general law symbolically before inserting numbers, because that is where omitted terms show up and where units can be checked. Convert bar, kPa, mm and litres before calculating, keep at least four significant figures internally, and report a sensible precision with units and direction.

Then check the answer against physics: expansion work is positive under the course convention, a passive device cannot raise total enthalpy, pump power and head loss cannot be negative, a heat-engine efficiency lies between 0 and the Carnot value, and a boundary-layer thickness or pipe velocity should fit the geometry.

## Mixed practice route

| Session | Questions | Purpose |
|---|---|---|
| A | PS1 Q4, PS2 Q5, PS3 Q4, PS4 Q1 | closed-system process chain |
| B | PS5 Q1, Q3, Q5; PS6 Q3, Q6, Q8 | scaling and hydrostatics |
| C | PS7 Q2–3, PS8 Q1, Q3, Q7 | particle acceleration, Euler, Bernoulli and continuity |
| D | PS9 Q2–5, Q9, Q11 | control-volume momentum and energy |
| E | PS10 Q1–3, Q5–7; PS11 Q6, Q9–10 | viscous losses |
| F | mock Q1–Q3 (13 May) | timed, mixed: cycles, momentum, pipe flow |

## Printed answers that disagree with a recalculation

Before checking your own work against a printed answer, note these differences found when every sheet was re-solved in Python. Each is explained beside the question in the solution note.

| Question | Printed | Recalculated | Reason |
|---|---|---|---|
| PS4 Q4.5 | $Q_{out}=1679$ J, $\eta=39.2$ % | 2.315 kJ, 31.8 % if the heat absorbed on part of 3→1 is counted as input | the sheet nets heat in and out along the same process |
| PS9 Q9.6 | 1616.67 N | 1.52–1.74 kN | depends on how the sheet's area is taken; the printed value cannot be reproduced |
| PS9 Q9.10 | sheet values | −123.0, 241.3, 203.3, 80.3 MW with $c_p=1005$ | printed values need $c_p=1010$ and kinetic energy at combustor entry |
| PS10 Q10.6 | 3.23 kN/m, $C_{dp}=0.248$ | 1.52 kN/m, 0.117 | the 27° is the included angle, so each face is at 13.5° |
| PS11 Q11.7 | 926 Pa (answer block) | 10 Pa, 20 815 s⁻¹ | the sheet's own worked solution gives these; 926 Pa belongs to no part of Q11.7 |

## Common traps

> [!warning] Traps that recur in the sheets
> - Celsius in $pV=mRT$ or in entropy and efficiency formulae;
> - $c_p$ for a rigid closed container, where $c_v$ applies;
> - treating $Q=0$ as $\Delta T=0$;
> - Bernoulli through a pump, heater, wake or long pipe without work or loss terms;
> - leaving out pressure forces on inlet and outlet faces in a momentum balance;
> - reporting the force on the fluid when the question asks for the force on the support;
> - mixing Darcy and Fanning friction factors (the course uses Darcy, $\Delta p=f\tfrac LD\tfrac12\rho\bar V^2$);
> - using $V_{max}$ where a formula needs $\bar V$;
> - forgetting the second wetted side of a plate.

## Links

- [[SESA1016 Formula Sheet]] · [[SESA1016 Thermofluids Hub#Problem sheets|problem-sheet solutions]] · [[SESA1016 Thermofluids Hub#Exam skills|exam skills]]

---
title: "SESA1016 Thermofluids Hub"
module: "SESA1016 Thermofluids"
type: hub
tags: [sesa1016, hub, thermofluids]
status: complete
---

# SESA1016 Thermofluids Hub

> [!abstract] Module at a glance
> **Store and convert energy** (thermodynamics) -> **identify similarity** (dimensional analysis) -> **describe fluids** (properties, pressure and motion) -> **apply conservation laws** (mass, momentum and energy) -> **predict losses** (drag and conduit flow).
>
> One distinction runs through the whole module: a **closed system** follows a fixed mass, while a **control volume** occupies a chosen region of space. The first is the natural language of piston-cycle thermodynamics; the second is the natural language of flowing fluids.
>
> Quick reference: [[SESA1016 Formula Sheet]] · assessment preparation: [[SESA1016 Online Exam Question Map]]

## Topic map

### Part A: Closed-system thermodynamics

1. [[SESA1016 T1 - Thermodynamic Systems, Properties and State]]: systems, control volumes, intensive/extensive properties, equilibrium and the ideal-gas law
2. [[SESA1016 T2 - Work, Heat and the First Law]]: sign convention, boundary work, $c_v$, $c_p$, enthalpy and common processes
3. [[SESA1016 T3 - Heat Engines and the Second Law]]: cycles, efficiency, Kelvin-Planck, heat pumps and reversibility
4. [[SESA1016 T4 - Entropy and Isentropic Relations]]: entropy transfer, entropy generation and ideal-gas entropy changes
5. [[SESA1016 T5 - Ideal Heat Engine Models]]: Carnot, Otto, Diesel and Brayton cycles

### Part B: Similarity and fluid fundamentals

6. [[SESA1016 T6 - Dimensional Analysis and Similarity]]: dimensional homogeneity, Buckingham $\Pi$, dimensionless groups and scale models
7. [[SESA1016 T7 - Fluid Properties and Viscosity]]: density, compressibility, Newtonian stress and temperature dependence
8. [[SESA1016 T8 - Hydrostatics]]: Pascal, Stevin, Archimedes, manometers and atmospheric stratification

### Part C: Fluid motion and inviscid flow

9. [[SESA1016 T9 - Describing Flow and the Material Derivative]]: Eulerian/Lagrangian descriptions, streamlines and flow classifications
10. [[SESA1016 T10 - Euler and Bernoulli Equations]]: acceleration, Euler equation, Bernoulli, Pitot tubes and pressure coefficient

### Part D: Control-volume conservation laws

11. [[SESA1016 T11 - Conservation of Mass]]: volume flow, mass flow, mean velocity and multiple ports
12. [[SESA1016 T12 - Conservation of Momentum]]: momentum flux, forces, jets, bends and propulsion
13. [[SESA1016 T13 - Conservation of Energy and Propulsion]]: steady-flow energy equation, Reynolds transport theorem and turbojets

### Part E: Viscous losses

14. [[SESA1016 T14 - Boundary Layers and the Origin of Drag]]: displacement/momentum thickness, transition, separation and drag
15. [[SESA1016 T15 - Flow in Conduits]]: entrance length, laminar/turbulent profiles, Darcy-Weisbach, minor losses and pumps

## Core concept notes

| Thermodynamics | Fluid mechanics | Conservation and losses |
|---|---|---|
| [[Closed System vs Control Volume]] | [[Pressure and Head]] | [[Control-volume Analysis Workflow]] |
| [[Thermodynamic State and Process]] | [[Newtonian Fluid and Viscosity]] | [[Mass Flow Rate]] |
| [[Boundary Work]] | [[Material Derivative]] | [[Momentum Flux]] |
| [[Internal Energy and Enthalpy]] | [[Streamline, Pathline and Streakline]] | [[Steady-flow Energy Equation]] |
| [[Thermal Efficiency and COP]] | [[Bernoulli Equation]] | [[Boundary-layer Thickness Measures]] |
| [[Entropy Generation]] | [[Stagnation Pressure and Pitot Tube]] | [[Skin-friction and Pressure Drag]] |
| [[Isentropic Ideal-gas Relations]] | [[Reynolds Number]] | [[Darcy Friction Factor]] |
| [[Buckingham Pi Theorem]] | [[Pressure Coefficient]] | [[Major and Minor Head Losses]] |

## Problem sheets - full worked solutions

| Sheet | Coverage | Solution note |
|---|---|---|
| 1 | Basic concepts and ideal gas | [[SESA1016 Problem Sheet 01 - Basic Concepts Solutions]] |
| 2 | Work and heat | [[SESA1016 Problem Sheet 02 - Work and Heat Solutions]] |
| 3 | Heat engines and entropy | [[SESA1016 Problem Sheet 03 - Heat Engines and Entropy Solutions]] |
| 4 | Heat-engine models | [[SESA1016 Problem Sheet 04 - Heat Engine Models Solutions]] |
| 5 | Dimensional analysis | [[SESA1016 Problem Sheet 05 - Dimensional Analysis Solutions]] |
| 6 | Fluid properties and hydrostatics | [[SESA1016 Problem Sheet 06 - Fluid Properties and Hydrostatics Solutions]] |
| 7 | Describing flow and Euler equation | [[SESA1016 Problem Sheet 07 - Describing Flow and Euler Equation Solutions]] |
| 8 | Bernoulli and mass conservation | [[SESA1016 Problem Sheet 08 - Bernoulli and Mass Conservation Solutions]] |
| 9 | Momentum and energy conservation | [[SESA1016 Problem Sheet 09 - Momentum and Energy Conservation Solutions]] |
| 10 | Drag and external flows | [[SESA1016 Problem Sheet 10 - Drag and External Flows Solutions]] |
| 11 | Flow in conduits | [[SESA1016 Problem Sheet 11 - Flows in Conduits Solutions]] |

## No past papers: how to prepare honestly

> [!info] Evidence available
> This was the first delivery and the assessment was online, so there is no historical frequency distribution to mine. The defensible evidence is the **chapter worked examples**, the **81 numbered sheet problems**, the marked tutorial problems and the answer blocks. [[SESA1016 Online Exam Question Map]] converts those into a coverage matrix and mixed practice without pretending that invented questions are past papers.

## Recommended study route

1. Read the relevant topic note once for the physical model and assumptions.
2. Build a one-line equation map from [[SESA1016 Formula Sheet]].
3. Attempt the matching sheet without looking at the solution.
4. Compare modelling choices, signs and units - not just the final number.
5. Finish with mixed questions from [[SESA1016 Online Exam Question Map]].

## All notes

```dataview
TABLE type, stream, status, file.mtime AS "Updated"
FROM "Year 1/SESA1016 Thermofluids"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into

- **Builds on**: algebra, calculus, mechanics, ideal gases and energy conservation.

| Later module | Bridge from SESA1016 | Continue with |
|---|---|---|
| [[SESA2022 Aerodynamics Hub]] | Bernoulli, pressure coefficient, boundary layers and drag | [[SESA2022 T2 - Boundary Layers]] · [[SESA2022 T3 - Potential Flow]] |
| [[SESA2023 Propulsion Hub]] | ideal gases, entropy, Brayton cycles, momentum thrust, SFEE and similarity | [[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]] · [[SESA2023 W02 - Thermodynamics, Mixtures, SFEE and Isentropic Efficiency]] · [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]] · [[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]] |
| [[SESA2029 Digital Aerospace Methods Hub]] — CFD | material derivative, Newtonian fluids, control-volume conservation, Euler flow and boundary layers | [[SESA2029 A6 - Higher-Order Time Integration, Runge-Kutta and the Blasius Equation]] · [[SESA2029 A7 - Governing Equations - Euler and Navier-Stokes]] · [[SESA2029 A8 - Turbulence, RANS and Turbulence Models]] · [[SESA2029 A9 - Finite Volume Method]] |
| [[SESA2024 Astronautics Hub]] | jet momentum, nozzle energy conversion and propulsion control volumes | [[SESA2024 07 - Spacecraft Propulsion]] |

> [!tip] The cleanest progression
> Learn the physical balances here first. Propulsion adds compressibility, component efficiencies and combustion; Aerodynamics adds circulation and lifting flows; Digital Aerospace discretises the same conservation laws and makes their modelling assumptions visible in a CFD solver.

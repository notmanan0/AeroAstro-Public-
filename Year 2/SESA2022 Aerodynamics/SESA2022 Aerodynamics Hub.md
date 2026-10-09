---
title: "SESA2022 Aerodynamics Hub"
module: "SESA2022 Aerodynamics"
type: hub
tags: [sesa2022, hub, moc]
status: complete
---

# SESA2022 Aerodynamics Hub

> [!abstract] Module at a glance
> **Viscous flow** (boundary layers) → **inviscid flow** (potential flow) → **aerofoils** (thin aerofoil theory) → **wings** (lifting line) → **aircraft** (trim and static stability).
>
> Quick reference: [[SESA2022 Formula Sheet]] · exam strategy: [[SESA2022 Past Paper Map]]

## Topic map
1. [[SESA2022 T2 - Boundary Layers]]: no-slip, $\delta^*$, $\theta$, $H$, MIE, law of the wall, virtual origin, separation
2. [[SESA2022 T3 - Potential Flow]]: LEGO bricks, cylinder, Rankine oval, Kutta–Joukowski, method of images
3. [[SESA2022 T4 - Thin Aerofoil Theory]]: vortex sheet, Kutta condition, $C_l = 2\pi(\alpha-\alpha_{L=0})$, flaps
4. [[SESA2022 T5 - Finite Wing Theory]]: lifting line, induced drag, elliptic loading, $(L/D)_{max}$
5. [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]: trim, neutral point, stick fixed/free, manoeuvre margin

## Concept notes

| Boundary layers                         | Potential flow                            | Thin aerofoil                                  | Finite wing                                | Stability                                |
| --------------------------------------- | ----------------------------------------- | ---------------------------------------------- | ------------------------------------------ | ---------------------------------------- |
| [[Displacement and Momentum Thickness]] | [[Streamfunction and Velocity Potential]] | [[Vortex Sheet]]                               | [[Biot-Savart Law and Helmholtz Theorems]] | [[Neutral Point and Static Margin]]      |
| [[Momentum Integral Equation]]          | [[Elementary Potential Flows]]            | [[Kutta Condition]]                            | [[Downwash and Induced Drag]]              | [[Stick-Fixed vs Stick-Free Stability]]  |
| [[Law of the Wall]]                     | [[Flow Past a Cylinder]]                  | [[Kelvin's Circulation Theorem]]               | [[Elliptic Lift Distribution]]             | [[Manoeuvre Point and Manoeuvre Margin]] |
| [[Virtual Origin Method]]               | [[Rankine Oval]]                          | [[Glauert Integrals]]                          | [[Oswald Efficiency Factor]]               | [[Lateral and Directional Stability]]    |
| [[Boundary Layer Separation]]           | [[Kutta-Joukowski Theorem]]               | [[Aerodynamic Centre and Centre of Pressure]]  | [[Maximum Lift-to-Drag Ratio]]             |                                          |
|                                         | [[Method of Images]]                      | [[Aerofoil Stall]]                             |                                            |                                          |
|                                         | [[D'Alembert's Paradox]]                  | [[Trailing-Edge Flap in Thin Aerofoil Theory]] |                                            |                                          |

Legacy compressible-flow content (examined up to 2019-20, now [[SESA2023 Propulsion Hub|SESA2023]]): [[Isentropic Nozzle Flow]] · [[Normal Shock Waves]]

## Problem sheets (full worked solutions)
- [[SESA2022 Tutorial 2 - Viscous Flow Solutions]]
- [[SESA2022 Tutorial 3 - Potential Flow Solutions]]
- [[SESA2022 Examples Sheet 4 - Thin Aerofoil Theory Solutions]]
- [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]]
- [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
- [[SESA2022 Static Stability Past Paper Questions Solutions]]

## Past papers (all 12 solved)

| Year | Format | Solutions |
|---|---|---|
| 2013-14 | closed book | [[SESA2022 Exam 2013-14 Solutions]] ✅ |
| 2014-15 | closed book | [[SESA2022 Exam 2014-15 Solutions]] ✅ |
| 2015-16 | closed book | [[SESA2022 Exam 2015-16 Solutions]] ✅ |
| 2016-17 | closed book | [[SESA2022 Exam 2016-17 Solutions]] ✅ |
| 2017-18 | closed book | [[SESA2022 Exam 2017-18 Solutions]] ✅ |
| 2018-19 | closed book | [[SESA2022 Exam 2018-19 Solutions]] ✅ |
| 2019-20 | closed book | [[SESA2022 Exam 2019-20 Solutions]] ✅ |
| 2020-21 | 24 h online, per-student data | [[SESA2022 Exam 2020-21 Solutions]] ✅ |
| 2021-22 | 8 h online, notebook data | [[SESA2022 Exam 2021-22 Solutions]] ✅ |
| 2022-23 | online, per-ID data | [[SESA2022 Exam 2022-23 Solutions]] ✅ |
| 2023-24 | online, per-ID data | [[SESA2022 Exam 2023-24 Solutions]] ✅ |
| 2024-25 | 2 h closed book + rubric | [[SESA2022 Exam 2024-25 Solutions]] ✅ |

> [!warning] Data not in the vault
> The 2020-21 per-student parameters, the 2021-22 notebook profile, the 2022-23 and 2023-24 `.csv` files, and `0020Cpcomp.csv` are missing. Those parts are solved on **clearly labelled illustrative data**, with reusable code. Everything else uses the exact paper values.

## Labs & coursework
- [[SESA2022 Wind Tunnel Lab Summary]]: NACA 0020 $C_p$, finite-wing polar, flat-plate BL (submitted Dec 2025)

## All notes
```dataview
TABLE type, status, file.mtime AS "Updated"
FROM "Year 2/SESA2022 Aerodynamics"
WHERE type
SORT type ASC, file.name ASC
```

## Builds on / feeds into
- **From** [[SESA1016 Thermofluids Hub]]: [[SESA1016 T10 - Euler and Bernoulli Equations]] and [[SESA1016 T14 - Boundary Layers and the Origin of Drag]] provide the pressure-flow and viscous-drag foundations.
- [[SESA2027 Aerospace Mechanics & Control Hub]]: static stability (T6) becomes dynamic stability ($M_w = -H_sC_{L^*_\alpha}$)
- [[SESA3043 Advanced Aeronautics]]: viscous–inviscid coupling, panel/VLM methods, swept wings
- [[SESA3029 Aerothermodynamics]]: compressible boundary layers
- [[SESA3047 Advanced Aerospace Mechanics & Control]]: lateral/directional dynamics

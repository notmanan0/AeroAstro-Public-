---
title: "TTT and CCT Diagrams"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, steels, phase-transformations, kinetics]
status: complete
parent: ["[[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying]]"]
related: ["[[Martensite]]", "[[Hardenability and Jominy Test]]", "[[Tempering]]"]
---

# TTT and CCT Diagrams

![[Figures/materials_ttt_critical_cooling_rate.png]]

The equilibrium phase diagram has **no time axis**. TTT and CCT diagrams add kinetics.

## Time-temperature-transformation (TTT, isothermal)

Austenitise, quench rapidly to a hold temperature, and measure the fraction transformed against time. Repeating this at many temperatures gives **start** (~1 %) and **finish** (~99 %) C-shaped curves. Example: eutectoid steel at 705 °C starts pearlite at about 5.8 min and finishes at about 67 min.

**The nose** (about 540-550 °C at about 1 s for eutectoid steel) comes from two competing factors:

- just below $A_1$ (727 °C): small undercooling, so a small **driving force** for nucleation, so slow;
- far below: large driving force but **slow diffusion** (little thermal energy), so slow again.

Products: coarse pearlite (high $T$), then fine pearlite (near the nose), then **bainite** (below the nose; mixed diffusion and shear), then **martensite** below the horizontal $M_s$ ($M_{50}$, $M_{90}$) and $M_f$ lines.

## Continuous cooling transformation (CCT)

Measured at constant cooling rates, so it matches real processing. The curves sit slightly **lower and to the right** of the TTT curves.

| Cooling | Result |
|---|---|
| Furnace | coarse pearlite (anneal) |
| Air | fine pearlite (normalise) |
| Oil | pearlite + bainite + martensite (plain C) |
| Water ≥ critical rate | martensite (harden) |

**Critical cooling rate**: the slowest cooling curve that just misses the nose. From 700 °C for the 2024-25 eutectoid diagram that is roughly $(700-540)/0.8\approx150$-200 °C/s.

## Shifting the curves right (more hardenable)

- Alloying: Mo, Mn, Cr, Ni, V, B (and C up to about 0.6 %).
- **Coarser austenite grains** (higher austenitising temperature, or a long hold such as 780 °C): fewer boundary nucleation sites.

Then martensite forms at slower, safer cooling rates. Ni also **lowers $M_s$** (it is a $\gamma$ stabiliser).

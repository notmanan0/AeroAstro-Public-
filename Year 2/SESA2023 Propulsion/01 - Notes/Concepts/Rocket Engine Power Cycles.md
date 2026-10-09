---
title: "Rocket Engine Power Cycles"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["pressure-fed", "expander cycle", "gas generator cycle", "staged combustion", "full-flow staged combustion", "turbopump", "tap-off"]
tags: [sesa2023, concept, rockets]
status: complete
parent_lectures: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Rocket Performance Parameters]]", "[[Euler Work Equation]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf"]
---
# Rocket Engine Power Cycles

## Definition

> [!note] Definition
> The way a liquid-rocket engine raises its propellants to chamber pressure. Either the tanks are pressurised, or a turbine drives pumps, and the cycle is defined by what drives the turbine.

## Explanation
**Why pressure matters**: a higher $P_c$ gives a higher $V_j$ (more expansion possible), a smaller chamber and throat for a given thrust, and a lighter engine per unit thrust.

| Cycle | How it works | + | − | Examples |
|---|---|---|---|---|
| **Pressure-fed** | Tanks pressurised by He (or self-pressurised); valves only | Simplest, cheapest, lightest, no start-up | Tank walls cap $P_c$, so low thrust. Used for upper stages and thrusters | Aestus |
| **Expander (closed)** | Fuel cools the nozzle/chamber, is vaporised, drives the turbine, then enters the chamber | Simple; clean fuel means low turbine wear | Turbine power limited by heat pick-up (area ∝ L², volume ∝ L³), so size-limited; not self-starting | Vinci, RL10 |
| **Expander bleed (open)** | Part of the heated fuel drives the turbine and is dumped | Larger turbine pressure ratio | Dumped fuel lowers $I_{sp}$ | |
| **Gas generator (GG)** | A small pre-combustor burns a little propellant (off-ratio) to drive the turbine; the exhaust is dumped | High turbine power, high $P_c$, throttleable | Complex; wasted propellant; hot gas wears the turbine | F-1, Merlin 1D, Vulcain 2 |
| **Tap-off** (legacy) | Hot gas tapped from the main chamber drives the turbine | No separate generator | Turbine exposed to chamber gas | J-2S |
| **Staged combustion (SC)** | All the fuel, with a little oxidiser, passes through a pre-burner; the rich turbine exhaust goes into the main chamber | Highest $P_c$ (SSME > 200 bar), no dumped flow | Harshest turbine environment, very complex | SSME (fuel-rich), RD-253 (oxidiser-rich, UDMH/N₂O₄, Proton) |
| **Full-flow SC** (legacy) | Two pre-burners (fuel-rich and oxidiser-rich) each drive their own pump; both exhausts go to the chamber | All propellant through the turbines, so a lower turbine $T$ for the same power; no fuel/oxidiser seal on a shared shaft; gas–gas injection | Most complex | RD-270, Raptor |

**Turbopump design** (legacy 2015-16 Q2(iv)):
- **Expander**: high-efficiency turbine at a low pressure ratio; H₂ pumps need very high tip speed (low density).
- **GG**: a high-pressure-ratio turbine with a small flow; the flow is dumped, so turbine efficiency is less critical.
- **SC**: a low-pressure-ratio, high-flow turbine working in hot, rich or oxidising gas; pump discharge pressure far above $P_c$.
- **All**: cavitation margins (inducers), seals, bearings in cryogenics, and start transients.

## Related
- [[Rocket Performance Parameters]] · [[Euler Work Equation]]

## Sources
- Week 10 notes §10.5; Lecture 30

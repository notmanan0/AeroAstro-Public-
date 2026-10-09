---
title: "Gauge Factor"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["gauge factor G", "piezoresistivity", "strain gauge sensitivity", "dR/R = G epsilon"]
tags: [feeg1004, concept, transducers, strain]
status: complete
parent_lectures: ["[[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]"]
related_concepts: ["[[Strain Gauge Bridge Configurations]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Ohm's Law and Resistivity]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 03 - Complete Systems - Lecture Slides.pdf"]
---

# Gauge Factor

## Definition

> [!note] Definition
>
> $$G = \frac{\Delta R/R}{\varepsilon},\qquad \frac{\Delta R}{R} = \frac{\Delta\rho}{\rho} + (1 + 2\nu)\varepsilon$$
>
> The first term is piezoresistive; the second is geometric (length up, diameter down through Poisson's ratio ν).

## Explanation
- **Metal foil or wire**: $G\approx2$, geometry-dominated ($1 + 2\nu\approx1.6$ plus a little piezoresistance). 120 or 350 Ω.
- **Semiconductor**: $G\approx100$–120, piezoresistive-dominated. Very sensitive, but temperature-dependent, non-linear and about 10× the price.
- Strains are µε-scale, so ΔR/R ~ 10⁻³ or less. That is why a bridge is essential.

## Examples
- SESA2027 PS C Q2: 3 mV from a 5 V quarter bridge with $G$ = 2.1 gives ε = 1.14 × 10⁻³ ([[Wheatstone Bridge and Strain Gauges]]).

## Related
- Topic notes: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- Concepts: [[Strain Gauge Bridge Configurations]] · [[Ohm's Law and Resistivity]]
- Cross-module: [[Stress, Strain and Young's Modulus]] · [[Strain Gauge Rosettes]]

## Sources
- Transducers lecture 3

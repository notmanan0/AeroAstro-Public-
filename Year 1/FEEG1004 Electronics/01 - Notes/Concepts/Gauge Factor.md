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

The gauge factor $G$ of a strain gauge is its fractional change in resistance per unit strain. It sets how much signal a given strain produces.

$$
G = \frac{\Delta R/R}{\varepsilon},\qquad \frac{\Delta R}{R} = \frac{\Delta\rho}{\rho} + (1 + 2\nu)\varepsilon
$$

The second equation splits the resistance change into two parts. The first term is piezoresistive, a change in the resistivity of the material itself. The second is geometric: stretching the conductor increases its length and, through Poisson's ratio $\nu$, reduces its diameter, and both raise $R = \rho L/A$.

Metal foil and wire gauges have $G\approx2$ and are dominated by geometry, since $1 + 2\nu\approx1.6$ and piezoresistance adds only a little. They are usually made as $120\ \Omega$ or $350\ \Omega$ elements. Semiconductor gauges have $G\approx100$–$120$ and are dominated by piezoresistance. They are far more sensitive, but their output depends on temperature, is non-linear, and they cost about ten times as much.

Engineering strains are of order microstrain, so even with $G\approx2$ the fractional change $\Delta R/R$ is $10^{-3}$ or less. A change that small cannot be read off an ohmmeter, which is why gauges are always used in a bridge. For example, a $5\ \mathrm V$ quarter bridge with $G = 2.1$ giving $3\ \mathrm{mV}$ corresponds to $\varepsilon = 1.14 \times 10^{-3}$ (SESA2027 PS C Q2; [[Wheatstone Bridge and Strain Gauges]]).

## Related

- [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- [[Strain Gauge Bridge Configurations]] · [[Ohm's Law and Resistivity]]
- Cross-module: [[Stress, Strain and Young's Modulus]] · [[Strain Gauge Rosettes]]
- Sources: Transducers lecture 3

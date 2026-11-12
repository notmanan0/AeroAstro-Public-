---
title: "Strain Gauge Bridge Configurations"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["quarter bridge", "half bridge", "full bridge", "dummy gauge", "temperature compensation", "load cell", "V = NEGe/4"]
tags: [feeg1004, concept, transducers, strain, bridge]
status: complete
parent_lectures: ["[[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]"]
related_concepts: ["[[Gauge Factor]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Standard Op-Amp Configurations]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 03 - Complete Systems - Lecture Slides.pdf"]
---

# Strain Gauge Bridge Configurations

A strain gauge bridge configuration is the choice of how many of the four Wheatstone bridge arms hold active gauges and where they sit on the member. With $N$ active gauges, excitation $E$, gauge factor $G$ and strain $\varepsilon$, the bridge output is

$$
V = \frac{N\,E\,G\,\varepsilon}{4}
$$

The placement rule follows from the bridge equation: resistance changes in **adjacent** arms subtract, and changes in **opposite** arms add. A gauge pair that sees equal and opposite strains therefore doubles the signal when placed in adjacent arms, while any strain both gauges share (temperature, or a load component that is not wanted) cancels. The table sets out the standard layouts.

| Measurand | Layout | Signal | Temp. comp. | Cancels |
|---|---|---|---|---|
| bending | half: top +ε, bottom −ε (adjacent) | ×2 | ✔ | axial |
| bending | full: 4 gauges | ×4 | ✔ | axial |
| axial | 2 active (opposite arms) | ×2 | ✘ | bending |
| axial | 2 active + 2 dummy | ×2 | ✔ | bending |
| torsion | 4 at ±45° | ×4 | ✔ | bending, axial |

A **dummy gauge** sits at the same temperature as the active gauges but is unstressed, so the bridge stays balanced as the temperature changes. Two active gauges in opposite arms add their temperature changes as well as their strains, so that axial layout has no temperature compensation until two dummies fill the other arms. In bending the top and bottom fibres strain oppositely, and in torsion the principal strains lie at ±45°, so those layouts compensate for temperature without dummies.

In practice the bridge is first balanced with a trim potentiometer and an isolation resistor, and the small output is amplified by a differential amplifier.

![[ee_e3_gauge_configurations.png|700]]

## Related

- [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- [[Gauge Factor]] · [[Wheatstone Bridge and Strain Gauges]] · [[Standard Op-Amp Configurations]]
- Cross-module: [[Engineer's Bending Theory]] (top and bottom fibres strain oppositely) · [[Torsion of Circular Shafts]] (±45° principal strains)
- Sources: Transducers lecture 3

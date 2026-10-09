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

## Definition

> [!note] Definition
>
> $$V = \frac{N\,E\,G\,\varepsilon}{4}$$
>
> Here $N$ is the number of active gauges, $E$ the excitation, $G$ the gauge factor and $\varepsilon$ the strain. **Adjacent** arms subtract; **opposite** arms add.

## Explanation
| Measurand | Layout | Signal | Temp. comp. | Cancels |
|---|---|---|---|---|
| bending | half: top +ε, bottom −ε (adjacent) | ×2 | ✔ | axial |
| bending | full: 4 gauges | ×4 | ✔ | axial |
| axial | 2 active (opposite arms) | ×2 | ✘ | bending |
| axial | 2 active + 2 dummy | ×2 | ✔ | bending |
| torsion | 4 at ±45° | ×4 | ✔ | bending, axial |

- **Dummy gauges** sit at the same temperature as the active ones but unstressed, so the bridge stays balanced as temperature changes.
- Balance the bridge initially with a trim pot and an isolation resistor.
- Amplify the output with a **differential amplifier**.

![[ee_e3_gauge_configurations.png|700]]

## Related
- Topic notes: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]
- Concepts: [[Gauge Factor]] · [[Wheatstone Bridge and Strain Gauges]] · [[Standard Op-Amp Configurations]]
- Cross-module: [[Engineer's Bending Theory]] (top and bottom fibres strain oppositely) · [[Torsion of Circular Shafts]] (±45° principal strains)

## Sources
- Transducers lecture 3

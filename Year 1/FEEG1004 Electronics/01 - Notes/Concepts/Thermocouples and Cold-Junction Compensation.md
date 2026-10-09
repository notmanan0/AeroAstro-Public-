---
title: "Thermocouples and Cold-Junction Compensation"
module: "FEEG1004 Electronics"
type: concept
stream: "Part E: Transducers and Measurement"
aliases: ["thermocouple", "Seebeck effect", "cold-junction compensation", "CJC", "reference junction", "ice bath"]
tags: [feeg1004, concept, transducers, temperature]
status: complete
parent_lectures: ["[[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]"]
related_concepts: ["[[RTDs and Thermistors]]", "[[Passive and Active Transducers]]"]
sources: ["02 - Sources/S2 Transducers/S2-W26-31 Transducers 01 - Measurement Systems - Lecture Slides.pdf"]
---

# Thermocouples and Cold-Junction Compensation

## Definition

> [!note] Definition
> Two dissimilar metals joined at a junction develop a temperature-dependent contact potential. With two junctions at different temperatures, the net EMF (Seebeck effect) is
> $$V\approx S\,(T_{hot} - T_{ref}),\qquad S\sim\text{tens of }\mu\mathrm V/°\mathrm C$$
> It is an **active**, **differential** sensor.

## Explanation
- It measures a temperature *difference*. For absolute readings the reference junction temperature must be known.
- **Ice bath**: the classic 0 °C reference, impractical outside the lab.
- **Cold-junction compensation**: an IC (silicon transistor) sensor measures the terminal temperature, and the electronics add the equivalent EMF.
- Extra junctions (to copper leads) cancel if they are at the same temperature.
- The signal is small (µV), so it needs amplification. Dedicated amplifiers include CJC and give e.g. 10 mV/°C.

## Examples
- Type J (iron–constantan) ≈ 52 µV/°C; type K ≈ 41 µV/°C.

## Related
- Topic notes: [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- Year 2: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] (thermoelectric sensing) · engine temperatures, [[Turbine Entry Temperature and Blade Cooling]]

## Sources
- Transducers lecture 1

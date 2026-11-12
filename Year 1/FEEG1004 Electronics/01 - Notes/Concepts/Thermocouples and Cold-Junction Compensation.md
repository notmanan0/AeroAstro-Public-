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

A thermocouple is a pair of dissimilar metals joined at two junctions; each junction develops a temperature-dependent contact potential, and with the junctions at different temperatures the net EMF (the **Seebeck effect**) is

$$
V\approx S\,(T_{hot} - T_{ref}),\qquad S\sim\text{tens of }\mu\mathrm V/°\mathrm C
$$

It is an active, differential sensor: it generates its own signal, and that signal measures a temperature difference. For an absolute reading the temperature of the reference junction must be known. The classic reference is an ice bath at 0 °C, which is impractical outside the laboratory. **Cold-junction compensation** (CJC) replaces it: an IC sensor based on a silicon transistor measures the temperature of the terminals, and the electronics add the equivalent EMF. The extra junctions formed where the thermocouple wires meet the copper leads cancel, provided they are at the same temperature.

The sensitivity is about 52 µV/°C for type J (iron–constantan) and about 41 µV/°C for type K. A signal of microvolts needs amplification, and dedicated thermocouple amplifiers include CJC and give an output such as 10 mV/°C.

## Related

- [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]
- [[RTDs and Thermistors]] · [[Passive and Active Transducers]]
- Year 2: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] (thermoelectric sensing) · engine temperatures, [[Turbine Entry Temperature and Blade Cooling]]
- Sources: Transducers lecture 1

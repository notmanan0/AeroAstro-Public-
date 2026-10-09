---
title: "Maximum Power Transfer"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["maximum power transfer theorem", "impedance matching", "R_L = R_TH"]
tags: [feeg1004, concept, dc-circuits, power]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Thevenin and Norton Equivalent Circuits]]", "[[Electric Current and Electrical Power]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf"]
---

# Maximum Power Transfer

## Definition

> [!note] Definition
> A source $(V_{TH}, R_{TH})$ delivers the most power to a resistive load when
> $$R_L = R_{TH},\qquad P_{max} = \frac{V_{TH}^2}{4R_{TH}},\qquad \eta = 50\ \%$$

## Explanation
- $P = V_{TH}^2R_L/(R_L + R_{TH})^2$. Differentiate and set to zero to get $R_L = R_{TH}$.
- At the optimum, half the power is lost in the source. **Power systems avoid it** ($R_L\gg R_{TH}$ for efficiency); **signal systems** (antennas, RF) use it.
- The ideal 5 V source shorted by 1 mΩ "delivering 25 kW" shows why real sources need $R_{TH}$ in their models.

## Examples
- A 13 V car battery with 10 mΩ ESR could in principle deliver 4.2 kW into 10 mΩ, with the battery dissipating the same.

![[ee_a7_battery_model.png|700]]

## Related
- Topic notes: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Cross-module: the solar-array maximum-power point, [[Solar Cells and Arrays]] · [[Link Budget Equation]] (matched RF chains)

## Sources
- Recorded lecture 7a (real-world sources); derived

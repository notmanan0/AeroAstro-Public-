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

A source with Thévenin voltage $V_{TH}$ and resistance $R_{TH}$ delivers the most power to a resistive load when the load resistance equals the source resistance. At that point the source wastes as much power internally as it delivers, so the efficiency is $50\ \%$.

$$
R_L = R_{TH},\qquad P_{max} = \frac{V_{TH}^2}{4R_{TH}},\qquad \eta = 50\ \%
$$

The load current is $V_{TH}/(R_L + R_{TH})$, so the load power is $P = V_{TH}^2R_L/(R_L + R_{TH})^2$. Differentiating with respect to $R_L$ and setting the result to zero gives $R_L = R_{TH}$, and substituting back gives $P_{max}$.

Because half the power is lost in the source at the optimum, power systems deliberately avoid it and run with $R_L\gg R_{TH}$ for efficiency. Signal systems such as antennas and RF chains, where the signal is weak and efficiency matters less, are matched for maximum power instead.

The theorem also shows why a real source must be modelled with its internal resistance. An ideal $5\ \mathrm V$ source shorted by $1\ \mathrm{m\Omega}$ would deliver $25\ \mathrm{kW}$, which no real source can do. A $13\ \mathrm V$ car battery with $10\ \mathrm{m\Omega}$ internal resistance could in principle deliver $4.2\ \mathrm{kW}$ into a matched $10\ \mathrm{m\Omega}$ load, while dissipating the same $4.2\ \mathrm{kW}$ inside itself.

![[ee_a7_battery_model.png|700]]

## Related

- [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Cross-module: the solar-array maximum-power point, [[Solar Cells and Arrays]] · [[Link Budget Equation]] (matched RF chains)
- Sources: Recorded lecture 7a (real-world sources); derived

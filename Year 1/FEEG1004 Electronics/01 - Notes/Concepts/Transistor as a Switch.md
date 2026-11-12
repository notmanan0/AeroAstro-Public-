---
title: "Transistor as a Switch"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["transistor switch", "low-side switch", "saturated switch", "driving a relay", "driving a motor"]
tags: [feeg1004, concept, transistor, switching]
status: complete
parent_lectures: ["[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
related_concepts: ["[[Bipolar Junction Transistor]]", "[[MOSFET]]", "[[Flyback Diode]]", "[[Electromechanical Relays]]"]
sources: ["02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §1.6.7"]
---

# Transistor as a Switch

A transistor used as a switch is driven either fully OFF (cut-off) or fully ON (a saturated BJT with $V_{CE}\approx0.2$ V, or a MOSFET at its on-resistance $R_{DS(on)}$), so that a low-current logic signal can switch a high-current load. A microcontroller pin supplies only about 20 mA, far too little to drive a motor directly.

In the usual **low-side** placement the transistor sits between the load and ground. Designing a BJT switch takes three steps:

1. The minimum base current is $I_{B,min} = I_{load}/\beta$.
2. The base resistor is $R_B = (V_{drive} - 0.7)/I_B$, usually chosen smaller than this to guarantee saturation.
3. The load resistor $R_L$ sets the load current, $R_L = (V_{CC} - V_{load} - V_{CE,sat})/I$.

For an LED switch (Week 8) these steps give a 1.43 kΩ base resistor and a 31.3 Ω collector resistor.

A MOSFET switch needs its gate driven above the threshold voltage, and draws no steady gate current. The power it dissipates is $I^2R_{DS(on)}$, which must be checked against its rating: a motor switch carrying 50 A with $R_{DS(on)}$ = 0.04 Ω dissipates 100 W. An inductive load such as a motor or relay coil always needs a flyback diode across it.

A simple thermostat chains these pieces together: an NTC thermistor divider drives a BJT, which switches a relay, which switches a mains heater.

![[ee_b3_transistor_switches.png|700]]

## Related

- [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- [[Bipolar Junction Transistor]] · [[MOSFET]] · [[Flyback Diode]] · [[Electromechanical Relays]] · [[DC Motor Speed Control]]
- Sources: Week 8 session; Mills notes §1.6.7

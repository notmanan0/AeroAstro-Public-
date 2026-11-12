---
title: "MOSFET"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["field-effect transistor", "FET", "enhancement mode", "RDS(on)", "gate threshold", "JFET"]
tags: [feeg1004, concept, transistor]
status: complete
parent_lectures: ["[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
related_concepts: ["[[Bipolar Junction Transistor]]", "[[Transistor as a Switch]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf", "Mills notes §1.6.3–1.6.7", "Week 8 session"]
---

# MOSFET

A MOSFET is a voltage-controlled transistor whose insulated (oxide) gate draws almost no current. In the n-channel **enhancement** type, a gate–source voltage above the threshold (about 1–2 V) forms an inversion layer that lets drain current flow, and when fully on the channel behaves as a resistance $R_{DS(on)}$ dissipating

$$
P = I^2R_{DS(on)}
$$

The terminals map onto those of the BJT: drain to collector, gate to base and source to emitter. A **depletion** MOSFET already conducts at $V_{GS} = 0$, and a **JFET** controls its channel with a reverse-biased junction instead of an insulated gate. Against the BJT, the MOSFET has a higher input resistance and is less sensitive to temperature, which makes it the device of choice in integrated circuits (CMOS), but its gain is lower. Used as an amplifier, the common-source stage is inverting, like the common emitter.

As a switch the limit is heating in $R_{DS(on)}$. With $R_{DS(on)}$ = 0.04 Ω and a 100 W dissipation limit, $I = \sqrt{100/0.04}$ = 50 A continuous, with the heat carried away by a heatsink. The near-zero gate current also suits signal sources that can supply only microamps, such as the photodiode in a night-light circuit.

## Related

- [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- [[Transistor as a Switch]] · [[Bipolar Junction Transistor]] · [[DC Motor Speed Control]]
- Sources: Mills notes §1.6.3–1.6.7; Week 8 session

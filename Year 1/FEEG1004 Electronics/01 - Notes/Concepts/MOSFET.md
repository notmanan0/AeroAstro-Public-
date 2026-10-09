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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf"]
---

# MOSFET

## Definition

> [!note] Definition
> A voltage-controlled transistor. In the n-channel **enhancement** type, a gate–source voltage above the threshold (~1–2 V) forms an inversion layer that lets drain current flow. The insulated (oxide) gate draws **almost no current**. Fully ON, it behaves as a resistance $R_{DS(on)}$:
>
> $$P = I^2R_{DS(on)}$$

## Explanation
- Terminals map to the BJT's: drain ↔ collector, gate ↔ base, source ↔ emitter.
- **Depletion** MOSFETs conduct at $V_{GS} = 0$. **JFETs** control their channel with a reverse-biased junction.
- Compared with BJTs: higher input resistance and less temperature sensitivity, ideal for ICs (CMOS), but lower gain.
- The common-source amplifier is inverting, like the common emitter.

## Examples
- $R_{DS(on)}$ = 0.04 Ω with a 100 W limit allows 50 A continuous. The heat goes to a heatsink.
- Photodiode night-light: a MOSFET suits a signal source that can supply only µA.

## Related
- Topic notes: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Concepts: [[Transistor as a Switch]] · [[Bipolar Junction Transistor]] · [[DC Motor Speed Control]]

## Sources
- Mills notes §1.6.3–1.6.7; Week 8 session

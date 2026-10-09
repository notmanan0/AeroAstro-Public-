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
sources: ["02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf", "02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Transistor as a Switch

## Definition

> [!note] Definition
> A transistor driven fully OFF (cut-off) or fully ON (saturated BJT, $V_{CE}\approx0.2$ V; or MOSFET at $R_{DS(on)}$) lets a low-current logic signal switch a high-current load.

## Explanation
- **BJT design**:
  1. $I_{B,min} = I_{load}/\beta$.
  2. $R_B = (V_{drive} - 0.7)/I_B$, usually chosen smaller to guarantee saturation.
  3. $R_L$ sets the load current: $(V_{CC} - V_{load} - V_{CE,sat})/I$.
- **MOSFET**: drive the gate above threshold; no gate current is needed. Check $I^2R_{DS(on)}$ against the power rating.
- **Low-side** placement: the transistor sits between the load and ground.
- Always add a **flyback diode** for inductive loads.
- Microcontroller pins give about 20 mA, far too little to drive motors directly.

![[ee_b3_transistor_switches.png|700]]

## Examples
- W8 LED switch: 1.43 kΩ base and 31.3 Ω collector resistor.
- MOSFET motor switch: 50 A at 0.04 Ω and 100 W.
- Mills thermostat: NTC divider → BJT → relay → mains heater.

## Related
- Topic notes: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Concepts: [[Flyback Diode]] · [[Electromechanical Relays]] · [[DC Motor Speed Control]]

## Sources
- Week 8 session; Mills notes §1.6.7

---
title: "Flyback Diode"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["freewheeling diode", "snubber diode", "protective diode", "clamp diode"]
tags: [feeg1004, concept, inductor, diode, protection]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]", "[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]", "[[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]"]
related_concepts: ["[[Inductance]]", "[[Transistor as a Switch]]", "[[Electromechanical Relays]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 08 - DC Motor Control - Lecture Slides.pdf"]
---

# Flyback Diode

## Definition

> [!note] Definition
> A diode placed across an inductive load (relay coil, solenoid, motor), **reverse-biased in normal operation**. When the drive switch opens, it gives the inductor current a loop to circulate and decay through, clamping the voltage to about supply + 0.7 V.

## Explanation
- The inductor current cannot stop instantly. Without a path, $v = L\,di/dt$ climbs until the switch arcs or the transistor breaks down (hundreds of volts).
- With the diode, the stored $\tfrac{1}{2}LI^2$ dissipates in the coil resistance with $\tau = L/R$.
- In a **DC chopper** the same diode is the **freewheeling diode**: it keeps the motor current continuous while the transistor is off (answer b in DC Machines 08).

![[ee_a7_flyback.png|640]]

## Examples
- Relay coil 5 V, 101 Ω: $i(0^-)$ = 49.6 mA. Without a diode, a 10 kΩ gap leakage path would see ~500 V.
- The Mills BJT heater circuit and the MOSFET motor switch both need it.

## Related
- Topic notes: [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Concepts: [[Inductance]] · [[Transistor as a Switch]] · [[DC Motor Speed Control]]

## Sources
- Recorded lecture 7c; Mills notes §1.6.7; DC Machines 08 slides

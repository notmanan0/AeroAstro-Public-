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

A flyback diode is a diode connected across an inductive load such as a relay coil, solenoid or motor, oriented so that it is reverse-biased in normal operation. When the drive switch opens, it gives the inductor current a loop to circulate and decay through, clamping the switch voltage to about the supply plus $0.7\ \mathrm V$.

![[ee_a7_flyback.png|640]]

The diode is needed because inductor current cannot stop instantly. If the switch opens with no other path available, $v = L\,di/dt$ rises until something gives way: the switch contacts arc or the transistor breaks down, typically at hundreds of volts. A $101\ \Omega$ relay coil on a $5\ \mathrm V$ supply carries $i(0^-)=5/101=49.5\ \mathrm{mA}$; forced through a $10\ \mathrm{k\Omega}$ leakage path across the open gap, that current would produce about $500\ \mathrm V$.

With the diode in place, the coil current flows round the coil–diode loop instead, and the stored energy $\tfrac{1}{2}LI^2$ is dissipated in the coil resistance with time constant $\tau = L/R$. The BJT heater switch and the MOSFET motor switch in B3 both need one.

In a DC chopper the same component is called the **freewheeling diode**. It keeps the motor armature current continuous during the intervals when the transistor is off (DC Machines 08 question, answer (b)).

## Related

- [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- [[Inductance]] · [[Transistor as a Switch]] · [[DC Motor Speed Control]]
- Sources: Recorded lecture 7c; Mills notes §1.6.7; DC Machines 08 slides

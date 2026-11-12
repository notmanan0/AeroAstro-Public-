---
title: "Electromechanical Relays"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["relay", "SPDT", "DPST", "normally open", "normally closed"]
tags: [feeg1004, concept, relay, switching]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Flyback Diode]]", "[[Transistor as a Switch]]", "[[Inductance]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf"]
---

# Electromechanical Relays

A relay is an electrically operated switch: current in a **coil** magnetises a core, which pulls an **armature** and moves a set of contacts. A small control current can therefore switch a large load, possibly at mains voltage.

Relays are described by their **poles**, the number of independent switches, and their **throws**, the number of contacts each switch can connect to, giving types such as SPST, SPDT and DPST. Normally open (NO) and normally closed (NC) describe the contacts with the coil de-energised. A relay is chosen by its contact current and voltage ratings (the AC and DC ratings differ), its coil voltage and its coil resistance. Switching a $1\ \mathrm{kW}$, $230\ \mathrm V$ lamp, for example, needs contacts rated above $1000/230=4.3\ \mathrm A$.

Electrically, the coil is a resistance $R$ in series with an inductance $L$, and the contacts add a small contact resistance. The pull-in voltage has to appear across the coil itself, not just across the drive circuit. An $83\ \Omega$ indicator lamp placed in series with a $101\ \Omega$ coil on a $5\ \mathrm V$ supply leaves only $2.74\ \mathrm V$ across the coil, so the relay fails to operate; the lamp belongs in parallel with the coil instead.

Because the coil is inductive, the transistor or switch that drives it needs a [[Flyback Diode]] to protect it when the coil current is interrupted.

## Related

- [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- [[Transistor as a Switch]] · [[Potential Divider]]
- Sources: Recorded lecture 7c; Mills notes §1.6.7

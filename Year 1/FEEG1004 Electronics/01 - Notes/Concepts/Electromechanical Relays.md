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

## Definition

> [!note] Definition
> An electrically operated switch: current in a **coil** magnetises a core that pulls an **armature**, moving contacts. A small control current switches a large, possibly mains, load.

## Explanation
- **Poles** = number of independent switches; **throws** = contacts per switch (SPST, SPDT, DPST, ...). NO/NC describe the contacts with the coil **de-energised**.
- **Equivalent circuit**: coil $R$ in series with $L$, plus contact resistance. The pull-in voltage must actually appear **across the coil**.
- Select by contact current and voltage (AC and DC ratings differ), coil voltage and coil resistance.
- An inductive coil needs a [[Flyback Diode]] on its driver.

## Examples
- A 1 kW, 230 V lamp needs a relay rated above 4.3 A.
- An 83 Ω indicator lamp in **series** with a 101 Ω coil leaves only 2.74 V for the coil, so it fails. Put the lamp in parallel.

## Related
- Topic notes: [[FEEG1004 A7 - Thevenin, Superposition and Relays]] · [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Concepts: [[Transistor as a Switch]] · [[Potential Divider]]

## Sources
- Recorded lecture 7c; Mills notes §1.6.7

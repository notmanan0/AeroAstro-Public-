---
title: "Bipolar Junction Transistor"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["BJT", "npn transistor", "I_C = beta I_B", "current gain", "common emitter", "saturation", "active mode"]
tags: [feeg1004, concept, transistor]
status: complete
parent_lectures: ["[[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]"]
related_concepts: ["[[MOSFET]]", "[[Transistor as a Switch]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "02 - Sources/S1 Electronics/S1-W08-EL2 Transistors - Recorded.pdf"]
---

# Bipolar Junction Transistor

## Definition

> [!note] Definition
> An npn BJT is a current-controlled device:
> - **Active**: $V_{BE}\approx0.7$ V and $I_C = \beta I_B$ ($\beta\sim100$–200).
> - **Saturation**: $V_{CE}\approx0.2$ V and $I_C < \beta I_B$ (a closed switch).
> - **Cut-off**: $I_B = 0$ (an open switch).

## Explanation
- A narrow, lightly doped base lets about 99 % of the emitter electrons reach the collector.
- The active model holds only if the collector circuit can supply $\beta I_B$ with $V_{CE}$ > about 0.2 V. Otherwise the transistor saturates.
- **Common-emitter amplifier**: $V_{out} = V_{CC} - \beta I_BR_C$. It is **inverting**, biased at about $V_{CC}/2$, with coupling capacitors blocking DC.
- A Darlington pair has gain $\beta_1\beta_2$.

![[ee_b3_bjt_characteristics.png|640]]

## Examples
- A 300 mA LED switch needs $I_B$ = 3 mA, so $R_B$ = 1.43 kΩ and $R_L$ = 31.3 Ω.

## Related
- Topic notes: [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- Concepts: [[Transistor as a Switch]] · [[MOSFET]] · [[P-N Junction Diode]]

## Sources
- Mills notes §1.6.1–1.6.2; Week 8 session

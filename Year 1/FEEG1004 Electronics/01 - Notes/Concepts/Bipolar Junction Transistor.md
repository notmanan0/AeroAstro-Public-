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

An npn bipolar junction transistor is a current-controlled device in which a small base current controls a much larger collector current. It has three operating modes: active, saturation and cut-off.

In the **active** mode the base–emitter junction is forward biased with $V_{BE}\approx0.7\ \mathrm V$ and the collector current is $I_C=\beta I_B$, with $\beta$ typically $100$–$200$. The gain comes from the narrow, lightly doped base, which lets about $99\ \%$ of the electrons leaving the emitter reach the collector. The active model holds only if the collector circuit can supply $\beta I_B$ while keeping $V_{CE}$ above about $0.2\ \mathrm V$. If it cannot, the transistor **saturates**: $V_{CE}\approx0.2\ \mathrm V$, $I_C<\beta I_B$, and the device behaves as a closed switch. With $I_B=0$ it is in **cut-off** and behaves as an open switch.

As an amplifier, the common-emitter stage gives $V_{out}=V_{CC}-\beta I_BR_C$. It is inverting, it is biased at about $V_{CC}/2$ so the output can swing both ways, and coupling capacitors block the DC bias from the source and load. A Darlington pair has overall gain $\beta_1\beta_2$.

![[ee_b3_bjt_characteristics.png|640]]

As a switch, a $300\ \mathrm{mA}$ LED load needs $I_B=3\ \mathrm{mA}$, which gives $R_B=1.43\ \mathrm{k\Omega}$ and $R_L=31.3\ \Omega$.

## Related

- [[FEEG1004 B3 - Transistors - BJT and MOSFET Switches and Amplifiers]]
- [[Transistor as a Switch]] · [[MOSFET]] · [[P-N Junction Diode]]
- Sources: Mills notes §1.6.1–1.6.2; Week 8 session

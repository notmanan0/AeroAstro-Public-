---
title: "Op-Amp Comparator"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["comparator", "open-loop op-amp", "zero-crossing detector", "PWM comparator"]
tags: [feeg1004, concept, op-amp]
status: complete
parent_lectures: ["[[FEEG1004 B4 - Operational Amplifiers]]"]
related_concepts: ["[[Op-Amp Golden Rules]]", "[[RTDs and Thermistors]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §2.1–2.2", "Week 9 session"]
---

# Op-Amp Comparator

A comparator is an op-amp used without feedback. Its open-loop gain $A_{OL}$ is so large that the output saturates at one rail or the other, depending on which input is higher.

$$
V_{out} = \begin{cases}+V_{sat} & V_+ > V_-\\ -V_{sat} & V_+ < V_-\end{cases}\qquad V_{sat}\approx V_{CC} - 1\ \mathrm V
$$

The output is linear only while $|V_+ - V_-|$ is below about 70 µV. Outside that tiny window it is binary, so the circuit compares two voltages instead of amplifying their difference. With no negative feedback, the [[Op-Amp Golden Rules]] do not apply.

The same behaviour has several uses. Comparing a sine wave with zero turns it into a square wave (a zero-crossing detector), and comparing a triangle wave with a variable reference produces a PWM signal. A sensor divider compared with a reference divider gives a threshold alarm, and a bank of comparators forms the core of a flash ADC.

![[ee_b4_opamp_open_loop.png|700]]

An NTC thermistor light switch trips when the sensor divider ratio equals the reference ratio, so for a thermistor of 5 kΩ at 40 °C the reference needs $R$ = 2.5 kΩ.

## Related

- [[FEEG1004 B4 - Operational Amplifiers]]
- [[Op-Amp Golden Rules]] · [[RTDs and Thermistors]] · [[Potential Divider]] · [[DC Motor Speed Control]] (PWM)
- Year 2: [[ADC Quantisation and Resolution]]
- Sources: Mills notes §2.1–2.2; Week 9 session

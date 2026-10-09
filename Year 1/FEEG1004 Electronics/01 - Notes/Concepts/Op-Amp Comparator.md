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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Op-Amp Comparator

## Definition

> [!note] Definition
> An op-amp **without feedback**. Because $A_{OL}$ is huge, the output saturates:
> $$V_{out} = \begin{cases}+V_{sat} & V_+ > V_-\\ -V_{sat} & V_+ < V_-\end{cases}\qquad V_{sat}\approx V_{CC} - 1\ \mathrm V$$

## Explanation
- Linear only for |V₊ − V₋| < ~70 µV. Otherwise it is binary, so it **compares** two voltages.
- The golden rules do **not** apply.
- Uses:
  - sine → square (zero-crossing detector);
  - triangle vs a variable reference gives PWM;
  - threshold alarms with a sensor divider against a reference divider;
  - the core of flash ADCs.

![[ee_b4_opamp_open_loop.png|700]]

## Examples
- NTC thermistor light switch: it trips when the sensor divider ratio equals the reference ratio ($R$ = 2.5 kΩ for 5 kΩ at 40 °C).

## Related
- Topic notes: [[FEEG1004 B4 - Operational Amplifiers]]
- Concepts: [[RTDs and Thermistors]] · [[Potential Divider]] · [[DC Motor Speed Control]] (PWM)
- Year 2: [[ADC Quantisation and Resolution]]

## Sources
- Mills notes §2.1–2.2; Week 9 session

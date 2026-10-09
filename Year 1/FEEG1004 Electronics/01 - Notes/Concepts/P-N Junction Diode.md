---
title: "P-N Junction Diode"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["diode", "p-n junction", "depletion region", "forward bias", "reverse bias", "0.7 V drop", "ideal diode"]
tags: [feeg1004, concept, semiconductors, diode]
status: complete
parent_lectures: ["[[FEEG1004 B1 - Semiconductors and Diodes]]"]
related_concepts: ["[[Band Theory and Semiconductor Doping]]", "[[Rectification and Smoothing]]", "[[Zener Diode Regulator]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# P-N Junction Diode

## Definition

> [!note] Definition
> A junction of p- and n-type semiconductor that conducts in one direction.
> - **Forward bias** (anode +): conducts once $V_D\approx0.7$ V (Si) or 0.3 V (Ge).
> - **Reverse bias**: blocks (µA leakage) until breakdown.
>
> The symbol's arrow points anode (p) → cathode (n), the direction of forward current.

## Explanation
- **Depletion region**: carriers diffuse across and recombine, leaving fixed ions and a built-in field. Reverse bias widens it; forward bias narrows it.
- **Circuit models**:
  - ideal (short/open);
  - constant drop (0.7 V source when ON);
  - the full exponential (for completeness).
- **Solve by assumption**: guess ON/OFF, solve, check the current direction or voltage, and revise if inconsistent.
- LEDs have larger forward voltages (~2–3 V, depending on colour).

![[ee_b1_diode_vi.png|700]]

## Examples
- Tutorial 3 Q1: four ideal-diode circuits; only forward-biased diodes conduct (2 mA each way).
- LED on 5 V with 2.1 V at 60 mA: $R$ = 48 Ω.

## Related
- Topic notes: [[FEEG1004 B1 - Semiconductors and Diodes]] · [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- Concepts: [[Rectification and Smoothing]] · [[Diode Limiters and Clamps]] · [[Zener Diode Regulator]] · [[Flyback Diode]]

## Sources
- Mills notes §1.4–1.5.1; Week 7 interactive session

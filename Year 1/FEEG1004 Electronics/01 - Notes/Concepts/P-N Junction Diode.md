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
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf", "Mills notes §1.4–1.5.1", "Week 7 interactive session"]
---

# P-N Junction Diode

A p-n junction diode is a junction of p- and n-type semiconductor that conducts in one direction. **Forward biased** (anode positive) it conducts once $V_D\approx0.7$ V for silicon or 0.3 V for germanium; **reverse biased** it blocks, passing only microamps of leakage, until breakdown.

The arrow of the circuit symbol points from anode (p) to cathode (n), the direction of forward current. At the junction, carriers diffuse across and recombine, leaving a **depletion region** of fixed ions with a built-in field. Reverse bias widens this region and forward bias narrows it until current flows. LEDs work the same way but have larger forward voltages, about 2–3 V depending on colour.

![[ee_b1_diode_vi.png|700]]

Circuit analysis uses one of three models: the ideal diode (a short circuit when on, an open circuit when off), the constant-drop model (a 0.7 V source when on), and the full exponential characteristic, given for completeness. With any of them a circuit is solved by assumption: guess whether each diode is on or off, solve, check that the current direction or voltage agrees with the guess, and revise if it does not. In Tutorial 3 Q1, four ideal-diode circuits reduce this way to conduction through the forward-biased diodes only, with 2 mA in each direction. To run an LED with 2.1 V at 60 mA from 5 V, the series resistor is $R = (5 - 2.1)/0.06$ = 48 Ω.

## Related

- [[FEEG1004 B1 - Semiconductors and Diodes]] · [[FEEG1004 B2 - Diode Circuits - Rectifiers, Regulators, Limiters and Clamps]]
- [[Band Theory and Semiconductor Doping]] · [[Rectification and Smoothing]] · [[Diode Limiters and Clamps]] · [[Zener Diode Regulator]] · [[Flyback Diode]]
- Sources: Mills notes §1.4–1.5.1; Week 7 interactive session

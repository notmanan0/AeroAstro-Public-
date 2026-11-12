---
title: "Thevenin and Norton Equivalent Circuits"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Thevenin", "Thévenin equivalent", "Norton equivalent", "open-circuit voltage", "source resistance", "ESR"]
tags: [feeg1004, concept, dc-circuits, network-theorems]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Superposition Theorem (Circuits)]]", "[[Maximum Power Transfer]]", "[[Loading Effect and Buffering]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf"]
---

# Thevenin and Norton Equivalent Circuits

Any two-terminal linear network is equivalent, at its terminals, to a **Thévenin** source $V_{TH}$ (the open-circuit voltage) in series with $R_{TH}$, or to a **Norton** source $I_N = V_{TH}/R_{TH}$ (the short-circuit current) in parallel with $R_N = R_{TH}$. $R_{TH}$ is the resistance seen at the terminals with every independent source zeroed: voltage sources shorted and current sources opened.

The terminal V–I line is

$$
V = V_{TH} - IR_{TH}
$$

so its intercept is the open-circuit voltage and its slope is minus the source resistance. Batteries (through their ESR), power supplies and amplifier outputs are specified in this form. The method is to identify the network to be replaced, find $R_{TH}$, then $V_{TH}$, and attach the load. In AC circuits $R_{TH}$ becomes an impedance $Z_{TH}$.

One network (Lecture 7a) reduces to 11 V and 5/3 Ω, so a 3 Ω load takes 2.36 A. Another (Week 6) gives 13.3 V and 6.67 Ω, so a 40 Ω load takes 0.286 A. Tutorial 2 Q3 gives 0.75 V and 8.5 Ω. In Tutorial 8 Q1 the loaded RC filter is a Thévenin source $KV_{in}$ with resistance $R_1\parallel R_L$ driving $C$.

![[ee_a7_thevenin_example.png|700]]

## Related

- [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- [[Maximum Power Transfer]] · [[Superposition Theorem (Circuits)]] · [[Loading Effect and Buffering]]
- Sources: Recorded lecture 7a; Week 6 interactive session

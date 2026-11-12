---
title: "Ideal Transformer"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["transformer", "turns ratio", "step-up", "step-down", "V1/V2 = N1/N2"]
tags: [feeg1004, concept, machines, transformer]
status: complete
parent_lectures: ["[[FEEG1004 C3 - Transformers and AC Power Transmission]]"]
related_concepts: ["[[Transformer EMF Equation]]", "[[Faraday's Law and Lenz's Law]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Ideal Transformer

An ideal transformer is two windings on a shared magnetic core, with no losses, whose voltages are in the ratio of their turns and whose currents are in the inverse ratio. It changes the level of an AC voltage while passing the same power.

$$
\frac{V_1}{V_2} = \frac{N_1}{N_2},\qquad V_1I_1 = V_2I_2\ \Rightarrow\ \frac{I_2}{I_1} = \frac{N_1}{N_2},\qquad \eta = \frac{P_2}{P_1}\ (\to99\ \%\ \text{large units})
$$

The same core flux links both windings, so applying Faraday's law to each gives the same EMF per turn and hence the voltage ratio. With no losses, input and output power are equal, so stepping the voltage up steps the current down by the same factor. Power is therefore transmitted at high voltage, since the $I^2R$ loss in the lines falls with the square of the current. A primary of 400 turns and a secondary of 1000 turns raise $500\ \mathrm V$ to $1250\ \mathrm V$. In Tutorial 5 Q5, a 70:350 turns ratio raises $230\ \mathrm V$ to $1150\ \mathrm V$, and a $10\ \mathrm{kW}$ load draws $43.5\ \mathrm A$ on the primary side.

A transformer works only on AC, since a constant flux induces no EMF. The core is laminated to block the eddy currents that the alternating flux would otherwise drive through solid iron. Large units reach efficiencies near $99\ \%$.

Seen from the primary, a resistive load $R_L$ on the secondary appears as $(N_1/N_2)^2R_L$. This is a standard result, derived in [[FEEG1004 C3 - Transformers and AC Power Transmission]].

## Related

- [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- [[Transformer EMF Equation]] · [[Linear Variable Differential Transformer]]
- Sources: Sharkh notes §3.5; Machines 04 slides

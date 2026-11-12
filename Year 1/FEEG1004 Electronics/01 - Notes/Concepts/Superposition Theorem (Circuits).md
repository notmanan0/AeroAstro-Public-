---
title: "Superposition Theorem (Circuits)"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["superposition theorem", "circuit superposition", "zeroing sources"]
tags: [feeg1004, concept, dc-circuits, linearity]
status: complete
parent_lectures: ["[[FEEG1004 A7 - Thevenin, Superposition and Relays]]"]
related_concepts: ["[[Thevenin and Norton Equivalent Circuits]]", "[[Mesh Current Method]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf", "02 - Sources/S1 Fundamentals/S1-W06 Thevenin and Superposition - Interactive.pdf"]
---

# Superposition Theorem (Circuits)

In a **linear** circuit, any voltage or current equals the sum of the contributions from each independent source acting alone, with the other sources zeroed. A zeroed voltage source becomes a short circuit and a zeroed current source becomes an open circuit.

Linearity is essential, so the theorem does not apply to circuits with diodes or saturated transistors unless they have been linearised. Power is not superposable either, because it goes as $I^2R$: find the total current first, then the power.

Every voltage and current is therefore a linear combination of the source values, and with the other sources held fixed it is an affine function of the one that varies. In Tutorial 2 Q2, for example, $i_a = 0.8I_s + 0.048$, where the constant is the contribution of the fixed voltage source. In the Week 6 circuit the two sources contribute 0.4 A and 1.6 A, giving 2.0 A in the 20 Ω resistor. The same idea underpins superposition for beams and the solution of linear ODEs.

Joining two amplifier outputs directly gives $v_{in}\approx\tfrac{5}{6}V_1 + \tfrac{1}{6}V_2$, where the weights depend on the two output impedances. A summing amplifier does the job properly.

![[ee_t2_q2_superposition.png|640]]

## Related

- [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- [[Thevenin and Norton Equivalent Circuits]] · [[Mesh Current Method]]
- Cross-module: [[Superposition for Indeterminate Beams]] · [[Transfer Function]] · [[Method of Undetermined Coefficients]]
- Sources: Recorded lecture 7b; Week 6 interactive session

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
sources: ["02 - Sources/S1 Fundamentals/S1-W06-7abc Thevenin Superposition and Relays - Recorded.pdf"]
---

# Superposition Theorem (Circuits)

## Definition

> [!note] Definition
> In a **linear** circuit, any voltage or current equals the sum of the contributions from each independent source acting alone, with the others zeroed:
> - voltage source → **short circuit**;
> - current source → **open circuit**.

## Explanation
- Linearity is essential: no diodes or saturated transistors (unless linearised). Power is **not** superposable ($I^2R$).
- The result is always an affine function of the sources, e.g. $i_a = 0.8I_s + 0.048$ (Tutorial 2 Q2).
- The same idea underpins beam superposition and linear ODEs.

## Examples
- W6: $0.4 + 1.6$ = 2.0 A in the 20 Ω resistor.
- Joining two amplifier outputs gives $v_{in}\approx\tfrac{5}{6}V_1 + \tfrac{1}{6}V_2$, dependent on output impedances. Use a summing amplifier instead.

![[ee_t2_q2_superposition.png|640]]

## Related
- Topic notes: [[FEEG1004 A7 - Thevenin, Superposition and Relays]]
- Cross-module: [[Superposition for Indeterminate Beams]] · [[Transfer Function]] · [[Method of Undetermined Coefficients]]

## Sources
- Recorded lecture 7b; Week 6 interactive session

---
title: "Magnetomotive Force and Reluctance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["mmf", "reluctance", "magnetic circuit", "F = Ni", "magnetic field intensity H"]
tags: [feeg1004, concept, magnetism, machines]
status: complete
parent_lectures: ["[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Magnetic Flux and Flux Density]]", "[[Inductance]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "02 - Sources/S2 Machines/S2-W18-21 Electric Machines 02 - AC Synchronous Generators - Lecture Slides.pdf"]
---

# Magnetomotive Force and Reluctance

## Definition

> [!note] Definition
> $$\mathcal F = Ni = \oint H\,dl\approx\sum_kH_kl_k,\qquad \mathcal F = \mathcal R\Phi,\qquad \mathcal R = \frac{l}{\mu_0\mu_rA}$$
> This is "Ohm's law" for magnetic circuits: mmf drives flux through reluctance.

## Explanation
- mmf [A-turns] plays the role of voltage, flux of current, and reluctance of resistance.
- Steel has $\mu_r$ of order 10³, so the flux follows the core. Air gaps dominate the total reluctance.
- Self-inductance follows: $L = N\Phi/i = N^2/\mathcal R$. Changing the gap or core position changes $L$, which is how inductive sensors work.
- Steel **saturates** near 1.5 T, so its reluctance rises sharply.

## Examples
- Toroid: 4 A × 100 turns = 400 A-turns; with $\mathcal R = 1.68\times10^6$ A/Wb, $\Phi$ = 0.238 mWb.

## Related
- Topic notes: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[FEEG1004 E2 - Displacement Sensors - Potentiometric, Capacitive and Inductive]]
- Concepts: [[Inductance]] · [[Magnetic Flux and Flux Density]] · [[Linear Variable Differential Transformer]]

## Sources
- Sharkh machines notes §2; Machines 02 slides (toroid question)

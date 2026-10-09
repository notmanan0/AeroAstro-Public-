---
title: "Faraday's Law and Lenz's Law"
module: "FEEG1004 Electronics"
type: concept
stream: "Part A: Electrical Fundamentals and DC Circuits"
aliases: ["Faraday's law", "Lenz's law", "electromagnetic induction", "EMF = -N dPhi/dt"]
tags: [feeg1004, concept, magnetism, induction]
status: complete
parent_lectures: ["[[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]]", "[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]"]
related_concepts: ["[[Magnetic Flux and Flux Density]]", "[[Motional EMF in Electric Machines]]", "[[Inductance]]"]
sources: ["02 - Sources/S1 Fundamentals/S1-W03-2ab Magnetism and Induction - Recorded.pdf"]
---

# Faraday's Law and Lenz's Law

## Definition

> [!note] Definition
>
> $$\mathcal E = -N\frac{d\Phi}{dt}$$
>
> A changing flux through an $N$-turn coil induces an EMF. **Lenz**: its direction drives a current whose field opposes the change.

## Explanation
- Only a **change** of flux matters: a steady field through a stationary coil induces nothing.
- The EMF is minus the gradient of the $\Phi(t)$ graph. It is zero at flux maxima and minima.
- Lenz's law is energy conservation. The more power a generator delivers, the harder it is to turn.
- For a conductor moving through a field, the law reduces to $\mathcal E = BLu$ ([[Motional EMF in Electric Machines]]).
- The induced electric field circulates, so it is **not** an electrostatic potential.

## Examples
- Tutorial 1 Q5: $\mathcal E = 80\pi\sin40\pi t$ V for a 10-turn coil at 20 Hz in 2 T.
- Tutorial 5 Q1: magnet through a coil gives two opposite pulses.

![[ee_a2_magnet_through_coil.png|640]]

## Related
- Topic notes: [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Concepts: [[Inductance]] · [[Transformer EMF Equation]] · [[Linear Variable Differential Transformer]]
- Maths: [[Stokes' Theorem]]

## Sources
- Recorded lecture 2a; Sharkh machines notes §2.1

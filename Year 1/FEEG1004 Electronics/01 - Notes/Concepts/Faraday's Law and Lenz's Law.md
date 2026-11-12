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

Faraday's law states that a changing magnetic flux through an $N$-turn coil induces an EMF equal to $N$ times the rate of change of flux. Lenz's law gives its direction: the induced EMF drives a current whose own field opposes the change of flux.

$$
\mathcal E = -N\frac{d\Phi}{dt}
$$

Only a change of flux induces anything; a steady field through a stationary coil gives no EMF. On a graph of $\Phi(t)$, the EMF is $-N$ times the gradient, so it is zero wherever the flux passes through a maximum or minimum. A magnet pushed through a coil gives two pulses of opposite sign, one as the flux rises on entry and one as it falls on exit (Tutorial 5 Q1).

![[ee_a2_magnet_through_coil.png|640]]

The minus sign is energy conservation. If the induced current reinforced the change, the process would feed itself and create energy from nothing. Instead, the current a generator delivers produces a force opposing the motion, so the more power it supplies, the harder it is to turn.

For a coil rotating in a uniform field the flux varies sinusoidally. A 10-turn coil of area $0.1\ \mathrm{m^2}$ turning at $20\ \mathrm{Hz}$ in $2\ \mathrm T$ gives $\mathcal E = 80\pi\sin40\pi t\ \mathrm V$ (Tutorial 1 Q5). For a straight conductor moving through a field, the law reduces to $\mathcal E = BLu$ ([[Motional EMF in Electric Machines]]).

The induced electric field circulates around the changing flux, so its line integral round a closed loop is not zero. It cannot be described by an electrostatic potential.

## Related

- [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] · [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- [[Inductance]] · [[Transformer EMF Equation]] · [[Linear Variable Differential Transformer]]
- Maths: [[Stokes' Theorem]]
- Sources: Recorded lecture 2a; Sharkh machines notes §2.1

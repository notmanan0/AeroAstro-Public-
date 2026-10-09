---
title: "Motional EMF in Electric Machines"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["E = NBLu", "motional EMF", "generator effect", "Fleming's right-hand rule", "turbo-generator EMF"]
tags: [feeg1004, concept, machines, induction]
status: complete
parent_lectures: ["[[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]]", "[[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]]"]
related_concepts: ["[[Faraday's Law and Lenz's Law]]", "[[Back EMF and Torque Constants]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Motional EMF in Electric Machines

## Definition

> [!note] Definition
> A conductor of active length $L$ cutting a field $B$ at speed $u$ (with $N$ turns):
>
> $$\mathcal E = NBLu$$
>
> In a rotating machine $u = \omega D/2$, and a coil has two active sides.

## Explanation
- It follows from $\Phi = BLx$ and $u = -dx/dt$ in Faraday's law.
- Only flux-cutting conductors contribute; end windings do not.
- Direction: Fleming's **right-hand** rule.
- **Turbo-generator**: $E_{peak} = NB(2L_{rotor})(\omega D/2) = NBL_{rotor}\omega D$.
- **DC machine**: summing $Z/a$ series conductors gives $E = K_E\omega$.

## Examples
- 2-pole, 3000 rpm, 0.8 T, 7 m × 0.7 m rotor, 2 turns: $E_{peak}$ = 2463 V, rms 1742 V.
- Tutorial 5 Q4: 10 turns × 0.7 T × 0.8 m × 3.14 m/s = 17.6 V peak per coil.

## Related
- Topic notes: [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C4 - DC Generators and the Commutator]]
- Concepts: [[Faraday's Law and Lenz's Law]] · [[Back EMF and Torque Constants]]

## Sources
- Sharkh notes §2.1, §3.2, §4.3.1

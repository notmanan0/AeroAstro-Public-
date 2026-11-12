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
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "Sharkh notes §2.1, §3.2, §4.3.1"]
---

# Motional EMF in Electric Machines

Motional EMF is the voltage induced in a conductor that moves through a magnetic field. For $N$ turns of active length $L$ cutting a field $B$ at speed $u$,

$$
\mathcal E = NBLu
$$

The result follows from Faraday's law with the linked flux $\Phi = BLx$ and $u = -dx/dt$. Only conductors that cut flux contribute, so the end windings of a machine add nothing, and the direction of the EMF follows Fleming's **right-hand** rule. In a rotating machine of diameter $D$ the conductor speed is $u = \omega D/2$, and each coil has two active sides. For a turbo-generator this gives

$$
E_{peak} = NB(2L_{rotor})(\omega D/2) = NBL_{rotor}\omega D
$$

In a DC machine, summing the EMFs of the $Z/a$ conductors in series gives $E = K_E\omega$ ([[Back EMF and Torque Constants]]).

A 2-pole turbo-generator at 3000 rpm ($\omega$ = 314 rad/s) with $B$ = 0.8 T, a 7 m × 0.7 m rotor and 2 turns has $E_{peak}$ = 2463 V, or 1742 V rms. In Tutorial 5 Q4, 10 turns × 0.7 T × 0.8 m × 3.14 m/s gives 17.6 V peak per coil.

## Related

- [[FEEG1004 C1 - Magnetic Circuits, Faraday's Law and Force on Conductors]] · [[FEEG1004 C2 - AC Synchronous Generators and Three-Phase Systems]] · [[FEEG1004 C4 - DC Generators and the Commutator]]
- [[Faraday's Law and Lenz's Law]] · [[Back EMF and Torque Constants]]
- Sources: Sharkh notes §2.1, §3.2, §4.3.1

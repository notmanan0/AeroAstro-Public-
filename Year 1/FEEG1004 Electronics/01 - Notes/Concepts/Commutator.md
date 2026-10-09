---
title: "Commutator"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["split ring", "brushes", "mechanical rectifier", "commutation"]
tags: [feeg1004, concept, machines, dc-machine]
status: complete
parent_lectures: ["[[FEEG1004 C4 - DC Generators and the Commutator]]", "[[FEEG1004 C5 - DC Motors - Torque, Back EMF and Efficiency]]"]
related_concepts: ["[[Back EMF and Torque Constants]]", "[[DC Motor Speed Control]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Commutator

## Definition

> [!note] Definition
> A segmented (split) ring on the rotor, contacted by stationary brushes, that reverses each coil's connection every half-turn. It is the key component that makes a machine DC rather than AC.

## Explanation
- **Generator**: it rectifies the coil EMF mechanically. More coils and segments give lower ripple.
- **Motor**: it keeps the current under each pole in one direction, so the torque is unidirectional and the rotor and stator fields stay near 90° (maximum torque per amp).
- **Drawbacks**: friction, sparking (arcing) and brush wear need maintenance. **Brushless** machines replace it with semiconductor switches.

![[ee_c4_commutator_emf.png|640]]

## Related
- Topic notes: [[FEEG1004 C4 - DC Generators and the Commutator]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- Concepts: [[Back EMF and Torque Constants]] · [[Rectification and Smoothing]] (electronic equivalent)

## Sources
- Sharkh notes §4; Machines 05–06, 08 slides

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

A commutator is a segmented (split) ring on the rotor, contacted by stationary brushes, that reverses each coil's connection to the external circuit every half-turn. It is the component that makes a rotating machine DC rather than AC.

In a generator the commutator rectifies the alternating coil EMF mechanically, so the brushes see a unidirectional voltage. A single coil gives a heavily rippled output; more coils and segments reduce the ripple.

In a motor it does the reverse job. By switching the current as each conductor passes from one pole to the next, it keeps the current under each pole flowing in one direction, so the torque is unidirectional and the rotor and stator fields stay near $90^\circ$ apart, which gives the maximum torque per amp.

The cost is friction, sparking (arcing) at the brushes and brush wear, all of which need maintenance. Brushless machines replace the commutator with semiconductor switches.

![[ee_c4_commutator_emf.png|640]]

## Related

- [[FEEG1004 C4 - DC Generators and the Commutator]] · [[FEEG1004 C6 - DC Motor Characteristics and Speed Control]]
- [[Back EMF and Torque Constants]] · [[Rectification and Smoothing]] (electronic equivalent)
- Sources: Sharkh notes §4; Machines 05–06, 08 slides

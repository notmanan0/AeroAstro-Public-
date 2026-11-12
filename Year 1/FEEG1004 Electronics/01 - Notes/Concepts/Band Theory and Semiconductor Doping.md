---
title: "Band Theory and Semiconductor Doping"
module: "FEEG1004 Electronics"
type: concept
stream: "Part B: Electronics"
aliases: ["band gap", "valence band", "conduction band", "n-type", "p-type", "doping", "holes"]
tags: [feeg1004, concept, semiconductors]
status: complete
parent_lectures: ["[[FEEG1004 B1 - Semiconductors and Diodes]]"]
related_concepts: ["[[P-N Junction Diode]]", "[[RTDs and Thermistors]]"]
sources: ["02 - Sources/S1 Electronics/S1 Electronics Notes - Diodes Transistors Op-Amps and Digital - Mills.pdf"]
---

# Band Theory and Semiconductor Doping

In a solid, the discrete energy levels of the atoms broaden into **bands**, and current can flow only if electrons sit in a partly filled band. A **semiconductor** has a full valence band and an empty conduction band separated by a narrow gap ($1.1\ \mathrm{eV}$ in silicon), so heat promotes a few electrons across the gap and leaves mobile **holes** behind.

The width of the gap separates the three classes of material. In a conductor the bands overlap, so there are always free states next to occupied ones. In an insulator the gap is too wide for thermal energy to cross. A semiconductor sits between the two, and because more electrons are promoted as the temperature rises, its conductivity increases with temperature.

A hole behaves as a positive carrier. When a neighbouring valence electron hops into the vacancy, the vacancy moves the other way, so holes drift towards the negative terminal and carry conventional current in the same direction as the electrons.

**Doping** adds carriers deliberately. Group V donors such as phosphorus give **n-type** material with extra electrons; Group III acceptors such as boron give **p-type** material with extra holes. The carriers supplied by doping are the **majority** carriers, while thermal generation supplies the **minority** carriers. The minority population is why semiconductor devices depend on temperature.

![[ee_b1_energy_bands.png|700]]

Two applications follow directly. An NTC thermistor's resistance falls by about $4\ \%$ per $^\circ\mathrm C$ as more carriers are generated thermally, and a photodiode or solar cell uses photons with energy above the gap to create electron–hole pairs.

## Related

- [[FEEG1004 B1 - Semiconductors and Diodes]]
- [[P-N Junction Diode]] · [[RTDs and Thermistors]] · [[MOSFET]]
- Cross-module: [[Solar Cells and Arrays]] · [[Atomic Bonding and Interatomic Potential]]
- Sources: Mills notes §1.2–1.3

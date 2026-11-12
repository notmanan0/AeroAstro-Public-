---
title: "Polymer Glass Transition and Viscoelasticity"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["glass transition temperature", "Tg", "viscoelasticity", "stress relaxation", "relaxation time", "relaxation modulus", "polymer creep", "cold drawing", "stable neck", "damping in polymers"]
tags: [feeg1002, concept, materials, polymers]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C10 - Polymers - Structure and Mechanics]]"]
related_concepts: ["[[Atomic Bonding and Interatomic Potential]]", "[[Creep]]", "[[Ceramic Flaw Sensitivity]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 16 - Polymer Structure and Types.pdf", "02 - Sources/Materials/Lectures/Lecture 17 - Polymer Mechanics.pdf"]
---

# Polymer Glass Transition and Viscoelasticity

The glass transition temperature $T_g$ is the temperature below which the van der Waals bonds between polymer chains are strong enough to stop the chains sliding, so an amorphous or semi-crystalline thermoplastic is glassy and brittle below it and able to flow above it; viscoelasticity is the time-dependent deformation, creep and stress relaxation, that chain sliding produces.

On cooling, the specific volume of a crystalline polymer drops suddenly at the melting temperature $T_m$ as the chains pack into ordered regions. An amorphous polymer shows no step; it contracts as a supercooled liquid until, at $T_g$, the slope of the curve decreases as the chains stop moving. A semi-crystalline polymer shows both. The temperature of a test relative to $T_g$ and $T_m$ sets the shape of the stress–strain curve: below $T_g$ the polymer is linear elastic to brittle fracture at low strain; between $T_g$ and $T_m$ it yields, forms a stable neck that propagates at roughly constant load as the chains align (cold drawing), and fails at very large strain; close to $T_m$ it flows viscously at very low stress. Loading slowly has the same effect as testing hotter.

![[m10_stress_strain_temperature.png|900]]

Held at constant strain, the stress in a thermoplastic falls because chains slip past one another where the local stress is highest. With the rate of relaxation proportional to the stress itself, $d\sigma/dt=-\sigma/\tau$, so

$$
\sigma(t)=\sigma_0\exp\left(-\frac{t}{\tau}\right),\qquad \tau=-\frac{t}{\ln(\sigma/\sigma_0)}
$$

with $\tau$ the relaxation time, after which the stress has fallen to 37 %. The apparent stiffness then depends on time, measured by the relaxation modulus $E_r(t)=\sigma(t)/\varepsilon_0$. Plotted at a fixed time (say 10 s) against temperature, $E_r$ of an amorphous thermoplastic passes through glassy, leathery, rubbery, rubbery-flow and viscous-flow regions, falling by orders of magnitude around $T_g$; a highly crystalline polymer keeps a high $E_r$ until its crystals melt. Creep under constant load is the same mechanism seen the other way round, modelled with springs and a dashpot, and the lag of strain behind stress gives polymers their damping, which peaks near $T_g$.

## Related

- [[FEEG1002 C10 - Polymers - Structure and Mechanics#Specific volume and the two transitions|specific volume and the two transitions]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#The glass transition|the glass transition]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#Three regimes|three regimes]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#Stable neck growth and cold drawing|cold drawing]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#Creep and stress relaxation|creep and stress relaxation]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#The stress-relaxation equation|the stress-relaxation equation]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#The relaxation modulus|the relaxation modulus]] · [[FEEG1002 C10 - Polymers - Structure and Mechanics#Damping|damping]]
- [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q1 - Polypropylene at three temperatures|Tutorial 5, Q1]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q2 - Time dependence and stress relaxation|Q2]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q3 - Relaxation modulus and crystallinity|Q3]]
- [[Atomic Bonding and Interatomic Potential]] · [[Creep]]

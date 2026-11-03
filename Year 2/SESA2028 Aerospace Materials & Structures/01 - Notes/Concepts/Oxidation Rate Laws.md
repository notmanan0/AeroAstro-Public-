---
title: "Oxidation Rate Laws"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["High-temperature oxidation", "Parabolic oxidation", "Linear oxidation", "Logarithmic oxidation", "Protective oxide scale"]
tags: [sesa2028, materials, oxidation, high-temperature, corrosion]
status: lectured
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Evans Diagram and Passivation]]", "[[Thermal Barrier Coatings]]", "[[Gamma Prime Strengthening]]"]
---

# Oxidation Rate Laws

The oxidation rate laws describe how the weight gain of a metal oxidising at high temperature grows with time, linearly for a non-protective oxide, parabolically for a thick adherent one, and logarithmically for a very protective one, reflecting how hard it is for ions to cross the growing scale.

Oxidation is measured by weighing a sample in a furnace; the oxide adds mass unless it is volatile. The oxide forms between metal and gas and so separates them: the metal's reactivity sets the driving force, but temperature, oxygen supply and the defects in the oxide set the rate, and usually the rate dominates. Metal ions form at the metal–oxide interface and oxygen ions at the oxide–gas interface. In a cation-defective oxide the metal ions diffuse out and new oxide grows at the outer surface; in an anion-defective one the oxygen ions diffuse in and new oxide grows at the metal.

![[materials_oxidation_rate_laws.png|700]]

A porous or cracked scale, as on potassium or tantalum, offers no barrier, so the reaction proceeds at a constant rate, $w=k_Lt$, the worst case. A coherent, adherent scale that keeps thickening, as on copper or iron, slows growth because the ions must cross more oxide; if the growth rate is inversely proportional to thickness, integrating gives $x^2\propto t$, the parabolic law $w^2=k_pt+C$. A very protective film grows quickly at first and then almost stops, $w=k_e\log(Ct+A)$, as on aluminium and chromium. Oxides are ceramics, so thermal-expansion or lattice mismatch can crack or spall them and expose fresh metal.

Chromia and alumina protect because they are dense, adherent and nearly defect-free. Too little chromium gives a mixed, defective oxide that can oxidise faster than none at all; above about 12 % a continuous chromia layer forms. In a turbine blade, oxidation consumes load-bearing metal, roughens the aerofoil, sheds erosive debris and attacks grain boundaries ahead of fatigue cracks, so it is fought with chromium and aluminium, cooling, coatings and [[Thermal Barrier Coatings]].

## Related

- Topic: [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys|M8]] · [[SESA2028 M3 - Corrosion, Wear and Surface Engineering|M3]]
- Concepts: [[Evans Diagram and Passivation]] · [[Thermal Barrier Coatings]] · [[Stainless Steel Classes]] · [[Gamma Prime Strengthening]]

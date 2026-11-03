---
title: "Ductile-Brittle Transition"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["DBT", "DBTT", "Ductile to brittle transition"]
tags: [sesa2028, materials, fracture, toughness, charpy]
status: lectured
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Hall-Petch Relation]]", "[[Stainless Steel Classes]]"]
---

# Ductile-Brittle Transition

The ductile-brittle transition is the temperature range over which a material's impact toughness drops from an upper shelf, where it fails by ductile tearing, to a lower shelf, where it fails by brittle cleavage.

It comes from a competition. Plastic flow needs the yield stress $\sigma_y$, cleavage needs the fracture stress $\sigma_f$, and whichever is reached first decides the failure. The fracture stress barely changes with temperature. In body-centred cubic metals such as ferritic steel there are no close-packed slip planes, slip is thermally activated, and the yield stress rises steeply as the temperature falls. Above the temperature where $\sigma_y$ crosses $\sigma_f$ the metal yields first and is ductile; below it, it cleaves. Hexagonal close-packed metals (Mg, Ti) have too few easy slip systems and can show the same behaviour. Face-centred cubic metals (aluminium alloys, austenitic stainless steel, nickel) slip easily on many close-packed planes without thermal activation, so their yield stress stays low and flat and they are ductile at every temperature, which is why austenitic stainless steel is used for cryogenic tanks.

![[materials_dbt_yield_vs_cleavage.png|800]]

Anything that raises the yield stress at a given temperature moves the crossing to a higher temperature. More carbon in steel does this and also lowers the upper-shelf energy, so a stronger steel is less tough and turns brittle at higher temperatures. Grain-boundary segregation of sulphur and phosphorus raises the transition, while a fine grain size, manganese (which ties sulphur up as MnS) and nickel lower it. The Charpy 27 J transition temperatures quoted in the steels lectures make the point: about 42 °C (longitudinal) and 61 °C (transverse) for the Titanic's hull plate, about 23 °C for Liberty-ship steels, and about −18 °C for modern A36 ship plate ([[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]]).

The Charpy test is the natural way to find the transition and to check batch consistency, but it gives an energy, not a design stress; design uses $K_{Ic}$ measured on the lower side of the transition if the part can get that cold.

## Related

- Topic: [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics|M1]] · [[SESA2028 M7 - Steels - Phase Transformations, Heat Treatment and Alloying|M7]] · [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]]
- Concepts: [[Fracture Toughness and LEFM Validity]] · [[Hall-Petch Relation]] · [[Stainless Steel Classes]]

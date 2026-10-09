---
title: "Nernst Equation and Galvanic Series"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, corrosion, electrochemistry]
status: complete
parent: ["[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
related: ["[[Evans Diagram and Passivation]]", "[[Localised Corrosion]]", "[[Corrosion Protection]]"]
---

# Nernst Equation and Galvanic Series

![[Figures/materials_electrode_potentials.png]]

## Standard electrode potentials

Each half-reaction $\mathrm{M^{n+}+ne^-\rightleftharpoons M}$ has a standard potential $E^0$ measured against the standard hydrogen electrode (SHE, 0 V; 1 M ions, 25 °C). **In a couple, the more negative metal is the anode and corrodes.**

Zn-Cu: $E^0_{Zn}=-0.76$ V, $E^0_{Cu}=+0.34$ V. The lecture writes the cell as "most negative minus least negative" $=-1.10$ V; the EMF magnitude is 1.10 V, and Zn dissolves.

Spontaneity: $\Delta G=-nFE$. A positive cell EMF means $\Delta G<0$, so the reaction happens. Fe in acid: $\Delta G=-84.9$ kJ/mol, so it corrodes. Cu in acid: $+65.6$ kJ/mol, so it does not.

## Galvanic series

The practical ranking of metals **and alloys** measured in a real environment (usually seawater). It includes passive states: passive stainless sits near the noble end, active stainless much lower. Use it, rather than $E^0$, to judge real dissimilar-metal joints.

## Nernst equation: concentration matters

$$
E=E^0+\frac{0.0592}{n}\log_{10}[\mathrm{M^{n+}}]\qquad(25\ ^\circ\mathrm C).
$$

(The slide writes $E=E^0-(0.592/n)\log C_{ion}$. The coefficient is 0.0592 V, and the sign depends on whether reduction or oxidation potentials are used.)

**Physical meaning:** a region of the *same* metal with lower ion concentration, or less oxygen at the cathode, has a different potential. That sets up a **concentration cell** with no second metal needed. It drives **crevice corrosion** and **differential aeration** (the water droplet on steel: the oxygen-starved centre becomes the anode).

## Rate is a separate question

Potentials tell you **which** metal corrodes. **How fast** depends on current density (Faraday) and polarisation ([[Evans Diagram and Passivation]]).

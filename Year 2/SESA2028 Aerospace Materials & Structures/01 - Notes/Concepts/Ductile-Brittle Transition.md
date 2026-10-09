---
title: "Ductile-Brittle Transition"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fracture, toughness, charpy]
status: complete
parent: ["[[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]"]
related: ["[[Fracture Toughness and LEFM Validity]]", "[[Hall-Petch Relation]]", "[[Stainless Steel Classes]]"]
---

# Ductile-Brittle Transition

![[Figures/materials_ductile_brittle_transition.png]]

The ductile-brittle transition (DBT) is the temperature range over which a material's impact toughness drops from an upper shelf (ductile, high energy) to a lower shelf (brittle cleavage, low energy).

## Mechanism: yield vs cleavage

- Cleavage fracture stress $\sigma_f$: roughly independent of $T$.
- Yield stress $\sigma_y(T)$: in **BCC** (and HCP) metals slip is thermally activated, so $\sigma_y$ **rises steeply as $T$ falls**.
- Above the crossover, the material yields first (ductile). Below it, $\sigma_f$ is reached first (brittle).
- **FCC** metals (Al, Cu, Ni, austenitic stainless) have many close-packed slip systems that need no thermal activation. $\sigma_y$ stays flat and they **never** show a DBT. That is why austenitic stainless is used for cryogenic tanks.

## What moves the DBT

| Factor | Effect on transition temperature |
|---|---|
| More carbon | raises it (and lowers the upper shelf) |
| Finer grain size | lowers it (Hall-Petch toughening) |
| S, P segregated to grain boundaries | raises it |
| Mn (ties up S as MnS), Ni | lowers it |
| Higher strain rate, thicker section, sharper notch | raise it |

## Examples

Charpy 27 J transition temperatures: Titanic plate +42 °C (longitudinal) and +61 °C (transverse); Liberty ships about +23 °C; modern A36 ship steel about -18 °C.

Mg (HCP) also has a DBT, which is why it is worked hot ([[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium|M6]]).

Charpy testing is ideal for **finding** the transition (ranking and QA), but it gives no design stress.

---
title: "Shot Peening"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, fatigue, residual-stress, surface-engineering]
status: complete
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Goodman Relation]]", "[[S-N Curve and Basquin Law]]", "[[Shrink Fit]]"]
---

# Shot Peening

![[Figures/materials_shot_peening_residual_stress.png]]

Shot peening fires small hard balls (steel, ceramic or glass) at a surface.

## Mechanism

Each impact makes a dimple whose surface layer is plastically **stretched**. On unloading, the elastic material underneath resists the stretched layer and pushes back, leaving the surface in **residual compression** balanced by tension deeper down.

Lecture X-ray diffraction data for a peened tempered-martensite blade steel: about $-600$ MPa at the surface, about $-800$ MPa at about 100 µm (near yield), crossing into balancing tension at about 400 µm.

## Effects

| Effect | Fatigue consequence |
|---|---|
| Compressive residual stress | lowers the **mean** stress ([[Goodman Relation]]); stops shallow cracks opening, so a large HCF and fatigue-limit gain |
| Work-hardened surface | resists slip-band initiation |
| **Rougher surface** | an unwanted side effect: micro-notches. Often followed by light polishing |

It does not change the stress **range**. It helps most in **HCF**, where initiation dominates, and less in high-stress LCF, where plasticity can relax the residual stress.

## Where to use it

At stress concentrations: fillets, spline and keyway roots, fir-tree roots, weld toes, landing-gear components. Laser shock peening and deep rolling are deeper-acting alternatives.

The mechanism is the same as the residual stress left by an autofrettaged or shrink-fitted cylinder ([[Shrink Fit]], [[Lame Thick-Cylinder Solution]]): plasticity locks in a self-equilibrating stress field.

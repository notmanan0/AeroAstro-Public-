---
title: "Fibre Metal Laminates"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["FML", "GLARE", "ARALL", "Hybrid laminate", "Crack bridging"]
tags: [sesa2028, materials, composites, fatigue, damage-tolerance]
status: lectured
parent: ["[[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]]"]
related: ["[[MMC vs CMC]]", "[[Paris Law]]", "[[Total Life vs Damage Tolerance]]"]
---

# Fibre Metal Laminates

A fibre metal laminate is a stack of thin aluminium sheets bonded with fibre-reinforced epoxy plies, glass in GLARE and aramid in ARALL, designed so that intact fibres bridge any fatigue crack in the metal.

The laminate is laid up like a club sandwich, 2000-series aluminium sheet alternating with prepreg, and cured. A fatigue crack starts and grows in an aluminium layer exactly as it would in a solid sheet, but when it reaches a composite ply the interface delaminates locally while the fibres stay whole and attached. They hold the crack faces together behind the tip. In a monolithic sheet the driving force $\Delta K=Q\Delta\sigma\sqrt{\pi a}$ keeps rising as the crack lengthens, which is why Paris-law growth accelerates; in the laminate, the longer the crack, the more load the bridging fibres take, so the stress at the tip falls and the crack can slow to a near-arrest.

![[materials_fibre_bridging.png|800]]

That behaviour is what damage-tolerant design wants: a crack that is found grows slowly and predictably enough to be inspected and repaired. The laminates were developed for exactly that market, aircraft fuselage and wing skins, and keep the metal's familiar behaviour on the outside. The same bridging idea, intact fibres carrying load across a cracked matrix, is what makes [[MMC vs CMC|ceramic matrix composites]] tough.

## Related

- Topic: [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|M5]] · [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[MMC vs CMC]] · [[Paris Law]] · [[Total Life vs Damage Tolerance]]

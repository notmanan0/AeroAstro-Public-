---
title: "Total Life vs Damage Tolerance"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
aliases: ["Total life approach", "Damage-tolerant design", "Safe life"]
tags: [sesa2028, materials, fatigue, lifing, design-philosophy]
status: lectured
parent: ["[[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]"]
related: ["[[Miner's Rule]]", "[[Paris Law]]", "[[S-N Curve and Basquin Law]]"]
---

# Total Life vs Damage Tolerance

The total-life approach predicts the cycles to initiate a crack and grow it to failure from S-N data, while the damage-tolerant approach assumes a crack of known size is already present and predicts how long it takes to grow to the critical size.

A total-life prediction counts $N_i+N_g$ from S-N or strain-life curves, combined over a load spectrum with [[Miner's Rule]] and corrected for mean stress with the [[Goodman Relation]]. Because S-N data are normally measured on well-finished specimens, initiation dominates the result, so the approach in effect designs against initiation. Its weakness is the same fact: the curves depend heavily on surface finish, and a scratch, dent or corrosion pit removes much of the initiation life the curve assumed. It suits smooth parts, or parts that must not crack at all or cannot be inspected.

The damage-tolerant approach accepts the almost inevitable presence of defects. It needs the initial defect size and position from non-destructive testing (dye penetrant, optical, X-ray or ultrasound), the final crack size (usually $a_c$ from $K_{Ic}$ at the peak stress, though a deflection limit or net-section yield could set it), the stress range, and the Paris constants. Integrating the [[Paris Law]] gives the remaining life and so a safe inspection interval. It suits inspectable structures that can tolerate a crack for a while: airframes, pressure vessels, welded offshore structures, turbine discs managed by inspection.

The choice is the first part of most past-paper lifing questions, and the data list is often worth marks on its own.

## Related

- Topic: [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing|M2]]
- Concepts: [[Miner's Rule]] · [[Paris Law]] · [[S-N Curve and Basquin Law]] · [[Goodman Relation]]

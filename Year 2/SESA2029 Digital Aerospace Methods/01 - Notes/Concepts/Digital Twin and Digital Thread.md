---
title: "Digital Twin and Digital Thread"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["digital twin", "digital thread", "digitalisation"]
tags: [sesa2029, concept, digital-design]
status: complete
parent_lectures: ["[[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]"]
related_concepts: ["[[Verification and Validation]]", "[[Model Updating]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L1)", "02 - Sources/CFD/CFD.txt"]
---

# Digital Twin and Digital Thread

## Definition

> [!note] Definition
> A **digital twin** is a digital model of an intended or actual physical product, system or process (the *physical twin*). It is effectively indistinguishable from the real thing for practical purposes: simulation, integration, testing, monitoring and maintenance. A **digital thread** is the record of a product's whole life, from creation to removal. The twin is the *current* state; the thread is the *history*.

## Explanation

Digitalisation serves aerospace engineering in three ways:
1. **Supporting traditional design**: computation complements or replaces physical tests. Wind-tunnel hours per programme have fallen since about 1980.
2. **New design approaches**: multidisciplinary design optimisation (MDO) couples aerodynamics, structures and weight inside an optimiser.
3. **Operations and maintenance**: a twin fed with sensor data detects problems early and predicts when maintenance is needed.

A digital design environment links geometry, pre-processing (meshing), discipline analyses (CFD, FEA) and their coupling, search methods (optimisation) and post-processing. A twin is only as good as its **validation**. Calibrated (updated) FE models and validated CFD are its building blocks, and stochastic model updating can even infer damage for structural health monitoring.

## Examples

- An aerostructural wing loop: CFD loads feed an FE model, deformed shapes feed back into the CFD, and an optimiser adjusts the design until the requirements are met.
- A digital twin of an engine fan tracks each blade's measured vibration against its calibrated FE model to schedule inspection.

## Related

- Parent lectures: [[SESA2029 A1 - Digital Design and the Role of CFD and FEA]]
- Related concepts: [[Verification and Validation]] · [[Model Updating]]
- Module overview: [[SESA2029 Digital Aerospace Methods Hub]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L1)
- 02 - Sources/CFD/CFD.txt

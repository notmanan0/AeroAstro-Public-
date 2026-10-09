---
title: "FE Model Verification Checks"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["free-free modal check", "unit gravity check", "unit enforced displacement check", "rigid body mode check", "model checks"]
tags: [sesa2029, concept, fea, validation]
status: complete
parent_lectures: ["[[SESA2029 B10 - FE Verification, Validation and Model Updating]]"]
related_concepts: ["[[Verification and Validation]]", "[[Boundary Conditions and Rigid Body Modes]]", "[[FE Element Quality Checks]]", "[[Natural Frequencies and Mode Shapes]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# FE Model Verification Checks

## Definition

> [!note] Definition
> Standard numerical tests of an FE model's **mathematical soundness**, run before trusting its results:
> - **free–free modal**;
> - **unit enforced displacement**;
> - **unit gravity**;
> - **thermal equilibrium**.
>
> They are backed by accuracy checks: units, mass, reactions, coincident nodes, free edges, normals.

## Explanation

| Check | Pass | Catches |
|---|---|---|
| Free–free modal (no constraints) | exactly 6 modes ≈ 0 Hz, then flexible modes | disconnected parts (e.g. an engine giving 12 rigid modes), illegal grounding (< 6) |
| Unit enforced displacement (1 unit per translation, 1 rad per rotation) | rigid-body motion; zero element and grid-point forces | incorrect single-point or multi-point constraints |
| Unit gravity (1 g in X, Y, Z) | smooth deflection; reactions = weight | loosely connected nodes (weak springs, MPCs, BCs) |
| Thermal (uniform ΔT, unconstrained) | free expansion, zero stress | spurious constraints, material mismatches |
| Mass and reactions | mass = hand estimate; $\sum$ reactions = applied loads | unit errors, lost or misdirected loads |

**Accuracy checklist**:
- dimensions and units;
- element types and properties;
- mesh quality;
- material data and orientation;
- free edges and faces;
- coincident nodes and elements;
- local coordinate systems;
- shell normals;
- beam orientation and offsets.

## Examples

- Free–free wing: modes 1–6 at 0, 0, $3.5\times10^{-4}$, $4.6\times10^{-4}$, $7.4\times10^{-4}$ and $8.9\times10^{-4}$ Hz. That is six rigid-body modes, so the model is properly connected.

## Related

- Parent lectures: [[SESA2029 B10 - FE Verification, Validation and Model Updating]]
- Related concepts: [[Verification and Validation]] · [[Boundary Conditions and Rigid Body Modes]] · [[FE Element Quality Checks]] · [[Natural Frequencies and Mode Shapes]]
- APDL scripts: [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt

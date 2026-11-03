---
title: "Biot-Savart Law and Helmholtz Theorems"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["Biot-Savart", "Helmholtz vortex theorems", "horseshoe vortex"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Downwash and Induced Drag]]", "[[Kelvin's Circulation Theorem]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt (2025-26 transcripts)"]
---

# Biot-Savart Law and Helmholtz Theorems

The Biot–Savart law gives the velocity a vortex filament of strength $\Gamma$ induces at a point,

$$
d\mathbf V = \frac{\Gamma}{4\pi}\frac{d\mathbf l\times\mathbf r}{|\mathbf r|^3},
$$

and Helmholtz's theorems say how vortex filaments can exist in inviscid flow: a filament has the same strength all along its length, and it can't end in the fluid, so it must close on itself, extend to infinity or end on a boundary.

For a semi-infinite straight filament, at perpendicular distance $h$ from its end, the law gives $V = \Gamma/(4\pi h)$, half the $\Gamma/(2\pi h)$ of an infinite filament. This is the result finite-wing theory uses.

Helmholtz's second theorem is why a wing must have trailing vortices. The bound vortex on the wing can't just stop at the tips, so it turns downstream as two trailing vortices, forming a horseshoe vortex that closes far downstream through the starting vortex. A single horseshoe gives infinite downwash at the tips, so Prandtl's lifting line uses a continuous sheet instead: wherever the spanwise circulation changes, vorticity $-(d\Gamma/dy)\,dy$ is shed into the wake. Applying Biot–Savart to that sheet gives the downwash at the wing,

$$
w(y_0) = -\frac{1}{4\pi}\int_{-b/2}^{b/2}\frac{d\Gamma/dy}{y_0-y}\,dy ,
$$

which [[SESA2022 Exam 2018-19 Solutions]] Q3(i) evaluates for the elliptic distribution.

## Related

- Full derivation and worked examples: [[SESA2022 T5 - Finite Wing Theory#1. Definitions and vortex theorems (6 Nov lecture)|T5 §1]]
- [[Downwash and Induced Drag]] · [[Kelvin's Circulation Theorem]] · [[Elliptic Lift Distribution]]

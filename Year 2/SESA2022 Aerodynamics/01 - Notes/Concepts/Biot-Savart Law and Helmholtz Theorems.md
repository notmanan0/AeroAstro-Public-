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
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf"]
---

# Biot-Savart Law and Helmholtz Theorems

## Definition

> [!note] Definition
> **Biot–Savart**: a vortex filament of strength $\Gamma$ induces a velocity
>
> $$d\mathbf V = \frac{\Gamma}{4\pi}\frac{d\mathbf l\times\mathbf r}{|\mathbf r|^3}$$
>
> For a **semi-infinite** straight filament, at perpendicular distance $h$ from its end, $V = \dfrac{\Gamma}{4\pi h}$ (half the $\Gamma/(2\pi h)$ of an infinite filament).

## Explanation
**Helmholtz's vortex theorems** (inviscid flow):
1. The strength of a vortex filament is constant along its length.
2. A vortex filament can't end in the fluid. It must close on itself, extend to infinity, or end on a boundary.

**Consequences for wings**:
- The **bound vortex** on the wing can't just stop at the tips. It turns downstream as two **trailing vortices**, forming the **horseshoe vortex**, and closes far downstream with the starting vortex.
- Where the spanwise circulation changes, vorticity $-\frac{d\Gamma}{dy}dy$ is shed into the wake. **Prandtl's lifting line** uses a continuous sheet of these.
- Applying Biot–Savart to the trailing sheet gives the downwash at the wing:

$$
w(y_0) = -\frac{1}{4\pi}\int_{-b/2}^{b/2}\frac{d\Gamma/dy}{y_0-y}\,dy
$$

- A single horseshoe vortex gives infinite downwash at the tips, which is why a continuous distribution is needed.

## Examples
- Downwash integral for the ELD: [[SESA2022 Exam 2018-19 Solutions]] Q3(i).

## Related
- Parent lectures: [[SESA2022 T5 - Finite Wing Theory]]
- Related concepts: [[Downwash and Induced Drag]], [[Kelvin's Circulation Theorem]], [[Elliptic Lift Distribution]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf`

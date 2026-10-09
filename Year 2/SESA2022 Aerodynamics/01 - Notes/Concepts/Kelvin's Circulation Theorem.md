---
title: "Kelvin's Circulation Theorem"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 4: Thin Aerofoil Theory"
aliases: ["Kelvin's theorem", "starting vortex", "DΓ/Dt = 0"]
tags: [sesa2022, concept, thin-aerofoil-theory]
status: complete
parent_lectures: ["[[SESA2022 T4 - Thin Aerofoil Theory]]"]
related_concepts: ["[[Kutta Condition]]", "[[Biot-Savart Law and Helmholtz Theorems]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf"]
---

# Kelvin's Circulation Theorem

## Definition

> [!note] Definition
> In an inviscid, barotropic flow with conservative body forces, the circulation round a closed **material** curve (one that moves with the fluid) is constant in time:
>
> $$\frac{D\Gamma}{Dt} = 0$$

## Explanation
- **Starting vortex**: before an aerofoil moves, a large curve round it and the surrounding air has $\Gamma = 0$. After start-up, the aerofoil carries bound circulation $\Gamma$. Kelvin says the total must still be zero, so a **starting vortex** of strength $-\Gamma$ must have been shed from the TE and left behind in the wake.
- Every change in lift (a gust, a flap deflection, a pitch change) sheds a corresponding vortex into the wake. This is the basis of **unsteady aerodynamics** (Wagner and Theodorsen functions).
- Irrotational flow stays irrotational. That justifies potential flow outside boundary layers and wakes, which is where vorticity is generated.
- The 3D counterparts are Helmholtz's vortex theorems (see [[Biot-Savart Law and Helmholtz Theorems]]).

## Examples
- A vortex near the ground and a wall, as the starting vortex of a take-off: [[SESA2022 Exam 2020-21 Solutions]] Part C.

## Related
- Parent lectures: [[SESA2022 T4 - Thin Aerofoil Theory]]
- Related concepts: [[Kutta Condition]], [[Biot-Savart Law and Helmholtz Theorems]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 4 Thin airfoil theory_v3.pdf`

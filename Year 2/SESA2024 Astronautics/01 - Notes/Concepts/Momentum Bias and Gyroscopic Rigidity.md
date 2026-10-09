---
title: "Momentum Bias and Gyroscopic Rigidity"
module: "SESA2024 Astronautics"
type: concept
stream: "Spacecraft Subsystems"
aliases: ["momentum bias", "gyroscopic precession", "gyroscopic rigidity", "nutation"]
tags: [sesa2024, concept, attitude-control]
status: complete
parent_lectures: ["[[SESA2024 06 - Attitude Control]]"]
related_concepts: ["[[Spacecraft Stabilisation Types]]", "[[Reaction Wheels and Momentum Dumping]]", "[[Inertia Matrix]]"]
sources: ["02 - Sources/Lectures/Chapter 6/Chapter 6 - Attitude Control - prerecorded material.pdf"]
---

# Momentum Bias and Gyroscopic Rigidity

## Definition

> [!note] Definition
> **Momentum bias** means deliberately storing a large angular momentum $H_0$ along one body axis, by spinning the body or a wheel. A disturbance torque $T$ applied for time $dt$ then only **rotates the direction** of $\mathbf H$ by
> $$d\psi = \frac{T\,dt}{H_0}\qquad\Rightarrow\qquad\dot\psi = \frac{T}{H_0}\ \text{(precession rate)}$$

## Explanation
- $d\mathbf H = \mathbf T\,dt$. When $\mathbf T\perp\mathbf H$, the change is sideways, so $\mathbf H$ **precesses**. The response appears 90° "later" in the direction of rotation.
- Large $H_0$ means a small $d\psi$: the spacecraft is **less sensitive to external disturbance torques** (gyroscopic rigidity). Without bias, the same impulse produces an angular *rate* ($\Delta\omega = T\,dt/I$) that grows without limit.
- Sketch for the exam (2022/23 A2): $\mathbf H_0$ with a small $\mathbf T\,dt$ added. Show a low-, mid- and high-bias triangle, where the angle between $\mathbf H_0$ and $\mathbf H_1$ shrinks as $H_0$ grows.
- **Costs**:
  - one axis must stay invariantly pointing (usually the orbit normal);
  - an oscillatory **nutation** mode appears (the spin axis cones around $\mathbf H$) and must be damped;
  - the torque response differs from an unbiased body;
  - external torquers are still needed, because disturbances build up momentum.
- Momentum bias is used by Type 1–3 stabilisation. Type 4 (3-axis) has **zero bias**.

## Examples
- Hybrid comsats: a 6500 rpm momentum wheel normal to the orbit plane gives the pitch-axis bias.
- Spin during solid-motor burns (the OMOTENASHI retro-motor; the GEO observatory transfer phase at about 60 rpm) keeps the thrust axis stiff and averages out misalignment.

![[ast_momentum_dumping.png|480]]

## Related
- [[Spacecraft Stabilisation Types]] · [[Reaction Wheels and Momentum Dumping]] · [[Inertia Matrix]]

## Sources
- Chapter 6 pre-recorded slides 14–20

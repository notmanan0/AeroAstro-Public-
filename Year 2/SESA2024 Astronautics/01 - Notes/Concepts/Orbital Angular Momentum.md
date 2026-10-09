---
title: "Orbital Angular Momentum"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["moment of momentum", "specific angular momentum", "h = r x V", "rpVp = raVa"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
related_concepts: ["[[Kepler's Laws]]", "[[Vis-Viva Equation]]", "[[Nodal Regression (J2)]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Keplers Laws and the ellipse equation_2025-26_V5.pdf"]
---

# Orbital Angular Momentum

## Definition

> [!note] Definition
>
> $$\mathbf h = \mathbf r\times\mathbf V,\qquad h = r^2\dot\theta = rV\sin\alpha = rV\cos\gamma = \sqrt{\mu a(1-e^2)}$$
>
> This is the moment of momentum per unit mass. It is **conserved** under a central force.

## Explanation
- The transverse equation of motion is $2\dot r\dot\theta+r\ddot\theta = \frac1r\frac{d}{dt}(r^2\dot\theta) = 0$, so $h$ is constant.
- $\mathbf h$ is **normal to the orbit plane**, and the plane is fixed in inertial space.
  - Only a torque, for example from Earth oblateness ($J_2$), can precess it (nodal regression).
- At periapsis and apoapsis $\mathbf r\perp\mathbf V$, so

$$r_pV_p = r_aV_a$$

- **Kepler 2**: the area rate is $\dot A = h/2$.
- Combining with energy conservation gives $\varepsilon = -\mu/2a$.

## Examples
- 200 × 40 000 km orbit: $r_pV_p$ = 6578 × 10.302 = 67 767 km²/s, which equals $r_aV_a$ = 46 378 × 1.461 ✔.
- Workbook Ch5 Q1: prove the invariant plane and $r_pV_p = r_aV_a$.

## Related
- [[Kepler's Laws]] · [[Vis-Viva Equation]] · [[Nodal Regression (J2)]] · [[Momentum Bias and Gyroscopic Rigidity]] (the same vector mechanics applied to the spacecraft body)

## Year 1 foundation
- Angular impulse and momentum for a particle, central forces: [[FEEG1002 D5 - Angular Impulse and Momentum]].

## Sources
- Chapter 5 Lecture 2 (orbital motion)

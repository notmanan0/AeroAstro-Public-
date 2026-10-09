---
title: "Rolling Without Slip"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["no slip condition", "v = omega r", "rolling with slip", "rolling resistance"]
tags: [feeg1002, concept, dynamics, rigid-body, rolling]
status: complete
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Instantaneous Centre of Rotation]]", "[[Coulomb Friction]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: []
---

# Rolling Without Slip

## Definition

> [!note] Definition
> The contact point has the ground's velocity (zero), so
>
> $$s_G = r\theta,\qquad v_G = r\omega,\qquad a_G = r\alpha,\qquad F_f\le\mu_sN\ \text{(static, does no work)}$$
>
> With slip: $a_G\ne r\alpha$ and $F_f = \mu_kN$ opposing the sliding. Kinetic friction does work $-F_k\Delta s_{sl}$.

## Explanation

- **Assume no slip**, solve for the friction needed, then **check** $F_f\le\mu_sN$. If it fails, re-solve with $F_f = \mu_kN$.
- On an incline, rolling needs $\mu_s\ge\tan\theta\,k^2/(k^2 + r^2)$. Hoops need the most friction, spheres the least.
- **Energy**: $KE = \tfrac12mv^2(1 + k^2/r^2)$. The speed after a drop $h$ is $\sqrt{2gh/(1 + k^2/r^2)}$.
- **Rigid wheels** would roll for ever. **Rolling resistance**, from deformation and hysteresis, is modelled as a force equal to a fraction of the weight.
- Contact-point acceleration is $\omega^2r$ towards the centre, even though its velocity is zero.

## Examples

- **Tutorial 8 Q5**: a hoop at 20° needs 0.182 > 0.15, so it slips: $\alpha = 7.37$ rad/s², $t = 1.63$ s for 3 m.

![[d_rolling_race_energy_split.png|760]]

## Related

- Topic notes: [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Instantaneous Centre of Rotation]] · [[Coulomb Friction]] · [[Kinetic Energy of a Rigid Body]]
- Year 2: Landing-gear wheel spin-up and tyre loads · the same friction check governs belt and brake design

## Sources

- Dynamics Lecture 7.2–7.3, 8.3, 9.2

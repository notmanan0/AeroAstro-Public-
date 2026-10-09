---
title: "Kinetic Energy of a Rigid Body"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["rotational kinetic energy", "1/2 I omega^2", "KE = 1/2 m vG^2 + 1/2 IG omega^2"]
tags: [feeg1002, concept, dynamics, rigid-body, energy]
status: complete
parent_lectures: ["[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Instantaneous Centre of Rotation]]", "[[Mass Moment of Inertia and Radius of Gyration]]"]
sources: []
---

# Kinetic Energy of a Rigid Body

## Definition

> [!note] Definition
>
> $$KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2 = \tfrac12I_{IC}\omega^2$$
>
> Translation only: $\tfrac12mv_G^2$. Fixed axis O: $\tfrac12I_O\omega^2$. System: $\sum KE_i$.

## Explanation

- The cross term vanishes only because the reference point is G. Hence the parallel-axis form $\tfrac12(I_G + mr_{G/IC}^2)\omega^2$.
- **Energy alone** gives only the **total** KE. The split between the two terms comes from kinematics (rolling, a fixed axis, the IC) or from kinetics. A spinning bar thrown upwards keeps its $\omega$, because gravity acts through G.
- **Work of a couple**: $U = \int M\,d\theta$.

## Examples

- **Pinned disc** (Lecture 9): $M\theta + FR\theta = \tfrac12I_O\omega^2$ gives 2.73 rev to reach 20 rad/s.
- **Diver** (Tutorial 9 Q4): $mgr_G = \tfrac12I_A\omega^2$ gives 5.16 rad/s and 1.24 rev before entry.

![[d_t9_q4_diver.png|700]]

## Related

- Topic notes: [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Work-Energy Principle]] · [[Instantaneous Centre of Rotation]] · [[Mass Moment of Inertia and Radius of Gyration]]
- Year 2: Rotor, flywheel and reaction-wheel energy, [[Reaction Wheels and Momentum Dumping]] · Rayleigh's energy method for natural frequencies, [[Natural Frequencies and Mode Shapes]]

## Sources

- Dynamics Lecture 9.1

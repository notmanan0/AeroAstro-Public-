---
title: "FEEG1002 D9 - Work and Energy for Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part D: Dynamics"
order: 9
tags: [feeg1002, dynamics, rigid-body, work, energy, rolling]
aliases: ["Dynamics Lecture 9", "Rigid body energy", "Rotational kinetic energy", "Work of a couple"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
next_topics: []
key_concepts: ["[[Kinetic Energy of a Rigid Body]]", "[[Work-Energy Principle]]", "[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]"]
tutorial_sheets: ["[[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# FEEG1002 D9 - Work and Energy for Rigid Bodies

> [!abstract] Summary
> A rigid body stores kinetic energy in translation **and** rotation:
> $$KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2 = \tfrac12I_{IC}\omega^2$$
> The second form uses the instantaneous centre. The work–energy principle carries over unchanged, $KE_1 + V_1 + \sum U_{1-2} = KE_2 + V_2$, with one addition: a **couple** does work $\int M\,d\theta$. Many forces do **no** work:
> - pin reactions;
> - normal forces;
> - static friction under rolling without slip;
> - internal forces of a rigid body.
>
> That makes energy the fastest route whenever a problem links a **speed** to a **position**.

## Key Concepts
- [[Kinetic Energy of a Rigid Body]] · [[Work-Energy Principle]] · [[Conservative Forces and Potential Energy]] · [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]]

---

## 1. Kinetic energy (L9.1)
Summing $\tfrac12v^2\,dm$ with $\mathbf v_i = \mathbf v_G + \boldsymbol\omega\times\mathbf r_{i/G}$ gives $KE = \tfrac12mv_G^2 + \tfrac12I_G\omega^2$. The cross term vanishes because G is the centre of mass.

| Motion | $KE$ |
|---|---|
| Translation | $\tfrac12mv_G^2$ |
| Rotation about a fixed axis O | $\tfrac12mv_G^2 + \tfrac12I_G\omega^2 = \tfrac12I_O\omega^2$ (just $\tfrac12I_G\omega^2$ if O = G) |
| General plane motion | $\tfrac12mv_G^2 + \tfrac12I_G\omega^2 = \tfrac12I_{IC}\omega^2$, since $v_G = \omega r_{G/IC}$ |
| System of bodies | $\sum KE_i$ (energy is a scalar), e.g. crank + connecting rod + piston |

**Rolling bodies**: $KE = \tfrac12mv^2(1 + k^2/r^2)$. Down the same slope, a sphere beats a disc, which beats a hoop, because the hoop puts half its energy into rotation.

![[d_rolling_race_energy_split.png|920]]

## 2. Work (L9.2)
- **Force**: $U = \int\mathbf F\cdot d\mathbf r$, or $F_c\cos\theta\,s$ for a constant force.
- **Couple (moment)**: $U_M = \int_{\theta_1}^{\theta_2}M\,d\theta$, or $M(\theta_2 - \theta_1)$ if $M$ is constant. It is positive when $M$ and the rotation have the same sense.
- **Forces that do no work**:
  - forces at fixed points (pin reactions);
  - forces perpendicular to their displacement (normals, and weight in horizontal-plane motion);
  - **static friction in rolling without slip**, because the contact point is instantaneously at rest;
  - internal forces of a rigid body (equal, opposite and not deforming).
- **Rolling with slip**: kinetic friction **does** work, $U = -F_k\,\Delta s_{sl}$. The slip distance is $\Delta s_{sl} = x_G - R\theta$.
- **Free rolling of rigid bodies** would go on forever. Real wheels stop because of **rolling resistance**, the deformation and hysteresis of the tyre and ground. It is modelled as a force $R_r$ equal to a fraction of the weight (Tutorial 3 Q10 used 2%).
- **Internal forces in machines can do work**: pistons in cylinders, brake pads, crate on truck. For the crate-and-lorry *system*, static friction does zero net work; on the crate alone it does positive work.
- **Potential energy**:
  - $V_g = mgy_G$, measured at the **centre of mass**;
  - $V_e = \tfrac12k(l - l_0)^2$ with the spring length from the geometry, e.g. the cosine rule $l^2 = b^2 + c^2 - 2bc\cos\theta$.

## 3. The principle and conservation (L9.2)
$$
KE_1 + V_{g1} + V_{e1} + \sum U^{nc}_{1-2} = KE_2 + V_{g2} + V_{e2}
$$

- With only conservative forces, $KE + V$ = const.
- **Limitation**: energy gives only the **total** KE. How it splits between translation and rotation needs **kinematics** (a fixed axis, rolling, or the IC) or a **kinetics** check. Example: a spinning bar thrown upwards keeps its $\omega$, because gravity acts through G and $\sum M_G = 0$. So the potential energy exchanges only with the translational KE.

> [!example] Pinned disc (L9 example 1): $m = 30$ kg, $R = 0.2$ m, $M = 5$ N m plus a 10 N cord pull, from rest to $\omega = 20$ rad/s
> - The pin does no work. $U = M\theta + FR\theta$ and $KE_2 = \tfrac12I_O\omega^2$ with $I_O = \tfrac12mR^2 = 0.6$ kg m².
> - $\theta = 120/(5 + 2) = 17.14$ rad = **2.73 revolutions**.

> [!example] Rod in slots pulled by $P = 50$ N (L9 example 2): 10 kg, 0.8 m, from $\theta = 0$ to $45°$
> - IC: $r_{G/IC} = L/2$, so $KE_2 = \tfrac12\left(m\tfrac{L^2}{4} + \tfrac1{12}mL^2\right)\omega_2^2$.
> - $U_P = PL\sin\theta_2$. $V_g$ is measured at G: $mg\tfrac L2$, then $mg\tfrac L2\cos\theta_2$.
> - **Vertical plane: $\omega_2 = 6.11$ rad/s.** Horizontal plane (no gravity): 5.15 rad/s.
>
> ![[d_rod_in_slots_example.png|720]]

> [!example] Conservation of energy (L9 example 3): 10 kg rod, 0.4 m, spring $k = 800$ N/m unstretched at $\theta = 0$, released at 30°
> - At $\theta = 0$, end A is the IC.
> - $-mg\tfrac L2\sin30° + \tfrac12k(L\sin30°)^2 = \tfrac12\left(m\tfrac{L^2}4 + \tfrac1{12}mL^2\right)\omega_2^2$.
> - **$\omega_2 = 4.82$ rad/s** (vertical plane), or 7.75 rad/s in the horizontal plane.

## 4. Where A is not the IC (Tutorial 9)
The spool problems in Tutorial 9 test your understanding of the IC.
- **Q2**: a spool rolls without slip, pulled by a cord from its **core**. The contact point is the IC, so the cord end moves $s(R_e + R_i)/R_e$.
- **Q3**: a cord is wound on the core and fixed to a wall. The cord's tangent point is stationary, so **it** is the IC. The rim contact then **slides**, and kinetic friction does work over the slip distance.

![[d_t9_spools_ic.png|920]]

## Year 2 bridge
- **Energy methods in structures**: the same bookkeeping, *work of the loads = stored energy*, drives [[SESA2028 S7 - Strain Energy and Conservation of Energy]] and [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]. Lagrangian mechanics (later years) builds equations of motion from $KE$ and $V$ alone.
- **Rotating machinery**: $\tfrac12I\omega^2$ is flywheel and rotor energy. Reaction wheels store angular momentum *and* energy ([[Reaction Wheels and Momentum Dumping]]). The power delivered by a couple is $P = M\omega$, the shaft power of [[FEEG1002 A8 - Torsion of Circular Shafts]] and [[SESA2023 Propulsion Hub]].
- **Vibration by energy**: equating maximum PE and maximum KE (Rayleigh's method) gives $\omega_n$ without writing $\sum F = ma$ ([[FEEG1002 D6 - Single Degree of Freedom Vibration]]). The same idea is behind FE modal analysis ([[Natural Frequencies and Mode Shapes]]).

## Links
- Previous: [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · Particle version: [[FEEG1002 D3 - Work, Energy and Power]]
- Worked problems: [[FEEG1002 Dynamics Tutorial 9 - Work and Energy for Rigid Bodies Solutions]]

## Sources
- Dynamics Lecture 9: 9.1 kinetic energy of rigid bodies; 9.2 work of forces and couples, rolling and friction; solved examples 1–3 (pinned disc, rod in slots, spring-loaded rod)

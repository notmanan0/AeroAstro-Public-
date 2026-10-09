---
title: "Work-Energy Principle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["work energy theorem", "conservation of energy", "KE1 + U = KE2", "energy method"]
tags: [feeg1002, concept, dynamics, energy]
status: complete
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Conservative Forces and Potential Energy]]", "[[Kinetic Energy of a Rigid Body]]", "[[Power and Efficiency]]"]
sources: []
---

# Work-Energy Principle

## Definition

> [!note] Definition
> Integrating $\sum F_t = mv\,dv/ds$ along the path gives
>
> $$KE_1 + V_1 + \sum U^{nc}_{1-2} = KE_2 + V_2,\qquad U = \int\mathbf F\cdot d\mathbf r,\quad KE = \tfrac12mv^2\ \big(+\tfrac12I_G\omega^2\big)$$
>
> With only conservative forces, $KE + V$ is constant.

## Explanation

- It is a **scalar** equation. It relates speed to position without time, and needs no accelerations.
- **Forces that do no work**:
  - normal reactions;
  - pin reactions;
  - forces perpendicular to the motion;
  - static friction under rolling without slip;
  - cord tensions inside a system;
  - a pendulum's tension.
- **Couples** do work $\int M\,d\theta$.
- **Limitation**: it gives one unknown. The split between translation and rotation, and any contact forces, still need kinematics or $\sum F = ma$. The loop trap, where $N\ge0$ must be checked, is the classic example.
- Kinetic friction and drag enter as $U^{nc} < 0$. In the lecture model the lost energy becomes heat.

## Examples

- **Loop** (Lecture 3): $v_A = \sqrt{5gR} = 8.58$ m/s. The naive $\sqrt{4gR}$ loses contact at 131.8°.
- **Rod in slots** (Lecture 9): $\omega = 6.11$ rad/s.

![[d_loop_the_loop.png|760]]

## Related

- Topic notes: [[FEEG1002 D3 - Work, Energy and Power]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Conservative Forces and Potential Energy]] · [[Kinetic Energy of a Rigid Body]] · [[Power and Efficiency]]
- Year 2: Strain energy and conservation of energy in structures, [[SESA2028 S7 - Strain Energy and Conservation of Energy]] ([[Strain Energy]]) · [[Principle of Virtual Work]] · orbital energy, [[Vis-Viva Equation]]

## Sources

- Dynamics Lecture 3.2, 9.2

---
title: "Coulomb Friction"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["static friction", "kinetic friction", "dry friction", "mu_s N", "mu_k N", "impending motion"]
tags: [feeg1002, concept, dynamics, friction]
status: complete
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Newton's Laws of Motion]]", "[[Rolling Without Slip]]", "[[Work-Energy Principle]]"]
sources: []
---

# Coulomb Friction

## Definition

> [!note] Definition
> - **No sliding**: $F_s \le \mu_sN$. $F_s$ comes from equilibrium or the equation of motion; $\mu_sN$ is only its **limit** (impending motion).
> - **Sliding**: $F_k = \mu_kN$, opposing the relative sliding velocity, with usually $\mu_k < \mu_s$.

## Explanation

- Friction is independent of contact area and sliding speed. It is a model for dry, unlubricated surfaces; car tyres violate it.
- **Assume, then check**:
  1. Assume no slip and solve for the friction needed.
  2. If $F > \mu_sN$, redo with $F = \mu_kN$ in the direction that opposes sliding.
- Rolling wheels and blocks on accelerating trucks both need this check.
- **Work**:
  - kinetic friction always does **negative** work, $-\mu_kN\times$ sliding distance, and is non-conservative;
  - static friction usually does none (its point does not move), except when it drags a body along, as with the crate on a truck.
- A block on an incline stays at rest if $\tan\theta\le\mu_s$.

## Examples

- **Tutorial 1 Q10**: $F_0 = mg(\sin15° + \mu_s\cos15°) = 316.5$ N for impending motion up the slope.
- **Lawn roller** (Lecture 8): no slip needs 94.3 N but only $\mu_sN = 81.0$ N is available, so it slips.

![[d_coulomb_friction.png|760]]

## Related

- Topic notes: [[FEEG1002 D1 - Linear Motion of Particles]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Newton's Laws of Motion]] · [[Rolling Without Slip]] · [[Work-Energy Principle]]
- Year 2: Friction and wear in [[SESA2028 M3 - Corrosion, Wear and Surface Engineering]] · non-linear (Coulomb) damping vs the viscous model in [[FEEG1002 D6 - Single Degree of Freedom Vibration]]

## Sources

- Dynamics Lecture 1.3, 8.3, 9.2

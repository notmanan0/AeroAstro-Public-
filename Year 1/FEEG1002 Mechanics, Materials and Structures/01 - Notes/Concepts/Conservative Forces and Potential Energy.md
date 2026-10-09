---
title: "Conservative Forces and Potential Energy"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["potential energy", "gravitational potential energy", "elastic potential energy", "mgh", "1/2 k x^2", "-GMm/r"]
tags: [feeg1002, concept, dynamics, energy]
status: complete
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Coulomb Friction]]", "[[Equivalent Spring Stiffness]]"]
sources: []
---

# Conservative Forces and Potential Energy

## Definition

> [!note] Definition
> A force is **conservative** if its work depends only on the end points ($\oint\mathbf F\cdot d\mathbf r = 0$). A potential $V$ then exists with $U_{A-B} = -(V_B - V_A)$:
> - weight: $V_g = mgy$ (measured at the centre of mass);
> - gravitational attraction: $V_g = -Gm_1m_2/r$;
> - spring: $V_e = \tfrac12k\,\Delta l^2$.

## Explanation

- The datum for $V_g$ is arbitrary; only differences matter. $-GMm/r$ is always negative and tends to 0 at infinity.
- $V_e$ is positive for stretch **and** compression. Get $\Delta l$ from the geometry (cosine rule, Pythagoras), not the displacement of a point.
- **Non-conservative forces**: kinetic friction ($-2\mu_kNs$ for a there-and-back trip), drag, and applied forces that always push the motion along.
- Mathematically, $\mathbf F = -\nabla V$ exactly when $\nabla\times\mathbf F = 0$.

## Examples

- **Tutorial 3 Q3**: the springs go from 0.5 m to 0.3 m long ($l_0 = 0.2$ m), releasing $2\times\tfrac12(1500)(0.3^2 - 0.1^2) = 120$ J.

## Related

- Topic notes: [[FEEG1002 D3 - Work, Energy and Power]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Work-Energy Principle]] · [[Coulomb Friction]] · [[Equivalent Spring Stiffness]]
- Year 2: [[Conservative Vector Fields]] and [[MATH2048 VC3 - Line Integrals and Conservative Fields]] · strain energy as the potential of an elastic structure: [[Strain Energy]], [[Principle of Minimum Total Potential Energy]]

## Sources

- Dynamics Lecture 3.1

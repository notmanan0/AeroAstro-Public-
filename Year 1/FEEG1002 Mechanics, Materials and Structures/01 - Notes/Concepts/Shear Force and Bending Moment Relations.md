---
title: "Shear Force and Bending Moment Relations"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["dQ/dx = -w", "dM/dx = Q", "SF and BM relations", "load-shear-moment relations"]
tags: [feeg1002, concept, statics, beams, sfd, bmd]
status: complete
parent_lectures: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]", "[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Engineer's Bending Theory]]", "[[Macaulay's Method]]"]
sources: []
---

# Shear Force and Bending Moment Relations

## Definition

> [!note] Definition
> For a beam with downward distributed load $w(x)$, shear force $Q$ (positive downwards on the left part's cut face) and bending moment $M$ (sagging positive):
>
> $$\frac{dQ}{dx} = -w(x),\qquad \frac{dM}{dx} = Q,\qquad M(x_2) - M(x_1) = \int_{x_1}^{x_2}Q\,dx$$

## Explanation

- Both relations come from equilibrium of an element $dx$, dropping the $(dx)^2$ term.
- **Reading the diagrams**:
  - point force: jump in $Q$;
  - couple: jump in $M$;
  - no load: constant $Q$, linear $M$;
  - UDL: linear $Q$, parabolic $M$;
  - $Q = 0$: extremum of $M$;
  - free, pinned or roller end: $M = 0$.
- **Beware**: $dM/dx = 0$ finds a local extremum; the largest $|M|$ may be at a support, a load point or a jump.
- The chain continues to deflection: $EI\,d^2v/dx^2 = -M$. So $w\to Q\to M\to$ slope $\to v$ is four integrations, each fixed by a boundary condition.

## Examples

![[s1_standard_beam_cases.png|860]]

- Linearly varying load: $M_{max} = W_BL^2/(9\sqrt3)$ at $x = L/\sqrt3$.
- Tutorial 3 Q3, with $w = \tfrac83x - \tfrac49x^2$: $M_{max} = 15$ kN m at midspan.

## Related

- Topic notes: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Engineer's Bending Theory]] · [[Macaulay's Method]]
- Year 2: Same chain written with $V$ in [[SESA2028 S2 - Beam Deflection and Bending Design]] · $Q(x)$ drives [[Shear Flow]] · $M(x)$ drives the unit-load integrals of [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- Statics 1 Lectures 5b–c, 6b–c

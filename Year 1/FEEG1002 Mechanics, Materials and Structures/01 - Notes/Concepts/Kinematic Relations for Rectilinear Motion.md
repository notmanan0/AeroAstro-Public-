---
title: "Kinematic Relations for Rectilinear Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["a = v dv/ds", "SUVAT", "constant acceleration equations", "rectilinear kinematics"]
tags: [feeg1002, concept, dynamics, kinematics]
status: complete
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
related_concepts: ["[[Newton's Laws of Motion]]", "[[Normal and Tangential Coordinates]]", "[[Work-Energy Principle]]"]
sources: []
---

# Kinematic Relations for Rectilinear Motion

## Definition

> [!note] Definition
> For motion along a straight line with position $s(t)$:
>
> $$v = \frac{ds}{dt},\qquad a = \frac{dv}{dt} = \frac{d^2s}{dt^2},\qquad a = v\frac{dv}{ds}$$
>
> For **constant** acceleration only: $v = v_0 + at$, $s = s_0 + v_0t + \tfrac12at^2$ and $v^2 = v_0^2 + 2a(s - s_0)$.

## Explanation

- **Choose the integral to match the data**:
  - $a(t)$: $\int dv = \int a\,dt$;
  - $a(s)$ (springs, buoyancy, gravity with altitude): $\int v\,dv = \int a\,ds$;
  - $a(v)$ (drag): $dt = dv/a(v)$ or $ds = v\,dv/a(v)$.
- $a = v\,dv/ds$ comes from the chain rule. Integrated over position, it *is* the work–energy principle ([[Work-Energy Principle]]).
- A maximum speed occurs where $a = 0$, **not** where a force first appears: the bungee cord in Tutorial 1 Q5.
- Check the end points of an interval as well as the stationary points.
- The rotational analogue uses $s\to\theta$, $v\to\omega$, $a\to\alpha$ ([[FEEG1002 D7 - Kinematics of Rigid Bodies]]).

## Examples

- **Tutorial 1 Q1**: $s = 4t + 1.6t^2 - 0.08t^3$ gives $v_{max} = 14.7$ m/s at $t = 6.67$ s.
- **Tutorial 1 Q7**, brake phase: $a = -0.003v^2$ gives $s = \ln(4)/0.003 = 462$ m.

![[d_t1_q1_boat_kinematics.png|560]]

## Related

- Topic notes: [[FEEG1002 D1 - Linear Motion of Particles]]
- Concepts: [[Newton's Laws of Motion]] · [[Normal and Tangential Coordinates]] · [[Work-Energy Principle]]
- Year 2: Separable and linear ODEs in [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] · state-space form $\dot{\mathbf x} = \mathbf A\mathbf x$ in [[State-Space Representation]]

## Sources

- Dynamics Lecture 1.1

---
title: "Coefficient of Restitution"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["restitution", "elastic impact", "plastic impact", "e", "central impact", "oblique impact"]
tags: [feeg1002, concept, dynamics, momentum, impact]
status: complete
parent_lectures: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]"]
related_concepts: ["[[Principle of Linear Impulse and Momentum]]", "[[Work-Energy Principle]]"]
sources: []
---

# Coefficient of Restitution

## Definition

> [!note] Definition
>
> $$e = \frac{v_{B2} - v_{A2}}{v_{A1} - v_{B1}} = \frac{\text{relative speed of separation}}{\text{relative speed of approach}}$$
>
> taken along the **line of impact**. $e = 1$ is elastic (KE conserved); $e = 0$ is plastic (the bodies stick).

## Explanation

- **Central impact**: two unknowns, two equations (momentum and $e$):

$$v_{A2} = \frac{m_A - em_B}{m_A + m_B}v_{A1} + \frac{m_B(1+e)}{m_A + m_B}v_{B1},\qquad v_{B2} = \frac{m_A(1+e)}{m_A + m_B}v_{A1} + \frac{m_B - em_A}{m_A + m_B}v_{B1}$$

- For equal masses and $e = 1$ the velocities **swap** (Newton's cradle).
- The KE lost is a fraction $1 - e^2$ of the KE of the relative motion.
- **Oblique impact of smooth bodies**:
  - use $e$ and total momentum along the line of impact;
  - each body keeps its own momentum along the plane of contact.
- $e$ comes from experiment and depends on speed, size and material.

## Examples

- **Galilean cannon**: $h_4 = [e(e + 2)]^2h_0$, so $9h_0$ at $e = 1$. The lecture slide's $6.25h_0$ for $e = 0.5$ is an algebra slip; the correct value is $1.56h_0$.

![[d_restitution_sweep.png|760]]

## Related

- Topic notes: [[FEEG1002 D4 - Linear Impulse and Momentum]]
- Concepts: [[Principle of Linear Impulse and Momentum]] · [[Work-Energy Principle]]
- Year 2: Energy absorption in impact and crashworthiness, and dynamic toughness in [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]

## Sources

- Dynamics Lecture 4.2–4.3

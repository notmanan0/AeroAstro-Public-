---
title: "Relative Velocity Equation for Rigid Bodies"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["v_B = v_A + omega x r_B/A", "relative motion analysis", "relative acceleration"]
tags: [feeg1002, concept, dynamics, rigid-body, kinematics]
status: complete
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]"]
related_concepts: ["[[Instantaneous Centre of Rotation]]", "[[Rolling Without Slip]]", "[[Normal and Tangential Coordinates]]"]
sources: []
---

# Relative Velocity Equation for Rigid Bodies

## Definition

> [!note] Definition
> For two points on one rigid body:
>
> $$\mathbf v_B = \mathbf v_A + \boldsymbol\omega\times\mathbf r_{B/A},\qquad \mathbf a_B = \mathbf a_A + \boldsymbol\alpha\times\mathbf r_{B/A} - \omega^2\mathbf r_{B/A}$$
>
> Relative to A, B moves on a circle, so $v_{B/A} = \omega r_{B/A}$, perpendicular to $\mathbf r_{B/A}$.

## Explanation

- Choose A and B where the **directions** of motion are known: pins, sliders, rolling centres.
- In 2D the vector equation gives two scalar equations, so it solves two unknowns (e.g. $v_B$ and $\omega$).
- In 2D, $\boldsymbol\omega\times\mathbf r = \omega(-r_y, r_x)$. Draw the vector triangle as a check.
- The acceleration form has tangential ($\alpha r$) and normal ($\omega^2r$, towards A) relative parts, the rigid-body version of $n$–$t$ components.

## Examples

- **Sliding rod** (Lecture 7): $v_A = 3$ m/s gives $\omega = 4$ rad/s and $v_B = 5.2$ m/s.
- **Crank–slider** (Tutorial 7 Q5): $\omega_{CB} = \mp39.3$ rad/s at the dead centres and 0 at 90°.

![[d_t7_q5_crank_slider.png|620]]

## Related

- Topic notes: [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Instantaneous Centre of Rotation]] · [[Rolling Without Slip]] · [[Normal and Tangential Coordinates]]
- Year 2: Transport theorem $\dot{\mathbf v}_I = \dot{\mathbf v}_B + \boldsymbol\omega\times\mathbf v$ in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · [[Euler Angles and Rotation Matrices]]

## Sources

- Dynamics Lecture 7.3–7.4

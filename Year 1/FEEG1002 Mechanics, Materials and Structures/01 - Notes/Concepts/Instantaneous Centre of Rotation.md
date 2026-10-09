---
title: "Instantaneous Centre of Rotation"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["IC", "instantaneous centre of zero velocity", "ICR"]
tags: [feeg1002, concept, dynamics, rigid-body, kinematics]
status: complete
parent_lectures: ["[[FEEG1002 D7 - Kinematics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Relative Velocity Equation for Rigid Bodies]]", "[[Rolling Without Slip]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: []
---

# Instantaneous Centre of Rotation

## Definition

> [!note] Definition
> The point of the body (or its extension) with **zero velocity** at the instant considered. The body momentarily rotates about it:
> $$\mathbf v_P = \boldsymbol\omega\times\mathbf r_{P/IC},\qquad v_P = \omega r_{P/IC},\qquad KE = \tfrac12I_{IC}\omega^2$$

## Explanation

- **Finding it**: draw perpendiculars to two non-parallel velocity directions; they meet at the IC.
- If the velocities are parallel and equal, the IC is at infinity: the body **translates** instantaneously, $\omega = 0$ (the crank–slider at 90°).
- **Rolling without slip**: the contact point is the IC.
- A **fixed, inextensible cord** makes its tangent point the IC. The rim contact then slides (Tutorial 9 Q3).
- It is a **velocity-only** tool. The IC itself accelerates, so do not use it for accelerations.

## Examples

- **Sliding rod** (Lecture 7): $r_{A/IC} = 0.75$ m and $r_{B/IC} = 1.30$ m.
- **Rod in slots** (Lecture 9): $r_{G/IC} = L/2$ gives the KE in one line.

![[d_sliding_rod_ic.png|560]]

## Related

- Topic notes: [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Relative Velocity Equation for Rigid Bodies]] · [[Rolling Without Slip]] · [[Kinetic Energy of a Rigid Body]]
- Year 2: Rigid-body motion and zero-strain-energy modes, [[Boundary Conditions and Rigid Body Modes]]

## Sources

- Dynamics Lecture 7.3, 9.1

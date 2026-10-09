---
title: "Mass Moment of Inertia and Radius of Gyration"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["mass moment of inertia", "MMI", "radius of gyration", "I = mk^2", "rotational inertia"]
tags: [feeg1002, concept, dynamics, rigid-body, inertia]
status: complete
parent_lectures: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Parallel Axis Theorem]]", "[[Planar Rigid-Body Equations of Motion]]", "[[Kinetic Energy of a Rigid Body]]"]
sources: []
---

# Mass Moment of Inertia and Radius of Gyration

## Definition

> [!note] Definition
>
> $$I_O = \int r_O^2\,dm\ \ [\text{kg m}^2],\qquad I_O = I_G + md^2,\qquad I = mk^2$$
>
> Standard values about G: rod $\tfrac1{12}mL^2$ ($\tfrac13mL^2$ about an end), disc/cylinder $\tfrac12mr^2$, hoop $mr^2$, sphere $\tfrac25mr^2$, plate $\tfrac1{12}m(a^2 + b^2)$.

## Explanation

- $I$ resists angular acceleration, as $m$ resists linear acceleration ($\sum M = I\alpha$ vs $\sum F = ma$).
- $I_G$ is the **smallest** over all parallel axes.
- **Composite bodies**:
  1. locate G;
  2. find each part's $I_{Gi}$;
  3. shift each to G with $m_id_i^2$;
  4. add.
- The radius of gyration $k$ is where all the mass could sit for the same $I$. It measures how spread out the mass is (disc $r/\sqrt2$, hoop $r$).
- Do not confuse it with the **area** moment $\int r^2\,dA$ (m⁴) of bending and torsion. The maths is identical, but the units and meaning differ.
- In 3D, $I$ becomes the inertia tensor ([[Inertia Matrix]]).

## Examples

- **Tutorial 8 Q1**: bar plus disc gives $l_G = 0.743$ m and $I_G = 1.55$ kg m².
- **Tutorial 8 Q3**: a point mass at $2l/3$ leaves $l_G/k_A^2$ unchanged (centre of percussion).

![[d_mass_moment_of_inertia.png|760]]

## Related

- Topic notes: [[FEEG1002 D8 - Kinetics of Rigid Bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies]]
- Concepts: [[Parallel Axis Theorem]] · [[Planar Rigid-Body Equations of Motion]] · [[Kinetic Energy of a Rigid Body]]
- Year 2: [[Inertia Matrix]] and principal axes in [[SESA2024 06 - Attitude Control]] · the $I_{yy}$ pitch inertia in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] · the area analogue in [[Parallel Axis Theorem]] and [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]

## Sources

- Dynamics Lecture 8.1

---
title: "Conservative Forces and Potential Energy"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["potential energy", "gravitational potential energy", "elastic potential energy", "mgh", "1/2 k x^2", "-GMm/r", "conservative force", "non-conservative force", "mechanical potential energy"]
tags: [feeg1002, concept, dynamics, energy]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Work-Energy Principle]]", "[[Coulomb Friction]]", "[[Equivalent Spring Stiffness]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 03 - Work, Energy and Power.pdf", "02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# Conservative Forces and Potential Energy

A force is conservative if the work it does between two points does not depend on the path taken, so that it does no work round any closed path; its work can then be written as minus the change of a function of position, the potential energy $V$.

$$
\oint\mathbf F\cdot d\mathbf r=0,\qquad \int_A^B\mathbf F\cdot d\mathbf r=-(V_B-V_A)
$$

The minus sign means that when a conservative force does positive work its potential energy falls. The work of the weight, with $y$ up, is $-mg(y_2-y_1)$, which depends only on the change of height; the work of a spring is $-(\tfrac12ks_2^2-\tfrac12ks_1^2)$, which depends only on the end extensions. Reading off the potentials gives the three potentials of mechanics:

$$
V_g=mgy,\qquad V_g=-G\frac{m_1m_2}{r},\qquad V_e=\tfrac12k\,\Delta l^2,\ \ \Delta l=l-l_0
$$

The datum for $mgy$ is arbitrary because only differences enter; for a rigid body $y$ is the height of the centre of mass. The gravitational form, needed when the change in distance is comparable with the Earth's radius, is always negative and tends to zero as $r\to\infty$. The elastic energy is positive for stretching and compression alike, and $\Delta l$ is measured from the unstretched length, found from the geometry (often with the cosine rule), not from the starting length.

Kinetic friction, drag and propulsive forces are **non-conservative**. A block slid from A to B and back costs $-2\mu_kNs$ of friction work, while the weight does $-mgs$ then $+mgs$, a total of zero: friction can only take energy away. These forces stay in $\sum U_{1-2}$ in the work-energy principle, while weight and springs move to the potential-energy side. The usual mistake is to count the weight twice, as work and as $V_g$; each force appears once.

## Related

- [[FEEG1002 D3 - Work, Energy and Power#2. Conservative forces and potential energy|D3 §2]] · [[FEEG1002 D3 - Work, Energy and Power#Work of friction|work of friction]] · [[FEEG1002 D3 - Work, Energy and Power#With potential energy|work-energy with potentials]] · [[FEEG1002 D3 - Work, Energy and Power#Collar on a rough vertical shaft|collar on a shaft]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#3. Potential energy and the work-energy principle|rigid bodies in D9]] · [[FEEG1002 D5 - Angular Impulse and Momentum#Satellite in an elliptical orbit|orbit example]]
- [[Work-Energy Principle]] · [[Coulomb Friction]] · [[Equivalent Spring Stiffness]]
- Year 2: path independence as a property of the field, [[Conservative Vector Fields]] in [[MATH2048 VC3 - Line Integrals and Conservative Fields]] · strain energy as the potential of an elastic structure, [[Strain Energy]] and [[Principle of Minimum Total Potential Energy]] · orbital energy, [[Vis-Viva Equation]]

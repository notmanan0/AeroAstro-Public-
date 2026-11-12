---
title: "Work-Energy Principle"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["work energy theorem", "conservation of energy", "KE1 + U = KE2", "energy method", "conservation of mechanical energy", "work of a force"]
tags: [feeg1002, concept, dynamics, energy]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D3 - Work, Energy and Power]]", "[[FEEG1002 D9 - Work and Energy for Rigid Bodies]]"]
related_concepts: ["[[Conservative Forces and Potential Energy]]", "[[Kinetic Energy of a Rigid Body]]", "[[Power and Efficiency]]", "[[Coulomb Friction]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 03 - Work, Energy and Power.pdf", "02 - Sources/Dynamics/Lectures/Lecture 09 - Work and Energy for Rigid Bodies.pdf"]
---

# Work-Energy Principle

The work-energy principle states that the work done by all the forces on a particle between two states equals the change in its kinetic energy $\tfrac12mv^2$; with the work of weight and springs written as potential energy, it becomes the energy equation used in problems.

$$
KE_1+\sum U_{1-2}=KE_2,\qquad KE_1+V_{g1}+V_{e1}+\sum U_{1-2}=KE_2+V_{g2}+V_{e2}
$$

A force does work $U_{1-2}=\int\mathbf F\cdot d\mathbf r=\int F_t\,ds$, so only the component along the path counts and normal forces do none. Resolving Newton's law along the tangent, $\sum F_t=mv\,dv/ds$, separating and integrating from state 1 to state 2 gives the first form. In the second, $\sum U_{1-2}$ holds only the non-conservative forces (friction, drag, applied forces and couples), and if it is zero, $KE+V$ is conserved.

It is a scalar equation linking forces, speeds and positions without time, so it gives one unknown and is the wrong tool for a time or an acceleration. Forces that do no work drop out: normal and pin reactions, a pendulum's tension, the friction on a wheel rolling without slip, and internal forces between points that do not move apart. For a rigid body the kinetic energy includes $\tfrac12I_G\omega^2$ and a couple does $\int M\,d\theta$; the rod sliding in two slots pulled by 50 N reaches 6.11 rad/s at 45° in a vertical plane.

The energy equation often needs a second law alongside it. A particle entering a frictionless loop of radius 1.5 m must keep $N\ge0$ at the top, which needs $v_B=\sqrt{gR}$, and energy then gives the entry speed $v_A=\sqrt{5gR}=8.58$ m/s. Taking $v_B=0$ instead gives $\sqrt{4gR}=7.67$ m/s, and a particle at that speed leaves the track 48.2° from the top. Similarly a block entering a rough incline at 6 m/s slides 5.76 m on a 10° slope, while at 30° the formula returns a negative distance because friction cannot hold the block at all.

Kinetic friction does $-\mu_kNs$, and the particle model counts that as the heat produced. The commonest error is counting the weight twice, once as work and once as $V_g$.

![[d_loop_the_loop.png|760]]

## Related

- [[FEEG1002 D3 - Work, Energy and Power#1. Work of a force|work of a force]] · [[FEEG1002 D3 - Work, Energy and Power#3. The work-energy principle|D3 §3]] · [[FEEG1002 D3 - Work, Energy and Power#With potential energy|with potential energy]] · [[FEEG1002 D3 - Work, Energy and Power#Conservation of energy|conservation of energy]] · [[FEEG1002 D3 - Work, Energy and Power#Friction and heat|friction and heat]] · [[FEEG1002 D3 - Work, Energy and Power#Systems of particles|systems of particles]] · [[FEEG1002 D3 - Work, Energy and Power#Block sliding down a rough incline|rough incline]] · [[FEEG1002 D3 - Work, Energy and Power#Minimum speed for a loop|loop]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Forces that do no work|forces that do no work]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#3. Potential energy and the work-energy principle|rigid bodies]] · [[FEEG1002 D9 - Work and Energy for Rigid Bodies#Rod sliding in two slots|rod in two slots]]
- [[Conservative Forces and Potential Energy]] · [[Kinetic Energy of a Rigid Body]] · [[Power and Efficiency]] · [[Coulomb Friction]]
- Year 2: energy methods for structures, [[Strain Energy]] in [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · [[Principle of Virtual Work]] · orbital energy, [[Vis-Viva Equation]]

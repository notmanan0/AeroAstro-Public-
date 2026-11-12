---
title: "Principle of Linear Impulse and Momentum"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["impulse", "linear momentum", "conservation of linear momentum", "impulse-momentum", "impulse-momentum theorem", "average force", "impulsive force"]
tags: [feeg1002, concept, dynamics, momentum]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D4 - Linear Impulse and Momentum]]", "[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
related_concepts: ["[[Coefficient of Restitution]]", "[[Principle of Angular Impulse and Momentum]]", "[[Newton's Laws of Motion]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 04 - Linear Impulse and Momentum.pdf"]
---

# Principle of Linear Impulse and Momentum

The principle of linear impulse and momentum states that the impulse of the forces on a particle over an interval equals the change in its linear momentum $m\mathbf v$; it is Newton's second law integrated over time.

$$
m\mathbf v_1+\sum\int_{t_1}^{t_2}\mathbf F\,dt=m\mathbf v_2
$$

For constant mass, $\sum\mathbf F=m\,d\mathbf v/dt$ separates into $\sum\mathbf F\,dt=m\,d\mathbf v$ and integrates directly. Momentum and impulse are both vectors in N s (kg m/s), so the principle is written per component and links force, time and velocity without position. The impulse is the area under the force-time curve. The **average force** is the constant force giving the same area over the same time, and a pulse always peaks above it: the tennis ball hit by a contact force peaking at 160 N receives 0.64 N s in 5 ms, leaves upwards at 4.67 m/s, and feels an average of 128 N.

During an impact lasting milliseconds, finite steady forces such as the weight contribute almost nothing and are neglected as **non-impulsive**, while the contact force is large enough to give a finite impulse. Over a longer event every force counts; a rocket accelerating for 6 s must include the impulse of its weight.

For a system of particles the internal forces cancel in pairs, leaving $m(\mathbf v_G)_1+\sum\int\mathbf F_{ext}\,dt=m(\mathbf v_G)_2$. If the external impulses sum to zero, as in a collision or explosion between free bodies, the total momentum is conserved, and this can hold along one axis but not another. Momentum alone cannot give both velocities after a collision, which is why the [[Coefficient of Restitution]] is needed.

A body bouncing off rigid ground does not conserve its momentum, because the ground applies an external impulse. In the crash test, the 1500 kg car arriving at 3 m/s and rebounding at 1 m/s has a velocity change of 4 m/s, not 2, so the 0.4 s contact needs an average force of 15.0 kN. The maximum force cannot be found without the force history. A sudden impulse $J$ on a mass at rest is equivalent to an initial velocity $J/m$, which is how an impact starts a free vibration.

![[d_impulse_force_time.png|760]]

## Related

- [[FEEG1002 D4 - Linear Impulse and Momentum#1. Principle of linear impulse and momentum|D4 §1]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Impulse and average force|average force]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Impulsive and non-impulsive forces|impulsive forces]] · [[FEEG1002 D4 - Linear Impulse and Momentum#2. Conservation of linear momentum|conservation]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Tennis ball bouncing off the ground|tennis ball]] · [[FEEG1002 D4 - Linear Impulse and Momentum#Crash test|crash test]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#4. Impulse and momentum for rigid bodies|rigid bodies]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Response to initial conditions|impulse as initial velocity]]
- [[Coefficient of Restitution]] · [[Principle of Angular Impulse and Momentum]] · [[Newton's Laws of Motion]]
- Later: variable-mass momentum in the [[Tsiolkovsky Rocket Equation]] · control-volume momentum, [[SESA1016 T12 - Conservation of Momentum]] and [[Momentum Flux]]

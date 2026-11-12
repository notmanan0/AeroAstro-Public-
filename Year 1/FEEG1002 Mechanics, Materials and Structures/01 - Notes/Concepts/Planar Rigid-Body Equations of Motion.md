---
title: "Planar Rigid-Body Equations of Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["sum M_G = I_G alpha", "rigid body kinetics", "sum M_O = I_O alpha", "kinetic diagram rigid body", "kinetic moments", "Euler's equations in the plane"]
tags: [feeg1002, concept, dynamics, rigid-body, kinetics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D8 - Kinetics of Rigid Bodies]]"]
related_concepts: ["[[Mass Moment of Inertia and Radius of Gyration]]", "[[Newton's Laws of Motion]]", "[[Rolling Without Slip]]", "[[Principle of Angular Impulse and Momentum]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 08 - Kinetics of Rigid Bodies.pdf"]
---

# Planar Rigid-Body Equations of Motion

A rigid body in plane motion obeys two force equations for its centre of mass and one moment equation, which about G involves only the moment of inertia and about any other point P also includes the moment of $m\mathbf a_G$.

$$
\sum F_x=m(a_G)_x,\qquad \sum F_y=m(a_G)_y,\qquad \sum M_G=I_G\alpha
$$

$$
\sum M_P=\bar{\mathbf r}\times m\mathbf a_G+I_G\alpha
$$

The force equations treat the body as a particle at G, since the internal forces cancel in pairs. The moment equation comes from summing the moments of $dm\,\mathbf a$ for every element, with $\mathbf a_i=\mathbf a_G+\boldsymbol\alpha\times\boldsymbol\rho_i-\omega^2\boldsymbol\rho_i$; every term containing $\int\boldsymbol\rho\,dm$ vanishes about the centre of mass, leaving the right-hand side above, the **kinetic moments**. Moments are therefore taken of everything on the kinetic diagram: $m(a_G)_x$ and $m(a_G)_y$ drawn at G and the couple $I_G\alpha$. Moments about a point where unknown forces act remove those forces.

Three cases follow. In translation $\alpha=0$, so $\sum M_G=0$, but only about G; about another point the moment of $m\mathbf a_G$ must be kept. A translating body must also be checked for tipping by confirming that every normal reaction is positive: the 200 kg handcart pushed at 60° has $N_A=765$ N and $N_B=1240$ N, so it does not tip. In rotation about a fixed axis O, $(a_G)_t=r_G\alpha$ and $(a_G)_n=r_G\omega^2$, and moments about O give

$$
\sum M_O=(I_G+mr_G^2)\alpha=I_O\alpha
$$

with the pin reactions eliminated. The 15 kg rod pinned 0.3 m from one end and released from rest has $\alpha=16.35$ rad/s² and a tangential pin reaction of 110.4 N; the normal reaction is zero because $\omega=0$ at release. For a rolling wheel, the three equations have four unknowns, and the fourth relation is either $a_G=r\alpha$ (no slip, then check $F\le\mu_sN$) or $F=\mu_kN$ (slip).

The usual errors are taking $\sum M=0$ about a point other than G for a translating body, and writing $F=\mu_sN$ for a wheel assumed not to slip.

![[d_pinned_rod_released.png|620]]

## Related

- [[FEEG1002 D8 - Kinetics of Rigid Bodies#3. Planar equations of motion|D8 §3]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#General plane motion|derivation]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Translation|translation]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rotation about a fixed axis|fixed axis]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rolling with and without slip|rolling]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Handcart that must not tip|handcart]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Rod released from rest about a pivot|released rod]] · [[FEEG1002 D8 - Kinetics of Rigid Bodies#Driven wheel from the mock exam|driven wheel]]
- [[Mass Moment of Inertia and Radius of Gyration]] · [[Parallel Axis Theorem]] · [[Newton's Laws of Motion]] · [[Rolling Without Slip]] · [[Principle of Angular Impulse and Momentum]]
- Year 2: three-dimensional rigid-body dynamics of aircraft in [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] and of spacecraft in [[SESA2024 06 - Attitude Control]]

---
title: "Kinematic Relations for Rectilinear Motion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["a = v dv/ds", "SUVAT", "constant acceleration equations", "rectilinear kinematics", "equations of uniformly accelerated motion", "separation of variables in kinematics"]
tags: [feeg1002, concept, dynamics, kinematics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
related_concepts: ["[[Newton's Laws of Motion]]", "[[Projectile Motion]]", "[[Normal and Tangential Coordinates]]", "[[Work-Energy Principle]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 01 - Linear Motion.pdf"]
---

# Kinematic Relations for Rectilinear Motion

For a particle on a straight line with position $s(t)$, the velocity is $v=ds/dt$, the acceleration is $a=dv/dt$, and by the chain rule $a=v\,dv/ds$; integrated in the form that matches what $a$ depends on, these turn an equation of motion into speed, position and time.

$$
v=\frac{ds}{dt},\qquad a=\frac{dv}{dt}=\frac{d^2s}{dt^2},\qquad a=v\frac{dv}{ds}
$$

The third relation follows from $a=\frac{dv}{ds}\frac{ds}{dt}$ with $ds/dt=v$, and is the one to use whenever the force depends on position. The sign of $a$ says which way the velocity is changing, not whether the particle is speeding up: with $v<0$, a negative $a$ means a rising speed.

Newton's second law usually supplies $a$, and the integral is chosen by what it depends on, separating the variables each time. If $a=a(t)$, integrate $dv=a\,dt$. If $a=a(s)$, as for springs, partial buoyancy and gravity varying with altitude, integrate $v\,dv=a\,ds$. If $a=a(v)$, as for drag, use $ds=v\,dv/a(v)$ for position or $dt=dv/a(v)$ for time. A ship driven by $F$ against linear drag $bv$ reaches $v=\frac Fb(1-e^{-bt/m})$; a body falling against quadratic drag approaches $v_t=\sqrt{mg/C}$ as $v=v_t\tanh(gt/v_t)$; a particle launched upwards with gravity falling off as $1/r^2$ escapes if $v_0\ge\sqrt{2g_0R_e}=11.2$ km/s.

Only when $a=a_c$ is constant do the integrals collapse to the **SUVAT equations**:

$$
v=v_0+a_ct,\qquad s=s_0+v_0t+\tfrac12a_ct^2,\qquad v^2=v_0^2+2a_c(s-s_0)
$$

These hold for free fall without drag, sliding with kinetic friction and a constant applied force. With a spring, drag, partial buoyancy or varying gravity they give wrong numbers, so the first question in any problem is whether $a$ is constant. The same relations apply to rotation with $s\to\theta$, $v\to\omega$, $a\to\alpha$, and $a_t\,ds=v\,dv$ along a curved path is the step from which the work-energy principle is derived.

## Related

- [[FEEG1002 D1 - Linear Motion of Particles#1. Position, velocity and acceleration|D1 §1]] · [[FEEG1002 D1 - Linear Motion of Particles#2. Choosing the integral|choosing the integral]] · [[FEEG1002 D1 - Linear Motion of Particles#3. Constant acceleration|constant acceleration]] · [[FEEG1002 D1 - Linear Motion of Particles#Drag and terminal velocity|terminal velocity]] · [[FEEG1002 D1 - Linear Motion of Particles#Escape velocity|escape velocity]] · [[FEEG1002 D1 - Linear Motion of Particles#Ship and marble with linear drag|linear drag]] · [[FEEG1002 D2 - Curvilinear Motion#Circular paths|angular analogues]] · [[FEEG1002 D3 - Work, Energy and Power#3. The work-energy principle|work-energy derivation]]
- [[Newton's Laws of Motion]] · [[Projectile Motion]] · [[Normal and Tangential Coordinates]] · [[Work-Energy Principle]]
- Year 2: first- and second-order ODEs in [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]

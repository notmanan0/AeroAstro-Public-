---
title: "Differentiation of Vectors"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Vector functions", "Velocity and acceleration vectors", "Polar unit vectors"]
tags: [math1054, concept, vector-calculus]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector Algebra and Components]]", "[[Normal and Tangential Coordinates]]", "[[Projectile Motion]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.5", "MATH1054 Module Booklet, Module 15"]
---

# Differentiation of Vectors

The derivative of a vector function $\mathbf r(t)=(x(t),y(t),z(t))$ is $\dot{\mathbf r}=\lim_{\Delta t\to0}[\mathbf r(t+\Delta t)-\mathbf r(t)]/\Delta t=(\dot x,\dot y,\dot z)$, found component by component because $\mathbf i$, $\mathbf j$ and $\mathbf k$ are fixed; for a position vector, $\dot{\mathbf r}$ is the velocity and $\ddot{\mathbf r}$ the acceleration. Integration is also component-wise, with a constant vector of integration.

The usual product rules carry over, and each is proved by applying the scalar rule to the components. For the dot product, $\frac{\mathrm d}{\mathrm dt}(u_1v_1+u_2v_2+u_3v_3)$ splits into $\sum\dot u_iv_i+\sum u_i\dot v_i$, so

$$
\frac{\mathrm d}{\mathrm dt}(\mathbf u\cdot\mathbf v)=\dot{\mathbf u}\cdot\mathbf v+\mathbf u\cdot\dot{\mathbf v},\qquad\frac{\mathrm d}{\mathrm dt}(\mathbf u\times\mathbf v)=\dot{\mathbf u}\times\mathbf v+\mathbf u\times\dot{\mathbf v},
$$

and the cross-product rule follows the same way from the component $u_2v_3-u_3v_2$, with the factors kept in their original order. Two results follow at once. If $|\mathbf a|$ is constant, differentiating $\mathbf a\cdot\mathbf a=$ constant gives $2\mathbf a\cdot\dot{\mathbf a}=0$, so $\mathbf a\perp\dot{\mathbf a}$: on a circle about O the velocity is tangent, and at constant speed the acceleration is perpendicular to the velocity. And differentiating $|\mathbf r|^2=\mathbf r\cdot\mathbf r$ gives $\mathrm d|\mathbf r|/\mathrm dt=\hat{\mathbf r}\cdot\dot{\mathbf r}$, only the radial part of the velocity, so the speed $|\dot{\mathbf r}|$ is in general not $\mathrm d|\mathbf r|/\mathrm dt$.

In polar coordinates the unit vectors $\hat{\mathbf r}=(\cos\theta,\sin\theta)$ and $\hat{\boldsymbol\theta}=(-\sin\theta,\cos\theta)$ turn with the particle, with $\mathrm d\hat{\mathbf r}/\mathrm dt=\dot\theta\,\hat{\boldsymbol\theta}$ and $\mathrm d\hat{\boldsymbol\theta}/\mathrm dt=-\dot\theta\,\hat{\mathbf r}$. Differentiating $\mathbf r=r\hat{\mathbf r}$ twice with the product rule gives

$$
\dot{\mathbf r}=\dot r\,\hat{\mathbf r}+r\dot\theta\,\hat{\boldsymbol\theta},\qquad\ddot{\mathbf r}=(\ddot r-r\dot\theta^2)\,\hat{\mathbf r}+(2\dot r\dot\theta+r\ddot\theta)\,\hat{\boldsymbol\theta},
$$

with the centripetal term $-r\dot\theta^2$ and the Coriolis term $2\dot r\dot\theta$.

For example, the helix $\mathbf r=(\cos t,\sin t,t)$ has $\dot{\mathbf r}=(-\sin t,\cos t,1)$ and $\ddot{\mathbf r}=(-\cos t,-\sin t,0)$, so $\dot{\mathbf r}\cdot\ddot{\mathbf r}=0$, as it must be because the speed $\sqrt2$ is constant (Specimen Test 15 Q5). Going the other way, $\ddot{\mathbf r}=(\cos t,\sin t,0)$ with $\dot{\mathbf r}(0)=(0,-1,1)$ and $\mathbf r(0)=(-1,0,0)$ integrates to $\dot{\mathbf r}=(\sin t,-\cos t,1)$ and the helix $\mathbf r=(-\cos t,-\sin t,t)$ (Booklet Exercise A). A projectile with $\ddot{\mathbf r}=-g\mathbf k$, $\mathbf r(0)=\mathbf 0$ and $\dot{\mathbf r}(0)=(u,0,v)$ follows $\mathbf r=\mathbf Vt-\tfrac12gt^2\mathbf k$, the parabola $z=\frac vu\,x-\frac{g}{2u^2}\,x^2$ (James Example 9.21).

The common traps are reversing the order in the cross-product rule, which changes the sign of a term, and forgetting that a constant of integration is a vector, which loses two of its three components when it is fitted to initial data.

## Related

- Topics: [[MATH1054 M15 - Vectors II]] (derivations and all work-scheme examples) · [[FEEG1002 D2 - Curvilinear Motion]] · [[FEEG1002 D5 - Angular Impulse and Momentum]] · [[SESA2024 02 - Kepler's Laws and the Orbit Equation]]
- Concepts: [[Vector Algebra and Components]] · [[Product, Quotient and Chain Rules]] · [[Normal and Tangential Coordinates]] · [[Projectile Motion]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §9.5.1 and Exercises 32–35; MATH1054 Module Booklet, Module 15 work scheme, items 3–4 and Exercise A

---
title: "Exact Differential Equations"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Exact equation", "Exactness test"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Partial Derivatives]]", "[[Integrating Factor Method]]", "[[Conservative Vector Fields]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.7", "MATH1054 Module Booklet, Module 12"]
---

# Exact Differential Equations

A first-order equation $p(t,x)\,\dot x+q(t,x)=0$ is exact when there is a function $h(t,x)$ with $\partial h/\partial x=p$ and $\partial h/\partial t=q$. Its solutions are then the curves $h(t,x)=C$.

The reason is the chain rule for $h\big(t,x(t)\big)$: $\dfrac{\mathrm dh}{\mathrm dt}=\dfrac{\partial h}{\partial x}\dot x+\dfrac{\partial h}{\partial t}=p\,\dot x+q$, so the equation says $\mathrm dh/\mathrm dt=0$. Whether $h$ exists can be tested without finding it. If it does, differentiating $h_x=p$ with respect to $t$ and $h_t=q$ with respect to $x$ gives two mixed second derivatives of $h$, which are equal for any $h$ with continuous second derivatives, so

$$
\frac{\partial p}{\partial t}=\frac{\partial q}{\partial x}.
$$

If the test fails, the equation is not exact. If it holds, $h$ is built by integrating $p$ with respect to $x$, holding $t$ fixed and adding an unknown function $C_1(t)$ in place of a constant, then differentiating with respect to $t$ and matching to $q$. The equation for $C_1'(t)$ contains no $x$ precisely because the test holds: $\partial_x\big(q-\partial_t\!\int p\,\mathrm dx\big)=q_x-p_t=0$.

For example, $(\ln\sin t-3x^2)\,\dot x+x\cot t+4t=0$ (Example 10.16) has $p_t=\cot t=q_x$. Integrating $p$ gives $h=x\ln\sin t-x^3+C_1(t)$; then $h_t=x\cot t+C_1'(t)$ must equal $x\cot t+4t$, so $C_1=2t^2$ and

$$
x\ln\sin t-x^3+2t^2=C ,
$$

a cubic in $x$ normally left implicit. With $x(\tfrac12\pi)=3$, $C=0-27+2(\tfrac12\pi)^2=\tfrac12\pi^2-27\approx-22.065$. Other cases: $\cos t\,\dot x-x\sin t+1=0$ with $x(0)=2$ gives $x\cos t+t=2$, so $x=\dfrac{2-t}{\cos t}$ (Exercise 24(d)); $\sqrt t\,\dot x-xt=0$ is not exact, since $p_t=1/(2\sqrt t)$ while $q_x=-t$ (Exercise 25(b)). Multiplying that last equation by $1/(x\sqrt t)$ makes it exact, and a multiplier of this kind is an integrating factor; the [[Integrating Factor Method]] is the systematic version for linear equations.

Two traps recur. The "constant" from integrating with respect to $x$ is a function of $t$, and writing it as a plain number loses the $t$-only terms of $h$, such as the $2t^2$ above. When both conditions are integrated separately and compared, a term that appears in both is counted once. The construction is the same as finding the potential of a conservative vector field ([[Conservative Vector Fields]]), and the solution curves are the contours of $h$.

## Related

- Topics: [[MATH1054 M12 - Differential Equations II]] (derivation of the test, Examples 10.15–10.16, Exercises 23(e), 24(d), 25(b), Specimen Test 12 Q4) · [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- Concepts: [[Partial Derivatives]] · [[Integrating Factor Method]] · [[Conservative Vector Fields]] · [[Homogeneous First-Order ODEs]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.5.7; MATH1054 Module Booklet, Module 12

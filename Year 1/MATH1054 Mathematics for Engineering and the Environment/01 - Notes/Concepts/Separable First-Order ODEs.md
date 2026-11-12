---
title: "Separable First-Order ODEs"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Separation of variables (ODE)", "Separable equation", "Variables separable"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M06 - Differential Equations I]]"]
related_concepts: ["[[Homogeneous First-Order ODEs]]", "[[Integrating Factor Method]]", "[[Classification of Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.1", "MATH1054 Module Booklet, Module 6"]
---

# Separable First-Order ODEs

A first-order ODE is separable if its right-hand side factorises as $\dot x=f(t)g(x)$, so that the dependent variable can be moved to one side and the independent variable to the other; wherever $g(x)\neq0$ it is then solved by

$$
\int\frac{\mathrm dx}{g(x)}=\int f(t)\,\mathrm dt+C .
$$

The rule is the chain rule run backwards. Let $G$ be an antiderivative of $1/g$, so $G'(x)=1/g(x)$. Along a solution,

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}G\big(x(t)\big)&=\frac1{g(x)}\frac{\mathrm dx}{\mathrm dt}\\
&=f(t),
\end{aligned}
$$

so integrating in $t$ gives $G(x)=\int f(t)\,\mathrm dt+C$, which is the rule above. One constant is enough, because constants on both sides would merge. The method is: separate, integrate with one constant, apply the initial condition, then solve for $x$ where possible, choosing any $\pm$ sign from the initial data and stating where the solution is valid.

For example, $\dot x=4xt$ (Example 10.13) gives $\int\mathrm dx/x=\int4t\,\mathrm dt$, so $\ln|x|=2t^2+c$ and $x=Ae^{2t^2}$ with $A=\pm e^c$. With a condition, $t^2\dot x=1/x$ and $x(4)=9$ (Exercise 12(b)) give $\tfrac12x^2=-1/t+C$; at $t=4$, $\tfrac{81}2=-\tfrac14+C$, so $C=\tfrac{163}4$ and $x=\sqrt{\tfrac{163}2-\tfrac2t}$, the positive root because $x(4)>0$. Likewise $\dot x=(t+1)/(x+1)$ with $x(0)=1$ (Specimen Test 6, Q3) gives $(x+1)^2=(t+1)^2+3$ and $x=\sqrt{t^2+2t+4}-1$, valid for all $t$.

The main trap is the division by $g(x)$. Every root of $g$ gives a constant solution that the separated integral cannot see, so it has to be checked separately: for $\dot x=4xt$ the lost solution $x\equiv0$ is recovered by allowing $A=0$, but for $\sqrt t\,\dot x=\sqrt x$ (Exercise 13(a)) the solution $x\equiv0$ is not in the family $x=(\sqrt t+c)^2$ for any $c$, and that family itself only solves the equation where $\sqrt t+c\geq0$.

Two more behaviours come from nonlinearity. If $f(t)g(x)$ is singular at the initial point the solution need not be unique: $\dot x=(t^2+1)/(x+2)$ with $x(0)=-2$ (Exercise 14(a)) has the two solutions $x=-2\pm\sqrt{\tfrac23t^3+2t}$. And a solution can blow up in finite time: $\dot x=e^{x+t}$ with $x(0)=a$ (Exercise 14(d)) gives $x=-\ln(1+e^{-a}-e^t)$, which tends to infinity as $t\to\ln(1+e^{-a})$, at $t=\ln2\approx0.693$ for $a=0$.

Separation of variables for ODEs is a different technique from [[Separation of Variables]] for PDEs, where a product solution $X(x)T(t)$ splits one PDE into two ODEs.

## Related

- Topics: [[MATH1054 M06 - Differential Equations I]] · [[MATH1054 M12 - Differential Equations II]]
- Concepts: [[Classification of Differential Equations]] · [[Homogeneous First-Order ODEs]] (reduced to separable form by $x=vt$) · [[Integrating Factor Method]] · [[Separation of Variables]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.5.1 and §10.5.3; MATH1054 Module Booklet, Module 6 (work scheme item 13, Specimen Test 6 Q3)

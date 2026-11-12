---
title: "Linear Differential Operators and Superposition"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Linear operator", "Superposition principle", "CF + PI", "Complementary function", "Particular integral"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M13 - Differential Equations III]]"]
related_concepts: ["[[Auxiliary Equation]]", "[[Method of Undetermined Coefficients]]", "[[Classification of Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.8", "MATH1054 Module Booklet, Module 13"]
---

# Linear Differential Operators and Superposition

A linear differential operator $\mathrm L=a_n(t)\mathrm D^n+\dots+a_1(t)\mathrm D+a_0(t)$, with $\mathrm D=\mathrm d/\mathrm dt$, satisfies $\mathrm L[ax_1+bx_2]=a\mathrm L[x_1]+b\mathrm L[x_2]$ for all functions $x_1,x_2$ and constants $a,b$. Superposition is the consequence: solutions of $\mathrm L[x]=0$ can be added and scaled, and every solution of $\mathrm L[x]=f$ is the complementary function plus one particular integral.

The linearity comes from differentiation itself. The sum and constant-multiple rules give $\mathrm D[ax_1+bx_2]=a\mathrm D x_1+b\mathrm D x_2$; repeating this gives the same for $\mathrm D^k$; and multiplying each $\mathrm D^k$ term by a coefficient $a_k(t)$ and summing keeps the property:

$$
\begin{aligned}
\mathrm L[ax_1+bx_2]&=\sum_k a_k(t)\,\mathrm D^k[ax_1+bx_2]\\
&=a\sum_k a_k(t)\mathrm D^kx_1+b\sum_k a_k(t)\mathrm D^kx_2\\
&=a\mathrm L[x_1]+b\mathrm L[x_2].
\end{aligned}
$$

The coefficients may vary with $t$, as in $\mathrm L=\mathrm D^2+4t\mathrm D-\sin t$ (James Example 10.27), but must not depend on $x$. An operator such as $\phi[f]=f^2$ is not linear, since $\phi[2f]=4f^2\neq2\phi[f]$.

Three results follow, each in one line from the definition. If $\mathrm L[x_1]=\mathrm L[x_2]=0$ then $\mathrm L[ax_1+bx_2]=0$, so with $n$ linearly independent solutions of an $n$th-order equation the **complementary function** (CF) is $x_c=A_1x_1+\dots+A_nx_n$. If $x_p$ is any one solution of $\mathrm L[x]=f$, the **particular integral** (PI), then $\mathrm L[x_c+x_p]=0+f=f$, and conversely any solution $x$ has $\mathrm L[x-x_p]=f-f=0$, so $x-x_p$ is part of the CF; hence the general solution is exactly $x=x_c+x_p$. Finally, if $\mathrm L[x_1]=f_1$ and $\mathrm L[x_2]=f_2$ then $\mathrm L[x_1+x_2]=f_1+f_2$, so a forcing made of several terms can be solved term by term and the particular integrals added.

For example, $\ddot x+5\dot x-9x=e^{-2t}+2-t$ (James Example 10.43) splits into two problems. With $P(m)=m^2+5m-9$, the exponential piece gives $x_1=e^{-2t}/P(-2)=-\tfrac1{15}e^{-2t}$, because $P(-2)=4-10-9=-15$. The linear piece takes $x_2=at+b$, so $5a-9(at+b)=2-t$, giving $a=\tfrac19$ and $b=-\tfrac{13}{81}$. Adding them and the CF from $m=\tfrac12(-5\pm\sqrt{61})\approx1.405,\,-6.405$:

$$
x=Ae^{1.405t}+Be^{-6.405t}-\tfrac1{15}e^{-2t}+\tfrac19t-\tfrac{13}{81}.
$$

Substituting back confirms $\mathrm L[x]=e^{-2t}+2-t$ for every $A$ and $B$.

The common trap is to stretch superposition beyond what linearity gives. Adding two solutions of the forced equation $\mathrm L[x]=f$ does not give another solution: $\mathrm L[x_1+x_2]=2f$. Only CF terms may be added freely to a solution of the forced problem, which is also why initial or boundary conditions must be applied to the full $x_c+x_p$ and never to $x_c$ alone. Nor does superposition hold for a nonlinear equation: $x=1/t$ solves $\dot x+x^2=0$, but $x=2/t$ gives $\dot x+x^2=-2/t^2+4/t^2=2/t^2\neq0$.

## Related

- Topics: [[MATH1054 M13 - Differential Equations III]] (derivations, constant-coefficient methods, damped oscillators); [[MATH1054 M06 - Differential Equations I]]; [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]; [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- Concepts: [[Auxiliary Equation]] · [[Method of Undetermined Coefficients]] · [[Classification of Differential Equations]] · [[Resonance]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.8 and §10.9.3 (Examples 10.27, 10.43); MATH1054 Module Booklet, Module 13

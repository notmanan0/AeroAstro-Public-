---
title: "Integrating Factor Method"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Integrating factor", "First-order linear ODE"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Exact Differential Equations]]", "[[Separable First-Order ODEs]]", "[[RC and RL Transients]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.9", "MATH1054 Module Booklet, Module 12"]
---

# Integrating Factor Method

The integrating factor method solves the first-order linear equation $\dot x+p(t)\,x=r(t)$ by multiplying it by $g(t)=e^{\int p\,\mathrm dt}$, which turns the left-hand side into the single derivative $\frac{\mathrm d}{\mathrm dt}(gx)$.

The factor comes from the product rule. Multiplying by any $g(t)$ gives $g\dot x+gpx$ on the left, while $\frac{\mathrm d}{\mathrm dt}(gx)=g\dot x+\dot gx$. The two agree when $\dot g=gp$, a separable equation with solution $\ln g=\int p\,\mathrm dt$. The same condition is what makes $g\dot x+g(px-r)=0$ an [[Exact Differential Equations|exact equation]], since the exactness test reads $\partial g/\partial t=\partial(gpx-gr)/\partial x=gp$. With this $g$,

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(gx)&=g\,r\\
gx&=\int g\,r\,\mathrm dt+C\\
x&=\frac1g\left[\int g\,r\,\mathrm dt+C\right].
\end{aligned}
$$

No constant is needed in $\int p\,\mathrm dt$, because it would multiply both sides by the same number, and for $t>0$ the logarithms simplify through $e^{a\ln t}=t^a$. The solution splits into $C/g$, which solves the unforced equation $\dot x+px=0$ and is the transient, plus $\frac1g\int gr\,\mathrm dt$, one particular solution. That is the complementary function plus particular integral structure used for second-order equations in [[MATH1054 M13 - Differential Equations III]].

For $\dot x+tx=t$ (Example 10.17), $g=e^{t^2/2}$, so $\big(xe^{t^2/2}\big)'=te^{t^2/2}$, which integrates to $xe^{t^2/2}=e^{t^2/2}+C$ and

$$
x=1+Ce^{-t^2/2}.
$$

Substituting back, $\dot x+tx=-Cte^{-t^2/2}+t+Cte^{-t^2/2}=t$, and every solution tends to the equilibrium $x=1$. Other results: $\dot x-\frac xt=t^2-3$ with $x(1)=-1$ has $g=1/t$ and gives $x=\tfrac12t^3-3t\ln t-\tfrac32t$ (Exercise 32(c)); $\dot x+\frac{2x}t=\cos t$ has $g=t^2$ and, after integrating $t^2\cos t$ by parts twice, gives $x=\sin t+\dfrac{2\cos t}t-\dfrac{2\sin t}{t^2}+\dfrac C{t^2}$ (Exercise 33(c)).

The method solves every first-order linear equation for which the integrals can be done, including an RC circuit charging, $RC\,\dot v+v=V_0$, which gives $v=V_0\big(1-e^{-t/RC}\big)$ from $v(0)=0$, and the other first-order lags of engineering. The trap is skipping the standard form: the coefficient of $\dot x$ must be 1 before $p$ is read off, so $t\dot x+2x=t\cos t$ is first divided by $t$ to give $p=2/t$, $g=t^2$ and right-hand side $\cos t$.

## Related

- Topics: [[MATH1054 M12 - Differential Equations II]] (derivation, Examples 10.17–10.18, Exercises 31(c), 32(c), 33(c), Specimen Test 12 Q2, applications) · [[MATH1054 M13 - Differential Equations III]]
- Concepts: [[Exact Differential Equations]] · [[Separable First-Order ODEs]] · [[Linear Differential Operators and Superposition]] · [[RC and RL Transients]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.5.9; MATH1054 Module Booklet, Module 12

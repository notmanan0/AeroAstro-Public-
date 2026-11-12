---
title: "Homogeneous First-Order ODEs"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 3: Differential Equations"
aliases: ["Homogeneous-type equation", "x = vt substitution", "Equations of the form dx/dt = f(x/t)"]
tags: [math1054, concept, odes]
status: complete
parent_lectures: ["[[MATH1054 M12 - Differential Equations II]]"]
related_concepts: ["[[Separable First-Order ODEs]]", "[[Exact Differential Equations]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §10.5.5", "MATH1054 Module Booklet, Module 12"]
---

# Homogeneous First-Order ODEs

A first-order equation of the form $\dot x=f(x/t)$, whose right-hand side depends on $x$ and $t$ only through their ratio. The substitution $x=ty$ (often written $x=vt$) turns it into a separable equation for $y(t)$.

The right-hand side $F(t,x)$ has this form when scaling both variables leaves it unchanged, $F(\lambda t,\lambda x)=F(t,x)$; choosing $\lambda=1/t$ then gives $F(t,x)=F(1,x/t)$. For a ratio of polynomials that means every term in the numerator and denominator has the same total degree in $x$ and $t$. The name is overloaded: a homogeneous *linear* equation is one with no forcing term, which is a different idea, so the course calls these "equations of the form $\mathrm dx/\mathrm dt=f(x/t)$".

The substitution works because of the product rule. With $x=ty$,

$$
\dot x=t\dot y+y ,
$$

so $\dot x=f(y)$ becomes

$$
\begin{aligned}
t\dot y+y&=f(y)\\
t\dot y&=f(y)-y\\
\int\frac{\mathrm dy}{f(y)-y}&=\ln t+C\qquad(t>0),
\end{aligned}
$$

after which $y$ is replaced by $x/t$. Along each ray $x=y_0t$ the slope of the direction field is the constant $f(y_0)$, which is why only the ratio $x/t$ matters.

For example, $t^2\dot x=x^2+xt$ divides to $\dot x=(x/t)^2+x/t$, so $f(y)=y^2+y$ and $t\dot y=y^2$. Then $-1/y=\ln t+C$, and with $A=-C$,

$$
x=\frac{t}{A-\ln t}
$$

(Example 10.14 and Specimen Test 12 Q3). Substituting back, $\dot x=(A-\ln t+1)/(A-\ln t)^2$, and both sides equal $t^2(A-\ln t+1)/(A-\ln t)^2$. Likewise $t\dot x=x+t\tan(x/t)$ gives $t\dot y=\tan y$, so $\sin y=At$ and $x=t\sin^{-1}(At)$ (Exercise 20(d)).

The trap is the division by $f(y)-y$. Every root $y_0$ of $f(y_0)=y_0$ gives a straight-line solution $x=y_0t$ that the general formula can miss; in Example 10.14, $f(y)-y=y^2$ vanishes at $y=0$, and $x=0$ is a solution not of the form $t/(A-\ln t)$. In initial-value problems such as Exercise 21(b), a square root appears at the end and the sign is fixed by the initial condition.

## Related

- Topics: [[MATH1054 M12 - Differential Equations II]] (derivation, Example 10.14 and Exercises 18(b), 20(d), 21(b)) · [[MATH1054 M06 - Differential Equations I]]
- Concepts: [[Separable First-Order ODEs]] · [[Exact Differential Equations]] · [[Integrating Factor Method]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §10.5.5; MATH1054 Module Booklet, Module 12

---
title: "Derivative from First Principles"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["First principles", "Definition of the derivative", "Difference quotient"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Product, Quotient and Chain Rules]]", "[[Partial Derivatives]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.2", "MATH1054 Module Booklet, Module 3"]
---

# Derivative from First Principles

The derivative of $f$ at $x$ is the limit of the difference quotient, $f'(x)=\dfrac{\mathrm df}{\mathrm dx}=\displaystyle\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$. Working from first principles means finding a derivative directly from this limit rather than from the rules.

The quotient is the slope of the chord joining $\big(x,f(x)\big)$ and $\big(x+\Delta x,f(x+\Delta x)\big)$. As $\Delta x\to0$ the chord turns into the tangent, so $f'(x)$ is the slope of the tangent, and for a function of time it is the instantaneous rate of change: velocity $\dot s$ and acceleration $\ddot s$. The limit must be the same from both sides. For $|x|$ at $0$ the quotient is $+1$ for $\Delta x>0$ and $-1$ for $\Delta x<0$, so $|x|$ has no derivative there even though it is continuous.

The method has four moves: expand $f(x+\Delta x)$, subtract $f(x)$ so that every term without a $\Delta x$ cancels, divide by $\Delta x$, and let $\Delta x\to0$. For $f(x)=25x-5x^2$ (James Example 8.2):

$$
\begin{aligned}
f(x+\Delta x)-f(x)&=25\,\Delta x-5\big[(x+\Delta x)^2-x^2\big]\\
&=25\,\Delta x-10x\,\Delta x-5(\Delta x)^2,\\
\frac{f(x+\Delta x)-f(x)}{\Delta x}&=25-10x-5\Delta x,\\
f'(x)&=25-10x .
\end{aligned}
$$

At $x=1$ the chord slope is $15-5\Delta x$: $5$, $10$ and $12.5$ for $\Delta x=2,\ 1,\ 0.5$, tending to $f'(1)=15$. The tangent at $(1,20)$ is $y-20=15(x-1)$, that is $y=15x+5$. The normal has the negative reciprocal slope $-\tfrac1{15}$, because perpendicular directions $(1,m_1)$ and $(1,m_2)$ satisfy $1+m_1m_2=0$, which gives $x+15y=301$. The same method gives $2x$ for $x^2$ and for $x^2-2$, $4x$ for $2x^2$, and $-1/x^2$ for $1/x$, where the two fractions are put over the common denominator $x(x+\Delta x)$ before dividing.

Each standard derivative ($x^n$, $\sin x$, $e^x$) and each rule (sum, product, quotient, chain) is proved this way once, and afterwards the results are used directly. The common trap is setting $\Delta x=0$ before dividing through, which turns the quotient into $0/0$. The factor $\Delta x$ in the numerator has to cancel first; after that, a $\Delta x$ left elsewhere, as in $\dfrac{-1}{x(x+\Delta x)}$, can safely go to zero.

## Related

- Topics: [[MATH1054 M03 - Differentiation I]] (Section 1)
- Concepts: [[Product, Quotient and Chain Rules]] · [[Partial Derivatives]] (the same limit with the other variables held constant)
- Later: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]] (the quotient with a finite step as a numerical derivative)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.2; MATH1054 Module Booklet, Module 3

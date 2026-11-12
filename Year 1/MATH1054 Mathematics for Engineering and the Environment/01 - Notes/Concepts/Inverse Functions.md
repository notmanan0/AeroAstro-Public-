---
title: "Inverse Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["f^{-1}", "Inverse function", "One-to-one"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]"]
related_concepts: ["[[Inverse Trigonometric Functions]]", "[[Hyperbolic Functions]]", "[[Even, Odd and Periodic Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.2.3", "MATH1054 Module Booklet, Module 7"]
---

# Inverse Functions

The inverse $f^{-1}$ of a function $f$ reverses it: $y=f^{-1}(x)$ exactly when $x=f(y)$. It exists only if $f$ is **one-to-one** (each output comes from a single input), and then the domain of $f^{-1}$ is the range of $f$ and its range is the domain of $f$.

A function is one-to-one when every horizontal line meets its graph at most once; a strictly increasing or strictly decreasing function always is. To find the inverse, write $y=f(x)$, solve for $x$ in terms of $y$, then swap the letters. Because swapping $x$ and $y$ sends $(a,b)$ to $(b,a)$, the graph of $f^{-1}$ is the reflection of the graph of $f$ in the line $y=x$, and vertical and horizontal asymptotes swap.

A function that fails the test can be made invertible by restricting its domain. $x^2$ on $x\geq0$ has inverse $\sqrt x$; $x^2+1$ on $x\geq0$ has inverse $\sqrt{x-1}$ on $x\geq1$ (Exercise 10(c)); $\sin x$ on $[-\frac\pi2,\frac\pi2]$ has inverse $\sin^{-1}x$ ([[Inverse Trigonometric Functions]]); $\cosh x$ on $x\geq0$ has inverse $\cosh^{-1}x$ ([[Hyperbolic Functions]]). The restriction is part of the definition, which is why $\sqrt{x^2}=|x|$ rather than $x$.

The derivative of an inverse follows from differentiating $f\big(f^{-1}(x)\big)=x$ with the chain rule:

$$
\begin{aligned}
f'\big(f^{-1}(x)\big)\,\big(f^{-1}\big)'(x)&=1\\
\big(f^{-1}\big)'(x)&=\frac{1}{f'\big(f^{-1}(x)\big)},
\end{aligned}
$$

or $\frac{\mathrm dy}{\mathrm dx}=1\big/\frac{\mathrm dx}{\mathrm dy}$, wherever $f'\neq0$. For $f(x)=x^3+x$, which has no simple inverse formula, $f(1)=2$ and $f'(1)=4$, so $\big(f^{-1}\big)'(2)=\frac14$; differencing a numerical solution of $z^3+z=2\pm10^{-6}$ gives $0.2500000$.

For example, $y=\frac{x+2}{x+1}$ ($x\neq-1$) rearranges as $x(y-1)=2-y$, so $f^{-1}(x)=\frac{2-x}{x-1}$ with $x\neq1$ (Example 2.7). The excluded value $1$ is the output $f$ never reaches, its horizontal asymptote. Composing back, $f\big(f^{-1}(x)\big)=x$.

![[m1054_inverse_reflections.png|900]]

The common trap is reading the $-1$ as a power. $f^{-1}(x)$ is the inverse function and $[f(x)]^{-1}=1/f(x)$ is the reciprocal, so $\sin^{-1}x$ is not $\operatorname{cosec}x$. A second trap is forgetting that the inverse undoes $f$ only on the restricted domain: $f^{-1}\big(f(x)\big)=x$ can fail outside it.

## Related

- Topics: [[MATH1054 M07 - Functions]] · [[MATH1054 M03 - Differentiation I]]
- Concepts: [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]] · [[Even, Odd and Periodic Functions]] · [[Product, Quotient and Chain Rules]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.2.3; MATH1054 Module Booklet, Module 7

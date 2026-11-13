---
title: "L'Hôpital's Rule"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["L'Hopital's rule", "Indeterminate forms"]
tags: [math1054, concept, limits]
status: complete
parent_lectures: ["[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Taylor and Maclaurin Series]]", "[[Derivative from First Principles]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §9.4", "MATH1054 Module Booklet, Module 20"]
---

# L'Hôpital's Rule

L'Hôpital's rule evaluates a limit of the indeterminate form $\frac00$ (or $\frac\infty\infty$): if $f(x)\to0$ and $g(x)\to0$ as $x\to a$, then $\displaystyle\lim_{x\to a}\frac{f(x)}{g(x)}=\lim_{x\to a}\frac{f'(x)}{g'(x)}$, provided the right-hand limit exists.

The reason is that near $a$ each function is close to its tangent line, $f(x)\approx(x-a)f'(a)$ and $g(x)\approx(x-a)g'(a)$, and the common factor $(x-a)$ cancels. The precise argument uses the Cauchy mean value theorem, which follows from Rolle's theorem applied to $h(t)=f(x)g(t)-g(x)f(t)$ when $f(a)=g(a)=0$: since $h(a)=h(x)=0$, there is a $c$ between $a$ and $x$ with $h'(c)=0$, that is

$$
\frac{f(x)}{g(x)}=\frac{f'(c)}{g'(c)} .
$$

As $x\to a$, $c\to a$ too, so $\frac fg$ has whatever limit $\frac{f'}{g'}$ has. If $\frac{f'}{g'}$ is again $\frac00$ the rule is applied again, which is why it can be repeated.

Repeating it while the form stays indeterminate, then substituting:

$$
\begin{aligned}
\lim_{x\to0}\frac{x\cos x-\sin x}{x^3}&=\lim_{x\to0}\frac{\cos x-x\sin x-\cos x}{3x^2}\\
&=\lim_{x\to0}\frac{-\sin x}{3x}\\
&=\lim_{x\to0}\frac{-\cos x}{3}=-\frac13
\end{aligned}
$$

(Exercise 19(e)). At a point other than zero the same applies: $\sin3\pi=\sin2\pi=0$, so

$$
\lim_{x\to\pi}\frac{\sin3x}{\sin2x}=\lim_{x\to\pi}\frac{3\cos3x}{2\cos2x}=\frac{3(-1)}{2(1)}=-\frac32
$$

(Exercise 19(c)). For $\frac\infty\infty$, $\lim_{x\to\infty}\frac{x}{e^x}=\lim_{x\to\infty}\frac{1}{e^x}=0$ (Booklet Example 2).

Maclaurin series give an independent check. With $\sin x-x=-\frac{x^3}{6}+\frac{x^5}{120}-\cdots$, the quotient $\frac{\sin x-x}{x^3}=-\frac16+\frac{x^2}{120}-\cdots\to-\frac16$, the same as three applications of the rule (James Example 9.14(a)). The definition of the derivative is itself a $\frac00$ limit, $f'(a)=\lim_{x\to a}\frac{f(x)-f(a)}{x-a}$ ([[Derivative from First Principles]]), and L'Hôpital's rule gives $\frac{f'(x)}{1}\to f'(a)$, consistent with it when $f'$ is continuous.

The trap is applying the rule to a form that is no longer indeterminate. In $\lim_{x\to0}\frac{1-\cos x}{x+x^2}$ one application gives $\frac{\sin x}{1+2x}$, which is $\frac01$ at $x=0$, so the limit is 0. Differentiating again would give $\frac{\cos x}{2}\to\frac12$, which is wrong. Check the form before every application, and differentiate numerator and denominator separately; the quotient rule plays no part.

## Related

- Topics: [[MATH1054 M20 - Further Calculus II#11. L'Hôpital's rule|M20 §11]] · [[MATH1054 M20 Solutions - Further Calculus II#Exercise 19: L'Hôpital's rule|Exercise 19 solutions]] · [[MATH1054 M20 Solutions - Further Calculus II#Example 9.14: L'Hôpital's rule|Example 9.14 solution]]
- Concepts: [[Taylor and Maclaurin Series]] · [[Derivative from First Principles]]
- Sources: James, Modern Engineering Mathematics (6th ed.) §9.4.3; MATH1054 Module Booklet, Module 20 (items 17–18, Booklet Example 2, Specimen Test 20 Q6).

---
title: "Integration by Parts"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["By parts", "LIATE"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M04 - Integration I]]"]
related_concepts: ["[[Trigonometric Integrals and Power Reduction]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.4", "MATH1054 Module Booklet, Module 4"]
---

# Integration by Parts

Integration by parts is the product rule for differentiation run backwards, $\int u\frac{\mathrm dv}{\mathrm dx}\,\mathrm dx=uv-\int v\frac{\mathrm du}{\mathrm dx}\,\mathrm dx$. It trades the integral of a product for a different integral, which is simpler if the factors are chosen well.

The formula comes from integrating the product rule $\frac{\mathrm d}{\mathrm dx}(uv)=u'v+uv'$ after moving $u'v$ across:

$$
\begin{aligned}
uv'&=\frac{\mathrm d}{\mathrm dx}(uv)-u'v,\\
\int uv'\,\mathrm dx&=uv-\int u'v\,\mathrm dx .
\end{aligned}
$$

With limits it reads $\int_a^buv'\,\mathrm dx=\big[uv\big]_a^b-\int_a^bu'v\,\mathrm dx$. No constant is needed when $v$ is found from $v'$, because replacing $v$ by $v+k$ adds $ku-\int ku'\,\mathrm dx=0$ to the right-hand side.

The choice of $u$ decides whether the new integral is easier. Take $u$ as the factor that simplifies on differentiation and $v'$ as one that can be integrated; the LIATE order (logarithm, inverse trigonometric, algebraic, trigonometric, exponential) gives the first choice for $u$. A logarithm goes in $u$ because it differentiates to a power, so $\int x^3\ln x\,\mathrm dx=\frac14x^4\ln x-\int\frac14x^3\,\mathrm dx=\frac1{16}x^4(4\ln x-1)+C$ (Exercise 110(c)), and $\int\ln x\,\mathrm dx=x\ln x-x+C$ with $v'=1$. A power $x^n$ against a sine or exponential needs $n$ applications, each lowering the power by one; Exercise 111(a) needs two:

$$
\begin{aligned}
\int_0^{\pi/2}x^2\sin x\,\mathrm dx&=\big[-x^2\cos x\big]_0^{\pi/2}+2\int_0^{\pi/2}x\cos x\,\mathrm dx\\
&=0+2\big[x\sin x+\cos x\big]_0^{\pi/2}\\
&=\pi-2 .
\end{aligned}
$$

For $e^{ax}\sin bx$ or $e^{ax}\cos bx$ neither factor ever simplifies. Two applications, differentiating the trigonometric factor both times, return the original integral $I$ with a new coefficient, and the equation is solved for $I$. Doing this once with general $a$ and $b$ gives

$$
\int e^{ax}\cos bx\,\mathrm dx=\frac{e^{ax}(a\cos bx+b\sin bx)}{a^2+b^2},\qquad\int e^{ax}\sin bx\,\mathrm dx=\frac{e^{ax}(a\sin bx-b\cos bx)}{a^2+b^2},
$$

each plus a constant; the full derivation is in [[MATH1054 M04 - Integration I#The general cyclic formulas|M04 §6]]. With $a=-2$, $b=3$ this gives Exercise 110(d), $\int e^{-2x}\sin3x\,\mathrm dx=-\frac1{13}e^{-2x}(2\sin3x+3\cos3x)+C$; differentiating back returns $e^{-2x}\sin3x$. The same integrals are the real and imaginary parts of $\int e^{(a+jb)x}\,\mathrm dx$ ([[Euler's Formula]]), and they appear in every Fourier coefficient of an exponential.

The common trap is swapping roles on the second pass of the cyclic case. If the trigonometric factor was differentiated the first time and the exponential is differentiated the second time, the second step undoes the first and the calculation ends at $I=I$.

## Related

- Topics: [[MATH1054 M04 - Integration I]] (derivation and all set examples, §6) · [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] (Fourier coefficients by parts)
- Concepts: [[Trigonometric Integrals and Power Reduction]] · [[Integration by Substitution]] · [[Product, Quotient and Chain Rules]] · [[Euler's Formula]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.8.4 (Example 8.51, Exercises 110–111); MATH1054 Module Booklet, Module 4 (work scheme item 8, Exercise B); worked solutions in [[MATH1054 M04 Solutions - Integration I]].

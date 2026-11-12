---
title: "Logarithmic Differentiation"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Log differentiation"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M08 - Differentiation II]]"]
related_concepts: ["[[Implicit and Parametric Differentiation]]", "[[Product, Quotient and Chain Rules]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.3.14", "MATH1054 Module Booklet, Module 8"]
---

# Logarithmic Differentiation

Logarithmic differentiation finds $y'$ by taking the logarithm of both sides of $y=f(x)$, differentiating implicitly and multiplying through by $y$:

$$
\ln y=\ln f(x)\ \Rightarrow\ \frac{y'}{y}=\frac{d}{dx}\ln f(x)\ \Rightarrow\ y'=y\,\frac{d}{dx}\ln f(x).
$$

The middle step is the chain rule on $\ln y$, with $y$ a function of $x$: $\frac{d}{dx}\ln y=\frac1y\frac{dy}{dx}$. It needs $y>0$ for $\ln y$ to exist; if $y$ can be negative, $\ln|y|$ has the same derivative $y'/y$ for $y\neq0$, so the final formula holds wherever $y\neq0$.

The method pays off in two cases. When the variable is in both the base and the exponent, as in $x^x$, $(\sin x)^x$ or $(\ln x)^x$, no single rule applies, but $\ln(u^v)=v\ln u$ turns the power into a product and $\frac{y'}y=v'\ln u+v\frac{u'}u$. A constant base is the simplest instance: $\ln(a^x)=x\ln a$ gives $\frac{d}{dx}a^x=a^x\ln a$. When $y$ is a long product or quotient of powers, $y=\prod u_k^{a_k}$, the log laws turn it into a sum, $\frac{y'}y=\sum a_k\frac{u_k'}{u_k}$, which avoids nested product and quotient rules.

Worked examples:

- $(\sin x)^x$ on $(0,\pi)$: $\ln y=x\ln\sin x$, so $y'=(\sin x)^x(\ln\sin x+x\cot x)$ (Example 8.25).
- $10^x$: $y'=10^x\ln10$ (Exercise 53(a)).
- $(\ln x)^x$ for $x>1$: $y'=(\ln x)^x\big[\ln(\ln x)+\frac1{\ln x}\big]$ (Exercise 58(a)).
- $(1-x^2)^{1/2}(2x^2+3)^{-4/3}$ for $|x|<1$: $\frac{y'}y=-\frac{x}{1-x^2}-\frac{16x}{3(2x^2+3)}=\frac{5x(2x^2-5)}{3(1-x^2)(2x^2+3)}$, so $y'=\dfrac{5x(2x^2-5)}{3(1-x^2)^{1/2}(2x^2+3)^{7/3}}$ (Exercise 58(c)).
- $x^x$: $y'=x^x(\ln x+1)$, zero at $x=1/e$, the minimum of $x^x$ with value $0.6922$.

The usual slip is forgetting the last step, multiplying $y'/y$ by $y$, or treating $x^x$ as a power ($x\cdot x^{x-1}$) or as an exponential ($x^x\ln x$); each of those gives only one of the two terms of $x^x(\ln x+1)$.

## Related

- Topics: [[MATH1054 M08 - Differentiation II]] (derivation and Examples 8.25–8.26) · [[MATH1054 M07 - Functions]] (logarithms and exponentials)
- Concepts: [[Implicit and Parametric Differentiation]] · [[Product, Quotient and Chain Rules]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.3.14; MATH1054 Module Booklet, Module 8

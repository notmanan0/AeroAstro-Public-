---
title: "Euler's Formula"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["e^{jθ}", "Euler identity"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Hyperbolic Functions]]", "[[Phasor Representation]]", "[[Auxiliary Equation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.7, §3.2.9", "MATH1054 Module Booklet, Module 5"]
---

# Euler's Formula

Euler's formula states that $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$ for real $\theta$ in radians. It places $e^{\mathrm j\theta}$ on the unit circle at angle $\theta$, so every complex number can be written as $re^{\mathrm j\theta}$.

The formula follows from the Maclaurin series. Substituting $x=\mathrm j\theta$ into $e^x=\sum x^n/n!$ and using $\mathrm j^2=-1$, $\mathrm j^3=-\mathrm j$, $\mathrm j^4=1$,

$$
\begin{aligned}
e^{\mathrm j\theta}&=1+\mathrm j\theta-\frac{\theta^2}{2!}-\mathrm j\frac{\theta^3}{3!}+\frac{\theta^4}{4!}+\mathrm j\frac{\theta^5}{5!}-\dots\\
&=\Big(1-\frac{\theta^2}{2!}+\frac{\theta^4}{4!}-\dots\Big)+\mathrm j\Big(\theta-\frac{\theta^3}{3!}+\frac{\theta^5}{5!}-\dots\Big)\\
&=\cos\theta+\mathrm j\sin\theta .
\end{aligned}
$$

It is also consistent with the law of exponents: $e^{\mathrm j\theta_1}e^{\mathrm j\theta_2}=e^{\mathrm j(\theta_1+\theta_2)}$ written out with the formula is exactly the polar product rule $(\cos\theta_1+\mathrm j\sin\theta_1)(\cos\theta_2+\mathrm j\sin\theta_2)=\cos(\theta_1+\theta_2)+\mathrm j\sin(\theta_1+\theta_2)$. That is why exponential form $re^{\mathrm j\theta}$ turns multiplication, division and powers of complex numbers into adding, subtracting and multiplying exponents, and why $e^{x+\mathrm jy}=e^x(\cos y+\mathrm j\sin y)$ has modulus $e^x$ and argument $y$.

Replacing $\theta$ by $-\theta$ gives $e^{-\mathrm j\theta}=\cos\theta-\mathrm j\sin\theta$, because cosine is even and sine is odd. Adding and subtracting the two formulae gives

$$
\cos\theta=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}2,\qquad\sin\theta=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j},
$$

which is Specimen Test 5, Q5. With $\theta=\mathrm jy$ these become $\cos\mathrm jy=\cosh y$ and $\sin\mathrm jy=\mathrm j\sinh y$, the link to [[Hyperbolic Functions]] and the starting point for complex trigonometric and logarithmic functions in M22. The formula also explains the real solutions of a second-order ODE whose auxiliary equation has roots $\alpha\pm\mathrm j\beta$: $e^{(\alpha\pm\mathrm j\beta)t}=e^{\alpha t}(\cos\beta t\pm\mathrm j\sin\beta t)$, so $e^{\alpha t}\cos\beta t$ and $e^{\alpha t}\sin\beta t$ are solutions ([[Auxiliary Equation]]). In AC circuits a sinusoid $V\cos(\omega t+\phi)$ is the real part of $Ve^{\mathrm j\phi}e^{\mathrm j\omega t}$ ([[Phasor Representation]]).

Some values to know: $e^{\mathrm j\pi/2}=\mathrm j$, $e^{\mathrm j\pi}=-1$ and $e^{2k\pi\mathrm j}=1$. As a worked example, $e^{2+\mathrm j\pi/3}=e^2\big(\cos\frac\pi3+\mathrm j\sin\frac\pi3\big)=\frac12e^2+\frac{\sqrt3}2e^2\mathrm j=3.6945+6.3991\mathrm j$ (James Example 3.16). Because $e^{2k\pi\mathrm j}=1$, an exponent can be shifted by any multiple of $2\pi\mathrm j$ without changing the number, which is how $64e^{-5\pi\mathrm j}$ becomes $64e^{\pi\mathrm j}$ with a principal argument.

The trap is units: $\theta$ must be in radians, since the series and the derivative $\frac{d}{d\theta}e^{\mathrm j\theta}=\mathrm je^{\mathrm j\theta}$ both assume it. Writing $e^{\mathrm j60}$ for $e^{\mathrm j\pi/3}$ gives a different number. A second slip is to forget the $\mathrm j$ in the denominator of the sine formula, which would make $\sin\theta$ imaginary.

## Related

- Topics: [[MATH1054 M05 - Complex Numbers I]] (derivation in §7) · [[MATH1054 M22 - Complex Numbers II]] · [[MATH1054 M07 - Functions]]
- Concepts: [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Taylor and Maclaurin Series]] · [[Hyperbolic Functions]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Phasor Representation]] · [[Auxiliary Equation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.2.7 (Euler's formula), §3.2.9 (cosine and sine as exponentials); MATH1054 Module Booklet, Module 5

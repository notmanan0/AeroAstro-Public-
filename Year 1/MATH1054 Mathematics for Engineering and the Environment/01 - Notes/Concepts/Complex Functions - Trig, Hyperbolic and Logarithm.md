---
title: "Complex Functions - Trig, Hyperbolic and Logarithm"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex logarithm", "Complex sine", "sin z", "ln z", "Principal value of the logarithm", "Ln z"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Euler's Formula]]", "[[Hyperbolic Functions]]", "[[De Moivre's Theorem and Roots of Complex Numbers]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2.9–3.2.10", "MATH1054 Module Booklet, Module 22"]
---

# Complex Functions - Trig, Hyperbolic and Logarithm

The circular functions of a complex number are defined by the exponential formulas $\cos z=\frac12(e^{\mathrm jz}+e^{-\mathrm jz})$ and $\sin z=\frac1{2\mathrm j}(e^{\mathrm jz}-e^{-\mathrm jz})$, and a logarithm of $z\neq0$ is any $w$ with $e^w=z$, which gives the infinitely many values $\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi)$, $k\in\mathbb Z$.

For real $z$ the exponential formulas are identities that follow from adding and subtracting Euler's formula and its conjugate ([[Euler's Formula]]); for complex $z$ they are the definitions. Putting $z=\mathrm jx$ links the circular and hyperbolic families ([[Hyperbolic Functions]]): $\cos\mathrm jx=\frac12(e^{-x}+e^{x})=\cosh x$ and $\sin\mathrm jx=\frac{1}{2\mathrm j}(e^{-x}-e^{x})=\mathrm j\sinh x$, and in the other direction $\cosh\mathrm jx=\cos x$ and $\sinh\mathrm jx=\mathrm j\sin x$. These four results are the reason behind Osborn's rule. With the addition formulae, for $z=x+\mathrm jy$,

$$
\begin{aligned}
\sin z&=\sin x\cosh y+\mathrm j\cos x\sinh y, & \cos z&=\cos x\cosh y-\mathrm j\sin x\sinh y,\\
\sinh z&=\sinh x\cos y+\mathrm j\cosh x\sin y, & \cosh z&=\cosh x\cos y+\mathrm j\sinh x\sin y,
\end{aligned}
$$

and $\tan(x+\mathrm jy)=\dfrac{\sin2x+\mathrm j\sinh2y}{\cos2x+\cosh2y}$. Squaring and adding the parts of $\sin z$ with $\cosh^2y=1+\sinh^2y$ gives $|\sin z|^2=\sin^2x+\sinh^2y$, which grows without bound as $|y|$ grows. So $\sin z$ and $\cos z$ are **unbounded** off the real axis, and equations such as $\sin z=2$ have solutions.

To solve $f(z)=c$, write $z=x+\mathrm jy$, equate real and imaginary parts, and solve the simpler of the two real equations first; usually one factor has to vanish, and the other equation then fixes the rest. For $\cos z=2$ the parts are $\cos x\cosh y=2$ and $\sin x\sinh y=0$. $y=0$ would need $\cos x=2$, so $\sin x=0$; then $\cos x=\pm1$ and $\cosh y\ge1$ force $\cos x=+1$, giving $z=2k\pi\pm\mathrm j\ln(2+\sqrt3)=2k\pi\pm1.3170\mathrm j$ (Example 3.17(d)). The same steps for $\sin z=2$ give $z=\frac\pi2+2k\pi\pm1.317\mathrm j$ (Exercise 30(a)).

The logarithm comes from $e^{u+\mathrm jv}=e^u(\cos v+\mathrm j\sin v)=z$: the modulus gives $e^u=|z|$, so $u=\ln|z|$, and $v$ is any argument of $z$, $\operatorname{Arg}z+2k\pi$. The log is therefore **multi-valued**, with values spaced $2\pi\mathrm j$ apart. The principal value $\operatorname{Ln}z$ takes $k=0$ with $-\pi<\operatorname{Arg}z\le\pi$; for example $\ln(-1)=\mathrm j\pi$ and $\ln(-3)=\ln3+\mathrm j\pi$ as principal values. For $z=-3+4\mathrm j$, $|z|=5$ and $\operatorname{Arg}z=\pi-\tan^{-1}\frac43=2.2143$, so

$$
\ln(-3+4\mathrm j)=\ln5+\mathrm j(2.2143+2k\pi)=1.609+\mathrm j(2.214+2k\pi)\qquad\text{(Example 3.18)},
$$

and `cmath.log(-3+4j)` returns the principal value $1.6094+2.2143\mathrm j$. The same logarithm solves $\tanh z=2$: $\frac{e^{2z}-1}{e^{2z}+1}=2$ gives $e^{2z}=-3$, so $z=\frac12\ln3+\mathrm j(\frac\pi2+k\pi)$.

The common trap is to treat principal values as if the real log laws held. $\operatorname{Ln}(z_1z_2)$ and $\operatorname{Ln}z_1+\operatorname{Ln}z_2$ can differ by $2\pi\mathrm j$: with $z_1=z_2=-1+\mathrm j$, $\operatorname{Ln}(-2\mathrm j)=0.6931-1.5708\mathrm j$ but $2\operatorname{Ln}(-1+\mathrm j)=0.6931+4.7124\mathrm j$. The second trap is the bound $|\cos z|\le1$, which holds only for real $z$.

## Related

- Topic: [[MATH1054 M22 - Complex Numbers II]] (derivations in §1 and §2, with Examples 3.17–3.18, Exercises 29–30 and Exercise A)
- Concepts: [[Euler's Formula]] · [[Hyperbolic Functions]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]]
- Used later: $\ln z$ as the complex potential of a source or vortex in [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.2.9–3.2.10; MATH1054 Module Booklet, Module 22

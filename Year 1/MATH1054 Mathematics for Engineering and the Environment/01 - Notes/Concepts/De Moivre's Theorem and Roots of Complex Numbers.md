---
title: "De Moivre's Theorem and Roots of Complex Numbers"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["De Moivre", "nth roots", "Roots of unity"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Euler's Formula]]", "[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Argand Diagram]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.3.1–3.3.2", "MATH1054 Module Booklet, Module 22"]
---

# De Moivre's Theorem and Roots of Complex Numbers

De Moivre's theorem states that $\big[r(\cos\theta+\mathrm j\sin\theta)\big]^n=r^n(\cos n\theta+\mathrm j\sin n\theta)$ for every integer $n$, and applied backwards it gives the $n$ distinct $n$th roots $z^{1/n}=r^{1/n}e^{\mathrm j(\theta+2k\pi)/n}$, $k=0,1,\dots,n-1$.

In exponential form the theorem is the index law $(re^{\mathrm j\theta})^n=r^ne^{\mathrm jn\theta}$: a power raises the modulus to the power $n$ and multiplies the argument by $n$. For positive integers it can also be proved by induction, multiplying $\cos n\theta+\mathrm j\sin n\theta$ by $\cos\theta+\mathrm j\sin\theta$ and using the addition formulae. Replacing $\theta$ by $-\theta$ gives the version with minus signs, $(\cos\theta-\mathrm j\sin\theta)^n=\cos n\theta-\mathrm j\sin n\theta$, and adding the cases $n$ and $-n$ with $|z|=1$ gives $z^n+z^{-n}=2\cos n\theta$ and $z^n-z^{-n}=2\mathrm j\sin n\theta$, which turn powers of $\cos\theta$ into multiple angles.

Roots come from solving $w^n=z$ with $w=Re^{\mathrm j\phi}$. Comparing moduli gives $R=r^{1/n}$; comparing arguments gives $n\phi=\theta+2k\pi$, because two arguments of the same number may differ by any whole number of turns. So $\phi=\frac{\theta+2k\pi}{n}$, and $k$ and $k+n$ give the same root, which leaves exactly **$n$ distinct roots**, equally spaced by $\frac{2\pi}n$ on the circle of radius $r^{1/n}$, at the vertices of a regular $n$-gon. They sum to zero for $n\ge2$. A rational power $z^{p/q}$ with $p/q$ in lowest terms is $(z^{1/q})^p$ and has $q$ distinct values.

For example, $1-\mathrm j=\sqrt2e^{-\mathrm j\pi/4}$, so $(1-\mathrm j)^{12}=(\sqrt2)^{12}e^{-3\pi\mathrm j}=64(-1)=-64$ (Example 3.19), and squaring first agrees: $(1-\mathrm j)^2=-2\mathrm j$ and $(-2\mathrm j)^6=-64$. For the cube roots of $8+8\mathrm j=8\sqrt2e^{\mathrm j\pi/4}$ (Exercise 37), the modulus is $(8\sqrt2)^{1/3}=2^{7/6}=2.2449$ and the arguments are $\frac{\pi}{12}+\frac{2k\pi}3$, that is $15^\circ$, $135^\circ$ and $255^\circ$ ($-105^\circ$ in principal form):

$$
(8+8\mathrm j)^{1/3}=2.1684+0.5810\mathrm j,\quad-1.5874+1.5874\mathrm j,\quad-0.5810-2.1684\mathrm j,
$$

each of which cubes back to $8+8\mathrm j$ in `cmath`.

Square roots also solve **quadratics with complex coefficients**, where the usual formula holds and the work is finding $\sqrt\Delta$. Writing $(u+v\mathrm j)^2=\Delta$ gives $u^2-v^2=\operatorname{Re}\Delta$ and $2uv=\operatorname{Im}\Delta$, and the modulus adds $u^2+v^2=|\Delta|$, so $u^2$ and $v^2$ follow by adding and subtracting. For $z^2+(2\mathrm j-3)z+5-\mathrm j=0$ (Example 3.22), $\Delta=-15-8\mathrm j$, $|\Delta|=17$, $u^2=1$, $v^2=16$, $\sqrt\Delta=\pm(1-4\mathrm j)$, and $z=1+\mathrm j$ or $2-3\mathrm j$. Check with Vieta: the roots sum to $-b/a=3-2\mathrm j$ and multiply to $c/a=5-\mathrm j$.

The trap is forgetting the $2k\pi$: dividing only the principal argument by $n$ gives one root out of $n$. The second trap is leaving arguments outside $(-\pi,\pi]$ when the answer is asked for in principal form, such as $\frac{11\pi}8$ for a square root of $-\frac12+\frac12\mathrm j$, which should be written $-\frac{5\pi}8$.

## Related

- Topic: [[MATH1054 M22 - Complex Numbers II]] (§3 De Moivre's theorem, §4 roots and rational powers, §5 complex quadratics, §6 multiple angles)
- Concepts: [[Euler's Formula]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Argand Diagram]] · [[Complex Functions - Trig, Hyperbolic and Logarithm]]
- Used later: complex roots of the auxiliary equation in [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.3.1–3.3.2; MATH1054 Module Booklet, Module 22

---
title: "Complex Numbers - Cartesian, Polar and Exponential Forms"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 2: Complex Numbers"
aliases: ["Complex number forms", "Polar form", "Modulus and argument", "Exponential form"]
tags: [math1054, concept, complex-numbers]
status: complete
parent_lectures: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Argand Diagram]]", "[[Euler's Formula]]", "[[De Moivre's Theorem and Roots of Complex Numbers]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §3.2", "MATH1054 Module Booklet, Module 5"]
---

# Complex Numbers - Cartesian, Polar and Exponential Forms

A complex number $z$ can be written in cartesian form $x+\mathrm jy$, in polar form $r(\cos\theta+\mathrm j\sin\theta)=r\angle\theta$, or in exponential form $re^{\mathrm j\theta}$, where $r=|z|=\sqrt{x^2+y^2}$ is the modulus and $\theta=\arg z$ the argument. The three are the same number described by coordinates or by length and direction.

Conversion one way is direct: $x=r\cos\theta$ and $y=r\sin\theta$ hold in every quadrant. The other way, $r=\sqrt{x^2+y^2}$ is safe, but $\theta$ needs care because $\tan\theta=y/x$ cannot distinguish $(x,y)$ from $(-x,-y)$. Take the reference angle $\alpha=\tan^{-1}|y/x|$ and place it by quadrant: $\theta=\alpha$ in the first, $\pi-\alpha$ in the second, $-(\pi-\alpha)$ in the third and $-\alpha$ in the fourth. That gives the **principal argument**, the value in $-\pi<\theta\le\pi$; every other argument differs from it by a multiple of $2\pi$.

Each form suits different operations. Cartesian form is the one for adding, subtracting and equating real and imaginary parts, since those act component by component. Dividing in cartesian form means multiplying top and bottom by the conjugate of the denominator, $\dfrac{z_1}{z_2}=\dfrac{z_1z_2^*}{|z_2|^2}$, because $z_2z_2^*=x_2^2+y_2^2$ is real. Polar and exponential forms are the ones for multiplying, dividing and taking powers. Multiplying out $r_1(\cos\theta_1+\mathrm j\sin\theta_1)\,r_2(\cos\theta_2+\mathrm j\sin\theta_2)$ and using the compound-angle formulae gives

$$
z_1z_2=r_1r_2\big[\cos(\theta_1+\theta_2)+\mathrm j\sin(\theta_1+\theta_2)\big]=r_1r_2e^{\mathrm j(\theta_1+\theta_2)},
$$

so moduli multiply and arguments add; in exponential form the same result is just the law of exponents ([[Euler's Formula]]). Quotients divide the moduli and subtract the arguments, and $z^n=r^ne^{\mathrm jn\theta}$.

As an example, $-\sqrt6-\mathrm j\sqrt2$ (James Example 3.10(d)) is in the third quadrant with $r=\sqrt{6+2}=2\sqrt2$ and $\alpha=\tan^{-1}\frac{\sqrt2}{\sqrt6}=\frac\pi6$, so

$$
-\sqrt6-\mathrm j\sqrt2=2\sqrt2\Big[\cos\Big(-\frac{5\pi}6\Big)+\mathrm j\sin\Big(-\frac{5\pi}6\Big)\Big]=2\sqrt2\,e^{-5\pi\mathrm j/6}.
$$

Long products are where polar form pays off: $\dfrac{(1+2\mathrm j)^2(4-3\mathrm j)^3}{(3+4\mathrm j)^4(2-\mathrm j)^3}$ has modulus $\dfrac{5\cdot125}{625\cdot5\sqrt5}=\dfrac{\sqrt5}{25}$ and argument $2(1.1071)+3(-0.6435)-4(0.9273)-3(-0.4636)=-2.0344$, which is $-\frac1{25}-\frac2{25}\mathrm j$ (Example 3.14). Going the other way, $e^{2+\mathrm j\pi/3}=e^2\big(\cos\frac\pi3+\mathrm j\sin\frac\pi3\big)=3.6945+6.3991\mathrm j$ (Example 3.16).

The common trap is the calculator's $\tan^{-1}(y/x)$, which lies in $(-\frac\pi2,\frac\pi2)$ and is wrong in the second and third quadrants: for $-1+\mathrm j$ it gives $-\frac\pi4$ instead of $\frac{3\pi}4$. The second trap is forgetting to bring a sum of arguments back into $(-\pi,\pi]$; in Example 3.12 the arguments add to $5.245$ rad, which is $5.245-2\pi=-1.038$ rad as a principal value.

## Related

- Topics: [[MATH1054 M05 - Complex Numbers I]] (derivations in §2–§7) · [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Argand Diagram]] · [[Euler's Formula]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Phasor Representation]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §3.2.2–3.2.7; MATH1054 Module Booklet, Module 5

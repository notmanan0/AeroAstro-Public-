---
title: "MATH1054 M05 - Complex Numbers I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 2: Complex Numbers"
order: 5
tags:
  - math1054
  - complex-numbers
  - argand-diagram
aliases: ["MATH1054 Module 5", "Complex Numbers I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M22 - Complex Numbers II]]"]
key_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Euler's Formula]]", "[[Argand Diagram]]"]
tutorial_sheets: ["[[MATH1054 M05 Solutions - Complex Numbers I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 5)", "02 - Sources/Modern Engineering Mathematics.pdf (§3.2, §4.2.x Ex 4.15)"]
---

# MATH1054 M05 - Complex Numbers I

> [!abstract] Summary
> A complex number $z=x+\mathrm jy$ with $\mathrm j^2=-1$ is a **point, or vector, in the plane**. It has three equivalent descriptions:
> - **cartesian** $x+\mathrm jy$, best for adding;
> - **polar** $r(\cos\theta+\mathrm j\sin\theta)$, best for multiplying and dividing;
> - **exponential** $re^{\mathrm j\theta}$, which is Euler's compact version of polar.
>
> The whole module is about moving fluently between the three forms, and knowing which one makes a given operation easy.

## Key Concepts
- [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Euler's Formula]] · [[Argand Diagram]] · Applications: [[Phasor Representation]], [[Complex Impedance]] (FEEG1004)

---

## 1. Cartesian algebra (James §3.2.1–3.2.5)
- $\operatorname{Re}z=x$ and $\operatorname{Im}z=y$. **Both are real numbers**, so $\operatorname{Im}(-3+\mathrm j)=1$, not $\mathrm j$.
- **Equality**: $z_1=z_2$ iff the real parts match *and* the imaginary parts match. This gives **two** real equations from one complex equation (Ex 3.2, Ex 17).
- **Add and subtract** componentwise. **Multiply** by expanding and using $\mathrm j^2=-1$.
- **Conjugate**: $z^*=x-\mathrm jy$. Then $zz^*=|z|^2$ is real.
- **Divide** by multiplying the top and bottom by the conjugate of the denominator:
$$
\frac{z_1}{z_2}=\frac{z_1z_2^*}{|z_2|^2}
$$
- Real polynomials have roots in **conjugate pairs**. For example, $x^3+8=(x+2)(x^2-2x+4)$ has roots $-2$ and $1\pm\mathrm j\sqrt3$.

## 2. The Argand diagram and polar form (James §3.2.6–3.2.7)
$$
r=|z|=\sqrt{x^2+y^2},\qquad x=r\cos\theta,\quad y=r\sin\theta
$$

![[m1054_polar_form_quadrants.png|560]]

The **principal argument** is $-\pi<\theta\le\pi$. Let $\alpha=\tan^{-1}|y/x|$ be the reference angle.

| Quadrant | sign of $(x,y)$ | $\theta$ |
|---|---|---|
| 1 | $(+,+)$ | $\alpha$ |
| 2 | $(-,+)$ | $\pi-\alpha$ |
| 3 | $(-,-)$ | $-(\pi-\alpha)$ |
| 4 | $(+,-)$ | $-\alpha$ |

> [!warning] Don't trust the calculator's $\tan^{-1}(y/x)$
> It only returns values in $(-\frac\pi2,\frac\pi2)$, so it is wrong in quadrants 2 and 3. **Sketch the point first.**

## 3. Multiplication and division in polar form
$$
z_1z_2=r_1r_2\angle(\theta_1+\theta_2),\qquad\frac{z_1}{z_2}=\frac{r_1}{r_2}\angle(\theta_1-\theta_2),\qquad z^n=r^n\angle n\theta
$$
Moduli multiply and arguments **add**. After adding, reduce to $(-\pi,\pi]$ by adding or subtracting $2\pi$ (Ex 3.12: $5.245\to-1.038$ rad).

- **Big products** (Ex 3.14): compute each factor's modulus and argument *once*, then combine with the powers.
- **Multiplying by $\mathrm j$** rotates by $+90°$ without changing the length. Ex 4.15 uses this to build a square on OP: $\mathrm j(1+2\mathrm j)=-2+\mathrm j$.

## 4. Euler's formula and exponential form (James §3.2.8)
$$
e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta\qquad\Longrightarrow\qquad z=re^{\mathrm j\theta},\quad e^{x+\mathrm jy}=e^x(\cos y+\mathrm j\sin y)
$$
The exponential laws now do the polar rules automatically: $r_1e^{\mathrm j\theta_1}\cdot r_2e^{\mathrm j\theta_2}=r_1r_2e^{\mathrm j(\theta_1+\theta_2)}$. Replacing $\theta$ by $-\theta$ and then adding or subtracting gives the inverse relations:
$$
\cos\theta=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}2,\qquad\sin\theta=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j}
$$
These lead directly to $\cosh$ and $\sinh$ ([[MATH1054 M07 - Functions|M07]]), and to complex trig functions and logs ([[MATH1054 M22 - Complex Numbers II|M22]]).

## 5. Geometry of $+$ and $-$
- $z_1+z_2$ is the diagonal of the parallelogram on $z_1$ and $z_2$.
- $z_1-z_2$ is the vector **from $z_2$ to $z_1$**, so $|z_1-z_2|$ is the distance between the points. This is the key to the loci in M22: $|z-a|=r$ is a circle.
- **Triangle inequality**: $|z_1+z_2|\le|z_1|+|z_2|$.

## Method checklist
1. For sums, differences and equality, use **cartesian** form.
2. For products, quotients, powers and roots, use **polar or exponential** form.
3. For a quotient in cartesian form, multiply by the conjugate.
4. For arguments: sketch the point, find $\alpha$, adjust for the quadrant, and reduce to $(-\pi,\pi]$.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M05 Solutions - Complex Numbers I]]
- Next: [[MATH1054 M22 - Complex Numbers II]] (De Moivre, roots, loci, complex functions)
- Used in: [[MATH1054 M06 - Differential Equations I]] (complex auxiliary roots), FEEG1004 AC circuits ([[Phasor Representation]])

## Sources
- MATH1054 Module Booklet, Module 5; James §3.2 and Example 4.15

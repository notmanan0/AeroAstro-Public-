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
status: lectured
coverage: "Module Booklet Module 5 work scheme; James §3.1, §3.2.1–3.2.7 and §3.2.9 (cos and sin as exponentials), §4.2.6 (complex numbers as vectors, Ex 4.15)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M22 - Complex Numbers II]]"]
key_concepts: ["[[Complex Numbers - Cartesian, Polar and Exponential Forms]]", "[[Euler's Formula]]", "[[Argand Diagram]]"]
tutorial_sheets: ["[[MATH1054 M05 Solutions - Complex Numbers I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 5)", "02 - Sources/Modern Engineering Mathematics.pdf (§3.1–3.2, §4.2.6 Ex 4.15)"]
---

# MATH1054 M05 - Complex Numbers I

> [!abstract] Summary
> A complex number $z=x+\mathrm jy$, with $\mathrm j^2=-1$, is a point or a vector in the plane, so it can be described either by its cartesian coordinates $(x,y)$ or by its length $r=|z|$ and angle $\theta=\arg z$. Cartesian form makes addition, subtraction and equating parts easy; polar form $r(\cos\theta+\mathrm j\sin\theta)$ makes multiplication easy, because moduli multiply and arguments add. Euler's formula $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$ compresses polar form to $re^{\mathrm j\theta}$, so the polar rules become the ordinary laws of exponents, and it gives $\cos\theta$ and $\sin\theta$ as combinations of $e^{\pm\mathrm j\theta}$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a sum, product, quotient, power, modulus or argument, or for $x$ and $y$ from a complex equation.
> - **Assumptions:** $\mathrm j^2=-1$; angles in radians; the principal argument lies in $-\pi<\theta\le\pi$; $\arg0$ is undefined.
> - **Method:** 1. Sketch the point and note its quadrant. 2. For $+$, $-$ and equations, stay in cartesian form and equate real and imaginary parts. 3. For a quotient in cartesian form, multiply top and bottom by the conjugate of the denominator. 4. For products, quotients and powers, find each $r$ and $\theta$ once, multiply the moduli and add the arguments. 5. Bring the argument back into $(-\pi,\pi]$ by adding or subtracting $2\pi$, then convert back with $x=r\cos\theta$, $y=r\sin\theta$.
> - **Common mistakes:** taking the calculator value of $\tan^{-1}(y/x)$ for a point in the second or third quadrant; leaving an argument such as $5.245$ or $\frac{13\pi}{12}$ outside $(-\pi,\pi]$.
> - **Practise:** [[#Powers and long products]] · [[MATH1054 M05 Solutions - Complex Numbers I#Part C: Specimen Test 5|Specimen Test 5]]

Real numbers fill a line, and on a line $x^2+1=0$ has no solution. Allowing one new number $\mathrm j$ with $\mathrm j^2=-1$ removes the obstruction: every quadratic, and indeed every polynomial, then has its full set of roots. The numbers then no longer fit on a line. A complex number has two independent real parts, so it is a point in a plane, the Argand diagram, and arithmetic on complex numbers is geometry in that plane: adding is placing vectors head to tail, and multiplying is stretching and rotating.

Engineers write $\mathrm j$ rather than the mathematician's $i$, because $i$ is already the symbol for current. In engineering their main use is describing rotation and oscillation. A sinusoid $A\cos(\omega t+\phi)$ is the real part of $Ae^{\mathrm j\phi}e^{\mathrm j\omega t}$, a vector of length $A$ turning at rate $\omega$, so adding sinusoids of one frequency becomes adding vectors, and differentiating becomes multiplying by $\mathrm j\omega$. That is the phasor method of AC circuit analysis ([[Phasor Representation]], [[Complex Impedance]]) and the reason the auxiliary equation of a vibrating system can have complex roots $\alpha\pm\mathrm j\beta$ whose solutions are $e^{\alpha t}\cos\beta t$ and $e^{\alpha t}\sin\beta t$ ([[MATH1054 M06 - Differential Equations I|M06]]).

De Moivre's theorem, roots of complex numbers, loci in the plane, and the trigonometric, hyperbolic and logarithmic functions of a complex variable ([[MATH1054 M22 - Complex Numbers II|M22]]) are all built on cartesian arithmetic, the conjugate, modulus and argument, polar form, Euler's formula and the vector picture.

---

## 1. Complex numbers, j and the Argand diagram

Define $\mathrm j=\sqrt{-1}$, so that $\mathrm j^2=-1$. The square root of any negative number is then a real multiple of $\mathrm j$: for a positive real $b$,

$$
\begin{aligned}
\sqrt{-b}&=\sqrt{b\,(-1)}\\
&=\sqrt b\,\sqrt{-1}\\
&=\pm\mathrm j\sqrt b ,
\end{aligned}
$$

so that, for example, $\sqrt{-16}=\pm4\mathrm j$, with both signs because $(\pm4\mathrm j)^2=16\mathrm j^2=-16$.

A **complex number** is $z=x+\mathrm jy$ with $x$ and $y$ real. The **real part** is $\operatorname{Re}z=x$ and the **imaginary part** is $\operatorname{Im}z=y$. Both are real numbers: the imaginary part does not include the $\mathrm j$, so $\operatorname{Im}(3-2\mathrm j)=-2$ and $\operatorname{Im}(-3+\mathrm j)=1$. If $x=0$ the number is purely imaginary, and if $y=0$ it is purely real. A particular number is usually written $3-2\mathrm j$; James writes $3-\mathrm j2$, which is the same number because $2\mathrm j=\mathrm j2$.

### Roots of polynomials

The quadratic $ax^2+bx+c=0$ has the roots

$$
x=\frac{-b\pm\sqrt{b^2-4ac}}{2a},
$$

which are real when $b^2\ge4ac$ and complex when $b^2<4ac$, because then the square root is $\mathrm j\sqrt{4ac-b^2}$. For $x^2+2x+2=0$ (Exercise 8(a)):

$$
\begin{aligned}
x&=\frac{-2\pm\sqrt{4-8}}{2}\\
&=\frac{-2\pm\sqrt{-4}}{2}\\
&=\frac{-2\pm2\mathrm j}{2}\\
&=-1\pm\mathrm j .
\end{aligned}
$$

Every quadratic that is irreducible over the reals therefore splits into two complex factors, for instance $x^2+2x+5=(x+1+2\mathrm j)(x+1-2\mathrm j)$. The **fundamental theorem of algebra**, whose proof is beyond this module, extends this to every degree: a polynomial equation of degree $n$ has exactly $n$ roots, counted with multiplicity, real or complex. The seventh-degree equation $x^7-7x^5-6x^4+4x^3-28x-24=0$ has the seven roots $-1$, $-2$, $3$, $1\pm\mathrm j$ and $-1\pm\mathrm j$. When the coefficients are real, the non-real roots come in conjugate pairs ([[#3. The complex conjugate|§3]] proves this).

For the cubic $x^3+8=0$ (Exercise 8(b)), $x=-2$ is a root by inspection, so $x+2$ is a factor:

$$
x^3+8=(x+2)(x^2-2x+4).
$$

The quadratic factor gives

$$
\begin{aligned}
x&=\frac{2\pm\sqrt{4-16}}{2}\\
&=\frac{2\pm2\mathrm j\sqrt3}{2}\\
&=1\pm\mathrm j\sqrt3 ,
\end{aligned}
$$

so the three roots are $-2$ and $1\pm\mathrm j\sqrt3$. All three have modulus 2 and are spaced $120°$ apart; they are the three cube roots of $-8$, which [[MATH1054 M22 - Complex Numbers II|M22]] finds directly.

### The Argand diagram

The number $x+\mathrm jy$ is plotted as the point $(x,y)$, with the real axis horizontal and the imaginary axis vertical. This plane is the **Argand diagram** (also called the complex plane). The vertical coordinate is $y$, not $\mathrm jy$; the $\mathrm j$ is accounted for by the choice of axis.

![[m1054_argand_points.png|900]]

Example 3.1 plots $3+2\mathrm j$, $-5+3\mathrm j$, $8-5\mathrm j$ and $-2-3\mathrm j$ at $(3,2)$, $(-5,3)$, $(8,-5)$ and $(-2,-3)$, one in each quadrant. Exercise 1 plots $1+\mathrm j$, $\sqrt3-\mathrm j$, $-3+4\mathrm j$, $1-\mathrm j\sqrt3$, $-1+\mathrm j\sqrt3$ and $-1-\mathrm j\sqrt3$. Of these, $\sqrt3-\mathrm j$, $1-\mathrm j\sqrt3$, $-1+\mathrm j\sqrt3$ and $-1-\mathrm j\sqrt3$ all have modulus 2, so they lie on the circle $|z|=2$, at angles $-30°$, $-60°$, $120°$ and $-120°$.

## 2. Cartesian arithmetic

### Equality

Two complex numbers are equal when they are the same point of the Argand diagram, so

$$
x_1+\mathrm jy_1=x_2+\mathrm jy_2\iff x_1=x_2\ \text{and}\ y_1=y_2 .
$$

One complex equation is therefore two real equations, which is how a single complex equation can determine two real unknowns.

In Example 3.2, $z_1=(3a+2)+\mathrm j(3b-1)$ and $z_2=(b+1)-\mathrm j(a+2-b)$ are equal, with $a$ and $b$ real. Equating real parts:

$$
\begin{aligned}
3a+2&=b+1\\
b&=3a+1 .
\end{aligned}
$$

Equating imaginary parts:

$$
\begin{aligned}
3b-1&=-(a+2-b)\\
3b-1&=-a-2+b\\
2b&=-a-1 .
\end{aligned}
$$

Substitute the first into the second:

$$
\begin{aligned}
2(3a+1)&=-a-1\\
7a&=-3\\
a&=-\tfrac37,\qquad b=3\big(-\tfrac37\big)+1=-\tfrac27 .
\end{aligned}
$$

Then $\operatorname{Re}z_1=3a+2=\frac57$ and $\operatorname{Im}z_1=3b-1=-\frac{13}7$, and the same values come from $z_2$, so $z_1=z_2=\frac57-\frac{13}7\mathrm j$.

### Addition and subtraction

Add or subtract the real parts and the imaginary parts separately:

$$
z_1\pm z_2=(x_1\pm x_2)+\mathrm j(y_1\pm y_2).
$$

With $z_1=3+2\mathrm j$ and $z_2=5-3\mathrm j$ (Example 3.3), $z_1+z_2=8-\mathrm j$ and $z_1-z_2=-2+5\mathrm j$.

### Multiplication and powers of j

Multiply out the brackets as for real numbers and replace $\mathrm j^2$ by $-1$:

$$
\begin{aligned}
z_1z_2&=(x_1+\mathrm jy_1)(x_2+\mathrm jy_2)\\
&=x_1x_2+\mathrm jx_1y_2+\mathrm jy_1x_2+\mathrm j^2y_1y_2\\
&=(x_1x_2-y_1y_2)+\mathrm j(x_1y_2+x_2y_1).
\end{aligned}
$$

For Example 3.4, $(3+2\mathrm j)(5+3\mathrm j)=15+9\mathrm j+10\mathrm j+6\mathrm j^2=9+19\mathrm j$.

Powers of $\mathrm j$ repeat with period 4:

$$
\mathrm j^2=-1,\qquad\mathrm j^3=\mathrm j\,\mathrm j^2=-\mathrm j,\qquad\mathrm j^4=\mathrm j^2\mathrm j^2=1,\qquad\mathrm j^5=\mathrm j,\ \dots
$$

so $\mathrm j^n$ depends only on the remainder of $n$ on division by 4. For example $\mathrm j^{11}=\mathrm j^{8}\mathrm j^3=-\mathrm j$, and $1/\mathrm j=\mathrm j^4/\mathrm j=\mathrm j^3=-\mathrm j$.

### Division

To divide, multiply the top and bottom by $x_2-\mathrm jy_2$, which makes the denominator real:

$$
\begin{aligned}
\frac{z_1}{z_2}&=\frac{(x_1+\mathrm jy_1)(x_2-\mathrm jy_2)}{(x_2+\mathrm jy_2)(x_2-\mathrm jy_2)}\\
&=\frac{x_1x_2-\mathrm jx_1y_2+\mathrm jy_1x_2-\mathrm j^2y_1y_2}{x_2^2-\mathrm j^2y_2^2}\\
&=\frac{(x_1x_2+y_1y_2)+\mathrm j(x_2y_1-x_1y_2)}{x_2^2+y_2^2}.
\end{aligned}
$$

The general formula is not worth memorising; the method is. For Example 3.5,

$$
\begin{aligned}
\frac{3+2\mathrm j}{5+3\mathrm j}&=\frac{(3+2\mathrm j)(5-3\mathrm j)}{(5+3\mathrm j)(5-3\mathrm j)}\\
&=\frac{15-9\mathrm j+10\mathrm j+6}{25+9}\\
&=\frac{21+\mathrm j}{34}=\frac{21}{34}+\frac1{34}\mathrm j .
\end{aligned}
$$

Example 3.6 asks for the real and imaginary parts of $z+1/z$ when $z=(2+\mathrm j)/(1-\mathrm j)$. First simplify $z$:

$$
\begin{aligned}
z&=\frac{(2+\mathrm j)(1+\mathrm j)}{(1-\mathrm j)(1+\mathrm j)}\\
&=\frac{2+2\mathrm j+\mathrm j-1}{2}\\
&=\tfrac12+\tfrac32\mathrm j .
\end{aligned}
$$

The reciprocal is the original fraction upside down:

$$
\begin{aligned}
\frac1z&=\frac{1-\mathrm j}{2+\mathrm j}\\
&=\frac{(1-\mathrm j)(2-\mathrm j)}{(2+\mathrm j)(2-\mathrm j)}\\
&=\frac{2-\mathrm j-2\mathrm j-1}{5}\\
&=\tfrac15-\tfrac35\mathrm j .
\end{aligned}
$$

Adding, $z+1/z=\big(\frac12+\frac15\big)+\mathrm j\big(\frac32-\frac35\big)=\frac7{10}+\frac9{10}\mathrm j$, so the real part is $\frac7{10}$ and the imaginary part $\frac9{10}$.

Exercise 6 practises all four operations: $(5+3\mathrm j)(2-\mathrm j)-(3+\mathrm j)=13+\mathrm j-3-\mathrm j=10$; $(1-2\mathrm j)^2=-3-4\mathrm j$; $\frac{1-\mathrm j}{1+\mathrm j}=\frac{(1-\mathrm j)^2}{2}=-\mathrm j$; $(3-2\mathrm j)^2=5-12\mathrm j$; and $\frac1{5-3\mathrm j}-\frac1{5+3\mathrm j}=\frac{(5+3\mathrm j)-(5-3\mathrm j)}{34}=\frac3{17}\mathrm j$.

### Equating real and imaginary parts in practice

Exercise 12 solves the simultaneous equations $4z+3w=23$ and $z+\mathrm jw=6+8\mathrm j$ for complex $z$ and $w$. Elimination works exactly as with real unknowns. From the second equation, $z=6+8\mathrm j-\mathrm jw$; substitute into the first:

$$
\begin{aligned}
4(6+8\mathrm j-\mathrm jw)+3w&=23\\
24+32\mathrm j-4\mathrm jw+3w&=23\\
w(3-4\mathrm j)&=-1-32\mathrm j\\
w&=\frac{(-1-32\mathrm j)(3+4\mathrm j)}{(3-4\mathrm j)(3+4\mathrm j)}\\
&=\frac{-3-4\mathrm j-96\mathrm j+128}{25}\\
&=\frac{125-100\mathrm j}{25}=5-4\mathrm j .
\end{aligned}
$$

Back-substitute: $z=6+8\mathrm j-\mathrm j(5-4\mathrm j)=6+8\mathrm j-5\mathrm j-4=2+3\mathrm j$. As a check, $4z+3w=8+12\mathrm j+15-12\mathrm j=23$.

Exercise 17 asks for real $x$ and $y$ with $\dfrac{2+x-\mathrm jy}{3x+\mathrm jy}=1+2\mathrm j$. Clear the fraction first, then equate parts:

$$
\begin{aligned}
2+x-\mathrm jy&=(1+2\mathrm j)(3x+\mathrm jy)\\
&=3x+\mathrm jy+6\mathrm jx+2\mathrm j^2y\\
&=(3x-2y)+\mathrm j(6x+y).
\end{aligned}
$$

The real parts give $2+x=3x-2y$, so $x-y=1$. The imaginary parts give $-y=6x+y$, so $y=-3x$. Then $x+3x=1$, so $x=\frac14$ and $y=-\frac34$.

## 3. The complex conjugate

The **complex conjugate** of $z=x+\mathrm jy$ is $z^*=x-\mathrm jy$: the sign of the imaginary part changes, so on the Argand diagram $z^*$ is the reflection of $z$ in the real axis. Adding and subtracting $z$ and $z^*$ isolates the two parts,

$$
\begin{aligned}
z+z^*&=(x+\mathrm jy)+(x-\mathrm jy)=2x=2\operatorname{Re}z,\\
z-z^*&=(x+\mathrm jy)-(x-\mathrm jy)=2\mathrm jy=2\mathrm j\operatorname{Im}z,
\end{aligned}
$$

and multiplying them gives a real, non-negative number:

$$
\begin{aligned}
zz^*&=(x+\mathrm jy)(x-\mathrm jy)\\
&=x^2-\mathrm jxy+\mathrm jxy-\mathrm j^2y^2\\
&=x^2+y^2 .
\end{aligned}
$$

That product is why the conjugate clears a denominator. Dividing $z^*$ by it gives the reciprocal, and multiplying by $z_1$ gives any quotient:

$$
\frac1z=\frac{z^*}{zz^*}=\frac{z^*}{x^2+y^2},\qquad\frac{z_1}{z_2}=\frac{z_1z_2^*}{z_2z_2^*}.
$$

For $z=2-3\mathrm j$ (Exercise 10), $z^*=2+3\mathrm j$, $zz^*=4+9=13$ and $1/z=(2+3\mathrm j)/13$.

The conjugate passes through sums and products. For sums this is immediate, $(z_1+z_2)^*=(x_1+x_2)-\mathrm j(y_1+y_2)=z_1^*+z_2^*$. For products, conjugate the expansion from [[#Multiplication and powers of j]]:

$$
\begin{aligned}
(z_1z_2)^*&=(x_1x_2-y_1y_2)-\mathrm j(x_1y_2+x_2y_1),\\
z_1^*z_2^*&=(x_1-\mathrm jy_1)(x_2-\mathrm jy_2)\\
&=x_1x_2-\mathrm jx_1y_2-\mathrm jy_1x_2+\mathrm j^2y_1y_2\\
&=(x_1x_2-y_1y_2)-\mathrm j(x_1y_2+x_2y_1),
\end{aligned}
$$

so $(z_1z_2)^*=z_1^*z_2^*$, and by repetition $(z^n)^*=(z^*)^n$. With $z_1=5+3\mathrm j$ and $z_2=3-2\mathrm j$, $z_1z_2=21-\mathrm j$ and $z_1^*z_2^*=(5-3\mathrm j)(3+2\mathrm j)=21+\mathrm j$, the conjugate as expected.

These two rules prove that the non-real roots of a real polynomial come in conjugate pairs. Let $p(z)=a_nz^n+\dots+a_1z+a_0$ with every $a_k$ real, and suppose $p(z_0)=0$. Conjugate the equation:

$$
\begin{aligned}
0=\big(p(z_0)\big)^*&=a_n^*(z_0^*)^n+\dots+a_1^*z_0^*+a_0^*\\
&=a_n(z_0^*)^n+\dots+a_1z_0^*+a_0\\
&=p(z_0^*),
\end{aligned}
$$

using $a_k^*=a_k$ for real coefficients. So $z_0^*$ is a root as well: $3\pm2\mathrm j$ for $x^2-6x+13$, and $1\pm\mathrm j\sqrt3$ for $x^3+8$. The argument fails when the coefficients are complex.

## 4. Modulus and argument

A point of the plane is fixed equally well by its distance from the origin and its direction. The **modulus** $|z|=r$ is the length of $OP$, and the **argument** $\arg z=\theta$ is the angle from the positive real axis to $OP$, anticlockwise positive. Pythagoras gives

$$
r=|z|=\sqrt{x^2+y^2},
$$

the square root of $x^2+y^2$, never of $x^2+(\mathrm jy)^2$. Comparing with [[#3. The complex conjugate|§3]], $zz^*=|z|^2$.

Adding any multiple of $2\pi$ to $\theta$ gives the same direction and so the same number, so the argument is fixed by a convention. The **principal argument** is the one value in

$$
-\pi<\theta\le\pi ,
$$

written $\operatorname{Arg}z$ when it needs distinguishing from the full set $\arg z=\operatorname{Arg}z+2k\pi$, $k\in\mathbb Z$. The argument of $0$ is undefined.

From the right-angled triangle, $\tan\theta=y/x$, but $\tan$ has period $\pi$, so this equation alone cannot tell $(x,y)$ from $(-x,-y)$. Work instead with the acute reference angle

$$
\alpha=\tan^{-1}\left|\frac yx\right|,\qquad0\le\alpha\le\tfrac\pi2,
$$

and place it in the right quadrant by the signs of $x$ and $y$. In the second quadrant the direction is $\alpha$ above the negative real axis, which lies at $\pi$, so $\theta=\pi-\alpha$. In the third it is $\alpha$ below the negative real axis; measured clockwise that axis lies at $-\pi$, so $\theta=-\pi+\alpha=-(\pi-\alpha)$. In the fourth it is $\alpha$ below the positive real axis, so $\theta=-\alpha$.

| Quadrant | signs of $(x,y)$ | principal argument $\theta$ |
|---|---|---|
| 1 | $(+,+)$ | $\alpha$ |
| 2 | $(-,+)$ | $\pi-\alpha$ |
| 3 | $(-,-)$ | $-(\pi-\alpha)$ |
| 4 | $(+,-)$ | $-\alpha$ |

![[m1054_polar_form_quadrants.png|620]]

> [!warning] The calculator's inverse tangent is wrong in two quadrants
> $\tan^{-1}(y/x)$ on a calculator returns a value in $(-\frac\pi2,\frac\pi2)$, which is correct only in quadrants 1 and 4. For $-1+\mathrm j$ it gives $\tan^{-1}(-1)=-\frac\pi4$, a fourth-quadrant direction, while the point is in the second quadrant with argument $\frac{3\pi}4$. Sketch the point before taking any inverse tangent.

Example 3.10 has one point in each quadrant:

| $z$ | quadrant | $\lvert z\rvert$ | $\alpha$ | $\operatorname{Arg}z$ |
|---|---|---|---|---|
| $3+2\mathrm j$ | 1 | $\sqrt{13}=3.606$ | $\tan^{-1}\frac23=0.588$ | $0.588$ rad ($33.69°$) |
| $1-\mathrm j$ | 4 | $\sqrt2=1.414$ | $\frac\pi4$ | $-\frac\pi4$ |
| $-1+\mathrm j$ | 2 | $\sqrt2=1.414$ | $\frac\pi4$ | $\pi-\frac\pi4=\frac{3\pi}4$ |
| $-\sqrt6-\mathrm j\sqrt2$ | 3 | $\sqrt{6+2}=2\sqrt2=2.828$ | $\tan^{-1}\frac{\sqrt2}{\sqrt6}=\tan^{-1}\frac1{\sqrt3}=\frac\pi6$ | $-\big(\pi-\frac\pi6\big)=-\frac{5\pi}6$ |

## 5. Polar form

From the triangle with hypotenuse $r$ and angle $\theta$,

$$
x=r\cos\theta,\qquad y=r\sin\theta,
$$

so substituting into $z=x+\mathrm jy$ gives the **polar form**

$$
z=r\cos\theta+\mathrm jr\sin\theta=r(\cos\theta+\mathrm j\sin\theta),
$$

which engineers abbreviate to $r\angle\theta$. These two equations hold in every quadrant, because $\cos\theta$ and $\sin\theta$ carry the signs of $x$ and $y$; only the inverse direction, finding $\theta$ from $x$ and $y$, needs the quadrant table.

Example 3.11 converts three numbers:

| $z$ | $r$ | $\theta$ | polar form |
|---|---|---|---|
| $12+5\mathrm j$ | $\sqrt{144+25}=13$ | $\tan^{-1}\frac5{12}=0.3948$ ($22.62°$) | $13(\cos0.3948+\mathrm j\sin0.3948)$ |
| $-3+4\mathrm j$ | $\sqrt{9+16}=5$ | $\pi-\tan^{-1}\frac43=2.2143$ ($126.87°$) | $5(\cos2.2143+\mathrm j\sin2.2143)$ |
| $-4-3\mathrm j$ | $\sqrt{16+9}=5$ | $-\big(\pi-\tan^{-1}\frac34\big)=-2.4981$ ($-143.13°$) | $5\big(\cos(-2.4981)+\mathrm j\sin(-2.4981)\big)$ |

Because $\cos(-t)=\cos t$ and $\sin(-t)=-\sin t$, the last can also be written $5(\cos2.4981-\mathrm j\sin2.4981)$. Converting back, $5(\cos2.2143+\mathrm j\sin2.2143)=-3.000+4.000\mathrm j$, which confirms the second-quadrant angle.

Exercise 24 includes the points on the axes, where no inverse tangent is needed: $\mathrm j=1\angle\frac\pi2$ and $-1=1\angle\pi$ (the principal range includes $+\pi$ and excludes $-\pi$). The others are $\sqrt3-\mathrm j\sqrt3=\sqrt6\angle\big(-\frac\pi4\big)$, then $-3-2\mathrm j=\sqrt{13}\angle\big(-(\pi-\tan^{-1}\frac23)\big)=\sqrt{13}\angle(-2.554)$, and $(2-\mathrm j)(2+\mathrm j)=4+1=5=5\angle0$.

## 6. Multiplication, division and powers in polar form

### Multiplication

Let $z_1=r_1(\cos\theta_1+\mathrm j\sin\theta_1)$ and $z_2=r_2(\cos\theta_2+\mathrm j\sin\theta_2)$. Multiply out:

$$
\begin{aligned}
z_1z_2&=r_1r_2(\cos\theta_1+\mathrm j\sin\theta_1)(\cos\theta_2+\mathrm j\sin\theta_2)\\
&=r_1r_2\big[\cos\theta_1\cos\theta_2+\mathrm j\cos\theta_1\sin\theta_2+\mathrm j\sin\theta_1\cos\theta_2+\mathrm j^2\sin\theta_1\sin\theta_2\big]\\
&=r_1r_2\big[(\cos\theta_1\cos\theta_2-\sin\theta_1\sin\theta_2)+\mathrm j(\sin\theta_1\cos\theta_2+\cos\theta_1\sin\theta_2)\big].
\end{aligned}
$$

The two brackets are the compound-angle formulae $\cos(\theta_1+\theta_2)$ and $\sin(\theta_1+\theta_2)$, so

$$
z_1z_2=r_1r_2\big[\cos(\theta_1+\theta_2)+\mathrm j\sin(\theta_1+\theta_2)\big],
$$

which says

$$
|z_1z_2|=|z_1||z_2|,\qquad\arg(z_1z_2)=\arg z_1+\arg z_2 .
$$

Moduli multiply and arguments add. The sum of two principal arguments can leave $(-\pi,\pi]$, in which case add or subtract $2\pi$.

A first example with exact angles is $z_1=1+\mathrm j=\sqrt2\angle\frac\pi4$ and $z_2=\sqrt3+\mathrm j=2\angle\frac\pi6$ (James Exercise 19). The product is $2\sqrt2\angle\frac{5\pi}{12}$, that is $2\sqrt2\angle75°$, and multiplying out in cartesian form gives the same point, $(1+\mathrm j)(\sqrt3+\mathrm j)=(\sqrt3-1)+\mathrm j(\sqrt3+1)=0.732+2.732\mathrm j$. The quotient, by the rule derived below, is $\frac1{\sqrt2}\angle\frac\pi{12}=0.683+0.183\mathrm j$.

![[m1054_m05_polar_product.png|900]]

Example 3.12 takes $z_1=-12+5\mathrm j$ and $z_2=-4+3\mathrm j$, both in the second quadrant. Then $|z_1|=\sqrt{144+25}=13$ and $|z_2|=\sqrt{16+9}=5$, so $|z_1z_2|=65$. The arguments are

$$
\arg z_1=\pi-\tan^{-1}\tfrac5{12}=2.7468,\qquad\arg z_2=\pi-\tan^{-1}\tfrac34=2.4981,
$$

whose sum is $5.2449$ rad ($300.51°$). That exceeds $\pi$, so subtract $2\pi$:

$$
\arg(z_1z_2)=5.2449-2\pi=-1.0383\ \text{rad}\ (-59.49°).
$$

> [!check] Example 3.12 in cartesian form
> $(-12+5\mathrm j)(-4+3\mathrm j)=48-36\mathrm j-20\mathrm j+15\mathrm j^2=33-56\mathrm j$. Its modulus is $\sqrt{1089+3136}=\sqrt{4225}=65$, and it lies in the fourth quadrant with $\tan^{-1}\frac{56}{33}=59.49°$ below the real axis, matching $-1.0383$ rad.

### Multiplying by j

Since $\mathrm j=1\angle\frac\pi2$, the product rule gives

$$
\mathrm jz=r\Big[\cos\Big(\theta+\frac\pi2\Big)+\mathrm j\sin\Big(\theta+\frac\pi2\Big)\Big]:
$$

multiplying by $\mathrm j$ keeps the modulus and turns the vector through $90°$ anticlockwise. In cartesian terms $\mathrm j(x+\mathrm jy)=-y+\mathrm jx$, the familiar rotation $(x,y)\mapsto(-y,x)$. For $z=2-3\mathrm j$ (Exercise 10(a)), $\mathrm jz=2\mathrm j-3\mathrm j^2=3+2\mathrm j$. Multiplying by $\mathrm j$ again turns through another $90°$, so $\mathrm j^2z=-z$ is the half-turn, consistent with $\mathrm j^2=-1$. In AC circuit analysis a phase lead of a quarter period is therefore a multiplication by $\mathrm j$.

![[m1054_m05_rotation_square.png|900]]

The left panel shows $z=2-3\mathrm j$ with its successive quarter-turns and its conjugate; $1/z=z^*/13$ points the same way as $z^*$ but has length $1/\sqrt{13}$. The right panel is Example 4.15 ([[#8. Complex numbers as vectors|§8]]).

### Division

First the reciprocal of a unit-modulus number, using the conjugate:

$$
\begin{aligned}
\frac1{\cos\theta+\mathrm j\sin\theta}&=\frac{\cos\theta-\mathrm j\sin\theta}{(\cos\theta+\mathrm j\sin\theta)(\cos\theta-\mathrm j\sin\theta)}\\
&=\frac{\cos\theta-\mathrm j\sin\theta}{\cos^2\theta+\sin^2\theta}\\
&=\cos\theta-\mathrm j\sin\theta=\cos(-\theta)+\mathrm j\sin(-\theta).
\end{aligned}
$$

So $1/z_2=\frac1{r_2}\angle(-\theta_2)$, and multiplying by $z_1$ with the product rule gives

$$
\frac{z_1}{z_2}=\frac{r_1}{r_2}\big[\cos(\theta_1-\theta_2)+\mathrm j\sin(\theta_1-\theta_2)\big],\qquad\left|\frac{z_1}{z_2}\right|=\frac{|z_1|}{|z_2|},\qquad\arg\frac{z_1}{z_2}=\arg z_1-\arg z_2 .
$$

In Example 3.13(a), $z_1=4\angle\frac\pi2$ and $z_2=9\angle\frac\pi3$. Then

$$
\begin{aligned}
\frac{z_1}{z_2}&=\frac49\Big(\cos\frac\pi6+\mathrm j\sin\frac\pi6\Big)=\frac{2\sqrt3}9+\frac29\mathrm j\approx0.385+0.222\mathrm j,\\
\frac{z_2}{z_1}&=\frac94\Big(\cos\frac\pi6-\mathrm j\sin\frac\pi6\Big)=\frac{9\sqrt3}8-\frac98\mathrm j\approx1.949-1.125\mathrm j .
\end{aligned}
$$

In Example 3.13(b), $z_1=1\angle\frac{3\pi}4$ and $z_2=2\angle\frac\pi8$, so $\frac{3\pi}4-\frac\pi8=\frac{5\pi}8$ and

$$
\frac{z_1}{z_2}=\frac12\Big(\cos\frac{5\pi}8+\mathrm j\sin\frac{5\pi}8\Big)\approx-0.191+0.462\mathrm j,\qquad\frac{z_2}{z_1}=2\Big(\cos\frac{5\pi}8-\mathrm j\sin\frac{5\pi}8\Big)\approx-0.765-1.848\mathrm j .
$$

### Powers and long products

Setting $z_1=z_2=z$ in the product rule gives $|z^2|=|z|^2$ and $\arg(z^2)=2\arg z$. Multiplying by $z$ again and repeating,

$$
|z^n|=|z|^n,\qquad\arg(z^n)=n\arg z ,
$$

with a multiple of $2\pi$ added or subtracted to bring the argument into the principal range. Negative powers follow from the quotient rule, so a long product of powers is handled by finding each factor's modulus and argument once and then combining them with the indices. This is the general case of De Moivre's theorem ([[MATH1054 M22 - Complex Numbers II|M22]]).

Example 3.14 asks for the modulus and argument of

$$
z=\frac{(1+2\mathrm j)^2(4-3\mathrm j)^3}{(3+4\mathrm j)^4(2-\mathrm j)^3}.
$$

The moduli are $|1+2\mathrm j|=\sqrt5$, $|4-3\mathrm j|=5$, $|3+4\mathrm j|=5$ and $|2-\mathrm j|=\sqrt5$, so

$$
\begin{aligned}
|z|&=\frac{(\sqrt5)^2\cdot5^3}{5^4\cdot(\sqrt5)^3}\\
&=\frac{5\cdot125}{625\cdot5\sqrt5}\\
&=\frac1{5\sqrt5}=\frac{\sqrt5}{25}\approx0.0894 .
\end{aligned}
$$

The arguments are $\arg(1+2\mathrm j)=1.1071$, $\arg(4-3\mathrm j)=-0.6435$, $\arg(3+4\mathrm j)=0.9273$ and $\arg(2-\mathrm j)=-0.4636$, so

$$
\begin{aligned}
\arg z&=2\arg(1+2\mathrm j)+3\arg(4-3\mathrm j)-4\arg(3+4\mathrm j)-3\arg(2-\mathrm j)\\
&=2(1.1071)+3(-0.6435)-4(0.9273)-3(-0.4636)\\
&=-2.0344\ \text{rad}\ (-116.57°),
\end{aligned}
$$

which already lies in $(-\pi,\pi]$. Converting back, $z=\frac{\sqrt5}{25}\angle(-2.0344)=-\frac1{25}-\frac2{25}\mathrm j$, the same value as expanding every bracket directly. Specimen Test 5, Q4 uses only the modulus rule: $|2+\mathrm j|=|-1-2\mathrm j|=\sqrt5$, so $\left|\dfrac{(2+\mathrm j)^{11}}{(-1-2\mathrm j)^9}\right|=\dfrac{(\sqrt5)^{11}}{(\sqrt5)^9}=5$.

## 7. Euler's formula and exponential form

**Euler's formula** is

$$
e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta\qquad(\theta\ \text{real, in radians}).
$$

For real $\theta$ the right-hand side has modulus $\sqrt{\cos^2\theta+\sin^2\theta}=1$ and argument $\theta$, so $e^{\mathrm j\theta}$ is the point on the unit circle at angle $\theta$. Particular values: $e^{\mathrm j\pi/2}=\mathrm j$, $e^{\mathrm j\pi}=-1$ and $e^{2k\pi\mathrm j}=1$ for every integer $k$, which is the exponential statement that adding $2\pi$ to an argument changes nothing.

### Justifying the formula

The formula is consistent with the law of exponents. If $e^{\mathrm j\theta}$ is to behave as an exponential, it must satisfy $e^{\mathrm j\theta_1}e^{\mathrm j\theta_2}=e^{\mathrm j(\theta_1+\theta_2)}$. Written with Euler's formula, that requirement is

$$
(\cos\theta_1+\mathrm j\sin\theta_1)(\cos\theta_2+\mathrm j\sin\theta_2)=\cos(\theta_1+\theta_2)+\mathrm j\sin(\theta_1+\theta_2),
$$

which is the polar product rule of [[#Multiplication]] with $r_1=r_2=1$. The quotient law $e^{\mathrm j\theta_1}/e^{\mathrm j\theta_2}=e^{\mathrm j(\theta_1-\theta_2)}$ matches the quotient rule in the same way.

Consistency is not a derivation. The formula itself follows from the Maclaurin series ([[Taylor and Maclaurin Series]]), which converge for every argument:

$$
e^{x}=\sum_{n=0}^\infty\frac{x^n}{n!},\qquad\cos\theta=1-\frac{\theta^2}{2!}+\frac{\theta^4}{4!}-\dots,\qquad\sin\theta=\theta-\frac{\theta^3}{3!}+\frac{\theta^5}{5!}-\dots
$$

Put $x=\mathrm j\theta$ in the exponential series, which defines $e^{\mathrm j\theta}$:

$$
\begin{aligned}
e^{\mathrm j\theta}&=1+\mathrm j\theta+\frac{(\mathrm j\theta)^2}{2!}+\frac{(\mathrm j\theta)^3}{3!}+\frac{(\mathrm j\theta)^4}{4!}+\frac{(\mathrm j\theta)^5}{5!}+\dots\\
&=1+\mathrm j\theta-\frac{\theta^2}{2!}-\mathrm j\frac{\theta^3}{3!}+\frac{\theta^4}{4!}+\mathrm j\frac{\theta^5}{5!}-\dots\\
&=\Big(1-\frac{\theta^2}{2!}+\frac{\theta^4}{4!}-\dots\Big)+\mathrm j\Big(\theta-\frac{\theta^3}{3!}+\frac{\theta^5}{5!}-\dots\Big)\\
&=\cos\theta+\mathrm j\sin\theta .
\end{aligned}
$$

The second line uses the period-4 cycle $\mathrm j^2=-1$, $\mathrm j^3=-\mathrm j$, $\mathrm j^4=1$; the third collects the real (even) and imaginary (odd) terms, which is allowed because the series converge absolutely.

> [!check] Six terms at θ = 0.7
> The terms $n=0$ to $5$ of $\sum(0.7\mathrm j)^n/n!$ add to $0.76500+0.64423\mathrm j$, against $\cos0.7=0.76484$ and $\sin0.7=0.64422$. The right panel of the figure below shows the same series at $\theta=\pi$: each term is the previous one turned through $90°$ and scaled by $\theta/n$, and the partial sums spiral in to $e^{\mathrm j\pi}=-1$.

![[m1054_m05_euler_unit_circle.png|900]]

### Exponential form

Euler's formula turns polar form into the **exponential form**

$$
z=r(\cos\theta+\mathrm j\sin\theta)=re^{\mathrm j\theta}=r\angle\theta ,
$$

and with it the polar rules become the laws of exponents:

$$
\begin{aligned}
z_1z_2&=r_1e^{\mathrm j\theta_1}\,r_2e^{\mathrm j\theta_2}=r_1r_2e^{\mathrm j(\theta_1+\theta_2)}=r_1r_2\big[\cos(\theta_1+\theta_2)+\mathrm j\sin(\theta_1+\theta_2)\big],\\
\frac{z_1}{z_2}&=\frac{r_1e^{\mathrm j\theta_1}}{r_2e^{\mathrm j\theta_2}}=\frac{r_1}{r_2}e^{\mathrm j(\theta_1-\theta_2)}=\frac{r_1}{r_2}\big[\cos(\theta_1-\theta_2)+\mathrm j\sin(\theta_1-\theta_2)\big],\\
z^n&=r^ne^{\mathrm jn\theta}.
\end{aligned}
$$

A general complex exponent separates into a modulus and an argument: $e^{x+\mathrm jy}=e^xe^{\mathrm jy}=e^x(\cos y+\mathrm j\sin y)$, a number of modulus $e^x$ and argument $y$.

Example 3.15 converts to exponential form. For $2+3\mathrm j$ (first quadrant), $r=\sqrt{13}$ and $\theta=\tan^{-1}\frac32=0.9828$, so $2+3\mathrm j=\sqrt{13}\,e^{0.9828\mathrm j}$. For $-2+\mathrm j$ (second quadrant), $r=\sqrt5$ and $\theta=\pi-\tan^{-1}\frac12=2.6779$, so $-2+\mathrm j=\sqrt5\,e^{2.6779\mathrm j}$.

Example 3.16 goes the other way:

$$
\begin{aligned}
e^{2+\mathrm j\pi/3}&=e^2e^{\mathrm j\pi/3}\\
&=e^2\Big(\cos\frac\pi3+\mathrm j\sin\frac\pi3\Big)\\
&=\tfrac12e^2+\tfrac{\sqrt3}2e^2\,\mathrm j\\
&=3.6945+6.3991\mathrm j,
\end{aligned}
$$

using $e^2=7.3891$.

Exercises 26 and 27 are pure exponent arithmetic. With $z_1=e^{\mathrm j\pi/4}$ and $z_2=e^{-\mathrm j\pi/3}$,

$$
\arg(z_1z_2^2)=\frac\pi4-\frac{2\pi}3=-\frac{5\pi}{12},\qquad\arg\frac{z_1^3}{z_2}=\frac{3\pi}4+\frac\pi3=\frac{13\pi}{12}\ \to\ \frac{13\pi}{12}-2\pi=-\frac{11\pi}{12},
$$

and $z_1^2+\mathrm jz_2=e^{\mathrm j\pi/2}+e^{\mathrm j\pi/2}e^{-\mathrm j\pi/3}=\mathrm j+e^{\mathrm j\pi/6}=\frac{\sqrt3}2+\frac32\mathrm j$. With $z_1=2e^{\mathrm j\pi/3}$ and $z_2=4e^{-2\mathrm j\pi/3}$:

| | modulus | argument as computed | principal argument | value |
|---|---|---|---|---|
| $z_1^3z_2^2$ | $8\cdot16=128$ | $\pi-\frac{4\pi}3=-\frac\pi3$ | $-\frac\pi3$ | $64-110.85\mathrm j$ |
| $z_1^2z_2^4$ | $4\cdot256=1024$ | $\frac{2\pi}3-\frac{8\pi}3=-2\pi$ | $0$ | $1024$ |
| $z_1^2/z_2^3$ | $4/64=\frac1{16}$ | $\frac{2\pi}3+2\pi=\frac{8\pi}3$ | $\frac{2\pi}3$ | $-\frac1{32}+\frac{\sqrt3}{32}\mathrm j$ |

Specimen Test 5, Q3 combines everything. For $z=-\sqrt3-\mathrm j$, $|z|=\sqrt{3+1}=2$ and the point is in the third quadrant with $\alpha=\tan^{-1}\frac1{\sqrt3}=\frac\pi6$, so $\operatorname{Arg}z=-\frac{5\pi}6$, every value of $\arg z$ is $-\frac{5\pi}6+2k\pi$, and $z=2e^{-5\pi\mathrm j/6}$. Then

$$
\begin{aligned}
z^6&=2^6e^{-5\pi\mathrm j}=64e^{-5\pi\mathrm j+6\pi\mathrm j}=64e^{\pi\mathrm j}\quad(=-64),\\
z^{-2}&=2^{-2}e^{5\pi\mathrm j/3}=\tfrac14e^{5\pi\mathrm j/3-2\pi\mathrm j}=\tfrac14e^{-\pi\mathrm j/3}.
\end{aligned}
$$

For $z^6$ the argument $-5\pi$ can be moved to $\pi$ or to $-\pi$; only $\pi$ is in the principal range.

### Cosine and sine as exponentials

Replacing $\theta$ by $-\theta$ in Euler's formula, and using that cosine is even and sine is odd,

$$
e^{-\mathrm j\theta}=\cos(-\theta)+\mathrm j\sin(-\theta)=\cos\theta-\mathrm j\sin\theta .
$$

Adding this to $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$ cancels the sines, and subtracting it cancels the cosines:

$$
\begin{aligned}
e^{\mathrm j\theta}+e^{-\mathrm j\theta}&=2\cos\theta, &\qquad e^{\mathrm j\theta}-e^{-\mathrm j\theta}&=2\mathrm j\sin\theta,\\
\cos\theta&=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}2, &\qquad\sin\theta&=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j}.
\end{aligned}
$$

This is Specimen Test 5, Q5. Geometrically, $e^{\mathrm j\theta}$ and $e^{-\mathrm j\theta}$ are mirror images in the real axis, so their sum is real and twice the common real part (left panel of the figure above). The formulae have the same shape as $\cosh x=\frac{e^x+e^{-x}}2$ and $\sinh x=\frac{e^x-e^{-x}}2$ ([[Hyperbolic Functions]], [[MATH1054 M07 - Functions|M07]]). Putting $\theta=\mathrm jy$ makes the link explicit:

$$
\cos(\mathrm jy)=\frac{e^{-y}+e^{y}}2=\cosh y,\qquad\sin(\mathrm jy)=\frac{e^{-y}-e^{y}}{2\mathrm j}=\mathrm j\sinh y .
$$

[[MATH1054 M22 - Complex Numbers II|M22]] uses these to define the trigonometric, hyperbolic and logarithmic functions of a complex variable.

## 8. Complex numbers as vectors

The point $P$ representing $z$ can equally be read as the vector $\vec{OP}$, and then complex addition is vector addition. Adding real and imaginary parts separately is adding components, so $z_1+z_2$ is the diagonal of the parallelogram with sides $\vec{Oz_1}$ and $\vec{Oz_2}$. Subtraction is addition of $-z_2$, the reflection of $z_2$ through the origin; equivalently, since $z_2+(z_1-z_2)=z_1$, the difference $z_1-z_2$ is the vector from the point $z_2$ to the point $z_1$, translated to start at $O$. Its length

$$
|z_1-z_2|=\sqrt{(x_1-x_2)^2+(y_1-y_2)^2}
$$

is the distance between the two points, which is why $|z-a|=r$ describes the circle of radius $r$ centred on $a$ ([[Loci in the Complex Plane]], M22). For example $|(3+2\mathrm j)-(5-3\mathrm j)|=|-2+5\mathrm j|=\sqrt{29}$.

![[m1054_specimen5_argand.png|900]]

The figure is Specimen Test 5, Q2 (left) and the Argand diagram for Q3(c) (right).

Because the three points $0$, $z_1$ and $z_1+z_2$ form a triangle with sides $|z_1|$, $|z_2|$ and $|z_1+z_2|$, no side exceeds the sum of the other two. This is the **triangle inequality**

$$
|z_1+z_2|\le|z_1|+|z_2| .
$$

Algebraically, expand with the conjugate:

$$
\begin{aligned}
|z_1+z_2|^2&=(z_1+z_2)(z_1^*+z_2^*)\\
&=|z_1|^2+z_1z_2^*+z_1^*z_2+|z_2|^2\\
&=|z_1|^2+2\operatorname{Re}(z_1z_2^*)+|z_2|^2\\
&\le|z_1|^2+2|z_1||z_2|+|z_2|^2=\big(|z_1|+|z_2|\big)^2,
\end{aligned}
$$

using $z_1^*z_2=(z_1z_2^*)^*$, $w+w^*=2\operatorname{Re}w$ and $\operatorname{Re}w\le|w|$. Equality holds only when $z_1$ and $z_2$ point the same way. With $3+4\mathrm j$ and $-5+12\mathrm j$, $|{-2}+16\mathrm j|=\sqrt{260}=16.12$, less than $5+13=18$.

Rotations combine with the vector picture. Example 4.15 builds a square on $\vec{OP}=(1,2)$ lying in the first and second quadrants. With $p=1+2\mathrm j$, the adjacent side from $O$ is $p$ turned through $+90°$:

$$
\vec{OQ}=\mathrm jp=\mathrm j+2\mathrm j^2=-2+\mathrm j ,
$$

and the fourth vertex is the vector sum

$$
\vec{OR}=\vec{OP}+\vec{OQ}=(1+2\mathrm j)+(-2+\mathrm j)=-1+3\mathrm j .
$$

The vertices are $(0,0)$, $(1,2)$, $(-2,1)$ and $(-1,3)$. Turning the other way, $-\mathrm jp=2-\mathrm j$, would put a vertex in the fourth quadrant, which the question excludes. As a check, $|\vec{OQ}|=\sqrt5=|\vec{OP}|$ and $\vec{OP}\cdot\vec{OQ}=(1)(-2)+(2)(1)=0$.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| $\mathrm j$ | $i$ | Mathematics and physics texts use $i$; engineering uses $\mathrm j$ because $i$ denotes current. MATLAB prints $i$. |
| conjugate $z^*$ | $\bar z$ | James and the booklet use $z^*$; Stroud and many maths texts write $\bar z$. |
| polar form $r(\cos\theta+\mathrm j\sin\theta)$ | $r\angle\theta$, modulus–argument form, exponential form $re^{\mathrm j\theta}$ | The angle notation is the usual engineering shorthand. |
| principal argument, $-\pi<\theta\le\pi$ | $\operatorname{Arg}z$; Stroud's range $0\le\theta<2\pi$ | Use the range $(-\pi,\pi]$ whenever a principal value is asked for. |
| Argand diagram | complex plane, Argand plane | |
| cartesian form $x+\mathrm jy$ | rectangular form, algebraic form | Calculators label the conversion "rectangular to polar". |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M05 Solutions - Complex Numbers I]]
- Previous: [[MATH1054 M04 - Integration I]] · Next in the booklet: [[MATH1054 M06 - Differential Equations I]] (complex roots of the auxiliary equation) · Continuation: [[MATH1054 M22 - Complex Numbers II]] (De Moivre, roots, loci, complex functions)
- Concepts: [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Euler's Formula]] · [[Argand Diagram]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Loci in the Complex Plane]] · [[Hyperbolic Functions]] · [[Taylor and Maclaurin Series]]
- Used in: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] and [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]] ([[Phasor Representation]], [[Complex Impedance]]); [[FEEG1002 D6 - Single Degree of Freedom Vibration]]; [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]] ([[Auxiliary Equation]]); [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]] ([[Complex Fourier Series]]); [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]

## Sources

- MATH1054 Module Booklet, Module 5 work scheme and Specimen Test 5 (PDF pp. 9–12)
- James, *Modern Engineering Mathematics* (6th ed.): §3.1 (pp. 184–185), §3.2.1–3.2.4 (pp. 185–194), §3.2.6–3.2.7 (pp. 195–201), §3.2.9 (p. 202), §4.2.6 and Example 4.15 (pp. 248–249)
- Worked solutions: [[MATH1054 M05 Solutions - Complex Numbers I]]

## Self-study tasks

### Core

- [ ] Exercises 6(a), (b), (d), (f), (g) (Module 05 work scheme): cartesian arithmetic and division by the conjugate. → [[MATH1054 M05 Solutions - Complex Numbers I#Exercise 6: Cartesian form]]
- [ ] Exercises 12 and 17 (Module 05 work scheme): complex simultaneous equations, and real $x$, $y$ by equating parts. → [[MATH1054 M05 Solutions - Complex Numbers I#Exercise 12: Simultaneous equations]]
- [ ] Exercises 24(a), (c), (e), (g), (i) (Module 05 work scheme): polar form with the quadrant rule. → [[MATH1054 M05 Solutions - Complex Numbers I#Exercise 24: Polar form]]
- [ ] Exercises 26 and 27 (Module 05 work scheme): products, quotients and powers in exponential form, reducing to the principal argument. → [[MATH1054 M05 Solutions - Complex Numbers I#Part B: Assigned exercises]]
- [ ] Specimen Test 5, Q1–Q5, timed. → [[MATH1054 M05 Solutions - Complex Numbers I#Part C: Specimen Test 5]]

### Further practice

- [ ] Exercise 1 (Module 05 work scheme): plot the six points and find each modulus and argument. → [[MATH1054 M05 Solutions - Complex Numbers I#Example 3.1 and Exercise 1: Argand diagrams]]
- [ ] Exercises 8(a), (b) and 10(a)–(c) (Module 05 work scheme): complex roots of polynomials, and $\mathrm jz$, $z^*$, $1/z$. → [[MATH1054 M05 Solutions - Complex Numbers I#Exercise 8: Roots of polynomials]]
- [ ] Examples 3.12 and 3.14 (Module 05 work scheme) without notes, checking each in cartesian form. → [[#Powers and long products]] · [[MATH1054 M05 Solutions - Complex Numbers I#Example 3.14: Modulus and argument of a product and quotient]]
- [ ] Example 4.15 (Module 05 work scheme): the square on OP by rotation through j. → [[#8. Complex numbers as vectors]]
- [ ] James Exercise 19, $z_1=1+\mathrm j$, $z_2=\sqrt3+\mathrm j$ (suggested, not in the work scheme). Answer: $z_1z_2=2\sqrt2\angle\frac{5\pi}{12}$, $z_1/z_2=\frac1{\sqrt2}\angle\frac\pi{12}$. → [[#Multiplication]]

## Transcript and slide slips

> [!warning] James text slips
> Where: [[#Roots of polynomials]] and [[#Powers and long products]].
>
> | Where | Printed | Correct |
> |---|---|---|
> | James §3.1, p. 185 | roots of $x^7-7x^5-6x^4+4x^3-28x-24=0$ listed as $-1,-2,-3,-1\pm\mathrm j,1\pm\mathrm j$ | the real roots are $-1$, $-2$ and $+3$; $x=-3$ gives $-1020\neq0$ |
> | James Example 3.14, p. 199 | $\arg(2-\mathrm j)$ substituted as $-0.461$, total $-2.035$ | $\arg(2-\mathrm j)=-\tan^{-1}\frac12=-0.4636$; the total is $-2.0344$ |

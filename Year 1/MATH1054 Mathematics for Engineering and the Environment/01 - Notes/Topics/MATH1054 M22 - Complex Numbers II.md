---
title: "MATH1054 M22 - Complex Numbers II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 2: Complex Numbers"
order: 22
tags:
  - math1054
  - complex-numbers
  - de-moivre
  - loci
aliases: ["MATH1054 Module 22", "Complex Numbers II"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 22 work scheme; James §3.2.9–3.2.10 (circular and hyperbolic functions of a complex variable, the complex logarithm), §3.3.1–3.3.2 (De Moivre's theorem, nth roots and rational powers, complex quadratics, z^n + z^-n = 2cos nθ), §3.4.1–3.4.2 (straight-line and circular loci)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M05 - Complex Numbers I]]", "[[MATH1054 M07 - Functions]]"]
next_topics: ["[[MATH1054 M24 - Statistics I]]"]
key_concepts: ["[[De Moivre's Theorem and Roots of Complex Numbers]]", "[[Complex Functions - Trig, Hyperbolic and Logarithm]]", "[[Loci in the Complex Plane]]"]
tutorial_sheets: ["[[MATH1054 M22 Solutions - Complex Numbers II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 22)", "02 - Sources/Modern Engineering Mathematics.pdf (§3.2.9–3.2.10, §3.3.1–3.3.2, §3.4.1–3.4.2)"]
---

# MATH1054 M22 - Complex Numbers II

> [!abstract] Summary
> Euler's formula extends the elementary functions to a complex argument: $\cos\mathrm jy=\cosh y$ and $\sin\mathrm jy=\mathrm j\sinh y$, so $\sin z$ and $\cos z$ are unbounded and equations such as $\cos z=2$ have infinitely many solutions, while $\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi)$ takes infinitely many values. De Moivre's theorem $(re^{\mathrm j\theta})^n=r^ne^{\mathrm jn\theta}$ gives powers directly, and with the $2k\pi$ ambiguity in the argument it gives exactly $n$ distinct $n$th roots, equally spaced on a circle of radius $r^{1/n}$. Conditions on $z$ such as $|z-a|=k|z-b|$ describe curves in the Argand diagram, found by substituting $z=x+\mathrm jy$: lines, circles and circles of Apollonius.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for $\sin$, $\cos$, $\sinh$, $\ln$ of a complex number, solves $\cos z=c$ or $z^n=w$, asks for all values of a root or rational power, solves a quadratic with complex coefficients, or asks for the locus of $z$.
> - **Assumptions:** angles in radians; $\operatorname{Arg}z$ is the principal argument, $-\pi<\operatorname{Arg}z\le\pi$; $k$ is any integer; a rational power $p/q$ is in lowest terms.
> - **Method:** 1. Write $z=x+\mathrm jy$ for functions and loci, or $z=re^{\mathrm j\theta}$ for powers, roots and logs. 2. Functions: expand with the addition formula and $\cos\mathrm jy=\cosh y$, $\sin\mathrm jy=\mathrm j\sinh y$. 3. Roots and logs: add $2k\pi$ to $\theta$ before dividing or taking the log; take $k=0,\dots,n-1$. 4. Equations $f(z)=c$: equate real and imaginary parts and solve the simpler equation first. 5. Loci: square any moduli, multiply a quotient by the conjugate of its denominator, complete the square, and remove points where a denominator vanishes.
> - **Common mistakes:** forgetting the $+2k\pi$ (one root instead of $n$, one log instead of infinitely many); keeping the excluded point $z=b$ on the locus of $\operatorname{Re}\frac{z-a}{z-b}=c$.
> - **Practise:** [[#Solving cos z = 2 and sin z = 2]] · [[MATH1054 M22 Solutions - Complex Numbers II#Exercise 45: Identify and sketch the loci|Exercise 45]]

Complex numbers have an arithmetic of their own as points in a plane ([[MATH1054 M05 - Complex Numbers I]]), and they can also be the arguments of functions. Euler's formula $e^{\mathrm j\theta}=\cos\theta+\mathrm j\sin\theta$ already ties the exponential to the circular functions, and once $\cos$ and $\sin$ are written as combinations of exponentials they make sense for any complex argument. The same formulas show that the circular and hyperbolic functions are one family: a cosine of an imaginary number is a hyperbolic cosine. The bound $|\cos x|\le1$ belongs only to real $x$, and $\cos z=2$ has solutions a short distance off the real axis.

Inverting the exponential gives the logarithm, and here the periodicity $e^{w+2\pi\mathrm j}=e^w$ matters: every nonzero complex number has infinitely many logarithms, spaced $2\pi\mathrm j$ apart, and one of them is chosen as the principal value. The same $2\pi$ ambiguity in the argument is what produces $n$ different $n$th roots. De Moivre's theorem turns a power into multiplication of the argument, so roots are found by dividing the argument, and the $n$ roots end up equally spaced on a circle.

For an engineer these are working tools. AC circuit analysis writes voltages and currents as phasors $Ve^{\mathrm j\omega t}$ and multiplies them by complex impedances ([[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]). The roots of a characteristic polynomial and the poles of a transfer function are points in the Argand diagram, and loci describe sets of them: the closed-loop condition $|G|=M\,|1+G|$ is a circle of Apollonius with foci $0$ and $-1$ in the $G$-plane. In aerodynamics the complex logarithm is the complex potential of a source or a point vortex, and the $2\pi$ jump in its imaginary part around the origin carries the circulation of the vortex and the volume flow of the source ([[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]).

---

## 1. Circular and hyperbolic functions of a complex variable (James §3.2.9)

### Cosine and sine from Euler's formula

Euler's formula and its version with $\theta$ replaced by $-\theta$ are

$$
\begin{aligned}
e^{\mathrm j\theta}&=\cos\theta+\mathrm j\sin\theta,\\
e^{-\mathrm j\theta}&=\cos\theta-\mathrm j\sin\theta,
\end{aligned}
$$

using $\cos(-\theta)=\cos\theta$ and $\sin(-\theta)=-\sin\theta$ ([[Euler's Formula]]). Adding the two lines and dividing by 2:

$$
\cos\theta=\frac{e^{\mathrm j\theta}+e^{-\mathrm j\theta}}{2}. \tag{3.11a}
$$

Subtracting the second from the first and dividing by $2\mathrm j$:

$$
\sin\theta=\frac{e^{\mathrm j\theta}-e^{-\mathrm j\theta}}{2\mathrm j}. \tag{3.11b}
$$

For real $\theta$ these are identities. For complex $\theta$ the right-hand sides are defined (the exponential of any complex number is defined), so they are taken as the definitions of $\cos$ and $\sin$ of a complex number. The hyperbolic functions are defined the same way from real exponentials ([[Hyperbolic Functions]]):

$$
\cosh x=\frac{e^{x}+e^{-x}}{2},\qquad\sinh x=\frac{e^{x}-e^{-x}}{2}. \tag{3.12}
$$

### Trigonometric functions of imaginary arguments

Put $\theta=\mathrm jx$ in (3.11a), with $x$ real. Since $\mathrm j\cdot\mathrm jx=-x$,

$$
\begin{aligned}
\cos\mathrm jx&=\frac{e^{\mathrm j^2x}+e^{-\mathrm j^2x}}{2}\\
&=\frac{e^{-x}+e^{x}}{2}\\
&=\cosh x.
\end{aligned} \tag{3.14a}
$$

Put $\theta=\mathrm jx$ in (3.11b):

$$
\begin{aligned}
\sin\mathrm jx&=\frac{e^{-x}-e^{x}}{2\mathrm j}\\
&=-\frac{1}{\mathrm j}\cdot\frac{e^{x}-e^{-x}}{2}\\
&=\mathrm j\sinh x,
\end{aligned} \tag{3.14b}
$$

because $-1/\mathrm j=\mathrm j$. In the other direction, put $x=\mathrm j\theta$ into the definition of $\cosh$ and $\sinh$, which for complex arguments are defined by the same exponential formulas:

$$
\cosh\mathrm jx=\frac{e^{\mathrm jx}+e^{-\mathrm jx}}{2}=\cos x,\qquad\sinh\mathrm jx=\frac{e^{\mathrm jx}-e^{-\mathrm jx}}{2}=\mathrm j\,\frac{e^{\mathrm jx}-e^{-\mathrm jx}}{2\mathrm j}=\mathrm j\sin x. \tag{3.13a, b}
$$

Dividing gives the tangent pair:

$$
\tan\mathrm jx=\frac{\mathrm j\sinh x}{\cosh x}=\mathrm j\tanh x,\qquad\tanh\mathrm jx=\frac{\mathrm j\sin x}{\cos x}=\mathrm j\tan x. \tag{3.14c, 3.13c}
$$

None of these needs memorising, but deriving them is examinable (Module 22 work scheme, item 1): each follows in two lines from Euler's formula and the definitions of $\cosh$ and $\sinh$ on the formula sheet. They also explain Osborn's rule for turning a trigonometric identity into a hyperbolic one ([[MATH1054 M07 - Functions]]): replacing $\sin$ by $\sinh$ brings in a factor $\mathrm j$, so a product of two sines brings in $\mathrm j^2=-1$ and its sign flips.

### Real and imaginary parts of sin z, cos z, sinh z and cosh z

Let $z=x+\mathrm jy$ with $x,y$ real. The addition formula $\sin(A+B)=\sin A\cos B+\cos A\sin B$ holds for complex $A,B$, because it follows from (3.11) and $e^{A+B}=e^Ae^B$. So

$$
\begin{aligned}
\sin z&=\sin x\cos\mathrm jy+\cos x\sin\mathrm jy\\
&=\sin x\cosh y+\mathrm j\cos x\sinh y.
\end{aligned}
$$

In the same way, from $\cos(A+B)=\cos A\cos B-\sin A\sin B$,

$$
\begin{aligned}
\cos z&=\cos x\cos\mathrm jy-\sin x\sin\mathrm jy\\
&=\cos x\cosh y-\mathrm j\sin x\sinh y.
\end{aligned}
$$

For the hyperbolic functions use $\sinh(A+B)=\sinh A\cosh B+\cosh A\sinh B$ and $\cosh(A+B)=\cosh A\cosh B+\sinh A\sinh B$ with (3.13):

$$
\begin{aligned}
\sinh z&=\sinh x\cosh\mathrm jy+\cosh x\sinh\mathrm jy=\sinh x\cos y+\mathrm j\cosh x\sin y,\\
\cosh z&=\cosh x\cosh\mathrm jy+\sinh x\sinh\mathrm jy=\cosh x\cos y+\mathrm j\sinh x\sin y.
\end{aligned}
$$

The modulus of $\sin z$ shows why $\sin z$ is not bounded. Square and add the real and imaginary parts, then use $\cosh^2y=1+\sinh^2y$:

$$
\begin{aligned}
|\sin z|^2&=\sin^2x\cosh^2y+\cos^2x\sinh^2y\\
&=\sin^2x\,(1+\sinh^2y)+\cos^2x\sinh^2y\\
&=\sin^2x+\sinh^2y.
\end{aligned}
$$

Likewise $|\cos z|^2=\cos^2x+\sinh^2y$. Both grow like $\tfrac14e^{2|y|}$ as $|y|$ grows, so $\sin z$ and $\cos z$ take every complex value somewhere in each vertical strip of width $2\pi$. The bound $-1\le\cos x\le1$ is a property of real $x$ only.

### Tangent of a complex number

$\tan z=\sin z/\cos z$. To split it into real and imaginary parts, multiply the top and bottom by $\cos(x-\mathrm jy)$, the conjugate of $\cos z$, and use the product-to-sum identities $2\sin A\cos B=\sin(A+B)+\sin(A-B)$ and $2\cos A\cos B=\cos(A+B)+\cos(A-B)$ with $A=x+\mathrm jy$, $B=x-\mathrm jy$, so $A+B=2x$ and $A-B=2\mathrm jy$:

$$
\begin{aligned}
\tan(x+\mathrm jy)&=\frac{\sin(x+\mathrm jy)\cos(x-\mathrm jy)}{\cos(x+\mathrm jy)\cos(x-\mathrm jy)}\\
&=\frac{\tfrac12\big[\sin2x+\sin2\mathrm jy\big]}{\tfrac12\big[\cos2x+\cos2\mathrm jy\big]}\\
&=\frac{\sin2x+\mathrm j\sinh2y}{\cos2x+\cosh2y}.
\end{aligned}
$$

The denominator is real and positive except where $\cos2x=-1$ and $y=0$, which are the real poles $x=\frac\pi2+n\pi$ of $\tan$.

### Evaluating the functions (Example 3.17 and Exercise 29)

Example 3.17(a), $\sin\big[\tfrac\pi4(1+\mathrm j)\big]$, has $x=y=\frac\pi4$, with $\sin\frac\pi4=\cos\frac\pi4=0.7071$, $\cosh\frac\pi4=1.3246$ and $\sinh\frac\pi4=0.8687$:

$$
\begin{aligned}
\sin\big(\tfrac\pi4+\mathrm j\tfrac\pi4\big)&=\sin\tfrac\pi4\cosh\tfrac\pi4+\mathrm j\cos\tfrac\pi4\sinh\tfrac\pi4\\
&=(0.7071)(1.3246)+\mathrm j(0.7071)(0.8687)\\
&=0.9366+0.6142\mathrm j.
\end{aligned}
$$

Example 3.17(b), $\sinh(3+4\mathrm j)$, uses the $\sinh z$ formula with $x=3$, $y=4$ (radians), $\sinh3=10.0179$, $\cosh3=10.0677$, $\cos4=-0.6536$, $\sin4=-0.7568$:

$$
\begin{aligned}
\sinh(3+4\mathrm j)&=\sinh3\cos4+\mathrm j\cosh3\sin4\\
&=(10.0179)(-0.6536)+\mathrm j(10.0677)(-0.7568)\\
&=-6.548-7.619\mathrm j.
\end{aligned}
$$

The same answer comes from $\sinh w=-\mathrm j\sin\mathrm jw$, which turns it into a sine of $\mathrm j(3+4\mathrm j)=-4+3\mathrm j$ and uses the circular addition formula instead.

Example 3.17(c), $\tan\big(\tfrac\pi4-3\mathrm j\big)$, has $x=\frac\pi4$, $y=-3$, so $\sin2x=1$, $\cos2x=0$, $\sinh2y=-\sinh6=-201.7132$ and $\cosh2y=\cosh6=201.7156$:

$$
\begin{aligned}
\tan\big(\tfrac\pi4-3\mathrm j\big)&=\frac{1-\mathrm j\sinh6}{0+\cosh6}\\
&=\frac{1}{\cosh6}-\mathrm j\tanh6\\
&=0.00496-0.99999\mathrm j.
\end{aligned}
$$

> [!check] Example 3.17(c) by the subtraction formula
> With $\tan\frac\pi4=1$ and $\tan(-3\mathrm j)=-\mathrm j\tanh3$, $\tan(A-B)=\dfrac{\tan A-\tan B}{1+\tan A\tan B}$ gives $\dfrac{1-\mathrm jt}{1+\mathrm jt}=\dfrac{(1-\mathrm jt)^2}{1+t^2}=\dfrac{1-t^2}{1+t^2}-\mathrm j\dfrac{2t}{1+t^2}$ with $t=\tanh3=0.99505$. That is $0.00496-0.99999\mathrm j$ again, and Python's `cmath.tan` returns $0.004957-0.999988\mathrm j$.

Exercise 29(a), with $\sin\frac{5\pi}6=\frac12$, $\cos\frac{5\pi}6=-\frac{\sqrt3}2$, $\cosh1=1.5431$ and $\sinh1=1.1752$:

$$
\begin{aligned}
\sin\big(\tfrac{5\pi}6+\mathrm j\big)&=\sin\tfrac{5\pi}6\cosh1+\mathrm j\cos\tfrac{5\pi}6\sinh1\\
&=\tfrac12(1.5431)-\mathrm j\tfrac{\sqrt3}2(1.1752)\\
&=0.7715-1.0178\mathrm j.
\end{aligned}
$$

Exercise 29(b) is a direct use of (3.14a): $\cos\big(\mathrm j\tfrac34\big)=\cosh\tfrac34=1.2947$, a real number. Specimen Test 22, Q1 asks for $\sin\big(\frac\pi2+\mathrm j\big)$:

$$
\begin{aligned}
\sin\big(\tfrac\pi2+\mathrm j\big)&=\sin\tfrac\pi2\cos\mathrm j+\cos\tfrac\pi2\sin\mathrm j\\
&=1\cdot\cosh1+0\cdot\mathrm j\sinh1\\
&=\cosh1=1.5431,
\end{aligned}
$$

so the real part is $\cosh1\approx1.5431$ and the imaginary part is 0.

### Solving cos z = 2 and sin z = 2

![[m1054_m22_cos_equals_2.png|900]]

To solve $\cos z=2$ (Example 3.17(d)), write $z=x+\mathrm jy$ and use the expansion of $\cos z$:

$$
\cos x\cosh y-\mathrm j\sin x\sinh y=2+0\mathrm j.
$$

Equating real and imaginary parts gives two real equations:

$$
\cos x\cosh y=2,\qquad\sin x\sinh y=0.
$$

The second is the simpler one. It holds if $y=0$ or $\sin x=0$. If $y=0$ the first equation reads $\cos x=2$, which has no real solution, so $\sin x=0$ and $x=n\pi$. Then $\cos x=(-1)^n$ and the first equation reads

$$
(-1)^n\cosh y=2.
$$

Since $\cosh y\ge1>0$, $n$ must be even, $n=2k$, and $\cosh y=2$. To invert, multiply $e^y+e^{-y}=4$ by $e^y$:

$$
\begin{aligned}
e^{2y}-4e^y+1&=0\\
e^y&=2\pm\sqrt3\\
y&=\ln(2\pm\sqrt3)=\pm\ln(2+\sqrt3),
\end{aligned}
$$

because $(2-\sqrt3)(2+\sqrt3)=1$, so $\ln(2-\sqrt3)=-\ln(2+\sqrt3)$. Therefore

$$
z=2k\pi\pm\mathrm j\cosh^{-1}2=2k\pi\pm\mathrm j\ln(2+\sqrt3)=2k\pi\pm1.3170\mathrm j,\qquad k\in\mathbb Z.
$$

Exercise 30(a), $\sin z=2$, runs the same way. The parts of $\sin x\cosh y+\mathrm j\cos x\sinh y=2$ give $\cos x\sinh y=0$ and $\sin x\cosh y=2$. Again $y=0$ would need $\sin x=2$, so $\cos x=0$ and $x=\frac\pi2+n\pi$, where $\sin x=(-1)^n$. Positivity of $\cosh y$ forces $\sin x=+1$, so $x=\frac\pi2+2k\pi$ and $\cosh y=2$:

$$
z=\tfrac\pi2+2k\pi\pm\mathrm j\ln(2+\sqrt3)=\tfrac\pi2+2k\pi\pm1.317\mathrm j,\qquad k\in\mathbb Z.
$$

This is the cosine answer shifted by $\frac\pi2$, as $\sin z=\cos\big(z-\frac\pi2\big)$ requires. Substituting $z=1.3170\mathrm j$ and $z=\frac\pi2+1.3170\mathrm j$ back into `cmath.cos` and `cmath.sin` returns $2.0000$ to machine precision.

## 2. The logarithm of a complex number (James §3.2.10)

### All values of the logarithm

A logarithm of $z\ne0$ is any $w$ with $e^w=z$. Write $z=x+\mathrm jy$ and $w=u+\mathrm jv$. Then

$$
\begin{aligned}
x+\mathrm jy&=e^{u+\mathrm jv}\\
&=e^u e^{\mathrm jv}\\
&=e^u(\cos v+\mathrm j\sin v).
\end{aligned}
$$

Equating real and imaginary parts:

$$
x=e^u\cos v,\qquad y=e^u\sin v.
$$

Squaring and adding removes $v$:

$$
\begin{aligned}
x^2+y^2&=e^{2u}(\cos^2v+\sin^2v)=e^{2u}\\
u&=\tfrac12\ln(x^2+y^2)=\ln|z|.
\end{aligned}
$$

The two equations then say that $\cos v=x/|z|$ and $\sin v=y/|z|$, which is the definition of an argument of $z$. Arguments are fixed only up to whole turns, so $v=\operatorname{Arg}z+2k\pi$ for any integer $k$, and

$$
\boxed{\ln z=\ln|z|+\mathrm j(\operatorname{Arg}z+2k\pi),\qquad k=0,\pm1,\pm2,\dots}
$$

The same result comes in one line from the exponential form $z=re^{\mathrm j(\theta+2k\pi)}$, with $\theta=\operatorname{Arg}z$: taking logs term by term gives $\ln z=\ln r+\mathrm j(\theta+2k\pi)$, which is the quickest route in practice. The logarithm of a complex number is multi-valued, with infinitely many values on a vertical line $u=\ln|z|$ spaced $2\pi$ apart. The value with $k=0$ and $-\pi<\operatorname{Arg}z\le\pi$ is the **principal value**, written $\operatorname{Ln}z$:

$$
\operatorname{Ln}z=\ln|z|+\mathrm j\operatorname{Arg}z. \tag{3.15}
$$

$\operatorname{Ln}$ jumps by $2\pi\mathrm j$ across the negative real axis, where $\operatorname{Arg}$ jumps from $\pi$ to $-\pi$. Zero has no logarithm, because $e^w$ is never zero.

![[m1054_m22_log_branches.png|900]]

> [!warning] The log laws fail for principal values
> $\ln(z_1z_2)=\ln z_1+\ln z_2$ holds as an equality between sets of values, but not between principal values. For $z_1=z_2=-1+\mathrm j$, $\operatorname{Ln}\big((-1+\mathrm j)^2\big)=\operatorname{Ln}(-2\mathrm j)=\ln2-\mathrm j\frac\pi2=0.6931-1.5708\mathrm j$, while $2\operatorname{Ln}(-1+\mathrm j)=\ln2+\mathrm j\frac{3\pi}2=0.6931+4.7124\mathrm j$. The two differ by $2\pi\mathrm j$, one step between branches.

### Logarithm examples (Example 3.18, Exercise A, Specimen Q2)

For $z=-3+4\mathrm j$ (Example 3.18), $|z|=\sqrt{9+16}=5$ and $z$ is in the second quadrant, so

$$
\operatorname{Arg}z=\pi-\tan^{-1}\tfrac43=2.2143.
$$

All values and the principal value are

$$
\ln(-3+4\mathrm j)=\ln5+\mathrm j(2.2143+2k\pi)=1.6094+\mathrm j(2.2143+2k\pi),\qquad\operatorname{Ln}(-3+4\mathrm j)=1.6094+2.2143\mathrm j.
$$

Exercise A(a): $|5+12\mathrm j|=\sqrt{25+144}=13$ and $\operatorname{Arg}(5+12\mathrm j)=\tan^{-1}\frac{12}5=1.1760$ (first quadrant), so

$$
\ln(5+12\mathrm j)=\ln13+\mathrm j(1.1760+2k\pi)=2.5649+\mathrm j(1.1760+2k\pi),\qquad k\in\mathbb Z.
$$

Exercise A(b): $-\frac12-\frac{\sqrt3}2\mathrm j$ has modulus $\sqrt{\frac14+\frac34}=1$ and lies in the third quadrant at $\operatorname{Arg}=-\pi+\frac\pi3=-\frac{2\pi}3$. Since $\ln1=0$, every value is purely imaginary:

$$
\ln\big(-\tfrac12-\tfrac{\sqrt3}2\mathrm j\big)=\mathrm j\Big(2k\pi-\frac{2\pi}3\Big),\qquad\operatorname{Ln}=-\frac{2\pi}{3}\mathrm j=-2.0944\mathrm j.
$$

Specimen Test 22, Q2 asks for $\ln(-3)$. In exponential form $-3=3e^{\mathrm j\pi}$, so

$$
\ln(-3)=\ln3+\mathrm j(\pi+2k\pi),
$$

and the principal value has real part $\ln3\approx1.0986$ and imaginary part $\pi$. In the same way $\operatorname{Ln}(-1)=\mathrm j\pi$ and $\operatorname{Ln}\mathrm j=\mathrm j\frac\pi2$: negative numbers have logarithms once complex values are allowed.

### Solving tanh z = 2

Example 3.17(e) asks for $z$ with $\tanh z=2$, which has no real solution because $|\tanh x|<1$. Write $\tanh$ in exponentials and multiply the top and bottom by $e^z$:

$$
\tanh z=\frac{e^z-e^{-z}}{e^z+e^{-z}}=\frac{e^{2z}-1}{e^{2z}+1}=2.
$$

Clear the fraction and collect $e^{2z}$:

$$
\begin{aligned}
e^{2z}-1&=2e^{2z}+2\\
e^{2z}&=-3\\
2z&=\ln(-3)=\ln3+\mathrm j(\pi+2k\pi)\\
z&=\tfrac12\ln3+\mathrm j\big(\tfrac\pi2+k\pi\big)=0.5493+\mathrm j\big(\tfrac\pi2+k\pi\big),\qquad k\in\mathbb Z.
\end{aligned}
$$

Equivalently $z=\tanh^{-1}2=\frac12\ln\frac{1+2}{1-2}=\frac12\ln(-3)$, the real formula for $\tanh^{-1}$ used with the complex logarithm. The alternative route equates real and imaginary parts of $\sinh z=2\cosh z$, which forces $\cos y=0$ and then $\tanh x=\frac12$, so $x=\tanh^{-1}\frac12=\frac12\ln3$: the same set.

> [!check] Substituting back
> $\tanh\big(x+\mathrm j\frac\pi2\big)=\dfrac{\sinh x\cos\frac\pi2+\mathrm j\cosh x\sin\frac\pi2}{\cosh x\cos\frac\pi2+\mathrm j\sinh x\sin\frac\pi2}=\dfrac{\mathrm j\cosh x}{\mathrm j\sinh x}=\coth x$, and $\tanh\big(\frac12\ln3\big)=\frac{3-1}{3+1}=\frac12$, so $\coth\big(\frac12\ln3\big)=2$. `cmath.tanh(0.5493+1.5708j)` returns $2.0000$.

## 3. De Moivre's theorem (James §3.3.1)

### Proof from the exponential form

Write $z=re^{\mathrm j\theta}=r(\cos\theta+\mathrm j\sin\theta)$ ([[Complex Numbers - Cartesian, Polar and Exponential Forms]]). The index laws hold for the exponential of a complex number, so for any integer $n$

$$
\begin{aligned}
z^n&=r^n\big(e^{\mathrm j\theta}\big)^n\\
&=r^ne^{\mathrm jn\theta}\\
&=r^n(\cos n\theta+\mathrm j\sin n\theta).
\end{aligned}
$$

This is **De Moivre's theorem**, usually stated as

$$
\big\{r(\cos\theta+\mathrm j\sin\theta)\big\}^n=r^n(\cos n\theta+\mathrm j\sin n\theta). \tag{3.16}
$$

A power raises the modulus to the power $n$ and multiplies the argument by $n$. Replacing $\theta$ by $-\theta$ and using the parity of $\cos$ and $\sin$ gives the version with minus signs on both sides:

$$
(\cos\theta-\mathrm j\sin\theta)^n=\cos n\theta-\mathrm j\sin n\theta.
$$

### Proof by induction for integer powers

The theorem can also be proved for positive integers $n$ without the exponential. It holds for $n=1$. Suppose it holds for $n$. Then

$$
\begin{aligned}
(\cos\theta+\mathrm j\sin\theta)^{n+1}&=(\cos n\theta+\mathrm j\sin n\theta)(\cos\theta+\mathrm j\sin\theta)\\
&=(\cos n\theta\cos\theta-\sin n\theta\sin\theta)+\mathrm j(\sin n\theta\cos\theta+\cos n\theta\sin\theta)\\
&=\cos(n+1)\theta+\mathrm j\sin(n+1)\theta,
\end{aligned}
$$

by the addition formulae, so it holds for $n+1$ and hence for every positive integer. For a negative integer $n=-m$, multiply by the conjugate:

$$
(\cos\theta+\mathrm j\sin\theta)^{-m}=\frac{1}{\cos m\theta+\mathrm j\sin m\theta}=\frac{\cos m\theta-\mathrm j\sin m\theta}{\cos^2m\theta+\sin^2m\theta}=\cos(-m\theta)+\mathrm j\sin(-m\theta).
$$

For non-integer powers the left-hand side has several values ([[#4. The nth roots of a complex number (James §3.3.1)|section 4]]).

### Powers by De Moivre (Example 3.19)

$1-\mathrm j$ has modulus $\sqrt2$ and argument $-\frac\pi4$:

$$
1-\mathrm j=\sqrt2\big[\cos\big(-\tfrac\pi4\big)+\mathrm j\sin\big(-\tfrac\pi4\big)\big]=\sqrt2\big(\cos\tfrac\pi4-\mathrm j\sin\tfrac\pi4\big).
$$

By the minus-sign form of the theorem,

$$
\begin{aligned}
(1-\mathrm j)^{12}&=(\sqrt2)^{12}\big(\cos\tfrac{12\pi}4-\mathrm j\sin\tfrac{12\pi}4\big)\\
&=2^6(\cos3\pi-\mathrm j\sin3\pi)\\
&=64(-1-0\mathrm j)=-64.
\end{aligned}
$$

Repeated squaring gives the same answer without polar form: $(1-\mathrm j)^2=1-2\mathrm j+\mathrm j^2=-2\mathrm j$, so $(1-\mathrm j)^{12}=(-2\mathrm j)^6=(-2)^6(\mathrm j^2)^3=64(-1)^3=-64$.

## 4. The nth roots of a complex number (James §3.3.1)

### Deriving the root formula

Let $z=r(\cos\theta+\mathrm j\sin\theta)$ with $r>0$, and look for every $w=R(\cos\phi+\mathrm j\sin\phi)$ with $w^n=z$, where $n$ is a positive integer. By De Moivre,

$$
R^n(\cos n\phi+\mathrm j\sin n\phi)=r(\cos\theta+\mathrm j\sin\theta).
$$

Equating real and imaginary parts:

$$
R^n\cos n\phi=r\cos\theta,\qquad R^n\sin n\phi=r\sin\theta.
$$

Squaring and adding gives $R^{2n}=r^2$, so $R=r^{1/n}$, the positive real root. Substituting back leaves

$$
\cos n\phi=\cos\theta,\qquad\sin n\phi=\sin\theta,
$$

which hold together exactly when $n\phi$ and $\theta$ differ by a whole number of turns:

$$
\begin{aligned}
n\phi&=\theta+2k\pi,\qquad k\in\mathbb Z\\
\phi&=\frac{\theta+2k\pi}{n}.
\end{aligned}
$$

So

$$
z^{1/n}=r^{1/n}\Big[\cos\frac{\theta+2k\pi}{n}+\mathrm j\sin\frac{\theta+2k\pi}{n}\Big]=r^{1/n}e^{\mathrm j(\theta+2k\pi)/n},\qquad k=0,1,\dots,n-1. \tag{3.17, 3.18}
$$

The integer $k$ can take any value, but $k$ and $k+n$ give arguments that differ by exactly $2\pi$, the same complex number. So $k=0,\dots,n-1$ lists every root once, and there are exactly $n$ distinct $n$th roots. They all have modulus $r^{1/n}$, and their arguments increase in steps of $\frac{2\pi}n$, so they lie at the vertices of a regular $n$-gon inscribed in the circle $|w|=r^{1/n}$.

> [!tip] Roots of unity
> With $\omega=e^{2\pi\mathrm j/n}$, the $n$th roots of 1 are $\omega^k=e^{2\pi\mathrm jk/n}$, $k=0,\dots,n-1$. If $w_0$ is any one $n$th root of $z$, the full set is $w_0,\ w_0\omega,\ \dots,\ w_0\omega^{n-1}$: one root, rotated by $\frac{2\pi}n$ each time. For $n\ge2$ the roots sum to zero, since $1+\omega+\dots+\omega^{n-1}=\frac{1-\omega^n}{1-\omega}=0$, which is a quick check on any set of computed roots.

In practice: find $r$ and the principal argument $\theta$, add $2k\pi$ to $\theta$ before dividing by $n$, and finally reduce each argument into $(-\pi,\pi]$ if the answer is wanted in principal form.

### Roots of minus a half plus a half j (Example 3.20)

$z=-\frac12+\frac12\mathrm j$ has $r=\sqrt{\frac14+\frac14}=2^{-1/2}$ and lies in the second quadrant at $\theta=\pi-\tan^{-1}1=\frac{3\pi}4$, so $z=2^{-1/2}\big(\cos\frac{3\pi}4+\mathrm j\sin\frac{3\pi}4\big)$.

For the square roots ($n=2$), the modulus is $(2^{-1/2})^{1/2}=2^{-1/4}=0.8409$ and the arguments are

$$
\frac{\frac{3\pi}4+2k\pi}{2}=\frac{3\pi}8+k\pi,\qquad k=0,1,
$$

that is $\frac{3\pi}8$ ($67.5^\circ$) and $\frac{11\pi}8$ ($247.5^\circ$). The second lies outside $(-\pi,\pi]$, and in principal form it is $\frac{11\pi}8-2\pi=-\frac{5\pi}8$:

$$
z^{1/2}=2^{-1/4}\big(\cos\tfrac{3\pi}8+\mathrm j\sin\tfrac{3\pi}8\big)=0.3218+0.7769\mathrm j,\qquad z^{1/2}=2^{-1/4}\big(\cos\tfrac{5\pi}8-\mathrm j\sin\tfrac{5\pi}8\big)=-0.3218-0.7769\mathrm j.
$$

The two square roots are negatives of each other, as square roots always are. For the cube roots ($n=3$), the modulus is $2^{-1/6}=0.8909$ and the arguments are $\frac{\pi}4+\frac{2k\pi}3$, that is $\frac\pi4$, $\frac{11\pi}{12}$ and $\frac{19\pi}{12}$ ($45^\circ$, $165^\circ$, $285^\circ$); the last is $-\frac{5\pi}{12}$ ($-75^\circ$) in principal form:

$$
\begin{aligned}
k=0:&\quad 2^{-1/6}\big(\cos\tfrac\pi4+\mathrm j\sin\tfrac\pi4\big)=0.6300+0.6300\mathrm j,\\
k=1:&\quad 2^{-1/6}\big(\cos\tfrac{11\pi}{12}+\mathrm j\sin\tfrac{11\pi}{12}\big)=-0.8605+0.2306\mathrm j,\\
k=2:&\quad 2^{-1/6}\big(\cos\tfrac{5\pi}{12}-\mathrm j\sin\tfrac{5\pi}{12}\big)=0.2306-0.8605\mathrm j.
\end{aligned}
$$

Cubing each with `cmath` returns $-0.5+0.5\mathrm j$, and the three sum to zero.

![[m1054_complex_roots.png|900]]

### More roots (Exercises 37 and 38, Specimen Q3)

Exercise 37: $8+8\mathrm j=8\sqrt2\,e^{\mathrm j\pi/4}$. The cube roots have modulus $(8\sqrt2)^{1/3}=(2^{7/2})^{1/3}=2^{7/6}=2.2449$ and arguments $\frac{\pi}{12}+\frac{2k\pi}3$, that is $\frac{\pi}{12}$, $\frac{3\pi}4$ and $\frac{17\pi}{12}$ ($15^\circ$, $135^\circ$, $255^\circ$, the last being $-105^\circ$ in principal form):

$$
(8+8\mathrm j)^{1/3}=2.1684+0.5810\mathrm j,\quad-1.5874+1.5874\mathrm j,\quad-0.5810-2.1684\mathrm j.
$$

They form an equilateral triangle on the circle of radius $2.245$ (the fourth panel of the figure above).

Exercise 38(a): $\sqrt3-\mathrm j$ has modulus 2 and argument $-\frac\pi6$ (fourth quadrant). The fourth roots have modulus $2^{1/4}=1.1892$ and arguments $\frac{-\pi/6+2k\pi}{4}=-\frac{\pi}{24}+\frac{k\pi}2$:

$$
(\sqrt3-\mathrm j)^{1/4}=2^{1/4}\angle\Big(-\frac{\pi}{24}\Big),\ \ 2^{1/4}\angle\frac{11\pi}{24},\ \ 2^{1/4}\angle\frac{23\pi}{24},\ \ 2^{1/4}\angle\Big(-\frac{13\pi}{24}\Big),
$$

numerically $1.1790-0.1552\mathrm j$, $0.1552+1.1790\mathrm j$, $-1.1790+0.1552\mathrm j$ and $-0.1552-1.1790\mathrm j$. Exercise 38(d): $-1=1\angle\pi$, so the fourth roots are $1\angle\frac{\pi+2k\pi}4$:

$$
(-1)^{1/4}=1\angle\tfrac\pi4,\ \ 1\angle\tfrac{3\pi}4,\ \ 1\angle\big(-\tfrac{3\pi}4\big),\ \ 1\angle\big(-\tfrac\pi4\big)=\frac{\pm1\pm\mathrm j}{\sqrt2}.
$$

Specimen Test 22, Q3: $z=4\sqrt2(1-\mathrm j)$ has $|z|=4\sqrt2\cdot\sqrt2=8$ and $\operatorname{Arg}z=-\frac\pi4$, so $z=8e^{-\mathrm j\pi/4}$. The cube roots are

$$
\begin{aligned}
z^{1/3}&=8^{1/3}e^{\mathrm j(-\pi/4+2k\pi)/3}=2e^{\mathrm j(-\pi/12+2k\pi/3)},\qquad k=0,1,2\\
&=2e^{-\mathrm j\pi/12},\quad2e^{\mathrm j7\pi/12},\quad2e^{\mathrm j5\pi/4}=2e^{-\mathrm j3\pi/4}.
\end{aligned}
$$

In Cartesian form, $2e^{-\mathrm j\pi/12}=2\cos\frac\pi{12}-2\mathrm j\sin\frac\pi{12}=1.932-0.518\mathrm j$, $2e^{\mathrm j7\pi/12}=-0.518+1.932\mathrm j$ and $2e^{-\mathrm j3\pi/4}=-\sqrt2-\mathrm j\sqrt2=-1.414-1.414\mathrm j$. On the Argand diagram they sit $120^\circ$ apart on the circle $|w|=2$:

![[m1054_spec22_roots.png|480]]

### Rational powers (Example 3.21)

For a rational power $p=m/n$ in lowest terms ($n$ a natural number, $m$ an integer), define $z^{m/n}=(z^{1/n})^m$ and apply De Moivre to each of the $n$ roots:

$$
\begin{aligned}
z^{m/n}&=\Big[r^{1/n}e^{\mathrm j(\theta+2k\pi)/n}\Big]^m\\
&=r^{m/n}e^{\mathrm j(m\theta+2km\pi)/n}\\
&=r^p\big[\cos(p\theta+2k\pi p)+\mathrm j\sin(p\theta+2k\pi p)\big],\qquad k=0,1,\dots,n-1.
\end{aligned}
$$

Because $m$ and $n$ have no common factor, the $n$ values of $km$ leave different remainders on division by $n$, so there are exactly $n$ distinct values: a rational power $z^{p/q}$ in lowest terms has $q$ values.

> [!warning] Reduce the fraction first
> $z^{2/4}$ read as $(z^{1/4})^2$ squares four roots into only two distinct values (the two square roots), but read as $(z^2)^{1/4}$ it gives four values. The count $q$ is only reliable once $p/q$ is in lowest terms, so write $z^{2/4}$ as $z^{1/2}$ before starting.

Example 3.21 evaluates $\big(-\frac12+\frac12\mathrm j\big)^{-2/3}$, with $r=2^{-1/2}$ and $\theta=\frac{3\pi}4$ from Example 3.20. The modulus is $(2^{-1/2})^{-2/3}=2^{1/3}=1.2599$ and the arguments are

$$
-\tfrac23\big(\tfrac{3\pi}4+2k\pi\big)=-\tfrac\pi2-\tfrac{4k\pi}3,\qquad k=0,1,2,
$$

that is $-\frac\pi2$, $-\frac{11\pi}6$ and $-\frac{19\pi}6$, which reduce to $-\frac\pi2$, $\frac\pi6$ and $\frac{5\pi}6$ ($-90^\circ$, $30^\circ$, $150^\circ$):

$$
z^{-2/3}=-1.2599\mathrm j,\quad1.0911+0.6300\mathrm j,\quad-1.0911+0.6300\mathrm j.
$$

There are three values because the denominator of $\frac23$ is 3. As a check, each value $w$ satisfies $w^{-3}=z^2=-\frac12\mathrm j$; for the first, $(-1.2599\mathrm j)^3=-2\mathrm j^3=2\mathrm j$, whose reciprocal is $-\frac12\mathrm j$.

## 5. Quadratic equations with complex coefficients (James §3.3.1, Example 3.22)

The quadratic formula holds when $a$, $b$, $c$ are complex ($a\ne0$), because completing the square uses only arithmetic:

$$
\begin{aligned}
az^2+bz+c&=0\\
\Big(z+\frac{b}{2a}\Big)^2&=\frac{b^2-4ac}{4a^2}\\
z&=\frac{-b\pm w}{2a},\qquad w^2=\Delta=b^2-4ac.
\end{aligned}
$$

The only new step is finding a square root $w$ of the complex discriminant $\Delta$; by section 4 it has exactly two, $\pm w$ ([[Completing the Square]]).

### Square root of a complex number by equating parts

Polar form and (3.17) with $n=2$ always works. When $\Delta=p+q\mathrm j$ has integer parts, equating parts is usually faster. Set $w=u+v\mathrm j$ with $u,v$ real:

$$
\begin{aligned}
(u+v\mathrm j)^2&=p+q\mathrm j\\
u^2-v^2+2uv\,\mathrm j&=p+q\mathrm j.
\end{aligned}
$$

So $u^2-v^2=p$ and $2uv=q$. A third equation comes from the modulus, since $|w^2|=|w|^2$:

$$
u^2+v^2=|\Delta|=\sqrt{p^2+q^2}.
$$

Adding and subtracting the first and third equations:

$$
u^2=\frac{|\Delta|+p}{2},\qquad v^2=\frac{|\Delta|-p}{2},
$$

and $2uv=q$ fixes the relative sign: $u$ and $v$ have the same sign if $q>0$ and opposite signs if $q<0$.

The roots $z_1$, $z_2$ can be checked without the formula. Expanding $a(z-z_1)(z-z_2)=az^2-a(z_1+z_2)z+az_1z_2$ and comparing with $az^2+bz+c$ gives Vieta's relations

$$
z_1+z_2=-\frac ba,\qquad z_1z_2=\frac ca.
$$

### Solving a complex quadratic (Example 3.22)

Solve $z^2+(2\mathrm j-3)z+(5-\mathrm j)=0$. The discriminant is

$$
\begin{aligned}
\Delta&=(2\mathrm j-3)^2-4(5-\mathrm j)\\
&=(-4-12\mathrm j+9)-20+4\mathrm j\\
&=-15-8\mathrm j.
\end{aligned}
$$

Here $p=-15$, $q=-8$, $|\Delta|=\sqrt{225+64}=17$, so $u^2=\frac{17-15}2=1$ and $v^2=\frac{17+15}2=16$. With $q<0$, $u$ and $v$ have opposite signs, so $\sqrt\Delta=\pm(1-4\mathrm j)$; indeed $(1-4\mathrm j)^2=1-8\mathrm j-16=-15-8\mathrm j$. Then

$$
z=\frac{(3-2\mathrm j)\pm(1-4\mathrm j)}{2}=\frac{4-6\mathrm j}{2}\ \text{ or }\ \frac{2+2\mathrm j}{2}=2-3\mathrm j\ \text{ or }\ 1+\mathrm j.
$$

The polar route reaches the same square roots: $\operatorname{Arg}(-15-8\mathrm j)=-(\pi-\tan^{-1}\frac8{15})=-2.6516$, so $(-15-8\mathrm j)^{1/2}=\sqrt{17}\,e^{\mathrm j(-2.6516+2k\pi)/2}$, and $k=0$ gives $\sqrt{17}(\cos1.3258-\mathrm j\sin1.3258)=1-4\mathrm j$.

> [!check] Vieta for Example 3.22
> Sum: $(2-3\mathrm j)+(1+\mathrm j)=3-2\mathrm j=-(2\mathrm j-3)$. Product: $(2-3\mathrm j)(1+\mathrm j)=2+2\mathrm j-3\mathrm j+3=5-\mathrm j$. Both match $-b/a$ and $c/a$, and SymPy's `solve` returns $\{1+\mathrm j,\ 2-3\mathrm j\}$.

### A quadratic with an irrational square root (Exercise 40)

Solve $z^2-(3+5\mathrm j)z+8\mathrm j-5=0$. The discriminant is

$$
\begin{aligned}
\Delta&=(3+5\mathrm j)^2-4(8\mathrm j-5)\\
&=(9+30\mathrm j-25)-32\mathrm j+20\\
&=4-2\mathrm j.
\end{aligned}
$$

Here $|\Delta|=\sqrt{20}=2\sqrt5$, so $u^2=\frac{2\sqrt5+4}2=2+\sqrt5$ and $v^2=\frac{2\sqrt5-4}2=\sqrt5-2$, giving $u=2.0582$, $v=0.4859$ with $uv=\sqrt{(2+\sqrt5)(\sqrt5-2)}=1$. Since $q=-2<0$, $\sqrt\Delta=\pm(2.0582-0.4859\mathrm j)$, and

$$
z=\frac{(3+5\mathrm j)\pm(2.0582-0.4859\mathrm j)}{2}=2.529+2.257\mathrm j\ \text{ or }\ 0.471+2.743\mathrm j.
$$

In exact form, $z=\dfrac{3\pm\sqrt{2+\sqrt5}}2+\mathrm j\,\dfrac{5\mp\sqrt{\sqrt5-2}}2$. The roots sum to $3+5\mathrm j$ and multiply to $-5.00+8.00\mathrm j$, matching the coefficients.

## 6. Powers and multiple angles (James §3.3.2)

Take $z=\cos\theta+\mathrm j\sin\theta$, so $|z|=1$. By De Moivre with $n$ and with $-n$,

$$
\begin{aligned}
z^n&=\cos n\theta+\mathrm j\sin n\theta,\\
z^{-n}&=\cos(-n\theta)+\mathrm j\sin(-n\theta)=\cos n\theta-\mathrm j\sin n\theta.
\end{aligned}
$$

Adding and subtracting:

$$
z^n+z^{-n}=2\cos n\theta,\qquad z^n-z^{-n}=2\mathrm j\sin n\theta\qquad(n\text{ any integer}). \tag{3.20a, b}
$$

This derivation is Specimen Test 22, Q4. Its main use is to rewrite a power of $\cos\theta$ or $\sin\theta$ as a sum of multiple angles, which can then be integrated term by term ([[Trigonometric Integrals and Power Reduction]]). With $n=1$, $2\cos\theta=z+z^{-1}$, and the binomial expansion gives

$$
\begin{aligned}
8\cos^3\theta&=(z+z^{-1})^3\\
&=z^3+3z+3z^{-1}+z^{-3}\\
&=(z^3+z^{-3})+3(z+z^{-1})\\
&=2\cos3\theta+6\cos\theta,
\end{aligned}
$$

so $\cos^3\theta=\frac14(\cos3\theta+3\cos\theta)$. At $\theta=\frac\pi3$ both sides equal $\frac18$. Run the other way, De Moivre expands a multiple angle as a polynomial: the real and imaginary parts of $(\cos\theta+\mathrm j\sin\theta)^3=\cos^3\theta+3\mathrm j\cos^2\theta\sin\theta-3\cos\theta\sin^2\theta-\mathrm j\sin^3\theta$ give

$$
\cos3\theta=\cos^3\theta-3\cos\theta\sin^2\theta=4\cos^3\theta-3\cos\theta,\qquad\sin3\theta=3\cos^2\theta\sin\theta-\sin^3\theta=3\sin\theta-4\sin^3\theta,
$$

using $\sin^2\theta=1-\cos^2\theta$ and $\cos^2\theta=1-\sin^2\theta$.

## 7. Loci in the complex plane (James §3.4.1–3.4.2)

A **locus** is the set of points with a stated property. For a condition on $z$ it is a curve or region in the Argand diagram ([[Argand Diagram]]). The geometric reading comes from one fact: $|z-a|$ is the distance from the point $z$ to the point $a$, and $\arg(z-a)$ is the direction of $z$ seen from $a$.

### Method

1. Substitute $z=x+\mathrm jy$.
2. For a modulus condition, write $|X+\mathrm jY|=\sqrt{X^2+Y^2}$ and square both sides.
3. For the real or imaginary part of a quotient, multiply the top and bottom by the conjugate of the denominator; the denominator becomes real.
4. Collect terms and complete the square to read off a centre and radius.
5. Remove points where the original expression is undefined (a denominator zero, or $\arg0$).

### Straight lines (Example 3.25)

(a) $\operatorname{Re}z=4$: every point $4+\mathrm jy$, the vertical line $x=4$.

(b) $\arg(z-1-\mathrm j)=\frac\pi4$: set $u=z-1-\mathrm j$, so $\arg u=\frac\pi4$ and $u=re^{\mathrm j\pi/4}$ with $r>0$ unknown. Then

$$
z=1+\mathrm j+r\big(\tfrac1{\sqrt2}+\tfrac{\mathrm j}{\sqrt2}\big),\qquad x-1=y-1=\tfrac{r}{\sqrt2}>0,
$$

the half-line $y=x$, $x>1$, starting at $(1,1)$ at $45^\circ$ with the end point excluded because $\arg0$ is undefined.

(c) $\left|\frac{z-2\mathrm j}{z-1}\right|=1$, that is $|z-2\mathrm j|=|z-1|$:

$$
\begin{aligned}
x^2+(y-2)^2&=(x-1)^2+y^2\\
x^2+y^2-4y+4&=x^2-2x+1+y^2\\
2x-4y+3&=0,\qquad\text{i.e. }y=\tfrac12x+\tfrac34.
\end{aligned}
$$

Geometrically the points equidistant from $2\mathrm j$ and $1$ form the perpendicular bisector of the segment joining them: the line passes through the midpoint $(\frac12,1)$ with slope $\frac12$, and the segment from $(1,0)$ to $(0,2)$ has slope $-2$.

(d) $\operatorname{Im}\big((1-2\mathrm j)z\big)=3$: expand the product,

$$
(1-2\mathrm j)(x+\mathrm jy)=x+2y+\mathrm j(y-2x),
$$

so $y-2x=3$, the line $y=2x+3$.

![[m1054_complex_loci.png|900]]

### Circles centred at a point (Example 3.26, Exercise 47(b))

$|z-z_1|=R$ is the circle of centre $z_1$ and radius $R$; with a parameter $t$ it is $z=z_1+Re^{\mathrm jt}$, $-\pi<t\le\pi$. For $|z-(2+3\mathrm j)|=2$ (Example 3.26),

$$
\begin{aligned}
|(x-2)+\mathrm j(y-3)|&=2\\
(x-2)^2+(y-3)^2&=4\\
x^2+y^2-4x-6y+9&=0,
\end{aligned}
$$

centre $(2,3)$, radius 2. A coefficient on $z$ must be divided out first. For $|2z-1|=3$ (Exercise 47(b)), $|2z-1|=2\,|z-\tfrac12|$, so $|z-\frac12|=\frac32$:

$$
\big(x-\tfrac12\big)^2+y^2=\tfrac94,
$$

the circle of centre $(\frac12,0)$ and radius $\frac32$.

### The circle of Apollonius (Example 3.27, Exercise 45(c), Specimen Q5)

$|z-a|=k|z-b|$ with $k>0$ fixed says the distance to $a$ is $k$ times the distance to $b$. For $k=1$ it is the perpendicular bisector of $a$ and $b$, as in Example 3.25(c). For $k\ne1$ it is a circle, the **circle of Apollonius**. Example 3.27, $\left|\dfrac{z-\mathrm j}{z-1-2\mathrm j}\right|=\sqrt2$, shows the working:

$$
\begin{aligned}
|x+\mathrm j(y-1)|&=\sqrt2\,|(x-1)+\mathrm j(y-2)|\\
x^2+(y-1)^2&=2\big[(x-1)^2+(y-2)^2\big]\\
x^2+y^2-2y+1&=2x^2-4x+2+2y^2-8y+8\\
0&=x^2+y^2-4x-6y+9\\
(x-2)^2+(y-3)^2&=4.
\end{aligned}
$$

This is the same circle as Example 3.26, centre $(2,3)$ and radius 2, described a different way.

The centre and radius follow in general from conjugates, with $|w|^2=w\bar w$. Square the condition:

$$
\begin{aligned}
(z-a)(\bar z-\bar a)&=k^2(z-b)(\bar z-\bar b)\\
(1-k^2)|z|^2-z(\bar a-k^2\bar b)-\bar z(a-k^2b)+|a|^2-k^2|b|^2&=0.
\end{aligned}
$$

Divide by $1-k^2$ (allowed since $k\ne1$) and write $c=\dfrac{a-k^2b}{1-k^2}$:

$$
\begin{aligned}
|z|^2-z\bar c-\bar zc+\frac{|a|^2-k^2|b|^2}{1-k^2}&=0\\
|z-c|^2&=|c|^2-\frac{|a|^2-k^2|b|^2}{1-k^2}.
\end{aligned}
$$

Over the common denominator $(1-k^2)^2$, the right-hand side's numerator is

$$
\begin{aligned}
|a-k^2b|^2-(|a|^2-k^2|b|^2)(1-k^2)&=|a|^2-k^2(a\bar b+\bar ab)+k^4|b|^2-|a|^2+k^2|a|^2+k^2|b|^2-k^4|b|^2\\
&=k^2\big(|a|^2-a\bar b-\bar ab+|b|^2\big)\\
&=k^2|a-b|^2.
\end{aligned}
$$

So the locus is the circle

$$
\boxed{\ \text{centre }c=\frac{a-k^2b}{1-k^2},\qquad\text{radius }R=\frac{k\,|a-b|}{|1-k^2|}\ }
$$

From $c-a=\frac{k^2(a-b)}{1-k^2}$ and $c-b=\frac{a-b}{1-k^2}$, the centre lies on the line through $a$ and $b$, and $|c-a|\,|c-b|=R^2$: $a$ and $b$ are inverse points of the circle. For $k>1$ the circle encloses $b$, for $k<1$ it encloses $a$. For Example 3.27, $a=\mathrm j$, $b=1+2\mathrm j$, $k=\sqrt2$ gives $c=\frac{\mathrm j-2-4\mathrm j}{-1}=2+3\mathrm j$ and $R=\frac{\sqrt2\cdot\sqrt2}{1}=2$, matching the Cartesian working, and $|c-a||c-b|=2\sqrt2\cdot\sqrt2=4=R^2$.

![[m1054_m22_apollonius.png|900]]

Exercise 45(c), $\left|\dfrac{z+\mathrm j}{z-\mathrm j}\right|=3$:

$$
\begin{aligned}
x^2+(y+1)^2&=9\big[x^2+(y-1)^2\big]\\
x^2+y^2+2y+1&=9x^2+9y^2-18y+9\\
0&=8x^2+8y^2-20y+8\\
x^2+\big(y-\tfrac54\big)^2&=\tfrac{25}{16}-1=\big(\tfrac34\big)^2,
\end{aligned}
$$

a circle of Apollonius with centre $(0,\frac54)$ and radius $\frac34$. It encloses $\mathrm j$ but not $-\mathrm j$. The general formula with $a=-\mathrm j$, $b=\mathrm j$, $k=3$ gives $c=\frac{-\mathrm j-9\mathrm j}{-8}=\frac54\mathrm j$ and $R=\frac{3\cdot2}8=\frac34$.

Specimen Test 22, Q5, $\left|\dfrac{z+2\mathrm j}{z-\mathrm j}\right|=2$:

$$
\begin{aligned}
x^2+(y+2)^2&=4\big[x^2+(y-1)^2\big]\\
x^2+y^2+4y+4&=4x^2+4y^2-8y+4\\
0&=3x^2+3y^2-12y\\
x^2+(y-2)^2&=4,
\end{aligned}
$$

the circle with centre $2\mathrm j$ and radius 2. The formula gives $c=\frac{-2\mathrm j-4\mathrm j}{-3}=2\mathrm j$ and $R=\frac{2\cdot3}3=2$.

### Real or imaginary part of a quotient (Example 3.28, Exercise 45(a))

For $\operatorname{Re}\dfrac{z-\mathrm j}{z+1}=0$ (Example 3.28), multiply the top and bottom by $\overline{z+1}=(x+1)-\mathrm jy$:

$$
\frac{z-\mathrm j}{z+1}=\frac{[x+\mathrm j(y-1)][(x+1)-\mathrm jy]}{(x+1)^2+y^2}.
$$

The denominator is real, so the real part vanishes when the real part of the numerator does:

$$
\begin{aligned}
x(x+1)+y(y-1)&=0\\
x^2+y^2+x-y&=0\\
\big(x+\tfrac12\big)^2+\big(y-\tfrac12\big)^2&=\tfrac12,
\end{aligned}
$$

the circle of centre $(-\frac12,\frac12)$ and radius $\frac1{\sqrt2}$, with the point $z=-1$ removed because the quotient is undefined there.

The geometry gives the same circle without algebra. $\operatorname{Re}\frac{z-a}{z-b}=0$ says $\frac{z-a}{z-b}$ is purely imaginary, so the directions from $z$ to $a$ and from $z$ to $b$ differ by $\pm\frac\pi2$: the angle at $z$ in the triangle $azb$ is a right angle, and by Thales' theorem $z$ lies on the circle with diameter $ab$. With $a=\mathrm j$, $b=-1$, the centre is $\frac{a+b}2=-\frac12+\frac12\mathrm j$ and the radius is $\frac{|a-b|}2=\frac{\sqrt2}2$. The point $z=a$ itself is included (the quotient is 0) and $z=b$ is excluded.

For $\operatorname{Re}\dfrac{z+\mathrm j}{z-\mathrm j}=1$ (Exercise 45(a)), multiply by $\overline{z-\mathrm j}=\bar z+\mathrm j$:

$$
\begin{aligned}
\frac{\operatorname{Re}\big[(z+\mathrm j)(\bar z+\mathrm j)\big]}{|z-\mathrm j|^2}&=\frac{x^2+y^2-1}{x^2+(y-1)^2}=1\\
x^2+y^2-1&=x^2+y^2-2y+1\\
y&=1,
\end{aligned}
$$

the horizontal line through $\mathrm j$, with the point $z=\mathrm j$ removed. A shorter route: $\frac{z+\mathrm j}{z-\mathrm j}=1+\frac{2\mathrm j}{z-\mathrm j}$, so the condition is that $\frac{2\mathrm j}{z-\mathrm j}$ is purely imaginary, which needs $z-\mathrm j$ real and nonzero.

> [!warning] Excluded points
> A locus defined through $\frac{z-a}{z-b}$ never contains $z=b$, even when the Cartesian equation is satisfied there; $(-1,0)$ satisfies $x^2+y^2+x-y=0$ but is not on the locus of Example 3.28. The same applies to the end point of a half-line $\arg(z-z_0)=\alpha$. Mark these as open circles on a sketch.

### Summary of standard loci

| Condition on $z$ | Locus |
|---|---|
| $\lvert z-z_0\rvert=r$ | circle, centre $z_0$, radius $r$ |
| $\lvert z-a\rvert=\lvert z-b\rvert$ | perpendicular bisector of $a$ and $b$ |
| $\lvert z-a\rvert=k\lvert z-b\rvert$, $k\ne1$ | circle of Apollonius, centre $\frac{a-k^2b}{1-k^2}$, radius $\frac{k\lvert a-b\rvert}{\lvert1-k^2\rvert}$ |
| $\arg(z-z_0)=\alpha$ | half-line from $z_0$ at angle $\alpha$, excluding $z_0$ |
| $\operatorname{Re}z=c$, $\operatorname{Im}(az)=c$ | straight lines |
| $\operatorname{Re}\frac{z-a}{z-b}=0$ | circle on diameter $ab$, minus $b$ |
| $\operatorname{Im}\frac{z-a}{z-b}=0$ | line through $a$ and $b$, minus $b$ |
| $\operatorname{Re}$ or $\operatorname{Im}$ of $\frac{z-a}{z-b}$ equal to another constant | circle or line through $b$, minus $b$ |

## Terminology and alternative names

| This note | Also written | Where |
|---|---|---|
| $\mathrm j$ | $i$ | mathematics texts, Python's `1j` uses j |
| $\operatorname{Ln}z$, principal value of the logarithm | $\ln z$ with $k=0$ | James (3.15) writes $\ln z$ for the principal value |
| $\operatorname{Arg}z$, principal argument in $(-\pi,\pi]$ | $\arg z$ | James uses $\arg z$ for the principal value |
| $\cos\mathrm jx=\cosh x$ and the like | Osborn's rule | James §2.7.4 and §3.2.9 |
| circle of Apollonius | Apollonian circle | general geometry texts |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M22 Solutions - Complex Numbers II]]
- Previous in the module: [[MATH1054 M20 - Further Calculus II]] · Next: [[MATH1054 M24 - Statistics I]]
- Builds on: [[MATH1054 M05 - Complex Numbers I]] (forms, modulus and argument), [[MATH1054 M07 - Functions]] (hyperbolic functions and Osborn's rule)
- Concepts: [[Complex Functions - Trig, Hyperbolic and Logarithm]] · [[De Moivre's Theorem and Roots of Complex Numbers]] · [[Loci in the Complex Plane]] · [[Euler's Formula]] · [[Hyperbolic Functions]] · [[Complex Numbers - Cartesian, Polar and Exponential Forms]] · [[Argand Diagram]]
- Used in Year 1: phasors and impedance in [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] and [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]] ([[Phasor Representation]], [[Complex Impedance]])
- Used in Year 2: complex roots of the auxiliary equation in [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]; $e^{\mathrm jn\omega t}$ and $z^n+z^{-n}=2\cos n\theta$ in [[MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series]]; [[Poles and Zeros]] and [[Root Locus]] in the $s$-plane (SESA2027)
- Used in Year 3: $\ln z$ as the complex potential of a source and a vortex in [[SESA3043 1.3 - Complex Potential, Wedge Flows and Unsteady Bernoulli]]; circles mapped to aerofoils in [[SESA3043 2.1 - Complex Functions and Conformal Mapping]]

## Sources

- MATH1054 Module Booklet, Module 22 work scheme and Specimen Test 22 (booklet PDF pp. 76–79)
- James, *Modern Engineering Mathematics* (6th ed.): §3.2.9 circular and hyperbolic functions, §3.2.10 logarithm (pp. 202–207); §3.3.1 De Moivre's theorem and roots, §3.3.2 powers and multiple angles (pp. 208–213); §3.4.1–3.4.2 straight lines and circles (pp. 216–219)
- Worked solutions to every set item: [[MATH1054 M22 Solutions - Complex Numbers II]]

## Self-study tasks

### Core

- [ ] Exercises 29(a),(b) and 30(a) (Module 22 work scheme): $\sin\big(\frac56\pi+\mathrm j\big)$, $\cos\big(\mathrm j\frac34\big)$, and all solutions of $\sin z=2$. Answers: $0.7715-1.0178\mathrm j$; $1.2947$; $z=\frac\pi2+2k\pi\pm1.317\mathrm j$. → [[#Solving cos z = 2 and sin z = 2]] · [[MATH1054 M22 Solutions - Complex Numbers II#Exercise 29|Exercise 29]] · [[MATH1054 M22 Solutions - Complex Numbers II#Part B: Assigned exercises|Exercise 30(a)]]
- [ ] Exercise A (Module 22 work scheme): all values of $\ln(5+12\mathrm j)$ and $\ln\big(-\frac12-\frac12\sqrt3\,\mathrm j\big)$. → [[#Logarithm examples (Example 3.18, Exercise A, Specimen Q2)]] · [[MATH1054 M22 Solutions - Complex Numbers II#Booklet Exercise A: All values of the logarithms|solution]]
- [ ] Exercises 37 and 38(a),(d) (Module 22 work scheme): the three values of $(8+8\mathrm j)^{1/3}$ on an Argand diagram, and $(\sqrt3-\mathrm j)^{1/4}$, $(-1)^{1/4}$ in polar form. → [[#More roots (Exercises 37 and 38, Specimen Q3)]] · [[MATH1054 M22 Solutions - Complex Numbers II#Exercise 38: Polar forms|Exercise 38]] · [[MATH1054 M22 Solutions - Complex Numbers II#Part B: Assigned exercises|Exercise 37]]
- [ ] Exercise 40 (Module 22 work scheme): solve $z^2-(3+5\mathrm j)z+8\mathrm j-5=0$ and check with Vieta. → [[#A quadratic with an irrational square root (Exercise 40)]] · [[MATH1054 M22 Solutions - Complex Numbers II#Part B: Assigned exercises|solution]]
- [ ] Exercises 45(a),(c) and 47(b) (Module 22 work scheme): identify and sketch the loci, marking excluded points. → [[#The circle of Apollonius (Example 3.27, Exercise 45(c), Specimen Q5)]] · [[MATH1054 M22 Solutions - Complex Numbers II#Exercise 45: Identify and sketch the loci|Exercise 45]] · [[MATH1054 M22 Solutions - Complex Numbers II#Part B: Assigned exercises|Exercise 47(b)]]

### Further practice

- [ ] Specimen Test 22, Q1–Q5, timed: $\sin(\frac\pi2+\mathrm j)$, $\ln(-3)$, the cube roots of $4\sqrt2(1-\mathrm j)$, $z^n\pm z^{-n}$, and the locus $\left|\frac{z+2\mathrm j}{z-\mathrm j}\right|=2$. → [[MATH1054 M22 Solutions - Complex Numbers II#Part C: Specimen Test 22|solutions]]
- [ ] Examples 3.17(a),(b),(d), 3.18–3.22 and 3.25–3.28 (Module 22 work scheme), reworked from the question alone. → [[MATH1054 M22 Solutions - Complex Numbers II#Part A: Worked examples|solutions]]
- [ ] Expand $\cos^3\theta$ in multiple angles and $\cos3\theta$, $\sin3\theta$ as polynomials, using [[#6. Powers and multiple angles (James §3.3.2)|section 6]] (suggested, not set; compare James Exercises 35 and 36).

## Transcript and slide slips

> [!warning] Slips in James (6th ed.)
> | Where | James says | Correct |
> |---|---|---|
> | [[#All values of the logarithm]] (p. 206) | final line of the derivation $v=\ln\lvert z\rvert+\mathrm j\arg z+\mathrm j2n\pi$ | $w=\ln\lvert z\rvert+\mathrm j\arg z+\mathrm j2n\pi$ (the work scheme gives the same correction) |
> | [[#Rational powers (Example 3.21)]] (p. 211) | "From Example 3.17, we can write $-\frac12+\mathrm j\frac12=\dots$" | the polar form comes from Example 3.20 |
> | [[#The circle of Apollonius (Example 3.27, Exercise 45(c), Specimen Q5)]] (p. 218) | the $k=1$ line is "as we saw in Example 3.25(d)" | Example 3.25(c), $\lvert z-2\mathrm j\rvert=\lvert z-1\rvert$ |
> | [[#Real or imaginary part of a quotient (Example 3.28, Exercise 45(a))]] (p. 219) | the locus is the whole circle of centre $(-\frac12,\frac12)$ | the point $z=-1$ must be excluded |

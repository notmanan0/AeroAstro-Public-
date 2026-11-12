---
title: "MATH1054 M07 - Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 7
tags:
  - math1054
  - functions
  - inverse-functions
  - hyperbolic-functions
aliases: ["MATH1054 Module 7", "Functions"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 7 work scheme; James §2.1, §2.2.1, §2.2.3–2.2.4, §2.2.6, §2.6.7, §2.7.1–2.7.2, §2.7.4–2.7.5, §8.3.9 (below eq. 8.18), §8.3.12"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M08 - Differentiation II]]"]
key_concepts: ["[[Inverse Functions]]", "[[Even, Odd and Periodic Functions]]", "[[Inverse Trigonometric Functions]]", "[[Hyperbolic Functions]]"]
tutorial_sheets: ["[[MATH1054 M07 Solutions - Functions]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 7)", "02 - Sources/Modern Engineering Mathematics.pdf (§2.2, §2.6–2.7, §8.3.9–8.3.12)"]
---

# MATH1054 M07 - Functions

> [!abstract] Summary
> A function is a rule together with a domain: each input in the domain gives exactly one output, and the set of outputs actually reached is the range. A function has an inverse only if it is one-to-one, so the periodic trigonometric functions are first restricted to principal branches, which gives $\sin^{-1}$ on $[-\frac\pi2,\frac\pi2]$, $\cos^{-1}$ on $[0,\pi]$ and $\tan^{-1}$ on $(-\frac\pi2,\frac\pi2)$. The hyperbolic functions $\cosh x=\frac12(e^x+e^{-x})$ and $\sinh x=\frac12(e^x-e^{-x})$ satisfy $\cosh^2x-\sinh^2x=1$, and their inverses are logarithms, for example $\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big)$. Every derivative of an inverse function comes from one rule, $\frac{\mathrm dy}{\mathrm dx}=1\big/\frac{\mathrm dx}{\mathrm dy}$, followed by an identity.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a domain, range or inverse; whether a function is odd, even or periodic; the value or graph of $\sin^{-1}$, $\cos^{-1}$ or $\tan^{-1}$; a log simplification; a hyperbolic value, identity or equation; or the derivative of an inverse trigonometric or hyperbolic function.
> - **Assumptions:** angles in radians; principal ranges $\sin^{-1}\in[-\frac\pi2,\frac\pi2]$, $\cos^{-1}\in[0,\pi]$, $\tan^{-1}\in(-\frac\pi2,\frac\pi2)$, $\cosh^{-1}\geq0$; $\ln$ needs a positive argument.
> - **Method:** 1. Write the condition the input must satisfy (root $\geq0$, denominator $\neq0$, log argument $>0$). 2. For an inverse, put $y=f(x)$, solve for $x$, swap letters; the new domain is the old range. 3. For a hyperbolic equation, substitute the exponentials and solve the quadratic in $e^x$, rejecting $e^x\leq0$. 4. For a derivative of $f^{-1}$, write $x=f(y)$, differentiate, and use $\cos^2+\sin^2=1$ or $\cosh^2-\sinh^2=1$ with the sign the principal range fixes. 5. Check one value numerically.
> - **Common mistakes:** taking $\sin^{-1}(\sin x)=x$ outside $[-\frac\pi2,\frac\pi2]$; writing $\frac{\mathrm d}{\mathrm dx}\cosh x=-\sinh x$ by analogy with $\cos$.
> - **Practise:** [[#Solving a hyperbolic equation (Example 2.59)]] · [[MATH1054 M07 Solutions - Functions#Part C: Specimen Test 7|Specimen Test 7]]

A function is a rule with a list of allowed inputs. The list matters as much as the formula: $\sqrt{(x+4)(3-x)}$ means nothing for $x=5$, and a temperature conversion means nothing below absolute zero. Asking which inputs are allowed and which outputs come out (the domain and the range) is what makes it possible to run a function backwards, and running it backwards is what an engineer does whenever a measured output has to be turned into the input that caused it: a thermocouple voltage into a temperature, a measured angle's sine into the angle.

Running a function backwards only works if no two inputs give the same output. Periodic functions fail this badly, since $\sin x$ takes every value in $[-1,1]$ infinitely often, so the inverse trigonometric functions are defined by keeping one branch of each graph. The choice of branch is why a calculator gives $\sin^{-1}(\sin 2)=\pi-2$ rather than $2$ and why $\cos^{-1}$ of a negative number is an obtuse angle, and it fixes the sign of the square root in each derivative.

The hyperbolic functions are built out of $e^x$ and $e^{-x}$. They behave like $\cos$ and $\sin$ with one sign changed, and they appear wherever an exponential grows in one direction and decays in the other: the temperature in a cooling fin, the sag of a hanging cable, the solutions $A\cosh kx+B\sinh kx$ of $y''=k^2y$ in [[MATH1054 M12 - Differential Equations II|M12]], and the separated solutions of Laplace's equation in Year 2. Their inverses are logarithms, and they supply the standard integrals $\int\frac{\mathrm dx}{\sqrt{x^2\pm a^2}}$ used in [[MATH1054 M09 - Integration II|M09]]. Symmetry (odd, even, periodic) applies to both families and is the starting point of Fourier series in MATH2048.

---

## 1. Functions, domain and range (James §2.2.1)

A **function** $f$ from a set $X$ to a set $Y$ assigns to each $x$ in $X$ exactly one $y=f(x)$ in $Y$. The set $X$ is the **domain**, $Y$ is the **codomain**, $f(x)$ is the **image** of $x$, and the set of all images is the **range** (James also calls it the image set). The range is contained in the codomain but is often smaller. For real functions the codomain is usually taken to be $\mathbb R$, so the work in a question goes into the domain (which inputs give a real answer) and the range (which outputs are actually reached).

A formula with no stated domain is given the largest domain on which it makes sense. Three conditions cover almost every case: the expression under an even root is $\geq0$, a denominator is $\neq0$, and the argument of a logarithm is $>0$.

### Domain and range of two formulae (Example 2.1)

For $f(x)=3x^2+1$ every real $x$ gives a real value, so the domain is $\mathbb R$. Since $x^2\geq0$,

$$
3x^2+1\geq1 ,
$$

with equality at $x=0$, so the range is $[1,\infty)$. The values asked for are $f(2)=13$ and $f(-3)=28$, and $f(-x)=3(-x)^2+1=f(x)$, so $f$ is even (Section 4).

For $f(x)=\sqrt{(x+4)(3-x)}$ the root needs

$$
(x+4)(3-x)\geq0 .
$$

The quadratic has roots $-4$ and $3$ and a negative $x^2$ coefficient, so it is non-negative between the roots and the domain is $[-4,3]$. For the range, complete the square:

$$
\begin{aligned}
(x+4)(3-x)&=-x^2-x+12\\
&=-\big(x^2+x\big)+12\\
&=-\big(x+\tfrac12\big)^2+\tfrac14+12\\
&=\tfrac{49}{4}-\big(x+\tfrac12\big)^2 .
\end{aligned}
$$

The largest value under the root is $\frac{49}4$, at $x=-\frac12$, and the smallest is $0$, at the ends $x=-4$ and $x=3$. Taking the root, the range is

$$
\big[0,\tfrac72\big].
$$

Also $f(2)=\sqrt{6\cdot1}=\sqrt6$, $f(-3)=\sqrt{1\cdot6}=\sqrt6$, and $f(-x)=\sqrt{(4-x)(3+x)}$, which is defined for $-3\leq x\leq4$, a different interval from the domain of $f$. (The value $\sqrt{35}/2$ printed in James is a slip; see [[#Transcript and slide slips]].)

### Celsius to Fahrenheit (Example 2.3)

The rule $T_2=\frac95T_1+32$ converts $T_1$ in °C to $T_2$ in °F: multiply by $\frac95$, then add $32$. Physically the domain is $T_1\geq-273.15\,$°C (absolute zero) and the codomain is $\mathbb R$. The graph is the part of the straight line of gradient $\frac95$ and intercept $32$ to the right of $T_1=-273.15$, and since the function is increasing the range starts at the image of absolute zero:

$$
T_2\geq\tfrac95(-273.15)+32=-459.67\ \text{°F}.
$$

The three conversions are $60\,$°C $\to108+32=140\,$°F, $0\,$°C $\to32\,$°F and $-50\,$°C $\to-90+32=-58\,$°F.

### A domain with a strict inequality (Specimen Test 7, Q1)

For

$$
f(x)=\frac{x^2+1}{\sqrt{x^2-1}}
$$

the root sits in a denominator, so it must be strictly positive:

$$
x^2-1>0\quad\Longleftrightarrow\quad|x|>1 .
$$

The domain is $(-\infty,-1)\cup(1,\infty)$. Only $x^2$ appears, so $f(-x)=f(x)$ and $f$ is even over its domain; for instance $f(2)=f(-2)=5/\sqrt3\approx2.887$.

## 2. Inverse functions (James §2.2.3)

The **inverse function** $f^{-1}$ reverses $f$: if $y=f(x)$ then $x=f^{-1}(y)$. Relabelling so that $x$ is again the input,

$$
y=f^{-1}(x)\quad\Longleftrightarrow\quad x=f(y).
$$

The roles of the two sets swap with the variables: the domain of $f^{-1}$ is the range of $f$, and the range of $f^{-1}$ is the domain of $f$.

For $f^{-1}$ to be a function, each output of $f$ must come from exactly one input. A function with this property is **one-to-one** (James also writes 1:1, or injective). Graphically, $f$ is one-to-one exactly when every horizontal line meets its graph at most once, because a horizontal line $y=c$ crossing twice means two inputs share the output $c$. A function that is strictly increasing or strictly decreasing on its domain always passes this test.

> [!warning] The $-1$ is not a power
> $f^{-1}(x)$ is the inverse function, while $[f(x)]^{-1}=1/f(x)$. So $\sin^{-1}x$ is the angle whose sine is $x$, not $\operatorname{cosec}x$, and $\sinh^{-1}x$ is not $\operatorname{cosech}x$. Only $\sin^2x$, $\sinh^2x$ and other positive powers of function names mean powers.

The method follows from the definition:

1. Write $y=f(x)$.
2. Solve for $x$ in terms of $y$.
3. Swap the letters $x$ and $y$.
4. State the domain of $f^{-1}$: the range of $f$.

The graph of $f^{-1}$ is the reflection of the graph of $f$ in the line $y=x$, because swapping $x$ and $y$ sends the point $(a,b)$ to $(b,a)$, its mirror image in that line. Vertical asymptotes of $f$ become horizontal asymptotes of $f^{-1}$ and vice versa. The axes need equal scales for the reflection to look like one.

![[m1054_inverse_reflections.png|900]]

### A linear inverse (Example 2.6)

For $y=\frac15(4x-3)$:

$$
\begin{aligned}
5y&=4x-3\\
4x&=5y+3\\
x&=\frac{5y+3}{4}.
\end{aligned}
$$

Swapping the letters,

$$
f^{-1}(x)=\frac{5x+3}{4}.
$$

As a check, $f(2)=\frac15(8-3)=1$ and $f^{-1}(1)=\frac{5+3}4=2$, and in general

$$
f\big(f^{-1}(x)\big)=\tfrac15\big(4\cdot\tfrac{5x+3}4-3\big)=\tfrac15(5x+3-3)=x .
$$

### A rational inverse (Example 2.7)

For $y=\dfrac{x+2}{x+1}$ with $x\neq-1$:

$$
\begin{aligned}
y(x+1)&=x+2\\
xy+y&=x+2\\
xy-x&=2-y\\
x(y-1)&=2-y\\
x&=\frac{2-y}{y-1}.
\end{aligned}
$$

So

$$
f^{-1}(x)=\frac{2-x}{x-1},\qquad x\neq1 .
$$

The excluded value is the missing output of $f$: setting $y=1$ in the original equation gives $x+1=x+2$, which has no solution, so the range of $f$ omits $1$. That value is the horizontal asymptote $y=1$ of $f$. In Example 2.8(b) the asymptotes $x=-1$ and $y=1$ of $f$ become $y=-1$ and $x=1$ for $f^{-1}$, as the middle panel above shows. The left panel is Example 2.8(a), the temperature line and its inverse $f^{-1}(x)=\frac59(x-32)$, which cross on $y=x$ at $-40$, the one temperature that reads the same in both scales.

### Restricting the domain (Example 2.8(c) and Exercise 10)

$f(x)=x^2$ is not one-to-one on $\mathbb R$, since $f(2)=f(-2)=4$. Its reflection in $y=x$ is the sideways parabola $y^2=x$, which gives two values of $y$ for each $x>0$ and so is not a function (dashed in the right panel above). Restricting $f$ to $x\geq0$ keeps one half, and the inverse of $x^2$ on $x\geq0$ is $\sqrt x$, the non-negative root. Composing in the other order shows the cost of the restriction:

$$
\sqrt{x^2}=|x|\quad\text{for all real }x,
$$

which equals $x$ only for $x\geq0$.

Exercise 10(a): $y=2x-3$ gives $x=\frac{y+3}2$, so $f^{-1}(x)=\frac12(x+3)$ on all of $\mathbb R$.

Exercise 10(c): $f(x)=x^2+1$ is even, so $f(-x)=f(x)$ and it is not one-to-one on $\mathbb R$. On $x\geq0$:

$$
\begin{aligned}
y&=x^2+1\\
x^2&=y-1\\
x&=+\sqrt{y-1}\qquad(x\geq0),
\end{aligned}
$$

so $f^{-1}(x)=\sqrt{x-1}$ with domain $x\geq1$, the range of $f$. Restricting to $x\leq0$ instead gives $f^{-1}(x)=-\sqrt{x-1}$.

### The derivative of an inverse function

Differentiate the identity $f\big(f^{-1}(x)\big)=x$ with the chain rule:

$$
\begin{aligned}
f'\big(f^{-1}(x)\big)\cdot\big(f^{-1}\big)'(x)&=1\\
\big(f^{-1}\big)'(x)&=\frac{1}{f'\big(f^{-1}(x)\big)},
\end{aligned}
$$

valid wherever $f'\big(f^{-1}(x)\big)\neq0$. In Leibniz notation, with $y=f^{-1}(x)$ and so $x=f(y)$,

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{1}{\mathrm dx/\mathrm dy}.
$$

The slope of the reflected graph is the reciprocal of the original slope at the mirror-image point. For example, $f(x)=x^3+x$ is increasing, so it has an inverse, although no simple formula for it. Since $f(1)=2$ and $f'(1)=3+1=4$,

$$
\big(f^{-1}\big)'(2)=\frac{1}{f'(1)}=\frac14 .
$$

The same rule gives $\frac{\mathrm d}{\mathrm dx}\ln x$: with $y=\ln x$, $x=e^y$, so $\frac{\mathrm dy}{\mathrm dx}=\frac1{e^y}=\frac1x$. Section 9 applies it to every inverse trigonometric and hyperbolic function.

> [!check] Inverse slope by finite differences
> Solving $z^3+z=2\pm10^{-6}$ numerically and differencing gives $\big(f^{-1}\big)'(2)=0.2500000$, matching $1/f'(1)=\frac14$.

## 3. Composite functions (James §2.2.4)

The **composite** $f\circ g$ applies $g$ first and then $f$:

$$
(f\circ g)(x)=f\big(g(x)\big).
$$

The intermediate variable $u=g(x)$ is the output of the first block and the input of the second. To form $f(g(x))$, replace every $x$ in the formula for $f$ by $g(x)$. The composite is defined only where $g(x)$ lies in the domain of $f$; for example $\ln(\sin x)$ needs $\sin x>0$.

For $f(x)=x^2+2x$ and $g(x)=x-1$ (Example 2.9):

$$
\begin{aligned}
f\big(g(x)\big)&=(x-1)^2+2(x-1)\\
&=x^2-2x+1+2x-2\\
&=x^2-1,
\end{aligned}
$$

$$
g\big(f(x)\big)=(x^2+2x)-1=x^2+2x-1 .
$$

The two differ, and in general $f\circ g\neq g\circ f$. A function composed with its own inverse gives the identity, $f\big(f^{-1}(x)\big)=x$, on the appropriate domain (Section 2).

Two composites recur: $f(x-k)$ is the graph of $f$ moved $k$ units to the right and $f(x+k)$ is the graph moved $k$ units to the left, for $k>0$. Writing $x^2+2x-3=(x+1)^2-4$ shows that this parabola is $x^2$ moved one unit left and four down, with its minimum at $(-1,-4)$ ([[Completing the Square]]).

## 4. Even, odd and periodic functions (James §2.2.6)

A function is **even** if

$$
f(-x)=f(x)
$$

for every $x$ in its domain, so its graph is symmetric about the $y$-axis. It is **odd** if

$$
f(-x)=-f(x),
$$

so its graph is unchanged by a half-turn about the origin. Putting $x=0$ in the odd condition gives $f(0)=-f(0)$, so an odd function has $f(0)=0$ or is undefined at $0$. Polynomials with only even powers, $\cos x$, $\cosh x$ and $|x|$ are even; polynomials with only odd powers, $\sin x$, $\tan x$, $\sinh x$ and $\tanh x$ are odd. Most functions are neither: a domain that is not symmetric about $0$ rules out both at once.

Products follow the sign rule for $\pm1$. If $f$ and $g$ are both even or both odd, $f(-x)g(-x)=(\pm f)(\pm g)=f(x)g(x)$ and $fg$ is even. If one is even and one is odd, $f(-x)g(-x)=-f(x)g(x)$ and $fg$ is odd. So $x\sin x$ is even and $x^2\sin x$ is odd.

Any function defined on a symmetric domain splits into an even part and an odd part:

$$
f(x)=\underbrace{\tfrac12\big[f(x)+f(-x)\big]}_{\text{even}}+\underbrace{\tfrac12\big[f(x)-f(-x)\big]}_{\text{odd}} .
$$

Replacing $x$ by $-x$ leaves the first bracket unchanged and changes the sign of the second. For $f(x)=e^x$ the two parts are $\frac12(e^x+e^{-x})$ and $\frac12(e^x-e^{-x})$, which are $\cosh x$ and $\sinh x$ (Section 7). For $f(x)=(x-1)^3=x^3-3x^2+3x-1$ they are $-3x^2-1$ and $x^3+3x$.

### Integrals over a symmetric interval

For an odd $f$, split the integral at $0$ and substitute $u=-x$ in the left half:

$$
\begin{aligned}
\int_{-a}^{0}f(x)\,\mathrm dx&=\int_{a}^{0}f(-u)\,(-\mathrm du)\\
&=\int_{0}^{a}f(-u)\,\mathrm du\\
&=-\int_{0}^{a}f(u)\,\mathrm du ,
\end{aligned}
$$

so the two halves cancel and $\int_{-a}^{a}f\,\mathrm dx=0$. For an even $f$ the last line has a plus sign and the halves add:

$$
\int_{-a}^{a}f(x)\,\mathrm dx=2\int_0^af(x)\,\mathrm dx .
$$

For example $\int_{-1}^{1}x^3\cos x\,\mathrm dx=0$ without any integration, since $x^3\cos x$ is odd, and $\int_{-2}^{2}x^2\,\mathrm dx=2\int_0^2x^2\,\mathrm dx=\frac{16}3$.

### Periodic functions

A function is **periodic** with period $P$ if

$$
f(x+P)=f(x)\quad\text{for all }x,
$$

and then $f(x+nP)=f(x)$ for every integer $n$; the period usually means the smallest such $P>0$. The graph is a row of identical strips of width $P$. The **frequency** is $\nu=1/P$, repetitions per unit of $x$, and the circular frequency is $\omega=2\pi\nu=2\pi/P$ in radians per unit of $x$. Since $\sin$ has period $2\pi$, $\sin\omega x$ has period $2\pi/\omega$; for example $\sin3x$ has period $\frac{2\pi}3$.

### Classifying graphs (Example 2.11 and Exercise 14)

Test a graph by reflecting the right half in the $y$-axis. If the result is the left half, the function is even. If the result reflected again in the $x$-axis is the left half, it is odd.

| Graph | Description | Verdict |
|---|---|---|
| Ex 2.11(a) | hump on the $y$-axis between cusps at $x=\pm1$, rising outside | even |
| Ex 2.11(b) | wave with zeros at $0,\pm1,\pm2$, antisymmetric about O | odd |
| Ex 2.11(c) | rising curve through $(0,1)$, asymptotic to the negative $x$-axis, like $e^x$ | neither |
| Ex 2.11(d) | flat top at $y=1$ on $[-1,1]$, zeros at $\pm2$, symmetric | even |
| Ex 2.11(e) | trapezoidal wave not symmetric about $x=0$ | neither |
| Ex 2.11(f) | humps of height $2$ antisymmetric about O | odd |
| Ex 14(a) | through O, minimum for $x<0$, matching maximum for $x>0$ | odd |
| Ex 14(b) | W shape with a local maximum at O | even |
| Ex 14(c) | line of positive slope and positive intercept | neither: $f(0)\neq0$ rules out odd, and a sloping line is not even |
| Ex 14(d) | through O, local maximum at $x<0$, minimum at O, increasing for $x>0$ | neither |
| Ex 14(e) | wave falling through O, maximum just left and minimum just right | odd |
| Ex 14(f) | bell-shaped hump centred on the $y$-axis | even |

### Periodic extensions of a triangle (Example 2.12)

On $[0,1]$ the function is the triangle

$$
f(x)=\begin{cases}3x,&0\leq x\leq\frac13,\\[2pt]\frac32(1-x),&\frac13\leq x\leq1,\end{cases}
$$

with peak $f(\frac13)=1$. Three different functions agree with it on $[0,1]$:

- (a) period 1: copy the triangle onto every interval $[n,n+1]$;
- (b) period 2 and even: define $f(x)=f(-x)$ on $[-1,0]$, which mirrors the triangle, then copy the piece on $[-1,1]$ every 2;
- (c) period 2 and odd: define $f(x)=-f(-x)$ on $[-1,0]$, which gives an inverted triangle, then copy the piece on $[-1,1]$ every 2.

![[m1054_periodic_extensions.png|900]]

The data on $[0,1]$ do not fix the function elsewhere; the symmetry and period chosen do. The even and odd extensions with period $2L$ of a function given on $[0,L]$ are the half-range cosine and sine series of MATH2048 ([[Half-Range Expansions]]).

## 5. Inverse trigonometric functions (James §2.6.7)

Each trigonometric function is periodic, so it fails the horizontal-line test. Each is restricted to one interval on which it is one-to-one and takes all its values, and the inverse is defined on that branch (James calls these the principal values; a calculator returns them):

$$
\begin{aligned}
y=\sin^{-1}x&\iff x=\sin y,\qquad -\tfrac\pi2\leq y\leq\tfrac\pi2,\quad -1\leq x\leq1,\\
y=\cos^{-1}x&\iff x=\cos y,\qquad 0\leq y\leq\pi,\quad -1\leq x\leq1,\\
y=\tan^{-1}x&\iff x=\tan y,\qquad -\tfrac\pi2< y<\tfrac\pi2,\quad x\in\mathbb R .
\end{aligned}
$$

$\sin^{-1}x$ is an angle, the angle in $[-\frac\pi2,\frac\pi2]$ whose sine is $x$; $x$ itself is a number. The cosine branch is $[0,\pi]$ rather than $[-\frac\pi2,\frac\pi2]$ because cosine is even, so it is not one-to-one on any interval symmetric about $0$. The tangent branch is open because $\tan y\to\pm\infty$ as $y\to\pm\frac\pi2$, which gives $\tan^{-1}$ the horizontal asymptotes $y=\pm\frac\pi2$.

| Function | Domain | Range | Increasing or decreasing | Symmetry |
|---|---|---|---|---|
| $\sin^{-1}x$ | $[-1,1]$ | $[-\frac\pi2,\frac\pi2]$ | increasing | odd |
| $\cos^{-1}x$ | $[-1,1]$ | $[0,\pi]$ | decreasing | $\cos^{-1}(-x)=\pi-\cos^{-1}x$ |
| $\tan^{-1}x$ | $\mathbb R$ | $(-\frac\pi2,\frac\pi2)$ | increasing | odd |

![[m1054_m07_inverse_trig_branches.png|900]]

The symmetries follow from the branches. If $y=\sin^{-1}x$ then $\sin(-y)=-x$ with $-y$ still in $[-\frac\pi2,\frac\pi2]$, so $\sin^{-1}(-x)=-\sin^{-1}x$; the same argument works for $\tan^{-1}$. For cosine, if $y=\cos^{-1}x$ then $\cos(\pi-y)=-\cos y=-x$ with $\pi-y$ in $[0,\pi]$, so $\cos^{-1}(-x)=\pi-\cos^{-1}x$. A negative argument therefore gives an obtuse angle for $\cos^{-1}$.

### The identity sin⁻¹x + cos⁻¹x = π/2

Let $\alpha=\sin^{-1}x$, so $\sin\alpha=x$ with $\alpha\in[-\frac\pi2,\frac\pi2]$. Then

$$
\begin{aligned}
\cos\big(\tfrac\pi2-\alpha\big)&=\sin\alpha=x,\\
\tfrac\pi2-\alpha&\in[0,\pi],
\end{aligned}
$$

so $\frac\pi2-\alpha$ is the angle in the cosine branch whose cosine is $x$, which is $\cos^{-1}x$. Hence

$$
\sin^{-1}x+\cos^{-1}x=\frac\pi2,\qquad -1\leq x\leq1 .
$$

### Values on a calculator (Example 2.50)

In radians, to 4 d.p.:

| $x$ | $\sin^{-1}x$ | $\cos^{-1}x$ | $\tan^{-1}x$ |
|---|---|---|---|
| $0.35$ | $0.3576=0.1138\pi$ | $1.2132=0.3862\pi$ | $0.3367=0.1072\pi$ |
| $-0.7$ | $-0.7754$ | $2.3462$ | $-0.6107$ |

Each value lies in its branch: $\cos^{-1}(-0.7)$ is in the second quadrant and $\tan^{-1}(-0.7)$ in the fourth. Also $\tan^{-1}0.35\neq\sin^{-1}0.35/\cos^{-1}0.35$; the inverse functions do not inherit $\tan=\sin/\cos$.

> [!check] Two identities on the table
> In both rows $\sin^{-1}x+\cos^{-1}x=1.5708=\frac\pi2$. Also $\cos^{-1}(-0.7)=\pi-\cos^{-1}(0.7)=3.1416-0.7954=2.3462$.

### Inverse trig of trig: triangular waves (Example 2.51, Exercise 68)

$y=\sin^{-1}(\sin x)$ is defined for every $x$, since $\sin x\in[-1,1]$, but it returns the angle in $[-\frac\pi2,\frac\pi2]$ with the same sine as $x$, which is $x$ only when $x$ is already in that interval. On $[\frac\pi2,\frac{3\pi}2]$, the angle $\pi-x$ lies in $[-\frac\pi2,\frac\pi2]$ and

$$
\sin(\pi-x)=\sin x ,
$$

so $y=\pi-x$ there. The function is odd (both $\sin$ and $\sin^{-1}$ are) and has period $2\pi$ (as $\sin$ does), so

$$
\sin^{-1}(\sin x)=\begin{cases}x,&-\frac\pi2\leq x\leq\frac\pi2,\\[2pt]\pi-x,&\frac\pi2\leq x\leq\frac{3\pi}2,\end{cases}\qquad\text{repeated with period }2\pi,
$$

a triangular wave of amplitude $\frac\pi2$. For example $\sin^{-1}(\sin2)=\pi-2=1.1416$.

For Exercise 68(c), $y=\cos^{-1}(\cos x)$ equals $x$ on the cosine branch $[0,\pi]$. It is even (since $\cos$ is) and has period $2\pi$, so

$$
\cos^{-1}(\cos x)=|x|\quad\text{on }[-\pi,\pi],\qquad\text{repeated with period }2\pi,
$$

a triangular wave between $0$ and $\pi$.

For Exercise 68(a), the identity of the previous subsection with $x$ replaced by $\cos x$ does the work:

$$
\begin{aligned}
\sin^{-1}(\cos x)&=\tfrac\pi2-\cos^{-1}(\cos x)\\
&=\tfrac\pi2-|x|\quad\text{on }[-\pi,\pi],
\end{aligned}
$$

repeated with period $2\pi$: a triangular wave between $-\frac\pi2$ and $\frac\pi2$ with peaks at $x=0,\pm2\pi,\dots$. The same result follows from $\cos x=\sin(\frac\pi2-x)$, since $\frac\pi2-x\in[-\frac\pi2,\frac\pi2]$ when $x\in[0,\pi]$.

![[m1054_inverse_trig_compositions.png|900]]

> [!warning] Composition order matters
> $\sin\big(\sin^{-1}x\big)=x$ for every $x$ in $[-1,1]$, but $\sin^{-1}(\sin x)=x$ only on $[-\frac\pi2,\frac\pi2]$. In the second order the branch restriction acts on the output. The same holds for $\cos^{-1}(\cos x)$, which equals $x$ only on $[0,\pi]$.

### The graph of cos⁻¹x and the value cos⁻¹(−1/2) (Specimen Test 7, Q2)

$\cos^{-1}x$ has domain $[-1,1]$ and range $[0,\pi]$, and decreases from $(-1,\pi)$ through $(0,\frac\pi2)$ to $(1,0)$; the graph has vertical tangents at both ends. Since $\cos\frac{2\pi}3=-\frac12$ and $\frac{2\pi}3\in[0,\pi]$,

$$
\cos^{-1}\big(-\tfrac12\big)=\frac{2\pi}3\approx2.0944 ,
$$

which agrees with $\pi-\cos^{-1}\frac12=\pi-\frac\pi3$.

![[m1054_arccos_specimen.png|560]]

## 6. Exponentials and logarithms (James §2.7.1–2.7.2)

The exponential $e^x$ is defined for all real $x$, is positive and strictly increasing, so it is one-to-one onto $(0,\infty)$. Its inverse is the **natural logarithm**:

$$
y=\ln x\iff x=e^y,\qquad x>0 .
$$

So $\ln e^x=x$ for all real $x$ and $e^{\ln x}=x$ for $x>0$; the graph of $\ln x$ is the reflection of $e^x$ in $y=x$. More generally $y=a^x$ (with $a>0$, $a\neq1$) gives $x=\log_ay$. In James and in engineering, $\log x$ means $\log_{10}x$ and $\ln x$ means $\log_ex$; the `exp` notation, $\exp\{\cdots\}=e^{\cdots}$, is used when the exponent is long.

### The logarithm laws, derived

Let $p=\log_ax$ and $q=\log_ay$, so $x=a^p$ and $y=a^q$. The index laws give

$$
\begin{aligned}
xy&=a^pa^q=a^{p+q}&&\Rightarrow\ \log_a(xy)=\log_ax+\log_ay,\\
\frac xy&=\frac{a^p}{a^q}=a^{p-q}&&\Rightarrow\ \log_a\frac xy=\log_ax-\log_ay,\\
x^n&=(a^p)^n=a^{np}&&\Rightarrow\ \log_ax^n=n\log_ax .
\end{aligned}
$$

For the change of base, let $y=\log_ax$, so $a^y=x$, and take $\log_b$ of both sides:

$$
\begin{aligned}
\log_b\big(a^y\big)&=\log_bx\\
y\log_ba&=\log_bx\\
\log_ax&=\frac{\log_bx}{\log_ba}.
\end{aligned}
$$

The laws hold only where every logarithm in them is defined, so $\ln(x^2y)=2\ln x+\ln y$ needs $x,y>0$; for negative $x$ the correct form is $2\ln|x|+\ln y$.

### Evaluating and simplifying logs (Example 2.57)

(a) $\log_232=\log_22^5=5\log_22=5$.

(b) Using $\log_28=3$ and the quotient law,

$$
\begin{aligned}
\tfrac13\log_28-\log_2\tfrac27&=\tfrac13\cdot3-\big(\log_22-\log_27\big)\\
&=1-1+\log_27\\
&=\log_27\approx2.807 .
\end{aligned}
$$

(c) For $x,y>0$,

$$
\begin{aligned}
\ln\frac{\sqrt{10x}}{y^2}&=\ln\sqrt{10x}-\ln y^2\\
&=\tfrac12\ln(10x)-2\ln y\\
&=\tfrac12\ln10+\tfrac12\ln x-2\ln y .
\end{aligned}
$$

(d) By the change of base with $b=10$, $\dfrac{\log_{10}32}{\log_{10}2}=\log_232=5$.

(e) Change both to base $e$:

$$
\frac{\log_3x}{\log_9x}=\frac{\ln x/\ln3}{\ln x/\ln9}=\frac{\ln9}{\ln3}=\frac{2\ln3}{\ln3}=2,
$$

for $x>0$, $x\neq1$.

### Exercises 75–77 and Specimen Test 7, Q3

For $x,y>0$ (Exercise 75):

$$
\ln(x^2y)=2\ln x+\ln y,\qquad\ln\sqrt{xy}=\tfrac12\ln x+\tfrac12\ln y,\qquad\ln\frac{x^5}{y^2}=5\ln x-2\ln y .
$$

As single logarithms (Exercise 76):

$$
\ln14-\ln21+\ln6=\ln\frac{14\cdot6}{21}=\ln4,\qquad 4\ln2-\tfrac12\ln25=\ln2^4-\ln25^{1/2}=\ln16-\ln5=\ln\tfrac{16}5 .
$$

Exercise 77 uses $e^{\ln u}=u$ after moving each coefficient inside the logarithm as a power. For $-1<x<1$,

$$
\exp\Big\{\tfrac12\ln\frac{1-x}{1+x}\Big\}=\exp\Big\{\ln\Big(\frac{1-x}{1+x}\Big)^{1/2}\Big\}=\sqrt{\frac{1-x}{1+x}},
$$

and for $x>0$, $e^{2\ln x}=e^{\ln x^2}=x^2$. In the same way $\exp\{\frac12\ln u\}=\sqrt u$ for $u>0$.

Specimen Test 7, Q3, for $x>3$:

$$
\begin{aligned}
y&=\exp\big\{\ln x-\tfrac12\ln(x-3)\big\}\\
&=\exp\Big\{\ln x-\ln\sqrt{x-3}\Big\}\\
&=\exp\Big\{\ln\frac{x}{\sqrt{x-3}}\Big\}\\
&=\frac{x}{\sqrt{x-3}} .
\end{aligned}
$$

At $x=7$ both forms give $3.5$.

## 7. Hyperbolic functions (James §2.7.4)

The **hyperbolic cosine** and **hyperbolic sine** are

$$
\cosh x=\frac{e^x+e^{-x}}{2},\qquad\sinh x=\frac{e^x-e^{-x}}{2},
$$

the even and odd parts of $e^x$ (Section 4). The other four are built from them exactly as $\tan$, $\sec$, $\operatorname{cosec}$ and $\cot$ are built from $\cos$ and $\sin$:

$$
\tanh x=\frac{\sinh x}{\cosh x},\qquad\operatorname{sech}x=\frac1{\cosh x},\qquad\operatorname{cosech}x=\frac1{\sinh x}\ (x\neq0),\qquad\coth x=\frac{\cosh x}{\sinh x}\ (x\neq0).
$$

For real $x$, $\cosh x\geq1$, with its minimum $\cosh0=1$, so $\cosh x$ is never zero and $\tanh$ and $\operatorname{sech}$ are defined everywhere. $\sinh$ is odd and strictly increasing with $\sinh0=0$. Dividing through by $e^x$,

$$
\tanh x=\frac{1-e^{-2x}}{1+e^{-2x}},
$$

which tends to $1$ as $x\to\infty$ and, by oddness, to $-1$ as $x\to-\infty$, so $|\tanh x|<1$. For large $|x|$ one exponential dominates: $\cosh x\approx\sinh x\approx\frac12e^x$ as $x\to\infty$.

![[m1054_m07_hyperbolic_graphs.png|900]]

The steady temperature in a straight bar of length $l$ with its ends held at $T_0$ and $T_1$ (a cooling fin) is

$$
T(x)=\frac{T_0\sinh m(l-x)+T_1\sinh mx}{\sinh ml},
$$

where $m$ is a physical constant. It satisfies $T''=m^2T$, $T(0)=T_0$ and $T(l)=T_1$, and it is the same shape as Example 2.58 below.

### The fundamental identity and its geometry

Adding and subtracting the definitions gives

$$
\cosh x+\sinh x=e^x,\qquad\cosh x-\sinh x=e^{-x}.
$$

Multiplying these,

$$
\begin{aligned}
(\cosh x+\sinh x)(\cosh x-\sinh x)&=e^xe^{-x}\\
\cosh^2x-\sinh^2x&=1 .
\end{aligned}
$$

The point $(\cos\theta,\sin\theta)$ lies on the circle $x^2+y^2=1$, and the point $(\cosh t,\sinh t)$ lies on the right branch of the hyperbola $x^2-y^2=1$, which is where the name comes from. In both cases the parameter is twice the area of the shaded sector.

![[m1054_m07_circle_hyperbola.png|860]]

Dividing the identity by $\cosh^2x$ and by $\sinh^2x$ gives the companions of $1+\tan^2=\sec^2$ and $1+\cot^2=\operatorname{cosec}^2$:

$$
1-\tanh^2x=\operatorname{sech}^2x,\qquad\coth^2x-1=\operatorname{cosech}^2x .
$$

### Addition and double-argument formulae

Start from the right-hand side and expand in exponentials:

$$
\begin{aligned}
\sinh x\cosh y&=\tfrac14\big(e^x-e^{-x}\big)\big(e^y+e^{-y}\big)\\
&=\tfrac14\big(e^{x+y}+e^{x-y}-e^{-x+y}-e^{-x-y}\big),\\
\cosh x\sinh y&=\tfrac14\big(e^{x+y}-e^{x-y}+e^{-x+y}-e^{-x-y}\big).
\end{aligned}
$$

Adding, the middle terms cancel:

$$
\sinh x\cosh y+\cosh x\sinh y=\tfrac12\big(e^{x+y}-e^{-(x+y)}\big)=\sinh(x+y).
$$

Subtracting instead gives $\sinh(x-y)$, and the same expansion for products of two cosh or two sinh gives $\cosh(x\pm y)$:

$$
\begin{aligned}
\sinh(x\pm y)&=\sinh x\cosh y\pm\cosh x\sinh y,\\
\cosh(x\pm y)&=\cosh x\cosh y\pm\sinh x\sinh y,\\
\tanh(x\pm y)&=\frac{\tanh x\pm\tanh y}{1\pm\tanh x\tanh y},
\end{aligned}
$$

the last by dividing the first by the second and then dividing top and bottom by $\cosh x\cosh y$. Setting $y=x$:

$$
\sinh2x=2\sinh x\cosh x,\qquad\cosh2x=\cosh^2x+\sinh^2x=1+2\sinh^2x=2\cosh^2x-1 .
$$

These need not be memorised (Module 7 work scheme, item 9), and each is a two-line derivation from the definitions.

### Osborn's rule

To turn a trigonometric identity into a hyperbolic one, replace each trigonometric function by its hyperbolic counterpart and change the sign of every product, or implied product, of two sines. An implied product hides inside $\tan^2x=\sin^2x/\cos^2x$, $\cot^2$ and $\operatorname{cosec}^2$. So $\cos^2x+\sin^2x=1$ becomes $\cosh^2x-\sinh^2x=1$, and $\cos(x+y)=\cos x\cos y-\sin x\sin y$ becomes $\cosh(x+y)=\cosh x\cosh y+\sinh x\sinh y$.

The rule works because of Euler's formula ([[MATH1054 M22 - Complex Numbers II|M22]]). From $\cos\theta=\frac12(e^{\mathrm j\theta}+e^{-\mathrm j\theta})$ and $\sin\theta=\frac1{2\mathrm j}(e^{\mathrm j\theta}-e^{-\mathrm j\theta})$ with $\theta=\mathrm jx$,

$$
\cos\mathrm jx=\tfrac12\big(e^{-x}+e^{x}\big)=\cosh x,\qquad\sin\mathrm jx=\tfrac1{2\mathrm j}\big(e^{-x}-e^{x}\big)=\mathrm j\sinh x .
$$

A trigonometric identity holds for complex arguments too. Substituting $\mathrm jx$ turns each cosine into $\cosh$ and each sine into $\mathrm j\sinh$, so a product of two sines picks up $\mathrm j^2=-1$, which is the sign change. Equivalently $\cosh\mathrm jx=\cos x$ and $\sinh\mathrm jx=\mathrm j\sin x$.

> [!tip] One sign apart
> $\cos$ and $\sin$ solve $y''=-y$; $\cosh$ and $\sinh$ solve $y''=+y$. That single sign is behind every difference between the two families: the minus in $\cosh^2-\sinh^2$, the plus in $\cosh(x+y)$, and the missing minus in $\frac{\mathrm d}{\mathrm dx}\cosh x=\sinh x$.

### Fitting two conditions (Example 2.58)

$f(x)=A\cosh2x+B\sinh2x$ with $f(0)=5$ and $f(1)=0$. Since $\cosh0=1$ and $\sinh0=0$,

$$
f(0)=A=5 .
$$

Then

$$
\begin{aligned}
f(1)=5\cosh2+B\sinh2&=0\\
B&=-\frac{5\cosh2}{\sinh2}=-5\coth2\approx-5.187 .
\end{aligned}
$$

Substituting and using $\sinh(a-b)=\sinh a\cosh b-\cosh a\sinh b$:

$$
\begin{aligned}
f(x)&=5\cosh2x-\frac{5\cosh2}{\sinh2}\sinh2x\\
&=\frac{5}{\sinh2}\big(\sinh2\cosh2x-\cosh2\sinh2x\big)\\
&=\frac{5\sinh(2-2x)}{\sinh2}.
\end{aligned}
$$

The final form shows $f(1)=0$ at a glance.

### Solving a hyperbolic equation (Example 2.59)

Solve $5\cosh x+3\sinh x=4$. Substitute the definitions:

$$
\begin{aligned}
\tfrac52\big(e^x+e^{-x}\big)+\tfrac32\big(e^x-e^{-x}\big)&=4\\
4e^x+e^{-x}&=4\\
4e^{2x}+1&=4e^x\qquad(\times e^x)\\
4e^{2x}-4e^x+1&=0\\
\big(2e^x-1\big)^2&=0 .
\end{aligned}
$$

So $e^x=\frac12$ twice, and

$$
x=\ln\tfrac12=-\ln2\approx-0.6931,
$$

a repeated root. The repeated root has a geometric meaning: $4e^x+e^{-x}=4\cosh(x+\ln2)$, since $4\cosh(x+\ln2)=2\big(2e^x+\frac12e^{-x}\big)$. The left-hand side therefore has minimum value $4$, reached at $x=-\ln2$, and the line $y=4$ touches the curve there rather than crossing it.

![[m1054_m07_ex259_tangency.png|640]]

The general method for $a\cosh x+b\sinh x=c$ is the same: multiply by $e^x$, solve the quadratic in $e^x$, and keep only positive roots, since $e^x>0$.

### Verifying a double-argument identity (Example 2.60)

Show $\tanh2x=\dfrac{2\tanh x}{1+\tanh^2x}$. Put $\tanh x=\dfrac{e^x-e^{-x}}{e^x+e^{-x}}$ and multiply top and bottom by $(e^x+e^{-x})^2$:

$$
\begin{aligned}
\frac{2\tanh x}{1+\tanh^2x}&=\frac{2(e^x-e^{-x})(e^x+e^{-x})}{(e^x+e^{-x})^2+(e^x-e^{-x})^2}\\
&=\frac{2\big(e^{2x}-e^{-2x}\big)}{\big(e^{2x}+2+e^{-2x}\big)+\big(e^{2x}-2+e^{-2x}\big)}\\
&=\frac{2\big(e^{2x}-e^{-2x}\big)}{2\big(e^{2x}+e^{-2x}\big)}\\
&=\tanh2x .
\end{aligned}
$$

By Osborn's rule, $\tan2x=\dfrac{2\tan x}{1-\tan^2x}$ contains the implied product $\tan^2x=\sin^2x/\cos^2x$, so $-\tan^2x$ becomes $+\tanh^2x$ and the rule gives the same identity.

### The other five from one value (Exercise 81 and Specimen Test 7, Q4)

Use $\cosh^2x-\sinh^2x=1$, remembering that $\cosh x>0$ always and that $\sinh x$, $\tanh x$, $\operatorname{cosech}x$ and $\coth x$ have the sign of $x$.

Exercise 81(a), $\cosh x=\frac54$:

$$
\sinh^2x=\tfrac{25}{16}-1=\tfrac9{16},\qquad\sinh x=\pm\tfrac34 .
$$

Both signs occur, because $\cosh$ is even and $x$ and $-x$ give the same $\cosh$. Then $e^x=\cosh x+\sinh x=\frac54\pm\frac34$, so $x=\pm\ln2$.

| $\sinh x$ | $\tanh x$ | $\operatorname{sech}x$ | $\operatorname{cosech}x$ | $\coth x$ |
|---|---|---|---|---|
| $\pm\frac34$ | $\pm\frac35$ | $\frac45$ | $\pm\frac43$ | $\pm\frac53$ |

Exercise 81(e), $\operatorname{cosech}x=-\frac34$: then $\sinh x=-\frac43$, so $x<0$, and

$$
\cosh x=\sqrt{1+\tfrac{16}9}=\tfrac53 .
$$

| $\sinh x$ | $\cosh x$ | $\tanh x$ | $\operatorname{sech}x$ | $\coth x$ |
|---|---|---|---|---|
| $-\frac43$ | $\frac53$ | $-\frac45$ | $\frac35$ | $-\frac54$ |

Here $e^x=\frac53-\frac43=\frac13$, so $x=-\ln3$.

Specimen Test 7, Q4, $\sinh x=-\frac5{12}$:

$$
\cosh x=\sqrt{1+\tfrac{25}{144}}=\sqrt{\tfrac{169}{144}}=\tfrac{13}{12},\qquad\tanh x=\frac{-5/12}{13/12}=-\tfrac5{13},\qquad\operatorname{sech}x=\tfrac{12}{13}.
$$

> [!check] Recovering x
> $e^x=\cosh x+\sinh x=\frac{13}{12}-\frac5{12}=\frac23$, so $x=\ln\frac23=-0.4055$, and a calculator gives $\sinh^{-1}(-\frac5{12})=-0.4055$ and $\cosh(-0.4055)=1.0833=\frac{13}{12}$.

## 8. Inverse hyperbolic functions (James §2.7.5)

$\sinh$ and $\tanh$ are strictly increasing, so they have inverses without restriction. $\cosh$ is even, so it is restricted to $x\geq0$, which makes the range of $\cosh^{-1}$ the non-negative numbers:

$$
\begin{aligned}
y=\sinh^{-1}x&\iff x=\sinh y,\qquad x\in\mathbb R,\\
y=\cosh^{-1}x&\iff x=\cosh y,\qquad x\geq1,\ y\geq0,\\
y=\tanh^{-1}x&\iff x=\tanh y,\qquad -1<x<1 .
\end{aligned}
$$

![[m1054_m07_inverse_hyperbolic.png|900]]

Because the hyperbolic functions are built from $e^y$, each inverse comes out as a logarithm. The three formulae below need not be memorised (Module 7 work scheme, item 10); deriving the first is Specimen Test 7, Q5.

### Logarithmic form of sinh⁻¹x (Specimen Test 7, Q5)

(i) $\sinh y=\frac12\big(e^y-e^{-y}\big)$.

(ii) With $x=\sinh y$:

$$
\begin{aligned}
x&=\tfrac12\big(e^y-e^{-y}\big)\\
2xe^y&=e^{2y}-1\qquad(\times2e^y)\\
\big(e^y\big)^2-2x\,e^y-1&=0 .
\end{aligned}
$$

(iii) This is a quadratic in $e^y$, so

$$
\begin{aligned}
e^y&=\frac{2x\pm\sqrt{4x^2+4}}{2}\\
&=x\pm\sqrt{x^2+1}.
\end{aligned}
$$

Since $\sqrt{x^2+1}>|x|$, the minus sign gives a negative value, which is impossible for $e^y$. Hence $e^y=x+\sqrt{x^2+1}$ and

$$
\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big),\qquad x\in\mathbb R .
$$

### Logarithmic forms of cosh⁻¹x and tanh⁻¹x

For $x=\cosh y$ the same steps give

$$
\begin{aligned}
2xe^y&=e^{2y}+1\\
\big(e^y\big)^2-2x\,e^y+1&=0\\
e^y&=x\pm\sqrt{x^2-1},
\end{aligned}
$$

real for $x\geq1$. This time both roots are positive. Their product is $1$, so they are reciprocals and their logarithms are $\pm\ln\big(x+\sqrt{x^2-1}\big)$, one positive and one negative. The restriction $y\geq0$ picks the plus sign:

$$
\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big),\qquad x\geq1 .
$$

For $x=\tanh y=\dfrac{e^{2y}-1}{e^{2y}+1}$:

$$
\begin{aligned}
x\big(e^{2y}+1\big)&=e^{2y}-1\\
e^{2y}(1-x)&=1+x\\
e^{2y}&=\frac{1+x}{1-x}\\
\tanh^{-1}x&=\frac12\ln\frac{1+x}{1-x},\qquad -1<x<1 .
\end{aligned}
$$

The fraction is positive exactly when $|x|<1$, which matches the range of $\tanh$.

### Values from the log forms (Example 2.61)

To 4 s.f.:

$$
\begin{aligned}
\sinh^{-1}0.5&=\ln\big(0.5+\sqrt{1.25}\big)=\ln1.61803=0.4812,\\
\cosh^{-1}3&=\ln\big(3+\sqrt8\big)=\ln5.82843=1.763,\\
\tanh^{-1}(-0.4)&=\tfrac12\ln\frac{0.6}{1.4}=\tfrac12\ln\tfrac37=-0.4236 .
\end{aligned}
$$

A calculator's `asinh`, `acosh` and `atanh` give the same three values. The other root in $\cosh^{-1}3$, $\ln\big(3-\sqrt8\big)=-1.763$, is the excluded negative branch.

## 9. Derivatives of inverse trigonometric and hyperbolic functions (James §8.3.9, §8.3.12)

### Inverse trigonometric derivatives

Let $y=\sin^{-1}x$ with $|x|<1$, so $x=\sin y$ and $y\in(-\frac\pi2,\frac\pi2)$:

$$
\begin{aligned}
\frac{\mathrm dx}{\mathrm dy}&=\cos y\\
\frac{\mathrm dy}{\mathrm dx}&=\frac1{\cos y}\\
&=\frac1{\sqrt{1-\sin^2y}}\\
&=\frac1{\sqrt{1-x^2}} .
\end{aligned}
$$

The positive root is correct because $\cos y>0$ on $(-\frac\pi2,\frac\pi2)$; the graph of $\sin^{-1}$ is increasing.

Let $y=\cos^{-1}x$, so $x=\cos y$ with $y\in(0,\pi)$, where $\sin y>0$:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac{1}{-\sin y}=-\frac1{\sqrt{1-\cos^2y}}=-\frac1{\sqrt{1-x^2}},\qquad|x|<1 .
$$

This is minus the derivative of $\sin^{-1}x$, as it must be since $\sin^{-1}x+\cos^{-1}x$ is the constant $\frac\pi2$.

Let $y=\tan^{-1}x$, so $x=\tan y$, and use $\sec^2y=1+\tan^2y$:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac1{\sec^2y}=\frac1{1+\tan^2y}=\frac1{1+x^2},\qquad x\in\mathbb R .
$$

Both endpoints $x=\pm1$ are excluded from the first two results because the tangents to $\sin^{-1}$ and $\cos^{-1}$ are vertical there.

### Hyperbolic derivatives

From the definitions,

$$
\frac{\mathrm d}{\mathrm dx}\sinh x=\frac{e^x+e^{-x}}2=\cosh x,\qquad\frac{\mathrm d}{\mathrm dx}\cosh x=\frac{e^x-e^{-x}}2=\sinh x .
$$

There is no minus sign on the second, unlike $\frac{\mathrm d}{\mathrm dx}\cos x=-\sin x$. Only these two are on the formula sheet; the rest follow by the quotient rule and the identity:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\tanh x&=\frac{\cosh x\cosh x-\sinh x\sinh x}{\cosh^2x}=\frac1{\cosh^2x}=\operatorname{sech}^2x,\\
\frac{\mathrm d}{\mathrm dx}\operatorname{sech}x&=\frac{-\sinh x}{\cosh^2x}=-\operatorname{sech}x\tanh x,\\
\frac{\mathrm d}{\mathrm dx}\operatorname{cosech}x&=\frac{-\cosh x}{\sinh^2x}=-\operatorname{cosech}x\coth x,\\
\frac{\mathrm d}{\mathrm dx}\coth x&=\frac{\sinh^2x-\cosh^2x}{\sinh^2x}=-\operatorname{cosech}^2x .
\end{aligned}
$$

> [!warning] Signs that differ from the trigonometric versions
> $\frac{\mathrm d}{\mathrm dx}\cosh x=+\sinh x$ and $\frac{\mathrm d}{\mathrm dx}\operatorname{sech}x=-\operatorname{sech}x\tanh x$, whereas $\frac{\mathrm d}{\mathrm dx}\sec x=+\sec x\tan x$. Derive from the exponentials if unsure.

### Inverse hyperbolic derivatives

Let $y=\sinh^{-1}x$, so $x=\sinh y$, and use $\cosh y=+\sqrt{1+\sinh^2y}$ (cosh is positive):

$$
\frac{\mathrm dy}{\mathrm dx}=\frac1{\cosh y}=\frac1{\sqrt{1+x^2}},\qquad x\in\mathbb R .
$$

Let $y=\cosh^{-1}x$, so $x=\cosh y$ with $y\geq0$, where $\sinh y=+\sqrt{\cosh^2y-1}$:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac1{\sinh y}=\frac1{\sqrt{x^2-1}},\qquad x>1 .
$$

Let $y=\tanh^{-1}x$, so $x=\tanh y$ and $\operatorname{sech}^2y=1-\tanh^2y$:

$$
\frac{\mathrm dy}{\mathrm dx}=\frac1{\operatorname{sech}^2y}=\frac1{1-x^2},\qquad|x|<1 .
$$

Differentiating the log forms of Section 8 gives the same results; for instance

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\ln\big(x+\sqrt{x^2+1}\big)&=\frac{1+\dfrac{x}{\sqrt{x^2+1}}}{x+\sqrt{x^2+1}}\\
&=\frac{\dfrac{\sqrt{x^2+1}+x}{\sqrt{x^2+1}}}{x+\sqrt{x^2+1}}\\
&=\frac1{\sqrt{x^2+1}} .
\end{aligned}
$$

| $f$ | $f'$ | $f$ | $f'$ |
|---|---|---|---|
| $\sin^{-1}x$ | $\dfrac1{\sqrt{1-x^2}}$ | $\sinh x$ | $\cosh x$ |
| $\cos^{-1}x$ | $-\dfrac1{\sqrt{1-x^2}}$ | $\cosh x$ | $\sinh x$ |
| $\tan^{-1}x$ | $\dfrac1{1+x^2}$ | $\tanh x$ | $\operatorname{sech}^2x$ |
| $\sinh^{-1}x$ | $\dfrac1{\sqrt{1+x^2}}$ | $\cosh^{-1}x$ | $\dfrac1{\sqrt{x^2-1}}$ |
| $\tanh^{-1}x$ | $\dfrac1{1-x^2}$ | | |

Read backwards, the table gives the standard integrals used in [[MATH1054 M09 - Integration II|M09]]. With $a>0$ and the chain rule factor $\frac1a$ from $\frac{\mathrm d}{\mathrm dx}\frac xa$,

$$
\int\frac{\mathrm dx}{\sqrt{a^2-x^2}}=\sin^{-1}\frac xa+C,\qquad\int\frac{\mathrm dx}{a^2+x^2}=\frac1a\tan^{-1}\frac xa+C,
$$

$$
\int\frac{\mathrm dx}{\sqrt{x^2+a^2}}=\sinh^{-1}\frac xa+C,\qquad\int\frac{\mathrm dx}{\sqrt{x^2-a^2}}=\cosh^{-1}\frac xa+C\quad(x>a).
$$

For instance $\frac{\mathrm d}{\mathrm dx}\sin^{-1}\frac xa=\frac{1/a}{\sqrt{1-x^2/a^2}}=\frac1{\sqrt{a^2-x^2}}$.

### Inverse trigonometric derivatives with the chain and product rules (Examples 8.17(f)–(h), 8.18(b))

(f) With $z=6x$:

$$
\frac{\mathrm d}{\mathrm dx}\sin^{-1}6x=\frac{1}{\sqrt{1-36x^2}}\cdot6=\frac{6}{\sqrt{1-36x^2}},\qquad|x|<\tfrac16 .
$$

(g) By the product rule:

$$
\frac{\mathrm d}{\mathrm dx}\big(x^2\cos^{-1}x\big)=2x\cos^{-1}x-\frac{x^2}{\sqrt{1-x^2}} .
$$

(h) With $z=\dfrac{2x}{1+x^2}$, the quotient rule gives

$$
\frac{\mathrm dz}{\mathrm dx}=\frac{2(1+x^2)-2x\cdot2x}{(1+x^2)^2}=\frac{2(1-x^2)}{(1+x^2)^2},
$$

and

$$
1+z^2=\frac{(1+x^2)^2+4x^2}{(1+x^2)^2}=\frac{x^4+6x^2+1}{(1+x^2)^2},
$$

so

$$
\frac{\mathrm d}{\mathrm dx}\tan^{-1}\frac{2x}{1+x^2}=\frac{1}{1+z^2}\frac{\mathrm dz}{\mathrm dx}=\frac{2(1-x^2)}{x^4+6x^2+1} .
$$

8.18(b) uses the extended chain rule with $z=1-x^2$ and $w=\sqrt z$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\cos^{-1}\sqrt{1-x^2}&=\frac{-1}{\sqrt{1-w^2}}\cdot\frac{1}{2\sqrt z}\cdot(-2x)\\
&=\frac{-1}{\sqrt{x^2}}\cdot\frac{-x}{\sqrt{1-x^2}}\\
&=\frac{x}{|x|\sqrt{1-x^2}} ,
\end{aligned}
$$

using $1-w^2=x^2$ and $\sqrt{x^2}=|x|$. This is $+\frac1{\sqrt{1-x^2}}$ for $0<x<1$ and $-\frac1{\sqrt{1-x^2}}$ for $-1<x<0$, and there is no derivative at $x=0$. The reason: for $0\leq x\leq1$, $\cos^{-1}\sqrt{1-x^2}=\sin^{-1}x$, and the function is even, so it equals $|\sin^{-1}x|$, which has a corner at $0$.

### Hyperbolic derivatives with the chain and product rules (Example 8.20)

(a) $\dfrac{\mathrm d}{\mathrm dx}\tanh2x=2\operatorname{sech}^22x$.

(b) $\dfrac{\mathrm d}{\mathrm dx}\cosh^2x=2\cosh x\sinh x=\sinh2x$.

(c) By the product rule, then $\cosh u-\sinh u=e^{-u}$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\big(e^{-3x}\sinh3x\big)&=-3e^{-3x}\sinh3x+3e^{-3x}\cosh3x\\
&=3e^{-3x}\big(\cosh3x-\sinh3x\big)\\
&=3e^{-3x}e^{-3x}\\
&=3e^{-6x} .
\end{aligned}
$$

Equivalently $e^{-3x}\sinh3x=\frac12\big(1-e^{-6x}\big)$, whose derivative is $3e^{-6x}$ directly.

(d) With $u=\frac{3x}4$:

$$
\frac{\mathrm d}{\mathrm dx}\sinh^{-1}\frac{3x}4=\frac{3/4}{\sqrt{1+9x^2/16}}=\frac{3/4}{\tfrac14\sqrt{16+9x^2}}=\frac{3}{\sqrt{16+9x^2}} .
$$

### Exercises 35, 40 and 41

Exercise 35(a):

$$
\frac{\mathrm d}{\mathrm dx}\sin^{-1}\frac x2=\frac{1/2}{\sqrt{1-x^2/4}}=\frac{1}{\sqrt{4-x^2}},\qquad|x|<2 .
$$

Exercise 35(c), by the product rule with $\frac{\mathrm d}{\mathrm dx}\sqrt{1+x^2}=\frac{x}{\sqrt{1+x^2}}$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\Big[\sqrt{1+x^2}\,\tan^{-1}x\Big]&=\frac{x\tan^{-1}x}{\sqrt{1+x^2}}+\frac{\sqrt{1+x^2}}{1+x^2}\\
&=\frac{1+x\tan^{-1}x}{\sqrt{1+x^2}} .
\end{aligned}
$$

Exercise 35(f), by the product rule:

$$
\frac{\mathrm d}{\mathrm dx}\Big[\sqrt{1-x^2}\,\sin^{-1}x\Big]=-\frac{x\sin^{-1}x}{\sqrt{1-x^2}}+\frac{\sqrt{1-x^2}}{\sqrt{1-x^2}}=1-\frac{x\sin^{-1}x}{\sqrt{1-x^2}} .
$$

Exercise 40(c) and (d):

$$
\frac{\mathrm d}{\mathrm dx}\big(x^3\cosh2x\big)=3x^2\cosh2x+2x^3\sinh2x,\qquad\frac{\mathrm d}{\mathrm dx}\ln\big(\cosh\tfrac12x\big)=\frac{\tfrac12\sinh\tfrac12x}{\cosh\tfrac12x}=\tfrac12\tanh\tfrac12x .
$$

Exercise 41(a): $\dfrac{\mathrm d}{\mathrm dx}\sinh^{-1}2x=\dfrac{2}{\sqrt{1+4x^2}}$.

Exercise 41(b): $\cosh^{-1}(2x^2-1)$ needs $2x^2-1\geq1$, that is $|x|\geq1$. For $|x|>1$,

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dx}\cosh^{-1}(2x^2-1)&=\frac{4x}{\sqrt{(2x^2-1)^2-1}}\\
&=\frac{4x}{\sqrt{4x^4-4x^2}}\\
&=\frac{4x}{2|x|\sqrt{x^2-1}},
\end{aligned}
$$

which is $\dfrac{2}{\sqrt{x^2-1}}$ for $x>1$ and $-\dfrac{2}{\sqrt{x^2-1}}$ for $x<-1$. The result is simple because $\cosh2u=2\cosh^2u-1$ makes $\cosh^{-1}(2x^2-1)=2\cosh^{-1}|x|$.

### Specimen Test 7, Q6

$$
\frac{\mathrm d}{\mathrm dx}\tan^{-1}4x=\frac{4}{1+(4x)^2}=\frac{4}{1+16x^2},\qquad\frac{\mathrm d}{\mathrm dx}\big(x^3\sinh x\big)=3x^2\sinh x+x^3\cosh x .
$$

> [!check] Symbolic check
> Every derivative in this section, and each log form of Section 8 against the built-in `asinh`, `acosh` and `atanh`, was checked with SymPy; the differences simplify to $0$. Exercise 41(b) gives $1.7889=2/\sqrt{1.25}$ at $x=1.5$ and $-1.7889$ at $x=-1.5$.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| $\sin^{-1}x$, $\cos^{-1}x$, $\tan^{-1}x$ | $\arcsin x$, $\arccos x$, $\arctan x$; `asin`, `acos`, `atan` in MATLAB | James uses both; the $-1$ is never a reciprocal |
| $\sinh^{-1}x$, $\cosh^{-1}x$, $\tanh^{-1}x$ | $\operatorname{arsinh}x$ etc. (James); `asinh`, `acosh`, `atanh` in MATLAB; `arcsinh` in Maple | arsinh, not arcsinh: the output is an area (twice a hyperbolic sector), not an arc |
| range | image set | the outputs actually reached; the codomain may be larger |
| one-to-one | 1:1, injective | the condition for an inverse to exist |
| $\ln x$ | $\log_ex$; $\log x$ in pure mathematics | in James and in engineering, $\log x$ means $\log_{10}x$ |
| principal value | principal branch | the value a calculator returns |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M07 Solutions - Functions]]
- Previous: [[MATH1054 M06 - Differential Equations I]] · Prerequisite (chain, product and quotient rules): [[MATH1054 M03 - Differentiation I]] · Next: [[MATH1054 M08 - Differentiation II]]
- Concepts: [[Inverse Functions]] · [[Even, Odd and Periodic Functions]] · [[Inverse Trigonometric Functions]] · [[Hyperbolic Functions]] · [[Product, Quotient and Chain Rules]] · [[Completing the Square]]
- Later in MATH1054: the integrals $\int\frac{\mathrm dx}{\sqrt{a^2-x^2}}$, $\int\frac{\mathrm dx}{a^2+x^2}$ and $\int\frac{\mathrm dx}{\sqrt{x^2\pm a^2}}$ in [[MATH1054 M09 - Integration II]] and [[Integration by Substitution]]; $A\cosh kx+B\sinh kx$ as the solution of $y''=k^2y$ in [[MATH1054 M12 - Differential Equations II]]; $\cosh\mathrm jx=\cos x$, $\sinh\mathrm jx=\mathrm j\sin x$ and complex hyperbolic functions in [[MATH1054 M22 - Complex Numbers II]], [[Euler's Formula]] and [[Complex Functions - Trig, Hyperbolic and Logarithm]]
- Year 2: even and odd functions and half-range series in [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]] and [[Half-Range Expansions]]; cosh and sinh solutions in [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]; sinh in the separated solutions of [[MATH2048 PDE5 - Laplace's Equation]]; transforms of cosh and sinh in [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]

## Sources

- MATH1054 Module Booklet, Module 7 work scheme and Specimen Test 7 (booklet pp. 1–3 of Module 7, PDF pp. 16–18)
- James, *Modern Engineering Mathematics* (6th ed.): §2.1; §2.2.1 (Examples 2.1, 2.3); §2.2.3 (Examples 2.6–2.8); §2.2.4 (Example 2.9); §2.2.6 (Examples 2.11, 2.12); §2.6.7 (Examples 2.50, 2.51); §2.7.1–2.7.2 (Example 2.57); §2.7.4 (Examples 2.58–2.60, Osborn's rule); §2.7.5 (Example 2.61); §8.3.9 below eq. (8.18) (Examples 8.17(f)–(h), 8.18(b)); §8.3.12 (eqs 8.24–8.25, Example 8.20)
- Worked solutions to every example and exercise: [[MATH1054 M07 Solutions - Functions]]

## Self-study tasks

### Core

- [ ] Exercises 10(a),(c) (Module 07 work scheme): inverses, and a domain restriction for $x^2+1$. → [[#Restricting the domain (Example 2.8(c) and Exercise 10)]] · [[MATH1054 M07 Solutions - Functions#Exercise 10(a),(c) (pp.81–82): Inverses|solution]]
- [ ] Exercises 68(a),(c) (Module 07 work scheme, marked hard): sketch $\sin^{-1}(\cos x)$ and $\cos^{-1}(\cos x)$. → [[#Inverse trig of trig: triangular waves (Example 2.51, Exercise 68)]] · [[MATH1054 M07 Solutions - Functions#Exercise 68 (p.149) (harder): Sketches|solution]]
- [ ] Exercises 81(a),(e) (Module 07 work scheme): the other five hyperbolic functions from one value. → [[#The other five from one value (Exercise 81 and Specimen Test 7, Q4)]] · [[MATH1054 M07 Solutions - Functions#Exercise 81(a),(e): Find the other five hyperbolic functions|solution]]
- [ ] Exercises 35(a),(c),(f) and 41(a),(b) (Module 07 work scheme): inverse trigonometric and inverse hyperbolic derivatives. → [[#Exercises 35, 40 and 41]] · [[MATH1054 M07 Solutions - Functions#Exercise 35(a),(c),(f) (p.586): Inverse-trig derivatives|35]] · [[MATH1054 M07 Solutions - Functions#Exercise 41(a),(b) (p.591)|41]]
- [ ] Specimen Test 7, Q1–Q6, timed (about 30 minutes). → [[MATH1054 M07 Solutions - Functions#Part C: Specimen Test 7|solutions]]

### Further practice

- [ ] Exercise 14 (Module 07 work scheme): odd, even or neither from six graphs. → [[#Classifying graphs (Example 2.11 and Exercise 14)]] · [[MATH1054 M07 Solutions - Functions#Exercise 14 (p.87): Odd or even (Fig. 2.27)|solution]]
- [ ] Exercises 75, 76, 77 (Module 07 work scheme): logarithm laws. → [[#Exercises 75–77 and Specimen Test 7, Q3]] · [[MATH1054 M07 Solutions - Functions#Exercise 75: Log expansions|75]] · [[MATH1054 M07 Solutions - Functions#Exercise 76: Single logarithm|76]] · [[MATH1054 M07 Solutions - Functions#Exercise 77: Simplify|77]]
- [ ] Exercises 40(c),(d) (Module 07 work scheme): hyperbolic derivatives. → [[#Exercises 35, 40 and 41]] · [[MATH1054 M07 Solutions - Functions#Exercise 40(c),(d) (p.591)|solution]]
- [ ] Examples 2.58–2.61 (Module 07 work scheme): rework without notes, then check. → [[#Solving a hyperbolic equation (Example 2.59)]] · [[MATH1054 M07 Solutions - Functions#Example 2.61: Inverse hyperbolics via logs (4 s.f.)|2.61 solution]]
- [ ] Examples 8.17(f)–(h), 8.18(b) and 8.20 (Module 07 work scheme): chain and product rules with inverse and hyperbolic functions. → [[MATH1054 M07 Solutions - Functions#Example 8.17(f)–(h) and 8.18(b): Inverse-trig derivatives|8.17–8.18]] · [[MATH1054 M07 Solutions - Functions#Example 8.20: Hyperbolic derivatives|8.20]]

## Transcript and slide slips

> [!warning] Textbook and booklet slips
> | Where | Printed | Correct |
> |---|---|---|
> | [[#Domain and range of two formulae (Example 2.1)]]: James Example 2.1(b), p. 66 | largest value $f(-\frac12)=\sqrt{35}/2$, range $[0,\sqrt{35}/2]$ | $f(-\frac12)=\sqrt{\frac72\cdot\frac72}=\frac72$, range $[0,\frac72]$ |
> | [[#Celsius to Fahrenheit (Example 2.3)]]: James Example 2.3(a),(d), p. 67 | absolute zero $-273.16\,$°C, range $T_2>-459.69\,$°F | absolute zero is $-273.15\,$°C ($273.16$ K is the triple point of water), so $T_2\geq-459.67\,$°F |
> | Module 7 work scheme, item 10 and item 12 | Exercises 75–77 "on p.157", Exercise 35 "on p.590" | in the PDF edition they are on p. 155 (§2.7.3) and p. 586 (§8.3.11) |

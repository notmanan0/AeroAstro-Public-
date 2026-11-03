---
title: "MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 3: Fourier and Laplace Transforms"
order: 9
tags:
  - math2048
  - laplace-transform
  - heaviside
  - dirac-delta
aliases: ["MATH2048 Lecture 13", "Second shift theorem", "Impulse response"]
date: 2026-10-30
status: lectured
coverage: "Lecture 13 (28 Oct 2024, Ian Hawke): the Heaviside function and switching on and off, the Dirac delta and its sifting property, the transforms of both, the second shift theorem and its proof, y'' + y = H(x - 1), and a pendulum struck by a hammer every pi seconds."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
next_topics: ["[[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]"]
key_concepts: ["[[Heaviside Step Function]]", "[[Dirac Delta Function]]", "[[Laplace Transform Properties and Proofs]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 13.txt", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Appendix-Laplace Transform_additional slides.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§4.5, §4.7)"]
---

# MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem

> [!abstract] Summary
> Sources that switch on or off suddenly are built from the Heaviside function $H(x-a)$, and sources that act in an instant from the Dirac delta $\delta(x-a)$. Their transforms are $\frac{e^{-as}}{s}$ and $e^{-as}$, and the second shift theorem $\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s)$ says how to invert anything carrying a factor $e^{-as}$: invert the rest, then delay it by $a$ and switch it on at $a$. Every recent exam's question A1 is an IVP of this kind, often with the proof of the theorem as part (a).

> [!summary]- Exam use: quick path
> - **Use it when:** the ODE's right-hand side contains $H(x-a)$, $\delta(x-a)$, or a piecewise source that can be written with them; or you are asked to prove the second shift theorem (2025/26 A1(a), 5 marks).
> - **Assumptions:** $a>0$, so the switch or impulse happens inside $0<x<\infty$; $\mathrm{Re}\,s>0$; initial conditions at $x=0$.
> - **Method:** 1. Rewrite each source term in the form $g(x-a)H(x-a)$. 2. Transform; substitute the initial conditions. 3. Solve for $\tilde y$ and group terms by their $e^{-as}$ factor. 4. Partial-fraction each group, ignoring the exponential. 5. Invert each group, replace $x$ by $x-a$ and multiply by $H(x-a)$.
> - **Common mistakes:** treating $f(x)H(x-a)$ as if it were $f(x-a)H(x-a)$; inverting $e^{-as}\tilde f$ to $f(x)H(x-a)$ without shifting the argument of $f$.
> - **Practise:** [[#Switching on a constant force (L13)]] · [[#The 2025-26 exam, question A1]] · [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms|PS5 Q3(e)–(h), Q4]]

This is the lecture where the Laplace transform earns its place (ll. 1–29). The sources of interest are of two kinds. Some do nothing and then suddenly do something, or the reverse, like a current switched on or off. Others act at a single instant, like the force on a ball as it bounces off a wall: the velocity flips sign instantly, so the force that does it acts only at the moment of contact. That second kind is the derivative of the first. The methods of ODE1–ODE2 assume the source is smooth enough to differentiate, which is exactly what these sources are not. An integral transform doesn't care, because integration smooths things out: it adds regularity where differentiation removes it.

The chapter needs two functions. The Heaviside function is a unit step, and by scaling, shifting and multiplying it any piecewise-continuous source can be built; the Dirac delta is a unit impulse. Once their transforms are known, the only new tool needed is the second shift theorem, and the delta then needs no extra work at all (ll. 321–354).

---

## 1. The Heaviside function (L13)

$$
H(x-a)=\begin{cases}0,&x<a,\\1,&x>a.\end{cases}
$$

It is named after Oliver Heaviside, the nineteenth-century engineer (ll. 38–52). Changing the argument from $x$ to $x-a$ moves the switch to $x=a$, multiplying by a constant changes the height, and from there any discontinuous function can be assembled (ll. 53–116):

| Construction | What it does |
|---|---|
| $H(x+1)-H(x-1)$ | 1 on $-1<x<1$, 0 outside: on at $-1$, off at $1$ |
| $f(x)\,H(x-a)$ | $f$ switched on at $a$ |
| $f(x)\,[1-H(x-a)]$ | $f$ switched off at $a$ |
| $f(x)\,[H(x-a)-H(x-b)]$ | $f$ on only for $a<x<b$ |

The first row is the lecture's sketch: left of $-1$ both functions are 0, between $-1$ and $1$ only the first is 1, and right of $1$ both are 1 and cancel.

### Its Laplace transform

Take $a>0$, so the switch is inside the range of integration (ll. 151–178). For $x<a$ the integrand is zero, and for $x>a$ the Heaviside function is 1, so

$$
\mathcal L[H(x-a)]=\int_0^\infty H(x-a)e^{-sx}\,dx=\int_a^\infty e^{-sx}\,dx .
$$

Integrate the exponential:

$$
\int_a^\infty e^{-sx}\,dx=\left[-\frac{e^{-sx}}{s}\right]_a^\infty .
$$

The upper limit vanishes provided $\mathrm{Re}\,s>0$, and the lower limit cancels the minus sign:

$$
\mathcal L[H(x-a)]=\frac{e^{-as}}{s}.
$$

With $a=0$ this is $\mathcal L[1]=\frac1s$, as it should be, since $H(x)=1$ for all $x>0$.

## 2. The second shift theorem (L13)

$$
\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s),\qquad a>0 .
$$

Both arguments are $x-a$ (ll. 186–192). That is the natural way to state it, and other forms can be reduced to it by redefining the variable.

### Proof

This is the proof asked for in 2025/26 A1(a). Start from the definition (ll. 193–220):

$$
\mathcal L[f(x-a)H(x-a)]=\int_0^\infty f(x-a)H(x-a)e^{-sx}\,dx .
$$

The Heaviside function is 0 for $x<a$ and 1 for $x>a$, so it can be removed by raising the lower limit:

$$
=\int_a^\infty f(x-a)e^{-sx}\,dx .
$$

Substitute $\tau=x-a$, so $d\tau=dx$, $x=a$ becomes $\tau=0$, and $x\to\infty$ becomes $\tau\to\infty$ because $a$ is finite:

$$
=\int_0^\infty f(\tau)e^{-s(\tau+a)}\,d\tau .
$$

The factor $e^{-sa}$ contains no $\tau$, so it comes out of the integral:

$$
=e^{-sa}\int_0^\infty f(\tau)e^{-s\tau}\,d\tau=e^{-as}\tilde f(s).\qquad\blacksquare
$$

### Using it to invert

The theorem matters most in reverse (ll. 222–239):

$$
\mathcal L^{-1}\big[e^{-as}\tilde f(s)\big]=f(x-a)H(x-a).
$$

When a Heaviside source is transformed, $\tilde y$ ends up as rational functions of $s$, some multiplied by exponentials in $s$. The rational parts are handled by partial fractions and the table, as in TR2. The exponential is not something to invert directly. Factor it out, invert what is left to get $f(x)$, and then the exponent $-as$ tells you to replace $x$ by $x-a$ everywhere and multiply by $H(x-a)$. The result is the same response, delayed until $x=a$ and switched off before it.

![[m2048_tr_second_shift.png|620]]

Questions often give a source as $f(x)H(x-a)$ instead, with an unshifted $f$. Rewrite it so the argument is $x-a$ before transforming. In 2023/24 A1, $e^xH(x-1)=e\cdot e^{x-1}H(x-1)$, so its transform is $e\cdot\frac{e^{-s}}{s-1}$. Similarly $\sin x\,H(x-\pi)=-\sin(x-\pi)H(x-\pi)$, whose transform is $-\frac{e^{-\pi s}}{s^2+1}$. The general version, proved the same way, is $\mathcal L[f(x)H(x-a)]=e^{-as}\mathcal L[f(x+a)]$.

> [!check] SymPy
> `laplace_transform` gives $\frac{e^{-2s}}{s}$ for $H(x-2)$, $\frac{e^{1-s}}{s-1}$ for $e^xH(x-1)$, $\frac{e^{-s}}{s^2+1}$ for $\sin(x-1)H(x-1)$ and $-\frac{e^{-\pi s}}{s^2+1}$ for $\sin x\,H(x-\pi)$.

### Switching on a constant force (L13)

Solve $y''+y=H(x-1)$ with $y(0)=0$, $y'(0)=1$ (ll. 240–313). Before $x=1$ this is the unforced oscillator kicked from rest, whose solution is $\sin x$ (TR2). At $x=1$ a constant force switches on. The pendulum should keep swinging with the same period, but now about a displaced position.

Transform both sides:

$$
s^2\tilde y-sy(0)-y'(0)+\tilde y=\frac{e^{-s}}{s}.
$$

Substitute $y(0)=0$, $y'(0)=1$:

$$
(s^2+1)\tilde y=1+\frac{e^{-s}}{s}.
$$

Solve:

$$
\tilde y=\frac1{s^2+1}+e^{-s}\,\frac1{s(s^2+1)} .
$$

Partial fractions on the second fraction, ignoring the exponential (ll. 268–271), give $\frac1{s(s^2+1)}=\frac1s-\frac s{s^2+1}$, so

$$
\tilde y=\frac1{s^2+1}+e^{-s}\Big(\frac1s-\frac s{s^2+1}\Big).
$$

Now invert term by term from the formula sheet (ll. 272–306). $\frac1{s^2+1}$ is $\mathcal L[\sin x]$. The bracket is $\mathcal L[1-\cos x]$, and the factor $e^{-s}$ means $a=1$, so by the second shift theorem the whole second term is $\mathcal L\big[(1-\cos(x-1))H(x-1)\big]$. Hence

$$
y=\sin x+H(x-1)\big[1-\cos(x-1)\big].
$$

For $x<1$ this is $\sin x$, the expected free swing. After $x=1$ the extra term oscillates with the same period but a phase lag, starting the moment the force switches on (ll. 307–313).

![[m2048_tr_lecture13_solutions.png|900]]

> [!check] Continuity at the switch
> For $x>1$, $y''+y=1$ is satisfied exactly, and the extra term $1-\cos(x-1)$ and its derivative $\sin(x-1)$ are both zero at $x=1$. So $y$ and $y'$ are continuous through the switch; only $y''$ jumps, by the size of the step. SymPy's `inverse_laplace_transform` gives the same $y$.

The lecture's summary of the method (ll. 314–319): transforming the ODE turns each Heaviside source into an exponential on the right-hand side; after solving for $\tilde y$, some terms keep their exponentials; inverting those terms needs the second shift theorem and produces Heaviside functions in the answer.

## 3. The Dirac delta (L13)

The Dirac delta is badly named, because it is not a function (ll. 118–143). It is a functional: something that acts on a function and returns a number, and it only makes sense inside an integral. Its definition is what it does there:

$$
\int_a^b\delta(x-c)f(x)\,dx=\begin{cases}f(c),&a<c<b,\\0,&c\text{ outside }[a,b].\end{cases}
$$

It picks out the value of the function it multiplies at the point where its argument is zero, provided that point is inside the range of integration. This is called the sifting property.

You will often see $\delta$ described as zero everywhere except at the origin, where it is infinite. The lecturer called this "a very bad way of thinking about it" (l. 37). A slightly better picture is a sequence of narrower and taller rectangles, each with area 1, so that integrating any of them against $f$ gives approximately $f(0)$, and taking the limit (ll. 136–140). That picture is fine for intuition but not for calculation: always use the definition (ll. 141–143). The delta is the derivative of the Heaviside function in this sense, which is what makes it the model of an impulse, such as a hammer blow that changes momentum in an instant.

### Its Laplace transform

With $a>0$, the argument $x-a$ is zero somewhere in $0<x<\infty$, so the sifting property applies straight away, with no integral left to do (ll. 325–339):

$$
\mathcal L[\delta(x-a)]=\int_0^\infty\delta(x-a)e^{-sx}\,dx=e^{-sa}.
$$

More generally, $\mathcal L[\delta(x-a)f(x)]=f(a)e^{-sa}$, because the delta picks out the value of everything else in the integrand (ll. 341–343). If $a<0$ the argument never vanishes in the range and the transform is just zero (ll. 344–346). The formula sheet's entry $\mathcal L[\delta(x)]=1$ is the convention for $a=0$.

The same sifting idea simplifies a source before transforming: $g(x)\delta(x-a)=g(a)\delta(x-a)$. PS5 Q3(h) uses this to replace $\delta(x-2\pi)\cos x$ by $\delta(x-2\pi)$.

Compared with the Heaviside function, this is the same exponential without the $\frac1s$, and it is exactly the kind of term the second shift theorem already inverts (ll. 347–354). So delta sources need no new mathematics, even though the solutions they produce behave quite differently.

### A pendulum struck by a hammer (L13)

A pendulum hangs at rest, $y(0)=\dot y(0)=0$ (ll. 355–436). At $t=0$ a hammer strikes it from the left, giving it a positive velocity. It is left alone until $t=\pi$, when the hammer strikes again, and again at $2\pi$, $3\pi$ and so on:

$$
\ddot y+y=\sum_{n=0}^\infty\delta(t-n\pi).
$$

Transform. The initial values are both zero, and linearity takes the transform through the sum:

$$
(s^2+1)\tilde y=\sum_{n=0}^\infty e^{-n\pi s}.
$$

Solve:

$$
\tilde y=\sum_{n=0}^\infty e^{-n\pi s}\,\frac1{s^2+1}.
$$

Each term is an exponential times $\mathcal L[\sin t]$, so the second shift theorem with $a=n\pi$ inverts it to $H(t-n\pi)\sin(t-n\pi)$:

$$
y=\sum_{n=0}^\infty H(t-n\pi)\sin(t-n\pi).
$$

Every time $t$ passes a multiple of $\pi$, another sine switches on, with the same period but a different phase lag (ll. 415–430). Using $\sin(t-n\pi)=(-1)^n\sin t$, the sum is $\sin t$ on $(0,\pi)$; on $(\pi,2\pi)$ the new term $-\sin t$ cancels it and $y=0$; on $(2\pi,3\pi)$ another $+\sin t$ switches on, and so on. The strikes are perfectly timed: the second blow arrives just as the pendulum swings back through the bottom with velocity $-1$, and the impulse of $+1$ stops it dead. The next blow starts it again (right panel of the figure above).

> [!warning] Mistimed strikes don't make it diverge
> The lecture ends by saying that slightly mistimed strikes would give constructive interference and "the solution would tend to diverge off to infinity" (ll. 433–435). That is only true for strikes about a whole period apart. With spacing $\tau$, the first $N$ strikes give $\sum_{n<N}\sin(t-n\tau)$, whose amplitude is $\big|\sin\frac{N\tau}2\big|/\big|\sin\frac\tau2\big|\leq1/\big|\sin\frac\tau2\big|$. For $\tau$ near $\pi$ that bound is about 1, so the motion stays bounded. The amplitude grows without bound only when $\tau$ is a multiple of $2\pi$, when every strike arrives in phase: resonance with an impulsive source. A simulation of 60 periods gives a peak of 1.00 for $\tau=0.95\pi$, 6.39 for $\tau=1.9\pi$ and 30 (one per strike) for $\tau=2\pi$.

### The 2025-26 exam, question A1

Solve $y''+2y'+2y=\delta(x-13)$ with $y(0)=y'(0)=0$. Transform, with zero initial data:

$$
(s^2+2s+2)\tilde y=e^{-13s}.
$$

Complete the square in the denominator:

$$
\tilde y=e^{-13s}\,\frac1{(s+1)^2+1}.
$$

Without the exponential, $\frac1{(s+1)^2+1}$ is $\mathcal L[\sin x]$ with $s$ replaced by $s+1$, so by the first shift theorem it inverts to $e^{-x}\sin x$. The factor $e^{-13s}$ then delays this by 13:

$$
y=H(x-13)\,e^{-(x-13)}\sin(x-13).
$$

Nothing happens until the impulse at $x=13$, after which the system rings down as a decaying oscillation. This is its impulse response. The question asks you to name each theorem as you use it, here the first and second shift theorems. SymPy's inversion gives the same $y$.

## Transcript slips

> [!warning] Lecture 13
> | Where | Transcript says | Correct |
> |---|---|---|
> | l. 137 | integrating against the rectangle "gives you precisely the function at f equals to 0" | $f(0)$, the function at $x=0$ |
> | l. 162 | "let us assume that x is greater than a" | corrected at l. 163 to $a>0$ |
> | l. 172 | "0 to infinity, a to infinity" | the limits are $a$ to $\infty$ (corrected in passing) |
> | l. 299 | "Plath transform" | Laplace transform |
> | l. 423 | $\sin(t-\pi)=-\sin t$ "using the double angle formula" | the compound-angle formula $\sin(A-B)=\sin A\cos B-\cos A\sin B$ |
> | l. 428 | "sine of T minus 2 pi is just sine of pi" | $\sin(t-2\pi)=\sin t$ |
> | ll. 433–435 | slightly mistimed strikes make the solution diverge | only spacings near a multiple of $2\pi$ do; see the warning above |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]] · Next: [[MATH2048 PDE1 - Classification of PDEs and the Wave Equation]]
- Concepts: [[Heaviside Step Function]] · [[Dirac Delta Function]] · [[Laplace Transform Properties and Proofs]] · [[Partial Fractions for Inverse Laplace]]
- The same step and impulse inputs in control: [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]

## Sources

- Lecture 13 (28 Oct 2024) recording, Ian Hawke: `MATH2048 Lecture 13.txt`
- Slides `Lecture13_LaplaceTransform3.pdf` and the additional appendix slides; lecture notes §4.5 and §4.7
- Problem Sheet 5 Q3(e)–(h) and Q4, worked in [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]; past papers 2023/24 and 2025/26 question A1

## Self-study tasks

Nothing was explicitly set in Lecture 13. The lecturer's closing advice was that the things you need are "all the trigonometric identities and the partial fractions" (ll. 437–438). The tasks below are the problem-sheet and past-paper questions on this lecture.

### Core

- [ ] Prove the second shift theorem from the definition, as in 2025/26 A1(a). → [[#Proof]]
- [ ] Rework $y''+y=H(x-1)$, $y(0)=0$, $y'(0)=1$ without notes and check that $y$ and $y'$ are continuous at $x=1$. → [[#Switching on a constant force (L13)]]
- [ ] PS5 Q3(g): $2y''+y'+2y=\delta(x-5)$, $y(0)=y'(0)=0$. Answer: $y=\frac2{\sqrt{15}}H(x-5)e^{-(x-5)/4}\sin\big(\frac{\sqrt{15}}4(x-5)\big)$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] 2025/26 A1(b): $y''+2y'+2y=\delta(x-13)$, zero initial data. → [[#The 2025-26 exam, question A1]]

### Further practice

- [ ] PS5 Q3(e), (f) and (h): a sine switched off at $2\pi$, a unit force on for $0<x<10$, and $y''+y=\delta(x-2\pi)\cos x$. Answers: $\big(\frac13\sin x-\frac16\sin2x\big)[1-H(x-2\pi)]$; $g(x)-H(x-10)g(x-10)$ with $g=\frac12-e^{-x}+\frac12e^{-2x}$; $\sin x\,[1+H(x-2\pi)]$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] PS5 Q4: the damped impulse response $y''+\gamma y'+y=k\delta(x-1)$ and the kick $k_1$ needed for a peak of 2. Answers: $k_1=2.8108$, $2.3995$, $2$ for $\gamma=\frac12,\frac14,0$. → [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [ ] Redo the hammer problem with strikes every $2\pi$ and show the amplitude after $N$ strikes is $N$ (suggested, not lecturer-set). → [[#A pendulum struck by a hammer (L13)]]

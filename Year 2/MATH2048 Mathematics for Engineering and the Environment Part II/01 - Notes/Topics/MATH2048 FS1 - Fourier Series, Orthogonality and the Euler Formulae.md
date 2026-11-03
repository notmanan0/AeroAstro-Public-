---
title: "MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 4
tags:
  - math2048
  - fourier-series
  - orthogonality
aliases: ["MATH2048 Lecture 4", "MATH2048 Lecture 5", "Euler formulae (Fourier)"]
date: 2026-10-30
status: lectured
coverage: "Lectures 4 and 5 (7–8 Oct 2024, Ian Hawke): Fourier series against Taylor series, periodicity, the values of sin and cos at multiples of π, the orthogonality relations and the Euler formulae derived; the sawtooth (f = x) and tent (f = |x|) by brute force, and summing a series by evaluating at a point."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
next_topics: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
key_concepts: ["[[Fourier Series]]", "[[Orthogonality of Trigonometric Functions]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 4.txt", "02 - Sources/Lectures/MATH2048 Lecture 5.txt", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture4_FourierSeries1.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture5_FourierSeries2.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (Ch. 2)"]
---

# MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae

> [!abstract] Summary
> A Fourier series represents a periodic function as a constant plus an infinite sum of sines and cosines, $f(x)\sim\frac12a_0+\sum_{n\geq1}(a_n\cos nx+b_n\sin nx)$ for period $2\pi$. The coefficients come from orthogonality: multiply by one sine or cosine, integrate over a period, and every term but one vanishes, which gives the Euler formulae $a_n=\frac1\pi\int_{-\pi}^{\pi}f\cos nx\,dx$ and $b_n=\frac1\pi\int_{-\pi}^{\pi}f\sin nx\,dx$. In practice a coefficient is an integration by parts plus the two facts $\sin n\pi=0$ and $\cos n\pi=(-1)^n$.

> [!summary]- Exam use: quick path
> - **Use it when:** a function on a bounded interval has to be written as sines and cosines, most often to fit the initial data in a separation-of-variables PDE (A2), or to sum a series like $\sum1/n^2$.
> - **Assumptions:** $f$ is extended periodically outside the interval; period $2\pi$ here (general period $2L$ in [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence|FS2]]); $n$ and $m$ are integers.
> - **Method:** 1. Sketch $f$ and its periodic extension. 2. $a_0=\frac1\pi\int_{-\pi}^\pi f\,dx$ separately. 3. $a_n$ and $b_n$ by parts, differentiating the polynomial and integrating the trig function. 4. Use $\sin n\pi=0$, $\cos n\pi=(-1)^n$. 5. Write the series with $\frac12a_0$ and the dummy index $n$.
> - **Common mistakes:** forgetting the $\frac12$ on $a_0$ in the series; computing $a_0$ from the general $a_n$ formula after dividing by $n$, which fails at $n=0$.
> - **Practise:** [[#The tent function]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|PS2 (Fourier series) Q2]]

A Fourier series writes a complicated function in terms of simple ones, sines and cosines, because they are easy to work with: differentiate a sine and you get a cosine, differentiate a cosine and you get minus a sine, and that's it (L4, ll. 36–47). In this module the point is to plug them into differential equations, and in signal processing it is to talk about frequencies.

The lecturer compared it with the Taylor series (ll. 55–110). A Taylor series builds a function from its value and derivatives at one point, so it describes local behaviour well and can fail far from that point. A Fourier series builds the function from its averages against sines and cosines over the whole domain, so when it converges it converges everywhere, which makes it the tool for global behaviour. The coefficients play the same role in both: $f^{(n)}(0)/n!$ multiplies $x^n$ in one, and $a_n$ or $b_n$ multiplies $\cos nx$ or $\sin nx$ in the other.

The restriction is periodicity: every term repeats every $2\pi$ (the $n=2$ term repeats twice in that length, the $n=3$ term three times), so the series can only represent a periodic function. That is less of a restriction than it sounds (ll. 155–179): physical problems live on bounded domains, a domain of any length can be rescaled to length $2\pi$, and the function can then be treated as if copied periodically along the whole line. The coefficients are found by the same trick each time, orthogonality, which the lecturer compared to an orthogonal basis of vectors whose pairwise dot products are zero unless the vectors are the same (L5, ll. 19–22).

---

## 1. The series and the values you will use constantly (L4)

For a $2\pi$-periodic function, $f(x+2\pi)=f(x)$, the Fourier series is

$$
f(x)\sim\frac12a_0+\sum_{n=1}^{\infty}\big(a_n\cos nx+b_n\sin nx\big).
$$

The symbol $\sim$ means "is represented by" rather than "equals": we assume the two agree, calculate the coefficients, and check afterwards, because there are points where they don't (ll. 205–211). A function given only on $(-\pi,\pi)$ is understood to be extended periodically, copied along every $2\pi$.

Every coefficient calculation ends with sines and cosines evaluated at multiples of $\pi$, and the lecturer stressed these "over and over again" (ll. 180–193):

| For integer $n$ | Value |
|---|---|
| $\sin n\pi$ | $0$ |
| $\cos n\pi$ | $(-1)^n$ |
| $\sin\big(n+\tfrac12\big)\pi$ | $(-1)^n$ |
| $\cos\big(n+\tfrac12\big)\pi$ | $0$ |
| $1-(-1)^n$ | $0$ for $n$ even, $2$ for $n$ odd |

## 2. Orthogonality (L4)

For integers $m,n\geq1$,

$$
\int_{-\pi}^{\pi}\sin mx\sin nx\,dx=\pi\delta_{mn},\qquad\int_{-\pi}^{\pi}\cos mx\cos nx\,dx=\pi\delta_{mn},\qquad\int_{-\pi}^{\pi}\sin mx\cos nx\,dx=0,
$$

where the Kronecker delta $\delta_{mn}$ is 1 when $m=n$ and 0 otherwise. In words, the integral of two sines (or two cosines) over a period is zero unless their periods match exactly, and a sine against a cosine always gives zero.

### The sine–sine relation, derived

The lecture derived the first relation from the addition formulae (ll. 226–318). Start from

$$
\cos(A+B)=\cos A\cos B-\sin A\sin B .
$$

Replace $B$ by $-B$, using $\cos(-B)=\cos B$ (even) and $\sin(-B)=-\sin B$ (odd):

$$
\cos(A-B)=\cos A\cos B+\sin A\sin B .
$$

Subtract the first from the second:

$$
\cos(A-B)-\cos(A+B)=2\sin A\sin B .
$$

With $A=mx$, $B=nx$:

$$
\sin mx\sin nx=\tfrac12\big[\cos(m-n)x-\cos(m+n)x\big].
$$

For $m\neq n$, integrate over the symmetric range:

$$
\int_{-\pi}^{\pi}\sin mx\sin nx\,dx=\frac12\left[\frac{\sin(m-n)x}{m-n}-\frac{\sin(m+n)x}{m+n}\right]_{-\pi}^{\pi}=0,
$$

because $m\pm n$ is an integer, so every term is the sine of an integer multiple of $\pi$. The symmetric range is the convention because it guarantees exactly that; any range of length $2\pi$ gives the same answer, but the arithmetic is messier (ll. 254–282).

For $m=n$ the step above divides by zero, so it needs a separate calculation, the lecturer's admission that he had "pulled the wool over your eyes" (ll. 284–292). From $\cos2A=1-2\sin^2A$,

$$
\sin^2mx=\tfrac12(1-\cos2mx),
$$

so

$$
\int_{-\pi}^{\pi}\sin^2mx\,dx=\frac12\left[x-\frac{\sin2mx}{2m}\right]_{-\pi}^{\pi}=\frac12\big(\pi-(-\pi)\big)=\pi .
$$

The cosine–cosine relation comes the same way from adding the two formulae, and the sine–cosine one from the addition formula for sine (ll. 319–324); PS2 (Fourier series) Q1 asks for all three on $[-L,L]$.

## 3. The Euler formulae (L4)

To extract one coefficient from the infinite sum, multiply both sides by the matching trigonometric function and integrate over a period (ll. 212–221, 327–428).

**The constant.** Integrate the series term by term, pulling the constants through:

$$
\int_{-\pi}^{\pi}f\,dx=\frac12a_0\int_{-\pi}^{\pi}dx+\sum_{n=1}^\infty\Big(a_n\int_{-\pi}^{\pi}\cos nx\,dx+b_n\int_{-\pi}^{\pi}\sin nx\,dx\Big).
$$

Evaluate each integral:

$$
=\frac12a_0\big[x\big]_{-\pi}^{\pi}+\sum_{n=1}^\infty\Big(a_n\Big[\frac{\sin nx}{n}\Big]_{-\pi}^{\pi}+b_n\Big[-\frac{\cos nx}{n}\Big]_{-\pi}^{\pi}\Big).
$$

The sines vanish at $\pm n\pi$, and $\cos nx$ takes the same value $(-1)^n$ at both ends, so only the first term survives:

$$
\int_{-\pi}^{\pi}f\,dx=\pi a_0 .
$$

**The cosine coefficients.** Multiply by $\cos mx$ for a fixed integer $m\geq1$ and integrate:

$$
\int_{-\pi}^{\pi}f\cos mx\,dx=\frac12a_0\int_{-\pi}^{\pi}\cos mx\,dx+\sum_{n=1}^\infty\Big(a_n\int_{-\pi}^{\pi}\cos mx\cos nx\,dx+b_n\int_{-\pi}^{\pi}\cos mx\sin nx\,dx\Big).
$$

The first integral is zero, the last is zero by orthogonality, and the middle one is $\pi\delta_{mn}$:

$$
=\sum_{n=1}^\infty a_n\pi\delta_{mn}=\pi a_m .
$$

The sum runs over every $n$, but $m$ is one fixed integer, so exactly one term survives (ll. 409–419). Multiplying by $\sin mx$ instead picks out $b_m$ in the same way. The results are the **Euler formulae**:

$$
a_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\cos nx\,dx\quad(n\geq0),\qquad b_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\sin nx\,dx\quad(n\geq1).
$$

The $a_n$ formula also gives $a_0$, because $\cos0=1$; that is the reason for the convention of writing $\frac12a_0$ in the series, so that one formula covers both (ll. 425–428). In calculations, though, $a_0$ usually has to be done separately, because the general $a_n$ result typically has $n$ in a denominator.

$\frac12a_0=\frac1{2\pi}\int_{-\pi}^{\pi}f\,dx$ is the average of $f$ over a period, and the sines and cosines carry the fluctuations about that average, since each integrates to zero on its own (L5, ll. 84–92).

## 4. Worked examples by brute force (L5)

The lecture deliberately computed both examples without using symmetry, to show the mechanics; FS2 shows how symmetry halves the work (L5, ll. 42–44, 122–124).

### The sawtooth, f = x

Take $f(x)=x$ on $(-\pi,\pi)$, extended periodically, which gives a sawtooth with a jump at every odd multiple of $\pi$ (ll. 51–78).

The constant:

$$
a_0=\frac1\pi\int_{-\pi}^{\pi}x\,dx=\frac1\pi\Big[\frac{x^2}2\Big]_{-\pi}^{\pi}=\frac1{2\pi}\big(\pi^2-\pi^2\big)=0,
$$

as it must be, since $f$ is as much negative as positive (ll. 93–107).

For $a_m$, integrate by parts with $u=x$ (which differentiates away) and $v'=\cos mx$ (which never would) (ll. 126–158). The rule $\int uv'=[uv]-\int u'v$ gives

$$
a_m=\frac1\pi\left(\Big[\frac{x\sin mx}{m}\Big]_{-\pi}^{\pi}-\int_{-\pi}^{\pi}\frac{\sin mx}{m}\,dx\right)
$$

$$
=\frac1\pi\Big[\frac{x\sin mx}{m}+\frac{\cos mx}{m^2}\Big]_{-\pi}^{\pi}
$$

$$
=\frac1\pi\left(0+\frac{(-1)^m}{m^2}-\frac{(-1)^m}{m^2}\right)=0 .
$$

The lecturer's bookkeeping tip is to keep each trigonometric term with its own power of $m$, $\sin$ over $m$, $\cos$ over $m^2$, then $\sin$ over $m^3$ and so on, rather than pulling out common factors, because the alternating pattern catches lost powers (ll. 175–186).

For $b_m$, the same parts with $v'=\sin mx$:

$$
b_m=\frac1\pi\left(\Big[-\frac{x\cos mx}{m}\Big]_{-\pi}^{\pi}+\int_{-\pi}^{\pi}\frac{\cos mx}{m}\,dx\right)
$$

$$
=\frac1\pi\Big[-\frac{x\cos mx}{m}+\frac{\sin mx}{m^2}\Big]_{-\pi}^{\pi}
$$

$$
=-\frac1\pi\left(\frac{\pi(-1)^m}{m}-\frac{(-\pi)(-1)^m}{m}\right)=-\frac{2(-1)^m}{m}=\frac{2(-1)^{m+1}}{m}.
$$

So

$$
x\sim\sum_{n=1}^\infty\frac{2(-1)^{n+1}}{n}\sin nx=2\Big(\sin x-\frac{\sin2x}{2}+\frac{\sin3x}{3}-\dots\Big),
$$

relabelling $m$ as the summation index $n$ (ll. 238–242).

![[m2048_fs_sawtooth_gibbs.png|680]]

Truncating the series gives a usable approximation: in the lecture's plot four terms are already within about a per cent away from the jumps, and eight are better still (ll. 247–266). Near the jumps the partial sums overshoot, the Gibbs phenomenon.

### The tent function

Now take $f(x)=|x|$ on $(-\pi,\pi)$, whose periodic extension is a triangle wave, the "tent" (ll. 267–309). For integrating, the piecewise form is easier than the absolute value:

$$
f(x)=\begin{cases}-x,&-\pi\leq x<0,\\ x,&0\leq x\leq\pi.\end{cases}
$$

The constant splits into the two pieces:

$$
a_0=\frac1\pi\left(\int_{-\pi}^{0}(-x)\,dx+\int_0^{\pi}x\,dx\right)=\frac1\pi\left(\Big[-\frac{x^2}2\Big]_{-\pi}^0+\Big[\frac{x^2}2\Big]_0^{\pi}\right)=\frac1\pi\left(\frac{\pi^2}2+\frac{\pi^2}2\right)=\pi,
$$

which is twice the average value $\pi/2$, as expected (ll. 311–341).

For $a_m$ the indefinite integral is the sawtooth's, so reuse it rather than integrating again (ll. 342–357):

$$
a_m=\frac1\pi\left(-\Big[\frac{x\sin mx}{m}+\frac{\cos mx}{m^2}\Big]_{-\pi}^{0}+\Big[\frac{x\sin mx}{m}+\frac{\cos mx}{m^2}\Big]_0^{\pi}\right).
$$

The sines vanish at $0$ and $\pm m\pi$, and the cosines now give non-zero values at $x=0$ as well:

$$
a_m=\frac1\pi\left(-\frac{1-(-1)^m}{m^2}+\frac{(-1)^m-1}{m^2}\right)=\frac{2}{\pi m^2}\big((-1)^m-1\big),
$$

which is $0$ for even $m$ and $-4/(\pi m^2)$ for odd $m$ (ll. 363–382). The $b_m$ all vanish, left as a check in the lecture (ll. 384–390) and explained by symmetry in FS2. So

$$
|x|\sim\frac\pi2-\frac4\pi\sum_{n\ \mathrm{odd}}\frac{\cos nx}{n^2}=\frac\pi2-\frac4\pi\Big(\cos x+\frac{\cos3x}{9}+\frac{\cos5x}{25}+\dots\Big).
$$

![[m2048_fs_tent_convergence.png|680]]

This series converges much faster than the sawtooth's, with coefficients falling as $1/n^2$ rather than $1/n$, because the tent is continuous; four terms are already close everywhere except at the corners (ll. 396–399).

> [!check] SymPy
> Integrating directly gives $a_0=0$, $a_n=0$, $b_n=-2(-1)^n/n$ for $f=x$, and $a_0=\pi$, $a_n=2((-1)^n-1)/(\pi n^2)$, $b_n=0$ for $f=|x|$.

## 5. Summing series by evaluating at a point (L5)

A Fourier series is an identity, so it can be evaluated at any convenient point, and that often produces the value of an infinite sum (ll. 400–423). At $x=0$ the tent series gives $|0|=0$ on the left and $\cos0=1$ in every term on the right:

$$
0=\frac\pi2-\frac4\pi\sum_{n\ \mathrm{odd}}\frac1{n^2}.
$$

Rearrange:

$$
\sum_{n\ \mathrm{odd}}\frac1{n^2}=1+\frac19+\frac1{25}+\dots=\frac{\pi^2}{8}.
$$

The lecturer's comment was that most of the neat infinite sums in formula books were found exactly this way, and that this is why they turn up in exam questions: take the series, pick a point where the terms simplify, evaluate both sides and rearrange (ll. 416–423). The point has to be one where the series converges to $f$ itself; at a jump of the periodic extension it converges to the average of the two sides instead (FS2).

## Transcript slips

> [!warning] Lectures 4 and 5
> | Where | Transcript says | Correct |
> |---|---|---|
> | L4, l. 1 | "Furrier Series" | Fourier series |
> | L4, l. 222 | "chronica symbol" | Kronecker delta |
> | L4, l. 244 | "times sine of A times sine of minus B" | $-\sin A\sin(-B)$, which becomes $+\sin A\sin B$ |
> | L4, l. 363 | "the sum… of a zero times" | $a_n$ times $[\sin nx/n]$ |
> | L4, l. 375 | "minus 1 to the power pi" | $(-1)^n$ |
> | L5, ll. 23, 32, 41 | "Sturm-Ueyville", "Sturm-Lewel", "Sturm-Moeval" | Sturm–Liouville (not examinable) |
> | L5, l. 287 | "the tenth function" | the tent function (likewise elsewhere in L6–L7) |
> | L5, l. 399 | "the yellow term is also converging" | the green (eight-term) curve; yellow is the exact function |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · Next: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- The sines and cosines are the eigenfunctions of $y''+\lambda y=0$ with periodic conditions on $[-\pi,\pi]$ ([[ODE Eigenvalue Problems]]); Sturm–Liouville theory generalises this (L5, ll. 23–41, not examinable).
- Concepts: [[Fourier Series]] · [[Orthogonality of Trigonometric Functions]]

## Sources

- Lecture 4 (7 Oct 2024) and Lecture 5 (8 Oct 2024) recordings, Ian Hawke: `MATH2048 Lecture 4.txt`, `MATH2048 Lecture 5.txt`
- Slides `Lecture4_FourierSeries1.pdf`, `Lecture5_FourierSeries2.pdf`; lecture notes Ch. 2
- Problem Sheet 2 (Fourier series page) and Problem Sheet 3; worked solutions in [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

## Self-study tasks

Lecture 4 left the cosine–cosine and sine–cosine orthogonality relations to the students (ll. 319–325), and Lecture 5 left the tent's $b_n$ as a check (ll. 384–390). The lecturer also opened Lecture 4 with a STACK warning: always check the list of variables STACK says it recognised, use explicit `*` for multiplication and `exp()` for the exponential (ll. 1–26).

### Core

- [ ] Lecturer-set (L4, ll. 319–325): derive the cosine–cosine and sine–cosine orthogonality relations, including the $m=n$ cases. This is PS2 (Fourier series) Q1 on $[-L,L]$. → [[#2. Orthogonality (L4)]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|solution]]
- [ ] Lecturer-set (L5, ll. 384–390): show directly that all $b_n=0$ for $f=|x|$. → [[#The tent function]]
- [ ] PS2 (Fourier series) Q2: the Fourier series of $1+x$ on $[-2,2]$. → [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

### Further practice

- [ ] PS3 Q1(a)–(c): the real Fourier series of $e^x$ on $(-\pi,\pi)$ and its values at $0,\pm\frac\pi2,\pm\pi$. Answer: $a_n=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)}$, $b_n=-\frac{2(-1)^nn\sinh\pi}{\pi(1+n^2)}$. → [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|solution]]
- [ ] Evaluate the sawtooth series at $x=\pi/2$ to show $1-\frac13+\frac15-\dots=\frac\pi4$ (suggested, not lecturer-set). → [[#The sawtooth, f = x]]
- [ ] Derive the Euler formula for $b_m$ by multiplying by $\sin mx$ (suggested, not lecturer-set). → [[#3. The Euler formulae (L4)]]

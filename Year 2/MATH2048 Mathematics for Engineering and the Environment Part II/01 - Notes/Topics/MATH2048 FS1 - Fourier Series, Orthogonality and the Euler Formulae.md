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

A Fourier series writes a complicated function in terms of simple ones, sines and cosines, because they are easy to work with: differentiate a sine and you get a cosine, differentiate a cosine and you get minus a sine, so the family is closed under differentiation (L4, ll. 36–47). For differential equations the point is to plug them in, and in signal processing it is to talk about frequencies.

A Taylor series builds a function from its value and derivatives at one point, so it describes local behaviour well and can fail far from that point. A Fourier series, by contrast, builds the function from its averages against sines and cosines over the whole domain, so for a function meeting the Dirichlet conditions it converges at every point of the period, which makes it the tool for global behaviour. The coefficients play the same role in both: $f^{(n)}(0)/n!$ multiplies $x^n$ in one, and $a_n$ or $b_n$ multiplies $\cos nx$ or $\sin nx$ in the other.

The restriction is periodicity: every term repeats every $2\pi$ (the $n=2$ term repeats twice in that length, the $n=3$ term three times), so the series can only represent a periodic function. That is less of a restriction than it sounds (ll. 155–179): physical problems live on bounded domains, a domain of any length can be rescaled to length $2\pi$, and the function can then be treated as if copied periodically along the whole line. The coefficients are found by the same method each time, orthogonality, which works like an orthogonal basis of vectors whose pairwise dot products are zero unless the vectors are the same.

---

## 1. The series and the values you will use constantly (L4)

For a $2\pi$-periodic function, $f(x+2\pi)=f(x)$, the Fourier series is

$$
f(x)\sim\frac12a_0+\sum_{n=1}^{\infty}\big(a_n\cos nx+b_n\sin nx\big).
$$

The symbol $\sim$ means "is represented by" rather than "equals": the two are assumed to agree, the coefficients calculated and the agreement checked afterwards, because there are points where they don't (ll. 205–211). A function given only on $(-\pi,\pi)$ is understood to be extended periodically, copied along every $2\pi$.

Every coefficient calculation ends with sines and cosines evaluated at multiples of $\pi$, so learn these values:

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

Derive the first relation from the addition formulae (ll. 226–318). Start from

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

For $m=n$ the step above divides by zero, so it needs a separate calculation. From $\cos2A=1-2\sin^2A$,

$$
\sin^2mx=\tfrac12(1-\cos2mx),
$$

so

$$
\int_{-\pi}^{\pi}\sin^2mx\,dx=\frac12\left[x-\frac{\sin2mx}{2m}\right]_{-\pi}^{\pi}=\frac12\big(\pi-(-\pi)\big)=\pi .
$$

### The cosine–cosine and sine–cosine relations

These two follow the same pattern as the sine–sine relation (ll. 319–324). Adding the two cosine formulae instead of subtracting them gives

$$
\cos(A-B)+\cos(A+B)=2\cos A\cos B,
$$

so

$$
\cos mx\cos nx=\tfrac12\big[\cos(m-n)x+\cos(m+n)x\big].
$$

For $m\neq n$ both terms integrate to sines of integer multiples of $\pi$:

$$
\int_{-\pi}^{\pi}\cos mx\cos nx\,dx=\frac12\left[\frac{\sin(m-n)x}{m-n}+\frac{\sin(m+n)x}{m+n}\right]_{-\pi}^{\pi}=0 .
$$

For $m=n\geq1$, use $\cos2A=2\cos^2A-1$, so $\cos^2mx=\tfrac12(1+\cos2mx)$:

$$
\int_{-\pi}^{\pi}\cos^2mx\,dx=\frac12\left[x+\frac{\sin2mx}{2m}\right]_{-\pi}^{\pi}=\pi .
$$

For the mixed relation, add $\sin(A+B)=\sin A\cos B+\cos A\sin B$ and $\sin(A-B)=\sin A\cos B-\cos A\sin B$:

$$
\sin(A+B)+\sin(A-B)=2\sin A\cos B,
$$

$$
\sin mx\cos nx=\tfrac12\big[\sin(m+n)x+\sin(m-n)x\big].
$$

Each sine is odd, so its integral over the symmetric range $(-\pi,\pi)$ is zero whatever $m$ and $n$ are, including $m=n$, where the second term is $\sin0=0$:

$$
\int_{-\pi}^{\pi}\sin mx\cos nx\,dx=0 .
$$

This one needs no separate $m=n$ case, which is why the third relation has no Kronecker delta. PS2 (Fourier series) Q1 asks for all three on $[-L,L]$; replacing $x$ by $\pi x/L$ and $dx$ by $\pi\,dx/L$ turns each $\pi$ into $L$.

![[m2048_fs_orthogonality_products.png|820]]

A product of two different harmonics oscillates about zero with equal positive and negative area, while the square of one harmonic never goes negative and averages $\tfrac12$, which over a length $2\pi$ gives $\pi$.

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

The sum runs over every $n$, but $m$ is one fixed integer, so exactly one term survives (ll. 409–419).

**The sine coefficients.** Multiply by $\sin mx$ instead:

$$
\int_{-\pi}^{\pi}f\sin mx\,dx=\frac12a_0\int_{-\pi}^{\pi}\sin mx\,dx+\sum_{n=1}^\infty\Big(a_n\int_{-\pi}^{\pi}\sin mx\cos nx\,dx+b_n\int_{-\pi}^{\pi}\sin mx\sin nx\,dx\Big).
$$

The first integral is zero (an odd function over a symmetric range), the second is zero by the mixed relation, and the third is $\pi\delta_{mn}$:

$$
=\sum_{n=1}^\infty b_n\pi\delta_{mn}=\pi b_m .
$$

The results are the **Euler formulae**:

$$
a_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\cos nx\,dx\quad(n\geq0),\qquad b_n=\frac1\pi\int_{-\pi}^{\pi}f(x)\sin nx\,dx\quad(n\geq1).
$$

The $a_n$ formula also gives $a_0$, because $\cos0=1$; that is the reason for the convention of writing $\frac12a_0$ in the series, so that one formula covers both (ll. 425–428). In calculations, though, $a_0$ usually has to be done separately, because the general $a_n$ result typically has $n$ in a denominator.

$\frac12a_0=\frac1{2\pi}\int_{-\pi}^{\pi}f\,dx$ is the average of $f$ over a period, and the sines and cosines carry the fluctuations about that average, since each integrates to zero on its own (L5, ll. 84–92).

## 4. Worked examples by brute force (L5)

Both examples are computed without using symmetry, which would halve the work (FS2; L5, ll. 42–44, 122–124).

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

Each trigonometric term is best kept with its own power of $m$, $\sin$ over $m$, $\cos$ over $m^2$, then $\sin$ over $m^3$ and so on, rather than pulling out common factors, because the alternating pattern catches lost powers.

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

Truncating the series gives an approximation that improves with every term, but slowly, because the coefficients fall only as $1/n$ (ll. 247–266). At $x=1$ the partial sums with 4, 8 and 50 terms are $1.246$, $0.896$ and $0.995$. Near the jumps the partial sums overshoot, the Gibbs phenomenon, and adding terms squeezes the overshoot towards the jump without shrinking it.

> [!check] The Gibbs overshoot
> The maximum of the partial sum just left of $x=\pi$ is $3.414$ with 10 terms, $3.642$ with 50 and $3.688$ with 200. The jump is $2\pi$, so the overshoot above $\pi$ is $4.3\%$, $8.0\%$ and $8.7\%$ of the jump, approaching the limiting $8.95\%$ instead of zero.

### The tent function

Take $f(x)=|x|$ on $(-\pi,\pi)$, whose periodic extension is a triangle wave, the "tent" (ll. 267–309). For integrating, the piecewise form is easier than the absolute value:

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

which is $0$ for even $m$ and $-4/(\pi m^2)$ for odd $m$ (ll. 363–382).

The $b_m$ come out as zero (ll. 384–390). The indefinite integral of $x\sin mx$ is the sawtooth's,

$$
F(x)=-\frac{x\cos mx}{m}+\frac{\sin mx}{m^2},
$$

with $F(0)=0$, $F(\pi)=-\pi(-1)^m/m$ and $F(-\pi)=\pi(-1)^m/m$, since every sine vanishes. Split the integral at $0$:

$$
b_m=\frac1\pi\left(\int_{-\pi}^{0}(-x)\sin mx\,dx+\int_0^{\pi}x\sin mx\,dx\right)
$$

$$
=\frac1\pi\Big(-\big[F(0)-F(-\pi)\big]+\big[F(\pi)-F(0)\big]\Big)
$$

$$
=\frac1\pi\big(F(-\pi)+F(\pi)\big)
$$

$$
=\frac1\pi\left(\frac{\pi(-1)^m}{m}-\frac{\pi(-1)^m}{m}\right)=0 .
$$

The contributions of the two halves cancel exactly (by symmetry, FS2). So

$$
|x|\sim\frac\pi2-\frac4\pi\sum_{n\ \mathrm{odd}}\frac{\cos nx}{n^2}=\frac\pi2-\frac4\pi\Big(\cos x+\frac{\cos3x}{9}+\frac{\cos5x}{25}+\dots\Big).
$$

![[m2048_fs_tent_convergence.png|680]]

This series converges much faster than the sawtooth's, with coefficients falling as $1/n^2$ rather than $1/n$, because the tent is continuous; a few terms are already close everywhere except at the corners (ll. 396–399). The worst error sits at the corners $x=0,\pm\pi$, and with 1, 2 and 4 non-zero cosine terms it is $0.298$, $0.156$ and $0.079$, roughly halving each time the number of terms doubles.

> [!check] SymPy
> Integrating directly gives $a_0=0$, $a_n=0$, $b_n=-2(-1)^n/n$ for $f=x$, and $a_0=\pi$, $a_n=2((-1)^n-1)/(\pi n^2)$, $b_n=0$ for $f=|x|$.

### The exponential, e to the x (PS3 Q1)

A function with no symmetry at all needs both families of coefficients. Take $f(x)=e^x$ on $(-\pi,\pi)$, extended periodically, which jumps from $e^{\pi}$ down to $e^{-\pi}$ at every odd multiple of $\pi$.

The constant:

$$
a_0=\frac1\pi\int_{-\pi}^{\pi}e^x\,dx=\frac{e^{\pi}-e^{-\pi}}{\pi}=\frac{2\sinh\pi}{\pi}.
$$

For $a_n$ and $b_n$, integration by parts never removes the exponential, but doing it twice brings the original integral back, which can then be solved for. Let $C=\int e^x\cos nx\,dx$ and $S=\int e^x\sin nx\,dx$. Integrate by parts with $e^x$ as the part to integrate:

$$
C=e^x\cos nx+n\int e^x\sin nx\,dx=e^x\cos nx+nS,
$$

$$
S=e^x\sin nx-n\int e^x\cos nx\,dx=e^x\sin nx-nC .
$$

Substitute the second into the first:

$$
C=e^x\cos nx+ne^x\sin nx-n^2C,
$$

$$
(1+n^2)C=e^x\big(\cos nx+n\sin nx\big).
$$

Evaluate between $-\pi$ and $\pi$, where $\sin n\pi=0$ and $\cos n\pi=(-1)^n$:

$$
\int_{-\pi}^{\pi}e^x\cos nx\,dx=\frac{(-1)^n\big(e^{\pi}-e^{-\pi}\big)}{1+n^2}=\frac{2(-1)^n\sinh\pi}{1+n^2}.
$$

The same substitution the other way round gives $(1+n^2)S=e^x(\sin nx-n\cos nx)$, so

$$
\int_{-\pi}^{\pi}e^x\sin nx\,dx=\frac{-n(-1)^n\big(e^{\pi}-e^{-\pi}\big)}{1+n^2}=-\frac{2n(-1)^n\sinh\pi}{1+n^2}.
$$

Dividing by $\pi$,

$$
a_n=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)},\qquad b_n=-\frac{2n(-1)^n\sinh\pi}{\pi(1+n^2)},
$$

and the $n=0$ case of the $a_n$ formula reproduces $a_0$, so here the general formula does cover the constant. The series is

$$
e^x\sim\frac{\sinh\pi}{\pi}\left[1+2\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}\big(\cos nx-n\sin nx\big)\right].
$$

The $b_n$ fall only as $1/n$, like the sawtooth's, because the periodic extension jumps.

> [!check] Convergence at $x=0$
> $a_0/2=\sinh\pi/\pi=3.676$. At $x=0$ every sine vanishes, and the partial sums with 10, 100 and 1000 terms are $1.0328$, $1.00036$ and $1.0000037$, converging to $e^0=1$.

## 5. Summing series by evaluating at a point (L5)

A Fourier series is an identity, so it can be evaluated at any convenient point, and that often produces the value of an infinite sum (ll. 400–423). At $x=0$ the tent series gives $|0|=0$ on the left and $\cos0=1$ in every term on the right:

$$
0=\frac\pi2-\frac4\pi\sum_{n\ \mathrm{odd}}\frac1{n^2}.
$$

Rearrange:

$$
\sum_{n\ \mathrm{odd}}\frac1{n^2}=1+\frac19+\frac1{25}+\dots=\frac{\pi^2}{8}.
$$

Most of the neat infinite sums in formula books were found this way, which is why they turn up in exam questions: take the series, pick a point where the terms simplify, evaluate both sides and rearrange. The point has to be one where the series converges to $f$ itself; at a jump of the periodic extension it converges to the average of the two sides instead (FS2).

The sawtooth gives the alternating odd series. At $x=\pi/2$, $\sin\frac{n\pi}2$ is $0$ for even $n$ and $(-1)^{(n-1)/2}$ for odd $n$, so only odd terms survive and $(-1)^{n+1}=1$ for each of them:

$$
\frac\pi2=2\Big(1-\frac13+\frac15-\frac17+\dots\Big)
$$

$$
1-\frac13+\frac15-\dots=\frac\pi4 .
$$

The exponential gives a sum with no simple pattern of signs. At $x=0$ the series in [[#The exponential, e to the x (PS3 Q1)]] reads

$$
1=\frac{\sinh\pi}{\pi}\left[1+2\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}\right],
$$

so

$$
\sum_{n=1}^\infty\frac{(-1)^n}{1+n^2}=\frac12\left(\frac{\pi}{\sinh\pi}-1\right)=-0.36399 .
$$

> [!check] Direct summation
> Adding the first $2\times10^5$ terms of $\sum(-1)^n/(1+n^2)$ gives $-0.3639855$, matching $\tfrac12(\pi/\sinh\pi-1)=-0.3639855$. The Leibniz series converges far more slowly: $10^4$ terms of $1-\frac13+\frac15-\dots$ give $0.785373$ against $\pi/4=0.785398$.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · Next: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]
- The sines and cosines are the eigenfunctions of $y''+\lambda y=0$ with periodic conditions on $[-\pi,\pi]$ ([[ODE Eigenvalue Problems]]); Sturm–Liouville theory generalises this (L5, ll. 23–41, not examinable).
- Concepts: [[Fourier Series]] · [[Orthogonality of Trigonometric Functions]]

## Sources

- Lecture 4 (7 Oct 2024) and Lecture 5 (8 Oct 2024) recordings, Ian Hawke: `MATH2048 Lecture 4.txt`, `MATH2048 Lecture 5.txt`
- Slides `Lecture4_FourierSeries1.pdf`, `Lecture5_FourierSeries2.pdf`; lecture notes Ch. 2
- Problem Sheet 2 (Fourier series page) and Problem Sheet 3; worked solutions in [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

## Self-study tasks

Lecture 4 left the cosine–cosine and sine–cosine orthogonality relations to the students (ll. 319–325), and Lecture 5 left the tent's $b_n$ as a check (ll. 384–390). A STACK warning: always check the list of variables STACK says it recognised, use explicit `*` for multiplication and `exp()` for the exponential (ll. 1–26).

### Core

- [ ] Lecturer-set (L4, ll. 319–325): derive the cosine–cosine and sine–cosine orthogonality relations, including the $m=n$ cases. This is PS2 (Fourier series) Q1 on $[-L,L]$. → [[#The cosine–cosine and sine–cosine relations]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|solution]]
- [ ] Lecturer-set (L5, ll. 384–390): show directly that all $b_n=0$ for $f=|x|$. → [[#The tent function]]
- [ ] PS2 (Fourier series) Q2: the Fourier series of $1+x$ on $[-2,2]$. → [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

### Further practice

- [ ] PS3 Q1(a)–(c): the real Fourier series of $e^x$ on $(-\pi,\pi)$ and its values at $0,\pm\frac\pi2,\pm\pi$. Answer: $a_n=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)}$, $b_n=-\frac{2(-1)^nn\sinh\pi}{\pi(1+n^2)}$. → [[#The exponential, e to the x (PS3 Q1)]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|solution]]
- [ ] Evaluate the sawtooth series at $x=\pi/2$ to show $1-\frac13+\frac15-\dots=\frac\pi4$ (suggested, not lecturer-set). → [[#5. Summing series by evaluating at a point (L5)]]

## Transcript and slide slips

### Transcript slips

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

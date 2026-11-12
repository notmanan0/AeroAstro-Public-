---
title: "MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 2: Fourier Series"
order: 6
tags:
  - math2048
  - fourier-series
  - complex-fourier-series
aliases: ["MATH2048 Lecture 7", "MATH2048 Lecture 8", "Term-by-term differentiation", "Complex Fourier series"]
date: 2026-10-30
status: lectured
coverage: "Lecture 7 (14 Oct 2024): the series for x², term-by-term differentiation (when it works and when it fails), the extra conditions, and term-by-term integration with the constant fixed at x = 0. Lecture 8 (15 Oct 2024): the complex Fourier series derived from the real one, its single Euler formula, the example e^x, and the special case when f is itself a basis function. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]]"]
next_topics: ["[[MATH2048 TR1 - Fourier Transforms]]"]
key_concepts: ["[[Complex Fourier Series]]", "[[Fourier Series]]", "[[Fourier's Theorem]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 7.txt", "02 - Sources/Lectures/MATH2048 Lecture 8.txt", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture7_FourierSeries4.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier Series/Lecture8_FourierSeries5.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§2.5–2.6)"]
---

# MATH2048 FS3 - Calculus with Fourier Series and Complex Fourier Series

> [!abstract] Summary
> A Fourier series can always be integrated term by term, because integration smooths a function, but it can only be differentiated term by term if the function's periodic extension is continuous and piecewise smooth; differentiating the sawtooth's series gives a divergent series. The complex Fourier series $f\sim\sum_{n=-\infty}^{\infty}c_ne^{jn\pi x/L}$ packs the sines and cosines into complex exponentials with the single Euler formula $c_n=\frac1{2L}\int_{-L}^Lf\,e^{-jn\pi x/L}\,dx$, which turns exponential integrands into one-line integrals and is the step towards Fourier transforms.

> [!summary]- Exam use: quick path
> - **Use it when:** you have one Fourier series and need the series of its derivative or integral, or a function is (or contains) an exponential, or the question asks for a complex series.
> - **Assumptions:** differentiating term by term needs $f$ continuous over its whole periodic extension and piecewise smooth; integrating needs only the Dirichlet conditions; $c_n$ formula over one period $(-L,L)$.
> - **Method:** 1. Differentiation: check the extension has no jumps first, then differentiate each term. 2. Integration: integrate each term, then remove the $\frac12a_0x$ term with the known series for $x$ and fix the constant at a point where the extension is continuous (usually $x=0$). 3. Complex series: one integral for $c_n$, then check separately any $n$ where the general formula divides by zero.
> - **Common mistakes:** differentiating the series of a function whose extension jumps; fixing the integration constant at $x=\pm\pi$, where the series gives an average.
> - **Practise:** [[#Integrating the series for x squared]] · [[#Example: the complex series of e to the x]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series|PS4 Q1]]

Fourier series are put into differential equations, which requires knowing whether a series can be differentiated and integrated term by term (L7, ll. 3–8). When differentiating works it gives exact answers with no effort; when it fails the result is a series that diverges (ll. 140–145).

Whether it works depends on how smooth the function is. Differentiating amplifies the high-frequency terms, multiplying the $n$th coefficient by $n$, so the series of the derivative only converges if the coefficients were falling fast enough to begin with, and that depends on the function having no jumps. Integration divides the $n$th coefficient by $n$, damping the high frequencies, so it only ever makes things better and can always be done, whereas differentiation always makes things worse (ll. 349–362).

The complex series is the same series written differently. Euler's formula expresses each cosine and sine as two complex exponentials, one spinning each way, so a sum over positive $n$ of cosines and sines becomes a sum over all integers $n$ of exponentials. Nothing is gained for real functions in principle, but in practice integrals of exponentials are easier than integrals by parts, and the complex form is the one that turns into the Fourier transform in the next block (L8, ll. 19–36).

---

## 1. The series for x squared (L7)

The running example is $f(x)=x^2$ on $(-\pi,\pi)$, extended periodically (L7, ll. 9–73). It is even, so it has a cosine series with the half-range formulae (FS2):

$$
a_n=\frac2\pi\int_0^\pi x^2\cos nx\,dx .
$$

The constant:

$$
a_0=\frac2\pi\int_0^\pi x^2\,dx=\frac2\pi\cdot\frac{\pi^3}3=\frac{2\pi^2}{3},
$$

so the series starts with $\frac12a_0=\frac{\pi^2}3$, the average of $x^2$ over a period.

For $a_n$, integrate by parts twice, with the polynomial differentiated each time. First:

$$
\int_0^\pi x^2\cos nx\,dx=\Big[\frac{x^2\sin nx}{n}\Big]_0^\pi-\int_0^\pi\frac{2x\sin nx}{n}\,dx .
$$

The bracket vanishes because $\sin n\pi=0$. Second:

$$
-\int_0^\pi\frac{2x\sin nx}{n}\,dx=\Big[\frac{2x\cos nx}{n^2}\Big]_0^\pi-\int_0^\pi\frac{2\cos nx}{n^2}\,dx
$$

$$
=\frac{2\pi(-1)^n}{n^2}-\Big[\frac{2\sin nx}{n^3}\Big]_0^\pi=\frac{2\pi(-1)^n}{n^2}.
$$

Multiply by $\frac2\pi$:

$$
a_n=\frac{4(-1)^n}{n^2},
$$

so

$$
x^2\sim\frac{\pi^2}3+\sum_{n=1}^\infty\frac{4(-1)^n}{n^2}\cos nx\qquad(-\pi\leq x\leq\pi).
$$

The extension of $x^2$ is continuous, since $(\pm\pi)^2$ agree at the joins, so the series converges to $x^2$ everywhere, including at $\pm\pi$. Putting $x=\pi$, where $\cos n\pi=(-1)^n$, gives $\pi^2=\frac{\pi^2}3+4\sum\frac1{n^2}$, so $\sum_{n=1}^\infty\frac1{n^2}=\frac{\pi^2}6$.

## 2. Differentiating a Fourier series (L7)

Differentiating a Fourier series term by term kills the constant, turns cosines into minus sines and sines into cosines, and multiplies the $n$th term by $n$ (ll. 77–96).

**When it works.** Differentiate the $x^2$ series:

$$
2x\sim\sum_{n=1}^\infty\frac{4(-1)^n}{n^2}\cdot(-n\sin nx)=\sum_{n=1}^\infty\frac{4(-1)^{n+1}}{n}\sin nx .
$$

Dividing by 2 gives $x\sim\sum\frac{2(-1)^{n+1}}{n}\sin nx$, exactly the sawtooth series of FS1, as it should be.

**When it fails.** Differentiate again:

$$
1\overset{?}{\sim}\sum_{n=1}^\infty\frac{2(-1)^{n+1}}{n}\cdot n\cos nx=2\sum_{n=1}^\infty(-1)^{n+1}\cos nx .
$$

The coefficients no longer fall at all, and the partial sums oscillate ever more wildly as terms are added, worst near $\pm\pi$ (ll. 97–123). At $x=\pi$ every term is $2(-1)^{n+1}(-1)^n=-2$, so the sum diverges to $-\infty$ (ll. 124–139). At $x=0$ the terms are $2,-2,2,\dots$ and the partial sums jump between $2$ and $0$ for ever, never settling on the value $1$. Term-by-term differentiation has failed completely here.

![[m2048_fs_differentiated_series.png|900]]

**Why.** For a Fourier series of $f'$ to exist, $f'$ must satisfy the Dirichlet conditions, and in particular be bounded (ll. 146–168). The sawtooth jumps at $\pm\pi$. Smooth the jump slightly and the derivative there becomes a tall narrow spike; make the jump sharper and the spike grows without bound, so the derivative isn't bounded and has no Fourier series. That gives the extra conditions for term-by-term differentiation (ll. 169–178): $f$ must be **continuous** over its entire periodic extension, not just inside the interval, and **piecewise smooth**, made of finitely many pieces each infinitely differentiable. The second condition is stronger than mathematically necessary but is the practical test.

Applying the test (ll. 179–215): the sawtooth is piecewise smooth but jumps at the joins, so its series can't be differentiated. The extension of $x^2$ is continuous and piecewise smooth, so its series can. The tent $|x|$ is continuous and piecewise smooth, so differentiating its series gives the series of its derivative, a square wave of $\pm1$; but the square wave jumps, so that series can't be differentiated again (ll. 216–243). Explicitly, differentiating FS1's tent series term by term,

$$
\frac{d}{dx}\left[\frac\pi2-\frac4\pi\sum_{n\ \mathrm{odd}}\frac{\cos nx}{n^2}\right]=\frac4\pi\sum_{n\ \mathrm{odd}}\frac{\sin nx}{n},
$$

which should be $-1$ on $(-\pi,0)$ and $+1$ on $(0,\pi)$. At $x=\pi/2$ it gives $\frac4\pi\big(1-\frac13+\frac15-\dots\big)=\frac4\pi\cdot\frac\pi4=1$, using FS1's Leibniz sum, and $10^4$ odd terms give $0.99997$. The coefficients now fall as $1/n$, one power slower than the tent's $1/n^2$. The general pattern is that each differentiation costs one degree of smoothness until a jump appears and the process breaks. For PDEs this means the solution has to be at least as smooth as the highest derivative in the equation, which for the usual second-order equations is not a problem (ll. 244–248).

## 3. Integrating a Fourier series (L7)

Integrate the general series term by term (ll. 250–267):

$$
\int f\,dx\sim C+\frac12a_0x+\sum_{n=1}^\infty\Big(\frac{a_n}{n}\sin nx-\frac{b_n}{n}\cos nx\Big).
$$

The sum is a Fourier series again, with the sines and cosines swapped and the coefficients divided by $n$. Two things need fixing. The term $\frac12a_0x$ is not a Fourier series term, but the series for $x$ is known (the sawtooth), so it can be substituted. And the integration constant $C$ has to be found by evaluating both sides at a convenient point.

### Integrating the series for x squared

Integrate the $x^2$ series (ll. 273–281):

$$
\frac{x^3}{3}\sim C+\frac{\pi^2}3x+\sum_{n=1}^\infty\frac{4(-1)^n}{n^3}\sin nx .
$$

Fix $C$ at $x=0$ (ll. 282–312). The periodic extension of $x^3$ jumps at $\pm\pi$, where the series would give an average, but it is continuous at $0$, where the left side is $0$ and every sine vanishes:

$$
0=C+0+0\quad\Longrightarrow\quad C=0 .
$$

Replace $x$ by its series, $x\sim\sum\frac{2(-1)^{n+1}}{n}\sin nx$ (ll. 315–328):

$$
\frac{x^3}{3}\sim\sum_{n=1}^\infty\Big(\frac{2\pi^2(-1)^{n+1}}{3n}+\frac{4(-1)^n}{n^3}\Big)\sin nx .
$$

Multiply by 3 and put everything over $n^3$ (ll. 329–346):

$$
x^3\sim\sum_{n=1}^\infty\frac{2(-1)^n\big(6-\pi^2n^2\big)}{n^3}\sin nx .
$$

> [!check] SymPy and a point value
> Computing $b_n=\frac1\pi\int_{-\pi}^{\pi}x^3\sin nx\,dx$ directly gives $\frac{2(-1)^n(6-\pi^2n^2)}{n^3}$, the same. At $x=2$, $2\times10^4$ terms of the series give $7.9993$ against $2^3=8$; convergence is slow because the extension of $x^3$ jumps at $\pm\pi$ and the coefficients fall only as $1/n$.

The decay of the coefficients follows the smoothness of the extension (log scale in the figure). A jump in the periodic extension (sawtooth, square wave, $e^x$, $x^3$) gives coefficients falling as $1/n$; a corner with no jump (tent, $x^2$) gives $1/n^2$. Each integration moves one step down this scale and each differentiation one step up.

![[m2048_fs_coefficient_decay.png|760]]

## 4. Complex Fourier series (L8)

### From sines and cosines to exponentials

Start from Euler's formula and its conjugate (ll. 38–55):

$$
e^{\pm j\theta}=\cos\theta\pm j\sin\theta .
$$

Add and subtract:

$$
\cos\theta=\frac{e^{j\theta}+e^{-j\theta}}2,\qquad\sin\theta=\frac{e^{j\theta}-e^{-j\theta}}{2j}.
$$

Substitute with $\theta=n\pi x/L$ into the real series (ll. 57–96):

$$
f\sim\frac12a_0+\sum_{n=1}^\infty\Big[a_n\frac{e^{jn\pi x/L}+e^{-jn\pi x/L}}{2}+b_n\frac{e^{jn\pi x/L}-e^{-jn\pi x/L}}{2j}\Big].
$$

Group the terms by exponential:

$$
f\sim\frac12a_0+\sum_{n=1}^\infty\Big[\frac12\Big(a_n+\frac{b_n}{j}\Big)e^{jn\pi x/L}+\frac12\Big(a_n-\frac{b_n}{j}\Big)e^{-jn\pi x/L}\Big].
$$

Since $1/j=-j$:

$$
f\sim\frac12a_0+\frac12\sum_{n=1}^\infty\Big[(a_n-jb_n)e^{jn\pi x/L}+(a_n+jb_n)e^{-jn\pi x/L}\Big].
$$

In the second group relabel $n\to-n$, so that it runs over negative integers with a positive-looking exponent (ll. 97–135). Everything then fits one sum over all integers,

$$
f(x)\sim\sum_{n=-\infty}^{\infty}c_n\,e^{jn\pi x/L},
$$

with

$$
c_n=\tfrac12(a_n-jb_n)\ (n>0),\qquad c_0=\tfrac12a_0,\qquad c_n=\tfrac12(a_{-n}+jb_{-n})\ (n<0).
$$

The $c_n$ are complex even for a real function. If $f$ is odd only the $b_n$ survive and the $c_n$ are purely imaginary; if $f$ is even they are purely real (ll. 159–176). For real $f$, $c_{-n}=\overline{c_n}$.

### One Euler formula

For $n>0$, substitute the real Euler formulae and the exponential forms of cosine and sine (ll. 177–205):

$$
c_n=\frac12\left(\frac1L\int_{-L}^Lf\cos\frac{n\pi x}L\,dx-\frac jL\int_{-L}^Lf\sin\frac{n\pi x}L\,dx\right)
$$

$$
=\frac1{4L}\int_{-L}^Lf\Big[\big(e^{jn\pi x/L}+e^{-jn\pi x/L}\big)-\big(e^{jn\pi x/L}-e^{-jn\pi x/L}\big)\Big]dx
$$

$$
=\frac1{2L}\int_{-L}^Lf(x)\,e^{-jn\pi x/L}\,dx .
$$

The positive exponentials cancel and the negative ones add. For $n<0$ write $m=-n>0$, so $c_n=\frac12(a_m+jb_m)$:

$$
c_n=\frac1{4L}\int_{-L}^Lf\Big[\big(e^{jm\pi x/L}+e^{-jm\pi x/L}\big)+\big(e^{jm\pi x/L}-e^{-jm\pi x/L}\big)\Big]dx
$$

$$
=\frac1{2L}\int_{-L}^Lf\,e^{jm\pi x/L}\,dx=\frac1{2L}\int_{-L}^Lf\,e^{-jn\pi x/L}\,dx,
$$

using $j\cdot\frac1j=1$ in the sine term and $m=-n$ in the last step: the same formula (ll. 219–272). For $n=0$ it gives $\frac1{2L}\int f\,dx=\frac12a_0=c_0$ (ll. 274–289). So one formula covers every case:

$$
c_n=\frac1{2L}\int_{-L}^{L}f(x)\,e^{-jn\pi x/L}\,dx,\qquad n=0,\pm1,\pm2,\dots
$$

Compared with the real series (ll. 292–300), the sum runs over all integers, there is no separate constant term, the factor is $\frac1{2L}$ rather than $\frac1L$, and the exponential in the Euler formula has the opposite sign from the one in the series. Every step makes sense for a complex-valued $f$, so the formula applies to complex functions directly (ll. 301–309).

### Example: the complex series of e to the x

For $f=e^x$ on $(-\pi,\pi)$, which is neither even nor odd, the real series needs three Euler integrals, each by parts twice with a rearrangement at the end (ll. 313–328). The complex series needs one integral (ll. 329–360). With $L=\pi$:

$$
c_n=\frac1{2\pi}\int_{-\pi}^{\pi}e^{x}e^{-jnx}\,dx=\frac1{2\pi}\int_{-\pi}^{\pi}e^{(1-jn)x}\,dx
$$

$$
=\frac1{2\pi}\cdot\frac{1}{1-jn}\Big[e^{(1-jn)x}\Big]_{-\pi}^{\pi}
$$

$$
=\frac1{2\pi(1-jn)}\Big(e^{\pi}e^{-jn\pi}-e^{-\pi}e^{jn\pi}\Big).
$$

Since $e^{\pm jn\pi}=\cos n\pi\pm j\sin n\pi=(-1)^n$ (ll. 362–371):

$$
c_n=\frac{(-1)^n\big(e^{\pi}-e^{-\pi}\big)}{2\pi(1-jn)}=\frac{(-1)^n\sinh\pi}{\pi(1-jn)} .
$$

To recover the real series, rationalise the denominator by multiplying top and bottom by the conjugate $1+jn$ (ll. 385–404):

$$
\frac{1}{1-jn}=\frac{1+jn}{(1-jn)(1+jn)}=\frac{1+jn}{1+n^2},
$$

so

$$
c_n=\frac{(-1)^n\sinh\pi}{\pi}\cdot\frac{1+jn}{1+n^2}.
$$

Since $e^x$ is real, $c_{-n}=\overline{c_n}$, and the pair of terms $\pm n$ is a number plus its conjugate:

$$
c_ne^{jnx}+c_{-n}e^{-jnx}=c_ne^{jnx}+\overline{c_ne^{jnx}}=2\,\mathrm{Re}\big(c_ne^{jnx}\big).
$$

Expand the real part with $c_n=\alpha_n+j\beta_n$ and $e^{jnx}=\cos nx+j\sin nx$:

$$
2\,\mathrm{Re}\big(c_ne^{jnx}\big)=2\alpha_n\cos nx-2\beta_n\sin nx .
$$

So $a_n=2\,\mathrm{Re}\,c_n=\frac{2(-1)^n\sinh\pi}{\pi(1+n^2)}$ and $b_n=-2\,\mathrm{Im}\,c_n=-\frac{2(-1)^nn\sinh\pi}{\pi(1+n^2)}$, the PS3 Q1 answer worked by parts in [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae#The exponential, e to the x (PS3 Q1)|FS1]].

> [!check] SymPy
> The three real Euler integrals of $e^x$ give $a_0=\frac{2\sinh\pi}{\pi}$, $a_n=\frac{2(-1)^n\sinh\pi}{\pi(n^2+1)}$ and $b_n=-\frac{2(-1)^nn\sinh\pi}{\pi(n^2+1)}$, which match $c_n=\frac12(a_n-jb_n)$.

### The special case: when f is a basis function

The general $c_n$ formula can divide by zero for one particular $n$ (ll. 405–445). For $f=e^{jx}$ on $(-\pi,\pi)$:

$$
c_n=\frac1{2\pi}\int_{-\pi}^{\pi}e^{jx}e^{-jnx}\,dx=\frac1{2\pi}\int_{-\pi}^{\pi}e^{j(1-n)x}\,dx .
$$

For $n\neq1$:

$$
c_n=\frac{1}{2\pi}\cdot\frac{e^{j(1-n)\pi}-e^{-j(1-n)\pi}}{j(1-n)}=\frac{1}{2\pi}\cdot\frac{2j\sin\big((1-n)\pi\big)}{j(1-n)}=0,
$$

because $1-n$ is an integer. The factor $\frac{1}{j(1-n)}$ blows up at $n=1$, so that case has to be done separately: the integrand is $e^{0}=1$ and

$$
c_1=\frac{1}{2\pi}\int_{-\pi}^{\pi}1\,dx=1 .
$$

So the series of $e^{jx}$ is $e^{jx}$ itself, one term, as it must be, since the basis functions are orthogonal. The real version is the same: computing the series of $\sin x$ with the general formula produces a $\frac1{n-1}$ and fails at $n=1$. Whenever the function being expanded is itself one of the basis functions, or contains one, do the general case and then look for the values of $n$ where it fails.

### Example: the complex series of x (PS4 Q1)

For $f=x$ on $(-\pi,\pi)$, $c_0=\frac1{2\pi}\int_{-\pi}^{\pi}x\,dx=0$. For $n\neq0$, integrate by parts with $u=x$ and $v'=e^{-jnx}$, $v=\frac{e^{-jnx}}{-jn}=\frac{j}{n}e^{-jnx}$:

$$
c_n=\frac1{2\pi}\left(\Big[\frac{jx}{n}e^{-jnx}\Big]_{-\pi}^{\pi}-\frac jn\int_{-\pi}^{\pi}e^{-jnx}\,dx\right).
$$

The integral is zero for $n\neq0$, and $e^{\mp jn\pi}=(-1)^n$:

$$
c_n=\frac1{2\pi}\cdot\frac jn\big(\pi(-1)^n-(-\pi)(-1)^n\big)=\frac{j(-1)^n}{n}.
$$

The $c_n$ are purely imaginary, as they must be for an odd function. Then $b_n=-2\,\mathrm{Im}\,c_n=\frac{-2(-1)^n}{n}=\frac{2(-1)^{n+1}}{n}$ and $a_n=0$, the sawtooth series of FS1 again.

### Example: the complex series of a square wave (PS4 Q2)

Let $f=0$ on $(-2,0)$ and $f=1$ on $(0,2)$, so $L=2$ and the series uses $e^{jn\pi t/2}$. The constant is the average, $c_0=\frac14\int_0^21\,dt=\frac12$. For $n\neq0$ only the right half contributes:

$$
c_n=\frac14\int_0^2e^{-jn\pi t/2}\,dt=\frac14\Big[\frac{e^{-jn\pi t/2}}{-jn\pi/2}\Big]_0^2=\frac{j}{2n\pi}\big(e^{-jn\pi}-1\big)=\frac{j\big((-1)^n-1\big)}{2n\pi}.
$$

This is zero for even $n$ and $-\frac{j}{n\pi}$ for odd $n$. Pairing $\pm n$ as above, $b_n=-2\,\mathrm{Im}\,c_n=\frac{2}{n\pi}$ for odd $n$, so

$$
f\sim\frac12+\frac2\pi\sum_{k=1}^\infty\frac{1}{2k-1}\sin\frac{(2k-1)\pi t}{2}.
$$

> [!check] Values of the square-wave series
> At $t=0$ every sine vanishes and the series gives $\frac12$, the average across the jump. At $t=1$, 1000 terms give $0.99984$, and at $t=0.5$, 2000 terms give $0.99989$, both converging to $1$. SymPy's integral gives the same $c_n$.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 FS2 - Even and Odd Functions, Half-Range Series and Convergence]] · Next: [[MATH2048 TR1 - Fourier Transforms]]
- Smoothness of solutions in separation of variables: [[MATH2048 PDE2 - Separation of Variables for the Wave Equation]]
- Concepts: [[Complex Fourier Series]] · [[Fourier Series]] · [[Fourier's Theorem]]

## Sources

- Lecture 7 (14 Oct 2024) and Lecture 8 (15 Oct 2024) recordings, Ian Hawke: `MATH2048 Lecture 7.txt`, `MATH2048 Lecture 8.txt`
- Slides `Lecture7_FourierSeries4.pdf`, `Lecture8_FourierSeries5.pdf`; lecture notes §2.5–2.6
- Problem Sheets 3 and 4; worked solutions in [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]

## Self-study tasks

With complex series covered, Lecture 8 marked the end of the material needed for the Unit 2 coursework (l. 447), and referred to the $e^x$ problem on the sheet (ll. 311–313).

### Core

- [ ] Derive the series for $x^2$ and use it at $x=\pi$ to show $\sum1/n^2=\pi^2/6$. → [[#1. The series for x squared (L7)]]
- [ ] PS4 Q1: the complex series of $x$ on $(-\pi,\pi)$, its real form, then integrate it to get the series of $x^2$. Answer: $c_n=\frac{j(-1)^n}{n}$ for $n\neq0$, $c_0=0$. → [[#Example: the complex series of x (PS4 Q1)]] · [[MATH2048 Problem Sheets 2-4 Solutions - Fourier Series]]
- [ ] PS3 Q1 by the complex route: compute $c_n$ for $e^x$, then recover $a_n$ and $b_n$. → [[#Example: the complex series of e to the x]]

### Further practice

- [ ] PS4 Q2: the complex series of the square wave ($0$ on $(-2,0)$, $1$ on $(0,2)$), and its real form $\frac12+\frac2\pi\sum\frac{1}{2n-1}\sin\frac{(2n-1)\pi t}{2}$. → [[#Example: the complex series of a square wave (PS4 Q2)]]
- [ ] Decide, without calculating, whether the series of $|x|$, $x^2$ and the square wave can each be differentiated term by term, and say why (suggested, not lecturer-set). → [[#2. Differentiating a Fourier series (L7)]]
- [ ] Compute the complex series of $e^{jx}$ on $(-\pi,\pi)$, handling $n=1$ separately (L8, ll. 427–440). → [[#The special case: when f is a basis function]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lectures 7 and 8
> | Where | Transcript says | Correct |
> |---|---|---|
> | L7, ll. 51–56 | "so I have to you pie minus one to the and on and square from back peace" (speech-to-text garbling) | the boundary term $\frac{2\pi(-1)^n}{n^2}$ |
> | L7, ll. 237–241 | the square wave is not continuous, "so therefore, the derivative of the tenth function does not have a Fourier series itself" | the derivative of the tent, the square wave, does have a Fourier series (found by differentiating the tent's); it is the square wave's own derivative that can't be found term by term |
> | L7, l. 330 | "Cody Hum" | garbled; the lecturer is reading the slide's rearranged form of the $x^3$ series |
> | L8, ll. 64–79 | "a n plus 1 on j b n… so I get minus 1 half b n" | $\frac12(a_n+b_n/j)$ and $\frac12(a_n-b_n/j)$; corrected at ll. 88–96 |
> | L8, ll. 237–270 | loses a sign in the $n<0$ case, then finds it with a student's help | the $n<0$ case gives the same $c_n$ formula |
> | L8, ll. 395–396 | $\frac{1}{1-jn}$ "is equal to… 1 plus jn on 1 minus n squared" | $\frac{1+jn}{1+n^2}$, since $(1-jn)(1+jn)=1+n^2$ |

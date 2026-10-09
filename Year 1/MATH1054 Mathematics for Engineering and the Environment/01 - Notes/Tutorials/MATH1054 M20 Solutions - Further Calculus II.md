---
title: "MATH1054 M20 Solutions - Further Calculus II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 5: Series and Statistics"
tags:
  - math1054
  - tutorial-solutions
  - sequences-and-series
  - taylor-series
  - lhopital
sheet: "Specimen Test 20 (booklet) + Module 20 work scheme: Examples 7.1–7.29, 9.8, 9.10, 9.14; Exercises 14, 41, 19(a),(b),(c),(e); Booklet Exercises A–D"
theory_notes: ["[[MATH1054 M20 - Further Calculus II]]"]
key_concepts: ["[[Arithmetic and Geometric Series]]", "[[Convergence Tests for Series]]", "[[Taylor and Maclaurin Series]]", "[[L'Hôpital's Rule]]"]
status: complete
sources: ["tmp/md/module_20_further_calculus_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§7.2–7.8, §9.4)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 20)"]
---

# MATH1054 M20 Solutions - Further Calculus II

> [!abstract] Sheet Info
> The whole Module 20 work scheme. Limits and sums were checked with SymPy `limit`/`summation`, and the financial sums and error bounds in Python.
>
> **Standard results**:
> - Arithmetic: $a_n=a+(n-1)d$ and $S_n=\frac n2[2a+(n-1)d]$.
> - Geometric: $a_n=ar^{n-1}$, $S_n=\dfrac{a(1-r^n)}{1-r}$, and $S_\infty=\dfrac a{1-r}$ for $|r|<1$.

## Theory Links
- [[MATH1054 M20 - Further Calculus II]] · [[Arithmetic and Geometric Series]] · [[Convergence Tests for Series]] · [[Taylor and Maclaurin Series]] · [[L'Hôpital's Rule]]

---

# Part A: Worked examples

## Example 7.1: Compound-interest deposits
Let $a_n$ be the balance at the start of year $n$, just after that year's deposit. Then

$$a_1=1000,\qquad a_{n+1}=1.085\,a_n+1000.$$

| Start of year | Balance |
|---|---|
| 1 | £1000.00 |
| 2 | $1.085(1000)+1000=$ £2085.00 |
| 3 | $1.085(2085)+1000=$ £3262.23 |
| 4 | $1.085(3262.225)+1000=$ £4539.51 |

## Example 7.2: Duct diameters as a sequence
$\{D_n\}=\{d,\ 2d,\ 2.155d,\ 2.414d,\ 2.701d,\ 3d,\ 3d,\dots\}$. This is a **non-decreasing** sequence ($D_6=D_7$): adding a cable never needs a smaller duct.

> [!warning] Textbook erratum (the transcription faithfully copies James p.472)
> James prints $D_5=\frac14\sqrt{2(5-\sqrt5)}\,d\approx0.588d$, which is impossible because it is less than $D_1$. The quantity $\frac14\sqrt{2(5-\sqrt5)}$ is actually $\sin36°$.
>
> Five cables of diameter $d$ touching in a ring have their centres on a circle of radius $R=\dfrac{d}{2\sin36°}$. So
>
> $$D_5=2R+d=\Big(1+\frac{1}{\sin36°}\Big)d\approx2.701d.$$

## Example 7.3: Crank-and-rod displacement sequence
$y_n=5\cos n°+\sqrt{100-25\sin^2n°}$ for $n=0,1,2,\dots$

| $n$ | 0 | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|---|
| $y_n$ | 15.0000 | 14.9989 | 14.9954 | 14.9897 | 14.9817 | 14.9715 |

The sequence continues to $y_{180}=-5+10=5$ (the minimum at $x=180°$), then rises back to 15 at $360°$. It is periodic.

## Example 7.7: How many terms of $11+15+19+\cdots$ make 341?
Here $a=11$ and $d=4$:

$$S_n=\tfrac n2\big[22+4(n-1)\big]=n(2n+9)=341\ \Rightarrow\ 2n^2+9n-341=0\ \Rightarrow\ n=\frac{-9\pm\sqrt{81+2728}}4=\frac{-9\pm53}{4}$$

So $\boxed{n=11}$; the negative root is rejected. Check: the 11th term is $51$, and $\frac{11}2(11+51)=341$ ✔.

## Example 7.8: Sinking a 40 m well
This is arithmetic, with $a=30$, $d=5$ and $n=40$.
- **(a)** Total: $S_{40}=20\big(60+39\times5\big)=20\times255=\boxed{£5100}$.
- **(b)** Last metre: $a_{40}=30+39\times5=\boxed{£225}$.

## Example 7.9: Guaranteed insurance sum
The premium paid at the start of year $j$ earns interest for $26-j$ years, up to the end of year 25:

$$S=250\big(1.03^{25}+1.03^{24}+\dots+1.03^1\big)=250\times1.03\times\frac{1.03^{25}-1}{0.03}=\boxed{£9388.26}$$

## Example 7.22: Limits of sequences
Divide the top and bottom by the highest power of $n$.
- **(a)** $\dfrac{n}{n+1}=\dfrac{1}{1+1/n}\to\boxed1$
- **(b)** $\dfrac{2+3/n+1/n^2}{5+6/n+2/n^2}\to\boxed{\tfrac25}$

## Example 7.25: Convergence of series
**(a)** $1+3+5+\cdots$: $S_n=n^2\to\infty$, so it **diverges**.
**(b)** $1^2+2^2+\cdots$: the terms themselves $\to\infty$, so it **diverges**.
**(c)** Geometric with $r=\frac12$: $S_\infty=\frac{1}{1-1/2}=\boxed2$, so it **converges**.
**(d)** Use partial fractions: $\frac1{(k+1)(k+2)}=\frac1{k+1}-\frac1{k+2}$. The sum **telescopes**:

$$S_n=\Big(1-\tfrac12\Big)+\Big(\tfrac12-\tfrac13\Big)+\dots=1-\frac1{n+1}\to\boxed1$$

So it **converges**.

## Example 7.27: D'Alembert's ratio test
The test: find $\ell=\lim\left|\frac{a_{k+1}}{a_k}\right|$. If $\ell<1$ the series converges; if $\ell>1$ it diverges; if $\ell=1$ the test gives no information.

**(a)** $a_k=\dfrac{2^k}{k!}$:

$$\frac{a_{k+1}}{a_k}=\frac{2}{k+1}\to0<1$$

So it **converges** (to $e^2$).

**(b)** $a_k=\dfrac{2^k}{(k+1)^2}$:

$$\frac{a_{k+1}}{a_k}=2\Big(\frac{k+1}{k+2}\Big)^2\to2>1$$

So it **diverges**.

## Example 7.28: $\frac12+\frac23+\frac34+\cdots$ diverges
The terms $a_k=\dfrac{k}{k+1}\to1\neq0$. A convergent series needs $a_k\to0$ (the $n$th-term test), so the series **diverges**. In fact $S_n>\frac n2\to\infty$.

## Example 7.29: Radius of convergence
**(a)** $\sum\dfrac{x^n}n$:

$$\left|\frac{x^{n+1}/(n+1)}{x^n/n}\right|=\frac{n}{n+1}|x|\to|x|$$

It converges for $|x|<1$, so $\boxed{R=1}$.

**(b)** $\sum n^nx^n$:

$$\left|\frac{(n+1)^{n+1}x^{n+1}}{n^nx^n}\right|=(n+1)\Big(1+\frac1n\Big)^n|x|\to\infty\ \text{for any }x\neq0$$

So $\boxed{R=0}$: the series converges only at $x=0$.

## Example 9.8: A polynomial matching the derivatives at 0
Use the Maclaurin polynomial $\sum\frac{f^{(k)}(0)}{k!}x^k$:

$$f(x)\approx3+4x-\frac{10}{2!}x^2+\frac{12}{3!}x^3=\boxed{3+4x-5x^2+2x^3}$$

## Example 9.10: $e^x\sin x$

$$e^x\sin x=x+x^2+\frac{x^3}3-\frac{x^5}{30}-\cdots$$

The full working is in [[MATH1054 M08 Solutions - Differentiation II|M08 Solutions]].

## Example 9.14: L'Hôpital's rule
The rule applies to $\frac00$ (or $\frac\infty\infty$) forms: $\lim\frac fg=\lim\frac{f'}{g'}$.

**(a)**

$$\lim_{x\to0}\frac{\sin x-x}{x^3}=\lim\frac{\cos x-1}{3x^2}=\lim\frac{-\sin x}{6x}=\lim\frac{-\cos x}{6}=\boxed{-\tfrac16}$$

This takes three applications, because each intermediate step is still $\frac00$.

**(b)**

$$\lim_{x\to0}\frac{1-\cos x}{x+x^2}=\lim\frac{\sin x}{1+2x}=\frac01=\boxed0$$

**Stop** as soon as the form is no longer $\frac00$.

---

# Part B: Assigned exercises

## Exercise 14
**(a)** $a=4$ and $d=3$:
- 5th term: $4+4(3)=\boxed{16}$
- 10th term: $4+9(3)=\boxed{31}$

**(b)** $a=5$ and $ar^5=160$, so $r^5=32$ and $r=2$. The intermediate terms are $\boxed{10,\ 20,\ 40,\ 80}$.

## Booklet Exercise A: Limits of sequences
**(a)**

$$\frac{n+1}{n^2+1}=\frac{1/n+1/n^2}{1+1/n^2}\to\boxed0$$

**(b)**

$$\frac{3n^2+2n+1}{6n^2+5n+2}\to\boxed{\tfrac36=\tfrac12}$$

## Exercise 41: Geometric series
A geometric series converges iff $|r|<1$, in which case $S_\infty=\dfrac a{1-r}$.

| | $a$ | $r$ | Verdict |
|---|---|---|---|
| (a) | 2 | $\frac13$ | converges, $S=\dfrac2{2/3}=3$ |
| (b) | 4 | $-\frac12$ | converges, $S=\dfrac4{3/2}=\frac83$ |
| (c) | 10 | $\frac{11}{10}$ | **diverges** ($r>1$) |
| (d) | 1 | $-\frac54$ | **diverges** ($\lvert r\rvert>1$; it oscillates with growing amplitude) |

## Booklet Exercise B: $\cos x=1-\frac12x^2+R_3(x)$
**Maclaurin's theorem with Lagrange remainder**:

$$f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(0)}{k!}x^k+R_n(x),\qquad R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1},\quad0<\theta<1$$

For $f=\cos x$: $f(0)=1$, $f'(0)=0$, $f''(0)=-1$ and $f'''(0)=0$, with $f^{(4)}=\cos x$. Take $n=3$ (the $x^3$ term is zero anyway):

$$\cos x=1-\tfrac12x^2+R_3(x),\qquad R_3(x)=\frac{\cos(\theta x)}{4!}x^4$$

If $0<x<\frac\pi2$, then $0<\theta x<\frac\pi2$, so $0<\cos\theta x<1$. Hence

$$\boxed{0<R_3(x)<\frac{x^4}{4!}}$$

**Maximum error at $x=\frac\pi{10}$**:

$$R_3<\frac{(\pi/10)^4}{24}=0.000406$$

**Calculator check**:
- $\cos\frac\pi{10}=0.951057$
- $1-\frac12\big(\frac\pi{10}\big)^2=0.950652$
- The actual error is $0.000405$.

**Comment**: the actual error is positive, as predicted, and just below the bound. The bound is almost tight because the next non-zero term, $+\frac{x^4}{24}$, *is* essentially the whole error; $\cos\theta x$ is close to 1 for small $x$.

## Booklet Exercise C: $(1+x)^{1/2}=1+\frac12x+R_1(x)$
Here $f=(1+x)^{1/2}$, $f'=\frac12(1+x)^{-1/2}$ and $f''=-\frac14(1+x)^{-3/2}$. So $f(0)=1$ and $f'(0)=\frac12$, and the Lagrange remainder is

$$R_1(x)=\frac{f''(\theta x)}{2!}x^2=-\frac{x^2}{8(1+\theta x)^{3/2}},\qquad0<\theta<1$$

For $x=0.02>0$: $(1+\theta x)^{3/2}>1$, so

$$|R_1|<\frac{(0.02)^2}8=\frac{0.0004}{8}=\boxed{0.00005}$$

So $(1.02)^{1/2}\approx1.01$ with error at most $5\times10^{-5}$ ✔. Also $R_1<0$, so $1.01$ is an **over**-estimate. In fact $\sqrt{1.02}=1.0099505$, with error $4.95\times10^{-5}$.

## Booklet Exercise D: Maclaurin series of $e^x$
All the derivatives equal $e^x$, and $e^0=1$. So

$$\boxed{e^x=\sum_{n=0}^\infty\frac{x^n}{n!}=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots}$$

By the ratio test $\left|\frac{x}{n+1}\right|\to0$, so it converges for **all** $x$ ($R=\infty$).

## Exercise 19: L'Hôpital's rule
**(a)** At $x=2$ the form is $\frac00$:

$$\lim_{x\to2}\frac{x^3-3x-2}{x^3-8}=\lim\frac{3x^2-3}{3x^2}=\frac{9}{12}=\boxed{\tfrac34}$$

Or factorise: $\frac{(x-2)(x+1)^2}{(x-2)(x^2+2x+4)}\to\frac9{12}$.

**(b)**

$$\lim_{x\to0}\frac{1-(1-x)^{1/4}}{x}=\lim\frac{\frac14(1-x)^{-3/4}}{1}=\boxed{\tfrac14}$$

**(c)** $\sin3\pi=\sin2\pi=0$, so the form is $\frac00$:

$$\lim_{x\to\pi}\frac{\sin3x}{\sin2x}=\lim\frac{3\cos3x}{2\cos2x}=\frac{3(-1)}{2(1)}=\boxed{-\tfrac32}$$

**(e)**

$$\lim_{x\to0}\frac{x\cos x-\sin x}{x^3}=\lim\frac{\cos x-x\sin x-\cos x}{3x^2}=\lim\frac{-\sin x}{3x}=\boxed{-\tfrac13}$$

---

# Part C: Specimen Test 20

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 20), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Arithmetic sequence with $a_2=2$ and $a_4=18$
**(i)** $a+d=2$ and $a+3d=18$, so $\boxed{d=8,\ a=-6}$.
**(ii)** $a_{10}=-6+9(8)=\boxed{66}$.

## Q2: Geometric sequence with $a=3$ and $r=\frac23$
**(i)** $a_3=3\big(\tfrac23\big)^2=\boxed{\tfrac43}$.
**(ii)**

$$S_8=\frac{3\big(1-(2/3)^8\big)}{1-2/3}=9\Big(1-\frac{256}{6561}\Big)=\boxed{\frac{6305}{729}\approx8.649}$$

## Q3: Do the sequences converge?
**(i)**

$$\frac{1-2n^2}{1+n+n^2}=\frac{1/n^2-2}{1/n^2+1/n+1}\to\boxed{-2}$$

So it converges.

**(ii)** $1+4n-n^2\to-\infty$, so it **diverges**.

## Q4: $\frac13+\frac24+\frac35+\cdots$
The terms are $a_n=\frac{n}{n+2}\to1\neq0$. By the $n$th-term test the series **diverges**.

## Q5: Maclaurin's theorem

$$f(x)=f(0)+f'(0)x+\frac{f''(0)}{2!}x^2+\cdots+\frac{f^{(n)}(0)}{n!}x^n+R_n(x),\qquad R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1},\ 0<\theta<1$$

## Q6

$$\lim_{x\to0}\frac{\cos x-1}{x^2}=\lim\frac{-\sin x}{2x}=\lim\frac{-\cos x}{2}=\boxed{-\tfrac12}$$

## Q7: $(1+x)^{2/3}=1+\frac23x+R_1(x)$
Here $f'=\frac23(1+x)^{-1/3}$ and $f''=-\frac29(1+x)^{-4/3}$. So $f(0)=1$ and $f'(0)=\frac23$, and the **Lagrange remainder** is

$$R_1(x)=\frac{f''(\theta x)}{2!}x^2=-\frac{x^2}{9(1+\theta x)^{4/3}},\qquad0<\theta<1$$

For $0<x<0.3$: $(1+\theta x)^{4/3}>1$, so

$$|R_1|<\frac{x^2}9<\frac{0.09}9=0.01\ ✔$$

(At $x=0.3$, the actual error is $0.0089$.)

## Sources
- Transcribed problem statements: `tmp/md/module_20_further_calculus_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §7.2–7.8, §9.4; MATH1054 Module Booklet, Module 20

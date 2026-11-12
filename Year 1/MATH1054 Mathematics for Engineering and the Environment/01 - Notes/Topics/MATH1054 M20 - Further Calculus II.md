---
title: "MATH1054 M20 - Further Calculus II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 5: Series and Statistics"
order: 20
tags:
  - math1054
  - sequences-and-series
  - convergence
  - taylor-series
  - lhopital
aliases: ["MATH1054 Module 20", "Further Calculus II", "Sequences and series"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 20 work scheme (sequences and series, Rolle's theorem and the mean value theorems, Taylor's and Maclaurin's theorems, L'Hôpital's rule) and Specimen Test 20; James §7.2–7.3, §7.5–7.7, §9.3.1, §9.4.1–9.4.3"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M08 - Differentiation II]]"]
next_topics: ["[[MATH1054 M22 - Complex Numbers II]]"]
key_concepts: ["[[Arithmetic and Geometric Series]]", "[[Convergence Tests for Series]]", "[[Taylor and Maclaurin Series]]", "[[L'Hôpital's Rule]]"]
tutorial_sheets: ["[[MATH1054 M20 Solutions - Further Calculus II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 20)", "02 - Sources/Modern Engineering Mathematics.pdf (§7.2–7.8, §9.4)"]
---

# MATH1054 M20 - Further Calculus II

> [!abstract] Summary
> A sequence is an ordered list of numbers and a series is the running sum of one: arithmetic and geometric series have closed-form sums, and an infinite geometric series converges to $\frac{a}{1-r}$ exactly when $|r|<1$. An infinite series converges when its partial sums tend to a finite limit, which d'Alembert's ratio test settles for most series met here; applied to a power series $\sum a_nx^n$ it gives the radius of convergence $R=\lim|a_n/a_{n+1}|$. Rolle's theorem leads to the mean value theorem and on to Taylor's theorem with the Lagrange remainder $R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}$, $0<\theta<1$, which turns a Maclaurin approximation into a guaranteed error bound. The same mean value ideas prove L'Hôpital's rule, $\lim\frac fg=\lim\frac{f'}{g'}$ for $\frac00$ and $\frac\infty\infty$ forms.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks for a term or sum of an arithmetic or geometric sequence (often a savings or cost problem), the limit of a sequence, whether a series converges, the radius of convergence of a power series, a bound on the error of a truncated Maclaurin expansion, or a limit of the form $\frac00$ or $\frac\infty\infty$.
> - **Assumptions:** sum to infinity only for $|r|<1$; the ratio test as stated needs positive terms (use $|a_k|$ otherwise) and says nothing when the limit is 1; the Lagrange remainder needs $f^{(n+1)}$ to exist between $0$ and $x$, with $0<\theta<1$ unknown; angles in radians; L'Hôpital only on $\frac00$ or $\frac\infty\infty$.
> - **Method:** 1. Name the object: finite sum, sequence, infinite series, power series, approximation or limit. 2. Finite sums: read off $a$ and $d$ or $r$ and use $S_n$; sequences: divide by the highest power of $n$. 3. Infinite series: $n$th-term test first, then geometric, telescoping or the ratio test; power series: $R=\lim|a_n/a_{n+1}|$, endpoints separately. 4. Error bounds: write $R_n$ in Lagrange form and bound $|f^{(n+1)}(\theta x)|$ over $0<\theta<1$. 5. Limits: check the form, differentiate numerator and denominator separately, and check the form again before each repeat.
> - **Common mistakes:** applying L'Hôpital to a form that is no longer $\frac00$ (or using the quotient rule on $\frac fg$); taking $a_k\to0$ as proof that $\sum a_k$ converges.
> - **Practise:** [[#Two limits by L'Hôpital's rule (Example 9.14)]] · [[MATH1054 M20 Solutions - Further Calculus II#Part C: Specimen Test 20|Specimen Test 20]]

A sequence is a function whose inputs are the whole numbers $0,1,2,\dots$, so it lists values one after another: the balance of a savings account at the start of each year, the position of a crank at each degree of rotation, the successive guesses of an iterative root finder. A series adds those values up. Two families have exact sums. An arithmetic series grows by a fixed step, so its sum is the number of terms times the average of the first and last; a geometric series grows by a fixed factor, so multiplying it by that factor and subtracting cancels everything except the two ends. These cover costs that rise by a fixed amount, compound interest and loan repayments.

An infinite sum needs care, because adding infinitely many numbers is not an arithmetic operation but a limit. The partial sums $S_n$ form a sequence, and the series converges if that sequence settles on a finite value. Without that check, manipulations that look legitimate give nonsense: the trick that correctly sums a convergent geometric series assigns the value $\frac13$ to $1-2+4-8+\cdots$. The $n$th-term test and d'Alembert's ratio test decide convergence without finding the sum, and the ratio test applied to a power series gives the interval of $x$ on which the series means anything.

The Maclaurin series of [[MATH1054 M08 - Differentiation II|Module 8]] are made precise by a chain of theorems. Rolle's theorem (a smooth curve that starts and ends at the same height has a horizontal tangent somewhere) gives the mean value theorem, and applying Rolle's theorem to a well-chosen function gives Taylor's theorem: $f(x)$ equals its degree-$n$ Taylor polynomial plus a remainder that looks like the next term, with the derivative evaluated at an unknown point between $0$ and $x$. Bounding that derivative bounds the error, which is what an engineer needs before trusting $\sin x\approx x$ or $\sqrt{1.02}\approx1.01$. The same remainder estimates are the truncation errors of finite-difference schemes in [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables|SESA2029]], and the convergence of series of functions is again the question for the Fourier series of [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae|MATH2048]]. L'Hôpital's rule comes from the same ideas: near a point where numerator and denominator both vanish, each is approximately its derivative times $(x-a)$, so their ratio tends to the ratio of the derivatives.

---

## 1. Sequences and recurrence relations (James §7.2)

A **sequence** is the list of values $\{f_0,f_1,f_2,\dots\}$ of a function defined on the whole numbers, with $f_k=f(k)$. A finite sequence $\{f_0,\dots,f_n\}$ is written $\{f_k\}_{k=0}^{n}$ and an infinite one $\{f_k\}_{k=0}^{\infty}$, or just $\{f_k\}$. The index $k$ is a dummy variable: replacing it by $n$ or $r$ changes nothing. A **series** is a sum of terms, and its sum to $n$ terms, $S_n=\sum_{k=1}^{n}f_k$, is itself a sequence.

A sequence can be specified in three ways, and Examples 7.1, 7.2 and 7.3 are one of each: by a **recurrence relation** that gives each term from the one before, by a list with no formula at all, or by an explicit formula in $k$.

### Savings with compound interest (Example 7.1)

A bank pays 8.5% a year, compounded annually, and a customer deposits £1000 at the start of each year. Let $x_n$ be the balance at the start of year $n+1$, just after that year's deposit. A year's interest multiplies the balance by $1.085$, and the new deposit adds 1000:

$$
x_0=1000,\qquad x_{n}=1.085\,x_{n-1}+1000 .
$$

Iterating,

$$
\begin{aligned}
x_1&=1.085(1000)+1000=2085,\\
x_2&=1.085(2085)+1000=3262.225,\\
x_3&=1.085(3262.225)+1000=4539.514,
\end{aligned}
$$

so the balances at the start of years 1 to 4 are £1000, £2085.00, £3262.23 and £4539.51. Rounding $x_2$ down to £3262.22 before the next step changes $x_3$ by less than a penny.

### Cable ducts (Example 7.2)

The smallest circular duct that holds $n$ cables of diameter $d$ has diameter

$$
\{D_n\}=\Big\{d,\ 2d,\ \big(1+\tfrac{2}{\sqrt3}\big)d,\ \big(1+\sqrt2\big)d,\ \big(1+\tfrac{1}{\sin36^\circ}\big)d,\ 3d,\ 3d,\ \dots\Big\}=\{d,\ 2d,\ 2.155d,\ 2.414d,\ 2.701d,\ 3d,\ 3d,\dots\}.
$$

No formula or recurrence produces these: each comes from its own packing geometry. For five cables, the centres sit at the corners of a regular pentagon of side $d$, so they lie on a circle of radius $R$ with $d=2R\sin36^\circ$, and

$$
\begin{aligned}
R&=\frac{d}{2\sin36^\circ},\\
D_5&=2R+d=\Big(1+\frac{1}{\sin36^\circ}\Big)d=2.701d .
\end{aligned}
$$

The sequence is non-decreasing ($D_6=D_7=3d$, since a seventh cable fits in the centre of a ring of six), as it must be: adding a cable never allows a smaller duct. James prints a different $D_5$; see [[#Transcript and slide slips]].

### The crank and connecting rod (Example 7.3)

The end of a connecting rod of length $l=10$ driven by a crank of radius $r=5$ is at

$$
y=r\cos x^\circ+\sqrt{l^2-r^2\sin^2x^\circ},
$$

and a simulation evaluates it at every whole degree. The formula gives each term directly:

$$
\begin{aligned}
y_k&=5\cos k^\circ+\sqrt{100-25\sin^2k^\circ}\\
&=5\Big[\cos k^\circ+\sqrt{4-\sin^2k^\circ}\Big]\\
&=5\Big[\cos k^\circ+\sqrt{3+\cos^2k^\circ}\Big].
\end{aligned}
$$

| $k$ | 0 | 1 | 2 | 3 | 4 | 5 | 90 | 180 | 359 | 360 |
|---|---|---|---|---|---|---|---|---|---|---|
| $y_k$ | 15.0000 | 14.9989 | 14.9954 | 14.9897 | 14.9817 | 14.9715 | 8.6603 | 5.0000 | 14.9989 | 15.0000 |

The minimum $y_{180}=-5+10=5$ is the inner dead centre, and the sequence returns to 15 at $k=360$ and repeats with period 360.

## 2. Arithmetic sequences and series (James §7.3.1)

An **arithmetic sequence** (arithmetic progression, AP) has a constant difference $d$ between successive terms, so with first term $a$

$$
a_k=a+(k-1)d,\qquad k=1,2,\dots,n .
$$

The sum of its $n$ terms is the **arithmetic series**. Write it forwards and backwards:

$$
\begin{aligned}
S_n&=a+(a+d)+(a+2d)+\cdots+\big[a+(n-1)d\big],\\
S_n&=\big[a+(n-1)d\big]+\big[a+(n-2)d\big]+\cdots+a .
\end{aligned}
$$

Adding the two lines column by column, every column sums to the same thing, $2a+(n-1)d$, and there are $n$ columns:

$$
\begin{aligned}
2S_n&=n\big[2a+(n-1)d\big],\\
S_n&=\frac n2\big[2a+(n-1)d\big]=\frac n2(\text{first}+\text{last}).
\end{aligned}
$$

With $a=d=1$ this is the familiar $1+2+\cdots+n=\frac12n(n+1)$.

### How many terms give 341 (Example 7.7)

How many terms of $11+15+19+\cdots$ sum to 341? Here $a=11$ and $d=4$:

$$
\begin{aligned}
341&=\frac n2\big[22+4(n-1)\big]\\
&=\frac n2(4n+18)\\
&=n(2n+9),\\
0&=2n^2+9n-341,\\
n&=\frac{-9\pm\sqrt{81+2728}}{4}=\frac{-9\pm53}{4}.
\end{aligned}
$$

The roots are $n=11$ and $n=-\frac{31}{2}$, and only the positive whole number makes sense, so $n=11$. Check: the 11th term is $11+10(4)=51$, and $\frac{11}{2}(11+51)=341$.

### Sinking a well (Example 7.8)

A contractor charges £30 for the first metre of a 40 m well and £5 more for each metre after. The costs form an AP with $a=30$, $d=5$, $n=40$, so

$$
\begin{aligned}
S_{40}&=\frac{40}{2}\big[2(30)+39(5)\big]=20\times255=£5100,\\
a_{40}&=30+39(5)=£225 .
\end{aligned}
$$

The total is £5100 and the last metre costs £225.

## 3. Geometric sequences and series (James §7.3.2)

A **geometric sequence** (geometric progression, GP) has a constant ratio $r$ between successive terms, $a_k=ar^{k-1}$. Its sum to $n$ terms is

$$
S_n=a+ar+ar^2+\cdots+ar^{n-1}.
$$

Multiply by $r$, which shifts every term one place along:

$$
rS_n=ar+ar^2+\cdots+ar^{n-1}+ar^{n}.
$$

Subtract; everything cancels except the first term of $S_n$ and the last of $rS_n$:

$$
\begin{aligned}
S_n-rS_n&=a-ar^n,\\
(1-r)S_n&=a(1-r^n),\\
S_n&=\frac{a(1-r^n)}{1-r},\qquad r\neq1 .
\end{aligned}
$$

For $r=1$ every term is $a$ and $S_n=na$. For $r>1$ the equivalent form $S_n=\frac{a(r^n-1)}{r-1}$ keeps both brackets positive.

### A guaranteed insurance sum (Example 7.9)

A policy guarantees the return of premiums of £250, paid at the start of each of 25 years, with 3% compound interest. The first premium earns interest for 25 years and is worth $250(1.03)^{25}$ at the end; the last earns it for one year and is worth $250(1.03)$. The total is

$$
\begin{aligned}
S&=250\big[1.03+1.03^2+\cdots+1.03^{25}\big]\\
&=250\times\frac{1.03\,(1.03^{25}-1)}{1.03-1}\\
&=£9388.26,
\end{aligned}
$$

using the GP sum with $a=1.03$, $r=1.03$, $n=25$.

## 4. Limits of sequences (James §7.5)

A sequence $\{a_n\}$ **converges** to the limit $a$, written $a_n\to a$ as $n\to\infty$ or $\lim_{n\to\infty}a_n=a$, if for every $\varepsilon>0$, however small, there is an $N$ such that

$$
|a_n-a|<\varepsilon\qquad\text{for all }n>N .
$$

Beyond the $N$th term every term lies in the band between $a-\varepsilon$ and $a+\varepsilon$; a smaller $\varepsilon$ needs a larger $N$. The limit need not be a term of the sequence: $\{1/n\}$ tends to 0 but never reaches it. A sequence that does not converge **diverges**, either to $\pm\infty$ or by oscillating.

### Rules for combining limits

A convergent sequence is bounded: there is an $M$ with $|a_n|<M$ for all $n$. If $a_n\to a$ and $b_n\to b$, then

$$
a_n\pm b_n\to a\pm b,\qquad a_nb_n\to ab,\qquad \frac{a_n}{b_n}\to\frac ab\quad(b_n\neq0,\ b\neq0).
$$

The sum rule shows how such proofs go. Given $\varepsilon$, choose $N$ so large that $|a_n-a|<\frac\varepsilon2$ and $|b_n-b|<\frac\varepsilon2$ for $n>N$. Then, by the triangle inequality,

$$
\begin{aligned}
\big|(a_n+b_n)-(a+b)\big|&=\big|(a_n-a)+(b_n-b)\big|\\
&\leq|a_n-a|+|b_n-b|\\
&<\tfrac\varepsilon2+\tfrac\varepsilon2=\varepsilon .
\end{aligned}
$$

The product and quotient rules follow from similar inequalities, using the boundedness of $\{a_n\}$.

### Dividing by the highest power (Example 7.22)

(a) $x_n=\dfrac{n}{n+1}$ gives $0,\frac12,\frac23,\frac34,\dots$. Divide top and bottom by $n$:

$$
x_n=\frac{1}{1+1/n}\to\frac{1}{1+0}=1,
$$

using $1/n\to0$, the sum rule for the denominator and the quotient rule.

(b) For a ratio of polynomials in $n$, divide top and bottom by the highest power of $n$ present:

$$
\begin{aligned}
x_n=\frac{2n^2+3n+1}{5n^2+6n+2}&=\frac{2+3/n+1/n^2}{5+6/n+2/n^2}\\
&\to\frac{2+0+0}{5+0+0}=\frac25 .
\end{aligned}
$$

The same step shows that a ratio of polynomials tends to the ratio of the leading coefficients when the degrees are equal, to 0 when the denominator has the higher degree (Booklet Exercise A(a), $\frac{n+1}{n^2+1}\to0$), and diverges when the numerator has.

### Standard limits

Three limits are used constantly.

For $p>0$, $\dfrac1{n^p}\to0$, because $\frac1{n^p}<\varepsilon$ whenever $n>\varepsilon^{-1/p}$.

For $|r|<1$, $r^n\to0$. Taking logarithms, $|r|^n<\varepsilon$ whenever $n\ln|r|<\ln\varepsilon$, that is $n>\ln\varepsilon/\ln|r|$ (dividing by the negative $\ln|r|$ reverses the inequality). For $|r|>1$, $|r^n|\to\infty$; for $r=-1$, $r^n$ oscillates between $\pm1$.

For every fixed $x$, $\dfrac{x^n}{n!}\to0$. Each term is the previous one times $\frac{x}{n+1}$. Once $n+1>2|x|$ that factor has modulus below $\frac12$, so from some $N$ on

$$
\left|\frac{x^{N+j}}{(N+j)!}\right|<\Big(\frac12\Big)^{j}\left|\frac{x^N}{N!}\right|\to0\quad\text{as }j\to\infty .
$$

The terms can grow a long way first: $10^n/n!$ rises to $2755.73$ at $n=9$ and $n=10$, is still $41.10$ at $n=20$, and only falls to $3.77\times10^{-3}$ at $n=30$. The factorial always wins in the end, which is why the exponential series converges for every $x$ ([[#The exponential series (Booklet Exercise D)]]). Finally, $\left(1+\frac1n\right)^n\to e$, which can be taken as the definition of $e$ and is needed in Example 7.29(b).

## 5. Infinite series (James §7.6.1)

An infinite series $\sum_{k}u_k$ **converges** to the sum $S$ if its sequence of partial sums $S_n=u_1+\cdots+u_n$ converges to $S$; otherwise it **diverges**. The definition matters because algebra that is valid for finite sums can fail for infinite ones. Take $S=1-2+4-8+16-\cdots$. Then $2S=2-4+8-16+\cdots$, and adding the two lines term by term leaves $3S=1$, so "$S=\frac13$". The partial sums are $1,-1,3,-5,11,-21,\dots$, which do not settle anywhere: the series diverges and the manipulation was meaningless.

![[m1054_m20_partial_sums.png|900]]

### Four series from their partial sums (Example 7.25)

Each of these has a closed form for $S_n$, so convergence is decided by taking the limit.

(a) $1+3+5+\cdots+(2k+1)+\cdots$ is arithmetic with $a=1$, $d=2$:

$$
S_n=\frac n2\big[2+2(n-1)\big]=n^2\to\infty,
$$

so it diverges.

(b) $1^2+2^2+3^2+\cdots$ has $S_n=\frac16n(n+1)(2n+1)\to\infty$, so it diverges; its terms themselves grow without bound.

(c) $1+\frac12+\frac14+\cdots$ is geometric with $a=1$, $r=\frac12$:

$$
S_n=\frac{1-(1/2)^n}{1-1/2}=2\Big(1-\frac1{2^n}\Big)\to2,
$$

so it converges to 2.

(d) $\frac1{1\cdot2}+\frac1{2\cdot3}+\cdots+\frac1{(k+1)(k+2)}+\cdots$ splits into [[Partial Fractions|partial fractions]],

$$
\frac1{(k+1)(k+2)}=\frac1{k+1}-\frac1{k+2},
$$

so the partial sum **telescopes**, each negative part cancelling the next positive part:

$$
\begin{aligned}
S_n&=\Big(1-\frac12\Big)+\Big(\frac12-\frac13\Big)+\cdots+\Big(\frac1n-\frac1{n+1}\Big)\\
&=1-\frac1{n+1}\to1,
\end{aligned}
$$

and the series converges to 1. The figure above shows (c) and (d) approaching their limits and two divergent series running away.

### The sum to infinity of a geometric series

From the finite sum,

$$
S_n=\frac{a(1-r^n)}{1-r}=\frac{a}{1-r}-\frac{a\,r^n}{1-r}.
$$

The first part does not depend on $n$, and the second tends to 0 exactly when $r^n\to0$, that is when $|r|<1$. So

$$
a+ar+ar^2+\cdots=\frac{a}{1-r},\qquad|r|<1,
$$

and for $|r|\geq1$ the series diverges ($r=1$ gives $S_n=na$, $r=-1$ gives partial sums $a,0,a,0,\dots$, and $|r|>1$ gives terms that grow). The fallacy above is the case $r=-2$, where the formula would give $\frac{1}{1-(-2)}=\frac13$ but the condition fails. Exercise 41(a) is the convergent case $2+\frac23+\frac29+\cdots=\frac{2}{1-1/3}=3$. The same multiply-and-subtract step sums $a+2ar+3ar^2+\cdots=\frac{a}{(1-r)^2}$ for $|r|<1$.

### The nth-term test and the harmonic series

If $\sum u_k$ converges to $S$, then $S_n\to S$ and $S_{n-1}\to S$, so

$$
\begin{aligned}
u_n&=S_n-S_{n-1}\\
&\to S-S=0 .
\end{aligned}
$$

Turned round, this is the **$n$th-term test for divergence**: if $u_n$ does not tend to 0, the series diverges. It can only ever prove divergence. The **harmonic series** $1+\frac12+\frac13+\cdots$ has terms tending to 0 and still diverges. Group its terms in blocks of 1, 2, 4, 8, …, and replace each term in a block by the smallest one in it:

$$
\begin{aligned}
1+\frac12+\Big(\frac13+\frac14\Big)+\Big(\frac15+\cdots+\frac18\Big)+\cdots
&\geq1+\frac12+\Big(\frac14+\frac14\Big)+\Big(\frac18+\cdots+\frac18\Big)+\cdots\\
&=1+\frac12+\frac12+\frac12+\cdots .
\end{aligned}
$$

So $S_{2^m}\geq1+\frac m2$, which is unbounded. The growth is very slow, like $\ln n+0.5772$: $S_{10}=2.929$, $S_{100}=5.187$, $S_{1000}=7.485$.

> [!warning] Terms tending to zero is necessary, not sufficient
> $u_k\to0$ does not show that $\sum u_k$ converges; the harmonic series is the counterexample. The $n$th-term test is a quick first check that can only conclude "diverges". When $u_k\to0$, another test has to decide.

## 6. D'Alembert's ratio test (James §7.6.2)

A series of positive terms has increasing partial sums, so it converges as soon as its partial sums are bounded above, and it diverges to $+\infty$ otherwise. That gives the **comparison test**: if $0\leq u_k\leq c_k$ and $\sum c_k$ converges, then $\sum u_k$ converges too, because its partial sums are bounded by $\sum c_k$. Comparing with a geometric series gives the test used most often.

**D'Alembert's ratio test.** For a series of positive terms $\sum u_k$, let

$$
\ell=\lim_{n\to\infty}\frac{u_{n+1}}{u_n}.
$$

If $\ell<1$ the series converges; if $\ell>1$ it diverges; if $\ell=1$ the test gives no conclusion.

To prove the first part, suppose $\ell<1$ and choose any $r$ with $\ell<r<1$. Because the ratios get arbitrarily close to $\ell$, there is an $N$ with $\frac{u_{n+1}}{u_n}<r$ for all $n\geq N$. Applying this repeatedly,

$$
u_{N+1}<ru_N,\qquad u_{N+2}<ru_{N+1}<r^2u_N,\qquad\dots,\qquad u_{N+j}<r^ju_N .
$$

So from $u_N$ onwards the terms are below those of the geometric series $u_N(1+r+r^2+\cdots)=\frac{u_N}{1-r}$, which converges because $r<1$. By comparison the tail converges, and adding the finitely many terms before $u_N$ does not change that.

If $\ell>1$, then from some $N$ on $\frac{u_{n+1}}{u_n}>1$, so the terms increase and cannot tend to 0; the $n$th-term test gives divergence.

If $\ell=1$, both outcomes occur. The harmonic series has $\frac{n}{n+1}\to1$ and diverges. The series $\sum\frac1{k^2}$ also has ratio $\frac{n^2}{(n+1)^2}\to1$, but it converges: for $k\geq2$, $\frac1{k^2}<\frac1{k(k-1)}=\frac1{k-1}-\frac1k$, which telescopes, so

$$
\begin{aligned}
\sum_{k=1}^{n}\frac1{k^2}&<1+\Big(1-\frac12\Big)+\Big(\frac12-\frac13\Big)+\cdots+\Big(\frac1{n-1}-\frac1n\Big)\\
&=2-\frac1n<2 .
\end{aligned}
$$

(The sum is $\frac{\pi^2}{6}=1.645$.)

For a series with terms of both signs, the test is applied to $|u_k|$. If $\sum|u_k|$ converges the series is **absolutely convergent**, and an absolutely convergent series converges (James §7.6.3).

### The ratio test in action (Example 7.27)

(a) $u_k=\dfrac{2^k}{k!}$:

$$
\begin{aligned}
\frac{u_{n+1}}{u_n}&=\frac{2^{n+1}}{(n+1)!}\cdot\frac{n!}{2^n}\\
&=\frac{2}{n+1}\to0=\ell .
\end{aligned}
$$

Since $\ell<1$ the series converges; its sum is $e^2=7.389$, from the exponential series.

(b) $u_k=\dfrac{2^k}{(k+1)^2}$:

$$
\begin{aligned}
\frac{u_{n+1}}{u_n}&=\frac{2^{n+1}}{(n+2)^2}\cdot\frac{(n+1)^2}{2^n}\\
&=2\Big(\frac{n+1}{n+2}\Big)^2\to2=\ell .
\end{aligned}
$$

Since $\ell>1$ the series diverges.

### When the ratio test fails (Example 7.28)

For $\frac12+\frac23+\frac34+\cdots$, $u_k=\frac{k}{k+1}$ and the ratio $\frac{(n+1)^2}{n(n+2)}\to1$, so the ratio test is silent. The $n$th-term test is not:

$$
u_n=1-\frac1{n+1}\to1\neq0,
$$

so the series diverges. Every term is at least $\frac12$, so $S_n\geq\frac n2$. Specimen Test 20 Q4, $\frac13+\frac24+\frac35+\cdots$, is the same: $u_n=\frac{n}{n+2}\to1$.

## 7. Power series and the radius of convergence (James §7.7)

A **power series** is

$$
a_0+a_1x+a_2x^2+\cdots+a_nx^n+\cdots=\sum_{n=0}^{\infty}a_nx^n,
$$

with coefficients $a_n$ that do not depend on $x$. Whether it converges depends on $x$. Apply the ratio test to the absolute values of the terms:

$$
\begin{aligned}
\left|\frac{a_{n+1}x^{n+1}}{a_nx^n}\right|&=\left|\frac{a_{n+1}}{a_n}\right||x|\\
&\to\frac{|x|}{R},\qquad R=\lim_{n\to\infty}\left|\frac{a_n}{a_{n+1}}\right| .
\end{aligned}
$$

The ratio limit is below 1 when $|x|<R$ and above 1 when $|x|>R$. So the series converges absolutely for $-R<x<R$ and diverges for $|x|>R$, and $R$ is the **radius of convergence**. At $x=\pm R$ the limit is exactly 1 and the test says nothing, so each endpoint has to be checked by another method. $R=\infty$ means convergence for every $x$, and $R=0$ means convergence only at $x=0$.

![[m1054_m20_interval_of_convergence.png|900]]

### Radii 1 and 0 (Example 7.29)

(a) $\displaystyle\sum_{n=1}^\infty\frac{x^n}{n}$ has $a_n=\frac1n$:

$$
\left|\frac{a_n}{a_{n+1}}\right|=\frac{n+1}{n}\to1=R .
$$

It converges for $|x|<1$ and diverges for $|x|>1$. At $x=1$ it is the harmonic series, which diverges. At $x=-1$ it is $-1+\frac12-\frac13+\cdots$, which converges to $-\ln2$ (the series is $-\ln(1-x)$, from the logarithmic series below). The interval of convergence is $-1\leq x<1$.

(b) $\displaystyle\sum_{n=1}^\infty n^nx^n$ has $a_n=n^n$:

$$
\begin{aligned}
\left|\frac{a_n}{a_{n+1}}\right|&=\frac{n^n}{(n+1)^{n+1}}\\
&=\frac{1}{n+1}\cdot\frac{1}{(1+1/n)^n}\\
&\to0\cdot\frac1e=0=R .
\end{aligned}
$$

The series converges only at $x=0$: for any $x\neq0$ the terms $(nx)^n$ grow without bound.

(c) The exponential series $\sum\frac{x^n}{n!}$ has $\left|\frac{a_n}{a_{n+1}}\right|=\frac{(n+1)!}{n!}=n+1\to\infty$, so $R=\infty$.

### Standard power series

The standard series (James Figure 7.13) are below; the radius of each follows from the ratio test as above. The most-used ones are on the formula sheet and in the Data Book.

| Series | Valid for |
|---|---|
| $\dfrac1{1+x}=1-x+x^2-x^3+\cdots$ | $-1<x<1$ |
| $\dfrac1{1-x}=1+x+x^2+x^3+\cdots$ | $-1<x<1$ |
| $(1+x)^r=1+rx+\dfrac{r(r-1)}{2!}x^2+\cdots+\dbinom rn x^n+\cdots$ | $-1<x<1$ ($r$ not a whole number) |
| $\ln(1+x)=x-\dfrac{x^2}2+\dfrac{x^3}3-\cdots$ | $-1<x\leq1$ |
| $\ln(1-x)=-x-\dfrac{x^2}2-\dfrac{x^3}3-\cdots$ | $-1\leq x<1$ |
| $e^x=1+x+\dfrac{x^2}{2!}+\dfrac{x^3}{3!}+\cdots$ | all $x$ |
| $\sin x=x-\dfrac{x^3}{3!}+\dfrac{x^5}{5!}-\cdots$, $\cos x=1-\dfrac{x^2}{2!}+\dfrac{x^4}{4!}-\cdots$ | all $x$ (radians) |
| $\sinh x=x+\dfrac{x^3}{3!}+\cdots$, $\cosh x=1+\dfrac{x^2}{2!}+\cdots$ | all $x$ |

Here $\binom rn=\frac{r(r-1)\cdots(r-n+1)}{n!}$; when $r$ is a positive whole number the binomial series stops at $x^r$ and is valid for all $x$. Power series can be added, multiplied and divided where they all converge, and substituting the $e^x$, $\sin x$ and $\cos x$ series into $e^{jx}$ proves [[Euler's Formula]].

## 8. Rolle's theorem and the mean value theorems (James §9.3.1)

**Rolle's theorem.** If $f$ is continuous on $[a,b]$, differentiable on $(a,b)$, and $f(a)=f(b)$, then there is at least one $c$ with $a<c<b$ and $f'(c)=0$.

A continuous function on a closed interval attains a maximum and a minimum there. If both are attained at the end points, then, since $f(a)=f(b)$, the maximum equals the minimum, $f$ is constant and $f'(c)=0$ for every $c$. Otherwise one of them, say the maximum, is at an interior point $c$. For small $h>0$, $f(c+h)\leq f(c)$ and $f(c-h)\leq f(c)$, so

$$
\frac{f(c+h)-f(c)}{h}\leq0,\qquad\frac{f(c-h)-f(c)}{-h}\geq0 .
$$

Both quotients tend to $f'(c)$ as $h\to0$, so $f'(c)\leq0$ and $f'(c)\geq0$, which forces $f'(c)=0$. Geometrically, somewhere between $a$ and $b$ the tangent is horizontal: there is a [[Stationary Points and Inflection|stationary point]].

The theorem only needs differentiability on the open interval, so it holds for the upper semicircle $y=\sqrt{1-x^2}$ on $[-1,1]$, whose slope is infinite at the end points. It fails without its hypotheses. $f(x)=1-|x|$ on $[-1,1]$ has $f(-1)=f(1)=0$ but slope $\pm1$ everywhere except the corner at $0$, where it is not differentiable. $f(x)=x$ on $[0,1)$ with $f(1)=0$ has equal end values but slope 1 throughout, because of the jump at $x=1$. The theorem also says nothing about where $c$ is, or how many there are. For $f(x)=x(x-1)(x-3)$ on $[0,3]$,

$$
\begin{aligned}
f'(x)&=3x^2-8x+3=0,\\
c&=\frac{8\pm\sqrt{64-36}}{6}=\frac{4\pm\sqrt7}{3}=0.451\ \text{or}\ 2.215,
\end{aligned}
$$

two points, both inside $(0,3)$.

![[m1054_m20_mean_value_theorems.png|900]]

**The first mean value theorem of integral calculus.** If $f$ is continuous on $[a,b]$, there is a $c$ with $a<c<b$ and

$$
f(c)=\frac{1}{b-a}\int_a^bf(x)\,dx .
$$

Let $m$ and $M$ be the minimum and maximum of $f$ on $[a,b]$. Integrating $m\leq f(x)\leq M$,

$$
\begin{aligned}
m(b-a)&\leq\int_a^bf\,dx\leq M(b-a),\\
m&\leq\frac{1}{b-a}\int_a^bf\,dx\leq M,
\end{aligned}
$$

and a continuous function takes every value between its minimum and maximum (the intermediate value theorem), so it takes the mean value at some $c$. The area under the curve equals the area of a rectangle of width $b-a$ and height $f(c)$. For $\sin x$ on $[0,\pi]$, $\int_0^\pi\sin x\,dx=2$, the mean is $\frac2\pi=0.6366$, and $\sin c=0.6366$ at $c=0.690$ and $c=2.451$; again $c$ need not be unique.

**The first mean value theorem of differential calculus.** If $f$ is continuous on $[a,b]$ and differentiable on $(a,b)$, there is a $c$ with $a<c<b$ and

$$
\frac{f(b)-f(a)}{b-a}=f'(c).
$$

The proof applies Rolle's theorem to $f$ minus the chord through its end points,

$$
g(x)=f(x)-f(a)-\frac{f(b)-f(a)}{b-a}(x-a).
$$

Then $g(a)=0$ and $g(b)=f(b)-f(a)-\big(f(b)-f(a)\big)=0$, and $g$ is as smooth as $f$, so Rolle gives a $c$ with $g'(c)=0$:

$$
\begin{aligned}
g'(c)=f'(c)-\frac{f(b)-f(a)}{b-a}&=0,\\
f'(c)&=\frac{f(b)-f(a)}{b-a}.
\end{aligned}
$$

When $f'$ is continuous the same result follows from the integral theorem applied to $f'$: $\int_a^bf'\,dx=f(b)-f(a)=(b-a)f'(c)$. At some point the tangent is parallel to the chord. For $f(x)=x^3$ on $[0,2]$ the chord slope is $\frac{8-0}{2-0}=4$, and $3c^2=4$ gives $c=\frac{2}{\sqrt3}=1.155$. Writing $b=a+h$ and $c=a+\theta h$ with $0<\theta<1$ puts the theorem in the form

$$
f(a+h)=f(a)+hf'(a+\theta h),
$$

which is Taylor's theorem with $n=0$.

## 9. Taylor's theorem and the Lagrange remainder (James §9.4.1)

### A polynomial from four derivatives (Example 9.8)

Find a polynomial with $f(0)=3$, $f'(0)=4$, $f''(0)=-10$ and $f'''(0)=12$. Four conditions fix a cubic $p(x)=a+bx+cx^2+dx^3$. Match the value and each derivative at $0$ in turn:

$$
\begin{aligned}
p(0)&=a=3,\\
p'(x)=b+2cx+3dx^2,\quad p'(0)&=b=4,\\
p''(x)=2c+6dx,\quad p''(0)&=2c=-10\ \Rightarrow\ c=-5,\\
p'''(x)=6d,\quad p'''(0)&=6d=12\ \Rightarrow\ d=2,
\end{aligned}
$$

so $p(x)=3+4x-5x^2+2x^3$. Each coefficient is $f^{(k)}(0)/k!$, because $k$ differentiations of $x^k$ leave $k!$. In general the **Taylor polynomial** of degree $n$ about $x=a$,

$$
p_n(x)=f(a)+(x-a)f'(a)+\frac{(x-a)^2}{2!}f''(a)+\cdots+\frac{(x-a)^n}{n!}f^{(n)}(a),
$$

matches $f$ and its first $n$ derivatives at $a$. About $a=1$, for example, the data $f(1)=4$, $f'(1)=0$, $f''(1)=2$, $f'''(1)=12$ give $p(x)=4+(x-1)^2+2(x-1)^3$ (James Example 9.9).

### Deriving Taylor's theorem

**Taylor's theorem.** If $f,f',\dots,f^{(n)}$ are continuous on $[a,x]$ and $f^{(n+1)}$ exists on $(a,x)$, then

$$
f(x)=p_n(x)+R_n(x),\qquad R_n(x)=\frac{(x-a)^{n+1}}{(n+1)!}f^{(n+1)}(a+\theta h),\quad h=x-a,\ 0<\theta<1 .
$$

$R_n$ in this form is **Lagrange's form of the remainder**. The theorem follows from Rolle's theorem. Fix $x$, and for $t$ between $a$ and $x$ define

$$
F(t)=f(x)-\sum_{k=0}^{n}\frac{f^{(k)}(t)}{k!}(x-t)^k-K\frac{(x-t)^{n+1}}{(n+1)!},
$$

with the constant $K$ chosen so that $F(a)=0$:

$$
K=\frac{(n+1)!}{(x-a)^{n+1}}\big[f(x)-p_n(x)\big].
$$

At $t=x$ every term with a factor $(x-t)$ vanishes and the $k=0$ term is $f(x)$, so $F(x)=f(x)-f(x)=0$. Rolle's theorem therefore gives a $c$ strictly between $a$ and $x$ with $F'(c)=0$. To differentiate $F$, take one term of the sum at a time with the product rule:

$$
\frac{d}{dt}\left[\frac{f^{(k)}(t)}{k!}(x-t)^k\right]=\frac{f^{(k+1)}(t)}{k!}(x-t)^k-\frac{f^{(k)}(t)}{(k-1)!}(x-t)^{k-1}\qquad(k\geq1),
$$

and the $k=0$ term differentiates to $f'(t)$. Written out, the sum telescopes, each negative part cancelling the positive part of the term before:

$$
\begin{aligned}
\frac{d}{dt}\sum_{k=0}^{n}\frac{f^{(k)}(t)}{k!}(x-t)^k&=f'(t)+\Big[f''(t)(x-t)-f'(t)\Big]+\Big[\frac{f'''(t)}{2!}(x-t)^2-f''(t)(x-t)\Big]+\cdots\\
&=\frac{f^{(n+1)}(t)}{n!}(x-t)^n .
\end{aligned}
$$

The last term of $F$ differentiates to $+K\frac{(x-t)^n}{n!}$, so

$$
\begin{aligned}
F'(t)&=-\frac{f^{(n+1)}(t)}{n!}(x-t)^n+K\frac{(x-t)^n}{n!}\\
&=\frac{(x-t)^n}{n!}\Big[K-f^{(n+1)}(t)\Big].
\end{aligned}
$$

At $t=c\neq x$ the factor $(x-c)^n$ is not zero, so $F'(c)=0$ gives $K=f^{(n+1)}(c)$. Equating the two expressions for $K$,

$$
f(x)-p_n(x)=\frac{(x-a)^{n+1}}{(n+1)!}f^{(n+1)}(c),
$$

and writing $c=a+\theta h$ with $0<\theta<1$ gives the theorem. With $n=0$ it is the mean value theorem, which is why Taylor's theorem is also called the $n$th mean value theorem. Replacing $x$ by $a+x$ gives the equivalent form (James 9.11) used on the formula sheet:

$$
f(a+x)=f(a)+xf'(a)+\frac{x^2}{2!}f''(a)+\cdots+\frac{x^n}{n!}f^{(n)}(a)+\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(a+\theta x).
$$

### Maclaurin's theorem

Putting $a=0$ gives **Maclaurin's theorem**, the statement Specimen Test 20 Q5 asks for:

$$
f(x)=f(0)+xf'(0)+\frac{x^2}{2!}f''(0)+\cdots+\frac{x^n}{n!}f^{(n)}(0)+R_n(x),\qquad R_n(x)=\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(\theta x),\quad0<\theta<1 .
$$

The value of $\theta$ is not known, and it depends on $x$ and $n$, but knowing $0<\theta<1$ and the form of $f^{(n+1)}$ is usually enough to bound $|R_n|$. Note the labelling: $R_n$ contains $x^{n+1}$ and follows the $x^n$ term; many books call the same quantity $R_{n+1}$. "Two terms and a remainder" means $f(0)+xf'(0)+R_1(x)$.

> [!tip] The remainder is the next term, evaluated somewhere else
> $R_n$ looks exactly like the next term of the series, $\frac{x^{n+1}}{(n+1)!}f^{(n+1)}(0)$, except that the derivative is taken at the unknown point $\theta x$ instead of at $0$. So the error of a truncated Maclaurin series is roughly the first omitted term, and the bound comes from asking how large $f^{(n+1)}$ can be anywhere between $0$ and $x$.

### Booklet Example 1: sin x ≈ x

Show that writing $\sin x$ as $x$ has error less than $0.005$ for $0<x<0.1$. With $f=\sin x$, $f'=\cos x$ and $f''=-\sin x$, Maclaurin's theorem with two terms and a remainder is

$$
\begin{aligned}
\sin x&=\sin0+x\cos0+\frac{x^2}{2!}\big(-\sin\theta x\big)\\
&=x+R_1,\qquad R_1=-\frac{x^2}{2}\sin\theta x,\quad0<\theta<1 .
\end{aligned}
$$

Since $|\sin\theta x|\leq1$,

$$
|R_1|\leq\frac{x^2}{2}<\frac{(0.1)^2}{2}=0.005\qquad(0<x<0.1).
$$

The bound is safe but generous: the actual error at $x=0.1$ is $0.1-\sin0.1=1.67\times10^{-4}$, close to the next series term $\frac{x^3}{6}$, because $|\sin\theta x|\leq\theta x<0.1$ is far below the crude bound of 1.

### Booklet Exercise B: cos x ≈ 1 − x²/2

For $f=\cos x$: $f(0)=1$, $f'(0)=0$, $f''(0)=-1$, $f'''(0)=0$ and $f^{(4)}(x)=\cos x$. The $x^3$ term is zero, so take $n=3$:

$$
\cos x=1-\frac{x^2}{2}+R_3(x),\qquad R_3(x)=\frac{x^4}{4!}\cos\theta x,\quad0<\theta<1 .
$$

For $0<x<\frac\pi2$, $0<\theta x<\frac\pi2$, so $0<\cos\theta x<1$, and

$$
0<R_3(x)<\frac{x^4}{4!}.
$$

At $x=\frac{\pi}{10}$ the maximum error is

$$
\frac{(\pi/10)^4}{24}=4.06\times10^{-4}.
$$

> [!check] Calculator comparison at x = π/10
> $\cos\frac\pi{10}=0.951057$ and $1-\frac12\big(\frac\pi{10}\big)^2=0.950652$, so the actual error is $4.05\times10^{-4}$: positive, as $R_3>0$ predicts, and just below the bound $4.06\times10^{-4}$. The bound is nearly attained because $\cos\theta x$ is close to 1 for small $x$; here $\theta=0.258$.

In the left panel below, $1-\frac{x^2}{2}$ and $1-\frac{x^2}{2}+\frac{x^4}{24}$ follow $\cos x$ closely near the origin, the quadratic departing visibly beyond $|x|\approx1$ and the quartic beyond $|x|\approx2$; the right panel shows the actual error lying just under the bound $\frac{x^4}{24}$ across $0<x<\frac\pi2$.

![[m1054_maclaurin_cos.png|900]]

### Booklet Exercise C: the square root of 1.02

For $f=(1+x)^{1/2}$, $f'=\frac12(1+x)^{-1/2}$ and $f''=-\frac14(1+x)^{-3/2}$, so $f(0)=1$, $f'(0)=\frac12$, and with two terms and a remainder

$$
\begin{aligned}
(1+x)^{1/2}&=1+\tfrac12x+R_1(x),\\
R_1(x)&=\frac{x^2}{2!}f''(\theta x)=-\frac{x^2}{8(1+\theta x)^{3/2}},\qquad0<\theta<1 .
\end{aligned}
$$

For $x=0.02>0$, $(1+\theta x)^{3/2}>1$, so

$$
|R_1|<\frac{(0.02)^2}{8}=\frac{0.0004}{8}=0.00005 .
$$

So $\sqrt{1.02}\approx1.01$ with error at most $5\times10^{-5}$, and since $R_1<0$, $1.01$ is an over-estimate. The true value is $\sqrt{1.02}=1.0099505$, an error of $4.95\times10^{-5}$. Specimen Test 20 Q7 is the same calculation for $(1+x)^{2/3}=1+\frac23x+R_1$, with $R_1=-\frac{x^2}{9(1+\theta x)^{4/3}}$, giving $|R_1|<\frac{x^2}{9}<0.01$ for $0<x<0.3$ (actual error $0.0089$ at $x=0.3$).

![[m1054_m20_lagrange_bounds.png|900]]

## 10. Taylor and Maclaurin series (James §9.4.2)

If $R_n(x)\to0$ as $n\to\infty$, the Taylor polynomials converge to $f(x)$ and $f$ equals its **Taylor series** about $a$,

$$
f(a+x)=\sum_{n=0}^{\infty}\frac{x^n}{n!}f^{(n)}(a),
$$

and with $a=0$ its **Maclaurin series**,

$$
f(x)=\sum_{n=0}^{\infty}\frac{x^n}{n!}f^{(n)}(0).
$$

The remainder may tend to zero only on a restricted interval, or not at all, in which case the series represents $f$ only on its interval of convergence. The standard series, and how to build new ones by multiplying, substituting and integrating known ones, are in [[Taylor and Maclaurin Series]].

### The exponential series (Booklet Exercise D)

Every derivative of $e^x$ is $e^x$, and $e^0=1$, so every coefficient is $\frac1{n!}$:

$$
e^x=1+x+\frac{x^2}{2!}+\frac{x^3}{3!}+\cdots=\sum_{n=0}^{\infty}\frac{x^n}{n!}.
$$

The ratio test gives $\left|\frac{x}{n+1}\right|\to0$, so the series converges for all $x$. It also converges to $e^x$, because the remainder

$$
|R_n(x)|=\frac{|x|^{n+1}}{(n+1)!}e^{\theta x}\leq\frac{|x|^{n+1}}{(n+1)!}e^{|x|}
$$

is a constant times $\frac{|x|^{n+1}}{(n+1)!}$, which tends to 0 by the standard limit of §4. The same bound sizes a truncation. With $x=1$ and $n=5$,

$$
e\approx1+1+\frac1{2!}+\frac1{3!}+\frac1{4!}+\frac1{5!}=2.716667,\qquad0<R_5=\frac{e^{\theta}}{6!}<\frac{3}{720}=0.00417,
$$

using $e^\theta<e<3$. The actual error is $0.00162$.

### The series of e to the x times sin x (Example 9.10)

For $f(x)=e^x\sin x$, the product rule and the identity $\sin x+\cos x=\sqrt2\sin\big(x+\frac\pi4\big)$ give

$$
\begin{aligned}
f'(x)&=e^x(\sin x+\cos x)\\
&=\sqrt2\,e^x\sin\big(x+\tfrac\pi4\big).
\end{aligned}
$$

The identity holds because $\sin\big(x+\frac\pi4\big)=\sin x\cos\frac\pi4+\cos x\sin\frac\pi4=\frac{1}{\sqrt2}(\sin x+\cos x)$. So differentiating multiplies by $\sqrt2$ and adds $\frac\pi4$ to the argument of the sine, and repeating,

$$
f^{(k)}(x)=(\sqrt2)^k\,e^x\sin\big(x+\tfrac{k\pi}{4}\big),\qquad f^{(k)}(0)=(\sqrt2)^k\sin\tfrac{k\pi}{4}.
$$

For $k=0,1,\dots,6$ this gives $0,1,2,2,0,-4,-8$, and the Maclaurin series is

$$
\begin{aligned}
e^x\sin x&=0+x+\frac{2}{2!}x^2+\frac{2}{3!}x^3+0-\frac{4}{5!}x^5-\cdots\\
&=x+x^2+\frac{x^3}{3}-\frac{x^5}{30}-\cdots .
\end{aligned}
$$

The remainder is

$$
R_n(x)=\frac{(\sqrt2\,x)^{n+1}}{(n+1)!}\,e^{\theta x}\sin\Big[\theta x+\frac{(n+1)\pi}{4}\Big],\qquad0<\theta<1,
$$

and with $|\sin|\leq1$ and $e^{\theta x}\leq e^{|x|}$, $|R_n|\leq e^{|x|}\frac{(\sqrt2|x|)^{n+1}}{(n+1)!}\to0$ for every $x$, so the series converges to $e^x\sin x$ everywhere. Multiplying the series for $e^x$ and $\sin x$ gives the same terms with far less work (James Example 9.11; see [[MATH1054 M08 - Differentiation II|Module 8]]).

## 11. L'Hôpital's rule (James §9.4.3)

If $f(x)\to A$ and $g(x)\to B\neq0$ as $x\to a$, then $\frac{f}{g}\to\frac AB$. When $B=0$ a finite limit is only possible if $A=0$ too, and then substitution gives the indeterminate form $\frac00$. **L'Hôpital's rule:** if $f(a)=g(a)=0$, then

$$
\lim_{x\to a}\frac{f(x)}{g(x)}=\lim_{x\to a}\frac{f'(x)}{g'(x)},
$$

provided the right-hand limit exists. The derivatives of numerator and denominator are taken separately; this is not the quotient rule.

### Deriving the rule

Near $a$ each function is approximately its tangent line, and the constant terms vanish:

$$
\frac{f(x)}{g(x)}=\frac{f(a)+(x-a)f'(a)+\cdots}{g(a)+(x-a)g'(a)+\cdots}=\frac{f'(a)+\frac12(x-a)f''(a)+\cdots}{g'(a)+\frac12(x-a)g''(a)+\cdots}\to\frac{f'(a)}{g'(a)},
$$

valid when $g'(a)\neq0$. A proof that covers repeated use needs the **Cauchy mean value theorem**, which comes from Rolle's theorem. For $x$ near $a$, with $f$ and $g$ differentiable and $g'\neq0$ between $a$ and $x$, let

$$
h(t)=\big[f(x)-f(a)\big]g(t)-\big[g(x)-g(a)\big]f(t).
$$

Expanding, $h(a)=f(x)g(a)-g(x)f(a)$ and $h(x)=-f(a)g(x)+g(a)f(x)$, which are equal. Rolle's theorem gives a $c$ between $a$ and $x$ with $h'(c)=0$:

$$
\big[f(x)-f(a)\big]g'(c)=\big[g(x)-g(a)\big]f'(c).
$$

With $f(a)=g(a)=0$ this reads

$$
\frac{f(x)}{g(x)}=\frac{f'(c)}{g'(c)},
$$

where $g(x)\neq0$ because $g(x)=g(x)-g(a)=(x-a)g'(\xi)$ for some $\xi$ between $a$ and $x$, by the mean value theorem. As $x\to a$ the point $c$, trapped between $a$ and $x$, also tends to $a$, so if $\frac{f'}{g'}$ has a limit $L$ at $a$, then $\frac fg\to L$ as well. If $\frac{f'}{g'}$ is again $\frac00$ at $a$, the same argument applies to $f'$ and $g'$, so the rule can be repeated. If at some stage one of the derivatives is non-zero at $a$, the form is no longer indeterminate and the rule no longer applies; the limit is then found by substitution, and may be zero, infinite or non-existent (as for $\lim_{x\to0}\frac1x$).

### Two limits by L'Hôpital's rule (Example 9.14)

(a) $\dfrac{\sin x-x}{x^3}$ is $\frac00$ at $x=0$. Differentiate top and bottom separately, checking the form each time:

$$
\begin{aligned}
\lim_{x\to0}\frac{\sin x-x}{x^3}&=\lim_{x\to0}\frac{\cos x-1}{3x^2}\qquad\Big(\text{still }\tfrac00\Big)\\
&=\lim_{x\to0}\frac{-\sin x}{6x}\qquad\Big(\text{still }\tfrac00\Big)\\
&=\lim_{x\to0}\frac{-\cos x}{6}=-\frac16 .
\end{aligned}
$$

It takes three applications, because the first two quotients are still $\frac00$. The series give the same answer at once: $\sin x-x=-\frac{x^3}{6}+\frac{x^5}{120}-\cdots$, so $\frac{\sin x-x}{x^3}=-\frac16+\frac{x^2}{120}-\cdots\to-\frac16$.

(b) $\dfrac{1-\cos x}{x+x^2}$ is $\frac00$ at $x=0$:

$$
\lim_{x\to0}\frac{1-\cos x}{x+x^2}=\lim_{x\to0}\frac{\sin x}{1+2x}=\frac01=0 .
$$

The quotient $\frac{\sin x}{1+2x}$ is $\frac01$ at $x=0$, which is not indeterminate, so the process stops and the limit is 0.

> [!warning] Stop as soon as the form is determinate
> Differentiating once more in (b) would give $\lim\frac{\cos x}{2}=\frac12$, a wrong answer: the rule only applies to $\frac00$ and $\frac\infty\infty$. Check the form before every application, and differentiate numerator and denominator separately rather than applying the quotient rule to $\frac fg$.

The same pattern answers Specimen Test 20 Q6: $\lim_{x\to0}\frac{\cos x-1}{x^2}=\lim\frac{-\sin x}{2x}=\lim\frac{-\cos x}{2}=-\frac12$.

### Infinity over infinity (Booklet Example 2)

The rule also holds when $f$ and $g$ both tend to $\pm\infty$, and when $x\to\pm\infty$. For $x\to\infty$ with $\frac{f'}{g'}\to L$: fix a large $N$ and apply the Cauchy mean value theorem on $[N,x]$,

$$
\frac{f(x)-f(N)}{g(x)-g(N)}=\frac{f'(c)}{g'(c)},\qquad N<c<x,
$$

so the left side is close to $L$ once $N$ is large enough. Dividing top and bottom of the left side by $g(x)$,

$$
\frac{f(x)-f(N)}{g(x)-g(N)}=\frac{f(x)}{g(x)}\cdot\frac{1-f(N)/f(x)}{1-g(N)/g(x)},
$$

and with $N$ fixed and $f,g\to\infty$ the second factor tends to 1, so $\frac{f(x)}{g(x)}$ is also close to $L$. For example, $x\to\infty$ and $e^x\to\infty$, so

$$
\lim_{x\to\infty}\frac{x}{e^x}=\lim_{x\to\infty}\frac{1}{e^x}=0 .
$$

The exponential series confirms it: for $x>0$, $e^x>\frac{x^2}{2}$, so $0<\frac{x}{e^x}<\frac2x\to0$.

## Terminology and alternative names

| Course term (James, booklet) | Also called | Note |
|---|---|---|
| arithmetical sequence, arithmetical series | arithmetic progression (AP) | James notes that "progression" is the old name |
| geometric sequence, geometric series | geometric progression (GP) | |
| d'Alembert's ratio test | ratio test | |
| first mean value theorem (of differential calculus) | mean value theorem, Lagrange's mean value theorem | Taylor's theorem is the $n$th mean value theorem |
| $R_n(x)$, the remainder containing $x^{n+1}$ | $R_{n+1}(x)$ in many other books | the booklet keeps James's $R_n$ throughout |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M20 Solutions - Further Calculus II]]
- Previous: [[MATH1054 M18 - Matrices III]] · Prerequisite: [[MATH1054 M08 - Differentiation II]] (Maclaurin series, stationary points) · Next: [[MATH1054 M22 - Complex Numbers II]]
- Concepts: [[Arithmetic and Geometric Series]] · [[Convergence Tests for Series]] · [[Taylor and Maclaurin Series]] · [[L'Hôpital's Rule]] · [[Partial Fractions]] · [[Stationary Points and Inflection]] · [[Euler's Formula]] · [[Improper Integrals]]
- Later: Fourier series are series of functions whose convergence is treated in [[Fourier's Theorem]]; [[MATH2048 FS1 - Fourier Series, Orthogonality and the Euler Formulae]] sums $1+\frac19+\frac1{25}+\cdots=\frac{\pi^2}{8}$ by evaluating a Fourier series at a point. The Lagrange remainder is the truncation error of finite differences in [[Truncation Error and Order of Accuracy]] and [[Taylor Table Method]] (SESA2029), and the mean value theorem underlies the convergence of the iterations in [[Direct Substitution and Newton-Raphson]].

## Sources

- MATH1054 Module Booklet, Module 20 work scheme (pp. 1–5 of the module, PDF pp. 70–74) and Specimen Test 20 (p. 6, PDF p. 75), including Booklet Examples 1 and 2 and Exercises A–D.
- James, *Modern Engineering Mathematics* (6th ed.): §7.1–7.3 (pp. 471–484), §7.5 (pp. 498–502), §7.6 (pp. 506–511), §7.7 (pp. 513–517), §9.3.1 (pp. 708–710), §9.4.1–9.4.3 (pp. 715–725).
- Worked solutions to every work-scheme item: [[MATH1054 M20 Solutions - Further Calculus II]].

## Self-study tasks

### Core

- [ ] Exercise 14 (Module 20 work scheme, James p. 484): terms of an arithmetic and a geometric sequence. → [[MATH1054 M20 Solutions - Further Calculus II#Exercise 14|solution]]
- [ ] Exercise A (Module 20 work scheme) and Exercise 41 (James p. 512): limits of two sequences, and which geometric series converge. → [[MATH1054 M20 Solutions - Further Calculus II#Booklet Exercise A: Limits of sequences|Exercise A]] · [[MATH1054 M20 Solutions - Further Calculus II#Exercise 41: Geometric series|Exercise 41]]
- [ ] Exercises B and C (Module 20 work scheme): Lagrange-remainder bounds for $\cos x\approx1-\frac12x^2$ and $\sqrt{1.02}\approx1.01$. → [[#Booklet Exercise B: cos x ≈ 1 − x²/2]] · [[#Booklet Exercise C: the square root of 1.02]] · [[MATH1054 M20 Solutions - Further Calculus II#Part B: Assigned exercises|solutions]]
- [ ] Exercise 19(a), (b), (c), (e) (Module 20 work scheme, James p. 725): four limits by L'Hôpital's rule. Answers $\frac34$, $\frac14$, $-\frac32$, $-\frac13$. → [[MATH1054 M20 Solutions - Further Calculus II#Exercise 19: L'Hôpital's rule|solution]]
- [ ] Specimen Test 20, Q1–Q7, timed. → [[MATH1054 M20 Solutions - Further Calculus II#Part C: Specimen Test 20|solutions]]

### Further practice

- [ ] Exercise D (Module 20 work scheme): the Maclaurin series of $e^x$, and show that its remainder tends to 0. → [[#The exponential series (Booklet Exercise D)]] · [[MATH1054 M20 Solutions - Further Calculus II#Part B: Assigned exercises|solution]]
- [ ] Example 7.29(b) and Example 7.25(b), (d) (James pp. 506–514; the work scheme sets only parts (a) and (c) of 7.25 and part (a) of 7.29). → [[#Radii 1 and 0 (Example 7.29)]] · [[MATH1054 M20 Solutions - Further Calculus II#Example 7.25: Convergence of series|solution]]
- [ ] Prove the first mean value theorem from Rolle's theorem using $g(x)=f(x)-f(a)-\frac{f(b)-f(a)}{b-a}(x-a)$ (Module 20 work scheme, item 11). → [[#8. Rolle's theorem and the mean value theorems (James §9.3.1)]]
- [ ] Example 9.10 (Module 20 work scheme, item 15): the Maclaurin series of $e^x\sin x$ by repeated differentiation, then check it by multiplying the series of $e^x$ and $\sin x$. → [[#The series of e to the x times sin x (Example 9.10)]] · [[MATH1054 M20 Solutions - Further Calculus II#Part A: Worked examples|solution]]
- [ ] Redo Booklet Example 1 with three terms and a remainder, $\sin x=x+R_2$, and show the error is below $1.7\times10^{-4}$ for $0<x<0.1$ (suggested, not set). → [[#Booklet Example 1: sin x ≈ x]]

## Transcript and slide slips

> [!warning] James, Example 7.2 (p. 472)
> Where: [[#Cable ducts (Example 7.2)]].
>
> James prints $D_5=\frac14\sqrt{2(5-\sqrt5)}\,d\approx0.588d$, which is impossible because it is smaller than $D_1=d$. The printed quantity is $\sin36^\circ$; the duct diameter for five cables is $D_5=\big(1+\frac{1}{\sin36^\circ}\big)d=2.701d$.

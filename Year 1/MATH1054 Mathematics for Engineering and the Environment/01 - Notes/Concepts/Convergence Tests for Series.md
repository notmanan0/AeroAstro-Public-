---
title: "Convergence Tests for Series"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Ratio test", "d'Alembert's ratio test", "Radius of convergence", "nth term test"]
tags: [math1054, concept, series]
status: complete
parent_lectures: ["[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Arithmetic and Geometric Series]]", "[[Taylor and Maclaurin Series]]", "[[Improper Integrals]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §7.6–7.7", "MATH1054 Module Booklet, Module 20"]
---

# Convergence Tests for Series

An infinite series $\sum a_k$ converges if its partial sums $S_n=a_1+\cdots+a_n$ tend to a finite limit, and convergence tests decide this without finding the sum. The ones used in MATH1054 are the $n$th-term test, the geometric and telescoping sums, and d'Alembert's ratio test, which for a power series gives the radius of convergence.

The **$n$th-term test** comes from $a_n=S_n-S_{n-1}$: if the series converges to $S$, then $a_n\to S-S=0$. So if $a_k\not\to0$ the series diverges, as for $\frac12+\frac23+\frac34+\cdots$, whose terms tend to 1. The converse is false. The harmonic series $\sum\frac1k$ has terms tending to 0, yet grouping them in blocks of 1, 2, 4, 8, … shows each block is at least $\frac12$, so its partial sums grow without bound (slowly: $S_{1000}=7.485$).

Some series can be summed outright. A geometric series $\sum ar^k$ converges if and only if $|r|<1$, to $\frac{a}{1-r}$ ([[Arithmetic and Geometric Series]]). A **telescoping** series collapses after partial fractions: $\frac1{(k+1)(k+2)}=\frac1{k+1}-\frac1{k+2}$, so $\sum_{k=0}^{n-1}\frac1{(k+1)(k+2)}=1-\frac1{n+1}\to1$.

**D'Alembert's ratio test** handles the rest. For positive terms let $\ell=\lim\frac{a_{k+1}}{a_k}$. If $\ell<1$, pick $r$ with $\ell<r<1$; from some term $a_N$ on each term is less than $r$ times the one before, so the tail is smaller than the convergent geometric series $a_N(1+r+r^2+\cdots)$ and the series converges. If $\ell>1$ the terms eventually increase, cannot tend to 0, and the series diverges. If $\ell=1$ the test says nothing: $\sum\frac1k$ diverges and $\sum\frac1{k^2}$ converges, and both have $\ell=1$. For terms of either sign the test is applied to $|a_k|$, and absolute convergence implies convergence.

Two examples (James 7.27):

$$
\begin{aligned}
a_k=\frac{2^k}{k!}:&\qquad\frac{a_{k+1}}{a_k}=\frac{2}{k+1}\to0,\ \text{so it converges (to }e^2=7.389),\\
a_k=\frac{2^k}{(k+1)^2}:&\qquad\frac{a_{k+1}}{a_k}=2\Big(\frac{k+1}{k+2}\Big)^2\to2,\ \text{so it diverges.}
\end{aligned}
$$

Applied to a **power series** $\sum c_nx^n$, the ratio of successive terms tends to $|x|\lim\left|\frac{c_{n+1}}{c_n}\right|$, which is below 1 exactly when $|x|<R$ with

$$
R=\lim_{n\to\infty}\left|\frac{c_n}{c_{n+1}}\right| .
$$

So the series converges for $|x|<R$ and diverges for $|x|>R$. $\sum\frac{x^n}{n}$ has $R=\frac{n+1}{n}\to1$; $\sum n^nx^n$ has $R=0$ and converges only at $x=0$; $\sum\frac{x^n}{n!}=e^x$ has $R=\infty$ (James 7.29).

The trap is at the edge. At $x=\pm R$ the ratio limit is exactly 1 and the endpoints need separate treatment: $\sum\frac{x^n}{n}$ diverges at $x=1$ (the harmonic series) but converges at $x=-1$, to $-\ln2$, so its interval of convergence is $-1\leq x<1$. The same borderline appears for [[Improper Integrals]]: $\int_1^\infty x^{-p}\,dx$ converges only for $p>1$, and $\sum k^{-p}$ behaves the same way at $p=1$ and $p=2$.

## Related

- Topics: [[MATH1054 M20 - Further Calculus II#5. Infinite series (James §7.6.1)|M20 §5]] · [[MATH1054 M20 - Further Calculus II#6. D'Alembert's ratio test (James §7.6.2)|M20 §6]] · [[MATH1054 M20 - Further Calculus II#7. Power series and the radius of convergence (James §7.7)|M20 §7]] · [[MATH1054 M20 Solutions - Further Calculus II]]
- Concepts: [[Arithmetic and Geometric Series]] · [[Taylor and Maclaurin Series]] · [[Improper Integrals]] · [[Partial Fractions]] · [[Fourier's Theorem]] (convergence of Fourier series, MATH2048)
- Sources: James, Modern Engineering Mathematics (6th ed.) §7.6–7.7; MATH1054 Module Booklet, Module 20.

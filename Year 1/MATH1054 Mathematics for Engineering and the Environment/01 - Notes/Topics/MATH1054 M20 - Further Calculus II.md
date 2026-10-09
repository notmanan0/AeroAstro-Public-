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
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M08 - Differentiation II]]"]
next_topics: ["[[MATH1054 M22 - Complex Numbers II]]"]
key_concepts: ["[[Arithmetic and Geometric Series]]", "[[Convergence Tests for Series]]", "[[Taylor and Maclaurin Series]]", "[[L'Hôpital's Rule]]"]
tutorial_sheets: ["[[MATH1054 M20 Solutions - Further Calculus II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 20)", "02 - Sources/Modern Engineering Mathematics.pdf (§7.2–7.8, §9.4)"]
---

# MATH1054 M20 - Further Calculus II

> [!abstract] Summary
> **Sequences** are lists of numbers; **series** are their running sums. This module covers:
> - arithmetic and geometric progressions, with finance applications;
> - limits of sequences;
> - tests for when an infinite series converges, especially d'Alembert's ratio test and the radius of convergence of power series;
> - **Maclaurin's theorem with the Lagrange remainder**, which gives a guaranteed error bound;
> - **L'Hôpital's rule** for $\frac00$ limits.

## Key Concepts
- [[Arithmetic and Geometric Series]] · [[Convergence Tests for Series]] · [[Taylor and Maclaurin Series]] · [[L'Hôpital's Rule]]

---

## 1. Progressions (James §7.2–7.3)
| | $n$th term | Sum of $n$ terms |
|---|---|---|
| Arithmetic ($a$, $d$) | $a+(n-1)d$ | $\frac n2[2a+(n-1)d]=\frac n2(\text{first}+\text{last})$ |
| Geometric ($a$, $r$) | $ar^{n-1}$ | $\dfrac{a(1-r^n)}{1-r}$ |

**Recurrences** such as $a_{n+1}=1.085a_n+1000$ model savings, loans and iterative algorithms.

## 2. Limits of sequences (James §7.5)
For rational expressions in $n$, divide by the highest power of $n$. For example, $\frac{2n^2+\cdots}{5n^2+\cdots}\to\frac25$.

Standard limits: $\frac1{n^p}\to0$ for $p>0$; $r^n\to0$ for $|r|<1$; and $\frac{x^n}{n!}\to0$ for every $x$.

## 3. Infinite series (James §7.6–7.7)
$\sum a_k$ converges if the partial sums $S_n$ tend to a finite limit.

| Test | Statement |
|---|---|
| $n$th term (divergence) | if $a_k\not\to0$, the series diverges. (The converse is false: $\sum\frac1k$ diverges.) |
| Geometric | $\sum ar^k$ converges iff $\lvert r\rvert<1$, to $\frac a{1-r}$ |
| Telescoping | partial fractions make most terms cancel (Ex 7.25(d)) |
| **d'Alembert's ratio test** | $\ell=\lim\left\lvert\frac{a_{k+1}}{a_k}\right\rvert$: converges if $\ell<1$, diverges if $\ell>1$, inconclusive if $\ell=1$ |

**Power series** $\sum c_nx^n$ converge for $|x|<R$, where the radius of convergence is

$$
R=\lim_{n\to\infty}\left|\frac{c_n}{c_{n+1}}\right|
$$

For example, $\sum\frac{x^n}n$ has $R=1$; $\sum n^nx^n$ has $R=0$; $e^x$ has $R=\infty$.

## 4. Maclaurin's theorem with remainder (James §9.4, booklet)

$$
f(x)=\sum_{k=0}^{n}\frac{f^{(k)}(0)}{k!}x^k+R_n(x),\qquad R_n(x)=\frac{f^{(n+1)}(\theta x)}{(n+1)!}x^{n+1}\quad(0<\theta<1)
$$

The Lagrange remainder turns "approximately" into a **guaranteed error bound**: bound $|f^{(n+1)}|$ on the interval.
- $\cos x\approx1-\frac{x^2}2$ has error less than $\frac{x^4}{24}$, which is $4.06\times10^{-4}$ at $x=\frac\pi{10}$.
- $\sqrt{1.02}\approx1.01$ has error less than $5\times10^{-5}$.

![[m1054_maclaurin_cos.png|600]]

## 5. L'Hôpital's rule (James §9.4.x)
If $\frac{f}{g}\to\frac00$ (or $\frac\infty\infty$), then $\displaystyle\lim\frac fg=\lim\frac{f'}{g'}$, provided the latter exists.
- Repeat it while the form stays indeterminate. For example, $\frac{\sin x-x}{x^3}\to-\frac16$ needs three applications.
- **Stop** once the form is determinate; otherwise you get wrong answers.
- Series give a check: $\sin x-x=-\frac{x^3}6+\cdots$ ✔.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M20 Solutions - Further Calculus II]]
- Prev: [[MATH1054 M08 - Differentiation II]] (Maclaurin series) · Next: [[MATH1054 M22 - Complex Numbers II]]
- Later: [[Fourier Series]] and [[Fourier's Theorem]] (MATH2048, series of functions); [[Truncation Error and Order of Accuracy]] (SESA2029, Taylor remainders)

## Sources
- MATH1054 Module Booklet, Module 20; James §7.2–7.8, §9.4

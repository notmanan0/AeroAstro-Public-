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

## Definition

> [!note] Definition
> $\sum a_k$ **converges** if its partial sums tend to a finite limit.
>
> **d'Alembert's ratio test**: let $\ell=\lim\left|\frac{a_{k+1}}{a_k}\right|$. The series converges if $\ell<1$, diverges if $\ell>1$, and the test is inconclusive if $\ell=1$.

## Explanation
- **$n$th-term test**: if $a_k\not\to0$, the series diverges. (The converse fails: $\sum\frac1k$ diverges.)
- **Telescoping** via partial fractions: $\sum\frac1{(k+1)(k+2)}=1$.
- **Power series** $\sum c_nx^n$ converge for $|x|<R$, where $R=\lim|c_n/c_{n+1}|$.

## Examples
- $\sum\frac{2^k}{k!}$ converges ($\ell=0$); $\sum\frac{2^k}{(k+1)^2}$ diverges ($\ell=2$) (Ex 7.27).
- $\sum\frac{x^n}n$ has $R=1$; $\sum n^nx^n$ has $R=0$ (Ex 7.29).

## Related
- Topics: [[MATH1054 M20 - Further Calculus II]]
- Concepts: [[Arithmetic and Geometric Series]] · [[Taylor and Maclaurin Series]] · [[Improper Integrals]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §7.6–7.7
- MATH1054 Module Booklet, Module 20

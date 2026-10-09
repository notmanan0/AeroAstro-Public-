---
title: "Arithmetic and Geometric Series"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Arithmetic progression", "Geometric progression", "AP", "GP", "Sum to infinity"]
tags: [math1054, concept, series]
status: complete
parent_lectures: ["[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Convergence Tests for Series]]", "[[Taylor and Maclaurin Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §7.2–7.3", "MATH1054 Module Booklet, Module 20"]
---

# Arithmetic and Geometric Series

## Definition

> [!note] Definition
> - **Arithmetic**: $a_n=a+(n-1)d$ and $S_n=\frac n2[2a+(n-1)d]$.
> - **Geometric**: $a_n=ar^{n-1}$, $S_n=\dfrac{a(1-r^n)}{1-r}$, and $S_\infty=\dfrac a{1-r}$ for $|r|<1$.

## Explanation
- **Finance**: compound interest uses geometric sums; regular deposits give a recurrence $a_{n+1}=(1+i)a_n+P$.
- **Recurrence relations** define sequences step by step.
- **"How many terms?"** gives a quadratic in $n$ for an AP, or a log equation for a GP.

## Examples
- $11+15+19+\cdots=341$ gives $n=11$ (Ex 7.7).
- The insurance sum $250\times1.03\times\frac{1.03^{25}-1}{0.03}=£9388.26$ (Ex 7.9).
- $2+\frac23+\frac29+\cdots=3$ (Ex 41(a)).

## Related
- Topics: [[MATH1054 M20 - Further Calculus II]]
- Concepts: [[Convergence Tests for Series]] · [[Taylor and Maclaurin Series]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §7.2–7.3
- MATH1054 Module Booklet, Module 20

---
title: "Random Variables, PDF and CDF"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Probability density function", "Distribution function", "PDF", "CDF", "Probability mass function"]
tags: [math1054, concept, random-variables]
status: complete
parent_lectures: ["[[MATH1054 M24 - Statistics I]]"]
related_concepts: ["[[Mean, Median and Variance of a Distribution]]", "[[Probability Rules and Conditional Probability]]", "[[Normal Distribution and Standardisation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.4", "MATH1054 Module Booklet, Module 24"]
---

# Random Variables, PDF and CDF

## Definition

> [!note] Definition
> - **Discrete**: $p_X(x)=P(X=x)$, with $\sum p_X=1$.
> - **Continuous**: a density $f_X\ge0$, with $\int f_X=1$ and $P(a<X\le b)=\int_a^bf_X$.
> - **Both**: $F_X(x)=P(X\le x)$.

## Explanation
- $F_X$ is non-decreasing, rising from 0 to 1. It is a step function for discrete $X$, and continuous with $F'=f$ for continuous $X$.
- For continuous $X$, $P(X=a)=0$.
- **Exponential**: $f=\lambda e^{-\lambda x}$ and $F=1-e^{-\lambda x}$. It models lifetimes and waiting times.

## Examples
- Ships: $F=(0.1,0.4,0.75,0.95,1)$ (Ex 13.12).
- $f=\frac14x^{-1/2}$ on $(0,4)$ gives $F=\frac12\sqrt x$ and $P(X>1)=\frac12$ (Ex 28).
- Lifetime: $P(X>6)=e^{-3}=0.0498$ (Ex 13.14).

## Related
- Topics: [[MATH1054 M24 - Statistics I]]
- Concepts: [[Mean, Median and Variance of a Distribution]] · [[Probability Rules and Conditional Probability]] · [[Normal Distribution and Standardisation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §13.4
- MATH1054 Module Booklet, Module 24

---
title: "Binomial Distribution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Binomial", "Bernoulli trials"]
tags: [math1054, concept, statistics]
status: complete
parent_lectures: ["[[MATH1054 M25 - Statistics II]]"]
related_concepts: ["[[Probability Rules and Conditional Probability]]", "[[Normal Distribution and Standardisation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.5.1", "MATH1054 Module Booklet, Module 25"]
---

# Binomial Distribution

## Definition

> [!note] Definition
> The number of successes $X$ in $n$ independent trials, each with probability $p$, has
> $$P(X=r)=\binom nr p^r(1-p)^{n-r},\qquad E[X]=np,\qquad\operatorname{Var}X=np(1-p)$$

## Explanation
- "At least $k$": sum from $k$ to $n$, or use $1-P(X\le k-1)$.
- The Poisson distribution is **not** part of MATH1054, so use the exact binomial.

## Examples
- Fire engines: $P(\text{at least }3\text{ of }5)=0.998$ (Ex 50).
- Drills: $P(X\le2)=0.677$ (Ex 51).
- Stock claim: $P(X\ge3)=0.0755$ (Ex 13.25).

## Related
- Topics: [[MATH1054 M25 - Statistics II]]
- Concepts: [[Probability Rules and Conditional Probability]] · [[Normal Distribution and Standardisation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §13.5.1
- MATH1054 Module Booklet, Module 25

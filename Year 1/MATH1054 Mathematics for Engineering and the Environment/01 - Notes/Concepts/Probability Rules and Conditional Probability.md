---
title: "Probability Rules and Conditional Probability"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Conditional probability", "Independence", "Total probability", "Addition rule", "Combinations"]
tags: [math1054, concept, probability]
status: complete
parent_lectures: ["[[MATH1054 M24 - Statistics I]]"]
related_concepts: ["[[Random Variables, PDF and CDF]]", "[[Binomial Distribution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.2–13.3", "MATH1054 Module Booklet, Module 24"]
---

# Probability Rules and Conditional Probability

## Definition

> [!note] Definition
>
> $$P(A\cup B)=P(A)+P(B)-P(A\cap B),\qquad P(B\mid A)=\frac{P(A\cap B)}{P(A)},\qquad P(B)=\sum_iP(B\mid A_i)P(A_i)$$
>
> $A$ and $B$ are independent iff $P(A\cap B)=P(A)P(B)$.

## Explanation
- **"At least one"** $=1-P(\text{none})$.
- **Total probability** splits a problem over a partition (e.g. seen / not seen the advert).
- **Combinations**: $\binom nr=\frac{n!}{r!(n-r)!}$.

## Examples
- $P(B\mid\bar A)=\frac{0.25}{0.7}=\frac5{14}$ (Ex 18).
- The three code-breakers succeed with probability $1-\frac25=0.6$ (Ex 19).
- $P(\text{buy})=0.149$ (Ex 22).
- $\binom64=15$ (Booklet Ex A).

## Related
- Topics: [[MATH1054 M24 - Statistics I]]
- Concepts: [[Random Variables, PDF and CDF]] · [[Binomial Distribution]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §13.2–13.3
- MATH1054 Module Booklet, Module 24

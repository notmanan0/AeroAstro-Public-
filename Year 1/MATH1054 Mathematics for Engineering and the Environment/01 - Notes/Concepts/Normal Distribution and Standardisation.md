---
title: "Normal Distribution and Standardisation"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Normal distribution", "Gaussian", "Z-score", "Standard normal", "Central limit theorem"]
tags: [math1054, concept, statistics]
status: complete
parent_lectures: ["[[MATH1054 M25 - Statistics II]]"]
related_concepts: ["[[Confidence Intervals and Hypothesis Tests for the Mean]]", "[[Binomial Distribution]]", "[[Mean, Median and Variance of a Distribution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.5.3", "MATH1054 Module Booklet, Module 25"]
---

# Normal Distribution and Standardisation

## Definition

> [!note] Definition
> $X\sim N(\mu,\sigma^2)$, where the second parameter is the **variance**. Standardise with $Z=\frac{X-\mu}\sigma\sim N(0,1)$:
> $$P(X\le x)=\Phi\Big(\frac{x-\mu}{\sigma}\Big),\qquad\Phi(-z)=1-\Phi(z)$$

## Explanation
- **Coverage**: $\pm1\sigma$ covers 68.3%, $\pm1.96\sigma$ covers 95%, and $\pm2.58\sigma$ covers 99%.
- **Inverse problems**: read $z$ from the table, then use $x=\mu+z\sigma$.
- **Sample means**: $\bar X\sim N(\mu,\sigma^2/n)$. For large $n$ this holds for **any** parent distribution (the central limit theorem).

## Examples
- $N(4,4)$: $P(X\le6.7)=\Phi(1.35)=0.9115$ (Ex 13.28).
- To have only 3% of bags underweight, the mean fill must be $6.094$ kg (Ex 59).
- Components: $P(X>400)=0.977$, so the batch meets the specification (Booklet Ex B).

## Related
- Topics: [[MATH1054 M25 - Statistics II]]
- Concepts: [[Confidence Intervals and Hypothesis Tests for the Mean]] · [[Binomial Distribution]] · [[Mean, Median and Variance of a Distribution]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §13.5.3
- MATH1054 Module Booklet, Module 25

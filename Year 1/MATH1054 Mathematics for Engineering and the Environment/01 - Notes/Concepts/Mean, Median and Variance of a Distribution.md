---
title: "Mean, Median and Variance of a Distribution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Expected value", "Mean", "Variance", "Standard deviation", "Median", "Mode", "Interquartile range", "Sample variance"]
tags: [math1054, concept, random-variables]
status: complete
parent_lectures: ["[[MATH1054 M24 - Statistics I]]", "[[MATH1054 M25 - Statistics II]]"]
related_concepts: ["[[Random Variables, PDF and CDF]]", "[[Normal Distribution and Standardisation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.4, §13.4.x", "MATH1054 Module Booklet, Modules 24–25"]
---

# Mean, Median and Variance of a Distribution

## Definition

> [!note] Definition
> $$\mu=E[X]=\sum xp_X\ \text{or}\ \int xf_X\,\mathrm dx,\qquad\sigma^2=E[X^2]-\mu^2$$
> - **Median**: $F(m)=\frac12$.
> - **Mode**: the most likely value.
> - **IQR**: $Q_3-Q_1$, where $F(Q_1)=\frac14$ and $F(Q_3)=\frac34$.

## Explanation
- The **sample** versions are $\bar x=\frac1n\sum x_i$ and $s^2=\frac1{n-1}\sum(x_i-\bar x)^2$. The booklet insists on the $n-1$ divisor.
- **Skew**: for right-skewed data (e.g. exponential), mode < median < mean.
- **Exponential with mean $\mu$**: $\sigma=\mu$, median $\mu\ln2$, IQR $\mu\ln3$.

## Examples
- Ships: $\mu=1.8$ and $\sigma=1.03$ (Ex 13.16–13.17).
- Malfunctions: mean 1.8, median 2, $\sigma=1.342$ (Ex 33).
- Impurities: $\bar x=2.283$ and $s=0.625$ (Ex 42).

## Related
- Topics: [[MATH1054 M24 - Statistics I]] · [[MATH1054 M25 - Statistics II]]
- Concepts: [[Random Variables, PDF and CDF]] · [[Normal Distribution and Standardisation]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §13.4, §13.4.x
- MATH1054 Module Booklet, Modules 24–25

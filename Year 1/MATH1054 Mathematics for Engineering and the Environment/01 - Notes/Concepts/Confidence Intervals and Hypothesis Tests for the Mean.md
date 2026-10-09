---
title: "Confidence Intervals and Hypothesis Tests for the Mean"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Confidence interval", "Hypothesis test", "Significance level", "One-tailed test", "Two-tailed test", "Standard error"]
tags: [math1054, concept, statistics]
status: complete
parent_lectures: ["[[MATH1054 M25 - Statistics II]]"]
related_concepts: ["[[Normal Distribution and Standardisation]]", "[[Accuracy and Precision]]"]
sources: ["MATH1054 Module Booklet, Module 25 (booklet §8–10)", "James, Modern Engineering Mathematics (6th ed.) §13.6"]
---

# Confidence Intervals and Hypothesis Tests for the Mean

## Definition

> [!note] Definition
> $$\text{CI: }\bar x\pm z_{\alpha/2}\frac{\sigma}{\sqrt n};\qquad\text{test statistic: }Z=\frac{\bar x-\mu_0}{\sigma/\sqrt n}$$
> Replace $\sigma$ by $s$ when $n\ge30$.

## Explanation
- $z$ values: 90% uses $1.645$; 95% uses $1.96$; 99% uses $2.58$.
- **Test procedure**:
  1. State $H_0:\mu=\mu_0$.
  2. Choose $H_1$: one-tailed ($>$ or $<$, as in "improvement") or two-tailed ($\neq$, as in "different").
  3. Compare $Z$ with the critical value: $1.645$ for 5% one-tailed, $1.96$ for 5% two-tailed.
- **Type I error**: rejecting a true $H_0$, with probability equal to the significance level. **Type II error**: accepting a false $H_0$.

## Examples
- Carton fill: the 95% CI is $(567.9,572.1)$ ml (Booklet Ex C).
- Wire strength: $Z=2.07>1.645$, so the new process is better (Booklet Ex E).
- Phosphorus: $Z=3.0>1.96$, a significant difference (Booklet Ex F).

## Related
- Topics: [[MATH1054 M25 - Statistics II]]
- Concepts: [[Normal Distribution and Standardisation]] · [[Accuracy and Precision]]

## Sources
- MATH1054 Module Booklet, Module 25 (booklet §8–10)
- James, Modern Engineering Mathematics (6th ed.) §13.6

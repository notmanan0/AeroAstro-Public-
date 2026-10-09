---
title: "MATH1054 M25 - Statistics II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 5: Series and Statistics"
order: 25
tags:
  - math1054
  - statistics
  - normal-distribution
  - hypothesis-testing
aliases: ["MATH1054 Module 25", "Statistics II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M24 - Statistics I]]"]
next_topics: []
key_concepts: ["[[Binomial Distribution]]", "[[Normal Distribution and Standardisation]]", "[[Confidence Intervals and Hypothesis Tests for the Mean]]"]
tutorial_sheets: ["[[MATH1054 M25 Solutions - Statistics II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 25)", "02 - Sources/Modern Engineering Mathematics.pdf (§13.4–13.5)"]
---

# MATH1054 M25 - Statistics II

> [!abstract] Summary
> This module moves from single random variables to inference:
> - **joint distributions**, which for independent variables are just products;
> - **sample statistics**, $\bar x$ and $s$ (with the $n-1$ divisor);
> - the **binomial** distribution, for counts of successes;
> - the **normal** distribution, via standardisation $Z=(X-\mu)/\sigma$;
> - the **sampling distribution of $\bar X$**: the central limit theorem, confidence intervals, and one- and two-tailed hypothesis tests for a mean.

## Key Concepts
- [[Binomial Distribution]] · [[Normal Distribution and Standardisation]] · [[Confidence Intervals and Hypothesis Tests for the Mean]]

---

## 1. Joint distributions and sample statistics (James §13.4.x)
- For independent $X,Y$: $P(X=u,Y=v)=P(X=u)P(Y=v)$. To find $P(X+Y\le k)$, sum the relevant cells.
- **Sample mean**: $\bar x=\frac1n\sum x_i$.
- **Sample variance**, using the $n-1$ divisor as the booklet requires:
$$
s^2=\frac{1}{n-1}\sum(x_i-\bar x)^2=\frac{\sum x_i^2-n\bar x^2}{n-1}
$$

## 2. The binomial distribution (James §13.5.1)
$n$ independent trials, each succeeding with probability $p$:
$$
P(X=r)=\binom nr p^r(1-p)^{n-r},\qquad E[X]=np,\qquad\operatorname{Var}X=np(1-p)
$$
"At least $k$" means summing from $k$ to $n$, or using the complement.

## 3. The normal distribution (James §13.5.3)
$X\sim N(\mu,\sigma^2)$, where the second parameter is the **variance**. Standardise and use the table of $\Phi(z)=P(Z\le z)$:
$$
P(X\le x)=\Phi\Big(\frac{x-\mu}{\sigma}\Big),\qquad\Phi(-z)=1-\Phi(z)
$$
**Inverse problems** (Ex 59, 13.28(b)): read $z$ from the table, then solve $x=\mu+z\sigma$.

| Coverage | $\pm z$ |
|---|---|
| 68.3% | 1 |
| 90% | 1.645 |
| 95% | 1.96 |
| 99% | 2.58 |

![[m1054_normal_tests.png|800]]

## 4. The sampling distribution of $\bar X$ (booklet)
$$
E[\bar X]=\mu,\qquad\text{SE}=\sigma_{\bar X}=\frac{\sigma}{\sqrt n},\qquad Z=\frac{\bar X-\mu}{\sigma/\sqrt n}\sim N(0,1)
$$
This is exact if the parent distribution is normal. For $n\ge30$ it holds approximately for *any* parent: the **central limit theorem**. For $n\ge30$ with $\sigma$ unknown, use $s$. (Small samples need the $t$-distribution, which is not in this module.)

## 5. Confidence intervals
$$
\bar x\pm z_{\alpha/2}\frac{\sigma}{\sqrt n}\qquad(95\%:\ z=1.96;\ 99\%:\ z=2.58;\ 90\%:\ z=1.645)
$$
Interpretation: 95% of intervals built this way contain the true $\mu$.

## 6. Hypothesis tests for a mean
1. State $H_0:\mu=\mu_0$, and $H_1$:
   - $\mu>\mu_0$ or $\mu<\mu_0$ is **one-tailed** ("improvement", "greater than");
   - $\mu\neq\mu_0$ is **two-tailed** ("different").
2. Compute the test statistic $Z=\dfrac{\bar x-\mu_0}{\sigma/\sqrt n}$.
3. Compare with the critical value at the significance level:
   - 5% one-tailed: $1.645$;
   - 5% two-tailed: $\pm1.96$;
   - 1% two-tailed: $\pm2.58$.
4. If $Z$ falls in the rejection region, **reject $H_0$**. Otherwise there is insufficient evidence.

**Errors**: a type I error rejects a true $H_0$, and has probability equal to the significance level. A type II error accepts a false $H_0$.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M25 Solutions - Statistics II]]
- Prev: [[MATH1054 M24 - Statistics I]]
- Related: [[Accuracy and Precision]], [[Verification and Validation]]

## Sources
- MATH1054 Module Booklet, Module 25; James §13.4–13.5

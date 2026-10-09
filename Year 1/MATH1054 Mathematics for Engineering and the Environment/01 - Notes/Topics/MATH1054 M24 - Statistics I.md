---
title: "MATH1054 M24 - Statistics I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 5: Series and Statistics"
order: 24
tags:
  - math1054
  - probability
  - random-variables
aliases: ["MATH1054 Module 24", "Statistics I", "Probability"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M09 - Integration II]]", "[[MATH1054 M10 - Integration III]]"]
next_topics: ["[[MATH1054 M25 - Statistics II]]"]
key_concepts: ["[[Probability Rules and Conditional Probability]]", "[[Random Variables, PDF and CDF]]", "[[Mean, Median and Variance of a Distribution]]"]
tutorial_sheets: ["[[MATH1054 M24 Solutions - Statistics I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 24)", "02 - Sources/Modern Engineering Mathematics.pdf (§13.2–13.4)"]
---

# MATH1054 M24 - Statistics I

> [!abstract] Summary
> This module covers:
> - **probability**: sample spaces, events, and the addition, multiplication and total-probability rules;
> - **counting**: combinations;
> - **random variables**: discrete ones are described by a probability function $p_X$, continuous ones by a density $f_X$, and both by the distribution function $F_X$;
> - **summaries** of a distribution: centre (mean, median, mode) and spread (variance, standard deviation, interquartile range).
>
> Continuous probability is just integration: areas under $f_X$.

## Key Concepts
- [[Probability Rules and Conditional Probability]] · [[Random Variables, PDF and CDF]] · [[Mean, Median and Variance of a Distribution]]

---

## 1. Probability rules (James §13.2–13.3)
| Rule | Formula |
|---|---|
| Complement | $P(\bar A)=1-P(A)$ |
| Addition | $P(A\cup B)=P(A)+P(B)-P(A\cap B)$ |
| Conditional | $P(B\mid A)=\dfrac{P(A\cap B)}{P(A)}$ |
| Multiplication | $P(A\cap B)=P(A)P(B\mid A)$ |
| Independence | $P(A\cap B)=P(A)P(B)$ |
| Total probability | $P(B)=P(B\mid A)P(A)+P(B\mid\bar A)P(\bar A)$ |

**"At least one"** is best found as $1-P(\text{none})$. For three independent code-breakers, $1-\frac45\cdot\frac34\cdot\frac23=0.6$.

**Combinations**: the number of ways to choose $r$ from $n$ is $\binom nr=\dfrac{n!}{r!(n-r)!}$. For example, $\binom64=15$.

## 2. Random variables (James §13.4)
| | Discrete | Continuous |
|---|---|---|
| Describes | $p_X(x)=P(X=x)$ | density $f_X(x)\ge0$ |
| Normalisation | $\sum p_X=1$ | $\int f_X\,\mathrm dx=1$ |
| $F_X(x)=P(X\le x)$ | step function | $\int_{-\infty}^xf_X$, continuous |
| $P(a<X\le b)$ | $\sum_{a<x\le b}p_X$ | $F(b)-F(a)=\int_a^bf_X$ |

For a continuous variable, $P(X=a)=0$, and $f_X=F_X'$.

![[m1054_ships_pmf_cdf.png|760]]

## 3. Centre and spread

$$
\mu=E[X]=\sum xp_X\ \text{or}\ \int xf_X\,\mathrm dx,\qquad\sigma^2=\operatorname{Var}X=E[X^2]-\mu^2
$$

- **Median** $m$: $F(m)=\frac12$. For a discrete variable, it is the first $x$ with $F\ge\frac12$.
- **Mode**: the most probable value, i.e. the peak of $p_X$ or $f_X$.
- **Quartiles**: $F(Q_1)=\frac14$ and $F(Q_3)=\frac34$. $\text{IQR}=Q_3-Q_1$.

### The exponential distribution (a key example)

$$
f_X(x)=\lambda e^{-\lambda x}\ (x\ge0),\quad F_X(x)=1-e^{-\lambda x},\quad\mu=\sigma=\frac1\lambda,\quad\text{median}=\frac{\ln2}{\lambda},\quad\text{IQR}=\frac{\ln3}{\lambda}
$$

It is right-skewed: mode (0) < median < mean. It models lifetimes and waiting times.

![[m1054_lifetime_pdf_cdf.png|760]]

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M24 Solutions - Statistics I]]
- Next: [[MATH1054 M25 - Statistics II]] (joint distributions, binomial, normal, confidence intervals, hypothesis tests)
- Related: [[Accuracy and Precision]] (measurement uncertainty)

## Sources
- MATH1054 Module Booklet, Module 24; James §13.2–13.4

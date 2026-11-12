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

A random variable $X$ is a set of possible numerical values with a probability over them. A discrete one is described by its probability function $p_X(x)=P(X=x)$, a continuous one by a density $f_X(x)$, and both by the distribution function $F_X(x)=P(X\le x)$.

For a discrete variable, $p_X\ge0$ and $\sum p_X=1$, and $F_X$ is the running sum of $p_X$ from the left. It is a step function: flat between the possible values, with a jump of $p_X(x)$ at each one, and the value at a jump includes the jump. The ships arriving at a container terminal (James Example 13.12) have $p_X=(0.10,0.30,0.35,0.20,0.05)$ for $x=0,\dots,4$, so $F_X=(0.1,0.4,0.75,0.95,1)$.

For a continuous variable, probability is spread along the axis with a density. $F_X$ is continuous, and its derivative is the density:

$$
f_X(x)=F_X'(x),\qquad F_X(x)=\int_{-\infty}^xf_X(z)\,\mathrm dz,\qquad f_X\ge0,\qquad\int_{-\infty}^{\infty}f_X(x)\,\mathrm dx=1 .
$$

In either case $\{X\le b\}$ is the exclusive union of $\{X\le a\}$ and $\{a<X\le b\}$, so the probability of an interval is a difference of $F_X$ values, which for a continuous variable is an area:

$$
P(a<X\le b)=F_X(b)-F_X(a)=\int_a^bf_X(x)\,\mathrm dx .
$$

$F_X$ never decreases and rises from 0 at $-\infty$ to 1 at $+\infty$. Shrinking the interval to a point shows that a continuous variable takes any single value with probability zero, $P(X=a)=0$, so $<$ and $\le$ give the same probabilities.

James Exercise 28 shows the method. A density $f_X=c/\sqrt x$ on $(0,4)$ must have total area 1, so $c\big[2\sqrt x\big]_0^4=4c=1$ and $c=\frac14$. Integrating from 0 gives $F_X(x)=\frac12\sqrt x$ for $0<x<4$ (0 below, 1 above), and $P(X>1)=1-F_X(1)=\frac12$. The density is infinite at $x=0$, yet the area is finite: an improper integral that converges.

The **exponential distribution**, $f_X=\lambda e^{-\lambda x}$ and $F_X=1-e^{-\lambda x}$ for $x\ge0$, models lifetimes and waiting times. For component lifetimes in thousands of hours with $\lambda=\frac12$ (James Examples 13.13 and 13.14),

$$
P(X>6)=1-F_X(6)=e^{-3}=0.0498,
$$

so about one component in twenty lasts longer than 6000 hours.

The common trap is treating $f_X(x)$ as a probability. It is probability per unit length: $P(x<X\le x+\delta x)\approx f_X(x)\,\delta x$. A density can exceed 1, and in Exercise 28 it is unbounded, while every probability, and $F_X$ itself, stays between 0 and 1. A second trap is forgetting the pieces of $F_X$ outside the range of $X$: it is 0 to the left and 1 to the right.

## Related

- Topics: [[MATH1054 M24 - Statistics I]] (§7 discrete, §8 continuous, §11 the exponential family) · [[MATH1054 M25 - Statistics II]]
- Solutions: [[MATH1054 M24 Solutions - Statistics I]]
- Concepts: [[Mean, Median and Variance of a Distribution]] · [[Probability Rules and Conditional Probability]] · [[Normal Distribution and Standardisation]] · [[Binomial Distribution]] · [[Improper Integrals]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §13.4.1–13.4.4; MATH1054 Module Booklet, Module 24

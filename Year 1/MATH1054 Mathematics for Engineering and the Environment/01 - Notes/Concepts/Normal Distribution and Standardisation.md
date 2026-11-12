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

A random variable $X\sim N(\mu,\sigma^2)$ has the bell-shaped **normal** (Gaussian) density $f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac12\left(\frac{x-\mu}{\sigma}\right)^2}$ with mean $\mu$ and variance $\sigma^2$. **Standardisation** $Z=(X-\mu)/\sigma$ turns it into the standard normal $N(0,1)$, so that every normal probability comes from one table of $\Phi(z)=P(Z\le z)$.

The reason is a substitution in the distribution function. Put $u=(t-\mu)/\sigma$, so $dt=\sigma\,du$ and the upper limit $x$ becomes $(x-\mu)/\sigma$:

$$
\begin{aligned}
P(X\le x)&=\int_{-\infty}^{x}\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac12\left(\frac{t-\mu}{\sigma}\right)^2}dt\\
&=\int_{-\infty}^{(x-\mu)/\sigma}\frac{1}{\sqrt{2\pi}}e^{-u^2/2}\,du\\
&=\Phi\Big(\frac{x-\mu}{\sigma}\Big).
\end{aligned}
$$

The table lists $\Phi$ only for $z\ge0$. Symmetry of the curve about 0 gives the rest, $\Phi(-z)=1-\Phi(z)$, and the probability of lying within $z$ standard deviations of the mean is $\Phi(z)-\Phi(-z)=2\Phi(z)-1$. That gives the coverage values used throughout statistics: $\pm1\sigma$ holds 68.3%, $\pm1.645\sigma$ holds 90%, $\pm1.96\sigma$ holds 95% and $\pm2.58\sigma$ holds 99%. An inverse problem runs the table backwards: read $z$ for the required probability, then $x=\mu+z\sigma$.

The normal curve matters beyond data that happen to look bell-shaped. The mean $\bar X$ of $n$ independent observations has mean $\mu$ and standard deviation $\sigma/\sqrt n$, and it is exactly normal when the parent is normal. By the **central limit theorem** it is approximately normal for any parent once $n$ is large ($n\ge30$ in practice), which is what makes confidence intervals and tests for a mean work.

For example, if $X\sim N(4,4)$ then $\sigma=2$ and

$$
P(X\le6.7)=\Phi\Big(\frac{6.7-4}{2}\Big)=\Phi(1.35)=0.9115,
$$

while the $c$ with $P(X>c)=0.1$ needs $\Phi\big(\frac{c-4}2\big)=0.9$, so $\frac{c-4}2=1.2816$ and $c=6.563$. Other module results: a filling machine with $\sigma=0.05$ kg must fill to a mean of $6+1.881(0.05)=6.094$ kg for only 3% of "6 kg" bags to be underweight, and components with lifetimes $N(500,50^2)$ last over 400 hours with probability $\Phi(2)=0.977\ge0.95$, so that batch meets a 95% specification.

The trap is in the notation. The second parameter of $N(\mu,\sigma^2)$ is the variance, so $N(4,4)$ has $\sigma=2$, not 4, and a question giving "standard deviation 25" means $N(600,25^2)$. The second trap is the tail: $P(X>x)=1-\Phi(z)$, and a negative $z$ needs the symmetry rule before the table can be used.

## Related

- Topics: [[MATH1054 M25 - Statistics II#5. The normal distribution and standardisation (James §13.5.3)|MATH1054 M25 - Statistics II]] (§5 derives the mean, variance, symmetry and standardisation; §6 covers the central limit theorem)
- Concepts: [[Confidence Intervals and Hypothesis Tests for the Mean]] · [[Binomial Distribution]] · [[Mean, Median and Variance of a Distribution]] · [[Random Variables, PDF and CDF]]
- Later use: [[Accuracy and Precision]] (Gaussian sensor noise, about 95% within $\pm2\sigma$)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §13.5.3–13.5.4 (Figure 13.30, Examples 13.28–13.29, Exercise 59); MATH1054 Module Booklet, Module 25 (items 5–7, Exercises A–B).

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

The mean, median and mode measure where a distribution is centred, and the variance, standard deviation and interquartile range measure how widely it is spread. The mean is the probability-weighted average value, the median splits the probability in half, and the variance is the mean squared distance from the mean.

The **mean** is the long-run average of repeated observations: if the value $x$ turns up a fraction $p_X(x)$ of the time, the average tends to $\sum x\,p_X(x)$. For a continuous variable the sum becomes an integral:

$$
\mu=E[X]=\sum x\,p_X(x)\quad\text{or}\quad\int_{-\infty}^{\infty}x\,f_X(x)\,\mathrm dx .
$$

It is the centre of gravity of the distribution. The **median** $m$ solves $F_X(m)=\frac12$; for a discrete variable it is the first value at which $F_X$ reaches $\frac12$. The **mode** is the most likely value, the peak of $p_X$ or $f_X$. The **quartiles** solve $F_X(Q_1)=\frac14$ and $F_X(Q_3)=\frac34$, and the **interquartile range** (IQR) is $Q_3-Q_1$.

The **variance** is $\sigma^2=E[(X-\mu)^2]$, the moment of inertia about the centre of gravity, and the **standard deviation** $\sigma$ is its square root, in the units of $X$. Expanding the square and using $\int f_X=1$ and $\int xf_X=\mu$ gives the form used in calculations:

$$
\begin{aligned}
\sigma^2&=\int(x^2-2\mu x+\mu^2)f_X\,\mathrm dx\\
&=E[X^2]-2\mu^2+\mu^2\\
&=E[X^2]-\mu^2 .
\end{aligned}
$$

For the ship arrivals of James Example 13.12, $\mu=1.8$ and $E[X^2]=4.30$, so $\sigma^2=4.30-3.24=1.06$ and $\sigma=1.03$ (Examples 13.16–13.17). For the daily computer malfunctions of Exercise 33, the mean is 1.8, the median 2 (since $F(1)=0.46<0.5\le F(2)=0.73$), and $\sigma^2=5.04-3.24=1.80$, so $\sigma=1.342$.

An **exponential** variable with mean $\mu$ has $\sigma=\mu$, median $\mu\ln2$, quartiles $\mu\ln\frac43$ and $\mu\ln4$, and IQR $\mu\ln3$, all from solving $1-e^{-x/\mu}=p$. Its mode is 0, so mode < median < mean. That order is typical of right-skewed data, where a long tail of large values pulls the mean above the median.

Data have **sample** versions. For $n$ observations, $\bar x=\frac1n\sum x_i$, and the sample variance uses the divisor $n-1$:

$$
s^2=\frac1{n-1}\sum_{i=1}^n(x_i-\bar x)^2=\frac{1}{n-1}\Big(\sum x_i^2-n\bar x^2\Big).
$$

The deviations $x_i-\bar x$ always sum to zero, so only $n-1$ of them are free, and $s^2$ averages over those $n-1$. The divisor $n$ is not used in this course. For the reactor impurities of Exercise 42 ($n=12$, $\sum x=27.4$, $\sum x^2=66.86$), $\bar x=2.283$ and $s^2=(66.86-12\times2.2833^2)/11=0.3906$, so $s=0.625$.

The common trap is quoting the mean as the typical value of a skewed variable. For an exponential lifetime, $P(X\le\mu)=1-e^{-1}=0.632$, so nearly two-thirds of the units fail before the mean life. A second trap is finding $\sigma^2$ as $E[X^2]$ alone, or as $E[X^2]-\mu$, forgetting to square the mean.

## Related

- Topics: [[MATH1054 M24 - Statistics I]] (§9–§11: derivations, Examples 13.16–13.17, quartiles, the exponential family) · [[MATH1054 M25 - Statistics II]] (sample statistics, standard error)
- Solutions: [[MATH1054 M24 Solutions - Statistics I]] · [[MATH1054 M25 Solutions - Statistics II]]
- Concepts: [[Random Variables, PDF and CDF]] · [[Normal Distribution and Standardisation]] · [[Confidence Intervals and Hypothesis Tests for the Mean]] · [[Centroids and Solids of Revolution]] (the same first-moment integral)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §13.4.6–13.4.7 and §13.4.10; MATH1054 Module Booklet, Modules 24–25

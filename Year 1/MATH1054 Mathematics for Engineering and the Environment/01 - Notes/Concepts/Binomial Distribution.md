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

The **binomial distribution** $\mathrm{Bin}(n,p)$ gives the number of successes $X$ in $n$ independent trials that each succeed with the same probability $p$:

$$
P(X=r)=\binom nr p^r(1-p)^{n-r},\quad r=0,1,\dots,n,\qquad E(X)=np,\qquad\operatorname{Var}X=np(1-p)=npq .
$$

The formula is two probability rules put together. One particular sequence with $r$ successes and $n-r$ failures has probability $p^r(1-p)^{n-r}$ by the product rule for independent trials, and there are $\binom nr$ such sequences (choose which $r$ trials succeed). The sequences are mutually exclusive, so their probabilities add. The mean and variance follow from writing $X$ as a sum of $n$ independent Bernoulli variables, each 1 with probability $p$ and 0 otherwise. One trial has mean $p$ and variance $E(X_i^2)-p^2=p-p^2=pq$ with $q=1-p$, and means always add while variances add for independent variables, giving $np$ and $npq$. By the binomial theorem the probabilities sum to $(p+q)^n=1$.

The model needs four things: a fixed number of trials, two outcomes per trial, the same $p$ every time, and independence. Questions usually ask for "at least $k$", which is quickest as a complement, $P(X\ge k)=1-P(X\le k-1)$. For large $n$ the distribution approaches a normal curve with the same mean and variance (the central limit theorem), and for large $n$ with small $p$ the Poisson distribution approximates it (James §13.5.2). Neither approximation is used in MATH1054, so binomial questions are done with the exact formula.

For example, five fire engines each available 94% of the time, independently, give $X\sim\mathrm{Bin}(5,0.94)$ engines available, and

$$
\begin{aligned}
P(X\ge3)&=\binom53(0.94)^3(0.06)^2+\binom54(0.94)^4(0.06)+(0.94)^5\\
&=0.0299+0.2342+0.7339\\
&=0.998 .
\end{aligned}
$$

Two more results from the module: for 100 drills with reject probability 0.02, $P(X\le2)=0.1326+0.2707+0.2734=0.677$; for a supplier claiming 95% stock availability, an order of 20 with 3 or more items missing has probability $1-(0.3585+0.3774+0.1887)=0.0755$, unlikely but not significant at 5%.

The common trap is the tail. "At least 3" includes 3, so its complement is "at most 2", not "at most 3". And when judging whether an observed count is surprising, use the probability of a result at least as extreme as the one observed, not of that exact count, because any single value of $r$ can have a small probability.

## Related

- Topics: [[MATH1054 M25 - Statistics II#4. The binomial distribution|MATH1054 M25 - Statistics II]]
- Concepts: [[Probability Rules and Conditional Probability]] · [[Mean, Median and Variance of a Distribution]] · [[Normal Distribution and Standardisation]]
- Worked solutions: [[MATH1054 M25 Solutions - Statistics II#Example 13.25: 3 items out of stock in an order of 20]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §13.5.1 (Example 13.25, Exercises 50–51); MATH1054 Module Booklet, Module 25.

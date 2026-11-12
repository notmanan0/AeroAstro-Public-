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
status: lectured
coverage: "Module Booklet Module 25 work scheme (items 1–10, Examples A–F, Exercises A–F, Specimen Test 25); James §13.4.8–13.4.10, §13.5.1, §13.5.3 (Examples 13.19–13.29, Exercises 42(a), 50, 51, 59)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M24 - Statistics I]]"]
next_topics: []
key_concepts: ["[[Binomial Distribution]]", "[[Normal Distribution and Standardisation]]", "[[Confidence Intervals and Hypothesis Tests for the Mean]]"]
tutorial_sheets: ["[[MATH1054 M25 Solutions - Statistics II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 25)", "02 - Sources/Modern Engineering Mathematics.pdf (§13.4–13.5)"]
---

# MATH1054 M25 - Statistics II

> [!abstract] Summary
> Statistical inference estimates and tests the properties of a population from a sample, using the distributions of sums and averages of random variables. Means add for any random variables and variances add for independent ones, which gives the mean $\mu$ and standard error $\sigma/\sqrt n$ of a sample mean and explains the $n-1$ divisor in the sample variance $s^2$. The binomial distribution $P(X=r)=\binom nr p^r(1-p)^{n-r}$ counts successes in $n$ independent trials, and every normal probability reduces to the single table of $\Phi(z)$ through $Z=(X-\mu)/\sigma$. Because $\bar X$ is (approximately, for $n\ge30$) normal, $\bar x\pm1.96\,\sigma/\sqrt n$ is a 95% confidence interval for $\mu$, and $Z=(\bar x-\mu_0)/(\sigma/\sqrt n)$ tests the hypothesis $\mu=\mu_0$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a count of successes in $n$ trials (binomial), a normally distributed measurement (standardise), or a sample mean with $n$ and $\sigma$ or $s$ (standard error, confidence interval, hypothesis test).
> - **Assumptions:** independent trials or observations; in $N(\mu,\sigma^2)$ the second parameter is the variance; $\bar X$ is normal exactly for a normal parent and approximately for $n\ge30$; for $n\ge30$ replace an unknown $\sigma$ by $s$ (divisor $n-1$).
> - **Method:** 1. Identify the random variable and its distribution, with $\mu$ and $\sigma$ (for $\bar X$, $\sigma/\sqrt n$). 2. Standardise, $z=(\text{value}-\text{mean})/\text{SD}$. 3. Read $\Phi(z)$, using $\Phi(-z)=1-\Phi(z)$ and complements. 4. For an interval, $\bar x\pm z\,\sigma/\sqrt n$ with $z=1.645,\ 1.96,\ 2.58$ for 90, 95, 99%. 5. For a test, state $H_0$ and $H_1$, decide one- or two-tailed from the wording, compare $Z$ with $1.645$ (5%, one tail) or $1.96$ (5%, two tails), and state the conclusion in words.
> - **Common mistakes:** using the variance as the standard deviation ($N(4,4)$ has $\sigma=2$); dividing $\sigma$ by $n$ instead of $\sqrt n$, or using the one-tailed critical value for a "different from" question.
> - **Practise:** [[#Wire strength, one-tailed test (Booklet Exercise E)]] · [[MATH1054 M25 Solutions - Statistics II#Part C: Specimen Test 25|Specimen Test 25]]

A single measurement of a manufactured part, a component lifetime or a pulse rate is a random variable, described by its distribution, mean and variance ([[MATH1054 M24 - Statistics I|Statistics I]]). Engineering data rarely comes one value at a time. A batch is a sample of several measurements, a project time is a sum of stage times, and a quality claim is a statement about the whole population that a sample has to check. All of these need rules for combining random variables, and the two rules that matter are that means always add and that variances add when the variables are independent.

Applied to $n$ success-or-failure trials, the two rules give the mean $np$ and variance $np(1-p)$ of the binomial count. Applied to the average of $n$ measurements they show that $\bar X$ has the same mean as one measurement but a standard deviation smaller by $\sqrt n$, the **standard error**. The central limit theorem adds that this average is close to normal whatever the parent distribution, so normal tables answer questions about averages even when the data themselves are skewed.

Inference then runs the probability statement backwards. If $\bar X$ is within $1.96$ standard errors of $\mu$ with probability 0.95, then $\mu$ is within $1.96$ standard errors of the observed $\bar x$ for 95% of samples, which is a confidence interval. If a claimed $\mu_0$ makes the observed $\bar x$ improbably far out, the claim is rejected, which is a hypothesis test. The same calculations reappear in measurement uncertainty, sensor noise and model validation in later years (see [[#Links]]).

---

## 1. Independent random variables and joint distributions (James §13.4.8)

Two random variables measured on the same object, such as a person's height and weight, generally depend on each other. Two random variables are **independent** when knowing the value of one tells nothing about the other. For discrete variables $X$ (values $u_1,\dots,u_k$) and $Y$ (values $v_1,\dots,v_m$) independence means the joint probability factorises, exactly as for independent events $P(A\cap B)=P(A)P(B)$:

$$
P(X=u_i\cap Y=v_j)=P(X=u_i)\,P(Y=v_j).
$$

The table of all these joint probabilities is the **joint distribution**. Summing a row recovers the distribution of $X$, called the marginal distribution:

$$
\begin{aligned}
\sum_{j=1}^{m}P(X=u_i\cap Y=v_j)&=\sum_{j=1}^{m}P(X=u_i)P(Y=v_j)\\
&=P(X=u_i)\sum_{j=1}^{m}P(Y=v_j)\\
&=P(X=u_i),
\end{aligned}
$$

since the probabilities of $Y$ sum to 1. Summing over one variable gives the distribution of the other for dependent variables too, but only for independent variables can the table be built by multiplying the margins. The probability of any event involving both variables, such as $X+Y\le7$, is the sum of the cells where the event holds.

### Installation and commissioning times (James Example 13.19)

A plant is installed (time $X$ days) and then commissioned (time $Y$ days), and the two stages depend on unrelated random factors, so $X$ and $Y$ are independent with

| $u_i$ | 3 | 4 | 5 | 6 |
|---|---|---|---|---|
| $P(X=u_i)$ | 0.1 | 0.4 | 0.3 | 0.2 |

| $v_j$ | 2 | 3 | 4 |
|---|---|---|---|
| $P(Y=v_j)$ | 0.50 | 0.35 | 0.15 |

Each cell of the joint distribution is the product of its row and column probabilities, so for example $P(X=4\cap Y=3)=0.4\times0.35=0.140$:

| $X\backslash Y$ | 2 | 3 | 4 | $P(X)$ |
|---|---|---|---|---|
| 3 | 0.050 | 0.035 | 0.015 | 0.1 |
| 4 | 0.200 | 0.140 | 0.060 | 0.4 |
| 5 | 0.150 | 0.105 | 0.045 | 0.3 |
| 6 | 0.100 | 0.070 | 0.030 | 0.2 |
| $P(Y)$ | 0.50 | 0.35 | 0.15 | 1 |

The total time is at most seven days in the cells with $u+v\le7$: the whole $X=3$ row, $Y=2$ and $3$ in the $X=4$ row, and $Y=2$ in the $X=5$ row.

$$
\begin{aligned}
P(X+Y\le7)&=(0.050+0.035+0.015)+(0.200+0.140)+0.150\\
&=0.1+0.34+0.15\\
&=0.59 .
\end{aligned}
$$

## 2. Scaling and adding random variables (James §13.4.9)

### The distribution of a sum

A sum of random variables is itself a random variable, and its distribution comes from the joint table by collecting the cells with the same total. In Example 13.19 the total is exactly seven days on the anti-diagonal $(3,4)$, $(4,3)$, $(5,2)$:

$$
P(X+Y=7)=0.015+0.140+0.150=0.305 .
$$

Doing the same for every total from 5 to 10 days gives the distribution of the total time (James Example 13.20):

| $w$ (days) | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|
| $P(X+Y=w)$ | 0.050 | 0.235 | 0.305 | 0.265 | 0.115 | 0.030 |

and its expected value is $E(X+Y)=\sum wP(X+Y=w)=7.25$ days. The separate means are $E(X)=3(0.1)+4(0.4)+5(0.3)+6(0.2)=4.60$ and $E(Y)=2(0.5)+3(0.35)+4(0.15)=2.65$, and $4.60+2.65=7.25$.

### The mean of a sum is the sum of the means

The double sum below runs over every pair $(u_i,v_j)$, so it covers every possible total:

$$
\begin{aligned}
E(X+Y)&=\sum_{i=1}^{k}\sum_{j=1}^{m}(u_i+v_j)\,P(X=u_i\cap Y=v_j)\\
&=\sum_{i=1}^{k}u_i\sum_{j=1}^{m}P(X=u_i\cap Y=v_j)+\sum_{j=1}^{m}v_j\sum_{i=1}^{k}P(X=u_i\cap Y=v_j)\\
&=\sum_{i=1}^{k}u_iP(X=u_i)+\sum_{j=1}^{m}v_jP(Y=v_j)\\
&=E(X)+E(Y).
\end{aligned}
$$

The third line used the marginal sums of §1, which hold whether or not the variables are independent, so the mean of a sum is the sum of the means for any random variables.

### The variance of a sum of independent variables

Write $\mu_X=E(X)$ and $\mu_Y=E(Y)$, so that $E(X+Y)=\mu_X+\mu_Y$. Then

$$
\begin{aligned}
\operatorname{Var}(X+Y)&=E\big\{[(X+Y)-(\mu_X+\mu_Y)]^2\big\}\\
&=E\big\{[(X-\mu_X)+(Y-\mu_Y)]^2\big\}\\
&=E\{(X-\mu_X)^2\}+E\{(Y-\mu_Y)^2\}+2E\{(X-\mu_X)(Y-\mu_Y)\}\\
&=\operatorname{Var}X+\operatorname{Var}Y+2E\{(X-\mu_X)(Y-\mu_Y)\}.
\end{aligned}
$$

The last term (twice the **covariance**) measures dependence. For independent discrete variables the joint probability factorises and the double sum splits into a product of single sums:

$$
\begin{aligned}
E\{(X-\mu_X)(Y-\mu_Y)\}&=\sum_i\sum_j(u_i-\mu_X)(v_j-\mu_Y)P(X=u_i)P(Y=v_j)\\
&=\Big[\sum_i(u_i-\mu_X)P(X=u_i)\Big]\Big[\sum_j(v_j-\mu_Y)P(Y=v_j)\Big]\\
&=(\mu_X-\mu_X)(\mu_Y-\mu_Y)\\
&=0 .
\end{aligned}
$$

Hence, for **independent** $X$ and $Y$,

$$
\operatorname{Var}(X+Y)=\operatorname{Var}X+\operatorname{Var}Y .
$$

Both results extend to any number of variables, discrete or continuous. In Example 13.19, $\operatorname{Var}X=E(X^2)-\mu_X^2=22.0-4.6^2=0.84$ and $\operatorname{Var}Y=7.55-2.65^2=0.5275$, and the distribution of the total gives $\operatorname{Var}(X+Y)=1.3675=0.84+0.5275$.

### Adding or multiplying by a constant

For a constant $c$ and a continuous $X$ with density $f_X$ (replace integrals by sums for a discrete $X$):

$$
\begin{aligned}
E(X+c)&=\int_{-\infty}^{\infty}(x+c)f_X(x)\,dx\\
&=\int_{-\infty}^{\infty}xf_X(x)\,dx+c\int_{-\infty}^{\infty}f_X(x)\,dx\\
&=\mu_X+c,
\end{aligned}
$$

$$
\begin{aligned}
\operatorname{Var}(X+c)&=\int_{-\infty}^{\infty}\big[(x+c)-(\mu_X+c)\big]^2f_X(x)\,dx\\
&=\int_{-\infty}^{\infty}(x-\mu_X)^2f_X(x)\,dx\\
&=\sigma_X^2,
\end{aligned}
$$

$$
E(cX)=\int_{-\infty}^{\infty}cxf_X(x)\,dx=c\mu_X,
$$

$$
\begin{aligned}
\operatorname{Var}(cX)&=\int_{-\infty}^{\infty}(cx-c\mu_X)^2f_X(x)\,dx\\
&=c^2\int_{-\infty}^{\infty}(x-\mu_X)^2f_X(x)\,dx\\
&=c^2\sigma_X^2 .
\end{aligned}
$$

A shift moves the mean and leaves the spread alone, and a scale factor multiplies the mean by $c$ and the variance by $c^2$ (the standard deviation by $|c|$). For example, a mean temperature of $58^\circ$F converts through $T_C=\frac59(T_F-32)$ to $E(T_C)=\frac59(58-32)=14.4^\circ$C (James Example 13.21).

### The mean and variance of a sample mean

Let $X_1,\dots,X_n$ be independent observations of the same random variable, each with mean $\mu_X$ and variance $\sigma_X^2$, and let $\bar X=\frac1n(X_1+\dots+X_n)$. The rules above give

$$
\begin{aligned}
E(\bar X)&=\frac1n\big[E(X_1)+\dots+E(X_n)\big]\\
&=\frac1n\,n\mu_X\\
&=\mu_X,
\end{aligned}
$$

$$
\begin{aligned}
\operatorname{Var}(\bar X)&=\frac1{n^2}\operatorname{Var}(X_1+\dots+X_n)\\
&=\frac1{n^2}\,n\sigma_X^2\\
&=\frac{\sigma_X^2}{n},
\end{aligned}
$$

where the second line used independence. The standard deviation of the sample mean is therefore

$$
\sigma_{\bar X}=\frac{\sigma_X}{\sqrt n},
$$

the **standard error of the mean**. It falls only as $1/\sqrt n$: four times the sample buys half the error. This result underlies §3 and §6–8.

## 3. Sample average and sample variance (James §13.4.10)

For data $x_1,\dots,x_n$ the **sample average** and the **sample variance** used in this module are

$$
\bar x=\frac1n\sum_{i=1}^{n}x_i,\qquad s^2=\frac{1}{n-1}\sum_{i=1}^{n}(x_i-\bar x)^2,
$$

and the sample standard deviation is $s=\sqrt{s^2}$. In James's notation $s^2$ is $S_{X,n-1}^2$. The divisor-$n$ version $S_X^2=\frac1n\sum(X_i-\bar X)^2$, James's first definition, is biased (shown below) and is not used in this module.

### The hand-calculation form

Expanding the square gives the form on the formula sheet:

$$
\begin{aligned}
\sum_{i=1}^n(x_i-\bar x)^2&=\sum x_i^2-2\bar x\sum x_i+n\bar x^2\\
&=\sum x_i^2-2\bar x(n\bar x)+n\bar x^2\\
&=\sum x_i^2-n\bar x^2,
\end{aligned}
$$

so

$$
s^2=\frac{\sum x_i^2-n\bar x^2}{n-1}.
$$

With only $\sum x_i$ and $\sum x_i^2$, both statistics follow. Keep $\bar x$ to several figures in $n\bar x^2$, because the subtraction loses significant digits.

### Why the divisor is n − 1

The deviations from the sample average always sum to zero,

$$
\sum_{i=1}^n(x_i-\bar x)=\sum x_i-n\bar x=0,
$$

so once $n-1$ of them are known the last is fixed. Only $n-1$ of the squared deviations are free, and $s^2$ averages over those $n-1$ independent pieces of information.

The same fact shows up in the mean of the sample variance. For each observation $E(X_i^2)=\operatorname{Var}X_i+\mu^2=\sigma^2+\mu^2$, and by §2 $E(\bar X^2)=\operatorname{Var}\bar X+\mu^2=\sigma^2/n+\mu^2$. Then

$$
\begin{aligned}
E\Big[\sum_{i=1}^n(X_i-\bar X)^2\Big]&=E\Big[\sum X_i^2-n\bar X^2\Big]\\
&=n(\sigma^2+\mu^2)-n\Big(\frac{\sigma^2}{n}+\mu^2\Big)\\
&=n\sigma^2-\sigma^2\\
&=(n-1)\sigma^2 .
\end{aligned}
$$

Dividing by $n-1$ gives $E(s^2)=\sigma^2$: averaged over many samples, $s^2$ equals the population variance, while the divisor-$n$ version is too small on average by the factor $(n-1)/n$. The two agree closely for large $n$ (booklet item 9).

### Die tossed 24 times (James Example 13.22)

The 24 scores are 4, 6, 2, 4, 2, 1, 5, 1, 3, 1, 3, 4, 5, 4, 3, 1, 6, 5, 6, 3, 1, 2, 4, 6, with $\sum x_i=82$ and $\sum x_i^2=352$.

$$
\bar x=\frac{82}{24}=3.417,
$$

$$
\begin{aligned}
s^2&=\frac{352-24(3.41667)^2}{23}\\
&=\frac{352-280.167}{23}\\
&=3.123,
\end{aligned}
$$

$$
s=1.767 .
$$

The divisor-$n$ value is $\sqrt{352/24-3.41667^2}=\sqrt{14.667-11.674}=1.730$; the theoretical values for a fair die are $\mu=3.5$ and $\sigma=\sqrt{35/12}=1.708$ (James Examples 13.16–13.17).

These figures carry more digits than the data justify. The sample average has standard error $s/\sqrt n\approx0.35$, and the relative error of a sample standard deviation is roughly $1/\sqrt{2n}$, 14% for $n=24$, so the error in $s$ is of order 0.2. Honest values are $\bar x=3.4$ (likely error of order 0.4) and $s\approx1.7$ (likely error of order 0.2).

### Reactor impurities (James Exercise 42(a))

Twelve specimens give impurity percentages 2.3, 1.9, 2.1, 2.8, 2.3, 3.6, 1.4, 1.8, 2.1, 3.2, 2.0, 1.9, so $\sum x=27.4$ and $\sum x^2=66.86$.

$$
\bar x=\frac{27.4}{12}=2.283\%,
$$

$$
\begin{aligned}
s^2&=\frac{66.86-12(2.28333)^2}{11}\\
&=\frac{4.2967}{11}\\
&=0.3906,
\end{aligned}
$$

$$
s=0.625\% .
$$

The divisor-$n$ version would give $0.598\%$. Part (b) of the exercise, outside the work scheme, has median 2.1 and range $3.6-1.4=2.2$.

### Component lifetimes (Specimen Test 25, Q1)

Ten lifetimes (thousands of hours) 5.6, 4.1, 6.0, 5.8, 5.2, 4.3, 6.4, 5.5, 6.0, 5.1 give $\sum x=54.0$ and $\sum x^2=296.56$:

$$
\bar x=5.40,\qquad s^2=\frac{296.56-10(5.4)^2}{9}=\frac{4.96}{9}=0.5511,\qquad s=0.742\ \text{thousand hours}.
$$

## 4. The binomial distribution (James §13.5.1)

A **Bernoulli trial** is one observation with two outcomes, success with probability $p$ and failure with probability $q=1-p$, recorded as $X=1$ or $X=0$. Its mean and variance are

$$
E(X)=1\cdot p+0\cdot q=p,\qquad E(X^2)=1^2\cdot p+0^2\cdot q=p,
$$

$$
\operatorname{Var}X=E(X^2)-[E(X)]^2=p-p^2=pq .
$$

### The probability formula

Let $Y=X_1+\dots+X_n$ count the successes in $n$ independent Bernoulli trials with the same $p$. A particular sequence with $k$ successes and $n-k$ failures, such as $\{1,1,0,1,0\}$ for $n=5$, $k=3$, has probability $p^kq^{n-k}$ by the product rule for independent events. The number of different sequences with $k$ successes is the number of ways to choose which $k$ of the $n$ trials succeed, $\binom nk=\frac{n!}{k!(n-k)!}$. The sequences are mutually exclusive, so the addition rule gives

$$
P(Y=k)=\binom nk p^k(1-p)^{n-k},\qquad k=0,1,\dots,n .
$$

This is the **binomial distribution** with parameters $n$ and $p$, written $Y\sim\mathrm{Bin}(n,p)$. By the binomial theorem the probabilities sum to $\sum_k\binom nkp^kq^{n-k}=(p+q)^n=1$. Since $Y$ is a sum of $n$ independent Bernoulli variables, §2 gives its mean and variance directly:

$$
E(Y)=np,\qquad\operatorname{Var}Y=npq=np(1-p).
$$

The model needs a fixed number of trials, two outcomes per trial, a constant $p$ and independence. "At least $k$" means $P(Y\ge k)=P(k)+\dots+P(n)$, which is usually quicker as the complement $1-P(Y\le k-1)$. The Poisson distribution (James §13.5.2), an approximation to the binomial for large $n$ and small $p$, is not part of this module, so every binomial question here is done with the exact formula.

![[m1054_m25_binomial_pmfs.png|900]]

The figure shows $\mathrm{Bin}(12,0.2)$, skewed because $p$ is small, the symmetric $\mathrm{Bin}(12,0.5)$, and $\mathrm{Bin}(40,0.5)$, with a normal curve of the same mean and variance overlaid on each. As $n$ grows the binomial, a sum of independent trials, takes the normal shape predicted by the central limit theorem of §6; for $\mathrm{Bin}(40,0.5)$, $P(Y\le24)=0.9231$ against $\Phi\big((24.5-20)/\sqrt{10}\big)=0.9226$ from the normal curve. This normal approximation to the binomial (James §13.5.5) is outside the work scheme.

### Stock claim (James Example 13.25)

A supplier claims that 95% of catalogue items are in stock at any time. An order for 20 different components comes back with 3 out of stock. If the claim is true, each item is out of stock with $p=0.05$, independently, so the number missing is $Y\sim\mathrm{Bin}(20,0.05)$ with mean $np=1$. The observed 3 or anything worse has probability

$$
\begin{aligned}
P(Y\ge3)&=1-\big[P(0)+P(1)+P(2)\big]\\
&=1-\big[0.95^{20}+20(0.05)(0.95)^{19}+190(0.05)^2(0.95)^{18}\big]\\
&=1-[0.3585+0.3774+0.1887]\\
&=0.0755 .
\end{aligned}
$$

An order this bad or worse would happen about once in 13 orders under the claim, so the outcome is fairly unlikely and gives some grounds to doubt the claim, though $0.0755>0.05$ means it would not be rejected at the 5% level of §8. The relevant probability is that of the tail, 3 or more, not of exactly 3: any single outcome can have a small probability, and the relevant quantity is how far into the tail the observation lies. The calculation also assumes every item has the same 5% chance and items run out independently, neither of which is guaranteed if several components come from one late consignment.

### Fire engines (James Exercise 50)

Five fire engines operate independently and each is in its station 94% of the time, so the number available is $X\sim\mathrm{Bin}(5,0.94)$:

$$
\begin{aligned}
P(X\ge3)&=\binom53(0.94)^3(0.06)^2+\binom54(0.94)^4(0.06)+(0.94)^5\\
&=0.0299+0.2342+0.7339\\
&=0.998 .
\end{aligned}
$$

### Defective drills (James Exercise 51)

Each drill is a reject with probability 0.02 and a box holds 100, so the number of rejects is $X\sim\mathrm{Bin}(100,0.02)$:

$$
P(0)=0.98^{100}=0.1326,\qquad P(1)=100(0.02)(0.98)^{99}=0.2707,\qquad P(2)=\binom{100}2(0.02)^2(0.98)^{98}=0.2734,
$$

$$
P(X\le2)=0.1326+0.2707+0.2734=0.677 .
$$

> [!check] Poisson cross-check
> The Poisson approximation with $\lambda=np=2$ (James §13.5.2, outside this module) gives $e^{-2}(1+2+2)=0.6767$, agreeing with the exact binomial $0.6767$ to four figures.

## 5. The normal distribution and standardisation (James §13.5.3)

A continuous random variable $X$ has the **normal distribution** with mean $\mu$ and variance $\sigma^2$, written $X\sim N(\mu,\sigma^2)$, if its density is

$$
f_X(x)=\frac{1}{\sigma\sqrt{2\pi}}\exp\Big[-\frac12\Big(\frac{x-\mu}{\sigma}\Big)^2\Big],\qquad-\infty<x<\infty,\ \sigma>0 .
$$

The curve is bell-shaped and symmetric about $\mu$, and $\sigma$ sets its width. It is also called the Gaussian distribution. Measured data often follow it because a measurement error is the sum of many small independent effects, which is the situation of the central limit theorem (§6).

> [!warning] The second parameter is the variance
> $N(4,4)$ means $\mu=4$ and $\sigma^2=4$, so $\sigma=2$. Standardising with $\sigma=4$ is the commonest error in this module. When a question gives "mean 600, standard deviation 25", write $N(600,25^2)$.

### Why mu and sigma are the mean and standard deviation

Substitute $u=(x-\mu)/\sigma$, so $x=\mu+\sigma u$ and $dx=\sigma\,du$, and use the Gaussian integral $\int_{-\infty}^{\infty}e^{-u^2/2}\,du=\sqrt{2\pi}$:

$$
\begin{aligned}
E(X)&=\int_{-\infty}^{\infty}x\,\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac12\left(\frac{x-\mu}{\sigma}\right)^2}dx\\
&=\frac1{\sqrt{2\pi}}\int_{-\infty}^{\infty}(\mu+\sigma u)e^{-u^2/2}\,du\\
&=\frac{\mu}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-u^2/2}\,du+\frac{\sigma}{\sqrt{2\pi}}\int_{-\infty}^{\infty}ue^{-u^2/2}\,du\\
&=\mu\cdot1+\sigma\cdot0\\
&=\mu,
\end{aligned}
$$

because $ue^{-u^2/2}$ is odd. For the variance, integrate $u\cdot\big(ue^{-u^2/2}\big)$ by parts, with $\int ue^{-u^2/2}\,du=-e^{-u^2/2}$:

$$
\begin{aligned}
\operatorname{Var}X&=\int_{-\infty}^{\infty}(x-\mu)^2f_X(x)\,dx\\
&=\frac{\sigma^2}{\sqrt{2\pi}}\int_{-\infty}^{\infty}u^2e^{-u^2/2}\,du\\
&=\frac{\sigma^2}{\sqrt{2\pi}}\Big\{\big[-ue^{-u^2/2}\big]_{-\infty}^{\infty}+\int_{-\infty}^{\infty}e^{-u^2/2}\,du\Big\}\\
&=\frac{\sigma^2}{\sqrt{2\pi}}\big\{0+\sqrt{2\pi}\big\}\\
&=\sigma^2 .
\end{aligned}
$$

### The standard normal and its table

The case $\mu=0$, $\sigma=1$ is the **standard normal** $Z\sim N(0,1)$, with density $\phi(z)=\frac1{\sqrt{2\pi}}e^{-z^2/2}$ and cumulative distribution function

$$
\Phi(z)=P(Z\le z)=\frac1{\sqrt{2\pi}}\int_{-\infty}^{z}e^{-u^2/2}\,du .
$$

This integral has no elementary antiderivative, so $\Phi$ is tabulated (James Figure 13.30, and a shorter table on the formula sheet), usually only for $z\ge0$. Negative arguments follow from the symmetry $\phi(-u)=\phi(u)$. Substitute $u=-v$:

$$
\begin{aligned}
\Phi(-z)&=\int_{-\infty}^{-z}\phi(u)\,du\\
&=\int_{\infty}^{z}\phi(-v)(-dv)\\
&=\int_{z}^{\infty}\phi(v)\,dv\\
&=1-\Phi(z).
\end{aligned}
$$

### Standardisation

By §2, subtracting the mean and dividing by the standard deviation gives a variable with mean 0 and variance 1 for any distribution:

$$
E\Big(\frac{X-\mu}{\sigma}\Big)=\frac{\mu-\mu}{\sigma}=0,\qquad\operatorname{Var}\Big(\frac{X-\mu}{\sigma}\Big)=\frac{\operatorname{Var}X}{\sigma^2}=1 .
$$

For a normal $X$ the result is still normal, a property most distributions do not share. Substituting $u=(t-\mu)/\sigma$, $dt=\sigma\,du$, in the distribution function shows it directly:

$$
\begin{aligned}
P(X\le x)&=\int_{-\infty}^{x}\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac12\left(\frac{t-\mu}{\sigma}\right)^2}dt\\
&=\int_{-\infty}^{(x-\mu)/\sigma}\frac{1}{\sigma\sqrt{2\pi}}e^{-u^2/2}\,\sigma\,du\\
&=\Phi\Big(\frac{x-\mu}{\sigma}\Big).
\end{aligned}
$$

So $Z=(X-\mu)/\sigma\sim N(0,1)$, and conversely $X=\mu+\sigma Z$. One table serves every normal distribution: an interval probability is

$$
P(a<X\le b)=\Phi\Big(\frac{b-\mu}{\sigma}\Big)-\Phi\Big(\frac{a-\mu}{\sigma}\Big),
$$

and an inverse problem (find $x$ with a given probability) reads $z$ from the table backwards and returns $x=\mu+z\sigma$. For a continuous variable $P(X<x)=P(X\le x)$, so strict and non-strict inequalities give the same answer.

### Central areas and critical values

The probability of lying within $z$ standard deviations of the mean is

$$
\begin{aligned}
P(\mu-z\sigma\le X\le\mu+z\sigma)&=P(-z\le Z\le z)\\
&=\Phi(z)-\Phi(-z)\\
&=2\Phi(z)-1 .
\end{aligned}
$$

Within one standard deviation (Booklet Example C) this is $2(0.8413-0.5000)=0.6826$ (exactly $0.6827$). Setting $2\Phi(z)-1$ equal to a chosen coverage gives the standard values:

| Central coverage | $\Phi(z)$ | $\pm z$ | One tail beyond $z$ |
|---|---|---|---|
| 68.3% | 0.8413 | 1 | 15.9% |
| 90% | 0.95 | 1.645 | 5% |
| 95% | 0.975 | 1.96 | 2.5% |
| 99% | 0.995 | 2.58 (2.576) | 0.5% |

The 95% value comes from $\Phi(z)=0.975$, not $0.95$: 5% outside the central interval is 2.5% in each tail. The one-tailed 5% point is the 90% two-sided point, $1.645$, often rounded to 1.64.

![[m1054_m25_normal_critical_values.png|900]]

### X ~ N(4, 4) in both directions (James Example 13.28)

Here $\mu=4$ and $\sigma=2$. (a)

$$
\begin{aligned}
P(X\le6.7)&=P\Big(Z\le\frac{6.7-4}{2}\Big)\\
&=\Phi(1.35)\\
&=0.9115 .
\end{aligned}
$$

(b) Find $c$ with $P(X>c)=0.1$. Then $P(X\le c)=0.9$, so $\Phi\big(\frac{c-4}{2}\big)=0.9$. The table gives $\frac{c-4}{2}=1.2816$ (1.282 to three decimals), so

$$
c=4+2(1.2816)=6.563,
$$

or $6.564$ with $z=1.282$. Part (a) uses the table forwards (a probability from an interval) and part (b) backwards (an interval from a probability).

### Rocket burn time (James Example 13.29)

The burn time is $X\sim N(600,25^2)$ seconds. (a) By symmetry $P(Z<-2)=P(Z>2)=1-\Phi(2)$:

$$
\begin{aligned}
P(X<550)&=P\Big(Z<\frac{550-600}{25}\Big)\\
&=\Phi(-2)\\
&=1-\Phi(2)\\
&=1-0.9772\\
&=0.0228 .
\end{aligned}
$$

(b)

$$
P(X>640)=P\Big(Z>\frac{640-600}{25}\Big)=1-\Phi(1.6)=1-0.9452=0.0548 .
$$

![[m1054_normal_tests.png|900]]

The left panel shows these two tail areas; the right panel belongs to [[#Wire strength, one-tailed test (Booklet Exercise E)]].

### Cement bags (James Exercise 59)

A filling machine puts $X\sim N(\mu,0.05^2)$ kg into "six-kilogram" bags, and only 3% may be under 6 kg. Then $P(X<6)=0.03$, so $\Phi\big(\frac{6-\mu}{0.05}\big)=0.03$. The table gives $\Phi(1.881)=0.97$, so by symmetry $\frac{6-\mu}{0.05}=-1.881$ and

$$
\begin{aligned}
\mu&=6+1.881(0.05)\\
&=6.094\ \text{kg}.
\end{aligned}
$$

### Steel rods and video components (Booklet Exercises A and B)

Rod lengths are $N(3.10,0.16^2)$ m. The proportion longer than 3.50 m is

$$
P(X>3.50)=P\Big(Z>\frac{0.40}{0.16}\Big)=P(Z>2.5)=1-0.9938=0.0062,
$$

about 0.6% of rods. Component lifetimes are $N(500,50^2)$ hours and a purchaser needs at least 95% to last over 400 hours:

$$
P(X>400)=P(Z>-2)=\Phi(2)=0.9772\ge0.95,
$$

so the batch meets the specification.

### Component weights (Specimen Test 25, Q2)

Weights are $N(18,2^2)$ kg. Over 21 kg: $P(Z>1.5)=1-0.9332=0.0668$. At most 19 kg: $P(Z\le0.5)=\Phi(0.5)=0.6915$.

## 6. The sampling distribution of the mean and the central limit theorem (booklet items 6–7)

A sample of $n$ observations $X_1,\dots,X_n$ drawn at random from a population gives a sample mean $\bar X$. A second sample gives a different value, so $\bar X$ is itself a random variable, and its distribution over repeated samples is the **sampling distribution** of the mean. §2 has already given its centre and spread:

$$
E(\bar X)=\mu_X,\qquad\sigma_{\bar X}=\frac{\sigma_X}{\sqrt n}.
$$

These hold for any parent distribution, normal, binomial or otherwise. The means of samples of four adult heights scatter less than single heights, because a sample of four usually mixes people above and below average.

The shape of the sampling distribution depends on the parent and on $n$. If the parent is normal, $\bar X$ is exactly normal for every $n$. If it is not, the **central limit theorem** (James Theorem 13.1) states that for independent, identically distributed $X_i$ with mean $\mu_X$ and variance $\sigma_X^2$,

$$
\bar X\to N\Big(\mu_X,\frac{\sigma_X^2}{n}\Big),\qquad Z=\frac{\bar X-\mu_X}{\sigma_X/\sqrt n}\to N(0,1)\quad\text{as }n\to\infty,
$$

in the sense that the distribution functions converge. For practical work $n\ge30$ counts as large. The approximation is good sooner for a symmetric parent and later for a strongly skewed one.

![[m1054_m25_clt_sample_means.png|900]]

The figure takes an exponential parent with $\mu=\sigma=1$, about as skewed as a common distribution gets. One observation is far from normal, the mean of four is still visibly skewed, and the mean of thirty is close to the normal curve with standard error $1/\sqrt{30}=0.183$.

| Sample size | Distribution of $Z=\dfrac{\bar X-\mu_X}{\sigma_X/\sqrt n}$ |
|---|---|
| $n\ge30$ | Good approximation to $N(0,1)$, whatever the parent distribution |
| $n<30$ | Approximately $N(0,1)$ if the parent is approximately normal |
| all $n$ | Exactly $N(0,1)$ if the parent is normal |

When $\sigma_X$ is unknown, a sample with $n\ge30$ estimates it well enough by $s$, and $Z=(\bar X-\mu_X)/(s/\sqrt n)$ is still treated as $N(0,1)$.

> [!warning] Small samples with unknown sigma
> For $n<30$ the value of $s$ fluctuates too much from sample to sample, and $(\bar X-\mu)/(s/\sqrt n)$ from a normal parent follows the $t$-distribution with $n-1$ degrees of freedom, which is not in this module. Its 95% two-sided point is $2.045$ for $n=30$ and $2.776$ for $n=5$, against $1.96$ for the normal, so using $1.96$ with a small sample and $s$ gives an interval that is too narrow.

### Standard error and sample size (Booklet Example A)

A population has $\sigma=2.0$. The standard errors for $n=9$, $25$ and $100$ are

$$
\frac{2}{\sqrt9}=0.667,\qquad\frac{2}{\sqrt{25}}=0.4,\qquad\frac2{\sqrt{100}}=0.2 .
$$

A standard error of 0.5 needs $2/\sqrt n=\frac12$, so $4/n=\frac14$ and $n=16$.

### Shaft diameters (Booklet Example B)

Diameters are $N(2.500,0.009^2)$ cm and samples have $n=9$. The parent is normal, so $\bar X$ is exactly normal with mean 2.500 cm and standard error $0.009/\sqrt9=0.003$ cm. The proportion of sample means above 2.506 cm is

$$
\begin{aligned}
P(\bar X>2.506)&=P\Big(Z>\frac{2.506-2.500}{0.003}\Big)\\
&=P(Z>2.0)\\
&=1-\Phi(2.0)\\
&=1-0.9772\\
&=0.0228,
\end{aligned}
$$

that is, 2.28%. A single shaft exceeds 2.506 cm with probability $P(Z>0.667)\approx0.25$; averaging nine shrinks the spread by 3.

### Light-bulb life (Booklet Example D)

Bulbs have mean life 800 h and standard deviation 48 h, parent distribution unspecified. A sample of $n=144$ is large, so by the central limit theorem $\bar X$ is approximately normal with mean 800 and standard error $48/\sqrt{144}=4$:

$$
\begin{aligned}
P(\bar X<790)&=P\Big(Z<\frac{790-800}{4}\Big)\\
&=P(Z<-2.5)\\
&=1-\Phi(2.5)\\
&=0.0062 .
\end{aligned}
$$

### Means exceeding mu by sigma/3 (Specimen Test 25, Q3)

The sampling distribution of $\bar X$ has mean $\mu$ and standard deviation $\sigma/\sqrt n$. With $n=9$ the standard error is $\sigma/3$, so the proportion of samples whose mean exceeds $\mu$ by at least $\sigma/3$ is

$$
P\Big(\bar X-\mu\ge\frac\sigma3\Big)=P\Big(Z\ge\frac{\sigma/3}{\sigma/3}\Big)=P(Z\ge1)=1-0.8413=0.1587 .
$$

## 7. Confidence intervals for the mean (booklet item 8)

The sample mean $\bar x$ is a **point estimate** of $\mu$, but a single number says nothing about its precision. A **confidence interval** $(\bar x-k,\ \bar x+k)$ is built so that, over repeated samples, a stated proportion of such intervals contain $\mu$.

### Derivation of the 95% interval

Assume $\sigma$ is known (or $n\ge30$ and $s$ replaces it) and that $Z=(\bar X-\mu)/(\sigma/\sqrt n)$ is $N(0,1)$ under the conditions of §6. From the table, 95% of the standard normal lies between $-1.96$ and $1.96$:

$$
P\Big(-1.96\le\frac{\bar X-\mu}{\sigma/\sqrt n}\le1.96\Big)=0.95 .
$$

Rearrange the right-hand inequality to isolate $\mu$:

$$
\begin{aligned}
\frac{\bar X-\mu}{\sigma/\sqrt n}&\le1.96\\
\bar X-\mu&\le1.96\frac{\sigma}{\sqrt n}\\
\bar X-1.96\frac{\sigma}{\sqrt n}&\le\mu .
\end{aligned}
$$

The left-hand inequality gives the other side in the same way:

$$
\begin{aligned}
-1.96&\le\frac{\bar X-\mu}{\sigma/\sqrt n}\\
\mu-\bar X&\le1.96\frac{\sigma}{\sqrt n}\\
\mu&\le\bar X+1.96\frac{\sigma}{\sqrt n}.
\end{aligned}
$$

Together,

$$
P\Big(\bar X-1.96\frac{\sigma}{\sqrt n}\le\mu\le\bar X+1.96\frac{\sigma}{\sqrt n}\Big)=0.95,
$$

so the **95% confidence interval** for $\mu$ is

$$
\bar x\pm1.96\frac{\sigma}{\sqrt n}.
$$

The same steps with the other points of §5 give $\bar x\pm1.645\,\sigma/\sqrt n$ (90%) and $\bar x\pm2.58\,\sigma/\sqrt n$ (99%). In general the $100(1-\alpha)\%$ interval is $\bar x\pm z_{\alpha/2}\,\sigma/\sqrt n$ with $\Phi(z_{\alpha/2})=1-\alpha/2$. Higher confidence gives a wider interval, and a larger sample a narrower one, in proportion to $1/\sqrt n$.

> [!tip] What the 95% refers to
> $\mu$ is a fixed number and the interval is what varies from sample to sample. "95% confidence" means that if the interval were computed for very many samples, about 95 in 100 of the intervals would contain $\mu$. Any one computed interval either contains $\mu$ or does not.

![[m1054_m25_ci_coverage.png|900]]

The figure draws 50 samples of 30 cartons from a filling process with $\mu=570$ ml and $\sigma=6$ ml (the setting of Booklet Exercise C) and the 95% interval from each. Every interval has the same width $2\times1.96\times6/\sqrt{30}=4.29$ ml, the centres scatter with the sample mean, and two of the fifty intervals miss $\mu$, close to the expected 5% (2.5 in 50).

### Copper content and the sample size needed (Booklet Example E)

Individual measurements of the copper percentage have $\sigma=2.0\%$. For a standard error below 0.3,

$$
\begin{aligned}
\frac{2}{\sqrt n}&<0.3\\
\sqrt n&>\frac{2}{0.3}\\
n&>\frac{4}{0.09}=44.4,
\end{aligned}
$$

so at least 45 measurements are needed. With $n=45$ and observed mean $\bar w=12.91\%$, the central limit theorem makes $\bar W$ approximately normal with standard error $2/\sqrt{45}=0.298$, and the 95% interval for the true percentage $\omega$ is

$$
\begin{aligned}
12.91\pm1.96(0.298)&=12.91\pm0.58\\
&=(12.33,\ 13.49)\%.
\end{aligned}
$$

In general, a margin $E=z\,\sigma/\sqrt n$ needs $n\ge(z\sigma/E)^2$, rounded up.

### Carton fill (Booklet Exercise C)

$\sigma=6$ ml, $n=30$ and $\bar x=570$ ml, so the standard error is $6/\sqrt{30}=1.095$ ml.

$$
90\%:\quad570\pm1.645(1.095)=570\pm1.80=(568.2,\ 571.8)\ \text{ml},
$$

$$
95\%:\quad570\pm1.96(1.095)=570\pm2.15=(567.9,\ 572.1)\ \text{ml}.
$$

The 95% interval is wider than the 90% one, as it must be to be right more often.

### Astronaut pulse rate (Booklet Exercise D)

$n=32$ trainees, mean increase $\bar x=26.4$ beats per minute, $s=4.28$. Since $n\ge30$, $s$ replaces $\sigma$ and the standard error is $4.28/\sqrt{32}=0.757$:

$$
26.4\pm1.96(0.757)=26.4\pm1.48=(24.9,\ 27.9)\ \text{beats per minute}.
$$

### Metal bars (Specimen Test 25, Q4)

$n=100$, $\bar x=120$ mm and $s^2=400$ mm². The population standard deviation is estimated by $s=20$ mm, the standard error of the mean is $20/\sqrt{100}=2$ mm, and the 95% interval is $120\pm1.96(2)=(116.1,\ 123.9)$ mm.

## 8. Hypothesis tests for the mean (booklet item 10)

A **statistical hypothesis** is an assumption about the population. The **null hypothesis** $H_0$ fixes a parameter value, here $H_0:\mu=\mu_0$. The **alternative hypothesis** $H_1$ is a range of values, and it takes one of three forms:

$$
\text{(i) }H_1:\mu>\mu_0,\qquad\text{(ii) }H_1:\mu<\mu_0,\qquad\text{(iii) }H_1:\mu\ne\mu_0 .
$$

Forms (i) and (ii) are **one-sided** (one-tailed) and form (iii) is **two-sided** (two-tailed). The wording decides: "an improvement", "greater than", "increased" point one way; "different from", "a change" do not.

### The test statistic and the rejection region

If $H_0$ is true, the statistic

$$
Z=\frac{\bar X-\mu_0}{\sigma/\sqrt n}
$$

is $N(0,1)$, exactly or approximately under the conditions of §6, with $s$ for $\sigma$ when $n\ge30$. Values of $Z$ far from 0 in the direction of $H_1$ are unlikely under $H_0$. The **rejection region** is the set of such values, chosen so that its probability under $H_0$ equals the **significance level** $\alpha$, fixed before testing (usually 5% or 1%); the rest is the **acceptance region**:

| $H_1$ | Reject $H_0$ at level $\alpha$ when | 5% | 1% |
|---|---|---|---|
| $\mu>\mu_0$ | $Z>z_\alpha$ | $Z>1.645$ | $Z>2.326$ |
| $\mu<\mu_0$ | $Z<-z_\alpha$ | $Z<-1.645$ | $Z<-2.326$ |
| $\mu\ne\mu_0$ | $\lvert Z\rvert>z_{\alpha/2}$ | $\lvert Z\rvert>1.96$ | $\lvert Z\rvert>2.58$ |

Here $\Phi(z_\alpha)=1-\alpha$. A two-tailed test splits $\alpha$ between the tails, $\alpha/2$ in each, which is why its 5% critical value is the 95% confidence point $1.96$, while a one-tailed test puts all of $\alpha$ in one tail and uses $1.645$.

> [!warning] One tail or two
> The same data can be significant in a one-tailed test and not in a two-tailed one: $Z=1.80$ exceeds $1.645$ but not $1.96$. Decide the form of $H_1$ from the question's wording before computing $Z$, never from the sign or size of the result.

### Errors and the p-value

A decision from a sample can be wrong in two ways. A **type I error** rejects $H_0$ when it is true. The rejection region was built to have probability $\alpha$ under $H_0$, so

$$
P(\text{type I error})=P(\text{reject }H_0\mid H_0\text{ true})=\alpha,
$$

which is the significance level. A **type II error** accepts $H_0$ when it is false; its probability depends on the true $\mu$ and is not fixed by the test. Lowering $\alpha$ widens the acceptance region and makes type II errors more likely.

The **p-value** is the probability under $H_0$ of a result at least as extreme as the one observed, in the direction(s) of $H_1$: $P(Z\ge z_{\text{obs}})$ for $H_1:\mu>\mu_0$, and $2P(Z\ge|z_{\text{obs}}|)$ for $H_1:\mu\ne\mu_0$. $H_0$ is rejected at level $\alpha$ exactly when $p<\alpha$. "Accept $H_0$" means only that the data are consistent with it, not that it is proved.

### Tests and confidence intervals agree

For a two-sided test at 5%, $H_0$ is accepted when

$$
-1.96\le\frac{\bar x-\mu_0}{\sigma/\sqrt n}\le1.96,
$$

and multiplying through by $\sigma/\sqrt n$ and rearranging each side as in §7 turns this into

$$
\bar x-1.96\frac{\sigma}{\sqrt n}\le\mu_0\le\bar x+1.96\frac{\sigma}{\sqrt n},
$$

that is, exactly when $\mu_0$ lies inside the 95% confidence interval of §7. A 95% interval is the set of values of $\mu_0$ that a two-tailed 5% test would accept.

### Yarn breaking strength (Booklet Example F)

A standard process gives yarn with mean breaking strength 15.8 kg and standard deviation 1.9 kg. After a modification, 30 lengths have mean 16.5 kg; assume $\sigma$ is unchanged. The test is whether the mean has changed, in either direction, so

$$
H_0:\mu=15.8,\qquad H_1:\mu\ne15.8\quad\text{(two-tailed)}.
$$

At 5% there is 2.5% in each tail, since $P(Z>1.96)=1-\Phi(1.96)=0.025$, so accept $H_0$ if $-1.96\le Z\le1.96$. The data give

$$
\begin{aligned}
Z&=\frac{16.5-15.8}{1.9/\sqrt{30}}\\
&=\frac{0.7}{0.3469}\\
&=2.018>1.96,
\end{aligned}
$$

so $H_0$ is rejected at the 5% level: the evidence suggests the mean breaking strength has changed ($p=0.044$).

If the modification was designed to increase the strength, the alternative becomes $H_1:\mu>15.8$, one-tailed, with all 5% in the upper tail: accept $H_0$ if $Z\le1.645$. Again $Z=2.018$ falls in the rejection region, now with $p=0.022$. The rejection region depends on both the form of $H_1$ and the significance level.

> [!check] The yarn result as an interval
> The 95% interval for the new mean is $16.5\pm1.96(0.3469)=(15.82,\ 17.18)$ kg. It just excludes 15.8, which agrees with the two-tailed rejection at 5% and with $Z=2.018$ being only just beyond $1.96$.

### Wire strength, one-tailed test (Booklet Exercise E)

The existing process gives wire strength $N(1250,150^2)$. A new process gives $\bar x=1312$ from 25 measurements, with $\sigma$ unchanged. "Is the new process an improvement?" points one way:

$$
H_0:\mu=1250,\qquad H_1:\mu>1250\quad\text{(one-tailed, 5\%)}.
$$

$$
\begin{aligned}
Z&=\frac{\bar x-\mu_0}{\sigma/\sqrt n}\\
&=\frac{1312-1250}{150/\sqrt{25}}\\
&=\frac{62}{30}\\
&=2.07 .
\end{aligned}
$$

Since $2.07>1.645$, reject $H_0$: there is evidence at the 5% level that the new process improves the strength, with $p=P(Z\ge2.07)=0.019$. Equivalently, any sample mean above $1250+1.645(30)=1299.4$ would have led to rejection. A type II error is a real risk near that boundary: if the new process truly had $\mu=1300$, the test would accept $H_0$ with probability $\Phi\big((1299.35-1300)/30\big)=0.49$.

### Phosphorus content, two-tailed test (Booklet Exercise F)

The phosphorus content is thought to be 3%. 64 analyses give mean 3.3% with $s=0.8\%$. "Significantly different" is two-tailed:

$$
H_0:\mu=3,\qquad H_1:\mu\ne3 .
$$

With $n=64\ge30$, $s$ replaces $\sigma$:

$$
Z=\frac{3.3-3}{0.8/\sqrt{64}}=\frac{0.3}{0.1}=3.0 .
$$

$|Z|=3.0>1.96$, so reject $H_0$ at 5%, and $3.0>2.58$ as well, so the difference is significant at 1% too ($p=2P(Z>3)=0.0027$). The sample mean is significantly different from 3%.

### Light-bulb life test (Specimen Test 25, Q5)

100 bulbs have mean life 3580 h with $s=400$ h; the test is whether the brand's mean exceeds 3500 h. Then $H_0:\mu=3500$, $H_1:\mu>3500$, a one-sided test. At 5% the rejection region is $Z>1.645$ and the acceptance region $Z\le1.645$.

![[m1054_spec25_test.png|700]]

$$
Z=\frac{3580-3500}{400/\sqrt{100}}=\frac{80}{40}=2.0>1.645,
$$

so $H_0$ is rejected at 5%: the mean life exceeds 3500 h. The probability of a sample mean of 3580 or more when the true mean is 3500 is $P(Z\ge2)=0.0228$, the p-value of the test.

## Terminology and alternative names

| Term used here | Also written or called | Note |
|---|---|---|
| sample variance $s^2$ (divisor $n-1$) | $S^2_{X,n-1}$ (James), $\sigma^2_{n-1}$ on calculators | James's $S_X^2$ has divisor $n$ and is not used |
| standard error $\sigma/\sqrt n$ | $\sigma_{\bar X}$, standard deviation of the sample mean, SE | |
| $q$ | $1-p$, probability of failure | $\operatorname{Var}Y=npq$ |
| normal distribution | Gaussian distribution | |
| one-sided / two-sided test | one-tailed / two-tailed | |
| accept $H_0$ | do not reject $H_0$, insufficient evidence | |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M25 Solutions - Statistics II]] · Formula sheet: [[MATH1054 Formula Sheet]]
- Previous: [[MATH1054 M24 - Statistics I]] (probability rules, random variables, mean and variance). M25 is the last module of the course.
- Concepts: [[Binomial Distribution]] · [[Normal Distribution and Standardisation]] · [[Confidence Intervals and Hypothesis Tests for the Mean]] · [[Probability Rules and Conditional Probability]] · [[Random Variables, PDF and CDF]] · [[Mean, Median and Variance of a Distribution]]
- Later in the vault: the $\pm2\sigma$ (95%) uncertainty band of a measurement in [[FEEG1004 E1 - Measurement Systems and Temperature Sensors]]; Gaussian sensor noise and $\pm2\sigma$ in [[Accuracy and Precision]] and [[SESA2027 C2 - Sensor Characteristics, Dynamics and Design#Noise and SNR]]; the moving-average filter, whose noise falls by $\sqrt N$ exactly as the standard error does, in [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#Moving average (FIR)]]; stochastic model updating with parameter distributions in [[SESA2029 B10 - FE Verification, Validation and Model Updating]], [[Model Updating]] and [[Verification and Validation]].

## Sources

- MATH1054 Module Booklet, Module 25 (PDF pp. 87–95; module pp. 1–9): work-scheme items 1–5 (James sections), items 6–10 (sampling, central limit theorem, confidence intervals, hypothesis tests), Examples A–F, Exercises A–F, Specimen Test 25.
- James, *Modern Engineering Mathematics* (6th ed.): §13.4.8 independence (p. 1034, Example 13.19); §13.4.9 scaling and adding (pp. 1035–1037, Examples 13.20–13.21); §13.4.10 sample data (pp. 1037–1039, Example 13.22); §13.5.1 binomial (pp. 1044–1046, Example 13.25); §13.5.3 normal (pp. 1049–1052, Figure 13.30, Examples 13.28–13.29); §13.5.4 central limit theorem (Theorem 13.1); Exercises 42 (p. 1042), 50, 51, 59 (pp. 1059–1060).
- Worked solutions: [[MATH1054 M25 Solutions - Statistics II]]. Figures: `generate_m1054_m25_figures.py`.

## Self-study tasks

### Core

- [ ] Exercise 42(a), sample average and $n-1$ standard deviation only (Module 25 work scheme, item 3). → [[MATH1054 M25 Solutions - Statistics II#Part B: Assigned exercises|solution]] · [[#Reactor impurities (James Exercise 42(a))]]
- [ ] Exercises 50 and 51, binomial probabilities (Module 25 work scheme, item 5). → [[MATH1054 M25 Solutions - Statistics II#Part B: Assigned exercises|solutions]] · [[#Fire engines (James Exercise 50)]]
- [ ] Exercise 59 and Booklet Exercises A and B, normal probabilities forwards and backwards (Module 25 work scheme, items 5 and 7). → [[MATH1054 M25 Solutions - Statistics II#Exercise 59: Mean fill so that only 3% of bags are under 6 kg|solution]] · [[#Cement bags (James Exercise 59)]]
- [ ] Booklet Exercises C and D, confidence intervals (Module 25 work scheme, item 8). → [[MATH1054 M25 Solutions - Statistics II#Part B: Assigned exercises|solutions]] · [[#Carton fill (Booklet Exercise C)]]
- [ ] Booklet Exercises E and F, one- and two-tailed tests (Module 25 work scheme, item 10). → [[MATH1054 M25 Solutions - Statistics II#Booklet Exercise E: Is the new wire process an improvement? (5% level)|E]] · [[MATH1054 M25 Solutions - Statistics II#Booklet Exercise F: Phosphorus content, is 3.3% significantly different from 3%?|F]]

### Further practice

- [ ] Specimen Test 25, Q1–Q5 (Module Booklet, final page of Module 25), timed. → [[MATH1054 M25 Solutions - Statistics II#Part C: Specimen Test 25|solutions]] · [[MATH1054 M25 Solutions - Statistics II#Q1: Sample statistics|Q1]]
- [ ] Work Examples 13.19, 13.22, 13.25, 13.28 and 13.29 without the solution (Module 25 work scheme, items 1–5). → [[MATH1054 M25 Solutions - Statistics II#Part A: Worked examples|solutions]]
- [ ] Booklet Examples A–F on sampling, intervals and tests (Module 25 work scheme, items 6–10). → [[#6. The sampling distribution of the mean and the central limit theorem (booklet items 6–7)]] · [[#Yarn breaking strength (Booklet Example F)]]

## Transcript and slide slips

> [!warning] James, *Modern Engineering Mathematics* (6th ed.), §13.4.9–13.4.10
> Where: [[#2. Scaling and adding random variables (James §13.4.9)]] and [[#Die tossed 24 times (James Example 13.22)]]
>
> | Where | James prints | Correct |
> |---|---|---|
> | Example 13.21, p. 1037 | $E(T_C)=\frac59(58-32)=13.4^\circ$C | $\frac59(26)=14.4^\circ$C |
> | Example 13.22, p. 1038 | "The average of the squares is 13.667", $S_X=\sqrt{13.667-3.42^2}=1.73$ | the average of the squares is $352/24=14.667$; with it $S_X=1.73$ is right (13.667 would give 1.40) |

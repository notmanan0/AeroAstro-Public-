---
title: "MATH1054 M25 Solutions - Statistics II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 5: Series and Statistics"
tags:
  - math1054
  - tutorial-solutions
  - statistics
  - normal-distribution
  - hypothesis-testing
sheet: "Specimen Test 25 (booklet) + Module 25 work scheme: Examples 13.19–13.29; Exercises 42(a), 50, 51, 59; Booklet Exercises A–F"
theory_notes: ["[[MATH1054 M25 - Statistics II]]"]
key_concepts: ["[[Binomial Distribution]]", "[[Normal Distribution and Standardisation]]", "[[Confidence Intervals and Hypothesis Tests for the Mean]]"]
status: complete
sources: ["tmp/md/module_25_statistics_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§13.4.x, §13.5)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 25)"]
---

# MATH1054 M25 Solutions - Statistics II

> [!abstract] Sheet Info
> The whole Module 25 work scheme. Checks: binomial and normal probabilities with `scipy.stats`; sample statistics with NumPy.
>
> **Booklet conventions**:
> - The **sample variance** uses the $n-1$ divisor, $s^2=\frac1{n-1}\sum(x_i-\bar x)^2$. The booklet flags James's divisor $n$ as "not correct".
> - For $n\ge30$, replace $\sigma$ by $s$.
> - Critical values: $1.96$ (95%, two-tailed), $2.58$ (99%, two-tailed), $1.645$ (90% two-tailed, or 5% one-tailed).
> - The Poisson distribution is **not** used in this module.

## Theory Links
- [[MATH1054 M25 - Statistics II]] · [[Binomial Distribution]] · [[Normal Distribution and Standardisation]] · [[Confidence Intervals and Hypothesis Tests for the Mean]]

---

# Part A: Worked examples

## Example 13.19: Joint distribution of installation and commissioning time
The two stages are independent, so $P(X=u,Y=v)=P(X=u)\,P(Y=v)$.

| $X\backslash Y$ | 2 | 3 | 4 | $P(X)$ |
|---|---|---|---|---|
| 3 | 0.050 | 0.035 | 0.015 | 0.1 |
| 4 | 0.200 | 0.140 | 0.060 | 0.4 |
| 5 | 0.150 | 0.105 | 0.045 | 0.3 |
| 6 | 0.100 | 0.070 | 0.030 | 0.2 |
| $P(Y)$ | 0.50 | 0.35 | 0.15 | 1 |

**Total time at most 7 days**: add every cell with $u+v\le7$:
- $X=3$: the whole row, $0.1$
- $X=4$: $Y=2,3$, giving $0.2+0.14$
- $X=5$: $Y=2$, giving $0.15$

$$P(X+Y\le7)=0.1+0.34+0.15=\boxed{0.59}$$

## Example 13.22: Die tossed 24 times
$n=24$, $\sum x_i=82$ and $\sum x_i^2=352$.

$$\bar x=\frac{82}{24}=\boxed{3.417},\qquad s^2=\frac{\sum x_i^2-n\bar x^2}{n-1}=\frac{352-280.17}{23}=3.123,\qquad s=\boxed{1.767}$$

James's divisor-$n$ version gives $1.730$. The theoretical value for a fair die is $\sigma=1.708$ (Ex 13.17).

## Example 13.25: 3 items out of stock in an order of 20
Suppose the claim is true, so each item is out of stock with $p=0.05$. Then the number missing is $X\sim\mathrm{Bin}(20,0.05)$:

$$P(X\ge3)=1-\big[P(0)+P(1)+P(2)\big]=1-\big[0.3585+0.3774+0.1887\big]=\boxed{0.0755}$$

An outcome this bad or worse happens about once in every 13 orders. That makes it **fairly unlikely** and gives some grounds to doubt the 95% claim. But it is not conclusive: $0.075>0.05$, so the claim would not be rejected at the 5% level.

## Example 13.28: $X\sim N(4,4)$, so $\mu=4$ and $\sigma=2$
**(a)**

$$P(X\le6.7)=\Phi\Big(\frac{6.7-4}{2}\Big)=\Phi(1.35)=\boxed{0.9115}$$

**(b)** $P(X>c)=0.1$ means $\Phi\big(\frac{c-4}2\big)=0.9$. The table gives $\frac{c-4}2=1.2816$, so $c=\boxed{6.563}$.

> [!warning] $N(\mu,\sigma^2)$ notation
> The second parameter is the **variance**. $N(4,4)$ has $\sigma=2$, not 4.

## Example 13.29: Rocket burn time, $X\sim N(600,25^2)$
**(a)**

$$P(X<550)=\Phi\Big(\frac{550-600}{25}\Big)=\Phi(-2)=1-0.9772=\boxed{0.0228}$$

**(b)**

$$P(X>640)=1-\Phi(1.6)=1-0.9452=\boxed{0.0548}$$

![[m1054_normal_tests.png|800]]

---

# Part B: Assigned exercises

## Exercise 42(a): Reactor impurities (sample average and corrected $s$ only)
$n=12$, $\sum x=27.4$ and $\sum x^2=66.86$.

$$\bar x=\frac{27.4}{12}=\boxed{2.283\%},\qquad s^2=\frac{66.86-12(2.2833)^2}{11}=\frac{4.2967}{11}=0.3906,\qquad s=\boxed{0.625\%}$$

(For reference, part (b) would give a median of 2.1 and a range of 2.2.)

## Exercise 50: Five fire engines, each available with $p=0.94$
The number available is $X\sim\mathrm{Bin}(5,0.94)$:

$$P(X\ge3)=\binom53(0.94)^3(0.06)^2+\binom54(0.94)^4(0.06)+(0.94)^5=0.0299+0.2342+0.7339=\boxed{0.998}$$

## Exercise 51: Defective drills, $n=100$, $p=0.02$
The number defective is $X\sim\mathrm{Bin}(100,0.02)$. Use the exact binomial, since Poisson is not in this module:
- $P(0)=0.98^{100}=0.1326$
- $P(1)=100(0.02)(0.98)^{99}=0.2707$
- $P(2)=\binom{100}2(0.02)^2(0.98)^{98}=0.2734$

$$P(X\le2)=\boxed{0.677}$$

(The Poisson approximation with $\lambda=2$ gives 0.677, which agrees.)

## Exercise 59: Mean fill so that only 3% of bags are under 6 kg
We need $P(X<6)=0.03$, i.e. $\Phi\big(\frac{6-\mu}{0.05}\big)=0.03$. The table gives $\frac{6-\mu}{0.05}=-1.881$, so

$$\mu=6+1.881(0.05)=\boxed{6.094\ \text{kg}}$$

## Booklet Exercise A: Steel rods, $N(3.10,0.16^2)$

$$P(X>3.50)=P\Big(Z>\frac{0.40}{0.16}\Big)=P(Z>2.5)=1-0.9938=\boxed{0.0062}$$

So about 0.6% of rods are longer than 3.50 m.

## Booklet Exercise B: Video components, $N(500,50^2)$

$$P(X>400)=P(Z>-2)=\Phi(2)=0.9772$$

Since $0.9772\ge0.95$, **yes**: the batch meets the specification.

## Booklet Exercise C: Carton fill, $\sigma=6$ ml, $n=30$, $\bar x=570$
The standard error is $\frac{\sigma}{\sqrt n}=\frac6{\sqrt{30}}=1.095$ ml.
- **90%**: $570\pm1.645(1.095)=570\pm1.80$, giving $\boxed{(568.2,\ 571.8)\ \text{ml}}$.
- **95%**: $570\pm1.96(1.095)=570\pm2.15$, giving $\boxed{(567.9,\ 572.1)\ \text{ml}}$.

A higher confidence level gives a wider interval.

## Booklet Exercise D: Astronaut pulse rate, $n=32$, $\bar x=26.4$, $s=4.28$
Since $n\ge30$, use $s$ for $\sigma$. The standard error is $\frac{4.28}{\sqrt{32}}=0.757$.

$$26.4\pm1.96(0.757)=26.4\pm1.48\ \Rightarrow\ \boxed{(24.9,\ 27.9)}\ \text{beats per minute}$$

## Booklet Exercise E: Is the new wire process an improvement? (5% level)
- $H_0$: $\mu=1250$ (no change).
- $H_1$: $\mu>1250$ (an improvement). This is **one-tailed**.

$$Z=\frac{\bar x-\mu_0}{\sigma/\sqrt n}=\frac{1312-1250}{150/5}=\frac{62}{30}=2.07$$

The one-tailed 5% critical value is $1.645$. Since $2.07>1.645$, **reject $H_0$**: there is evidence at the 5% level that the new process improves the strength. The $p$-value is $0.019$.

## Booklet Exercise F: Phosphorus content, is 3.3% significantly different from 3%?
- $H_0$: $\mu=3$.
- $H_1$: $\mu\neq3$. "Different" makes it **two-tailed**.

$n=64\ge30$, so use $s=0.8$:

$$Z=\frac{3.3-3}{0.8/\sqrt{64}}=\frac{0.3}{0.1}=3.0$$

- $|Z|=3.0>1.96$, so **reject $H_0$** at 5%.
- $3.0>2.58$ as well, so it is significant at 1% too ($p=0.0027$).

The sample mean **is** significantly different from 3%.

---

# Part C: Specimen Test 25

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 25), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Sample statistics
$n=10$, $\sum x=54.0$ and $\sum x^2=296.56$.

$$\bar x=\boxed{5.40},\qquad s^2=\frac{296.56-10(5.4)^2}{9}=\frac{4.96}9=0.5511,\qquad s=\boxed{0.742}\ \text{(thousand hours)}$$

## Q2: $X\sim N(18,2^2)$
**(i)**

$$P(X>21)=P(Z>1.5)=1-0.9332=\boxed{0.0668}$$

**(ii)**

$$P(X\le19)=\Phi(0.5)=\boxed{0.6915}$$

## Q3: The sampling distribution of $\bar X$
(i) The mean is $\mu$.
(ii) The standard deviation (the standard error) is $\sigma/\sqrt n$.
(iii) With $n=9$, the SE is $\sigma/3$, so

$$P\big(\bar X-\mu\ge\tfrac\sigma3\big)=P(Z\ge1)=1-0.8413=\boxed{0.1587}$$

## Q4: $n=100$, $\bar x=120$ mm, $s^2=400$ mm²
(i) $\sigma\approx s=\boxed{20\ \text{mm}}$.
(ii) SE $=\frac{20}{\sqrt{100}}=\boxed{2\ \text{mm}}$.
(iii) The 95% CI is $120\pm1.96(2)$, i.e. $\boxed{(116.1,\ 123.9)\ \text{mm}}$.

## Q5: Light bulbs, $n=100$, $\bar x=3580$, $s=400$
**(i)** $H_0$: $\mu=3500$ hours.
**(ii)** $H_1$: $\mu>3500$ hours.
**(iii)** It is a **one-sided** test ("greater than").

**(iv)** At the 5% level, the rejection region is $Z>1.645$ and the acceptance region is $Z\le1.645$:

![[m1054_spec25_test.png|560]]

**(v)**

$$Z=\frac{3580-3500}{400/\sqrt{100}}=\frac{80}{40}=2.0>1.645$$

So **reject $H_0$**: the mean life does exceed 3500 hours, at the 5% level.

**(vi)**

$$P(\bar X\ge3580\mid\mu=3500)=P(Z\ge2)=\boxed{0.0228}$$

This is the $p$-value of the test.

## Sources
- Transcribed problem statements: `tmp/md/module_25_statistics_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §13.4–13.5; MATH1054 Module Booklet, Module 25 (confidence intervals and tests, booklet pp.87–95)

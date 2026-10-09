---
title: "MATH1054 M24 Solutions - Statistics I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 5: Series and Statistics"
tags:
  - math1054
  - tutorial-solutions
  - probability
  - random-variables
sheet: "Specimen Test 24 (booklet) + Module 24 work scheme: Examples 13.1–13.17; Exercises 18, 19, 22, 28, 33, 38; Booklet Exercise A"
theory_notes: ["[[MATH1054 M24 - Statistics I]]"]
key_concepts: ["[[Probability Rules and Conditional Probability]]", "[[Random Variables, PDF and CDF]]", "[[Mean, Median and Variance of a Distribution]]"]
status: complete
sources: ["tmp/md/module_24_statistics_i.md", "02 - Sources/Modern Engineering Mathematics.pdf (§13.2–13.4)", "02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 24)"]
---

# MATH1054 M24 Solutions - Statistics I

> [!abstract] Sheet Info
> The whole Module 24 work scheme. Every probability, mean, variance and quantile was checked in Python.
>
> **Notation**:
> - $p_X(x)=P(X=x)$ is the probability function of a discrete random variable.
> - $f_X$ is the density of a continuous one.
> - $F_X(x)=P(X\le x)$ is the (cumulative) distribution function.
> - $\operatorname{Var}X=E[X^2]-(E[X])^2$.

## Theory Links
- [[MATH1054 M24 - Statistics I]] · [[Probability Rules and Conditional Probability]] · [[Random Variables, PDF and CDF]] · [[Mean, Median and Variance of a Distribution]]

---

# Part A: Worked examples

## Examples 13.1 and 13.2: Sample spaces and events
- **Die**: $S=\{1,\dots,6\}$ and the event "even" is $E=\{2,4,6\}$. The outcome 5 is not in $E$, so $E$ did not occur.
- **Two coin tosses**: $S=\{\mathrm{HH},\mathrm{HT},\mathrm{TH},\mathrm{TT}\}$ and the event "same result twice" is $\{\mathrm{HH},\mathrm{TT}\}$. The outcome TT lies in it, so the event occurred.

With equally likely outcomes, $P(E)=\frac{|E|}{|S|}$. So $P(\text{even})=\frac36=\frac12$ and $P(\text{same})=\frac24=\frac12$.

## Example 13.12: Ship arrivals, probability and distribution functions
| $x$ | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| $p_X(x)$ | 0.10 | 0.30 | 0.35 | 0.20 | 0.05 |
| $F_X(x)$ | 0.10 | 0.40 | 0.75 | 0.95 | 1.00 |

$F_X$ is a **step function**. It jumps by $p_X(x)$ at each integer, and is flat (right-continuous) in between.

![[m1054_ships_pmf_cdf.png|760]]

## Example 13.13: Exponential lifetime, $f_X(x)=\frac12e^{-x/2}$ for $x\ge0$

$$F_X(x)=\int_0^x\tfrac12e^{-t/2}\,\mathrm dt=\boxed{1-e^{-x/2}}\quad(x\ge0),\qquad F_X=0\ (x<0)$$

The density starts at $\frac12$ and decays. The distribution function rises from 0 towards 1. (Units: thousands of hours.)

![[m1054_lifetime_pdf_cdf.png|760]]

## Example 13.14: The proportion lasting more than 6000 hours

$$P(X>6)=1-F_X(6)=e^{-3}=\boxed{0.0498}$$

That is about 5% of components.

## Example 13.16: Mean, median and mode
| Variable | Mean $E[X]$ | Median | Mode |
|---|---|---|---|
| (a) die | $\frac{1+2+\cdots+6}6=3.5$ | any value in $[3,4]$; conventionally $3.5$ | none: all outcomes are equally likely |
| (b) ships | $0(0.1)+1(0.3)+2(0.35)+3(0.2)+4(0.05)=1.8$ | $2$, since $F(1)=0.4<0.5\le F(2)$ | $2$ (largest $p$) |
| (c) lifetime | $\int_0^\infty x\frac12e^{-x/2}\,\mathrm dx=2$ | $1-e^{-m/2}=\frac12$, so $m=2\ln2=1.386$ | $0$ (the density is largest at $x=0$) |

For the exponential distribution, mode < median < mean. This is typical of a right-skewed distribution.

## Example 13.17: Variance and standard deviation
**(a) Die**: $E[X^2]=\frac{91}6$, so

$$\operatorname{Var}=\frac{91}6-3.5^2=\frac{35}{12}=2.917,\qquad\sigma=1.708$$

**(b) Ships**: $E[X^2]=0.3+1.4+1.8+0.8=4.30$, so

$$\operatorname{Var}=4.30-1.8^2=1.06,\qquad\sigma=1.030$$

**(c) Lifetime**: by parts twice, $E[X^2]=\int_0^\infty x^2\cdot\frac12e^{-x/2}\,\mathrm dx=8$. So

$$\operatorname{Var}=8-4=4,\qquad\sigma=2$$

For an exponential distribution, $\sigma$ equals the mean.

**Interquartile range** of the lifetime: the quartiles solve $F(q)=\frac14$ and $F(q)=\frac34$:

$$Q_1=-2\ln\tfrac34=0.575,\qquad Q_3=-2\ln\tfrac14=2.773$$

$$\boxed{\text{IQR}=Q_3-Q_1=2\ln3=2.197}\ \text{thousand hours}$$

---

# Part B: Assigned exercises

## Exercise 18: $P(A)=0.3$, $P(B)=0.4$, $P(B\mid A)=0.5$
**(a)** $P(A\cap B)=P(A)P(B\mid A)=0.3\times0.5=\boxed{0.15}$

**(b)** $P(A\cup B)=P(A)+P(B)-P(A\cap B)=0.3+0.4-0.15=\boxed{0.55}$

**(c)**

$$P(B\mid\bar A)=\frac{P(B\cap\bar A)}{P(\bar A)}=\frac{P(B)-P(A\cap B)}{1-P(A)}=\frac{0.25}{0.7}=\boxed{\tfrac5{14}\approx0.357}$$

## Exercise 19: Three independent code-breakers
The message stays hidden only if **all three** fail. By independence,

$$P(\text{all fail})=\tfrac45\cdot\tfrac34\cdot\tfrac23=\tfrac25.$$

$$P(\text{deciphered})=1-\tfrac25=\boxed{0.6}$$

**Complement trick**: "at least one" is $1-P(\text{none})$.

## Exercise 22: Advertising and purchases
Let M be "sees the magazine advert" and T be "sees the TV advert".

$$P(\text{seen})=P(\mathrm M\cup\mathrm T)=\tfrac1{50}+\tfrac15-\tfrac1{100}=0.02+0.20-0.01=0.21$$

By the **law of total probability**:

$$P(\text{buy})=P(\text{buy}\mid\text{seen})P(\text{seen})+P(\text{buy}\mid\text{not seen})P(\text{not seen})=\tfrac13(0.21)+\tfrac1{10}(0.79)=0.07+0.079=\boxed{0.149}$$

## Booklet Exercise A: Choosing 4 objects from 6

$$\binom64=\frac{6!}{4!\,2!}=\frac{6\times5}{2}=\boxed{15}$$

## Exercise 28: $f_X(x)=c/\sqrt x$ on $(0,4)$
**(a)** The total probability must be 1:

$$\int_0^4cx^{-1/2}\,\mathrm dx=c\big[2\sqrt x\big]_0^4=4c=1\ \Rightarrow\ \boxed{c=\tfrac14}$$

The density is unbounded at 0, but the integral is still finite (an improper integral, [[MATH1054 M10 - Integration III|M10]]).

**(b)**

$$F_X(x)=\begin{cases}0&x\le0\\ \int_0^x\tfrac14t^{-1/2}\,\mathrm dt=\tfrac12\sqrt x&0<x<4\\1&x\ge4\end{cases}$$

**(c)** $P(X>1)=1-F_X(1)=1-\tfrac12=\boxed{\tfrac12}$

## Exercise 33: Daily computer malfunctions
| $x$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| $p$ | 0.17 | 0.29 | 0.27 | 0.16 | 0.07 | 0.03 | 0.01 |
| $F$ | 0.17 | 0.46 | 0.73 | 0.89 | 0.96 | 0.99 | 1.00 |

- **Mean**: $\sum xp=0+0.29+0.54+0.48+0.28+0.15+0.06=\boxed{1.80}$
- **Median**: $F(1)=0.46<0.5\le F(2)=0.73$, so the median is $\boxed2$.
- **Standard deviation**: $E[X^2]=0.29+1.08+1.44+1.12+0.75+0.36=5.04$, so $\operatorname{Var}=5.04-3.24=1.80$ and $\sigma=\boxed{1.342}$.

## Exercise 38: Tyre distance, exponential with mean 30 (thousand km)
**(a)**

$$P(X\le19)=1-e^{-19/30}=\boxed{0.469}$$

**(b) Mean only**:

$$E[X]=\int_0^\infty\frac{x}{30}e^{-x/30}\,\mathrm dx=\boxed{30}\ \text{thousand km}$$

This uses the standard exponential result: the mean equals the scale parameter.

**(c)** For an exponential with mean $\mu$, the $p$-quantile is $-\mu\ln(1-p)$:
- **Median**: $30\ln2=\boxed{20.79}$ thousand km
- **Quartiles**: $Q_1=-30\ln0.75=8.63$ and $Q_3=-30\ln0.25=41.59$
- **IQR** $=30\ln3=\boxed{32.96}$ thousand km

---

# Part C: Specimen Test 24

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 24), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Events
(i) $E_1\cup E_3=\{\text{copper, sodium, zinc, oxygen, uranium}\}$
(ii) $E_1\cap E_2=\{\text{sodium}\}$
(iii) $(E_1\cap E_3)\cup E_2=\{\text{zinc}\}\cup E_2=\{\text{zinc, sodium, nitrogen, potassium}\}$
(iv) $\bar E_2=\{\text{copper, oxygen, uranium, zinc}\}$

## Q2

$$P(A\cap B)=P(A)+P(B)-P(A\cup B)=0.5+0.3-0.7=\boxed{0.1}$$

## Q3: Two bags (Bayes' theorem)
Bag 1 is WWWW and bag 2 is WWBB. The remaining balls are all white **iff** bag 1 was chosen.

$$P(\text{bag 1}\mid W)=\frac{P(W\mid1)P(1)}{P(W\mid1)P(1)+P(W\mid2)P(2)}=\frac{1\cdot\frac12}{1\cdot\frac12+\frac12\cdot\frac12}=\boxed{\tfrac23}$$

## Q4

$$\binom94=\frac{9\cdot8\cdot7\cdot6}{24}=\boxed{126}$$

## Q5: $f_X=ce^{-x}$ for $x>0$
**(i)** $\int_0^\infty ce^{-x}\,\mathrm dx=c=1$, so $\boxed{c=1}$.
**(ii)** $F_X(x)=0$ for $x\le0$, and $\boxed{1-e^{-x}}$ for $x>0$.
**(iii)** $P(X>1)=e^{-1}=\boxed{0.368}$.

## Q6: $P(1),\dots,P(5)=\frac15,\frac1{10},\frac25,\frac1{10},\frac15$
**(i)**

$$\mu=\tfrac15+\tfrac2{10}+\tfrac65+\tfrac4{10}+1=\boxed3$$

The distribution is symmetric about 3.

**(ii)** The mode is $\boxed3$, the value with the largest probability ($\frac25$).

## Q7: A density on $[0,1]$

$$\boxed{\mu=\int_0^1xf_X(x)\,\mathrm dx},\qquad\boxed{\sigma^2=\int_0^1(x-\mu)^2f_X(x)\,\mathrm dx=\int_0^1x^2f_X(x)\,\mathrm dx-\mu^2}$$

## Sources
- Transcribed problem statements: `tmp/md/module_24_statistics_i.md`
- James, *Modern Engineering Mathematics* (6th ed.) §13.2–13.4; MATH1054 Module Booklet, Module 24

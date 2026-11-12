---
title: "Arithmetic and Geometric Series"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Arithmetic progression", "Geometric progression", "AP", "GP", "Sum to infinity"]
tags: [math1054, concept, series]
status: complete
parent_lectures: ["[[MATH1054 M20 - Further Calculus II]]"]
related_concepts: ["[[Convergence Tests for Series]]", "[[Taylor and Maclaurin Series]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §7.2–7.3", "MATH1054 Module Booklet, Module 20"]
---

# Arithmetic and Geometric Series

An arithmetic sequence adds a fixed difference $d$ at each step, $a_n=a+(n-1)d$, and a geometric sequence multiplies by a fixed ratio $r$, $a_n=ar^{n-1}$; their sums to $n$ terms are the arithmetic and geometric series.

Writing the arithmetic series forwards and backwards and adding pairs each term with its mirror image, and every pair sums to $2a+(n-1)d$. With $n$ pairs making $2S_n$,

$$
S_n=\frac n2\big[2a+(n-1)d\big]=\frac n2(\text{first}+\text{last}).
$$

For the geometric series, multiplying by $r$ shifts every term one place, so subtracting leaves only the two ends:

$$
\begin{aligned}
S_n-rS_n&=a-ar^n,\\
S_n&=\frac{a(1-r^n)}{1-r}\qquad(r\neq1).
\end{aligned}
$$

If $|r|<1$ then $r^n\to0$ and the infinite series converges to the **sum to infinity** $S_\infty=\dfrac{a}{1-r}$; for $|r|\geq1$ it diverges. Exercise 41(a) is $2+\frac23+\frac29+\cdots=\frac{2}{1-1/3}=3$.

Savings, loans and insurance lead to geometric sums. Compound interest multiplies a balance by $(1+i)$ each period, so regular deposits $P$ give the recurrence $x_{n}=(1+i)x_{n-1}+P$, a sequence defined step by step from the previous term. Unrolling it turns the balance into a geometric series: in Example 7.1 ($i=0.085$, $P=1000$, $x_0=1000$),

$$
x_n=1000\big(1+1.085+\cdots+1.085^n\big)=1000\,\frac{1.085^{n+1}-1}{0.085},
$$

which gives $x_3=£4539.51$, the same as iterating the recurrence. Example 7.9 is the same idea for an insurance policy: premiums of £250 at the start of each of 25 years, growing at 3%, are worth

$$
250\big(1.03+1.03^2+\cdots+1.03^{25}\big)=250\times1.03\times\frac{1.03^{25}-1}{0.03}=£9388.26 .
$$

A "how many terms?" question gives a quadratic in $n$ for an arithmetic series and a logarithm for a geometric one. For $11+15+19+\cdots=341$ (Example 7.7), $a=11$ and $d=4$:

$$
\begin{aligned}
\tfrac n2\big[22+4(n-1)\big]&=341,\\
2n^2+9n-341&=0,\\
n&=\frac{-9\pm53}{4}=11\ \text{or}\ -\tfrac{31}{2},
\end{aligned}
$$

so $n=11$ terms (check: last term 51, $\frac{11}{2}(11+51)=341$). For the geometric series $1+2+4+\cdots$ to pass 1000, $2^n-1>1000$, so $n>\log_21001=9.97$ and 10 terms are needed ($2^{10}-1=1023$, while 9 terms give only 511).

The common trap is using $\frac{a}{1-r}$ without checking $|r|<1$: for $1-2+4-8+\cdots$ it gives $\frac13$, but the partial sums $1,-1,3,-5,11,\dots$ never settle. Another is miscounting $n$: the $n$th term carries $r^{n-1}$ or $(n-1)d$, so a 25-year scheme has 25 terms, not 24 or 26.

## Related

- Topics: [[MATH1054 M20 - Further Calculus II#2. Arithmetic sequences and series (James §7.3.1)|M20 §2]] · [[MATH1054 M20 - Further Calculus II#3. Geometric sequences and series (James §7.3.2)|M20 §3]] · [[MATH1054 M20 - Further Calculus II#The sum to infinity of a geometric series|sum to infinity]] · [[MATH1054 M20 Solutions - Further Calculus II]]
- Concepts: [[Convergence Tests for Series]] · [[Taylor and Maclaurin Series]]
- Sources: James, Modern Engineering Mathematics (6th ed.) §7.2–7.3 and §7.6.1; MATH1054 Module Booklet, Module 20.

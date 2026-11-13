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
status: lectured
coverage: "Module Booklet Module 24 work scheme (Examples A–D, Exercise A, Specimen Test 24); James §13.3.1–13.3.5 (probability, conditional probability, independence) and §13.4.1–13.4.7 (discrete and continuous random variables, mean, median, mode, variance, quartiles, expected values)"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M09 - Integration II]]", "[[MATH1054 M10 - Integration III]]"]
next_topics: ["[[MATH1054 M25 - Statistics II]]"]
key_concepts: ["[[Probability Rules and Conditional Probability]]", "[[Random Variables, PDF and CDF]]", "[[Mean, Median and Variance of a Distribution]]"]
tutorial_sheets: ["[[MATH1054 M24 Solutions - Statistics I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 24)", "02 - Sources/Modern Engineering Mathematics.pdf (§13.2–13.4)"]
---

# MATH1054 M24 - Statistics I

> [!abstract] Summary
> Probability assigns a number between 0 and 1 to each event in a sample space, and three axioms fix how those numbers combine: the complement rule, the general addition rule $P(A\cup B)=P(A)+P(B)-P(A\cap B)$, conditional probability $P(B\mid A)=P(A\cap B)/P(A)$, the law of total probability and Bayes' theorem all follow from them. A random variable is described by a probability function $p_X$ if it is discrete, or a density $f_X$ if it is continuous, and in both cases by the distribution function $F_X(x)=P(X\le x)$. Its centre is summarised by the mean, median and mode, and its spread by the variance $\sigma^2=E[X^2]-\mu^2$, the standard deviation and the interquartile range; for a continuous variable every one of these is an integral or an equation in $F_X$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives probabilities of some events and asks for others, or gives a probability table or density and asks for a constant, $F_X$, a probability, the mean, median, mode, variance or quartiles.
> - **Assumptions:** events in the addition axiom are mutually exclusive; the product rule $P(A\cap B)=P(A)P(B)$ needs independence; a density is non-negative and integrates to 1 over its whole range.
> - **Method:** 1. Name the events (or define $X$) and write the sample space. 2. Pick the rule: "or" is the addition rule, "and" the multiplication rule, "given" a conditional probability, several routes to one event total probability, the reverse question Bayes. 3. For a random variable, fix any constant from $\sum p_X=1$ or $\int f_X\,\mathrm dx=1$. 4. Build $F_X$ by summing or integrating from the left; then $P(a<X\le b)=F_X(b)-F_X(a)$. 5. Mean, then $E[X^2]$, then $\operatorname{Var}X=E[X^2]-\mu^2$; quantiles from $F_X(q)=p$.
> - **Common mistakes:** adding the probabilities of events that overlap, or multiplying the probabilities of events that are not independent; reading $f_X(x)$ as the probability that $X=x$, which for a continuous variable is zero.
> - **Practise:** [[#5. Total probability and Bayes' theorem]] · [[MATH1054 M24 Solutions - Statistics I#Exercise 22: Advertising and purchases|Exercise 22]]

Measurements scatter: a batch of fuses has a few faulty ones, component lifetimes vary from unit to unit, and a sensor reading carries noise. Probability is the arithmetic of that scatter: it gives the chance of an event as an idealised long-run proportion, and a small set of rules fixes how the chances of combined events (one or the other, both, one given the other) follow from the chances of their parts. The rules are the same whether the probabilities come from counting equally likely outcomes, from measured frequencies or from a model.

A random variable attaches a number to each outcome, the number of ships arriving in a day or the lifetime of a component in thousands of hours. A discrete variable takes a list of values with a probability on each; a continuous one takes any value in an interval, and probability is then spread along the axis with a density, so that probabilities become areas under a curve and the integration methods of [[MATH1054 M09 - Integration II|M09]] and [[MATH1054 M10 - Integration III|M10]] (integration by parts, improper integrals) do the work. The mean of a distribution is its centre of gravity and the variance its moment of inertia about that centre, the same integrals as in [[Centroids and Solids of Revolution]] with probability in place of mass.

The binomial and normal distributions are particular probability functions and densities, and confidence intervals and hypothesis tests use the mean and standard deviation defined here ([[MATH1054 M25 - Statistics II|M25]]).

---

## 1. Sample spaces, events and set operations

An **experiment** is any process whose result depends on chance, such as throwing a die or drawing 10 fuses at random from a box of 100. One performance gives one **outcome**. The **sample space** $S$ is the set of all possible outcomes, and an **event** is any subset of $S$. An event occurs if the actual outcome lies in it.

For a die, $S=\{1,2,3,4,5,6\}$ and the event "even" is $E=\{2,4,6\}$; if a 5 is thrown, $5\notin E$ and $E$ has not occurred (James Example 13.1). For two tosses of a coin, $S=\{\mathrm{HH},\mathrm{HT},\mathrm{TH},\mathrm{TT}\}$ and "both tosses give the same result" is $\{\mathrm{HH},\mathrm{TT}\}$; the outcome TT lies in it, so that event has occurred (Example 13.2). A sample space is discrete if its outcomes can be listed, possibly without end, and continuous when the experiment measures a continuous quantity such as a voltage, in which case $S$ is an interval like $(0,10)$.

Events combine by the set operations:

- the **union** $A\cup B$, "$A$ or $B$ occurs" (or both);
- the **intersection** $A\cap B$, "$A$ and $B$ both occur";
- the **complement** $\bar A=S-A$, "$A$ does not occur".

Two events with no outcome in common, $A\cap B=\emptyset$, are **mutually exclusive** (James calls them disjoint). The certain event is $S$ and the impossible event is $\emptyset$. De Morgan's laws turn the complement of a union into an intersection of complements and the other way round:

$$
\overline{A\cup B}=\bar A\cap\bar B,\qquad\overline{A\cap B}=\bar A\cup\bar B .
$$

![[m1054_m24_venn_events.png|900]]

In a Venn diagram the rectangle is $S$ and each closed curve an event; the shaded regions above are the four combinations used most often. The last one, $A\cap\bar B$ ("$A$ but not $B$"), is $A$ with the overlap removed.

### Listing the outcomes of combined events

Specimen Test 24, Q1 takes $S=\{\text{copper, sodium, nitrogen, potassium, oxygen, uranium, zinc}\}$ with $E_1=\{\text{copper, sodium, zinc}\}$, $E_2=\{\text{sodium, nitrogen, potassium}\}$ and $E_3=\{\text{oxygen, uranium, zinc}\}$. Work from the innermost bracket outwards:

$$
\begin{aligned}
E_1\cup E_3&=\{\text{copper, sodium, zinc, oxygen, uranium}\},\\
E_1\cap E_2&=\{\text{sodium}\},\\
(E_1\cap E_3)\cup E_2&=\{\text{zinc}\}\cup E_2=\{\text{zinc, sodium, nitrogen, potassium}\},\\
\bar E_2&=\{\text{copper, oxygen, uranium, zinc}\}.
\end{aligned}
$$

James Exercise 7 is the same drill with $S=\{\text{car, bus, train, bicycle, motorcycle, boat, aeroplane}\}$, $A=\{\text{bus, train, aeroplane}\}$, $B=\{\text{train, car, boat}\}$ and $C=\{\text{bicycle}\}$:

$$
\begin{aligned}
\bar A&=\{\text{car, bicycle, motorcycle, boat}\},\\
A\cap B\cap\bar C&=\{\text{train}\}\cap\bar C=\{\text{train}\},\\
(\bar A\cup B)\cap(\bar A\cap C)&=\{\text{car, bicycle, motorcycle, boat, train}\}\cap\{\text{bicycle}\}=\{\text{bicycle}\}.
\end{aligned}
$$

## 2. The axioms and the rules derived from them

The probability of an outcome is the proportion of times it is expected to occur in a long run of repetitions, the **frequency interpretation**. If the experiment is repeated $N$ times under the same conditions and outcome $e_1$ occurs $n_1$ times, $n_1/N$ is its relative frequency, and

$$
p_1=\lim_{N\to\infty}\frac{n_1}{N}.
$$

Proportions obey three rules, and these are taken as the **axioms of probability**. For every event $A\subseteq S$:

1. $P(S)=1$;
2. $P(A)\ge0$;
3. if $A\cap B=\emptyset$, then $P(A\cup B)=P(A)+P(B)$.

When the $n$ outcomes of $S$ are equally likely, axioms 1 and 3 give each one probability $1/n$, so an event with $|E|$ outcomes has

$$
P(E)=\frac{|E|}{|S|}.
$$

For a die, $P(\text{even})=\frac36=\frac12$; for two coins, $P(\text{same})=\frac24=\frac12$.

Every other rule follows from the axioms, and rules 4 to 7 below complete the seven numbered results to know.

**Rule 4, complement.** $A$ and $\bar A$ are mutually exclusive and together make up $S$, so axioms 1 and 3 give

$$
\begin{aligned}
P(A\cup\bar A)&=P(S)=1,\\
P(A)+P(\bar A)&=1,\\
P(\bar A)&=1-P(A).
\end{aligned}
$$

**Rule 5.** $\emptyset=\bar S$, so $P(\emptyset)=1-P(S)=0$.

**Rule 6.** If $A\subseteq B$, split $B$ into the exclusive pieces $A$ and $B\cap\bar A$:

$$
P(B)=P(A)+P(B\cap\bar A)\ge P(A),
$$

because $P(B\cap\bar A)\ge0$ by axiom 2.

**Rule 7, the general addition rule.** Split $A\cup B$ into the exclusive pieces $A$ and $B\cap\bar A$ (the part of $B$ outside $A$):

$$
P(A\cup B)=P(A)+P(B\cap\bar A).
$$

Split $B$ itself into the exclusive pieces $A\cap B$ and $\bar A\cap B$:

$$
P(B)=P(A\cap B)+P(B\cap\bar A),\qquad\text{so}\qquad P(B\cap\bar A)=P(B)-P(A\cap B).
$$

Substitute:

$$
P(A\cup B)=P(A)+P(B)-P(A\cap B).
$$

Adding $P(A)$ and $P(B)$ counts the overlap twice, so it is subtracted once. For exclusive events $P(A\cap B)=0$ and rule 7 reduces to axiom 3. The middle step is a useful result in its own right: by symmetry $P(A\cap\bar B)=P(A)-P(A\cap B)$, the probability of "$A$ but not $B$".

### Examples using the rules

James Example 13.3 asks for "an even number or a number less than four" on one throw of a fair die. The two events overlap in $\{2\}$:

$$
\begin{aligned}
P(\{2,4,6\}\cup\{1,2,3\})&=P(\{2,4,6\})+P(\{1,2,3\})-P(\{2\})\\
&=\tfrac12+\tfrac12-\tfrac16=\tfrac56 .
\end{aligned}
$$

The complement gives the same answer at once, since the event is "not 5": $1-\frac16=\frac56$. With exclusive outcomes, axiom 3 alone gives $P(\{2,4,6\})=\frac16+\frac16+\frac16=\frac12$, and in the same way $P(\{1,3,5\})=\frac12$.

In James Example 13.4, 80% of a class pass mathematics ($M$), 85% pass laboratory work ($L$) and 75% pass both. For a student chosen at random,

$$
\begin{aligned}
P(M\cup L)&=0.8+0.85-0.75=0.9,\\
P(M\cap\bar L)&=P(M)-P(M\cap L)=0.8-0.75=0.05,\\
P(\bar M\cap\bar L)&=1-P(M\cup L)=1-0.9=0.1 .
\end{aligned}
$$

The last line is De Morgan's law, but the Venn diagram of $A\cup B$ shows it directly: failing both is everything outside the union.

James Exercise 8 has mutually exclusive $A$ and $B$ with $P(A)=0.2$ and $P(B)=0.5$. Then $P(A\cup B)=0.2+0.5=0.7$ and $P(\bar A)=1-0.2=0.8$. Because $B$ lies entirely outside $A$, $\bar A\cap B=B$, so $P(\bar A\cap B)=P(B)-P(A\cap B)=0.5-0=0.5$.

Specimen Test 24, Q2 runs the addition rule backwards: with $P(A)=0.5$, $P(B)=0.3$ and $P(A\cup B)=0.7$,

$$
P(A\cap B)=P(A)+P(B)-P(A\cup B)=0.5+0.3-0.7=0.1 .
$$

> [!check] Exercise 11: a claim that breaks the addition rule
> Of 400 employees, 312 are said to have had a pay rise ($R$), 248 increased pension benefits ($B$), 173 both and 43 neither. By the addition rule $|R\cup B|=312+248-173=387$, so the claim accounts for $387+43=430$ people out of 400. Equivalently $P(R\cup B)=0.9675$ forces $P(\text{neither})=0.0325$, which is 13 people, not 43. The figures are inconsistent.

## 3. Conditional probability

Information often arrives in stages. Once event $A$ is known to have occurred, $A$ becomes the new sample space, and the chance of $B$ is the share of $A$ that also lies in $B$. In frequency terms, out of $N$ repetitions let $A$ occur $n_A$ times and $A\cap B$ occur $n_{AB}$ times. The proportion of the $A$-trials in which $B$ also occurs is

$$
\frac{n_{AB}}{n_A}=\frac{n_{AB}/N}{n_A/N}\ \longrightarrow\ \frac{P(A\cap B)}{P(A)}\quad(N\to\infty).
$$

That limit defines the **conditional probability** of $B$ given $A$:

$$
P(B\mid A)=\frac{P(A\cap B)}{P(A)},\qquad P(A)>0 .
$$

Multiplying through gives the **multiplication rule**, which is how the definition is usually used:

$$
P(A\cap B)=P(A)\,P(B\mid A)=P(B)\,P(A\mid B).
$$

A conditional probability satisfies the three axioms with $A$ as the sample space: $P(A\mid A)=1$, it is non-negative, and it adds over exclusive events. So the complement and addition rules hold for it too, for example $P(\bar B\mid A)=1-P(B\mid A)$.

James Example 13.5: a die is thrown and you are told only that the number is less than four. The sample space shrinks to $\{1,2,3\}$, which holds one even number:

$$
P(\text{even}\mid\text{less than four})=\frac{P(\{2\})}{P(\{1,2,3\})}=\frac{1/6}{1/2}=\frac13 .
$$

The information lowers the probability of "even" from $\frac12$ to $\frac13$.

James Example 13.6 has a flight that departs on time with $P(D)=0.83$, arrives on time with $P(A)=0.92$, and does both with $P(A\cap D)=0.78$. The chance it arrives on time given that it departed on time is

$$
P(A\mid D)=\frac{P(A\cap D)}{P(D)}=\frac{0.78}{0.83}=0.94 .
$$

The chance it did not depart on time given that it fails to arrive on time needs $P(\bar A\cap\bar D)$, which is the complement of the union:

$$
\begin{aligned}
P(\bar A\cap\bar D)&=1-P(A\cup D)\\
&=1-P(A)-P(D)+P(A\cap D)\\
&=1-0.92-0.83+0.78=0.03,
\end{aligned}
$$

so

$$
P(\bar D\mid\bar A)=\frac{P(\bar A\cap\bar D)}{P(\bar A)}=\frac{0.03}{0.08}=0.375 .
$$

James Exercise 18 gives $P(A)=0.3$, $P(B)=0.4$ and $P(B\mid A)=0.5$. The multiplication rule, the addition rule and the "$B$ but not $A$" result give, in turn,

$$
\begin{aligned}
P(A\cap B)&=P(A)P(B\mid A)=0.3\times0.5=0.15,\\
P(A\cup B)&=0.3+0.4-0.15=0.55,\\
P(B\mid\bar A)&=\frac{P(B\cap\bar A)}{P(\bar A)}=\frac{P(B)-P(A\cap B)}{1-P(A)}=\frac{0.25}{0.7}=\frac5{14}\approx0.357 .
\end{aligned}
$$

> [!warning] Order matters in a conditional probability
> $P(B\mid A)$ and $P(A\mid B)$ have the same numerator $P(A\cap B)$ but different denominators. In Example 13.6, $P(A\mid D)=0.78/0.83=0.94$ but $P(D\mid A)=0.78/0.92=0.85$. Bayes' theorem in Section 5 is the rule for turning one into the other.

### The weather chain (Example 13.7)

On an island every day is sunny ($S$) or rainy ($R$). A sunny day is followed by rain with probability $P(R\mid S)=0.6$, and a rainy day by rain with $P(R\mid R)=0.8$; each day depends only on the day before. By the complement rule for conditional probabilities, $P(S\mid S)=1-0.6=0.4$ and $P(S\mid R)=1-0.8=0.2$. Thursday is rainy; the question is the chance that Saturday is sunny.

Friday is either sunny or rainy, so "Saturday sunny" splits into two exclusive cases:

$$
\begin{aligned}
P(\text{Sat sunny})&=P(\text{Sat sunny and Fri sunny})+P(\text{Sat sunny and Fri rainy})\\
&=P(\text{Sat S}\mid\text{Fri S})P(\text{Fri S}\mid\text{Thu R})+P(\text{Sat S}\mid\text{Fri R})P(\text{Fri R}\mid\text{Thu R})\\
&=P(S\mid S)P(S\mid R)+P(S\mid R)P(R\mid R)\\
&=(0.4)(0.2)+(0.2)(0.8)=0.24 .
\end{aligned}
$$

The second line is the multiplication rule with every probability conditioned on Thursday being rainy; the "previous day only" assumption lets $P(\text{Sat S}\mid\text{Fri S and Thu R})$ be written as $P(S\mid S)$. This splitting over the possible states of Friday is the law of total probability of Section 5.

## 4. Independence

Knowing that $A$ has occurred can raise the probability of $B$, lower it or leave it unchanged. If $B_1\subseteq A$ then $P(B_1\mid A)=P(B_1)/P(A)>P(B_1)$ whenever $P(A)<1$; if $B_2$ and $A$ are exclusive then $P(B_2\mid A)=0<P(B_2)$. The case where it is unchanged is the important one. Events $A$ and $B$ are **independent** when

$$
P(B\mid A)=P(B).
$$

Substitute the definition of $P(B\mid A)$:

$$
\begin{aligned}
\frac{P(A\cap B)}{P(A)}&=P(B),\\
P(A\cap B)&=P(A)P(B).
\end{aligned}
$$

This product form is the usual test, and it is symmetric in $A$ and $B$, so independence also gives $P(A\mid B)=P(A)$. For any number of independent events the probabilities multiply,

$$
P(A_1\cap A_2\cap\dots\cap A_n)=P(A_1)P(A_2)\cdots P(A_n),
$$

the **product rule**. Complements of independent events are independent as well, which is what "at least one" calculations rely on:

$$
\begin{aligned}
P(\bar A\cap\bar B)&=1-P(A\cup B)\\
&=1-P(A)-P(B)+P(A)P(B)\\
&=\big(1-P(A)\big)\big(1-P(B)\big)=P(\bar A)P(\bar B).
\end{aligned}
$$

> [!warning] Independent is not the same as mutually exclusive
> Exclusive events cannot both occur, so $P(A\cap B)=0$ and knowing $A$ rules $B$ out completely: they are as dependent as events can be. Independent events with non-zero probabilities always overlap, since $P(A\cap B)=P(A)P(B)>0$. Exclusive events are added (axiom 3); independent events are multiplied (product rule). Adding where multiplication belongs is the classic gambler's error: the chance of a six in two throws of a die is not $\frac26$ but $1-(\frac56)^2=\frac{11}{36}$.

James Example 13.8 tests independence from two tables of joint probabilities for defects $A$ and $B$ on a production line. Both tables have $P(A)=0.10$ and $P(B)=0.20$, so independence requires $P(A\cap B)=0.10\times0.20=0.02$.

| (a) | $B$ | $\bar B$ | Total | | (b) | $B$ | $\bar B$ | Total |
|---|---|---|---|---|---|---|---|---|
| $A$ | 0.02 | 0.08 | 0.10 | | $A$ | 0.06 | 0.04 | 0.10 |
| $\bar A$ | 0.18 | 0.72 | 0.90 | | $\bar A$ | 0.14 | 0.76 | 0.90 |
| Total | 0.20 | 0.80 | 1.00 | | Total | 0.20 | 0.80 | 1.00 |

In table (a) every cell is the product of its row and column totals ($0.1\times0.8=0.08$, $0.9\times0.2=0.18$, $0.9\times0.8=0.72$), so the defects are independent. In table (b), $P(A\cap B)=0.06>0.02$: the defects occur together three times as often as independence would predict, which suggests a common cause.

James Example 13.9 draws one card from a 52-card pack, with $A$ an ace, $K$ a king and $C$ a club. Each suit has the same number of aces, so "ace" and "club" are independent, while "ace" and "king" are exclusive:

$$
\begin{aligned}
P(A\cap C)&=P(A)P(C)=\tfrac1{13}\cdot\tfrac14=\tfrac1{52},\\
P(A\cup C)&=\tfrac1{13}+\tfrac14-\tfrac1{52}=\tfrac4{13},\\
P(A\cap K)&=0,\\
P(A\cup K)&=\tfrac1{13}+\tfrac1{13}=\tfrac2{13}.
\end{aligned}
$$

"At least one" is almost always quickest through the complement, "none", which for independent trials is a product. Two fair dice give at least one six with probability (James Example 13.10)

$$
P(\text{at least one six})=1-P(\text{no six})=1-\left(\tfrac56\right)^2=\tfrac{11}{36}.
$$

In James Exercise 19, three people work independently on a code and succeed with probabilities $\frac15$, $\frac14$ and $\frac13$. The message stays hidden only if all three fail:

$$
\begin{aligned}
P(\text{all fail})&=\tfrac45\cdot\tfrac34\cdot\tfrac23=\tfrac25,\\
P(\text{deciphered})&=1-\tfrac25=0.6 .
\end{aligned}
$$

The birthday problem (James Example 13.11) uses the same pattern. With $n$ people and 365 equally likely birthdays, the $k$th person avoids the first $k-1$ birthdays with probability $(365-k+1)/365$, so

$$
P(\text{at least two share})=1-\frac{364}{365}\cdot\frac{363}{365}\cdots\frac{366-n}{365}.
$$

This is $0.476$ for $n=22$ and $0.507$ for $n=23$, so 23 people are enough for a better-than-even chance of a shared birthday.

## 5. Total probability and Bayes' theorem

A plant makes floppy disks on three machines (booklet Example A): machine $A$ makes 60% of them, $B$ 30% and $C$ 10%, and the fractions faulty are 1%, 2% and 5% respectively. Let $F$ be "the disk is faulty".

$A$, $B$ and $C$ are mutually exclusive and exhaustive, a **partition** of $S$, because every disk comes from exactly one machine. $F$ meets all three parts, so it splits into exclusive pieces:

$$
F=(F\cap A)\cup(F\cap B)\cup(F\cap C).
$$

Take probabilities, using axiom 3 for the exclusive pieces:

$$
P(F)=P(F\cap A)+P(F\cap B)+P(F\cap C).
$$

Replace each term with the multiplication rule, $P(F\cap A)=P(A)P(F\mid A)$:

$$
P(F)=P(A)P(F\mid A)+P(B)P(F\mid B)+P(C)P(F\mid C).
$$

This is the **law of total probability**. For any partition $A_1,\dots,A_n$ of $S$ it reads $P(F)=\sum_iP(A_i)P(F\mid A_i)$, and with the two-part partition $A,\bar A$ it is $P(F)=P(F\mid A)P(A)+P(F\mid\bar A)P(\bar A)$. For the disks,

$$
P(F)=(0.6)(0.01)+(0.3)(0.02)+(0.1)(0.05)=0.006+0.006+0.005=0.017 .
$$

The reverse question asks: a disk picked at random is faulty; what is the chance it came from machine $A$? Write $P(F\cap A)$ both ways round with the multiplication rule,

$$
P(F\cap A)=P(A)P(F\mid A)=P(F)P(A\mid F),
$$

and divide by $P(F)$:

$$
P(A\mid F)=\frac{P(A)P(F\mid A)}{P(F)}=\frac{(0.6)(0.01)}{0.017}=0.353 .
$$

With the total-probability sum in the denominator this is **Bayes' theorem**,

$$
P(A_j\mid F)=\frac{P(A_j)P(F\mid A_j)}{\sum_iP(A_i)P(F\mid A_i)}.
$$

![[m1054_m24_partition_tree.png|900]]

The tree is the same calculation drawn out: multiply along each path to get $P(A_i\cap F)$, add the paths that end in $F$ to get $P(F)$, and divide one path by that sum for Bayes. Machines $A$ and $B$ each contribute 0.006, so $P(B\mid F)=0.353$ as well, and $P(C\mid F)=0.005/0.017=0.294$. Machine $C$ makes only 10% of the disks but accounts for 29% of the faulty ones.

> [!tip] Bayes reverses the direction of the conditioning
> The data usually come as "fault rate given machine", $P(F\mid A_i)$, while the question asks "machine given fault", $P(A_i\mid F)$. Total probability gives the denominator, and the numerator is the one path of the tree that the question names.

James Exercise 22 is a two-part partition. One potential buyer in fifty sees a magazine advertisement ($M$), one in five sees the television one ($T$), and one in a hundred sees both. So

$$
P(\text{seen})=P(M\cup T)=\tfrac1{50}+\tfrac15-\tfrac1{100}=0.02+0.20-0.01=0.21 .
$$

One in three of those who have seen it buy, and one in ten of those who have not:

$$
\begin{aligned}
P(\text{buy})&=P(\text{buy}\mid\text{seen})P(\text{seen})+P(\text{buy}\mid\text{not seen})P(\text{not seen})\\
&=\tfrac13(0.21)+\tfrac1{10}(0.79)\\
&=0.07+0.079=0.149 .
\end{aligned}
$$

Bayes then gives the share of buyers who saw the advertisement, $P(\text{seen}\mid\text{buy})=0.07/0.149=0.470$.

Specimen Test 24, Q3 has one bag with four white balls and one with two white and two black. A bag is chosen at random and a white ball drawn; the remaining balls are all white exactly when the first bag was chosen. With $P(W\mid1)=1$ and $P(W\mid2)=\frac12$,

$$
P(\text{bag }1\mid W)=\frac{P(W\mid1)P(1)}{P(W\mid1)P(1)+P(W\mid2)P(2)}=\frac{1\cdot\frac12}{1\cdot\frac12+\frac12\cdot\frac12}=\frac23 .
$$

## 6. Counting with permutations and combinations

When outcomes are equally likely, $P(E)=|E|/|S|$, and the work is in counting. Both counts rest on the multiplication principle: if one choice can be made in $a$ ways and a second, for each of those, in $b$ ways, the pair can be made in $ab$ ways.

A **permutation** is an ordered arrangement. Arranging $n$ distinct objects in a row, the first place can be filled in $n$ ways, the second in $n-1$, and so on down to 1:

$$
n!=n(n-1)(n-2)\cdots3\cdot2\cdot1 .
$$

The letters a, b, c have $3!=6$ permutations: abc, acb, bac, bca, cab, cba (booklet Example B). Filling only $r$ places from $n$ objects stops after $r$ factors:

$$
{}^nP_r=n(n-1)\cdots(n-r+1)=\frac{n!}{(n-r)!}.
$$

A **combination** is a subset chosen without regard to order. Each subset of $r$ objects can be put in order in $r!$ ways, so every combination appears $r!$ times among the ordered selections:

$$
\binom nr=\frac{{}^nP_r}{r!}=\frac{n!}{r!\,(n-r)!},
$$

read "$n$ choose $r$". Cancel the larger factorial in the denominator first: choosing two letters from four gives $\binom42=\frac{4\cdot3}{2\cdot1}=6$ (booklet Example C), and $\binom83=\frac{8\cdot7\cdot6}{3!}=56$. Choosing 4 objects from 6 (Exercise A) and 4 from 9 (Specimen Test 24, Q4):

$$
\binom64=\frac{6!}{4!\,2!}=\frac{6\times5}{2}=15,\qquad\binom94=\frac{9\cdot8\cdot7\cdot6}{24}=126 .
$$

Booklet Example D draws two valves at random from a box of 12, of which four are faulty. The $\binom{12}2=66$ possible pairs are equally likely and $\binom42=6$ of them are both faulty, so

$$
P(\text{both faulty})=\frac{\binom42}{\binom{12}2}=\frac6{66}=\frac1{11}.
$$

For at least one faulty valve, count the $\binom82=28$ pairs drawn entirely from the eight good valves and take the complement:

$$
P(\text{at least one faulty})=1-\frac{\binom82}{\binom{12}2}=1-\frac{28}{66}=\frac{19}{33}.
$$

> [!check] The valves drawn one at a time
> The multiplication rule gives the same answers without counting. Both faulty: $\frac4{12}\cdot\frac3{11}=\frac1{11}$. Neither faulty: $\frac8{12}\cdot\frac7{11}=\frac{14}{33}$, so at least one faulty is $1-\frac{14}{33}=\frac{19}{33}$.

## 7. Discrete random variables

A **random variable** is a sample space of numerical values together with a probability over those values. It is written with a capital letter, $X$, and an observed value with the lower-case letter, $x$. A **discrete** random variable takes a list of values $v_1,v_2,\dots$ (finite or not), and is described by its **probability function**

$$
p_X(x)=P(X=x),\qquad p_X(x)\ge0,\qquad\sum_kp_X(v_k)=1,
$$

which is zero except at the listed values. Its **distribution function** (cumulative distribution function) is

$$
F_X(x)=P(X\le x)=\sum_{v_k\le x}p_X(v_k).
$$

$F_X$ is a step function: flat between the values, with a jump of $p_X(v_k)$ at each $v_k$, and the value at a jump includes that jump (it is right-continuous). The probability of an interval is a difference of $F_X$ values, because $\{X\le b\}$ is the exclusive union of $\{X\le a\}$ and $\{a<X\le b\}$:

$$
P(a<X\le b)=F_X(b)-F_X(a).
$$

James Example 13.12 counts the ships arriving at a container terminal in one day:

| $x$ | 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|
| $p_X(x)$ | 0.10 | 0.30 | 0.35 | 0.20 | 0.05 |
| $F_X(x)$ | 0.10 | 0.40 | 0.75 | 0.95 | 1.00 |

![[m1054_ships_pmf_cdf.png|900]]

So, for example, $P(1<X\le3)=F_X(3)-F_X(1)=0.95-0.40=0.55$, which is $p_X(2)+p_X(3)$.

James Exercise 33 gives the daily number of malfunctions of a computer; the same running sum builds $F_X$:

| $x$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| $p_X(x)$ | 0.17 | 0.29 | 0.27 | 0.16 | 0.07 | 0.03 | 0.01 |
| $F_X(x)$ | 0.17 | 0.46 | 0.73 | 0.89 | 0.96 | 0.99 | 1.00 |

## 8. Continuous random variables

A **continuous** random variable can take any value in an interval; outside that interval its probability is defined to be zero, so it lives on the whole real line. Its distribution function has the same definition, $F_X(x)=P(X\le x)$, but now there are no steps, $F_X$ is continuous, and where it is differentiable its derivative is the **probability density function**:

$$
f_X(x)=\frac{\mathrm d}{\mathrm dx}F_X(x),\qquad F_X(x)=\int_{-\infty}^{x}f_X(z)\,\mathrm dz .
$$

The dummy variable $z$ keeps the variable of integration separate from the upper limit $x$. Four properties follow from the definitions (James §13.4.4).

1. $F_X(x)\to0$ as $x\to-\infty$ and $F_X(x)\to1$ as $x\to+\infty$: $X$ cannot be less than $-\infty$ and is certain to be less than $+\infty$.
2. $F_X$ never decreases: if $x_1<x_2$, the event $X\le x_1$ is a subset of $X\le x_2$, so by rule 6, $F_X(x_1)\le F_X(x_2)$. Hence $f_X\ge0$.
3. For $x_1<x_2$, $P(x_1<X\le x_2)=F_X(x_2)-F_X(x_1)=\displaystyle\int_{x_1}^{x_2}f_X(z)\,\mathrm dz$: probability is area under the density.
4. $\displaystyle\int_{-\infty}^{\infty}f_X(x)\,\mathrm dx=1$: the total area is the probability that $X$ has some value.

Property 3 also shows that a single value has zero probability. For any $h>0$, $X=x$ is contained in $x-h<X\le x$, so

$$
0\le P(X=x)\le F_X(x)-F_X(x-h)\ \longrightarrow\ 0\quad(h\to0),
$$

because $F_X$ is continuous. In particular $P(X\le a)=P(X<a)$. For a small width $\delta x$ the area is close to a rectangle, $P(x<X\le x+\delta x)\approx f_X(x)\,\delta x$, so $f_X(x)$ is probability per unit length. It is not itself a probability; it can exceed 1, and it can even be unbounded, as in Exercise 28 below.

### Exponential lifetimes (Examples 13.13 and 13.14)

The lifetime $X$ of an electronic component, in thousands of hours, has density $f_X(x)=\frac12e^{-x/2}$ for $x\ge0$ and zero for $x<0$ (an exponential distribution with parameter $\frac12$). Integrating from the left,

$$
\begin{aligned}
F_X(x)&=\int_0^x\tfrac12e^{-z/2}\,\mathrm dz\\
&=\big[-e^{-z/2}\big]_0^x\\
&=1-e^{-x/2}\qquad(x\ge0),
\end{aligned}
$$

and $F_X(x)=0$ for $x<0$. The density starts at $\frac12$ and decays, while $F_X$ rises from 0 towards 1: most components fail early, but a few last much longer. The proportion lasting more than 6000 hours (Example 13.14) uses the complement:

$$
\begin{aligned}
P(X>6)&=1-F_X(6)\\
&=1-\big(1-e^{-6/2}\big)\\
&=e^{-3}=0.0498,
\end{aligned}
$$

about one component in twenty.

![[m1054_lifetime_pdf_cdf.png|900]]

Specimen Test 24, Q5 has $f_X(x)=ce^{-x}$ for $x>0$ and zero otherwise. Normalising,

$$
\int_0^\infty ce^{-x}\,\mathrm dx=c\big[-e^{-x}\big]_0^\infty=c=1,
$$

so $c=1$, $F_X(x)=1-e^{-x}$ for $x>0$ (and 0 for $x\le0$), and $P(X>1)=e^{-1}=0.368$.

### A density that is unbounded (Exercise 28)

James Exercise 28 takes $f_X(x)=c/\sqrt x$ for $0<x<4$ and zero elsewhere. The density is infinite at $x=0$, but the area under it is a convergent improper integral ([[Improper Integrals]]):

$$
\begin{aligned}
\int_0^4cx^{-1/2}\,\mathrm dx&=c\big[2\sqrt x\big]_0^4\\
&=4c=1,
\end{aligned}
$$

so $c=\frac14$. For $0<x<4$,

$$
F_X(x)=\int_0^x\tfrac14z^{-1/2}\,\mathrm dz=\tfrac14\big[2\sqrt z\big]_0^x=\tfrac12\sqrt x,
$$

with $F_X(x)=0$ for $x\le0$ and $F_X(x)=1$ for $x\ge4$. Then

$$
P(X>1)=1-F_X(1)=1-\tfrac12=\tfrac12 .
$$

## 9. Mean, median and mode

A distribution is often summarised by a measure of location (a typical value) and a measure of dispersion (the spread about it).

The **mean**, or expected value, weights each value by its probability. If $X$ is observed $N$ times and the value $v_k$ turns up $n_k$ times, the average of the observations is

$$
\frac1N\sum_kv_kn_k=\sum_kv_k\frac{n_k}{N}\ \longrightarrow\ \sum_kv_kP(X=v_k)\quad(N\to\infty).
$$

The limit defines the mean, and replacing the sum with an integral gives the continuous version:

$$
\mu_X=E[X]=\begin{cases}\displaystyle\sum_kv_k\,p_X(v_k),&X\text{ discrete},\\[2ex]\displaystyle\int_{-\infty}^{\infty}x\,f_X(x)\,\mathrm dx,&X\text{ continuous}.\end{cases}
$$

The mean is the centre of gravity of the distribution, the balance point of the bar chart or of the area under the density.

The **median** $m_X$ splits the probability in half. For a continuous variable it solves

$$
F_X(m_X)=\tfrac12 .
$$

For a discrete variable that equation usually has no solution, and the median is any value with $P(X\le m_X)\ge\frac12$ and $P(X\ge m_X)\ge\frac12$; in practice it is the first value at which $F_X$ reaches $\frac12$, unless $F_X$ equals $\frac12$ exactly on a flat stretch, in which case every point from there up to the next value qualifies. Mean and median coincide when the distribution has an axis of symmetry, and both then lie on it.

The **mode** is the value at which $p_X$ or $f_X$ is largest, the single most likely value. The three measures can differ and can come in any order.

James Example 13.16 finds all three for the die, the ships and the lifetimes.

For a fair die every face has probability $\frac16$:

$$
\mu_X=\sum_{k=1}^6k\cdot\tfrac16=\frac{1+2+3+4+5+6}6=3.5 .
$$

$F_X(3)=\frac12$ exactly and $F_X$ stays at $\frac12$ until 4, so any point of $[3,4]$ is a median; 3.5 is the conventional choice. All six values are equally likely, so each one is a mode and no single value stands out.

For the ships, from the table in Section 7,

$$
\mu_X=(0)(0.1)+(1)(0.3)+(2)(0.35)+(3)(0.2)+(4)(0.05)=1.8 .
$$

$F_X(1)=0.40<\frac12\le F_X(2)=0.75$, so the median is 2: $P(X\le2)=0.75$ and $P(X\ge2)=0.6$ both exceed one half. The mode is also 2, the value with the largest probability (0.35).

For the lifetimes, integrate by parts with $u=x$ and $\mathrm dv=\frac12e^{-x/2}\,\mathrm dx$, so $v=-e^{-x/2}$ ([[Integration by Parts]]):

$$
\begin{aligned}
\mu_X&=\int_0^\infty x\cdot\tfrac12e^{-x/2}\,\mathrm dx\\
&=\big[-xe^{-x/2}\big]_0^\infty+\int_0^\infty e^{-x/2}\,\mathrm dx\\
&=0+\big[-2e^{-x/2}\big]_0^\infty=2 .
\end{aligned}
$$

The boundary term vanishes because $xe^{-x/2}\to0$ as $x\to\infty$. The median solves $F_X(m)=\frac12$:

$$
\begin{aligned}
1-e^{-m/2}&=\tfrac12,\\
e^{-m/2}&=\tfrac12,\\
m&=2\ln2=1.386 .
\end{aligned}
$$

The mode is 0, where the density has its peak. So mode $<$ median $<$ mean, the usual order for a distribution with a long right tail: the few long-lived components pull the mean up but barely move the median.

Specimen Test 24, Q6 gives values 1 to 5 with probabilities $\frac15,\frac1{10},\frac25,\frac1{10},\frac15$:

$$
\mu=\tfrac15+\tfrac2{10}+\tfrac65+\tfrac4{10}+1=3,
$$

as the symmetry about 3 requires, and the mode is 3, the value with the largest probability $\frac25$.

For the malfunctions of Exercise 33,

$$
\mu=0+0.29+0.54+0.48+0.28+0.15+0.06=1.80,
$$

and $F_X(1)=0.46<0.5\le F_X(2)=0.73$, so the median is 2.

## 10. Variance, standard deviation and quartiles

The **variance** is the probability-weighted mean of the squared distance from the mean,

$$
\sigma_X^2=\operatorname{Var}X=\begin{cases}\displaystyle\sum_k(v_k-\mu_X)^2\,p_X(v_k),&X\text{ discrete},\\[2ex]\displaystyle\int_{-\infty}^{\infty}(x-\mu_X)^2f_X(x)\,\mathrm dx,&X\text{ continuous},\end{cases}
$$

the analogue of a moment of inertia about the centre of gravity. Squaring changes the units (volts become volts squared), so the **standard deviation** $\sigma_X=\sqrt{\operatorname{Var}X}$ is quoted alongside it, in the units of $X$.

Both are special cases of an **expected value**. For any function $h$,

$$
E[h(X)]=\sum_kh(v_k)\,p_X(v_k)\quad\text{or}\quad\int_{-\infty}^{\infty}h(x)\,f_X(x)\,\mathrm dx,
$$

with $h(X)=X$ giving the mean and $h(X)=(X-\mu_X)^2$ the variance. Expanding the square gives a shorter route to the variance. For continuous $X$,

$$
\begin{aligned}
\sigma_X^2&=\int_{-\infty}^{\infty}(x^2-2\mu_Xx+\mu_X^2)f_X(x)\,\mathrm dx\\
&=\int_{-\infty}^{\infty}x^2f_X\,\mathrm dx-2\mu_X\int_{-\infty}^{\infty}xf_X\,\mathrm dx+\mu_X^2\int_{-\infty}^{\infty}f_X\,\mathrm dx\\
&=E[X^2]-2\mu_X\cdot\mu_X+\mu_X^2\cdot1\\
&=E[X^2]-\mu_X^2 .
\end{aligned}
$$

The discrete proof is the same with sums. The variance is the mean of the square minus the square of the mean.

### Variances of the die, the ships and the lifetimes (Example 13.17)

For the die, $E[X^2]=\frac{1+4+9+16+25+36}6=\frac{91}6$, so

$$
\sigma_X^2=\frac{91}6-3.5^2=\frac{35}{12}=2.917,\qquad\sigma_X=1.708 .
$$

For the ships, with $\mu_X=1.8$, the definition gives

$$
\begin{aligned}
\sigma_X^2&=(0-1.8)^2(0.1)+(1-1.8)^2(0.3)+(2-1.8)^2(0.35)+(3-1.8)^2(0.2)+(4-1.8)^2(0.05)\\
&=0.324+0.192+0.014+0.288+0.242=1.060,
\end{aligned}
$$

so $\sigma_X=1.030$. The shortcut agrees: $E[X^2]=0+0.3+1.4+1.8+0.8=4.30$ and $4.30-1.8^2=1.06$.

For the lifetimes, with $\mu_X=2$, integrate by parts twice, each time differentiating the polynomial and integrating the exponential:

$$
\begin{aligned}
\sigma_X^2&=\int_0^\infty(x-2)^2\tfrac12e^{-x/2}\,\mathrm dx\\
&=\big[-(x-2)^2e^{-x/2}\big]_0^\infty+\int_0^\infty2(x-2)e^{-x/2}\,\mathrm dx\\
&=4+\big[-4(x-2)e^{-x/2}\big]_0^\infty+\int_0^\infty4e^{-x/2}\,\mathrm dx\\
&=4-8+8=4,
\end{aligned}
$$

so $\sigma_X=2$, equal to the mean. The first boundary term is $0-(-4)=4$; the second is $0-8=-8$; the last integral is $4\cdot2=8$. By the shortcut, $E[X^2]=\int_0^\infty x^2\cdot\frac12e^{-x/2}\,\mathrm dx=8$ and $8-2^2=4$.

For the malfunctions of Exercise 33,

$$
E[X^2]=0+0.29+1.08+1.44+1.12+0.75+0.36=5.04,
$$

so $\operatorname{Var}X=5.04-1.8^2=1.80$ and $\sigma=1.342$. For Specimen Test 24, Q6, $\sigma^2=\sum(x-3)^2p=\frac45+\frac1{10}+0+\frac1{10}+\frac45=\frac95$.

Specimen Test 24, Q7 asks only for the expressions. For a density on $[0,1]$,

$$
\mu=\int_0^1xf_X(x)\,\mathrm dx,\qquad\sigma^2=\int_0^1(x-\mu)^2f_X(x)\,\mathrm dx=\int_0^1x^2f_X(x)\,\mathrm dx-\mu^2 .
$$

### Quartiles and the interquartile range

The distribution function gives a second measure of spread. The **quartiles** $Q_1$ and $Q_3$ of a continuous variable solve

$$
F_X(Q_1)=\tfrac14,\qquad F_X(Q_3)=\tfrac34,
$$

and the median is the middle quartile $Q_2$. The three points cut the range of $X$ into four intervals of probability $\frac14$ each. The **interquartile range** is $Q_3-Q_1$; the semi-interquartile range $\frac12(Q_3-Q_1)$ is sometimes quoted instead. Splitting into 100 equal-probability intervals gives the percentiles, and the 10th and 90th percentiles are the deciles $d_1$ and $d_9$, with interdecile range $d_9-d_1$.

For the lifetimes, $1-e^{-q/2}=p$ gives $q=-2\ln(1-p)$, so

$$
\begin{aligned}
Q_1&=-2\ln\tfrac34=0.575,\\
Q_3&=-2\ln\tfrac14=2.773,\\
Q_3-Q_1&=2\ln\tfrac{3/4}{1/4}=2\ln3=2.197\ \text{thousand hours}.
\end{aligned}
$$

> [!check] 2.197, not 2.198
> Subtracting the rounded quartiles gives $2.773-0.575=2.198$, the value printed in James. The exact interquartile range is $2\ln3=2.1972$, which rounds to 2.197.

For the density of Exercise 28, $F_X(q)=\frac12\sqrt q=p$ gives $q=4p^2$, so $Q_1=\frac14$, median $1$ and $Q_3=\frac94$, with interquartile range 2. Its mean and variance follow from the same powers of $x$:

$$
\begin{aligned}
\mu&=\int_0^4x\cdot\tfrac14x^{-1/2}\,\mathrm dx=\tfrac14\cdot\tfrac23\big[x^{3/2}\big]_0^4=\tfrac43,\\
E[X^2]&=\int_0^4x^2\cdot\tfrac14x^{-1/2}\,\mathrm dx=\tfrac14\cdot\tfrac25\big[x^{5/2}\big]_0^4=\tfrac{16}5,\\
\sigma^2&=\tfrac{16}5-\tfrac{16}9=\tfrac{64}{45},\qquad\sigma=1.193 .
\end{aligned}
$$

![[m1054_m24_quartiles_ex28.png|900]]

The left panel shows the four strips of equal area: they are narrow where the density is high and wide where it is low. The right panel reads the same quartiles off $F_X$ by drawing across at $\frac14$, $\frac12$ and $\frac34$. The mean $\frac43$ lies to the right of the median 1, again because of the long right side of the density.

## 11. The exponential distribution

The lifetime example is one member of a family that models lifetimes and waiting times. With rate parameter $\lambda>0$,

$$
f_X(x)=\lambda e^{-\lambda x}\quad(x\ge0),\qquad f_X(x)=0\quad(x<0).
$$

Normalisation and the distribution function:

$$
\int_0^\infty\lambda e^{-\lambda x}\,\mathrm dx=\big[-e^{-\lambda x}\big]_0^\infty=1,\qquad F_X(x)=\int_0^x\lambda e^{-\lambda z}\,\mathrm dz=1-e^{-\lambda x}.
$$

The mean, by parts with $u=x$ and $v=-e^{-\lambda x}$:

$$
\begin{aligned}
\mu&=\int_0^\infty x\lambda e^{-\lambda x}\,\mathrm dx\\
&=\big[-xe^{-\lambda x}\big]_0^\infty+\int_0^\infty e^{-\lambda x}\,\mathrm dx\\
&=0+\frac1\lambda .
\end{aligned}
$$

The mean square, by parts with $u=x^2$, then using the mean:

$$
\begin{aligned}
E[X^2]&=\big[-x^2e^{-\lambda x}\big]_0^\infty+\int_0^\infty2xe^{-\lambda x}\,\mathrm dx\\
&=0+\frac2\lambda\int_0^\infty x\lambda e^{-\lambda x}\,\mathrm dx\\
&=\frac2\lambda\cdot\frac1\lambda=\frac2{\lambda^2}.
\end{aligned}
$$

Hence

$$
\sigma^2=\frac2{\lambda^2}-\frac1{\lambda^2}=\frac1{\lambda^2},\qquad\sigma=\frac1\lambda=\mu .
$$

The $p$-quantile solves $1-e^{-\lambda q}=p$:

$$
\begin{aligned}
e^{-\lambda q}&=1-p,\\
q&=-\frac{\ln(1-p)}\lambda=-\mu\ln(1-p).
\end{aligned}
$$

So the median is $\frac{\ln2}\lambda=0.693\mu$, the quartiles are $\mu\ln\frac43$ and $\mu\ln4$, and the interquartile range is $\frac{\ln4-\ln\frac43}\lambda=\frac{\ln3}\lambda$. The mode is 0, where $f_X=\lambda$ is largest, so mode $<$ median $<$ mean: the distribution is right-skewed. The lifetime example is $\lambda=\frac12$, which reproduces mean 2, standard deviation 2, median $2\ln2$ and interquartile range $2\ln3$.

> [!tip] The mean is not the typical value of a skewed variable
> For any exponential variable $P(X\le\mu)=1-e^{-1}=0.632$, so almost two-thirds of the components fail before the mean lifetime. A quoted mean life says little about what most units do; the median, $0.693\mu$, does.

James Exercise 38 models the running distance of a tyre, in thousands of km, with $f_X(x)=\frac1{30}e^{-x/30}$, an exponential with mean 30. Parts (a), (b) and (c) give:

$$
\begin{aligned}
P(X\le19)&=1-e^{-19/30}=0.469,\\
\mu&=30\ \text{thousand km}\quad(\text{and }\sigma=30),\\
\text{median}&=30\ln2=20.79\ \text{thousand km},\\
Q_1&=-30\ln0.75=8.63,\qquad Q_3=-30\ln0.25=41.59,\\
Q_3-Q_1&=30\ln3=32.96\ \text{thousand km}.
\end{aligned}
$$

## Terminology and alternative names

| Here (James and the booklet) | Also called |
|---|---|
| probability function $p_X(x)=P(X=x)$ | probability mass function (PMF); James writes $P_X(x)$ |
| distribution function $F_X(x)$ | cumulative distribution function (CDF) |
| (probability) density function $f_X$ | PDF |
| mutually exclusive events | disjoint events (James) |
| mean $\mu_X$ | expected value $E[X]$, expectation |
| $\binom nr$ | ${}^nC_r$, "$n$ choose $r$" |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M24 Solutions - Statistics I]]
- Previous: [[MATH1054 M22 - Complex Numbers II]] · Next: [[MATH1054 M25 - Statistics II]] (joint distributions, binomial and normal distributions, confidence intervals, hypothesis tests)
- Prerequisites: [[MATH1054 M09 - Integration II]] and [[Integration by Parts]] for the means and variances; [[MATH1054 M10 - Integration III]] and [[Improper Integrals]] for densities on $[0,\infty)$ or unbounded at a point
- Concepts: [[Probability Rules and Conditional Probability]] · [[Random Variables, PDF and CDF]] · [[Mean, Median and Variance of a Distribution]] · [[Centroids and Solids of Revolution]] (the mean as a centre of gravity)
- Built on in M25: [[Binomial Distribution]] · [[Normal Distribution and Standardisation]] · [[Confidence Intervals and Hypothesis Tests for the Mean]]
- Later years: [[Accuracy and Precision]] (SESA2027: random error measured by $\sigma$, Gaussian noise) · [[Bit Error Rate and Eb-N0]] (SESA2024: the probability that a received bit is wrong)

## Sources

- MATH1054 Module Booklet, Module 24: work scheme (booklet pp. 1–6, PDF pp. 80–85), including the Venn diagrams, Examples A–D and Exercise A; Specimen Test 24 (p. 7, PDF p. 86)
- James, *Modern Engineering Mathematics* (6th ed.): §13.3.1–13.3.5 (pp. 1009–1019) and Exercises 13.3.6 (pp. 1020–1021); §13.4.1–13.4.4 (pp. 1022–1027) and Exercises 13.4.5 (p. 1028); §13.4.6–13.4.7 (pp. 1028–1033) and Exercises 13.4.11 (p. 1042)
- Worked solutions to every work-scheme item: [[MATH1054 M24 Solutions - Statistics I]]

## Self-study tasks

The Module 24 work scheme sets James Exercises 7, 8 and 11 (p. 1020), 18, 19 and 22 (pp. 1021), Exercise 28 (p. 1028), Exercises 33 and 38(a), (b, mean only), (c) (p. 1042), booklet Exercise A, and Specimen Test 24. Exercises 7, 8 and 11 have no entry in the solutions note; they are worked in Sections 1 and 2 here.

### Core

- [ ] Exercise 18 (Module 24 work scheme): $P(A\cap B)$, $P(A\cup B)$ and $P(B\mid\bar A)$ from $P(A)=0.3$, $P(B)=0.4$, $P(B\mid A)=0.5$. Answers $0.15$, $0.55$, $\frac5{14}$. → [[#3. Conditional probability]] · [[MATH1054 M24 Solutions - Statistics I#Part B: Assigned exercises|solution (Part B)]]
- [ ] Exercise 22 (Module 24 work scheme): the probability that a potential customer buys, by total probability. Answer $0.149$. → [[MATH1054 M24 Solutions - Statistics I#Exercise 22: Advertising and purchases]]
- [ ] Exercise 28 (Module 24 work scheme): $c$, $F_X$ and $P(X>1)$ for $f_X=c/\sqrt x$ on $(0,4)$. Answers $\frac14$, $\frac12\sqrt x$, $\frac12$. → [[#A density that is unbounded (Exercise 28)]] · [[MATH1054 M24 Solutions - Statistics I#Part B: Assigned exercises|solution (Part B)]]
- [ ] Exercise 33 (Module 24 work scheme): mean, median and standard deviation of the daily malfunctions. Answers $1.80$, $2$, $1.342$. → [[MATH1054 M24 Solutions - Statistics I#Exercise 33: Daily computer malfunctions]]
- [ ] Specimen Test 24, Q1–Q7, timed. → [[MATH1054 M24 Solutions - Statistics I#Part C: Specimen Test 24]]

### Further practice

- [ ] Exercises 7, 8 and 11 (Module 24 work scheme): listing events, the rules for exclusive events, and an inconsistent survey. → [[#Listing the outcomes of combined events]] · [[#Examples using the rules]]
- [ ] Exercise 19 (Module 24 work scheme): three independent code-breakers. Answer $0.6$. → [[MATH1054 M24 Solutions - Statistics I#Exercise 19: Three independent code-breakers]]
- [ ] Booklet Example A and Specimen Test 24, Q3: total probability and Bayes, without looking at the tree. → [[#5. Total probability and Bayes' theorem]] · [[MATH1054 M24 Solutions - Statistics I#Q3: Two bags (Bayes' theorem)]]
- [ ] Exercise A and booklet Examples B–D (Module 24 work scheme): permutations, combinations and the faulty valves. Answer to Exercise A: $15$. → [[MATH1054 M24 Solutions - Statistics I#Booklet Exercise A: Choosing 4 objects from 6]] · [[#6. Counting with permutations and combinations]]
- [ ] Examples 13.16 and 13.17 (Module 24 work scheme): mean, median, mode, variance and interquartile range for the die, ships and lifetimes, including both integrations by parts. → [[MATH1054 M24 Solutions - Statistics I#Example 13.16: Mean, median and mode]] · [[MATH1054 M24 Solutions - Statistics I#Example 13.17: Variance and standard deviation]]
- [ ] Exercise 38(a), (b, mean only), (c) (Module 24 work scheme): the exponential tyre distance. Answers $0.469$, $30$, median $20.79$, IQR $32.96$. → [[MATH1054 M24 Solutions - Statistics I#Exercise 38: Tyre distance, exponential with mean 30 (thousand km)]]

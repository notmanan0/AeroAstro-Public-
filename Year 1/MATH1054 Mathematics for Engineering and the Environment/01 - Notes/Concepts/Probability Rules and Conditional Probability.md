---
title: "Probability Rules and Conditional Probability"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 5: Series and Statistics"
aliases: ["Conditional probability", "Independence", "Total probability", "Addition rule", "Combinations"]
tags: [math1054, concept, probability]
status: complete
parent_lectures: ["[[MATH1054 M24 - Statistics I]]"]
related_concepts: ["[[Random Variables, PDF and CDF]]", "[[Binomial Distribution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §13.2–13.3", "MATH1054 Module Booklet, Module 24"]
---

# Probability Rules and Conditional Probability

The probability rules say how the probabilities of combined events (one or the other, both, one given the other) follow from the probabilities of their parts. All of them derive from three axioms: $P(S)=1$, $P(A)\ge0$, and $P(A\cup B)=P(A)+P(B)$ when $A$ and $B$ cannot both occur.

The complement and general addition rules come from splitting events into exclusive pieces. $A$ and $\bar A$ are exclusive and fill $S$, so $P(A)+P(\bar A)=1$. Writing $A\cup B$ as $A$ together with the part of $B$ outside $A$, and noting that this part has probability $P(B)-P(A\cap B)$, gives

$$
P(\bar A)=1-P(A),\qquad P(A\cup B)=P(A)+P(B)-P(A\cap B).
$$

The overlap is subtracted because adding $P(A)$ and $P(B)$ counts it twice. "At least one" is nearly always quickest as $1-P(\text{none})$.

Once $A$ is known to have occurred, $A$ is the new sample space, and the chance of $B$ is the share of $A$ that lies in $B$. That is the **conditional probability**, and rearranging it gives the multiplication rule:

$$
P(B\mid A)=\frac{P(A\cap B)}{P(A)}\quad(P(A)>0),\qquad P(A\cap B)=P(A)P(B\mid A).
$$

$A$ and $B$ are **independent** when knowing $A$ leaves the chance of $B$ unchanged, $P(B\mid A)=P(B)$; substituting the definition turns this into the product form $P(A\cap B)=P(A)P(B)$, which is symmetric in $A$ and $B$.

If $A_1,\dots,A_n$ partition the sample space (exactly one of them occurs), any event $B$ splits into the exclusive pieces $B\cap A_i$, and the multiplication rule on each piece gives the **law of total probability**. Writing $P(A_j\cap B)$ both ways round and dividing by $P(B)$ gives **Bayes' theorem**, which reverses the direction of the conditioning:

$$
P(B)=\sum_iP(B\mid A_i)P(A_i),\qquad P(A_j\mid B)=\frac{P(B\mid A_j)P(A_j)}{\sum_iP(B\mid A_i)P(A_i)}.
$$

For equally likely outcomes, probabilities come from counting. A combination is a subset chosen without regard to order, and each subset of $r$ objects appears $r!$ times among the $n!/(n-r)!$ ordered selections, so the number of ways of choosing $r$ from $n$ is

$$
\binom nr=\frac{n!}{r!\,(n-r)!},
$$

for example $\binom64=15$ (booklet Exercise A).

Exercise 18 of the Module 24 work scheme uses three of the rules in turn. With $P(A)=0.3$, $P(B)=0.4$ and $P(B\mid A)=0.5$, the multiplication rule gives $P(A\cap B)=0.15$, the addition rule $P(A\cup B)=0.55$, and

$$
P(B\mid\bar A)=\frac{P(B)-P(A\cap B)}{1-P(A)}=\frac{0.25}{0.7}=\frac5{14}\approx0.357 .
$$

Three independent code-breakers who succeed with probabilities $\frac15$, $\frac14$, $\frac13$ all fail with probability $\frac45\cdot\frac34\cdot\frac23=\frac25$, so the code is broken with probability $1-\frac25=0.6$ (Exercise 19). In Exercise 22, 21% of potential buyers see an advertisement, one in three of those buy and one in ten of the rest do, so $P(\text{buy})=\frac13(0.21)+\frac1{10}(0.79)=0.149$. In booklet Example A, machines making 60%, 30% and 10% of a product with fault rates 1%, 2% and 5% give $P(F)=0.017$, and a faulty item came from the first machine with probability $0.006/0.017=0.353$.

The common trap is mixing up the two combination rules. Probabilities of mutually exclusive events add; probabilities of independent events multiply. The two conditions are nearly opposites: exclusive events with non-zero probabilities are never independent, because knowing one occurred rules the other out. A second trap is reading $P(A\mid B)$ as $P(B\mid A)$; they share a numerator but not a denominator.

## Related

- Topics: [[MATH1054 M24 - Statistics I]] (derivations in §2–§6, the tree diagram, worked examples) · [[MATH1054 M25 - Statistics II]]
- Solutions: [[MATH1054 M24 Solutions - Statistics I]]
- Concepts: [[Random Variables, PDF and CDF]] · [[Binomial Distribution]] (the product rule for independent trials, with $\binom nr$ counting the orders)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §13.2–13.3; MATH1054 Module Booklet, Module 24 (Examples A–D, Exercise A)

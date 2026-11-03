---
title: "Heaviside Step Function"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["Heaviside function", "Unit step", "H(x-a)"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]"]
related_concepts: ["[[Dirac Delta Function]]", "[[Laplace Transform Properties and Proofs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 13.txt"]
---

# Heaviside Step Function

The **Heaviside function** $H(x-a)$ is 0 for $x<a$ and 1 for $x>a$: a single switch, thrown at $x=a$. Its Laplace transform is $\frac{e^{-as}}{s}$ for $a>0$.

Scaling, shifting and multiplying it build any piecewise source. $f(x)H(x-a)$ switches $f$ on at $a$, $f(x)[1-H(x-a)]$ switches it off, and $f(x)[H(x-a)-H(x-b)]$ leaves it on only between $a$ and $b$. A unit force applied for $0<x<10$ is $1-H(x-10)$, and its response is $g(x)-H(x-10)g(x-10)$, where $g$ is the response to a force that stays on (PS5 Q3(f)).

What makes it useful with Laplace transforms is the second shift theorem, $\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s)$. Read backwards, a factor $e^{-as}$ in $\tilde y$ means "invert the rest, delay it by $a$ and switch it on at $a$". Read forwards, a source must be rewritten so that its argument is $x-a$ before it is transformed: $e^xH(x-1)=e\cdot e^{x-1}H(x-1)$, whose transform is $\frac{e\,e^{-s}}{s-1}$. For $y''+y=H(x-1)$ with $y(0)=0$, $y'(0)=1$ this gives $y=\sin x+H(x-1)[1-\cos(x-1)]$, in which $y$ and $y'$ are continuous at the switch and only $y''$ jumps.

Its derivative, in the generalised sense, is the [[Dirac Delta Function]].

![[m2048_tr_second_shift.png|520]]

## Related

- Derivation and examples: [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem]]
- [[Dirac Delta Function]] · [[Laplace Transform Properties and Proofs]]

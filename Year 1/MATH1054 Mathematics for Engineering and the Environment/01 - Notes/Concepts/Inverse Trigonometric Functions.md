---
title: "Inverse Trigonometric Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["arcsin", "arccos", "arctan", "sin^{-1}", "cos^{-1}", "tan^{-1}"]
tags: [math1054, concept, functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]", "[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Inverse Functions]]", "[[Hyperbolic Functions]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.6.7, §8.3.11", "MATH1054 Module Booklet, Module 7"]
---

# Inverse Trigonometric Functions

$\sin^{-1}x$, $\cos^{-1}x$ and $\tan^{-1}x$ (also written $\arcsin$, $\arccos$, $\arctan$) return the angle, in a fixed principal range, whose sine, cosine or tangent is $x$. The ranges are $[-\frac\pi2,\frac\pi2]$ for $\sin^{-1}$, $[0,\pi]$ for $\cos^{-1}$ and $(-\frac\pi2,\frac\pi2)$ for $\tan^{-1}$.

The trigonometric functions are periodic, so none is one-to-one and none has an inverse on all of $\mathbb R$ ([[Inverse Functions]]). Each is restricted to one branch on which it is one-to-one and takes all its values, and the inverse is defined on that branch. Cosine needs $[0,\pi]$ rather than a symmetric interval because it is even. The domains are $[-1,1]$ for $\sin^{-1}$ and $\cos^{-1}$ and all of $\mathbb R$ for $\tan^{-1}$, which has horizontal asymptotes $y=\pm\frac\pi2$.

| Function | Domain | Range | Derivative |
|---|---|---|---|
| $\sin^{-1}x$ | $[-1,1]$ | $[-\frac\pi2,\frac\pi2]$ | $\dfrac1{\sqrt{1-x^2}}$, $\lvert x\rvert<1$ |
| $\cos^{-1}x$ | $[-1,1]$ | $[0,\pi]$ | $-\dfrac1{\sqrt{1-x^2}}$, $\lvert x\rvert<1$ |
| $\tan^{-1}x$ | $\mathbb R$ | $(-\frac\pi2,\frac\pi2)$ | $\dfrac1{1+x^2}$ |

![[m1054_m07_inverse_trig_branches.png|900]]

The derivatives come from $x=\sin y$: $\frac{\mathrm dx}{\mathrm dy}=\cos y$, so

$$
\frac{\mathrm d}{\mathrm dx}\sin^{-1}x=\frac1{\cos y}=\frac1{\sqrt{1-\sin^2y}}=\frac1{\sqrt{1-x^2}},
$$

with the positive root because $\cos y>0$ on the branch. The same steps with $\sin y>0$ on $(0,\pi)$ give the minus sign for $\cos^{-1}$, and $\sec^2y=1+\tan^2y$ gives $\frac1{1+x^2}$ for $\tan^{-1}$. Read backwards they give the integrals $\int\frac{\mathrm dx}{\sqrt{a^2-x^2}}=\sin^{-1}\frac xa+C$ and $\int\frac{\mathrm dx}{a^2+x^2}=\frac1a\tan^{-1}\frac xa+C$ for $a>0$.

Two identities follow from the branches. If $\alpha=\sin^{-1}x$ then $\cos(\frac\pi2-\alpha)=x$ with $\frac\pi2-\alpha\in[0,\pi]$, so $\sin^{-1}x+\cos^{-1}x=\frac\pi2$. And $\cos(\pi-y)=-\cos y$ gives $\cos^{-1}(-x)=\pi-\cos^{-1}x$, while $\sin^{-1}$ and $\tan^{-1}$ are odd. For example (Example 2.50), $\sin^{-1}0.35=0.3576$ and $\cos^{-1}0.35=1.2132$, which sum to $1.5708=\frac\pi2$; $\tan^{-1}0.35=0.3367$; and $\cos^{-1}(-\frac12)=\pi-\frac\pi3=\frac{2\pi}3$ (Specimen Test 7, Q2).

The common trap is the composition $\sin^{-1}(\sin x)$. It equals $x$ only on $[-\frac\pi2,\frac\pi2]$; on $[\frac\pi2,\frac{3\pi}2]$ it is $\pi-x$, so the whole graph is a triangular wave of period $2\pi$, and $\sin^{-1}(\sin2)=\pi-2=1.1416$. Likewise $\cos^{-1}(\cos x)=|x|$ on $[-\pi,\pi]$, repeated with period $2\pi$. The other order, $\sin\big(\sin^{-1}x\big)=x$, holds for every $x$ in $[-1,1]$.

## Related

- Topics: [[MATH1054 M07 - Functions]] · [[MATH1054 M03 - Differentiation I]] · [[MATH1054 M09 - Integration II]]
- Concepts: [[Inverse Functions]] · [[Hyperbolic Functions]] · [[Even, Odd and Periodic Functions]] · [[Integration by Substitution]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.6.7, §8.3.9; MATH1054 Module Booklet, Module 7

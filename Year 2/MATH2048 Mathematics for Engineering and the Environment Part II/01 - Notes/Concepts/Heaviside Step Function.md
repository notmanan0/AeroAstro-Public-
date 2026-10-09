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
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf"]
---

# Heaviside Step Function

## Definition

> [!note] Definition
>
> $$H(x-a)=\begin{cases}0&x<a\\1&x>a\end{cases},\qquad\mathcal L[H(x-a)]=\frac{e^{-as}}{s}\quad(a\geq0).$$

## Explanation
**Building piecewise functions**:
- switch on at $a$: $fH(x-a)$;
- switch off at $a$: $f[1-H(x-a)]$;
- a window from $a$ to $b$: $f[H(x-a)-H(x-b)]$.

**Second shift theorem**: $\mathcal L[f(x-a)H(x-a)]=e^{-as}\tilde f(s)$.
- Going forward, rewrite the source so that it depends only on $x-a$. For example, $e^xH(x-1)=e\,e^{x-1}H(x-1)$.
- Going backward, $e^{-as}$ means "delay by $a$".

**Derivative**: $H'(x-a)=\delta(x-a)$.

## Examples
- $y''+y=H(x-1)$, $y(0)=0$, $y'(0)=1$ gives $y=\sin x+H(x-1)[1-\cos(x-1)]$.
- A pulse on $[0,10]$ is $1-H(x-10)$, whose response is $g(x)-H(x-10)g(x-10)$ (PS5 Q3f).

![[m2048_tr_second_shift.png|520]]

## Related
- [[Dirac Delta Function]] · [[Laplace Transform Properties and Proofs]]

## Sources
- Lecture 13

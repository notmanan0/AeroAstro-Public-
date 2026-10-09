---
title: "MATH1054 M03 - Differentiation I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 3
tags:
  - math1054
  - calculus
  - differentiation
  - newton-raphson
  - partial-derivatives
aliases: ["MATH1054 Module 3", "Differentiation I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M04 - Integration I]]", "[[MATH1054 M08 - Differentiation II]]"]
key_concepts: ["[[Derivative from First Principles]]", "[[Product, Quotient and Chain Rules]]", "[[Direct Substitution and Newton-Raphson]]", "[[Partial Derivatives]]"]
tutorial_sheets: ["[[MATH1054 M03 Solutions - Differentiation I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 3)", "02 - Sources/Modern Engineering Mathematics.pdf (§8.2–8.4, §9.4.8, §9.6)"]
---

# MATH1054 M03 - Differentiation I

> [!abstract] Summary
> This module covers four things:
> 1. The derivative as the limit of a difference quotient.
> 2. The algebra of rules that makes differentiation mechanical: sum, product, quotient and chain.
> 3. The standard derivatives you must know by heart.
> 4. Two applications: the **Newton–Raphson** root finder and **partial derivatives** of functions of two variables.
>
> Most of it is A-level revision, but partial derivatives are new. They are the gateway to MATH2048 vector calculus.

## Key Concepts
- [[Derivative from First Principles]] · [[Product, Quotient and Chain Rules]] · [[Direct Substitution and Newton-Raphson]] · [[Partial Derivatives]]

---

## 1. The derivative (James §8.2)
$$
f'(x)=\frac{\mathrm df}{\mathrm dx}=\lim_{\Delta x\to0}\frac{f(x+\Delta x)-f(x)}{\Delta x}
$$
Geometrically, this is the slope of the tangent: the limit of the chord slopes as the second point slides onto the first. Physically, it is an instantaneous rate: $v=\dot s$, $a=\dot v=\ddot s$.

- **Tangent** at $(x_0,y_0)$: $y-y_0=f'(x_0)(x-x_0)$.
- **Normal** at $(x_0,y_0)$: $y-y_0=-\dfrac{1}{f'(x_0)}(x-x_0)$. Perpendicular lines have gradients with product $m_1m_2=-1$.

> [!example] First principles in three lines: $f=x^2-2$
> $$\frac{(x+\Delta x)^2-2-(x^2-2)}{\Delta x}=2x+\Delta x\to2x.$$
> The recipe is always the same: expand, cancel $f(x)$, divide by $\Delta x$, then let $\Delta x\to0$.

## 2. The rules (James §8.3.1, 8.3.6; learn these)
| Rule | Statement |
|---|---|
| Constant multiple | $(cf)'=cf'$ |
| Sum | $(f\pm g)'=f'\pm g'$ |
| Product | $(uv)'=u'v+uv'$ |
| Quotient | $\left(\dfrac uv\right)'=\dfrac{u'v-uv'}{v^2}$ |
| Chain | $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{\mathrm dy}{\mathrm du}\cdot\dfrac{\mathrm du}{\mathrm dx}$ |
| Inverse | $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{1}{\mathrm dx/\mathrm dy}$ |

> [!tip] Simplify *before* you differentiate
> - $\left(\sqrt x+\frac1{\sqrt x}\right)^2=x+2+x^{-1}$ needs no product rule.
> - $\ln\frac{x-2}{x-3}=\ln(x-2)-\ln(x-3)$ needs no quotient rule.
> - $4x^7(x^2-3x)=4x^9-12x^8$.
>
> Each rewrite removes a rule application and a chance to slip.

## 3. Standard derivatives (James Fig. 8.26)
| $f(x)$ | $f'(x)$ | $f(x)$ | $f'(x)$ |
|---|---|---|---|
| $x^r$ ($r\in\mathbb R$) | $rx^{r-1}$ | $\sin^{-1}x$ | $\dfrac1{\sqrt{1-x^2}}$ |
| $e^{ax}$ | $ae^{ax}$ | $\cos^{-1}x$ | $-\dfrac1{\sqrt{1-x^2}}$ |
| $\ln x$ | $\dfrac1x$ | $\tan^{-1}x$ | $\dfrac1{1+x^2}$ |
| $\sin x$ | $\cos x$ | $\sec x$ | $\sec x\tan x$ |
| $\cos x$ | $-\sin x$ | $\csc x$ | $-\csc x\cot x$ |
| $\tan x$ | $\sec^2x$ | $\cot x$ | $-\csc^2x$ |

With the chain rule, each entry generalises: $\frac{\mathrm d}{\mathrm dx}\sin u=u'\cos u$, $\frac{\mathrm d}{\mathrm dx}\ln u=u'/u$, $\frac{\mathrm d}{\mathrm dx}e^{u}=u'e^u$, and so on.

**Worked patterns** (all from [[MATH1054 M03 Solutions - Differentiation I]]):
- $\dfrac{\mathrm d}{\mathrm dx}(5x^2+11)^9=9(5x^2+11)^8\cdot10x$: outer power, then inner derivative.
- $\dfrac{\mathrm d}{\mathrm dx}\sin^2(x^2+1)=2\sin(x^2+1)\cdot\cos(x^2+1)\cdot2x$: three layers, three factors.
- $\dfrac{\mathrm d}{\mathrm dx}\cos^{-1}\sqrt{1-x^2}=\dfrac{x}{|x|\sqrt{1-x^2}}$. Watch $\sqrt{x^2}=|x|$.

## 4. Higher derivatives (James §8.4)
$f''=\frac{\mathrm d}{\mathrm dx}f'$ and so on. The classic use is verifying that a function satisfies an ODE, such as Ex 62: $y=3e^{2x}\cos(2x-3)$ satisfies $y''-4y'+8y=0$. This previews [[MATH1054 M06 - Differential Equations I|M06]]. Here $r^2-4r+8=0$ gives $r=2\pm2j$, which is exactly the form $e^{2x}\cos(2x+\phi)$.

## 5. Newton–Raphson (James §9.4.8)
To solve $f(x)=0$, replace the curve by its tangent at $x_n$ and take the tangent's $x$-intercept:
$$
x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}
$$

![[m1054_newton_raphson.png|560]]

- **Rewrite first**: $g(x)=C$ becomes $f(x)=g(x)-C=0$. For example, $x\tan x=4$ becomes $x\tan x-4=0$.
- **No starting value given?** Tabulate $f$ and look for a sign change.
- **Convergence** is quadratic near a simple root: the number of correct digits roughly doubles each step. Stop when successive iterates agree to the required accuracy.
- **Failure modes**:
  - $f'(x_n)\approx0$ sends the iterate far away (Ex 26 from $x_0=1.5$ runs off to $-11$).
  - A starting point on a steep, curving section overshoots (Ex 9.17 from $x_0=1$).

See also [[Direct Substitution and Newton-Raphson]] (SESA/numerical-methods context).

## 6. Partial derivatives (James §9.6)
For $f(x,y)$, differentiate with respect to one variable while treating the other as a constant:
$$
\frac{\partial f}{\partial x}=\lim_{\Delta x\to0}\frac{f(x+\Delta x,y)-f(x,y)}{\Delta x}
$$
All the one-variable rules still apply. For example, $\dfrac{\partial}{\partial y}e^{-xy}=-xe^{-xy}$, because $x$ is a constant multiplier of $y$.

> [!note] Where this goes next
> $\nabla f=(f_x,f_y,f_z)$ is the gradient in MATH2048 ([[Gradient and Directional Derivative]]). Partial derivatives also define exact ODEs in [[MATH1054 M12 - Differential Equations II|M12]], where the test is $\partial_t(\cdot)=\partial_x(\cdot)$.

## Method checklist
1. Simplify algebraically (powers, log laws, expansion).
2. Identify the **outermost** operation, and apply the product, quotient or chain rule to it.
3. Recurse inwards until only standard derivatives remain.
4. Factor the result, and check one value numerically if unsure.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M03 Solutions - Differentiation I]]
- Next: [[MATH1054 M04 - Integration I]] · Continued in [[MATH1054 M07 - Functions]] (inverse and hyperbolic functions) and [[MATH1054 M08 - Differentiation II]] (implicit, parametric, logarithmic, stationary points)

## Sources
- MATH1054 Module Booklet, Module 3; James, *Modern Engineering Mathematics* 6th ed. §8.2–8.4, §9.4.8, §9.6

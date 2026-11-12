---
title: "Integration by Substitution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Substitution", "Change of variable", "u-substitution"]
tags: [math1054, concept, integration]
status: complete
parent_lectures: ["[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Parts]]", "[[Trigonometric Integrals and Power Reduction]]", "[[Hyperbolic Functions]]", "[[Completing the Square]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.8.6, §8.8.12", "MATH1054 Module Booklet, Module 9"]
---

# Integration by Substitution

Integration by substitution replaces the variable of integration by a new one, $u=g(x)$, so that an integrand of the form $f(g(x))\,g'(x)$ becomes $f(u)$:

$$
\int f\big(g(x)\big)\,g'(x)\,\mathrm dx=\int f(u)\,\mathrm du,\qquad\int_a^bf\big(g(x)\big)\,g'(x)\,\mathrm dx=\int_{g(a)}^{g(b)}f(u)\,\mathrm du.
$$

The rule is the chain rule read backwards. If $F'=f$, then $\frac{\mathrm d}{\mathrm dx}F(g(x))=f(g(x))\,g'(x)$, so $F(g(x))$ is an antiderivative of the left-hand integrand, and $F(u)$ is an antiderivative of $f(u)$; the two agree when $u=g(x)$. For the definite form, the fundamental theorem gives $\big[F(g(x))\big]_a^b=F(g(b))-F(g(a))=\int_{g(a)}^{g(b)}f(u)\,\mathrm du$, so the limits change with the variable and there is no need to return to $x$. The bookkeeping is $\mathrm du=g'(x)\,\mathrm dx$, and every $x$ in the integrand must be rewritten in terms of $u$ before integrating. The derivation needs $g'$ continuous on the interval; it does not need $g$ to be monotonic.

Read in the other direction, $x=g(t)$ turns $\int f(x)\,\mathrm dx$ into $\int f(g(t))\,g'(t)\,\mathrm dt$. Here $g$ must be monotonic on the interval, so that $t=g^{-1}(x)$ exists for the return to $x$. This is how roots are removed: $t=\sqrt{1-x}$ in $\int\frac{\mathrm dx}{2+\sqrt{1-x}}$, or a trigonometric or hyperbolic substitution chosen so that a Pythagorean identity makes the quantity under the root a perfect square.

| Spot | Substitute | Identity used |
|---|---|---|
| a function together with its derivative, $f'(x)\,[f(x)]^n$ | $u=f(x)$ | gives $\frac{[f(x)]^{n+1}}{n+1}$ for $n\neq-1$ |
| $\frac{f'(x)}{f(x)}$ | $u=f(x)$ | integrates directly to $\ln\lvert f(x)\rvert$ |
| $\sqrt{ax+b}$ | $u=\sqrt{ax+b}$ | $x=(u^2-b)/a$ |
| $\sqrt{a^2-x^2}$ | $x=a\sin\theta$, $\lvert\theta\rvert\leq\frac\pi2$ | $1-\sin^2\theta=\cos^2\theta$ |
| $\sqrt{x^2+a^2}$ or $x^2+a^2$ | $x=a\sinh u$ (or $x=a\tan\theta$) | $1+\sinh^2u=\cosh^2u$; $1+\tan^2\theta=\sec^2\theta$ |
| $\sqrt{x^2-a^2}$ | $x=a\cosh u$, $u\geq0$ | $\cosh^2u-1=\sinh^2u$ |
| $\sin^mx\cos^nx$ with $n$ odd | $u=\sin x$, keeping one $\cos x$ | $\cos^2x=1-\sin^2x$ |

As a worked example, take $\int_{-2}^2\frac{\sqrt{x+2}}{x+6}\,\mathrm dx$ (James Example 8.62). With $u=\sqrt{x+2}$, $x=u^2-2$, $\mathrm dx=2u\,\mathrm du$, $x+6=u^2+4$, and the limits become $0$ and $2$:

$$
\int_0^2\frac{2u^2}{u^2+4}\,\mathrm du=2\int_0^2\Big(1-\frac4{u^2+4}\Big)\,\mathrm du=2\Big[u-2\tan^{-1}\frac u2\Big]_0^2=4-\pi\approx0.8584.
$$

Two more from the same module: $x=\sin\theta$ gives $\int\sqrt{1-x^2}\,\mathrm dx=\frac12\sin^{-1}x+\frac12x\sqrt{1-x^2}+C$ (Example 8.60), and $u=\sqrt x$ with limits $1\to1$, $4\to2$ gives $\int_1^4\frac{e^{\sqrt x}}{\sqrt x}\,\mathrm dx=2\int_1^2e^u\,\mathrm du=2(e^2-e)\approx9.342$ (Exercise 115(d)). All three were checked with SymPy.

The common trap is the limits. After substituting in a definite integral, either change the limits and finish in $u$, or substitute back and use the original $x$-limits, but not a mixture: using the $x$-limits $1$ and $4$ on $2e^u$ above gives $2(e^4-e)\approx103.8$. The second trap is the sign of a root: $\sqrt{1-\sin^2\theta}=\lvert\cos\theta\rvert$, which equals $\cos\theta$ only on the range $-\frac\pi2\leq\theta\leq\frac\pi2$, so the range of the new variable has to be fixed along with the substitution.

## Related

- Topics: [[MATH1054 M09 - Integration II]] (derivations, all work-scheme examples and the Specimen Test); [[MATH1054 M04 - Integration I]]; [[MATH1054 M10 - Integration III]]
- Concepts: [[Integration by Parts]] · [[Trigonometric Integrals and Power Reduction]] · [[Hyperbolic Functions]] · [[Completing the Square]] · [[Product, Quotient and Chain Rules]] · [[Jacobian and Volume Elements]] (the same idea in several variables)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.8.6 and §8.8.12 (substitution, Figure 8.61); MATH1054 Module Booklet, Module 9.

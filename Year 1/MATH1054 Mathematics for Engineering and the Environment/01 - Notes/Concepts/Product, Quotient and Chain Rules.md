---
title: "Product, Quotient and Chain Rules"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Product rule", "Quotient rule", "Chain rule", "Differentiation rules"]
tags: [math1054, concept, differentiation]
status: complete
parent_lectures: ["[[MATH1054 M03 - Differentiation I]]"]
related_concepts: ["[[Derivative from First Principles]]", "[[Implicit and Parametric Differentiation]]", "[[Logarithmic Differentiation]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.3", "MATH1054 Module Booklet, Module 3"]
---

# Product, Quotient and Chain Rules

The product, quotient and chain rules give the derivative of a product, a quotient and a function of a function from the derivatives of the parts: $(uv)'=u'v+uv'$, $\big(\tfrac uv\big)'=\dfrac{u'v-uv'}{v^2}$, and $\dfrac{\mathrm dy}{\mathrm dx}=\dfrac{\mathrm dy}{\mathrm dz}\dfrac{\mathrm dz}{\mathrm dx}$ for $y=f(z)$, $z=g(x)$.

The product rule follows from the definition of the derivative by adding and subtracting $u(x)v(x+\Delta x)$ in the increment of $uv$:

$$
\begin{aligned}
\frac{\Delta(uv)}{\Delta x}&=\frac{u(x+\Delta x)-u(x)}{\Delta x}\,v(x+\Delta x)+u(x)\,\frac{v(x+\Delta x)-v(x)}{\Delta x}\\
&\longrightarrow u'v+uv',
\end{aligned}
$$

using the continuity of $v$. The quotient rule follows from the product rule applied to $u=yv$: $u'=y'v+yv'$, so $y'=(u'-yv')/v=(u'v-uv')/v^2$. The chain rule comes from writing $\dfrac{\Delta y}{\Delta x}=\dfrac{\Delta y}{\Delta z}\cdot\dfrac{\Delta z}{\Delta x}$ and noting that $\Delta z\to0$ as $\Delta x\to0$. The inverse-function rule $\dfrac{\mathrm dy}{\mathrm dx}=1\Big/\dfrac{\mathrm dx}{\mathrm dy}$ comes the same way from $\dfrac{\Delta y}{\Delta x}=1\Big/\dfrac{\Delta x}{\Delta y}$, and gives $\frac{\mathrm d}{\mathrm dx}\ln x=1/x$ from $x=e^y$.

In practice the chain rule means: differentiate the outer function with the inside left untouched, then multiply by the derivative of the inside, once per layer. That gives the generalised standard forms $\frac{\mathrm d}{\mathrm dx}u^n=nu^{n-1}u'$, $\frac{\mathrm d}{\mathrm dx}e^u=u'e^u$, $\frac{\mathrm d}{\mathrm dx}\ln u=u'/u$ and $\frac{\mathrm d}{\mathrm dx}\sin u=u'\cos u$. With three layers, as in $\sin^2(x^2+1)$, three factors appear: $2\sin(x^2+1)\cdot\cos(x^2+1)\cdot2x=2x\sin\big(2(x^2+1)\big)$. Choosing the rule means reading the outermost operation first. $(x^2+1)^3\sqrt{x-1}$ is a product whose factors each need the chain rule (James Example 8.16(c)):

$$
\begin{aligned}
y'&=6x(x^2+1)^2\sqrt{x-1}+\frac{(x^2+1)^3}{2\sqrt{x-1}}\\
&=\frac{(x^2+1)^2\big[12x(x-1)+(x^2+1)\big]}{2\sqrt{x-1}}\\
&=\frac{(x^2+1)^2(13x^2-12x+1)}{2\sqrt{x-1}},\qquad x>1.
\end{aligned}
$$

Other checked results are $\dfrac{3x+2}{2x^2+1}\mapsto\dfrac{3-8x-6x^2}{(2x^2+1)^2}$ (Example 8.14(a)) and $\tan^{-1}\dfrac{2x}{1+x^2}\mapsto\dfrac{2(1-x^2)}{x^4+6x^2+1}$ (Example 8.17(h)). Simplifying first often removes a rule altogether: expand $4x^7(x^2-3x)$, split $\ln\frac{x-2}{x-3}=\ln(x-2)-\ln(x-3)$, and write roots as powers. A quotient can always be done as the product $u\cdot v^{-1}$ instead.

The two common traps are dropping the inner derivative, so that $\frac{\mathrm d}{\mathrm dx}\cos x^4$ comes out as $-\sin x^4$ instead of $-4x^3\sin x^4$, and reversing the numerator of the quotient rule, which flips the sign of the answer. Taking out common factors before expanding, as in the second line above, keeps the result factorised and checkable.

## Related

- Topics: [[MATH1054 M03 - Differentiation I]] (Sections 2 and 3) · [[MATH1054 M08 - Differentiation II]]
- Concepts: [[Derivative from First Principles]] · [[Implicit and Parametric Differentiation]] · [[Logarithmic Differentiation]] · [[Partial Derivatives]] (the chain rule for $f(u)$ with $u=u(x,y)$)
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.3.1, §8.3.6, §8.3.7; MATH1054 Module Booklet, Module 3

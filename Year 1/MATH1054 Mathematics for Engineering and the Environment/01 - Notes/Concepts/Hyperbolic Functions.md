---
title: "Hyperbolic Functions"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["sinh", "cosh", "tanh", "Inverse hyperbolic functions", "Osborn's rule"]
tags: [math1054, concept, hyperbolic-functions]
status: complete
parent_lectures: ["[[MATH1054 M07 - Functions]]", "[[MATH1054 M22 - Complex Numbers II]]"]
related_concepts: ["[[Inverse Trigonometric Functions]]", "[[Euler's Formula]]", "[[Integration by Substitution]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §2.7.4–2.7.5, §8.3.12", "MATH1054 Module Booklet, Module 7"]
---

# Hyperbolic Functions

The hyperbolic cosine and sine are the even and odd parts of $e^x$, $\cosh x=\frac12(e^x+e^{-x})$ and $\sinh x=\frac12(e^x-e^{-x})$, and $\tanh x=\sinh x/\cosh x$; $\operatorname{sech}$, $\operatorname{cosech}$ and $\coth$ are their reciprocals, as for the trigonometric functions.

For real $x$, $\cosh x\geq1$ and is even; $\sinh x$ is odd and increasing; $\tanh x$ is odd with $|\tanh x|<1$. Adding and subtracting the definitions gives $\cosh x\pm\sinh x=e^{\pm x}$, and multiplying those two results gives the fundamental identity:

$$
\begin{aligned}
(\cosh x+\sinh x)(\cosh x-\sinh x)&=e^{x}e^{-x}\\
\cosh^2x-\sinh^2x&=1 .
\end{aligned}
$$

So $(\cosh t,\sinh t)$ lies on the hyperbola $x^2-y^2=1$, as $(\cos\theta,\sin\theta)$ lies on the circle, which is the origin of the name. Expanding in exponentials gives the addition formulae $\sinh(x\pm y)=\sinh x\cosh y\pm\cosh x\sinh y$ and $\cosh(x\pm y)=\cosh x\cosh y\pm\sinh x\sinh y$, and hence $\sinh2x=2\sinh x\cosh x$ and $\cosh2x=\cosh^2x+\sinh^2x$.

![[m1054_m07_hyperbolic_graphs.png|900]]

Osborn's rule turns a trigonometric identity into the hyperbolic one: swap each function for its hyperbolic counterpart and change the sign of every product, or implied product such as $\tan^2x$, of two sines. It works because $\cos\mathrm jx=\cosh x$ and $\sin\mathrm jx=\mathrm j\sinh x$ ([[Euler's Formula]]), so a product of two sines picks up $\mathrm j^2=-1$.

The derivatives are $\frac{\mathrm d}{\mathrm dx}\sinh x=\cosh x$ and $\frac{\mathrm d}{\mathrm dx}\cosh x=\sinh x$, with no minus sign, and $\frac{\mathrm d}{\mathrm dx}\tanh x=\operatorname{sech}^2x$ by the quotient rule. The inverses are logarithms. Writing $x=\sinh y$ and multiplying by $2e^y$ gives $(e^y)^2-2xe^y-1=0$, so $e^y=x\pm\sqrt{x^2+1}$, and only the plus sign is positive:

$$
\sinh^{-1}x=\ln\big(x+\sqrt{x^2+1}\big),\qquad\cosh^{-1}x=\ln\big(x+\sqrt{x^2-1}\big)\ (x\geq1),\qquad\tanh^{-1}x=\tfrac12\ln\frac{1+x}{1-x}\ (|x|<1).
$$

Their derivatives are $\frac1{\sqrt{1+x^2}}$, $\frac1{\sqrt{x^2-1}}$ and $\frac1{1-x^2}$, which give the integrals $\int\frac{\mathrm dx}{\sqrt{x^2\pm a^2}}$. The range of $\cosh^{-1}$ is restricted to $y\geq0$ because $\cosh$ is even.

As a worked example (Example 2.59), $5\cosh x+3\sinh x=4$ becomes $4e^x+e^{-x}=4$, then $4e^{2x}-4e^x+1=(2e^x-1)^2=0$, so $x=-\ln2\approx-0.6931$, a repeated root because the left side equals $4\cosh(x+\ln2)$, whose minimum is $4$. From one value the rest follow: $\sinh x=-\frac5{12}$ gives $\cosh x=\sqrt{1+\frac{25}{144}}=\frac{13}{12}$ and $\tanh x=-\frac5{13}$ (Specimen Test 7, Q4), and then $e^x=\cosh x+\sinh x=\frac23$.

These functions appear wherever a quantity grows one way and decays the other: $A\cosh kx+B\sinh kx$ solves $y''=k^2y$, the temperature along a cooling fin is a combination of $\sinh mx$ and $\sinh m(l-x)$, and a hanging cable takes the shape of a catenary, $y=a\cosh(x/a)$.

The common trap is carrying trigonometric signs across: $\frac{\mathrm d}{\mathrm dx}\cosh x$ is $+\sinh x$, the identity is $\cosh^2-\sinh^2=1$, and $\cosh x$ is always positive, so in $\cosh x=\sqrt{1+\sinh^2x}$ only the positive root is taken, while the sign of $\sinh x$ must come from the sign of $x$.

## Related

- Topics: [[MATH1054 M07 - Functions]] · [[MATH1054 M22 - Complex Numbers II]] · [[MATH1054 M09 - Integration II]] · [[MATH2048 ODE1 - Second-Order Linear ODEs with Constant Coefficients]]
- Concepts: [[Inverse Trigonometric Functions]] · [[Inverse Functions]] · [[Even, Odd and Periodic Functions]] · [[Euler's Formula]] · [[Complex Functions - Trig, Hyperbolic and Logarithm]] · [[Integration by Substitution]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §2.7.4–2.7.5, §8.3.12; MATH1054 Module Booklet, Module 7

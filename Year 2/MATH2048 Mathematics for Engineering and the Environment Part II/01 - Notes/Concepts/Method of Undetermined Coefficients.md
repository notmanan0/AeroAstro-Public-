---
title: "Method of Undetermined Coefficients"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["Particular integral", "Trial solution", "Complementary function", "CF + PI"]
tags: [math2048, concept, odes]
status: complete
parent_lectures: ["[[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]"]
related_concepts: ["[[Auxiliary Equation]]", "[[Resonance]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf", "02 - Sources/Lectures/MATH2048 Lecture 2.txt"]
---

# Method of Undetermined Coefficients

The **method of undetermined coefficients** finds a particular integral of a constant-coefficient ODE $y''+by'+cy=r(x)$ by guessing a function of the same form as the source, with unknown coefficients, substituting it and matching terms. The general solution is then the complementary function plus this particular integral, $y=c_1y_1+c_2y_2+y_P$.

| $r(x)$ | Guess for $y_P$ |
|---|---|
| polynomial of degree $n$ | general polynomial of degree $n$ |
| $e^{kx}$ | $Ce^{kx}$ |
| $\cos\omega x$ or $\sin\omega x$ | $C\cos\omega x+D\sin\omega x$ |
| $e^{kx}\times$ (any of the above) | $e^{kx}\times$ (the matching guess) |

If the guess overlaps the complementary function it can never balance the source, so multiply it by $x^s$, with $s$ the smallest power that removes the overlap; $s$ is the multiplicity of $k$ (or $k\pm j\omega$) as a root of the auxiliary equation, 0, 1 or 2. Writing $y_P=u\,e^{kx}$ shows why: the ODE becomes $u''+P'(k)u'+P(k)u=$ (source $\times e^{-kx}$), where $P$ is the auxiliary polynomial. If $P(k)=0$ the $u$ term disappears, and if $P'(k)=0$ as well only $u''$ remains, so $u$ needs one or two extra powers of $x$.

The method only works with constant coefficients and sources built from polynomials, exponentials and sines and cosines. For anything else, such as $\log(\sin x^{3/4})$ on the lecture slide, variation of parameters is needed (not examinable); the lecturer's advice is to give up after two failed guesses and use computer algebra.

Examples: $y''+4y'+4y=4x+25e^{3x}$ gives $y_P=x-1+e^{3x}$; $y''-2y'+y=4e^x$, a double root at 1, gives $y_P=2x^2e^x$; and $y''-2y'+2y=4e^x\sin x$, roots $1\pm j$, gives $y_P=-2xe^x\cos x$.

## Related

- Derivations and the clash examples: [[MATH2048 ODE2 - Euler Equations and Inhomogeneous ODEs]]
- [[Auxiliary Equation]] · [[Resonance]] · practice in [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS1 Q3)

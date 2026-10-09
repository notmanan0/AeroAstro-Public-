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
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture2_ODE.pdf", "02 - Sources/Lectures & Problem Sheets/ODEs/Appendix_Lecture1-2_(ODEs).pdf"]
---

# Method of Undetermined Coefficients

## Definition

> [!note] Definition
> For a constant-coefficient ODE $y''+by'+cy=r(x)$ with a "nice" source $r$ (polynomials, exponentials, sin/cos and their products), guess a particular integral $y_p$ of the same form with unknown coefficients. Substitute it into the ODE and match coefficients.
> The general solution is **CF + PI**: $y=c_1y_1+c_2y_2+y_p$.

## Explanation
| $r(x)$ | Trial $y_p$ |
|---|---|
| degree-$n$ polynomial | general degree-$n$ polynomial |
| $e^{kx}$ | $Ce^{kx}$ |
| $\cos\omega x$ or $\sin\omega x$ | $C\cos\omega x+D\sin\omega x$ |
| $e^{kx}\times$(any of the above) | $e^{kx}\times$(the matching trial) |

**Clash rule**: if the trial overlaps the CF, multiply it by $x^s$ with $s$ the smallest integer that removes the overlap. $s$ is the multiplicity of $k$ (or $k\pm j\omega$) as a root of the auxiliary equation: 0, 1 or 2.

**Why the rule works**: writing $y_p=u\,e^{kx}$ turns the ODE into

$$u''+P'(k)\,u'+P(k)\,u=\tilde r(x),$$

where $P$ is the auxiliary polynomial.
- If $P(k)=0$, the $u$ term is gone, so $u$ must be one degree higher (a factor $x$).
- If $P(k)=P'(k)=0$ too, only $u''$ remains (a factor $x^2$).

**Why CF + PI is general**: the operator is linear, so $y-y_p$ satisfies the homogeneous ODE.

**Limits**: it only works with constant coefficients and nice sources. For $r=\log(\sin x^{3/4})$ you would need variation of parameters, which is not examinable.

## Examples
- $y''+4y'+4y=4x+25e^{3x}$ gives $y_p=x-1+e^{3x}$.
- $y''-2y'+y=4e^x$ (double root 1) gives $y_p=2x^2e^x$.
- $y''-2y'+2y=4e^x\sin x$ (roots $1\pm j$) gives $y_p=-2xe^x\cos x$.

## Related
- [[Auxiliary Equation]] · [[Resonance]] · [[MATH2048 Problem Sheets 1-2 Solutions - ODEs]] (PS1 Q3)

## Sources
- Lecture 2; Appendix L1–2; Lecture Notes §1.1.2

---
title: "Routh-Hurwitz Stability Criterion"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part A: Dynamic Systems"
aliases: ["Routh-Hurwitz", "Routh discriminant", "Routh array"]
tags: [sesa2027, concept, stability]
status: complete
parent_lectures: ["[[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]"]
related_concepts: ["[[Characteristic Equation and Eigenvalues]]", "[[Closed-Loop Transfer Function]]"]
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf"]
---

# Routh-Hurwitz Stability Criterion

## Definition

> [!note] Definition
> A test for whether all roots of a polynomial have negative real parts, **without solving for them**. For the longitudinal stability quartic $A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0$ (with $A>0$), the aircraft is stable if and only if
>
> $$A,B,C,D,E>0\quad\text{and}\quad R = D(BC-AD)-B^2E>0$$
>
> $R$ is **Routh's discriminant**.

## Explanation
- **Necessary condition** (any order): all coefficients must be present and have the same sign. It is sufficient only for first- and second-order polynomials.
- For a quadratic $as^2+bs+c$: stable iff $a$, $b$, $c$ all have the same sign. This is used constantly in Part B for closed-loop polynomials.
- **General Routh array**: the number of sign changes in the first column equals the number of right-half-plane roots.
- In aircraft practice $A, B, C>0$ almost always hold. The critical conditions are:
  - **$E>0$**, which relates to static stability and the spiral/phugoid;
  - **$R>0$**, which relates to oscillatory stability.
- $E = 0$ gives a zero root (neutral). $R = 0$ gives a pair of roots on the imaginary axis (the boundary of oscillatory instability).

## Examples
- **L1.05 example**: $\lambda^4+\lambda^3+2.01\lambda^2+0.01\lambda+0.01$ gives $R = 0.01(2.01-0.01)-0.01 = 0.01>0$, so it is stable ✔.
- **PS1 Q1**: the product is $\lambda^4+1.3984\lambda^3+9.4894\lambda^2-0.01294\lambda+0.01518$.
  - $D<0$ already signals instability.
  - $R = -0.202<0$ confirms it: the phugoid diverges ([[SESA2027 Practice Problems 1 Solutions]]).
- **PS2 Q6**: $s^2+4s+K$ is stable for all $K>0$ ([[SESA2027 Practice Problems 2 Solutions]]).

## Related
- [[Characteristic Equation and Eigenvalues]] · [[Closed-Loop Transfer Function]] · [[Phugoid Mode]]

## Sources
- Lecture 1.05; Cook (2013), Ch. 7

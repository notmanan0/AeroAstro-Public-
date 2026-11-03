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
sources: ["02 - Sources/Lectures/Lecture 1.05.pdf", "Cook (2013), Ch. 7"]
---

# Routh-Hurwitz Stability Criterion

The Routh–Hurwitz criterion tests whether every root of a polynomial has a negative real part without solving for the roots. For the longitudinal stability quartic $A\lambda^4+B\lambda^3+C\lambda^2+D\lambda+E = 0$ with $A>0$, the aircraft is stable if and only if

$$
A,B,C,D,E>0\quad\text{and}\quad R = D(BC-AD)-B^2E>0,
$$

where $R$ is Routh's discriminant.

For any order, a necessary condition is that all the coefficients are present and have the same sign, but that is sufficient only for first- and second-order polynomials. The second-order case, $as^2+bs+c$ stable if and only if $a$, $b$ and $c$ share a sign, is used constantly in Part B for closed-loop polynomials; $s^2+4s+K$ in PS2 Q6 is stable for all $K>0$ ([[SESA2027 Practice Problems 2 Solutions]]). For higher orders the general Routh array is needed, and the number of sign changes in its first column equals the number of right-half-plane roots.

For aircraft, $A$, $B$ and $C$ are almost always positive, so the conditions that decide things are $E>0$, linked to static stability and the spiral and phugoid modes, and $R>0$, linked to oscillatory stability. $E = 0$ gives a zero root (neutral stability), and $R = 0$ puts a pair of roots on the imaginary axis, the boundary of oscillatory instability.

The L1.05 quartic $\lambda^4+\lambda^3+2.01\lambda^2+0.01\lambda+0.01$ gives $R = 0.01(2.01-0.01)-0.01 = 0.01>0$, so it is stable. In PS1 Q1 the product of the two factors is $\lambda^4+1.3984\lambda^3+9.4894\lambda^2-0.01294\lambda+0.01518$. $D<0$ already signals instability, and $R = -0.202<0$ confirms that the phugoid diverges ([[SESA2027 Practice Problems 1 Solutions]]).

## Related

- [[Characteristic Equation and Eigenvalues]] · [[Closed-Loop Transfer Function]] · [[Phugoid Mode]]

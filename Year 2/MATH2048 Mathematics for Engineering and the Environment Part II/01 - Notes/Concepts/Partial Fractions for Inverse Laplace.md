---
title: "Partial Fractions for Inverse Laplace"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 3: Fourier and Laplace Transforms"
aliases: ["Partial fractions", "Cover-up rule", "Inverse Laplace transform"]
tags: [math2048, concept, transforms]
status: complete
parent_lectures: ["[[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs]]"]
related_concepts: ["[[Laplace Transform Properties and Proofs]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture12_LaplaceTransform2.pdf", "02 - Sources/Lectures & Problem Sheets/Fourier and Laplace Transform/Lecture13_LaplaceTransform3.pdf", "02 - Sources/Lectures/MATH2048 Lecture 12.txt"]
---

# Partial Fractions for Inverse Laplace

Partial fractions is how MATH2048 inverts a Laplace transform: the rational function $\tilde y(s)$ is split into simple fractions that each appear in the table. There is an inversion integral, but it is a complex contour integral and not used in the module.

Each factor of the denominator contributes its own terms. A simple linear factor $s-r$ gives $\frac A{s-r}$, which inverts to $Ae^{rx}$. A repeated factor $(s-r)^n$ gives $\frac{A_1}{s-r}+\dots+\frac{A_n}{(s-r)^n}$, and $\frac1{(s-r)^k}$ inverts to $\frac{x^{k-1}}{(k-1)!}e^{rx}$. An irreducible quadratic is first completed to the square, $(s+c)^2+b^2$, and given a numerator $B(s+c)+Cb$ so that it inverts directly to $e^{-cx}(B\cos bx+C\sin bx)$ by the first shift theorem. If the numerator's degree is not less than the denominator's, divide first.

To find the coefficients, multiply through by the full denominator to get a polynomial identity that holds for every $s$. Substituting the roots of the denominator kills all but one term each time, which gives the coefficients of the highest power of each factor (the cover-up rule). Whatever is left comes from comparing powers of $s$ or substituting other convenient values. Lecture 12's example, $\frac{s^2+s+1}{s^2(s+1)^2(s+2)}$, gives $E=\frac12$, $C=1$ and $A=\frac34$ from $s=0,-1,-2$, then $B=0$ and $D=-\frac34$ from the $s^4$ coefficient and $s=1$.

With Heaviside or delta sources, $\tilde y$ contains factors $e^{-as}$. Set each aside, decompose only the rational part, and restore the exponential at the end with the second shift theorem. The Lecture 13 example needs $\frac1{s(s^2+1)}=\frac1s-\frac s{s^2+1}$, which inverts to $1-\cos x$. A denominator that is a polynomial in $s^2$, such as $(s^2+1)(s^2+4)$, can be split treating $s^2$ as the variable: $\frac1{(s^2+1)(s^2+4)}=\frac13\big[\frac1{s^2+1}-\frac1{s^2+4}\big]$ (PS5 Q3(e)).

## Related

- Worked examples: [[MATH2048 TR2 - Laplace Transforms - Definition, Properties and Solving IVPs#Partial fractions, the systematic route (L12)|TR2]] · [[MATH2048 TR3 - Heaviside and Delta Functions and the Second Shift Theorem#Switching on a constant force (L13)|TR3]] · [[MATH2048 Problem Sheet 4-5 Solutions - Fourier and Laplace Transforms]]
- [[Laplace Transform Properties and Proofs]]

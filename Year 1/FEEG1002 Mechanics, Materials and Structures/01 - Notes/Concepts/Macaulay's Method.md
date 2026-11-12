---
title: "Macaulay's Method"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["Macaulay brackets", "singularity functions", "step function method", "[x-a]^n"]
tags: [feeg1002, concept, statics, beams, deflection, singularity-functions]
status: complete
parent_lectures: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]", "[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
related_concepts: ["[[Heaviside Step Function]]", "[[Standard Beam Deflections]]", "[[Shear Force and Bending Moment Relations]]", "[[Superposition for Indeterminate Beams]]"]
sources: ["Statics 1 Lectures 10-11"]
---

# Macaulay's Method

Macaulay's method writes the bending moment of a beam with several loads as one expression valid along the whole length, using switch-on brackets

$$
[x-a]^n=\begin{cases}0 & x<a\\(x-a)^n & x\ge a\end{cases}
$$

and then integrates $EI\,d^2v/dx^2=-M$ twice to get the deflection with only two integration constants.

Without the brackets, a beam with $k$ load points has $k+1$ regions, each with its own bending moment, and double integration gives two constants per region. Most of the conditions that fix them are continuity of slope and deflection at the load points, which makes the algebra long. With the brackets one cut, taken beyond the last change in loading, gives a single moment expression: each load's term is zero for cuts before it and the ordinary term after it. Continuity is then automatic, and only the two real boundary conditions remain.

The brackets keep their meaning only if they are never expanded and are integrated as a whole, $\int[x-a]^n\,dx=[x-a]^{n+1}/(n+1)$; any bracket with a negative argument is zero when evaluated. For the left part of the beam, an upward force $R$ at $a$ contributes $+R[x-a]$, a downward force $F$ contributes $-F[x-a]$, a uniform load $w$ from $a$ contributes $-w[x-a]^2/2$ (its resultant times half the loaded length), and an anticlockwise couple $M_0$ contributes $-M_0[x-a]^0$. A bracket once switched on cannot be switched off, so a uniform load that stops at $b$ is written as the load from $a$ plus an equal upward load from $b$, $+w[x-b]^2/2$.

The method works the same way for indeterminate beams. The unknown reactions are carried through the integration as symbols, and the extra kinematic conditions (zero slope at a built-in end, zero deflection at a prop) supply the missing equations. Differentiating a Macaulay moment is a quick check: $dM/dx$ should reproduce the shear force diagram.

![[s1_macaulay_brackets.png|760]]

## Related

- Topic notes: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#4. Macaulay's method|A5, Macaulay's method]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Writing the bending moment for other loads|A5, writing M for other loads]] · [[FEEG1002 A6 - Statically Indeterminate Beams#2. The double integration method|A6, double integration method]]
- Tutorial: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]
- Concepts: [[Shear Force and Bending Moment Relations]] · [[Standard Beam Deflections]] · [[Superposition for Indeterminate Beams]]
- Year 2: $[x-a]^0$ is the [[Heaviside Step Function]], the same object as the delayed input of the [[Laplace Transform]] in [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]

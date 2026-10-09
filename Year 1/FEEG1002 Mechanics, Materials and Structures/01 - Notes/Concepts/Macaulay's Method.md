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
sources: []
---

# Macaulay's Method

## Definition

> [!note] Definition
> Write the bending moment as a **single** expression valid along the whole beam using switch-on brackets
> $$[x-a]^n = \begin{cases}0 & x<a\\ (x-a)^n & x\ge a\end{cases}$$
> Then integrate $EIv'' = -M$ twice, never expanding a bracket: $\int[x-a]^ndx = [x-a]^{n+1}/(n+1)$. Only **two** integration constants appear, whatever the number of loads.

## Explanation

Procedure:
1. Find the reactions, or keep them as unknowns if the beam is indeterminate.
2. Cut once, beyond the last load change, and write $M$ for the left part.
3. Integrate twice.
4. Apply the boundary conditions, remembering that brackets with $x<a$ vanish.

Contributions to $M$:

| Load | Term |
|---|---|
| Upward force $R$ at $a$ | $+R[x-a]$ |
| Downward force $F$ | $-F[x-a]$ |
| UDL from $a$ | $-w[x-a]^2/2$ |
| UDL stopping at $b$ | add $+w[x-b]^2/2$ |
| Anticlockwise couple $M_0$ | $-M_0[x-a]^0$ |

- A switched-on bracket cannot be switched off, hence the cancelling UDL.

## Examples

- Tutorial 5 Q2: $M = 12[x-3] - 3[x-2]^2 + 3[x-4]^2$, giving $v(5) = 0.5$ mm.
- Tutorial 5 Q1: cantilever with midspan load, $v(L) = 5FL^3/48EI$.

![[s1_macaulay_brackets.png|560]]

## Related

- Topic notes: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Concepts: [[Heaviside Step Function]] · [[Standard Beam Deflections]] · [[Shear Force and Bending Moment Relations]] · [[Superposition for Indeterminate Beams]]
- Year 2: $[x-a]^0$ is the [[Heaviside Step Function]] (MATH2048), the same object as the time-shifted input in the [[Laplace Transform]] of [[SESA2027 A4 - Laplace Transforms, Transfer Functions and Step Response]]

## Sources

- Statics 1 Lectures 10a–c

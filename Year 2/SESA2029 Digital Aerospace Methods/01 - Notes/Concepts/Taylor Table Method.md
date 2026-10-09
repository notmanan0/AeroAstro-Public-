---
title: "Taylor Table Method"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part A: Computational Fluid Dynamics"
aliases: ["Taylor table", "general finite-difference construction", "stencil derivation"]
tags: [sesa2029, concept, numerical-methods]
status: complete
parent_lectures: ["[[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]"]
related_concepts: ["[[Finite Difference Approximations]]", "[[Truncation Error and Order of Accuracy]]", "[[Convective Interpolation Schemes]]"]
sources: ["02 - Sources/CFD/All_lectures_as_delivered.pdf (L3 slides 8–10)", "02 - Sources/CFD/CFD.txt"]
---

# Taylor Table Method

## Definition

> [!note] Definition
> A systematic way to find the most accurate coefficients of a finite-difference stencil:
> 1. Expand every stencil point in a Taylor series about the target point.
> 2. Tabulate the coefficients.
> 3. Choose the unknowns to zero as many columns as possible.
> 4. The first non-zero column is the leading error.

## Explanation

**Recipe** (for $f'_j = (af_{j-2}+bf_{j-1}+cf_j)/h+\varepsilon$):
1. Multiply by $h$ and move every term except the error to the left: $hf'_j-af_{j-2}-bf_{j-1}-cf_j = h\varepsilon$.
2. Column headings: $f_j,\ hf'_j,\ \tfrac{h^2}{2}f''_j,\ \tfrac{h^3}{6}f'''_j,\dots$. The Taylor coefficients for $f_{j+m}$ are $1, m, m^2, m^3,\dots$.
3. Fill one row per term, including its sign. With $n$ unknowns, set the first $n$ column sums to zero.
4. The next column sum times its heading equals $h\varepsilon$. Divide by $h$ to read the order.

| Term | $f_j$ | $hf'_j$ | $\frac{h^2}{2}f''_j$ | $\frac{h^3}{6}f'''_j$ |
|---|---|---|---|---|
| $hf'_j$ | 0 | 1 | 0 | 0 |
| $-af_{j-2}$ | $-a$ | $2a$ | $-4a$ | $8a$ |
| $-bf_{j-1}$ | $-b$ | $b$ | $-b$ | $b$ |
| $-cf_j$ | $-c$ | 0 | 0 | 0 |

The three equations give $a = \tfrac12$, $b = -2$ and $c = \tfrac32$. The error is $h\varepsilon = (8a+b)\tfrac{h^3}{6}f'''$, so $\varepsilon = \tfrac{h^2}{3}f'''_j$: **second order**.

## Examples

- 2-point forward: $f'_j = (f_{j+1}-f_j)/h$ with $\varepsilon = -\tfrac h2f''_j$.
- 3-point forward: $f'_j = (-3f_j+4f_{j+1}-f_{j+2})/2h$ with $\varepsilon = -\tfrac{h^2}{3}f'''_j$.
- Central second derivative: $\varepsilon = -\tfrac{h^2}{12}f''''_j$.

Full tables are in [[SESA2029 CFD Worked Examples]].

## Related

- Parent lectures: [[SESA2029 A2 - Discrete Data, Finite Differences and Taylor Tables]]
- Related concepts: [[Finite Difference Approximations]] · [[Truncation Error and Order of Accuracy]] · [[Convective Interpolation Schemes]]

## Sources

- 02 - Sources/CFD/All_lectures_as_delivered.pdf (L3 slides 8–10)
- 02 - Sources/CFD/CFD.txt

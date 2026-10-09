---
title: "Gaussian Elimination"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Elimination", "Back substitution", "Row reduction", "Ill-conditioning"]
tags: [math1054, concept, linear-systems]
status: complete
parent_lectures: ["[[MATH1054 M17 - Matrices II]]", "[[MATH1054 M18 - Matrices III]]"]
related_concepts: ["[[Matrix Inverse]]", "[[Rank and Consistency of Linear Systems]]", "[[Jacobi, Gauss-Seidel and SOR Iteration]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §5.5", "MATH1054 Module Booklet, Module 17"]
---

# Gaussian Elimination

## Definition

> [!note] Definition
> Reduce the augmented matrix $[\mathbf A|\mathbf b]$ to upper-triangular form using row operations ($R_i\to R_i-mR_k$, swaps, scalings). Then solve from the bottom up (back-substitution).

## Explanation
- Row operations do not change the solution set.
- A zero pivot needs a row swap. **Partial pivoting** (swapping the largest pivot into place) also controls round-off error.
- **Ill-conditioning**: when $|\mathbf A|\approx0$, tiny data changes cause huge solution changes.
- **Tridiagonal systems** need only one elimination per row: the Thomas algorithm, used throughout finite differences.
- Cost: $O(n^3)$, compared with $O(n!)$ for cofactor expansion.

## Examples
- $(x,y,z,t)=(1,1,1,-1)$ (Ex 5.34); $(1,2,2,3)$ for a tridiagonal system (Ex 73).
- $0.5001\to0.4999$ flips $y=4500\to-4500$ (Ex 5.36).

## Related
- Topics: [[MATH1054 M17 - Matrices II]] · [[MATH1054 M18 - Matrices III]]
- Concepts: [[Matrix Inverse]] · [[Rank and Consistency of Linear Systems]] · [[Jacobi, Gauss-Seidel and SOR Iteration]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §5.5
- MATH1054 Module Booklet, Module 17

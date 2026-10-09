---
title: "Maxwell-Betti Reciprocity"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, energy-methods]
status: complete
parent: ["[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
---

# Maxwell-Betti Reciprocity

**Betti's theorem.** For a linear elastic structure with two load systems A and B:

$$
\sum P_A\,\delta_{A\leftarrow B}=\sum P_B\,\delta_{B\leftarrow A}.
$$

The work done by system A's forces moving through the displacements caused by B equals the work done by B's forces moving through the displacements caused by A.

**Maxwell's reciprocal theorem** (unit loads). Let $\delta_{ij}$ be the displacement at point $i$ (in direction $i$) caused by a unit load at point $j$ (in direction $j$). Then

$$
\boxed{\delta_{ij}=\delta_{ji}.}
$$

In words: *the deflection at $i$ due to a unit load at $j$ equals the deflection at $j$ due to a unit load at $i$.* The same holds for rotations and moments. The rotation at $i$ due to a unit force at $j$ equals the deflection at $j$ due to a unit moment at $i$ (numerically, in consistent units).

## Example

Cantilever, length $L$: the tip deflection due to a unit load at mid-span equals the mid-span deflection due to a unit load at the tip. Both are $\dfrac{5L^3}{48EI}$.

## Uses

- A check on flexibility coefficients and on virtual-work answers.
- It is why the flexibility and stiffness matrices are **symmetric** (FEA).
- Measuring an influence line by moving the *measurement* point instead of the load.

## Limits

It needs linear elasticity, small displacements and conservative loads. It fails for plasticity, large deflection and follower forces.

See [[Principle of Virtual Work]].

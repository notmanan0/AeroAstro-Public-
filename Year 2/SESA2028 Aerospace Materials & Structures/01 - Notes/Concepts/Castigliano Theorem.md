---
title: "Castigliano Theorem"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, castigliano]
status: complete
---

# Castigliano Theorem

For a linearly elastic structure,

$$
\delta_i=\frac{\partial U}{\partial P_i},\qquad
\theta_i=\frac{\partial U}{\partial M_i}.
$$

If the required displacement has no real load, introduce a dummy load $Q$, write every internal-force function in terms of $Q$, differentiate, and set $Q=0$ only at the end.

For bending-dominated members,

$$
\delta_i=\int\frac{M}{EI}\frac{\partial M}{\partial P_i}dx.
$$

This is mathematically the same core integral as the unit-load method. Castigliano is often faster when one real load parameter already appears cleanly in $M(x)$; virtual work is often clearer when many real loads act but only one displacement is wanted.

See [[SESA2028 S8 - Virtual Work and Castigliano Theorems]].


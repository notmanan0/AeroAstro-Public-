---
title: "Multi-Cell Torsion"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, torsion]
status: complete
---

# Multi-Cell Torsion

Assign one unknown constant circulation $q_i$ to each closed cell. Torque equilibrium supplies

$$
T=2\sum_iA_iq_i.
$$

A wall shared by cells $i,j$ carries $q_i-q_j$, not $q_i+q_j$, once a common circulation direction is chosen. Each cell has the same physical twist rate, giving the remaining compatibility equations:

$$
\frac1{2A_i}\oint_i\frac{q_{wall}}{Gt}ds
=
\frac1{2A_j}\oint_j\frac{q_{wall}}{Gt}ds.
$$

Solve the simultaneous system before converting any wall flow to stress.

See [[SESA2028 S4 - Torsion of Thin-Walled Sections]].


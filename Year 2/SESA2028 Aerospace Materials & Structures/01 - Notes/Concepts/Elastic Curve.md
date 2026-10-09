---
title: "Elastic Curve"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, beam-deflection]
status: complete
---

# Elastic Curve

The elastic curve is the deflected beam centreline. With constant $EI$, integrate

$$
EI v''(x)=M(x)
$$

twice and determine constants from support and continuity conditions. At a fixed end $v=0$ and $v'=0$; at a pin or roller $v=0$; at an internal hinge $M=0$ and displacement is continuous, but the two member slopes need not match.

Macaulay functions or piecewise integration are both valid if every load and stiffness discontinuity is handled.

See [[Moment Curvature Relation]].


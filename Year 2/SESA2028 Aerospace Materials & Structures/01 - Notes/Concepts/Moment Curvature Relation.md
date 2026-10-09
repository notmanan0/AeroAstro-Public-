---
title: "Moment Curvature Relation"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, beam-deflection]
status: complete
parent: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
---

# Moment Curvature Relation

Euler-Bernoulli beam theory (plane sections stay plane and normal to the axis, linear elastic, small slopes) gives

$$
\kappa=\frac{M}{EI},\qquad \kappa=\frac{v''}{[1+(v')^2]^{3/2}}\approx\frac{d^2v}{dx^2},
$$

so

$$
EI\frac{d^2v}{dx^2}=M(x).
$$

## Where it comes from

Plane sections give a linear strain $\varepsilon_x=-y\kappa$ (for bending about $z$). Hooke's law gives $\sigma_x=-Ey\kappa$. The moment resultant $M=-\int y\sigma_x\,dA=E\kappa\int y^2dA=EI\kappa$.

## The derivative chain

$$
v\ \xrightarrow{d/dx}\ \theta=v'\ \xrightarrow{\times EI\,d/dx}\ M=EIv''\ \xrightarrow{d/dx}\ V=EIv'''\ \xrightarrow{d/dx}\ -w=EIv''''
$$

(signs follow the chosen convention: $dV/dx=-w$, $dM/dx=V$).

## Good habits

- **Signs**: the sign of $M$ and the positive direction of $v$ must match the convention you drew. With sagging-positive $M$ and $v$ positive upwards, $EIv''=+M$. If you choose $v$ downward, a minus sign appears. Consistency beats memorising one version.
- **Continuity**: $v$ and $v'$ are continuous everywhere except at hinges (slope jump) or gaps. A point load gives a jump in $V$, so a kink in $M$. A point moment gives a jump in $M$.
- **Small slopes only**: large-deflection problems (elastica) need the exact curvature.

See [[Elastic Curve]] and [[SESA2028 S2 - Beam Deflection and Bending Design]].

---
title: "Second Moments of Area"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Structures"
tags: [sesa2028, structures, section-properties]
status: complete
parent: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
---

# Second Moments of Area

$$
I_y=\int_Az^2\,dA,\qquad I_z=\int_Ay^2\,dA,\qquad I_{yz}=\int_Ayz\,dA
$$

about **centroidal** axes. $I_y$ and $I_z$ are always positive. $I_{yz}$ can have either sign and changes sign if either axis is reversed.

## Standard results (about the element's own centroid)

| Shape | Second moment |
|---|---|
| Rectangle $b\times h$ (bending about the axis parallel to $b$) | $\dfrac{bh^3}{12}$ |
| Solid circle, radius $R$ | $\dfrac{\pi R^4}{4}$ |
| Thin circular tube, radius $r$, thickness $t$ | $\pi r^3t$ |
| Thin wall of length $L$, thickness $t$, inclined at $\alpha$ to the bending axis | $\dfrac{tL^3\sin^2\alpha}{12}$ |
| Rectangle, product of inertia about own centroidal axes | $0$ (it has symmetry) |

## Parallel-axis theorem

$$
I_y=\sum\left(I_{y,c}+A\,\Delta z^2\right),\qquad
I_z=\sum\left(I_{z,c}+A\,\Delta y^2\right),\qquad
I_{yz}=\sum\left(I_{yz,c}+A\,\Delta y\,\Delta z\right),
$$

where $\Delta y$ and $\Delta z$ are the **signed** offsets of each part's centroid from the section centroid. Getting the signs right in the $I_{yz}$ term is the most common error.

## Thin-walled approximation

For $t\ll b$, drop the $t^3$ terms (e.g. a horizontal flange contributes $A\Delta z^2$ to $I_y$ and essentially nothing of its own). Use **median-line** dimensions.

## Worked check

Equal-leg angle: $I_y=I_z=1.80\times10^6$ mm⁴ and $I_{yz}=1.07\times10^6$ mm⁴ (2013-14 A1). The principal values are $1.80\pm1.07$, i.e. $2.87$ and $0.73\times10^6$ mm⁴, at $45^\circ$.

See [[Principal Second Moments of Area]] and [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]].

## Year 1 foundation
- $I$ for symmetric sections and the parallel axis theorem: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]].

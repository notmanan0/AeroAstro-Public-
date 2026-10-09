---
title: "Secant Formula"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, buckling, eccentric-load]
status: complete
---

# Secant Formula

The secant formula combines direct compression with second-order bending from a constant load eccentricity. For a pin-ended column,

$$
\sigma_{max}=\frac PA\left[
1+\frac{ec}{r_g^2}
\sec\left(\frac{L}{2r_g}\sqrt{\frac{P}{EA}}\right)
\right].
$$

The secant term is a moment-amplification factor. As $P$ approaches the Euler load, the argument approaches $\pi/2$ and the ideal elastic stress grows without bound.

For other boundary conditions derive the corresponding differential-equation solution or use the appropriate effective configuration; do not change only $L$ blindly when the load application differs.

See [[Beam-Column Amplification]].


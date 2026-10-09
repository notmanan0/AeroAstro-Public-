---
title: "Bredt-Batho Torsion"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, torsion, thin-walled]
status: complete
---

# Bredt-Batho Torsion

For a single thin-walled closed cell,

$$
\boxed{q=\frac{T}{2A_m}}.
$$

The shear flow is constant around the cell even when thickness changes. The stress is not:

$$
\tau(s)=\frac q{t(s)}.
$$

The twist rate is

$$
\frac{d\phi}{dx}=\frac{T}{4A_m^2}\oint\frac{ds}{G(s)t(s)}.
$$

For multiple cells assign one constant circulation $q_i$ per cell. A common wall carries $q_i-q_j$. Combine one global torque equation with equal-twist compatibility between cells.

The enclosed area appears squared in torsional stiffness. That is why closing an open section is normally far more effective than modestly increasing its wall thickness.

![Open versus closed torsion](../Figures/structures_open_vs_closed_torsion.png)

See [[SESA2028 S4 - Torsion of Thin-Walled Sections]].


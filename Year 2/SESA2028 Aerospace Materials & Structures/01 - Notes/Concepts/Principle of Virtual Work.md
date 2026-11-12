---
title: "Principle of Virtual Work"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
tags: [sesa2028, structures, virtual-work]
status: lectured
---

# Principle of Virtual Work

To find one displacement, keep the real structure and apply a unit virtual load at the required point in the required direction. Then

$$
\delta=\int\left(
\frac{Nn}{EA}+\frac{Mm}{EI}+\frac{Tt}{GJ}
\right)dx.
$$

Uppercase quantities belong to the real system; lowercase quantities belong to the unit-load system. For a rotation, apply a unit moment.

The most common error is in setting up the integrals rather than evaluating them. Split the integral at every discontinuity in load, internal force, stiffness, member direction or support condition.

The PVW itself is an equilibrium statement: a system of forces in equilibrium does zero net work in any geometrically possible virtual displacement, so for a deformable body the external virtual work equals the internal virtual work, $\int_S\mathbf T^*\cdot\mathbf u\,dS=\int_V\boldsymbol\sigma^*:\boldsymbol\varepsilon\,dV$. Pairing the real displacements with a unit virtual load makes the left-hand side the displacement wanted. For the course's L-frame (cat house), the real and virtual moment diagrams below give a tip deflection of 42.9 mm for 50 mm timber and 8.47 mm for 75 mm timber.

![[structures_s8_l_frame_moments.png|800]]

## Related

- Topic: [[SESA2028 S8 - Virtual Work and Castigliano Theorems|S8]] (derivation, truss, beams, the L-frame worked in full)
- Concepts: [[Unit Load Method]] · [[Castigliano Second Theorem]] · [[Complementary Energy]]

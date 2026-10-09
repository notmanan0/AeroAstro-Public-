---
title: "SESA2028 S7 - Strain Energy and Conservation of Energy"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 7
tags: [sesa2028, structures, strain-energy, energy-methods]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]"]
next_topics: ["[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
key_concepts: ["[[Strain Energy]]", "[[Complementary Energy]]", "[[Maxwell-Betti Reciprocity]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL8 - Energy Methods 1 - Conservation of Energy.pdf", "02 - Sources/Structures Lectures/SL14 - EnergyMethods 1 - Strain Energy Review.pdf"]
---

# SESA2028 S7 - Strain Energy and Conservation of Energy

> [!abstract] Summary
> Energy methods replace the elastic curve by one or more integrals over internal actions. They are especially valuable when only one displacement or rotation is required, or when the structure is curved, framed or piecewise.

## 1. External work

For a load applied gradually to a linear elastic structure,

$$
W_{ext}=\frac12P\delta,
$$

because force rises from zero to $P$ while displacement rises from zero to $\delta$. For a gradually applied moment,

$$
W_{ext}=\frac12M\theta.
$$

Do not use the factor $1/2$ for a suddenly applied load or for a unit virtual load.

## 2. Internal strain energy

For a linearly elastic member,

$$
U=\int\left(
\frac{N^2}{2EA}
+\frac{M_y^2}{2EI_{yy}}
+\frac{M_z^2}{2EI_{zz}}
+\frac{T^2}{2GJ}
+\frac{V^2}{2\kappa GA}
\right)dx.
$$

In slender beams, bending energy usually dominates and

$$
U_b=\int\frac{M^2}{2EI}\,dx.
$$

![[Figures/structures_bending_strain_energy_density.png]]

The square is physically important: reversing the sign of a moment does not make stored energy negative.

## 3. Conservation of energy

For a linear elastic structure loaded gradually from zero,

$$
W_{ext}=U.
$$

This works directly when the load and desired displacement are work-conjugate and the deformation shape is fully represented by the internal energy expression. It gives one scalar equation; if several unknown displacements are present, virtual work or Castigliano is usually cleaner.

## 4. Curved members and frames

The same energy integral applies along the member centreline. For a circular arc,

$$
ds=R\,d\phi,
$$

so

$$
U_b=\int_{\phi_1}^{\phi_2}\frac{M(\phi)^2}{2EI}R\,d\phi.
$$

For a frame, split the integral by member and define a local coordinate on each. Keep axial energy if the loading directly stretches a member; omitting it is only justified after an order-of-magnitude comparison.

## 5. Complementary energy and reciprocity

In linear elasticity, strain energy and complementary energy are numerically equal. Maxwell-Betti reciprocity follows:

$$
\delta_{ij}=\delta_{ji},
$$

meaning the displacement at $i$ due to a unit load at $j$ equals the displacement at $j$ due to a unit load at $i$, provided the load directions correspond.

## 6. Checks

- Every energy term has units of work.
- With constant $EI$, the regions of largest $|M|$ dominate because the integrand contains $M^2$.
- If $P$ doubles in a linear structure, $U$ quadruples and $\delta$ doubles.
- If a result depends on the arbitrary sign chosen for $M$, something has gone wrong.

## Year 1 foundation
- Spring energy $\tfrac12k\,\Delta l^2$ and the work–energy principle in [[FEEG1002 D3 - Work, Energy and Power]]; the bar stiffness $k = EA/L$ in [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]; the rigid-body version in [[FEEG1002 D9 - Work and Energy for Rigid Bodies]].

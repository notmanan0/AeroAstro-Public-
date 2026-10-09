---
title: "SESA2028 S8 - Virtual Work and Castigliano Theorems"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 8
tags: [sesa2028, structures, virtual-work, castigliano]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
next_topics: ["[[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]"]
key_concepts: ["[[Principle of Virtual Work]]", "[[Unit Load Method]]", "[[Castigliano Second Theorem]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 1 - Energy Methods Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL9 - Energy methods 2 - Virtual Work and Strain Energy Solutions.pdf", "02 - Sources/Structures Lectures/SL15 - EnergyMethods 2 - The Pricinple of Virtual Work 1.pdf", "02 - Sources/Structures Lectures/SL16 - EnergyMethods 3 - The Pricinple of Virtual Work 2.pdf", "02 - Sources/Structures Lectures/SL17 - EnergyMethods 4 - The Pricinple of Virtual Work 3.pdf", "02 - Sources/Structures Lectures/SL18 - EnergyMethods 5 - Castigilianos Theorems.pdf"]
---

# SESA2028 S8 - Virtual Work and Castigliano Theorems

> [!abstract] Summary
> Virtual work finds one displacement by pairing the real internal-force field with a unit-load field. Castigliano differentiates the real strain energy with respect to a load. Both are systematic, sign-sensitive and far more general than memorised beam-deflection tables.

## 1. Unit-load method

Apply the real loading and find $N,M,T,V$. Remove it, apply a unit force at the required displacement in the required direction, and find $n,m,t,v$. Then

$$
\delta=\int\left(
\frac{Nn}{EA}
+\frac{Mm}{EI}
+\frac{Tt}{GJ}
+\frac{Vv}{\kappa GA}
\right)dx.
$$

For a rotation, apply a unit moment instead of a unit force.

![[Figures/structures_virtual_work_moment_fields.png]]

Unlike strain energy, the integrand $Mm$ can be negative. A negative result means the true displacement is opposite to the chosen unit-load direction.

## 2. Piecewise workflow

1. State the target displacement and positive direction.
2. Draw the real-load reactions and moment diagram.
3. Draw the unit-load system and its moment diagram.
4. Split at every load, support, hinge, property change or member junction.
5. Integrate $Mm/(EI)$ on each segment and sum.

If $EI$ is constant it may be factored out; do not do so when the section changes.

## 3. Castigliano's second theorem

For a linear elastic structure,

$$
\delta_i=\frac{\partial U}{\partial P_i},\qquad
\theta_i=\frac{\partial U}{\partial M_i}.
$$

With bending energy only,

$$
\delta_i=\int\frac{M}{EI}\frac{\partial M}{\partial P_i}\,dx.
$$

The derivative $\partial M/\partial P_i$ is exactly the unit-load moment field $m$, so Castigliano and virtual work are two views of the same linear calculation.

## 4. Dummy-load device

If no real load acts at the requested displacement, introduce a dummy load $Q$ there:

1. write $M(x;Q)$;
2. form $U(Q)$;
3. calculate $\partial U/\partial Q$;
4. set $Q=0$ only after differentiating.

Setting the dummy load to zero too early erases the required sensitivity.

## 5. Statically indeterminate structures

Choose a redundant reaction $R$ and write the total strain energy in terms of it. Compatibility supplies

$$
\frac{\partial U}{\partial R}=\delta_R,
$$

where $\delta_R$ is usually zero at an unyielding support. Solve for $R$, then recover the remaining reactions from equilibrium.

## 6. Choosing a method

| Need | Best first choice |
|---|---|
| one displacement with easy unit-load diagram | virtual work |
| several responses as functions of loads | Castigliano |
| redundant reaction | Castigliano/least work |
| complete elastic curve | direct integration |
| approximate deflection shape | Rayleigh-Ritz or assumed-shape energy |

> [!tip] Fast verification
> Take the limit of a parameter if possible. Removing an overhang, setting an axial load to zero or restoring symmetry should reduce the result to a familiar beam formula.

## Year 1 foundation
- Truss member forces and graphical (Williot) displacements in [[FEEG1002 A2 - Pin-Jointed Trusses]]; beam deflections by integration in [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]. Energy methods reproduce both.

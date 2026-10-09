---
title: "Principle of Minimum Total Potential Energy"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["PMPE", "minimum potential energy", "total potential energy", "virtual work", "strain energy"]
tags: [sesa2029, concept, fea, energy-methods]
status: complete
parent_lectures: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]", "[[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]]", "[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
related_concepts: ["[[Strong and Weak Forms]]", "[[Rayleigh-Ritz Method]]", "[[Matrix Displacement Method]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf", "02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Principle of Minimum Total Potential Energy

## Definition

> [!note] Definition
> Of all displacement fields that satisfy the displacement boundary conditions, the equilibrium one makes the total potential energy stationary (a minimum for stable equilibrium):
>
> $$\Pi = U+V,\qquad\delta\Pi = 0\;\Rightarrow\;\frac{\partial\Pi}{\partial d_i} = 0\ \ \forall i\;\Rightarrow\;\{F\} = [K]\{d\}$$
>
> $U$ is the strain energy and $V = -W$ is the potential of the applied loads.

## Explanation

- **Strain energy**: $U = \int_V\tfrac12\sigma\varepsilon\,dV$. The density $\tfrac12\sigma\varepsilon$ is the area under the stress–strain line. For a spring, $U = \tfrac12ku^2$.
- **Work potential**: $V = -\sum F_id_i$ (force × displacement, moment × rotation).
- **Virtual work**: a small admissible perturbation $\delta u$ does work $\delta W = F\delta u$, stored as $\delta U$ in a conservative system. Hence $\delta(U+V) = 0$.
- **Advantages over the strong form**:
  - only first derivatives are needed;
  - force BCs are automatic (they enter $V$);
  - trial fields need satisfy only the displacement BCs.
- It gives element matrices for any element: $[K] = \int[B]^T[D][B]\,dV$.

## Examples

- Spring: $\Pi = \tfrac12ku^2-Fu$, so $d\Pi/du = 0$ gives $F = ku$.

![[dam_total_potential_energy.png|500]]

- 2-node bar: $\Pi = \tfrac12k(u_j-u_i)^2-F_iu_i-F_ju_j$ leads to the bar matrix ([[SESA2029 FEA Worked Examples]]).

## Related

- Parent lectures: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] · [[SESA2029 B4 - Rayleigh-Ritz Method and Shape Functions]] · [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Related concepts: [[Strong and Weak Forms]] · [[Rayleigh-Ritz Method]] · [[Matrix Displacement Method]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf
- 02 - Sources/FEM Lectures/Lecture_6_Rayleigh-Ritz_&_Shape_function_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt

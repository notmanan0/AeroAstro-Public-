---
title: "Strong and Weak Forms"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["strong form", "weak form", "weighted residuals", "Galerkin method", "variational formulation"]
tags: [sesa2029, concept, fea, energy-methods]
status: complete
parent_lectures: ["[[SESA2029 B3 - Principle of Minimum Total Potential Energy]]"]
related_concepts: ["[[Principle of Minimum Total Potential Energy]]", "[[Rayleigh-Ritz Method]]", "[[Shape Functions]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Strong and Weak Forms

## Definition

> [!note] Definition
> - The **strong form** is the governing PDE (e.g. Navier–Cauchy equilibrium in displacement), required to hold at every point. It needs continuous second derivatives.
> - A **weak (integral) form** requires the equation to hold only in a weighted-average sense over the domain. It needs only first derivatives. It is obtained by weighted residuals (Galerkin) or equivalently from energy principles.

## Explanation

- The strong form is usually impossible to satisfy exactly except for the simplest geometries and BCs.
- **Weighted residual**: substitute a trial solution, form the residual $R$, and require $\int w_iR\,dV = 0$ for a set of weight functions. In **Galerkin**, the weights are the shape functions themselves.
- **FE approximation of the weak form**: interpolate the displacement from nodal values with shape functions. This reduces infinitely many unknowns to finitely many linear equations, $[K]\{d\} = \{F\}$. There is some loss of accuracy relative to the strong form, but a large gain in speed and generality.
- Weighted-residual and minimum-energy methods are both **variational** methods: they find stationary values of functionals.
- The CFD analogue is the finite-volume integral form, which also relaxes the pointwise PDE to cell averages.

## Examples

- Bar: the strong form $EAu'' + q = 0$ needs $u''$. The weak form $\int EA\,u'w'\,dx = \int qw\,dx+[\text{boundary}]$ needs only $u'$, and the force BCs appear naturally in the boundary term.

## Related

- Parent lectures: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- Related concepts: [[Principle of Minimum Total Potential Energy]] · [[Rayleigh-Ritz Method]] · [[Shape Functions]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_5_Mimimum_Potnetial_Energy.pdf
- 02 - Sources/FEM Lectures/FEA.txt

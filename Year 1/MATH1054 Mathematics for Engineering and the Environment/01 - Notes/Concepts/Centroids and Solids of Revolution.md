---
title: "Centroids and Solids of Revolution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Centroid", "Volume of revolution", "Centre of gravity", "Surface of revolution", "Arc length"]
tags: [math1054, concept, applications-of-integration]
status: complete
parent_lectures: ["[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Substitution]]", "[[RMS Value]]", "[[First Moment of Area]]", "[[Double Integrals and Change of Order]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.9", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# Centroids and Solids of Revolution

## Definition

> [!note] Definition
> For the region under $y=f(x)\ge0$ on $[a,b]$:
> $$A=\int y\,\mathrm dx,\quad\bar x=\frac1A\int xy\,\mathrm dx,\quad\bar y=\frac1{2A}\int y^2\,\mathrm dx,\quad V=\pi\int y^2\,\mathrm dx,\quad\bar x_V=\frac\pi V\int xy^2\,\mathrm dx$$

## Explanation
- $\bar y$ has the factor $\frac12$ because each vertical strip's own centroid is at mid-height.
- **Between curves**: the strip height is $y_u-y_l$; the centroid uses $\frac12(y_u^2-y_l^2)$; the volume is a washer, $\pi(y_u^2-y_l^2)$.
- **Arc length**: $\int\sqrt{1+y'^2}\,\mathrm dx$. **Surface area**: $2\pi\int y\sqrt{1+y'^2}\,\mathrm dx$.
- **Mean value**: $\frac1{b-a}\int f\,\mathrm dx$. **RMS**: $\sqrt{\frac1{b-a}\int f^2\,\mathrm dx}$ ([[RMS Value]]).
- Use symmetry first: solids of revolution have $\bar y=\bar z=0$.

## Examples
- $y=\sqrt{x-2}$ on $[2,5]$: area centroid $(3.8,\,0.650)$; the solid's centre of gravity is at $\bar x=4$ (Ex 8.65).
- Paraboloid surface: $\frac\pi6(5\sqrt5-1)$ (Ex 8.68).
- Between $y^2=4x$ and $y=2x$: area centroid $(\frac25,1)$, volume centroid $\bar x=\frac12$ (Ex 135).

## Related
- Topics: [[MATH1054 M09 - Integration II]]
- Concepts: [[Integration by Substitution]] · [[RMS Value]] · [[First Moment of Area]] · [[Double Integrals and Change of Order]]

## Sources
- James, Modern Engineering Mathematics (6th ed.) §8.9
- 02 - Sources/Formulae & Reference/Integration Formulae.md

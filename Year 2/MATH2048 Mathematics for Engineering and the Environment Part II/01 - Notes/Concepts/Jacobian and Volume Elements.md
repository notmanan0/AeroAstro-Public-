---
title: "Jacobian and Volume Elements"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Jacobian", "Spherical polar volume element", "Cylindrical coordinates", "Change of variables"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Divergence Theorem]]", "[[Flux Integrals]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf", "02 - Sources/Lectures/MATH2048 Lecture 29.txt"]
---

# Jacobian and Volume Elements

When a volume is described by parameters $(s,t,u)$, the volume element is $dV=|\det J|\,ds\,dt\,du$, where the **Jacobian** matrix $J$ holds the partial derivatives of $x$, $y$, $z$ with respect to the parameters.

The columns of $J$ are the edge vectors $\mathbf r_s$, $\mathbf r_t$, $\mathbf r_u$ of the small parallelepiped that a parameter box maps onto, and the determinant is that parallelepiped's volume. In cylindrical coordinates $(\rho,\phi,z)$, $\det J=\rho$, so $dV=\rho\,d\rho\,d\phi\,dz$. In spherical coordinates $(r,\theta,\phi)$ with $\theta$ measured from the north pole, $\det J=r^2\sin\theta$, so $dV=r^2\sin\theta\,dr\,d\theta\,d\phi$; deriving this is a recurring exam part. The two-dimensional analogue is the surface element $|\mathbf r_s\times\mathbf r_t|\,ds\,dt$ of [[Flux Integrals]].

The point of changing variables is to make the limits simple: a ball, a cone or a wedge becomes a box in the new coordinates, and the integral often separates into a product of single integrals, as in $V=\frac{R^3\beta}3(1-\cos\alpha)$ for the spherical wedge $0\leq\theta\leq\alpha$, $0\leq\phi\leq\beta$ (2024/25 B2). Finite-element solvers use the same idea to map each element onto a reference element.

## Related

- Derivation: [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem#1. Volume integrals and the Jacobian (L29)|VC5 §1]]
- [[Flux Integrals]] · [[Divergence Theorem]]

---
title: "Boundary Value Problems"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 1: Ordinary Differential Equations"
aliases: ["BVP", "Fredholm alternative", "Dirichlet condition", "Neumann condition", "Robin condition"]
tags: [math2048, concept, odes]
status: complete
parent_lectures: ["[[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]"]
related_concepts: ["[[ODE Eigenvalue Problems]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf"]
---

# Boundary Value Problems

## Definition

> [!note] Definition
> A **BVP** is an ODE plus conditions at **two different points**, e.g. $a_0y(x_0)+b_0y'(x_0)=\alpha$ and $a_1y(x_1)+b_1y'(x_1)=\beta$. By contrast, an IVP gives $y$ and $y'$ at one point.

## Explanation
**Method**: find the general solution first, then impose the BCs. This gives a $2\times2$ linear system for $c_1,c_2$.

| System | Outcome |
|---|---|
| $\det\neq0$ | unique solution |
| $\det=0$, inconsistent | no solution |
| $\det=0$, consistent | one-parameter family |

**Fredholm alternative**: the solution is unique iff the fully homogeneous problem has only $y\equiv0$. The failure cases happen exactly when the homogeneous problem has an eigenfunction.

**BC types**

| Name | Condition |
|---|---|
| Dirichlet | $y$ given |
| Neumann | $y'$ given |
| Robin | $y+cy'$ given |

## Examples
- $y''+y=0$: $y(0)=0$, $y(\pi/2)=1$ gives the unique solution $\sin x$. $y(0)=0$, $y(\pi)=1$ has no solution. $y(0)=y(\pi)=0$ gives the family $c\sin x$.
- $y''+\tfrac14y=1$: all four outcomes appear in PS2 Q2 ([[MATH2048 Problem Sheets 1-2 Solutions - ODEs]]).

## Related
- [[ODE Eigenvalue Problems]] · [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]]

## Sources
- Lecture 3; Appendix L1–2; Lecture Notes §1.2

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
sources: ["02 - Sources/Lectures & Problem Sheets/ODEs/Lecture3_ODE.pdf", "02 - Sources/Lectures/MATH2048 Lecture 3.txt"]
---

# Boundary Value Problems

A **boundary value problem** is an ODE with its conditions given at two different points, such as $a_0y(x_0)+b_0y'(x_0)=\alpha$ and $a_1y(x_1)+b_1y'(x_1)=\beta$, rather than the value and slope at one point as in an initial value problem.

The method is to find the general solution first and impose the conditions last, which gives a $2\times2$ linear system for $c_1$ and $c_2$. Unlike an initial value problem, it need not have a unique solution. If the system's determinant is non-zero the solution is unique; if it is zero the two conditions are not independent, and the data either contradict each other (no solution) or agree (a one-parameter family). The lecture notes call this the Fredholm alternative: the solution is unique exactly when the fully homogeneous problem has only $y\equiv0$, so the failures happen when the homogeneous problem has an eigenfunction.

The lecture shows all three outcomes for $y''+y=0$ with $y(0)=0$, whose solutions are all $c_2\sin x$. Adding $y(\pi/2)=1$ gives the unique solution $\sin x$; $y(\pi)=1$ has no solution, because every sine returns to zero at $\pi$; and $y(\pi)=0$ is satisfied by every $c_2\sin x$. Problem Sheet 2 Q2 does the same for $y''+\tfrac14y=1$.

![[m2048_ode_bvp_outcomes.png|800]]

The boundary conditions themselves come in three types: Dirichlet ($y$ given), Neumann ($y'$ given) and Robin ($y+cy'$ given).

## Related

- [[MATH2048 ODE3 - Boundary Value and Eigenvalue Problems]] · [[ODE Eigenvalue Problems]]

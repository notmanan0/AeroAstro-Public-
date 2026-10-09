---
title: "MATH1054 M14 - Vectors I"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 14
tags:
  - math1054
  - vectors
  - dot-product
  - cross-product
aliases: ["MATH1054 Module 14", "Vectors I"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M15 - Vectors II]]"]
key_concepts: ["[[Vector Algebra and Components]]", "[[Scalar (Dot) Product]]", "[[Vector (Cross) Product]]"]
tutorial_sheets: ["[[MATH1054 M14 Solutions - Vectors I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 14)", "02 - Sources/Modern Engineering Mathematics.pdf (§4.2–4.3)"]
---

# MATH1054 M14 - Vectors I

> [!abstract] Summary
> A vector has magnitude and direction. In components it is simply a triple $(a_1,a_2,a_3)$. This module covers:
> - addition, which works like forces and relative velocities;
> - the **dot product**, a scalar that measures alignment and gives work, components and angles;
> - the **cross product**, a vector perpendicular to both inputs, which gives areas, moments and rotational velocity.
>
> This is the language of all of FEEG1002 statics and dynamics.

## Key Concepts
- [[Vector Algebra and Components]] · [[Scalar (Dot) Product]] · [[Vector (Cross) Product]]

---

## 1. Components, magnitude and direction (James §4.2)
$$
\mathbf a=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k,\qquad|\mathbf a|=\sqrt{a_1^2+a_2^2+a_3^2},\qquad\hat{\mathbf a}=\frac{\mathbf a}{|\mathbf a|}
$$
- **Direction cosines**: $(l,m,n)=\hat{\mathbf a}$, with $l^2+m^2+n^2=1$.
- **Position vectors**: $\vec{\mathrm{AB}}=\mathbf b-\mathbf a$ (end minus start). A closed loop sums to $\mathbf0$.
- **Collinear points**: $\vec{\mathrm{PQ}}=\lambda\vec{\mathrm{QR}}$.

## 2. Relative velocity
The **apparent** velocity of B seen by A is $\mathbf v_B-\mathbf v_A$. A wind "from the NW" blows *towards* the SE.

![[m1054_relative_velocity.png|760]]

## 3. The scalar (dot) product (James §4.3.1)
$$
\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta=a_1b_1+a_2b_2+a_3b_3
$$
| Use | Formula |
|---|---|
| Angle between vectors | $\cos\theta=\dfrac{\mathbf a\cdot\mathbf b}{\lvert\mathbf a\rvert\lvert\mathbf b\rvert}$ |
| Perpendicular test | $\mathbf a\cdot\mathbf b=0$ |
| Component (resolved part) of $\mathbf F$ along $\mathbf u$ | $\mathbf F\cdot\hat{\mathbf u}$ |
| Work done by a constant force | $W=\mathbf F\cdot\mathbf d$ |

The dot product is commutative and distributive. But you **cannot cancel**: $\mathbf a\cdot\mathbf b=\mathbf a\cdot\mathbf c$ only means $\mathbf a\perp(\mathbf b-\mathbf c)$.

## 4. The vector (cross) product (James §4.3.2)
$$
\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix},\qquad|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta
$$
- The result is perpendicular to both $\mathbf a$ and $\mathbf b$, with its sense given by the **right-hand rule**.
- **Anti-commutative**: $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$. **Not associative** (Ex 4.24).
- $\mathbf a\times\mathbf b=\mathbf0$ iff $\mathbf a\parallel\mathbf b$.

| Use | Formula |
|---|---|
| Unit normal to a plane | $\pm\dfrac{\mathbf a\times\mathbf b}{\lvert\mathbf a\times\mathbf b\rvert}$ |
| Area of a parallelogram / triangle | $\lvert\mathbf a\times\mathbf b\rvert$ / $\frac12\lvert\mathbf a\times\mathbf b\rvert$ |
| Moment of $\mathbf F$ acting at P, about A | $\mathbf M_{\mathrm A}=\vec{\mathrm{AP}}\times\mathbf F$; its components are the moments about axes through A |
| Velocity of a point on a rotating body | $\mathbf v=\boldsymbol\omega\times\vec{\mathrm{AP}}$, with A on the axis |

**The triple vector product** ("BAC-CAB"):
$$
\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c
$$

> [!tip] Cross-product arithmetic
> Write the vectors twice, side by side ($a_1a_2a_3a_1a_2$), then take the "cross" products of adjacent pairs. **Always check** that the answer dots to zero with both inputs. For example, $(10,9,7)\cdot(2,-3,1)=20-27+7=0$ ✔.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M14 Solutions - Vectors I]]
- Next: [[MATH1054 M15 - Vectors II]] (triple products, lines, planes, vector calculus)
- Applied in FEEG1002: [[Free Body Diagram and Equilibrium]], [[Relative Velocity Equation for Rigid Bodies]]

## Sources
- MATH1054 Module Booklet, Module 14; James §4.2–4.3

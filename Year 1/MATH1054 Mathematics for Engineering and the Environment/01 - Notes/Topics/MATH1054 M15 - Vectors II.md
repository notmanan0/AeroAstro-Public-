---
title: "MATH1054 M15 - Vectors II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 4: Vectors and Matrices"
order: 15
tags:
  - math1054
  - vectors
  - lines-and-planes
  - vector-calculus
aliases: ["MATH1054 Module 15", "Vectors II"]
date: 2026-09-27
status: complete
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M14 - Vectors I]]"]
next_topics: ["[[MATH1054 M16 - Matrices I]]"]
key_concepts: ["[[Scalar Triple Product]]", "[[Equations of Lines and Planes]]", "[[Differentiation of Vectors]]"]
tutorial_sheets: ["[[MATH1054 M15 Solutions - Vectors II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 15)", "02 - Sources/Modern Engineering Mathematics.pdf (§4.3.3–4.4, §9.5)"]
---

# MATH1054 M15 - Vectors II

> [!abstract] Summary
> This module covers three things:
> 1. **Triple products**. $\mathbf a\cdot(\mathbf b\times\mathbf c)$ is a signed volume and gives the coplanarity test. $\mathbf a\times(\mathbf b\times\mathbf c)$ satisfies the BAC−CAB identity.
> 2. **The geometry of lines and planes** in 3D: equations, intersections, angles and distances.
> 3. **Vector functions of time**: differentiate and integrate component-wise to get velocity, acceleration and trajectories.

## Key Concepts
- [[Scalar Triple Product]] · [[Equations of Lines and Planes]] · [[Differentiation of Vectors]]

---

## 1. Triple products (James §4.3.3–4.3.4)

$$
[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c)=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix}
$$

- $|[\mathbf a,\mathbf b,\mathbf c]|$ is the **volume of the parallelepiped** on the three vectors.
- $[\mathbf a,\mathbf b,\mathbf c]=0$ iff the vectors are **coplanar** (linearly dependent).
- Cyclic shifts don't change it; swapping two vectors flips its sign.
- **Triple vector product**: $\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$.

## 2. Straight lines (James §4.4.1)

$$
\mathbf r=\mathbf a+t\mathbf d\qquad\Longleftrightarrow\qquad\frac{x-a_1}{d_1}=\frac{y-a_2}{d_2}=\frac{z-a_3}{d_3}
$$

**Do two lines intersect?** Equate the two vector equations to get three equations in the two parameters $s$ and $t$. Solve two of them, then **check the third**.
- If it holds, the lines intersect.
- If it fails, they are **skew** (or parallel, if $\mathbf d_1\parallel\mathbf d_2$).

**Shortest distance between skew lines**:

$$
d=\frac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|}
$$

The common perpendicular joins the feet P and Q, found from $\vec{\mathrm{PQ}}\cdot\mathbf d_1=\vec{\mathrm{PQ}}\cdot\mathbf d_2=0$.

![[m1054_skew_lines.png|600]]

## 3. Planes (James §4.4.2)

$$
\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n\quad\Longleftrightarrow\quad n_1x+n_2y+n_3z=d
$$

- **Through three points**: $\mathbf n=(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)$.
- **Line meets plane**: substitute $\mathbf r=\mathbf a+t\mathbf d$ and solve for $t$.
- **Two planes meet in a line**: its direction is $\mathbf n_1\times\mathbf n_2$. For a point on it, set one coordinate to a convenient value.
- **Distance from a point to a plane**:

$$
D=\frac{|n_1x_0+n_2y_0+n_3z_0-d|}{|\mathbf n|}
$$

## 4. Vector calculus in time (James §9.5)
Differentiate and integrate each component. The product rules still hold:

$$
\frac{\mathrm d}{\mathrm dt}(\mathbf a\cdot\mathbf b)=\dot{\mathbf a}\cdot\mathbf b+\mathbf a\cdot\dot{\mathbf b},\qquad\frac{\mathrm d}{\mathrm dt}(\mathbf a\times\mathbf b)=\dot{\mathbf a}\times\mathbf b+\mathbf a\times\dot{\mathbf b}\ \text{(keep the order)}
$$

- If $|\mathbf a|$ is constant, then $\mathbf a\perp\dot{\mathbf a}$. This is why circular motion has its velocity along the tangent.
- $\big|\dot{\mathbf r}\big|$ (speed) $\neq\frac{\mathrm d}{\mathrm dt}|\mathbf r|$ (rate of change of distance).
- **Polar components**:

$$
\dot{\mathbf r}=\dot r\hat{\mathbf r}+r\dot\theta\hat{\boldsymbol\theta},\qquad\ddot{\mathbf r}=(\ddot r-r\dot\theta^2)\hat{\mathbf r}+(2\dot r\dot\theta+r\ddot\theta)\hat{\boldsymbol\theta}
$$

- **Trajectories**: integrate the acceleration twice, using the initial position and velocity for the two vector constants. Projectiles give parabolas; Booklet Exercise A gives a helix.

## Links
- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M15 Solutions - Vectors II]]
- Prev: [[MATH1054 M14 - Vectors I]] · Next: [[MATH1054 M16 - Matrices I]] (the determinant, generalised)
- Applied: [[Projectile Motion]], [[Normal and Tangential Coordinates]] (FEEG1002); MATH2048 [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]

## Sources
- MATH1054 Module Booklet, Module 15; James §4.3.3–4.4, §9.5

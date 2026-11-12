---
title: "Vector (Cross) Product"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Cross product", "Vector product", "Moment of a force"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M14 - Vectors I]]", "[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Scalar (Dot) Product]]", "[[Scalar Triple Product]]", "[[Principle of Angular Impulse and Momentum]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.2.10", "MATH1054 Module Booklet, Module 14"]
---

# Vector (Cross) Product

The vector product of $\mathbf a$ and $\mathbf b$ is the vector $\mathbf a\times\mathbf b=|\mathbf a||\mathbf b|\sin\theta\,\hat{\mathbf n}$, where $\hat{\mathbf n}$ is the unit normal to both such that $\mathbf a$, $\mathbf b$, $\hat{\mathbf n}$ form a right-handed set (curl the right hand's fingers from $\mathbf a$ to $\mathbf b$; the thumb gives $\hat{\mathbf n}$).

Reversing the order reverses the rotation, so $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$, and parallel vectors give $\mathbf0$. Applied to the unit vectors, the definition gives $\mathbf i\times\mathbf j=\mathbf k$, $\mathbf j\times\mathbf k=\mathbf i$, $\mathbf k\times\mathbf i=\mathbf j$ (cyclic order positive, the reverse negative) and $\mathbf i\times\mathbf i=\mathbf0$. Expanding $(a_1\mathbf i+a_2\mathbf j+a_3\mathbf k)\times(b_1\mathbf i+b_2\mathbf j+b_3\mathbf k)$ by distributivity into nine terms and using that table gives the component form, remembered as a determinant:

$$
\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}=(a_2b_3-a_3b_2,\ a_3b_1-a_1b_3,\ a_1b_2-a_2b_1).
$$

The component form can be checked against the definition. Dotting it with $\mathbf a$ or $\mathbf b$ gives six terms that cancel in pairs, so it is perpendicular to both. Squaring and adding its components gives Lagrange's identity, $|\mathbf a\times\mathbf b|^2=|\mathbf a|^2|\mathbf b|^2-(\mathbf a\cdot\mathbf b)^2=|\mathbf a|^2|\mathbf b|^2(1-\cos^2\theta)$, so $|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta$, using $\sin\theta\ge0$ on $[0,\pi]$.

The magnitude is base times height of the parallelogram on $\mathbf a$ and $\mathbf b$, which gives the four standard uses: the unit normal to a plane, $\pm(\mathbf a\times\mathbf b)/|\mathbf a\times\mathbf b|$; the area of a parallelogram, $|\mathbf a\times\mathbf b|$, and of a triangle, half that; the moment about A of a force $\mathbf F$ through P, $\mathbf M_{\mathrm A}=\overrightarrow{\mathrm{AP}}\times\mathbf F$, of size force times perpendicular distance, whose components are the moments about axes through A parallel to the coordinate axes; and the velocity of a point P of a body rotating with angular velocity $\boldsymbol\omega$ about an axis through A, $\mathbf v=\boldsymbol\omega\times\overrightarrow{\mathrm{AP}}$.

The product is not associative. Expanding by components gives the triple vector product, "BAC minus CAB":

$$
\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf a\cdot\mathbf b)\,\mathbf c,\qquad(\mathbf a\times\mathbf b)\times\mathbf c=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf b\cdot\mathbf c)\,\mathbf a .
$$

For the triangle $\mathrm P(1,3,2)$, $\mathrm Q(-2,1,3)$, $\mathrm R(3,-2,-1)$ (James Example 4.26), $\overrightarrow{\mathrm{PQ}}\times\overrightarrow{\mathrm{PR}}=(-3,-2,1)\times(2,-5,-3)=(11,-7,19)$ and the area is $\frac12\sqrt{531}=\frac{3\sqrt{59}}2\approx11.52$. A force of 4 units along $(4,5,-2)$ through $(2,3,-5)$ has moment $\frac4{3\sqrt5}(8,-6,1)$ about $(1,2,-3)$ (Example 4.28), and a body turning at 5 rad/s about $(1,3,-2)$ through $(2,3,-1)$ gives the point $(-2,3,1)$ the velocity $\frac{30}{\sqrt{14}}(1,1,2)$ (Example 4.29).

The traps are order and sign. The moment is $\mathbf r\times\mathbf F$ and the velocity $\boldsymbol\omega\times\mathbf r$; the reverse order gives the opposite vector. The middle ($\mathbf j$) term of the determinant carries a minus sign. A quick check catches both kinds of slip: the answer must dot to zero with both inputs.

## Related

- Topics: [[MATH1054 M14 - Vectors I]] (derivations and worked examples) · [[MATH1054 M15 - Vectors II]] · [[FEEG1002 D5 - Angular Impulse and Momentum]] · [[FEEG1002 D7 - Kinematics of Rigid Bodies]]
- Concepts: [[Scalar (Dot) Product]] · [[Scalar Triple Product]] · [[Determinants and Cofactors]] · [[Principle of Angular Impulse and Momentum]] · [[Relative Velocity Equation for Rigid Bodies]] · [[Cross-Product Matrix]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §4.2.10 (and the triple vector product of Example 4.24); MATH1054 Module Booklet, Module 14

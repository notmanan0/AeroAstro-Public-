---
title: "Scalar Triple Product"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Triple product", "Box product", "Coplanarity test"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector (Cross) Product]]", "[[Determinants and Cofactors]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.2.12", "MATH1054 Module Booklet, Module 15"]
---

# Scalar Triple Product

The scalar triple product of three vectors is the scalar $[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c)$. In components it is the $3\times3$ determinant whose rows are $\mathbf a$, $\mathbf b$ and $\mathbf c$, and its absolute value is the volume of the parallelepiped with those three vectors as edges.

The determinant form comes from dotting $\mathbf a$ into the components of the [[Vector (Cross) Product|cross product]]. Each component of $\mathbf b\times\mathbf c$ is a $2\times2$ determinant, so

$$
\begin{aligned}
\mathbf a\cdot(\mathbf b\times\mathbf c)&=a_1(b_2c_3-b_3c_2)-a_2(b_1c_3-b_3c_1)+a_3(b_1c_2-b_2c_1)\\
&=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix},
\end{aligned}
$$

the expansion along the first row ([[Determinants and Cofactors]]). The volume follows from base times height. The parallelogram on $\mathbf b$ and $\mathbf c$ has area $|\mathbf b\times\mathbf c|$, and the height of the solid is the component of $\mathbf a$ along the unit normal $\hat{\mathbf n}=(\mathbf b\times\mathbf c)/|\mathbf b\times\mathbf c|$, so $V=|\mathbf b\times\mathbf c|\,|\mathbf a\cdot\hat{\mathbf n}|=|\mathbf a\cdot(\mathbf b\times\mathbf c)|$. The sign without the modulus is positive when $\mathbf a,\mathbf b,\mathbf c$ form a right-handed set and negative otherwise.

Because swapping two rows of a determinant changes its sign, a cyclic shift (two swaps) leaves the product unchanged and a single swap reverses it:

$$
\mathbf a\cdot(\mathbf b\times\mathbf c)=\mathbf b\cdot(\mathbf c\times\mathbf a)=\mathbf c\cdot(\mathbf a\times\mathbf b)=-\mathbf a\cdot(\mathbf c\times\mathbf b).
$$

The last cyclic form, read as $(\mathbf a\times\mathbf b)\cdot\mathbf c$, shows that the dot and the cross can be interchanged, so $(\mathbf a\times\mathbf b)\cdot\mathbf c$ (the form used in James) is the same number. A product with a repeated vector has two equal rows and is zero.

The most used consequence is the coplanarity test. Three vectors are coplanar (linearly dependent) exactly when the parallelepiped is flat, i.e. $\mathbf a\cdot(\mathbf b\times\mathbf c)=0$: either $\mathbf b\times\mathbf c=\mathbf 0$, or $\mathbf a$ is perpendicular to the normal of the plane of $\mathbf b$ and $\mathbf c$ and so lies in it. The same idea decides whether two lines meet and gives the numerator of the skew-line distance, $d=|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|/|\mathbf d_1\times\mathbf d_2|$ ([[Equations of Lines and Planes]]).

For example, $(2,-1,1)$, $(1,2,-3)$ and $(3,\lambda,5)$ are coplanar when

$$
\begin{aligned}
\begin{vmatrix}2&-1&1\\1&2&-3\\3&\lambda&5\end{vmatrix}&=2(10+3\lambda)+(5+9)+(\lambda-6)\\
&=7\lambda+28=0,
\end{aligned}
$$

so $\lambda=-4$ (James Example 4.31). The parallelepiped with edges $(2,-3,4)$, $(1,3,-1)$ and $(3,-1,2)$ gives the determinant $2(5)+3(5)+4(-10)=-15$, so its volume is 15 (Exercise 57).

The common trap is reporting $-15$ as a volume. The determinant carries the handedness of the ordering, and a volume is its absolute value, $V=|\mathbf a\cdot(\mathbf b\times\mathbf c)|$.

## Related

- Topics: [[MATH1054 M15 - Vectors II]] (derivations and all work-scheme examples) · [[MATH1054 M14 - Vectors I]] · [[MATH1054 M16 - Matrices I]]
- Concepts: [[Vector (Cross) Product]] · [[Scalar (Dot) Product]] · [[Determinants and Cofactors]] · [[Equations of Lines and Planes]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §4.2.12; MATH1054 Module Booklet, Module 15 work scheme, items 1–2

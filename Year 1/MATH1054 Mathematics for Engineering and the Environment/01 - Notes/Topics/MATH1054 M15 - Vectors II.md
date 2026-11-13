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
status: lectured
coverage: "Module Booklet Module 15 work scheme (items 1–8, Exercise A, Specimen Test 15); James §4.2.12 triple products, §4.3.1 lines, §4.3.3 planes, §9.5.1 differentiation and integration of vectors"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M14 - Vectors I]]"]
next_topics: ["[[MATH1054 M16 - Matrices I]]"]
key_concepts: ["[[Scalar Triple Product]]", "[[Equations of Lines and Planes]]", "[[Differentiation of Vectors]]"]
tutorial_sheets: ["[[MATH1054 M15 Solutions - Vectors II]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 15)", "02 - Sources/Modern Engineering Mathematics.pdf (§4.2.12–4.3.4, §9.5)"]
---

# MATH1054 M15 - Vectors II

> [!abstract] Summary
> The scalar triple product $\mathbf a\cdot(\mathbf b\times\mathbf c)$ is the $3\times3$ determinant of the three vectors' components and, up to sign, the volume of the parallelepiped they span, so it is zero exactly when the vectors are coplanar; the triple vector product expands as $\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$. Lines are written $\mathbf r=\mathbf a+t\mathbf d$ and planes $\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n$, and every intersection and distance question then reduces to dot and cross products, including the skew-line distance $|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|/|\mathbf d_1\times\mathbf d_2|$ and the point–plane distance $|\mathbf n\cdot\mathbf p_0-p|/|\mathbf n|$. A vector function of time is differentiated and integrated component by component, which gives velocity, acceleration and paths, and the product rules for $\mathbf a\cdot\mathbf b$ and $\mathbf a\times\mathbf b$ hold as long as the order of a cross product is kept.

> [!summary]- Exam use: quick path
> - **Use it when:** a question asks whether three vectors are coplanar or for a volume; for the equation of a line or a plane, where lines and planes meet, or a distance between a point, a line and a plane; or for velocity, acceleration or the path from a position or acceleration vector given as a function of $t$.
> - **Assumptions:** right-handed Cartesian axes ($\mathbf i\times\mathbf j=\mathbf k$); direction and normal vectors non-zero; for the calculus, components differentiable in $t$ and $\mathbf i,\mathbf j,\mathbf k$ fixed.
> - **Method:** 1. Write each line as point + parameter × direction and each plane as $\mathbf r\cdot\mathbf n=p$. 2. Get normals and common perpendiculars from cross products: $(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)$, $\mathbf d_1\times\mathbf d_2$, $\mathbf n_1\times\mathbf n_2$. 3. For an intersection, equate the two position vectors (or put the line into the plane) and solve; for two lines, solve two components and check the third. 4. For a distance, project a vector joining the two objects onto a unit normal, $D=|\overrightarrow{PQ}\cdot\hat{\mathbf n}|$. 5. For motion, differentiate or integrate each component, with one vector constant per integration fitted to the initial data.
> - **Common mistakes:** not checking the third component when two lines are equated, so skew lines appear to meet; dropping the modulus, so a volume or distance comes out negative.
> - **Practise:** [[#Skew lines and the common perpendicular]] · [[MATH1054 M15 Solutions - Vectors II#Exercise 72: Shortest distance between the lines|Exercise 72]]

A pair of vectors has two products ([[MATH1054 M14 - Vectors I|Module 14]]): the [[Scalar (Dot) Product|dot product]], which projects one vector onto another, and the [[Vector (Cross) Product|cross product]], which gives a vector perpendicular to both with length equal to the area of the parallelogram they span. Combining the two products over three vectors gives the triple products. The scalar triple product $\mathbf a\cdot(\mathbf b\times\mathbf c)$ is a base area times a height, so it is a volume, and it is zero exactly when the three vectors lie in one plane. The triple vector product $\mathbf a\times(\mathbf b\times\mathbf c)$ reduces to a combination of $\mathbf b$ and $\mathbf c$, which is the identity used whenever two cross products are nested.

The same two products describe straight lines and planes in three dimensions without coordinates-by-coordinates geometry. A line is a point plus a multiple of a direction; a plane is the set of points whose displacement from one known point is perpendicular to a normal. Every distance between points, lines and planes is found the same way: take any vector joining the two objects and keep only its component along the right unit normal. The engineering versions are the closest approach of two straight flight paths or pipelines (a skew-line distance), the clearance of a point from a flat surface (a point–plane distance) and the lattice planes of a crystal ([[Miller Indices for Planes and Directions]]). Where three planes meet is a set of three linear equations, which [[MATH1054 M17 - Matrices II|Module 17]] solves by elimination, and the determinant that appears here as a volume is generalised in [[MATH1054 M16 - Matrices I|Module 16]].

Vectors can also depend on time. Because $\mathbf i$, $\mathbf j$ and $\mathbf k$ are fixed, the derivative of a position vector is the vector of the derivatives of its components, and that derivative is the velocity. The dot- and cross-product rules lead to the facts used throughout dynamics: a vector of constant length is perpendicular to its own derivative, so circular motion has its velocity along the tangent, and in polar coordinates the rotating unit vectors produce the centripetal term $-r\dot\theta^2$ and the Coriolis term $2\dot r\dot\theta$ that [[FEEG1002 D2 - Curvilinear Motion]] and orbital mechanics rely on.

---

## 1. The scalar triple product

For three vectors $\mathbf a$, $\mathbf b$ and $\mathbf c$ the **scalar triple product** is the scalar

$$
[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c).
$$

The brackets can be dropped, because $(\mathbf a\cdot\mathbf b)\times\mathbf c$ is the cross product of a scalar with a vector and means nothing, so $\mathbf a\cdot\mathbf b\times\mathbf c$ has only one reading. The same quantity is also written $(\mathbf a\times\mathbf b)\cdot\mathbf c$, the form used in James; the two are equal, as shown below.

### Determinant form

Start from the components of the cross product ([[Vector (Cross) Product]]):

$$
\mathbf b\times\mathbf c=(b_2c_3-b_3c_2)\,\mathbf i+(b_3c_1-b_1c_3)\,\mathbf j+(b_1c_2-b_2c_1)\,\mathbf k .
$$

Take the dot product with $\mathbf a=(a_1,a_2,a_3)$, then write each bracket as a $2\times2$ determinant (the middle one changes sign, because $b_3c_1-b_1c_3=-(b_1c_3-b_3c_1)$), then recognise the expansion along the first row of a $3\times3$ determinant ([[Determinants and Cofactors]]):

$$
\begin{aligned}
\mathbf a\cdot(\mathbf b\times\mathbf c)&=a_1(b_2c_3-b_3c_2)+a_2(b_3c_1-b_1c_3)+a_3(b_1c_2-b_2c_1)\\
&=a_1\begin{vmatrix}b_2&b_3\\c_2&c_3\end{vmatrix}-a_2\begin{vmatrix}b_1&b_3\\c_1&c_3\end{vmatrix}+a_3\begin{vmatrix}b_1&b_2\\c_1&c_2\end{vmatrix}\\
&=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix}.
\end{aligned}
$$

Multiplied out in full this is $a_1b_2c_3-a_1b_3c_2-a_2b_1c_3+a_2b_3c_1+a_3b_1c_2-a_3b_2c_1$ (James equation 4.12). In practice, write the three vectors as the rows of a determinant in the order they appear and expand along the row with the most zeros.

### Volume of the parallelepiped

Take $\mathbf b$ and $\mathbf c$ as two edges of the base of a parallelepiped and $\mathbf a$ as the slanting third edge. The base is a parallelogram of area $|\mathbf b\times\mathbf c|$, and $\hat{\mathbf n}=(\mathbf b\times\mathbf c)/|\mathbf b\times\mathbf c|$ is the unit normal to it. The height of the solid, measured along that normal, is the size of the component of $\mathbf a$ along $\hat{\mathbf n}$, that is $h=|\mathbf a\cdot\hat{\mathbf n}|=|\mathbf a|\,|\cos\varphi|$ with $\varphi$ the angle between $\mathbf a$ and $\hat{\mathbf n}$. Volume is base area times height:

$$
\begin{aligned}
V&=|\mathbf b\times\mathbf c|\;|\mathbf a\cdot\hat{\mathbf n}|\\
&=|\mathbf b\times\mathbf c|\;\frac{|\mathbf a\cdot(\mathbf b\times\mathbf c)|}{|\mathbf b\times\mathbf c|}\\
&=|\mathbf a\cdot(\mathbf b\times\mathbf c)| .
\end{aligned}
$$

The modulus matters. $\mathbf b\times\mathbf c$ can point to either side of the base, so $\mathbf a\cdot(\mathbf b\times\mathbf c)$ is positive when $\mathbf a$ is on the same side as $\mathbf b\times\mathbf c$ (the ordered set $\mathbf a,\mathbf b,\mathbf c$ is right-handed) and negative when it is on the other side. The volume is always the absolute value.

![[m1054_m15_parallelepiped.png|700]]

In the figure, $\mathbf b=(3,0,0)$ and $\mathbf c=(1,0,-2)$ in axes with $y$ up and $z$ towards the viewer, so $\mathbf b\times\mathbf c=(0,6,0)$ and the base area is 6. The edge $\mathbf a=(0.8,2,-0.6)$ has height $\mathbf a\cdot\hat{\mathbf n}=2$ above the base, and $\mathbf a\cdot(\mathbf b\times\mathbf c)=2\times6=12$ is the volume.

### Cyclic order and swapping two vectors

Swapping two rows of a determinant changes its sign. A cyclic shift $\mathbf a,\mathbf b,\mathbf c\to\mathbf b,\mathbf c,\mathbf a$ is two swaps (first rows 1 and 2, then rows 2 and 3), so it leaves the value unchanged:

$$
\begin{aligned}
\mathbf a\cdot(\mathbf b\times\mathbf c)&=\begin{vmatrix}\mathbf a\\\mathbf b\\\mathbf c\end{vmatrix}
=-\begin{vmatrix}\mathbf b\\\mathbf a\\\mathbf c\end{vmatrix}
=\begin{vmatrix}\mathbf b\\\mathbf c\\\mathbf a\end{vmatrix}=\mathbf b\cdot(\mathbf c\times\mathbf a),
\end{aligned}
$$

where each row stands for the components of that vector. Repeating the shift gives the full cyclic rule (James 4.11),

$$
\mathbf a\cdot(\mathbf b\times\mathbf c)=\mathbf b\cdot(\mathbf c\times\mathbf a)=\mathbf c\cdot(\mathbf a\times\mathbf b),
$$

and any single swap flips the sign, e.g. $\mathbf a\cdot(\mathbf c\times\mathbf b)=-\mathbf a\cdot(\mathbf b\times\mathbf c)$. Because the dot product is commutative, $\mathbf c\cdot(\mathbf a\times\mathbf b)=(\mathbf a\times\mathbf b)\cdot\mathbf c$, so the last equality says $\mathbf a\cdot(\mathbf b\times\mathbf c)=(\mathbf a\times\mathbf b)\cdot\mathbf c$: the dot and the cross can be interchanged, which is why James's form and this one agree. Geometrically, all of these orderings measure the same parallelepiped. A triple product with a repeated vector has two equal rows and is zero, so $\mathbf a\cdot(\mathbf a\times\mathbf b)=0$, which restates that $\mathbf a\times\mathbf b$ is perpendicular to $\mathbf a$.

### The coplanarity test

If $\mathbf a$, $\mathbf b$ and $\mathbf c$ lie in one plane, the parallelepiped is flat and its volume is zero. The converse also holds. If $\mathbf a\cdot(\mathbf b\times\mathbf c)=0$, then either $\mathbf b\times\mathbf c=\mathbf 0$, in which case $\mathbf b$ and $\mathbf c$ are parallel (or one is zero) and the three vectors certainly lie in a plane, or $\mathbf a$ is perpendicular to the normal $\mathbf b\times\mathbf c$ and so lies in the plane of $\mathbf b$ and $\mathbf c$. Hence

$$
\mathbf a\cdot(\mathbf b\times\mathbf c)=0\iff\mathbf a,\ \mathbf b,\ \mathbf c\ \text{are coplanar}\iff\text{one of them is a linear combination of the other two.}
$$

Four points A, B, C, D lie in one plane exactly when the three edge vectors from one of them are coplanar, $(\mathbf b-\mathbf a)\cdot\big[(\mathbf c-\mathbf a)\times(\mathbf d-\mathbf a)\big]=0$.

### Coplanarity and volume examples (James Example 4.31, Exercises 57–59)

James Example 4.31: find $\lambda$ such that $(2,-1,1)$, $(1,2,-3)$ and $(3,\lambda,5)$ are coplanar. Expand along the first row:

$$
\begin{aligned}
\begin{vmatrix}2&-1&1\\1&2&-3\\3&\lambda&5\end{vmatrix}
&=2\big(2\cdot5-(-3)\lambda\big)-(-1)\big(1\cdot5-(-3)\cdot3\big)+1\big(1\cdot\lambda-2\cdot3\big)\\
&=2(10+3\lambda)+(5+9)+(\lambda-6)\\
&=20+6\lambda+14+\lambda-6\\
&=7\lambda+28 .
\end{aligned}
$$

Setting $7\lambda+28=0$ gives $\lambda=-4$. In the other order, $\mathbf a\times\mathbf b=(1,7,5)$ and $(\mathbf a\times\mathbf b)\cdot\mathbf c=3+7\lambda+25$, the same expression.

Exercise 57: the volume of the parallelepiped with edges $(2,-3,4)$, $(1,3,-1)$ and $(3,-1,2)$:

$$
\begin{aligned}
\begin{vmatrix}2&-3&4\\1&3&-1\\3&-1&2\end{vmatrix}
&=2\big(3\cdot2-(-1)(-1)\big)-(-3)\big(1\cdot2-(-1)\cdot3\big)+4\big(1\cdot(-1)-3\cdot3\big)\\
&=2(6-1)+3(2+3)+4(-1-9)\\
&=10+15-40\\
&=-15 .
\end{aligned}
$$

The volume is $|-15|=15$. The minus sign only says that this ordering of the three edges is left-handed.

Exercise 58: prove that $(3,2,-1)$, $(5,-7,3)$ and $(11,-3,1)$ are coplanar.

$$
\begin{aligned}
\begin{vmatrix}3&2&-1\\5&-7&3\\11&-3&1\end{vmatrix}
&=3\big((-7)(1)-3(-3)\big)-2\big(5\cdot1-3\cdot11\big)+(-1)\big(5(-3)-(-7)(11)\big)\\
&=3(2)-2(-28)-(62)\\
&=6+56-62=0 .
\end{aligned}
$$

The dependence is explicit: $2(3,2,-1)+(5,-7,3)=(11,-3,1)$.

Exercise 59: find $\lambda$ such that $(3,2,-1)$, $(1,-1,3)$ and $(2,-3,\lambda)$ are coplanar:

$$
\begin{aligned}
\begin{vmatrix}3&2&-1\\1&-1&3\\2&-3&\lambda\end{vmatrix}
&=3\big(-\lambda-3(-3)\big)-2\big(\lambda-3\cdot2\big)+(-1)\big(1(-3)-(-1)2\big)\\
&=3(9-\lambda)-2(\lambda-6)-(-1)\\
&=27-3\lambda-2\lambda+12+1\\
&=40-5\lambda ,
\end{aligned}
$$

so $\lambda=8$.

Specimen Test 15 Q1 needs no determinant. In (i), $\mathbf k\times\mathbf j=-\mathbf i$, so $\mathbf j\cdot(\mathbf k\times\mathbf j)=\mathbf j\cdot(-\mathbf i)=0$, as for any triple product with a repeated vector. In (ii), with $\mathbf a=\mathbf i+\mathbf j$, $\mathbf b=2\mathbf k$ and $\mathbf c=\mathbf j$,

$$
\begin{aligned}
\mathbf b\times\mathbf c&=2(\mathbf k\times\mathbf j)=-2\mathbf i,\\
\mathbf a\cdot(\mathbf b\times\mathbf c)&=(\mathbf i+\mathbf j)\cdot(-2\mathbf i)=-2 .
\end{aligned}
$$

> [!check] Specimen Q1(ii) as a determinant
> $\begin{vmatrix}1&1&0\\0&0&2\\0&1&0\end{vmatrix}=1(0\cdot0-2\cdot1)-1(0\cdot0-2\cdot0)+0=-2$, matching the unit-vector route.

## 2. The triple vector product

The **triple vector product** of three vectors is a cross product of a cross product. Its expansion (James 4.13) is

$$
(\mathbf a\times\mathbf b)\times\mathbf c=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf b\cdot\mathbf c)\,\mathbf a .
$$

Prove it one component at a time. Write $\mathbf w=\mathbf a\times\mathbf b=(a_2b_3-a_3b_2,\ a_3b_1-a_1b_3,\ a_1b_2-a_2b_1)$. The first component of $\mathbf w\times\mathbf c$ is $w_2c_3-w_3c_2$, so

$$
\begin{aligned}
\big[(\mathbf a\times\mathbf b)\times\mathbf c\big]_1&=(a_3b_1-a_1b_3)c_3-(a_1b_2-a_2b_1)c_2\\
&=a_3c_3b_1-b_3c_3a_1-b_2c_2a_1+a_2c_2b_1\\
&=(a_2c_2+a_3c_3)\,b_1-(b_2c_2+b_3c_3)\,a_1\\
&=(a_1c_1+a_2c_2+a_3c_3)\,b_1-(b_1c_1+b_2c_2+b_3c_3)\,a_1\\
&=(\mathbf a\cdot\mathbf c)\,b_1-(\mathbf b\cdot\mathbf c)\,a_1 ,
\end{aligned}
$$

where the fourth line adds and subtracts $a_1b_1c_1$. The second and third components follow by relabelling the subscripts cyclically ($1\to2\to3\to1$), which proves 4.13.

The other bracketing follows from 4.13 without new algebra. Reverse the outer cross product, then apply 4.13 with the letters $\mathbf a,\mathbf b,\mathbf c$ replaced by $\mathbf b,\mathbf c,\mathbf a$:

$$
\begin{aligned}
\mathbf a\times(\mathbf b\times\mathbf c)&=-(\mathbf b\times\mathbf c)\times\mathbf a\\
&=-\big[(\mathbf b\cdot\mathbf a)\,\mathbf c-(\mathbf c\cdot\mathbf a)\,\mathbf b\big]\\
&=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf a\cdot\mathbf b)\,\mathbf c .
\end{aligned}
$$

This is James 4.14, remembered as "BAC minus CAB": $\mathbf a\times(\mathbf b\times\mathbf c)=\mathbf b(\mathbf a\cdot\mathbf c)-\mathbf c(\mathbf a\cdot\mathbf b)$. Equation 4.13 is printed on the formula sheet and in the Data Book (Module 15 work scheme, item 2), so the skill is deriving 4.14 from it as above. The result of $\mathbf a\times(\mathbf b\times\mathbf c)$ is a combination of $\mathbf b$ and $\mathbf c$, so it lies in their plane, perpendicular to $\mathbf b\times\mathbf c$; the result of $(\mathbf a\times\mathbf b)\times\mathbf c$ lies in the plane of $\mathbf a$ and $\mathbf b$. The two are different in general, so the cross product is not associative and the brackets are essential. James Example 4.35 shows it with $\mathbf a=(1,0,0)$, $\mathbf b=(-1,2,0)$, $\mathbf c=(1,1,1)$: $\mathbf b\times\mathbf c=(2,1,-3)$ gives $\mathbf a\times(\mathbf b\times\mathbf c)=(0,3,1)$, while $\mathbf a\times\mathbf b=(0,0,2)$ gives $(\mathbf a\times\mathbf b)\times\mathbf c=(-2,2,0)$.

### Checking the expansion with numbers (James Example 4.34)

Take $\mathbf a=(3,-2,1)$, $\mathbf b=(-1,3,4)$ and $\mathbf c=(2,1,-3)$. Directly:

$$
\begin{aligned}
\mathbf b\times\mathbf c&=\big(3(-3)-4(1),\ 4(2)-(-1)(-3),\ (-1)(1)-3(2)\big)=(-13,5,-7),\\
\mathbf a\times(\mathbf b\times\mathbf c)&=\big((-2)(-7)-1(5),\ 1(-13)-3(-7),\ 3(5)-(-2)(-13)\big)=(9,8,-11).
\end{aligned}
$$

By the expansion, $\mathbf a\cdot\mathbf c=6-2-3=1$ and $\mathbf a\cdot\mathbf b=-3-6+4=-5$, so

$$
(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c=(-1,3,4)+5(2,1,-3)=(9,8,-11),
$$

the same vector, with two dot products instead of two cross products.

## 3. Differentiating a vector function of time

A vector whose components depend on time, $\mathbf v(t)=v_1(t)\,\mathbf i+v_2(t)\,\mathbf j+v_3(t)\,\mathbf k$, has derivative

$$
\frac{\mathrm d\mathbf v}{\mathrm dt}=\lim_{\Delta t\to0}\frac{\mathbf v(t+\Delta t)-\mathbf v(t)}{\Delta t}.
$$

Subtracting and dividing act on each component separately, and $\mathbf i,\mathbf j,\mathbf k$ are fixed in magnitude and direction, so their derivatives are zero. The product rule for a scalar times a vector (rule (b) below) makes this explicit for $\mathbf r=\sin t\,\mathbf i+\cos t\,\mathbf j$:

$$
\begin{aligned}
\dot{\mathbf r}&=\cos t\,\mathbf i+\sin t\,\frac{\mathrm d\mathbf i}{\mathrm dt}-\sin t\,\mathbf j+\cos t\,\frac{\mathrm d\mathbf j}{\mathrm dt}\\
&=\cos t\,\mathbf i-\sin t\,\mathbf j .
\end{aligned}
$$

So a vector is differentiated by differentiating its components. For a position vector $\mathbf r(t)=(x(t),y(t),z(t))$ the dot notation gives the **velocity** $\dot{\mathbf r}=(\dot x,\dot y,\dot z)$, the **acceleration** $\ddot{\mathbf r}=(\ddot x,\ddot y,\ddot z)$ and the **speed** $|\dot{\mathbf r}|$.

### The four rules and their proofs

With $\lambda(t)$ a scalar function and $\mathbf u(t)$, $\mathbf v(t)$ vector functions, the rules on James p. 734 are

$$
\begin{aligned}
&\text{(a)}\quad\frac{\mathrm d}{\mathrm dt}(\mathbf u+\mathbf v)=\dot{\mathbf u}+\dot{\mathbf v},\\
&\text{(b)}\quad\frac{\mathrm d}{\mathrm dt}(\lambda\mathbf v)=\dot\lambda\,\mathbf v+\lambda\,\dot{\mathbf v},\\
&\text{(c)}\quad\frac{\mathrm d}{\mathrm dt}(\mathbf u\cdot\mathbf v)=\dot{\mathbf u}\cdot\mathbf v+\mathbf u\cdot\dot{\mathbf v},\\
&\text{(d)}\quad\frac{\mathrm d}{\mathrm dt}(\mathbf u\times\mathbf v)=\dot{\mathbf u}\times\mathbf v+\mathbf u\times\dot{\mathbf v}.
\end{aligned}
$$

Rule (a) is the scalar sum rule applied to each component. Rule (b) follows from the limit, by adding and subtracting $\lambda(t)\mathbf v(t+\Delta t)$ in the numerator:

$$
\begin{aligned}
\frac{\lambda(t+\Delta t)\mathbf v(t+\Delta t)-\lambda(t)\mathbf v(t)}{\Delta t}
&=\frac{\lambda(t+\Delta t)-\lambda(t)}{\Delta t}\,\mathbf v(t+\Delta t)+\lambda(t)\,\frac{\mathbf v(t+\Delta t)-\mathbf v(t)}{\Delta t}\\
&\to\dot\lambda\,\mathbf v+\lambda\,\dot{\mathbf v}\quad\text{as }\Delta t\to0 .
\end{aligned}
$$

Rule (c) is the scalar product rule applied to each term of $\mathbf u\cdot\mathbf v$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(u_1v_1+u_2v_2+u_3v_3)&=(\dot u_1v_1+u_1\dot v_1)+(\dot u_2v_2+u_2\dot v_2)+(\dot u_3v_3+u_3\dot v_3)\\
&=(\dot u_1v_1+\dot u_2v_2+\dot u_3v_3)+(u_1\dot v_1+u_2\dot v_2+u_3\dot v_3)\\
&=\dot{\mathbf u}\cdot\mathbf v+\mathbf u\cdot\dot{\mathbf v}.
\end{aligned}
$$

Rule (d) works the same way on the first component of $\mathbf u\times\mathbf v$, which is $u_2v_3-u_3v_2$:

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(u_2v_3-u_3v_2)&=\dot u_2v_3+u_2\dot v_3-\dot u_3v_2-u_3\dot v_2\\
&=(\dot u_2v_3-\dot u_3v_2)+(u_2\dot v_3-u_3\dot v_2)\\
&=\big[\dot{\mathbf u}\times\mathbf v\big]_1+\big[\mathbf u\times\dot{\mathbf v}\big]_1 ,
\end{aligned}
$$

and the other two components follow by cyclic relabelling.

> [!warning] Keep the order in the cross-product rule
> In rule (d) the differentiated factor stays where it was: $\mathbf u\times\dot{\mathbf v}$, not $\dot{\mathbf v}\times\mathbf u$. Swapping the order changes the sign, because $\mathbf u\times\dot{\mathbf v}=-\dot{\mathbf v}\times\mathbf u$.

### Two consequences

A vector of constant magnitude is perpendicular to its derivative (James Exercise 35). If $|\mathbf a|$ is constant, so is $|\mathbf a|^2=\mathbf a\cdot\mathbf a$, and rule (c) gives

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(\mathbf a\cdot\mathbf a)&=0\\
\dot{\mathbf a}\cdot\mathbf a+\mathbf a\cdot\dot{\mathbf a}&=0\\
2\,\mathbf a\cdot\dot{\mathbf a}&=0 ,
\end{aligned}
$$

so $\mathbf a\cdot\dot{\mathbf a}=0$ and, when both are non-zero, $\mathbf a\perp\dot{\mathbf a}$. In the components of the exercise, $\mathbf a=f\,\mathbf i+g\,\mathbf j$ with $f^2+g^2$ constant gives $2(ff'+gg')=0$, the same statement. Applied to a position vector on a circle about the origin, it says the velocity is perpendicular to the radius, i.e. along the tangent. Applied to a velocity of constant magnitude, it says the acceleration is perpendicular to the velocity.

The speed is not the rate of change of distance from the origin. Differentiate $|\mathbf r|^2=\mathbf r\cdot\mathbf r$:

$$
\begin{aligned}
2|\mathbf r|\,\frac{\mathrm d|\mathbf r|}{\mathrm dt}&=2\,\mathbf r\cdot\dot{\mathbf r}\\
\frac{\mathrm d|\mathbf r|}{\mathrm dt}&=\frac{\mathbf r\cdot\dot{\mathbf r}}{|\mathbf r|}=\hat{\mathbf r}\cdot\dot{\mathbf r},
\end{aligned}
$$

which is only the component of the velocity along $\hat{\mathbf r}$ (for $\mathbf r\neq\mathbf 0$). It equals the speed $|\dot{\mathbf r}|$ only for motion straight along the radius.

### The unit circle (James Example 9.20)

The curve $\mathbf r=\sin t\,\mathbf i+\cos t\,\mathbf j$ has $x^2+y^2=\sin^2t+\cos^2t=1$, so it is the unit circle about O. At $t=0$ it is at $(0,1)$ and at $t=\pi/2$ at $(1,0)$, so it is traced clockwise. The four parts are

$$
\begin{aligned}
&\text{(a)}\quad\dot{\mathbf r}=\cos t\,\mathbf i-\sin t\,\mathbf j,\\
&\text{(b)}\quad\ddot{\mathbf r}=-\sin t\,\mathbf i-\cos t\,\mathbf j=-\mathbf r,\\
&\text{(c)}\quad|\dot{\mathbf r}|=(\cos^2t+\sin^2t)^{1/2}=1,\\
&\text{(d)}\quad|\mathbf r|=(\sin^2t+\cos^2t)^{1/2}=1,\quad\text{so}\quad\frac{\mathrm d}{\mathrm dt}|\mathbf r|=0 .
\end{aligned}
$$

The acceleration points to the centre (centripetal), the speed is a constant 1, and the distance from O does not change, so (c) and (d) differ: $|\mathrm d\mathbf r/\mathrm dt|\neq\mathrm d|\mathbf r|/\mathrm dt$. Since $|\mathbf r|=1$ is constant, $\mathbf r\cdot\dot{\mathbf r}=\sin t\cos t-\cos t\sin t=0$, the tangent-velocity result above.

> [!warning] Speed is not the rate of change of distance
> $|\dot{\mathbf r}|$ and $\mathrm d|\mathbf r|/\mathrm dt$ are different quantities. On the unit circle the first is 1 and the second is 0; on the helix below the first is $\sqrt2$ and the second is $\hat{\mathbf r}\cdot\dot{\mathbf r}=t/\sqrt{1+t^2}$.

Exercise 32 is a direct application: $\mathbf r=(t,t^2,t^3)$ gives $\dot{\mathbf r}=(1,2t,3t^2)$ and $\ddot{\mathbf r}=(0,2,6t)$.

### The helix (Specimen Test 15 Q5)

For $\mathbf r(t)=\cos t\,\mathbf i+\sin t\,\mathbf j+t\,\mathbf k$,

$$
\begin{aligned}
\dot{\mathbf r}&=(-\sin t,\ \cos t,\ 1),\\
\ddot{\mathbf r}&=(-\cos t,\ -\sin t,\ 0),\\
\dot{\mathbf r}\cdot\ddot{\mathbf r}&=\sin t\cos t-\sin t\cos t+0=0 .
\end{aligned}
$$

The dot product is zero because the speed $|\dot{\mathbf r}|=\sqrt{\sin^2t+\cos^2t+1}=\sqrt2$ is constant, which is the constant-magnitude result applied to $\dot{\mathbf r}$. The acceleration is horizontal and points from the particle to the $z$-axis.

![[m1054_m15_helix.png|600]]

### The derivative of r × ṙ (Specimen Test 15 Q7)

Given $\mathbf r\times\dot{\mathbf r}=t^2\,\mathbf i$, differentiate both sides with rule (d):

$$
\begin{aligned}
\frac{\mathrm d}{\mathrm dt}(\mathbf r\times\dot{\mathbf r})&=\dot{\mathbf r}\times\dot{\mathbf r}+\mathbf r\times\ddot{\mathbf r}\\
&=\mathbf 0+\mathbf r\times\ddot{\mathbf r},\\
\frac{\mathrm d}{\mathrm dt}(t^2\,\mathbf i)&=2t\,\mathbf i,
\end{aligned}
$$

so $\mathbf r\times\ddot{\mathbf r}=2t\,\mathbf i$. The term $\dot{\mathbf r}\times\dot{\mathbf r}$ vanishes because the cross product of a vector with itself is zero. Multiplied by a mass, $\mathbf r\times m\dot{\mathbf r}$ is the angular momentum of a particle about O and $\mathbf r\times m\ddot{\mathbf r}$ is the moment of the resultant force, so this one line is the moment equation of [[FEEG1002 D5 - Angular Impulse and Momentum]].

## 4. Velocity and acceleration in polar coordinates (James Exercise 34)

In the plane, the polar unit vectors at a point P with polar angle $\theta$ are $\hat{\mathbf r}$, pointing along OP, and $\hat{\boldsymbol\theta}$, which is $\hat{\mathbf r}$ turned through $+90^\circ$:

$$
\hat{\mathbf r}=\cos\theta\,\mathbf i+\sin\theta\,\mathbf j,\qquad\hat{\boldsymbol\theta}=-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j .
$$

Unlike $\mathbf i$ and $\mathbf j$, these turn as P moves, so their derivatives are not zero. With $\theta=\theta(t)$ and $\omega=\dot\theta$, the chain rule gives

$$
\begin{aligned}
\frac{\mathrm d\hat{\mathbf r}}{\mathrm dt}&=(-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j)\,\dot\theta=\omega\,\hat{\boldsymbol\theta},\\
\frac{\mathrm d\hat{\boldsymbol\theta}}{\mathrm dt}&=(-\cos\theta\,\mathbf i-\sin\theta\,\mathbf j)\,\dot\theta=-\omega\,\hat{\mathbf r}.
\end{aligned}
$$

Write the position as $\mathbf r=r\,\hat{\mathbf r}$, where $r=|\mathbf r|$, and use rule (b):

$$
\begin{aligned}
\dot{\mathbf r}&=\dot r\,\hat{\mathbf r}+r\,\frac{\mathrm d\hat{\mathbf r}}{\mathrm dt}\\
&=\dot r\,\hat{\mathbf r}+r\omega\,\hat{\boldsymbol\theta}.
\end{aligned}
$$

Differentiate again, term by term, with rule (b) on each product:

$$
\begin{aligned}
\ddot{\mathbf r}&=\ddot r\,\hat{\mathbf r}+\dot r\,\frac{\mathrm d\hat{\mathbf r}}{\mathrm dt}+(\dot r\omega+r\dot\omega)\,\hat{\boldsymbol\theta}+r\omega\,\frac{\mathrm d\hat{\boldsymbol\theta}}{\mathrm dt}\\
&=\ddot r\,\hat{\mathbf r}+\dot r\omega\,\hat{\boldsymbol\theta}+(\dot r\omega+r\dot\omega)\,\hat{\boldsymbol\theta}-r\omega^2\,\hat{\mathbf r}\\
&=(\ddot r-r\omega^2)\,\hat{\mathbf r}+(2\dot r\omega+r\dot\omega)\,\hat{\boldsymbol\theta}.
\end{aligned}
$$

The radial component contains the centripetal term $-r\omega^2$, present even when $r$ is constant, and the transverse component contains the Coriolis term $2\dot r\omega$, present when the particle moves outwards while the radius line turns. These are the radial and transverse accelerations of [[SESA2024 02 - Kepler's Laws and the Orbit Equation]], and the circular-path case of the normal and tangential components in [[FEEG1002 D2 - Curvilinear Motion]].

> [!check] Reduction to the unit circle
> James Example 9.20 has $\mathbf r=\sin t\,\mathbf i+\cos t\,\mathbf j=\cos(\tfrac\pi2-t)\,\mathbf i+\sin(\tfrac\pi2-t)\,\mathbf j$, so $r=1$, $\theta=\tfrac\pi2-t$ and $\omega=-1$. The polar formula gives $\ddot{\mathbf r}=(0-1\cdot1)\,\hat{\mathbf r}+0\,\hat{\boldsymbol\theta}=-\hat{\mathbf r}=-\mathbf r$, as found directly in part (b).

## 5. Integrating vectors: paths from the acceleration

Integration also acts on each component,

$$
\int\mathbf v(t)\,\mathrm dt=\Big(\int v_1\,\mathrm dt,\ \int v_2\,\mathrm dt,\ \int v_3\,\mathrm dt\Big)+\mathbf c,
$$

and the constant of integration is a constant vector $\mathbf c=(c_1,c_2,c_3)$, one scalar constant per component. Finding a path from the acceleration takes two integrations, so two vector constants, fixed by the initial velocity and the initial position.

### Projectile under gravity (James Example 9.21)

Solve $\ddot{\mathbf r}=-g\,\mathbf k$ with $\mathbf r(0)=\mathbf 0$ and $\dot{\mathbf r}(0)=\mathbf V$. Integrate once and fit the initial velocity:

$$
\begin{aligned}
\dot{\mathbf r}&=-gt\,\mathbf k+\mathbf c,\\
\dot{\mathbf r}(0)=\mathbf c&=\mathbf V,\\
\dot{\mathbf r}&=-gt\,\mathbf k+\mathbf V .
\end{aligned}
$$

Integrate again and fit the initial position:

$$
\begin{aligned}
\mathbf r&=\mathbf Vt-\tfrac12gt^2\,\mathbf k+\mathbf a,\\
\mathbf r(0)=\mathbf a&=\mathbf 0,\\
\mathbf r&=\mathbf Vt-\tfrac12gt^2\,\mathbf k .
\end{aligned}
$$

With $\mathbf V=(u,0,v)$ and $u\neq0$, the components are $x=ut$, $y=0$ and $z=vt-\tfrac12gt^2$. Eliminate $t=x/u$ and complete the square:

$$
\begin{aligned}
z&=v\,\frac xu-\frac g2\,\frac{x^2}{u^2}\\
&=\frac vu\,x-\frac{g}{2u^2}\,x^2\\
&=-\frac{g}{2u^2}\Big(x-\frac{uv}{g}\Big)^2+\frac{v^2}{2g}.
\end{aligned}
$$

The path is a parabola in the $xz$-plane with its highest point at $(uv/g,\ 0,\ v^2/2g)$, the result used for [[Projectile Motion]] in FEEG1002.

### A helix from its acceleration (Booklet Exercise A)

A particle has acceleration $\ddot{\mathbf r}=\cos t\,\mathbf i+\sin t\,\mathbf j$, and at $t=0$ it is at $(-1,0,0)$ moving with velocity $-\mathbf j+\mathbf k$. Integrate once:

$$
\begin{aligned}
\dot{\mathbf r}&=(\sin t,\ -\cos t,\ 0)+\mathbf C,\\
\dot{\mathbf r}(0)&=(0,-1,0)+\mathbf C=(0,-1,1)\ \Rightarrow\ \mathbf C=(0,0,1),\\
\dot{\mathbf r}&=(\sin t,\ -\cos t,\ 1).
\end{aligned}
$$

Integrate again:

$$
\begin{aligned}
\mathbf r&=(-\cos t,\ -\sin t,\ t)+\mathbf D,\\
\mathbf r(0)&=(-1,0,0)+\mathbf D=(-1,0,0)\ \Rightarrow\ \mathbf D=\mathbf 0,\\
\mathbf r&=(-\cos t,\ -\sin t,\ t).
\end{aligned}
$$

The path is a helix on the cylinder $x^2+y^2=1$, rising one unit in $z$ per radian of turn. It is the helix of Specimen Q5 half a turn on, since $(-\cos t,-\sin t)=(\cos(t+\pi),\sin(t+\pi))$.

### Velocity and position from a given acceleration (Specimen Test 15 Q6)

Given $\ddot{\mathbf r}=\sin2t\,\mathbf i-\cos t\,\mathbf j+t^2\,\mathbf k$, $\dot{\mathbf r}(0)=2\mathbf j$ and $\mathbf r(0)=\mathbf k$. Integrate once:

$$
\begin{aligned}
\dot{\mathbf r}&=\big(-\tfrac12\cos2t,\ -\sin t,\ \tfrac13t^3\big)+\mathbf C,\\
\dot{\mathbf r}(0)&=\big(-\tfrac12,\ 0,\ 0\big)+\mathbf C=(0,2,0)\ \Rightarrow\ \mathbf C=\big(\tfrac12,\ 2,\ 0\big),\\
\dot{\mathbf r}&=\big(\tfrac12-\tfrac12\cos2t,\ 2-\sin t,\ \tfrac13t^3\big)=\big(\sin^2t,\ 2-\sin t,\ \tfrac13t^3\big),
\end{aligned}
$$

using $1-\cos2t=2\sin^2t$. Integrate again, using the first form of the $x$-component:

$$
\begin{aligned}
\mathbf r&=\big(\tfrac t2-\tfrac14\sin2t,\ 2t+\cos t,\ \tfrac1{12}t^4\big)+\mathbf D,\\
\mathbf r(0)&=(0,\ 1,\ 0)+\mathbf D=(0,0,1)\ \Rightarrow\ \mathbf D=(0,-1,1),\\
\mathbf r&=\big(\tfrac t2-\tfrac14\sin2t,\ 2t+\cos t-1,\ \tfrac1{12}t^4+1\big).
\end{aligned}
$$

## 6. Straight lines

Let A and B be two points on a line, with position vectors $\mathbf a$ and $\mathbf b$, and let P, with position vector $\mathbf r$, be any point of the line. Then $\overrightarrow{\mathrm{AP}}$ is a multiple $t$ of $\overrightarrow{\mathrm{AB}}$, and the triangle law gives

$$
\begin{aligned}
\mathbf r&=\overrightarrow{\mathrm{OA}}+\overrightarrow{\mathrm{AP}}\\
&=\mathbf a+t\,\overrightarrow{\mathrm{AB}}\\
&=\mathbf a+t(\mathbf b-\mathbf a)\\
&=(1-t)\,\mathbf a+t\,\mathbf b .
\end{aligned}
$$

As $t$ runs over all real numbers P sweeps the whole line, with $t=0$ at A and $t=1$ at B. Writing $\mathbf d=\mathbf b-\mathbf a$ gives the line through A with **direction vector** $\mathbf d$:

$$
\mathbf r=\mathbf a+t\,\mathbf d .
$$

In components this is three **parametric equations**, $x=a_1+td_1$, $y=a_2+td_2$, $z=a_3+td_3$. Solving each for $t$ and equating gives the **Cartesian form**

$$
\frac{x-a_1}{d_1}=\frac{y-a_2}{d_2}=\frac{z-a_3}{d_3}\;(=t),
$$

valid when no $d_i$ is zero. If, say, $d_2=0$, the $y$-equation reads $y=a_2$ for every $t$, and the Cartesian form is read as "numerator zero": $y-a_2=0$ alongside the other two ratios. Any non-zero multiple of $\mathbf d$ is an equally good direction, and any point of the line an equally good base point, so one line has many correct equations.

The angle between two lines is the angle between their directions, $\cos\theta=\mathbf d_1\cdot\mathbf d_2/(|\mathbf d_1||\mathbf d_2|)$, so the lines are perpendicular when $\mathbf d_1\cdot\mathbf d_2=0$ and parallel when $\mathbf d_1\times\mathbf d_2=\mathbf 0$.

### Line examples (Exercises 66, 68, 71, Specimen Test 15 Q2, James Example 4.38)

Exercise 66 has A$(1,2,3)$ and B$(4,5,6)$. The direction is $\overrightarrow{\mathrm{AB}}=(3,3,3)$, or $(1,1,1)$ in lowest terms, so $\mathbf r=(1,2,3)+t(1,1,1)$, and the Cartesian form is $x-1=y-2=z-3$.

Exercise 71 has $\mathbf a=(2,0,-1)$ and $\mathbf b=(1,2,3)$, so $\mathbf d=\mathbf b-\mathbf a=(-1,2,4)$:

$$
\mathbf r=(2,0,-1)+s(-1,2,4),\qquad\frac{x-2}{-1}=\frac y2=\frac{z+1}4 .
$$

Exercise 68: show that the line joining $(2,3,4)$ to $(1,2,3)$ is perpendicular to the line joining $(1,0,2)$ to $(2,3,-2)$. The directions are $\mathbf d_1=(1,2,3)-(2,3,4)=(-1,-1,-1)$ and $\mathbf d_2=(2,3,-2)-(1,0,2)=(1,3,-4)$, and

$$
\mathbf d_1\cdot\mathbf d_2=-1-3+4=0 .
$$

Specimen Test 15 Q2(i)–(ii) has $\mathbf a=\mathbf i+\mathbf k=(1,0,1)$ and $\mathbf b=-\mathbf i+\mathbf j+\mathbf k=(-1,1,1)$, so $\mathbf b-\mathbf a=(-2,1,0)$ and

$$
\mathbf r=(1,0,1)+\lambda(-2,1,0).
$$

The line cuts the $yz$-plane where $x=0$: $1-2\lambda=0$, so $\lambda=\tfrac12$ and the point is $(0,\tfrac12,1)$.

James Example 4.38 finds where a line crosses all three coordinate planes. The line through A$(1,4,6)$ and B$(3,5,7)$ is $\mathbf r=(1,4,6)+t(2,1,1)$, i.e. $x=1+2t$, $y=4+t$, $z=6+t$:

| Plane | Condition | $t$ | Point |
|---|---|---|---|
| $yz$-plane, $x=0$ | $1+2t=0$ | $-\tfrac12$ | $(0,\tfrac72,\tfrac{11}2)$ |
| $zx$-plane, $y=0$ | $4+t=0$ | $-4$ | $(-7,0,2)$ |
| $xy$-plane, $z=0$ | $6+t=0$ | $-6$ | $(-11,-2,0)$ |

## 7. Intersecting, parallel and skew lines

Two lines $\mathbf r=\mathbf a_1+s\,\mathbf d_1$ and $\mathbf r=\mathbf a_2+t\,\mathbf d_2$ meet if some $s$ and $t$ give the same point. Equating the position vectors gives three scalar equations in two unknowns. Solve any two of them for $s$ and $t$, then substitute into the third:

- if the third equation holds, the lines intersect, and either line's equation gives the point;
- if it fails and $\mathbf d_1\parallel\mathbf d_2$, the lines are parallel and distinct;
- if it fails and the directions are not parallel, the lines are **skew**: they do not meet and are not parallel, which is possible only in three dimensions.

> [!warning] Always check the third equation
> Two equations in two unknowns usually have a solution, so solving two components always seems to produce an intersection. Only the third component decides whether the lines really meet. Exercise 71 below is a pair of skew lines.

The triple product gives a test without solving. Two non-parallel lines meet exactly when they lie in one plane, i.e. when the vector $\mathbf a_2-\mathbf a_1$ joining their base points lies in the plane of $\mathbf d_1$ and $\mathbf d_2$:

$$
\text{non-parallel lines intersect}\iff(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)=0 .
$$

### Two lines that meet (James Example 4.37)

$L_1$ passes through $(0,1,0)$ and $(1,3,-1)$, and $L_2$ through $(1,1,1)$ and $(-1,-1,1)$:

$$
L_1:\ \mathbf r=(0,1,0)+s(1,2,-1),\qquad L_2:\ \mathbf r=(1,1,1)+t(-2,-2,0).
$$

Equate components:

$$
\begin{aligned}
x:&\quad s=1-2t,\\
y:&\quad 1+2s=1-2t,\\
z:&\quad -s=1 .
\end{aligned}
$$

The $z$-equation gives $s=-1$, and the $x$-equation then gives $-1=1-2t$, so $t=1$. Check the $y$-equation: $1+2(-1)=-1$ and $1-2(1)=-1$, so it holds and the lines intersect, at $(0,1,0)-(1,2,-1)=(-1,-1,1)$. The test agrees: $\mathbf a_2-\mathbf a_1=(1,0,1)$ and

$$
\begin{vmatrix}1&0&1\\1&2&-1\\-2&-2&0\end{vmatrix}=1(0-2)-0+1(-2+4)=0 .
$$

### Choosing a constant so that lines meet (James Example 4.39)

$L_1$ passes through $(5,1,7)$ and $(6,0,8)$, and $L_2$ through $(3,1,3)$ and $(-1,3,\alpha)$:

$$
L_1:\ \mathbf r=(5,1,7)+s(1,-1,1),\qquad L_2:\ \mathbf r=(3,1,3)+t(-4,2,\alpha-3).
$$

The $x$- and $y$-equations do not involve $\alpha$:

$$
\begin{aligned}
x:&\quad 5+s=3-4t,\\
y:&\quad 1-s=1+2t\ \Rightarrow\ s=-2t .
\end{aligned}
$$

Substituting $s=-2t$ into the $x$-equation gives $5-2t=3-4t$, so $t=-1$ and $s=2$. The $z$-equation must then hold:

$$
\begin{aligned}
7+s&=3+t(\alpha-3)\\
9&=3-(\alpha-3)\\
\alpha&=-3 .
\end{aligned}
$$

The point of intersection is $(5,1,7)+2(1,-1,1)=(7,-1,9)$. By the triple-product test, $(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)$ with $\mathbf a_2-\mathbf a_1=(-2,0,-4)$ works out to $2\alpha+6$, which is zero for the same $\alpha=-3$.

### Two lines that do not meet (Exercise 71)

The line through $\mathbf c=(0,0,1)$ and $\mathbf d=(1,0,1)$ has direction $(1,0,0)$, so it is $\mathbf r=(t,0,1)$: every point has $y=0$ and $z=1$. On the line $\mathbf r=(2-s,\,2s,\,-1+4s)$ of Exercise 71, $y=0$ forces $s=0$, which gives $z=-1\neq1$. No point satisfies all three equations, and the directions $(-1,2,4)$ and $(1,0,0)$ are not parallel, so the lines are skew. The test confirms it: $(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)=(-2,0,2)\cdot(0,4,-2)=-4\neq0$.

### Intersection with a given line (Specimen Test 15 Q2(iii))

Equate $(1-2\lambda,\ \lambda,\ 1)$ with $(3+s,\ -4+s,\ 3-s)$:

$$
\begin{aligned}
z:&\quad 1=3-s\ \Rightarrow\ s=2,\\
x:&\quad 1-2\lambda=3+2=5\ \Rightarrow\ \lambda=-2,\\
y:&\quad \lambda=-4+s\ \Rightarrow\ -2=-2 .
\end{aligned}
$$

The third equation holds, so the lines meet at $(1-2(-2),\,-2,\,1)=(5,-2,1)$.

## 8. Shortest distance between skew lines

For a point P on $L_1$ and a point Q on $L_2$:

$$
\mathbf p=\mathbf a_1+t_1\mathbf d_1,\qquad\mathbf q=\mathbf a_2+t_2\mathbf d_2,\qquad\overrightarrow{\mathrm{PQ}}=(\mathbf a_2-\mathbf a_1)+t_2\,\mathbf d_2-t_1\,\mathbf d_1 .
$$

Let $\mathbf n=\mathbf d_1\times\mathbf d_2$, which is perpendicular to both lines, and $\hat{\mathbf n}=\mathbf n/|\mathbf n|$. Dot $\overrightarrow{\mathrm{PQ}}$ with $\hat{\mathbf n}$; the direction terms drop out because $\mathbf d_1\cdot\mathbf n=\mathbf d_2\cdot\mathbf n=0$:

$$
\begin{aligned}
\overrightarrow{\mathrm{PQ}}\cdot\hat{\mathbf n}&=(\mathbf a_2-\mathbf a_1)\cdot\hat{\mathbf n}+t_2\,\mathbf d_2\cdot\hat{\mathbf n}-t_1\,\mathbf d_1\cdot\hat{\mathbf n}\\
&=(\mathbf a_2-\mathbf a_1)\cdot\hat{\mathbf n}.
\end{aligned}
$$

So the component of $\overrightarrow{\mathrm{PQ}}$ along $\hat{\mathbf n}$ is the same for every choice of P and Q. A vector is at least as long as any one of its components, so $|\overrightarrow{\mathrm{PQ}}|\ge|(\mathbf a_2-\mathbf a_1)\cdot\hat{\mathbf n}|$, with equality exactly when $\overrightarrow{\mathrm{PQ}}$ has no other component, i.e. when it is parallel to $\mathbf n$ and so perpendicular to both lines. The shortest distance is therefore

$$
D=\frac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|},
$$

and it is achieved along the **common perpendicular**. The numerator is the triple product $[\mathbf a_2-\mathbf a_1,\mathbf d_1,\mathbf d_2]$, so $D=0$ exactly when the lines are coplanar, which for non-parallel lines means they intersect, as in §7. For parallel lines $\mathbf d_1\times\mathbf d_2=\mathbf 0$ and the formula breaks down; their separation is then the distance from $\mathbf a_2$ to $L_1$, $|(\mathbf a_2-\mathbf a_1)\times\mathbf d_1|/|\mathbf d_1|$, the perpendicular part of $\mathbf a_2-\mathbf a_1$.

The feet P and Q of the common perpendicular come from the two conditions $\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_1=0$ and $\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_2=0$, two linear equations in $t_1$ and $t_2$. A quicker route once $D$ is known (Module 15 work scheme, item 6): set $\overrightarrow{\mathrm{PQ}}$ equal to $\pm D\hat{\mathbf n}$, with the sign of $(\mathbf a_2-\mathbf a_1)\cdot\hat{\mathbf n}$, and equate components.

### Skew lines and the common perpendicular

James Example 4.42: the lines $\frac x3=\frac{y-9}{-1}=\frac{z-2}{1}$ and $\frac{x+6}{-3}=\frac{y+5}{2}=\frac{z-10}{4}$ have, in vector form,

$$
\mathbf a_1=(0,9,2),\quad\mathbf d_1=(3,-1,1),\qquad\mathbf a_2=(-6,-5,10),\quad\mathbf d_2=(-3,2,4).
$$

The common normal is

$$
\begin{aligned}
\mathbf d_1\times\mathbf d_2&=\big((-1)(4)-(1)(2),\ (1)(-3)-(3)(4),\ (3)(2)-(-1)(-3)\big)\\
&=(-6,-15,3)=-3(2,5,-1),
\end{aligned}
$$

so take $\mathbf n=(2,5,-1)$ with $|\mathbf n|=\sqrt{30}$. With $\mathbf a_2-\mathbf a_1=(-6,-14,8)$,

$$
\begin{aligned}
D&=\frac{|(-6,-14,8)\cdot(2,5,-1)|}{\sqrt{30}}\\
&=\frac{|-12-70-8|}{\sqrt{30}}\\
&=\frac{90}{\sqrt{30}}=3\sqrt{30}\approx16.43 .
\end{aligned}
$$

For the feet, $\overrightarrow{\mathrm{PQ}}=(-6,-14,8)+t_2(-3,2,4)-t_1(3,-1,1)$. Using $(-6,-14,8)\cdot\mathbf d_1=4$, $(-6,-14,8)\cdot\mathbf d_2=22$, $\mathbf d_1\cdot\mathbf d_2=-7$, $|\mathbf d_1|^2=11$ and $|\mathbf d_2|^2=29$:

$$
\begin{aligned}
\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_1=0:&\quad 4-7t_2-11t_1=0\ \Rightarrow\ 11t_1+7t_2=4,\\
\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_2=0:&\quad 22+29t_2+7t_1=0\ \Rightarrow\ 7t_1+29t_2=-22 .
\end{aligned}
$$

From the first, $t_1=(4-7t_2)/11$. Substituting into the second:

$$
\begin{aligned}
\frac{7(4-7t_2)}{11}+29t_2&=-22\\
28-49t_2+319t_2&=-242\\
270t_2&=-270\\
t_2=-1,\quad t_1&=\frac{4+7}{11}=1 .
\end{aligned}
$$

The feet are $\mathrm P=(0,9,2)+(3,-1,1)=(3,8,3)$ and $\mathrm Q=(-6,-5,10)-(-3,2,4)=(-3,-7,6)$, and the common perpendicular is the line through P along $\mathbf n$:

$$
\mathbf r=(3,8,3)+\mu(2,5,-1),\qquad\frac{x-3}2=\frac{y-8}5=\frac{z-3}{-1}.
$$

Equating components gives the same feet with less algebra (Module 15 work scheme, item 6). Since $(\mathbf a_2-\mathbf a_1)\cdot\mathbf n=-90<0$, $\overrightarrow{\mathrm{PQ}}=-D\hat{\mathbf n}=-3(2,5,-1)=(-6,-15,3)$. Equating components of $(-6,-14,8)+t_2(-3,2,4)-t_1(3,-1,1)=(-6,-15,3)$ gives $-3t_2-3t_1=0$, $2t_2+t_1=-1$ and $4t_2-t_1=-5$; the first two give $t_1=-t_2$ and $t_2=-1$, and the third checks: $-4-1=-5$.

> [!check] Length of PQ
> $\overrightarrow{\mathrm{PQ}}=\mathrm Q-\mathrm P=(-6,-15,3)$ and $|\overrightarrow{\mathrm{PQ}}|=\sqrt{36+225+9}=\sqrt{270}=3\sqrt{30}$, equal to $D$ from the formula. The normal $\mathbf d_2\times\mathbf d_1=(6,15,-3)$ gives the same common perpendicular with the opposite sense.

![[m1054_skew_lines.png|600]]

The figure labels the parameters $s$ (on $L_1$) and $t$ (on $L_2$), which are $t_1$ and $t_2$ here.

### Distance between two given lines (Exercise 72)

For $\mathbf r=(4,-2,3)+t(2,1,-1)$ and $\mathbf r=(-7,-2,1)+s(3,2,1)$:

$$
\begin{aligned}
\mathbf n&=(2,1,-1)\times(3,2,1)=\big(1\cdot1-(-1)\cdot2,\ (-1)\cdot3-2\cdot1,\ 2\cdot2-1\cdot3\big)=(3,-5,1),\\
\mathbf a_2-\mathbf a_1&=(-11,0,-2),\\
D&=\frac{|(-11)(3)+0(-5)+(-2)(1)|}{\sqrt{9+25+1}}=\frac{35}{\sqrt{35}}=\sqrt{35}\approx5.916 .
\end{aligned}
$$

The feet are at $t=-1$, the point $(2,-3,4)$, and $s=2$, the point $(-1,2,3)$; their difference $(-3,5,-1)=-\mathbf n$ has length $\sqrt{35}$.

## 9. Planes

Let A, with position vector $\mathbf a$, be a point of a plane and $\mathbf n$ a non-zero **normal**, perpendicular to the plane. For any point P of the plane, with position vector $\mathbf r$, the vector $\overrightarrow{\mathrm{AP}}=\mathbf r-\mathbf a$ lies in the plane and so is perpendicular to $\mathbf n$:

$$
\begin{aligned}
(\mathbf r-\mathbf a)\cdot\mathbf n&=0\\
\mathbf r\cdot\mathbf n-\mathbf a\cdot\mathbf n&=0\\
\mathbf r\cdot\mathbf n&=\mathbf a\cdot\mathbf n=p .
\end{aligned}
$$

The right-hand side $p$ is a constant scalar. With $\mathbf n=(n_1,n_2,n_3)$ and $\mathbf r=(x,y,z)$ the **Cartesian form** is the linear equation

$$
n_1x+n_2y+n_3z=p,
$$

and conversely every equation $\alpha x+\beta y+\gamma z=p$ with $(\alpha,\beta,\gamma)\neq\mathbf 0$ is a plane with normal $(\alpha,\beta,\gamma)$: the normal is read straight off the coefficients.

Dividing by $|\mathbf n|$ gives the unit-normal form $\mathbf r\cdot\hat{\mathbf n}=p/|\mathbf n|$. For any point P of the plane, $\mathbf r\cdot\hat{\mathbf n}=\overrightarrow{\mathrm{OP}}\cdot\hat{\mathbf n}$ is the component of $\overrightarrow{\mathrm{OP}}$ along the normal, which is the same for every point of the plane and equals the perpendicular distance from O to the plane, up to sign (Module 15 work scheme, item 7). So when the equation is written $\mathbf r\cdot\hat{\mathbf n}=p$ with $\hat{\mathbf n}$ a unit vector and $p\ge0$, $p$ is the perpendicular distance from the origin.

A plane through three points A, B, C that are not on one line contains the two edge vectors $\mathbf u=\mathbf b-\mathbf a$ and $\mathbf v=\mathbf c-\mathbf a$, so

$$
\mathbf n=(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a),\qquad\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n .
$$

The same plane in parametric form is $\mathbf r=\mathbf a+\lambda\mathbf u+\mu\mathbf v$, and in triple-product form $(\mathbf r-\mathbf a)\cdot\big[(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)\big]=0$, the coplanarity condition of §1 for the four points A, B, C and P. The angle between two planes is the angle between their normals, and a line makes the angle $90^\circ-\varphi$ with a plane, where $\varphi$ is the angle between the line's direction and the normal.

### Plane examples (James Example 4.44, Exercises 73 and 79(a), Specimen Test 15 Q3 and Q4)

James Example 4.44: the plane through $(1,1,1)$, $(0,1,2)$ and $(-1,1,-1)$.

$$
\begin{aligned}
\mathbf n&=(-1,0,1)\times(-2,0,-2)=\big(0\cdot(-2)-1\cdot0,\ 1\cdot(-2)-(-1)(-2),\ (-1)\cdot0-0\cdot(-2)\big)=(0,-4,0),\\
\mathbf r\cdot(0,1,0)&=(1,1,1)\cdot(0,1,0)=1,
\end{aligned}
$$

after dividing $\mathbf n$ by $-4$. The plane is $y=1$, and all three points have $y=1$.

Exercise 73: the plane through $(1,2,3)$, $(2,4,5)$ and $(4,5,6)$. The edge vectors are $\mathbf u=(1,2,2)$ and $\mathbf v=(3,3,3)$, so

$$
\begin{aligned}
\mathbf n&=\mathbf u\times\mathbf v=(2\cdot3-2\cdot3,\ 2\cdot3-1\cdot3,\ 1\cdot3-2\cdot3)=(0,3,-3)\propto(0,1,-1),\\
\mathbf r\cdot(0,1,-1)&=(1,2,3)\cdot(0,1,-1)=-1 .
\end{aligned}
$$

The vector form is $\mathbf r=(1,2,3)+\lambda(1,2,2)+\mu(1,1,1)$, or equivalently $\mathbf r\cdot(0,1,-1)=-1$, and the Cartesian form is $y-z=-1$, i.e. $z=y+1$. Check: $2-3=4-5=5-6=-1$.

Exercise 79(a): P and Q have position vectors $\mathbf a=(3,1,2)$ and $\mathbf b=(1,-2,-4)$, and the plane passes through Q perpendicular to PQ. Its normal is $\overrightarrow{\mathrm{PQ}}$:

$$
\begin{aligned}
\mathbf n&=\mathbf b-\mathbf a=(-2,-3,-6),\\
\mathbf b\cdot\mathbf n&=(1)(-2)+(-2)(-3)+(-4)(-6)=-2+6+24=28,\\
-2x-3y-6z&=28\ \iff\ 2x+3y+6z=-28 .
\end{aligned}
$$

Specimen Test 15 Q3: the plane with normal $6\mathbf i+2\mathbf j-3\mathbf k$ through $(2,1,0)$.

$$
\begin{aligned}
\mathbf r\cdot(6,2,-3)&=(2,1,0)\cdot(6,2,-3)=14,\\
|\mathbf n|&=\sqrt{36+4+9}=7,\\
\mathbf r\cdot\tfrac17(6,2,-3)&=2 .
\end{aligned}
$$

In Cartesian form it is $6x+2y-3z=14$, and in the form $\mathbf r\cdot\hat{\mathbf n}=p$ the perpendicular distance from O to the plane is $p=2$.

Specimen Test 15 Q4: the plane through $(1,0,1)$, $(-3,1,12)$ and $(2,-1,-4)$.

$$
\begin{aligned}
\mathbf n&=(-4,1,11)\times(1,-1,-5)\\
&=\big(1(-5)-11(-1),\ 11(1)-(-4)(-5),\ (-4)(-1)-1(1)\big)\\
&=(6,-9,3)\propto(2,-3,1),\\
\mathbf r\cdot(2,-3,1)&=(1,0,1)\cdot(2,-3,1)=3 .
\end{aligned}
$$

The plane is $2x-3y+z=3$. The other two points check: $-6-3+12=3$ and $4+3-4=3$.

## 10. Where a line meets a plane, and where two planes meet

A point of the line $\mathbf r=\mathbf a+t\mathbf d$ lies on the plane $\mathbf r\cdot\mathbf n=p$ when

$$
\begin{aligned}
(\mathbf a+t\mathbf d)\cdot\mathbf n&=p\\
\mathbf a\cdot\mathbf n+t\,\mathbf d\cdot\mathbf n&=p\\
t&=\frac{p-\mathbf a\cdot\mathbf n}{\mathbf d\cdot\mathbf n},\qquad\mathbf d\cdot\mathbf n\neq0 .
\end{aligned}
$$

If $\mathbf d\cdot\mathbf n=0$ the line is parallel to the plane: it lies in the plane when $\mathbf a\cdot\mathbf n=p$ and misses it otherwise. James Example 4.38 in §6 is this calculation for the three coordinate planes.

James Example 4.46: the line $\mathbf r=(2,1,1)+\lambda(0,1,2)$ and the plane $\mathbf r\cdot(1,1,2)=3$. Here $(2,1,1)\cdot(1,1,2)=5$ and $(0,1,2)\cdot(1,1,2)=5$, so

$$
\begin{aligned}
5+5\lambda&=3\\
\lambda&=-\tfrac25,\\
\mathbf r&=(2,1,1)-\tfrac25(0,1,2)=\big(2,\tfrac35,\tfrac15\big).
\end{aligned}
$$

Check: $2+\tfrac35+2\cdot\tfrac15=3$.

Two non-parallel planes $\mathbf r\cdot\mathbf n_1=p_1$ and $\mathbf r\cdot\mathbf n_2=p_2$ meet in a line. The line lies in both planes, so its direction is perpendicular to both normals, $\mathbf d=\mathbf n_1\times\mathbf n_2$. For a point on it, fix one coordinate and solve the two plane equations for the other two. Fix a coordinate whose component of $\mathbf d$ is non-zero; if that component is zero, the coordinate is the same all along the line and an arbitrary value may give no solution.

James Example 4.47: the planes $x+y+z=5$ and $4x+y+2z=15$.

$$
\begin{aligned}
\mathbf d&=(1,1,1)\times(4,1,2)=(1\cdot2-1\cdot1,\ 1\cdot4-1\cdot2,\ 1\cdot1-1\cdot4)=(1,2,-3).
\end{aligned}
$$

Set $z=1$: then $x+y=4$ and $4x+y=13$; subtracting gives $3x=9$, so $x=3$ and $y=1$. The line is

$$
\mathbf r=(3,1,1)+t(1,2,-3),\qquad\frac{x-3}1=\frac{y-1}2=\frac{z-1}{-3}.
$$

Setting $x=0$ instead gives $y+z=5$ and $y+2z=15$, so $z=10$, $y=-5$ and $\mathbf r=(0,-5,10)+t(1,2,-3)$. It is the same line, because $(0,-5,10)=(3,1,1)-3(1,2,-3)$. Three planes usually meet in a single point, found by solving three linear equations; the cases where they do not are the inconsistent and underdetermined systems of [[Rank and Consistency of Linear Systems]].

## 11. Distance from a point to a plane

Let $P_0$, with position vector $\mathbf p_0=(x_0,y_0,z_0)$, be a point off the plane $\mathbf r\cdot\mathbf n=p$, and let Q, with position vector $\mathbf q$, be any point of the plane, so $\mathbf q\cdot\mathbf n=p$. The perpendicular distance is the size of the component of $\overrightarrow{\mathrm{QP_0}}$ along the unit normal:

$$
\begin{aligned}
D&=|(\mathbf p_0-\mathbf q)\cdot\hat{\mathbf n}|\\
&=\frac{|\mathbf p_0\cdot\mathbf n-\mathbf q\cdot\mathbf n|}{|\mathbf n|}\\
&=\frac{|\mathbf p_0\cdot\mathbf n-p|}{|\mathbf n|}\\
&=\frac{|n_1x_0+n_2y_0+n_3z_0-p|}{\sqrt{n_1^2+n_2^2+n_3^2}} .
\end{aligned}
$$

Substitute the point into the left-hand side of the plane equation, subtract the right-hand side, and divide by the length of the normal. The sign of $\mathbf p_0\cdot\mathbf n-p$ says which side of the plane the point is on, and with $\mathbf p_0=\mathbf 0$ the formula gives the distance $|p|/|\mathbf n|$ from the origin, as in §9.

> [!tip] One picture for every distance
> The skew-line distance, the point–plane distance and the origin–plane distance are all the same construction: take any vector joining the two objects and keep its component along the unit normal they share. The choice of joining vector does not matter, because moving either end within its line or plane changes only the components perpendicular to that normal.

### Point to plane, three ways (James Example 4.48)

Find the distance from P$(2,-3,4)$ to the plane $x+2y+2z=13$, with $\mathbf n=(1,2,2)$ and $|\mathbf n|=3$.

The first way drops a perpendicular. The line through P along $\mathbf n$ is $\mathbf r=(2,-3,4)+t(1,2,2)$, and it meets the plane where

$$
\begin{aligned}
(2,-3,4)\cdot(1,2,2)+t\,(1,2,2)\cdot(1,2,2)&=13\\
4+9t&=13\\
t&=1 ,
\end{aligned}
$$

at the foot N$(3,-1,6)$. Then $PN=\sqrt{(3-2)^2+(-1+3)^2+(6-4)^2}=\sqrt9=3$.

The second way projects onto the normal (Module 15 work scheme, item 8). Q$(0,0,\tfrac{13}2)$ lies on the plane, so

$$
D=\Big|\overrightarrow{\mathrm{PQ}}\cdot\hat{\mathbf n}\Big|=\left|\Big(-2,3,\tfrac52\Big)\cdot\frac{(1,2,2)}{3}\right|=\left|\frac{-2+6+5}{3}\right|=3 .
$$

The formula does the same in one line: $D=|2+2(-3)+2(4)-13|/3=|-9|/3=3$.

![[m1054_m15_point_plane.png|700]]

The figure is drawn in the plane through P, N and Q, which contains the normal, so every length in it is true: $\overrightarrow{\mathrm{PQ}}$ is long, but its component along $\hat{\mathbf n}$ is the perpendicular PN.

Exercise 79(b): the distance from $(-1,1,1)$ to the plane $2x+3y+6z=-28$ of part (a), whose normal has length $\sqrt{4+9+36}=7$:

$$
D=\frac{|2(-1)+3(1)+6(1)-(-28)|}{7}=\frac{|-2+3+6+28|}{7}=\frac{35}7=5 .
$$

## Terminology and alternative names

| Course term | Also called | Where the course uses it | Note |
|---|---|---|---|
| scalar triple product $\mathbf a\cdot(\mathbf b\times\mathbf c)$ | triple scalar product, box product, $[\mathbf a,\mathbf b,\mathbf c]$ | James writes $(\mathbf a\times\mathbf b)\cdot\mathbf c$ | equal by the cyclic rule |
| triple vector product | vector triple product, "BAC − CAB" | James equations 4.13 and 4.14 | 4.13 is on the formula sheet |
| $\dot{\mathbf r}$, $\ddot{\mathbf r}$ | $\mathrm d\mathbf r/\mathrm dt$, $\mathrm d^2\mathbf r/\mathrm dt^2$, $\mathbf v$ | James §9.5 | dot notation means time derivative only |
| $\mathbf r\cdot\hat{\mathbf n}=p$ | Hessian normal form of a plane | Specimen Test 15 Q3 | $p$ is the distance from O |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M15 Solutions - Vectors II]]
- Previous: [[MATH1054 M14 - Vectors I]] (dot and cross products, [[Vector Algebra and Components]]) · Next: [[MATH1054 M16 - Matrices I]] (the determinant in general, [[Determinants and Cofactors]]); systems of three planes in [[MATH1054 M17 - Matrices II]]
- Concepts: [[Scalar Triple Product]] · [[Equations of Lines and Planes]] · [[Differentiation of Vectors]] · [[Scalar (Dot) Product]] · [[Vector (Cross) Product]]
- Dynamics that uses vector velocity and acceleration: [[FEEG1002 D2 - Curvilinear Motion]] ([[Projectile Motion]], [[Normal and Tangential Coordinates]]) · [[FEEG1002 D5 - Angular Impulse and Momentum]] (moment of a force $\mathbf r\times\mathbf F$, derivative of $\mathbf r\times m\mathbf v$) · [[FEEG1002 D7 - Kinematics of Rigid Bodies]] · [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] (radial and transverse acceleration)
- Later: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] (normals to surfaces), [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] (triple-product identities), [[MATH2048 VC3 - Line Integrals and Conservative Fields]] (integrals along $\mathbf r(t)$); [[SESA3047 2.1 - Vector Operations and the Transport Theorem]] (triple products and derivatives in rotating frames)

## Sources

- MATH1054 Module Booklet, Module 15 work scheme (Module 15 pp. 1–2, PDF pp. 55–56): items 1–2 triple products, items 3–4 calculus of vectors and Exercise A, items 5–8 lines and planes; Specimen Test 15 (Module 15 p. 3, PDF p. 57).
- James, *Modern Engineering Mathematics* (6th ed.): §4.2.12 Triple products (pp. 270–275) and Exercises 57–59 (p. 276); §4.3.1 Vector equation of a line (pp. 277–283) and Exercises 66–72 (p. 284); §4.3.3 Vector equation of a plane (pp. 284–288) and Exercises 73–83 (p. 288); §9.5.1 Differentiation and integration of vectors (pp. 734–736) and Exercises 32–36 (pp. 736–737).
- Worked solutions to every work-scheme item: [[MATH1054 M15 Solutions - Vectors II]].

## Self-study tasks

### Core

- [ ] Exercises 57, 58 and 59 (Module 15 work scheme, item 2): a volume and two coplanarity tests. → [[MATH1054 M15 Solutions - Vectors II#Exercise 57: Volume of the parallelepiped|Exercise 57]] · [[MATH1054 M15 Solutions - Vectors II#Exercise 58: Show the vectors are coplanar|Exercise 58]] · Exercise 59 in [[MATH1054 M15 Solutions - Vectors II#Part B: Assigned exercises|Part B]]
- [ ] Exercises 32, 34 (hard) and 35 of James Chapter 9, and Booklet Exercise A (work scheme, items 3–4). → [[MATH1054 M15 Solutions - Vectors II#Exercise 34 (Ch.9, hard): Polar unit vectors|Exercise 34]] · [[MATH1054 M15 Solutions - Vectors II#Booklet Exercise A: Path from the acceleration|Exercise A]] · Exercises 32 and 35 in [[MATH1054 M15 Solutions - Vectors II#Part B: Assigned exercises|Part B]]
- [ ] Exercises 71, 66, 68 and 72 (work scheme, items 5 and 8): line equations, an intersection test, perpendicular lines and a skew-line distance. → [[MATH1054 M15 Solutions - Vectors II#Exercise 68: Perpendicular lines|Exercise 68]] · [[MATH1054 M15 Solutions - Vectors II#Exercise 72: Shortest distance between the lines|Exercise 72]] · Exercises 66 and 71 in [[MATH1054 M15 Solutions - Vectors II#Part B: Assigned exercises|Part B]]
- [ ] Exercises 73 and 79 (work scheme, item 8): a plane through three points, a plane from a normal and a point-to-plane distance. → [[MATH1054 M15 Solutions - Vectors II#Exercise 79: The plane through Q, perpendicular to PQ|Exercise 79]] · Exercise 73 in [[MATH1054 M15 Solutions - Vectors II#Part B: Assigned exercises|Part B]]
- [ ] Specimen Test 15, Q1–Q7, under test conditions. → [[MATH1054 M15 Solutions - Vectors II#Part C: Specimen Test 15|Part C]] · [[MATH1054 M15 Solutions - Vectors II#Q2: A line and its intersections|Q2]] · [[MATH1054 M15 Solutions - Vectors II#Q6: Velocity and position from the acceleration|Q6]]

### Further practice

- [ ] Rework James Examples 4.37, 4.39 and 4.42 without looking, and find the feet in 4.42 by the booklet's equate-components route (work scheme, items 5–6). → [[MATH1054 M15 Solutions - Vectors II#Example 4.42: Shortest distance between skew lines, and the common perpendicular|Example 4.42]] · [[#Skew lines and the common perpendicular]]
- [ ] Rework James Examples 4.44, 4.46, 4.47 and 4.48, doing 4.48 by projecting onto the normal (work scheme, items 7–8). → [[MATH1054 M15 Solutions - Vectors II#Part A: Worked examples|Part A]] · [[#Point to plane, three ways (James Example 4.48)]]
- [ ] Rework James Examples 9.20 and 9.21, including the vertex of the parabola (work scheme, items 3–4). → [[MATH1054 M15 Solutions - Vectors II#Example 9.21: Projectile motion|Example 9.21]] · [[#Projectile under gravity (James Example 9.21)]]
- [ ] James Exercise 60 (suggested, not set in the work scheme): show that $(2,1,0)$, $(2,-2,-2)$, $(7,-3,-1)$ and $(13,3,5)$ are coplanar. Answer: the edge vectors $(0,-3,-2)$, $(5,-4,-1)$, $(11,2,5)$ have triple product 0. → [[#The coplanarity test]]

## Transcript and slide slips

> [!warning] James §4.2.12, p. 270: the volume needs a modulus
> Where: [[#1. The scalar triple product]]
> James concludes $(\mathbf a\times\mathbf b)\cdot\mathbf c=$ volume of the parallelepiped. The unit vector $\mathbf k$ in the proof is perpendicular to $\mathbf a$ and $\mathbf b$ but can point up or down, so the triple product is negative for a left-handed ordering; the volume is $|(\mathbf a\times\mathbf b)\cdot\mathbf c|$ (Module 15 work scheme, item 1). Exercise 57 is an instance: the determinant is $-15$ and the volume 15.

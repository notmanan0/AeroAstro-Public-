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
status: lectured
coverage: "Module Booklet Module 14 work scheme; James §4.1–4.2.11 (coordinates and direction cosines, vector addition, Cartesian components, the scalar product, the vector product and its applications to normals, areas, moments and rotating bodies), plus the triple vector product a×(b×c) met in James Example 4.24"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: []
next_topics: ["[[MATH1054 M15 - Vectors II]]"]
key_concepts: ["[[Vector Algebra and Components]]", "[[Scalar (Dot) Product]]", "[[Vector (Cross) Product]]"]
tutorial_sheets: ["[[MATH1054 M14 Solutions - Vectors I]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 14)", "02 - Sources/Modern Engineering Mathematics.pdf (§4.1–4.2.11)"]
---

# MATH1054 M14 - Vectors I

> [!abstract] Summary
> A vector has a magnitude and a direction, and in right-handed Cartesian axes it is the triple of its components, $\mathbf a=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$, added and scaled component by component. Two products are defined: the scalar product $\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta=a_1b_1+a_2b_2+a_3b_3$, a number that gives angles, components and work, and the vector product $\mathbf a\times\mathbf b=|\mathbf a||\mathbf b|\sin\theta\,\hat{\mathbf n}$, a vector normal to both inputs whose component form is a $3\times3$ determinant and which gives areas, moments $\mathbf M=\mathbf r\times\mathbf F$ and rigid-body velocities $\mathbf v=\boldsymbol\omega\times\mathbf r$. The cross product is not associative; the triple vector product obeys $\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives points, forces or velocities in $\mathbf i,\mathbf j,\mathbf k$ form and asks for a length, unit vector, angle, work done, resolved part, unit normal, triangle area, moment about a point or the velocity of a point on a rotating body.
> - **Assumptions:** right-handed Cartesian axes; the angle $\theta$ between two vectors lies in $[0,\pi]$; a moment is taken about a stated point, and the angular velocity axis passes through a stated point.
> - **Method:** 1. Turn every "magnitude $F$ in the direction $\mathbf d$" into $\mathbf F=F\,\mathbf d/|\mathbf d|$. 2. Form displacement vectors as end minus start, $\overrightarrow{\mathrm{AB}}=\mathbf b-\mathbf a$. 3. Dot product for angles, work and components; cross product for normals, areas, moments and velocities. 4. Keep the order: $\mathbf r\times\mathbf F$ and $\boldsymbol\omega\times\mathbf r$, with $\mathbf r$ from the reference point. 5. Check a cross product by dotting it with both inputs (both must give 0).
> - **Common mistakes:** using the direction vector $\mathbf d$ as if it were the force, without normalising; losing the minus sign on the middle ($\mathbf j$) term of the determinant.
> - **Practise:** [[#A force of 4 units about A (Example 4.28)]] · [[MATH1054 M14 Solutions - Vectors I#Exercise 52: Moment about A]]

A scalar is a quantity fixed by one number in suitable units, such as a mass, a temperature or a length. A vector also carries a direction, and it must add by the parallelogram rule: forces, displacements, velocities and accelerations do, which is what makes them vectors. Once axes are fixed, a vector is just three numbers, and every geometric construction (adding forces head to tail, finding the angle between two members of a frame, finding the normal to a panel) becomes arithmetic on those numbers.

Two kinds of product turn up because engineering needs two kinds of answer. The work done by a force, or the component of a force along a member, is a single number that depends on how well two directions line up; that is the scalar product, which uses $\cos\theta$. The turning effect of a force about a point has its own direction, the axis about which it tends to turn the body, and a size that depends on how far the force is from lining up with the position vector; that is the vector product, which uses $\sin\theta$ and points along the normal. The same product gives the area of a triangle and the velocity of a point on a spinning body.

This is the working language of statics and dynamics: [[Free Body Diagram and Equilibrium|equilibrium]] is $\sum\mathbf F=\mathbf0$ and $\sum\mathbf M=\mathbf0$, work is $\int\mathbf F\cdot d\mathbf r$ in [[FEEG1002 D3 - Work, Energy and Power]], angular momentum is $\mathbf r\times m\mathbf v$ in [[FEEG1002 D5 - Angular Impulse and Momentum]], and rigid-body kinematics is $\mathbf v_B=\mathbf v_A+\boldsymbol\omega\times\mathbf r_{B/A}$ in [[FEEG1002 D7 - Kinematics of Rigid Bodies]]. [[MATH1054 M15 - Vectors II]] builds the scalar triple product, lines and planes on these two products, and the Year 2 vector calculus of [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives|MATH2048 VC1]] and [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities|VC2]] uses both of them inside every gradient, divergence and curl.

---

## 1. Coordinates, length and direction cosines

Points are located by rectangular Cartesian axes $Oxyz$, taken **right-handed**: turning a right-handed screw from $Ox$ towards $Oy$ drives it along $Oz$, and likewise $Oy\to Oz$ drives it along $Ox$ and $Oz\to Ox$ along $Oy$. If $y$ and $z$ lie in the plane of the paper, $x$ points out of it. The convention matters for the vector product in §6, where swapping it would flip every answer.

The length $r=\mathrm{OP}$ of the line from the origin to $\mathrm P(x,y,z)$ follows from Pythagoras twice. Let $\mathrm M=(x,y,0)$ be the foot of the perpendicular from P to the $xy$-plane. In the right-angled triangle with legs $x$ and $y$,

$$
\mathrm{OM}^2=x^2+y^2 .
$$

The triangle OMP has a right angle at M, because MP is parallel to $Oz$, so

$$
\begin{aligned}
r^2&=\mathrm{OM}^2+\mathrm{MP}^2\\
&=x^2+y^2+z^2,\\
r&=\sqrt{x^2+y^2+z^2}.
\end{aligned}
$$

Let $\alpha$, $\beta$, $\gamma$ be the angles that OP makes with the positive $x$, $y$ and $z$ axes. The projection of OP on the $x$ axis has length $x$, so in the right-angled triangle formed by O, P and the foot of the perpendicular from P to $Ox$, $\cos\alpha=x/r$. The **direction cosines** of OP are

$$
l=\cos\alpha=\frac xr,\qquad m=\cos\beta=\frac yr,\qquad n=\cos\gamma=\frac zr .
$$

They are not independent:

$$
\begin{aligned}
l^2+m^2+n^2&=\frac{x^2}{r^2}+\frac{y^2}{r^2}+\frac{z^2}{r^2}\\
&=\frac{x^2+y^2+z^2}{r^2}\\
&=\frac{r^2}{r^2}\\
&=1 .
\end{aligned}
$$

### Length and direction cosines of OP (Example 4.1)

For $\mathrm P=(2,-1,3)$,

$$
\begin{aligned}
\mathrm{OP}^2&=2^2+(-1)^2+3^2\\
&=4+1+9\\
&=14,\\
\mathrm{OP}&=\sqrt{14}\approx3.742 .
\end{aligned}
$$

The direction cosines are

$$
(l,m,n)=\Big(\frac2{\sqrt{14}},\,-\frac1{\sqrt{14}},\,\frac3{\sqrt{14}}\Big)\approx(0.535,\,-0.267,\,0.802),
$$

and $l^2+m^2+n^2=\frac{4+1+9}{14}=1$.

The identity lets two measured angles fix the third. In Example 4.2 (James, not set in the work scheme) a theodolite at O measures $\angle\mathrm{TO}x=66°$ and $\angle\mathrm{TO}z=57°$ to the top T of a spire of height 35 m. Then $l=\cos66°=0.40674$ and $n=\cos57°=0.54464$, so

$$
\begin{aligned}
m^2&=1-l^2-n^2\\
&=1-0.16544-0.29663\\
&=0.53793,\\
m&=0.73344\quad(\text{taking the root with }y>0),
\end{aligned}
$$

and $\angle\mathrm{TO}y=\cos^{-1}0.73344=42.82°$. The height gives the distance, $r=35/n=64.26$ m, and then $x=rl=26.14$ m and $y=rm=47.13$ m, so $\mathrm T=(26.14,\,47.13,\,35)$.

## 2. Vectors and how they combine

A vector is represented by a directed line segment whose length is its magnitude and whose arrow gives its sense. The starting point is irrelevant: two segments of equal length, direction and sense represent the same vector. In print a vector is bold, $\mathbf a$; in handwriting it is underlined, $\underline a$, and the written work must always distinguish the vector $\mathbf a$ from its magnitude $a=|\mathbf a|$.

The basic properties are these. Two vectors are **equal** when they have the same magnitude, direction and sense. Multiplying by a scalar $\lambda$ gives $\lambda\mathbf b$, of magnitude $|\lambda||\mathbf b|$, in the direction of $\mathbf b$ if $\lambda>0$ and opposite to it if $\lambda<0$; in either case $\lambda\mathbf b$ is **parallel** to $\mathbf b$ (the $\lambda<0$ case is sometimes called antiparallel, though most authors just say parallel). The **modulus** $|\mathbf a|$ is the length; a vector of modulus 1 is a **unit vector**, written $\hat{\mathbf a}$, and every non-zero vector is its modulus times its unit vector,

$$
\mathbf a=|\mathbf a|\,\hat{\mathbf a},\qquad\hat{\mathbf a}=\frac{\mathbf a}{|\mathbf a|}.
$$

The **zero vector** $\mathbf0$ has zero length and no defined direction.

Vectors add by the **parallelogram rule**: $\mathbf a+\mathbf b$ is the diagonal of the parallelogram with $\mathbf a$ and $\mathbf b$ as adjacent sides. Since opposite sides of a parallelogram represent the same vector, this is the same as the **triangle law**: place $\mathbf b$ with its tail at the head of $\mathbf a$, and the sum runs from the tail of $\mathbf a$ to the head of $\mathbf b$. Repeating the triangle law gives the **polygon law**: the sum of vectors drawn head to tail is the closing side from the first tail to the last head. Addition is commutative, $\mathbf a+\mathbf b=\mathbf b+\mathbf a$ (the two routes round the parallelogram), and associative, $(\mathbf a+\mathbf b)+\mathbf c=\mathbf a+(\mathbf b+\mathbf c)$, so brackets and order can be dropped. Scalar multiplication distributes, $\lambda(\mathbf a+\mathbf b)=\lambda\mathbf a+\lambda\mathbf b$, because scaling the triangle of $\mathbf a$, $\mathbf b$ and $\mathbf a+\mathbf b$ by $\lambda$ gives a similar triangle.

Subtraction is addition of the negative, $\mathbf a-\mathbf b=\mathbf a+(-\mathbf b)$. With $\overrightarrow{\mathrm{OA}}=\mathbf a$ and $\overrightarrow{\mathrm{OB}}=\mathbf b$, the triangle law in triangle OBA gives

$$
\begin{aligned}
\overrightarrow{\mathrm{BA}}&=\overrightarrow{\mathrm{BO}}+\overrightarrow{\mathrm{OA}}\\
&=-\overrightarrow{\mathrm{OB}}+\overrightarrow{\mathrm{OA}}\\
&=\mathbf a-\mathbf b .
\end{aligned}
$$

In words, the vector from one point to another is "end minus start". Applied to any closed polygon, the polygon law says that going round and returning to the start gives zero total displacement: **a closed loop of vectors sums to $\mathbf0$**.

### Vectors round a quadrilateral (Example 4.4)

In the figure for this example (James Fig. 4.14) the arrows are $\mathbf a=\overrightarrow{\mathrm{AO}}$, $\mathbf b=\overrightarrow{\mathrm{OB}}$, $\mathbf c=\overrightarrow{\mathrm{OC}}$, $\mathbf d=\overrightarrow{\mathrm{OD}}$ and, round the quadrilateral ABCD, $\mathbf g=\overrightarrow{\mathrm{AB}}$, $\mathbf f=\overrightarrow{\mathrm{CB}}$, $\mathbf e=\overrightarrow{\mathrm{CD}}$, $\mathbf h=\overrightarrow{\mathrm{AD}}$. Each side follows from a triangle through O:

$$
\begin{aligned}
\mathbf g&=\overrightarrow{\mathrm{AO}}+\overrightarrow{\mathrm{OB}}=\mathbf a+\mathbf b,\\
\mathbf f&=\overrightarrow{\mathrm{OB}}-\overrightarrow{\mathrm{OC}}=\mathbf b-\mathbf c,\\
\mathbf e&=\overrightarrow{\mathrm{OD}}-\overrightarrow{\mathrm{OC}}=\mathbf d-\mathbf c .
\end{aligned}
$$

For $\mathbf e$ in terms of $\mathbf f$, $\mathbf g$, $\mathbf h$, go round the closed loop $\mathrm{C\to D\to A\to B\to C}$:

$$
\begin{aligned}
\overrightarrow{\mathrm{CD}}+\overrightarrow{\mathrm{DA}}+\overrightarrow{\mathrm{AB}}+\overrightarrow{\mathrm{BC}}&=\mathbf0\\
\mathbf e+(-\mathbf h)+\mathbf g+(-\mathbf f)&=\mathbf0\\
\mathbf e&=\mathbf f-\mathbf g+\mathbf h .
\end{aligned}
$$

The signs depend entirely on which way each arrow points, so read them off the figure before writing anything.

### The quadrilateral OACB (Example 4.5)

With $\overrightarrow{\mathrm{OA}}=\mathbf a$, $\overrightarrow{\mathrm{OB}}=\mathbf b$ and $\overrightarrow{\mathrm{OC}}=\mathbf b+\tfrac12\mathbf a$,

$$
\begin{aligned}
\overrightarrow{\mathrm{BC}}&=\overrightarrow{\mathrm{OC}}-\overrightarrow{\mathrm{OB}}=\big(\mathbf b+\tfrac12\mathbf a\big)-\mathbf b=\tfrac12\mathbf a,\\
\overrightarrow{\mathrm{CA}}&=\overrightarrow{\mathrm{OA}}-\overrightarrow{\mathrm{OC}}=\mathbf a-\big(\mathbf b+\tfrac12\mathbf a\big)=\tfrac12\mathbf a-\mathbf b .
\end{aligned}
$$

BC is parallel to OA and half its length, so OACB is a trapezium.

### Resultant of two forces (Example 4.6)

A force $\mathbf F$ of 2 N and a force $\mathbf F'$ of 1 N act at O with $60°$ between them. Resolve along $\mathbf F$ and perpendicular to it. Placing $\mathbf F'$ at the head A of $\mathbf F$ (triangle law), its head C is $1\cos60°=\tfrac12$ further along the line of $\mathbf F$ and $1\sin60°=\tfrac{\sqrt3}2$ to the side. If N is the foot of the perpendicular from C to the line of $\mathbf F$,

$$
\mathrm{ON}=2+\tfrac12=\tfrac52,\qquad\mathrm{CN}=\tfrac{\sqrt3}2 .
$$

Pythagoras in triangle ONC gives the magnitude of $\mathbf R=\mathbf F+\mathbf F'$:

$$
\begin{aligned}
|\mathbf R|^2&=\big(\tfrac52\big)^2+\big(\tfrac{\sqrt3}2\big)^2\\
&=\tfrac{25}4+\tfrac34\\
&=7,\\
|\mathbf R|&=\sqrt7\approx2.646\ \text{N}.
\end{aligned}
$$

The angle $\alpha$ between $\mathbf R$ and $\mathbf F$ is

$$
\tan\alpha=\frac{\mathrm{CN}}{\mathrm{ON}}=\frac{\sqrt3/2}{5/2}=\frac{\sqrt3}5,\qquad\alpha=19.1° .
$$

### Midpoints of a quadrilateral (Specimen Test 14, Q1(i))

ABCD has $\overrightarrow{\mathrm{AB}}=\mathbf a$, $\overrightarrow{\mathrm{BC}}=\mathbf b$, $\overrightarrow{\mathrm{CD}}=\mathbf c$, with E the midpoint of AB and G the midpoint of CD. The polygon law gives

$$
\overrightarrow{\mathrm{AC}}=\mathbf a+\mathbf b,\qquad\overrightarrow{\mathrm{AD}}=\mathbf a+\mathbf b+\mathbf c,
$$

and, going E to B to C to G,

$$
\begin{aligned}
\overrightarrow{\mathrm{EG}}&=\overrightarrow{\mathrm{EB}}+\overrightarrow{\mathrm{BC}}+\overrightarrow{\mathrm{CG}}\\
&=\tfrac12\mathbf a+\mathbf b+\tfrac12\mathbf c .
\end{aligned}
$$

Part (ii) of this question uses the scalar product and is in §5.

## 3. Relative velocity

Let A and B move with position vectors $\mathbf r_A(t)$ and $\mathbf r_B(t)$. The position of B relative to A is end minus start,

$$
\mathbf r_{B/A}=\mathbf r_B-\mathbf r_A .
$$

Differentiating with respect to time, with the axes not rotating,

$$
\mathbf v_{B/A}=\frac{d\mathbf r_B}{dt}-\frac{d\mathbf r_A}{dt}=\mathbf v_B-\mathbf v_A .
$$

So the **apparent velocity** of B as seen by an observer moving with A is $\mathbf v_B-\mathbf v_A$; equivalently, the true velocity of B is $\mathbf v_B=\mathbf v_A+\mathbf v_{B/A}$. A pilot's velocity through the air plus the velocity of the air over the ground gives the velocity over the ground, and the wind felt by a cyclist is the true wind minus the cyclist's velocity.

> [!warning] Winds are named by where they come from
> A "north-west wind" blows from the north-west towards the south-east. With $\mathbf i$ east and $\mathbf j$ north, a 50-knot NW wind is $\frac{50}{\sqrt2}(\mathbf i-\mathbf j)$, not $\frac{50}{\sqrt2}(-\mathbf i+\mathbf j)$.

### Aircraft in a north-west wind (Example 4.7)

An aircraft flies at 400 knots through the air in a 50-knot NW wind, and the pilot wants to track due west. Take $\mathbf i$ east and $\mathbf j$ north. The wind is

$$
\mathbf w=50\Big(\frac1{\sqrt2},-\frac1{\sqrt2}\Big)=(25\sqrt2,\,-25\sqrt2)\approx(35.36,\,-35.36).
$$

Let the aircraft head at $\alpha$ north of west, so its air velocity is $\mathbf a=400(-\cos\alpha,\,\sin\alpha)$. The ground velocity is

$$
\mathbf a+\mathbf w=\big(-400\cos\alpha+25\sqrt2,\ \ 400\sin\alpha-25\sqrt2\big).
$$

Due west means the $\mathbf j$ component vanishes:

$$
\begin{aligned}
400\sin\alpha-25\sqrt2&=0\\
\sin\alpha&=\frac{25\sqrt2}{400}=\frac{\sqrt2}{16}\\
\alpha&=5.07° .
\end{aligned}
$$

The heading is $5.07°$ north of west, a bearing of about $275°$. The ground speed is the size of the remaining $\mathbf i$ component:

$$
\begin{aligned}
400\cos\alpha-25\sqrt2&=398.43-35.36\\
&=363.1\ \text{knots}.
\end{aligned}
$$

### The cyclist and the wind (Exercise 9)

A cyclist riding east at 8 km/h feels the wind coming from the north; at 16 km/h it seems to come from the north-east. Let the true wind be $\mathbf w=(p,q)$. The wind felt is $\mathbf w-\mathbf v$.

At $\mathbf v=(8,0)$ the felt wind $(p-8,\,q)$ comes from the north, so it points due south: $p-8=0$ and $q<0$, so $p=8$.

At $\mathbf v=(16,0)$ the felt wind $(p-16,\,q)=(-8,\,q)$ comes from the north-east, so it points south-west and its two components are equal: $q=-8$.

$$
\mathbf w=(8,-8)\ \text{km/h},\qquad|\mathbf w|=8\sqrt2\approx11.3\ \text{km/h},
$$

blowing towards the south-east, which is a wind **from the north-west**.

![[m1054_relative_velocity.png|760]]

## 4. Cartesian components

Let $\mathbf i$, $\mathbf j$, $\mathbf k$ be unit vectors along $Ox$, $Oy$, $Oz$. For $\mathrm P=(x,y,z)$ let X be $(x,0,0)$ and M be $(x,y,0)$. The triangle law in triangle OXM and then in triangle OMP gives

$$
\begin{aligned}
\overrightarrow{\mathrm{OM}}&=\overrightarrow{\mathrm{OX}}+\overrightarrow{\mathrm{XM}}=x\mathbf i+y\mathbf j,\\
\overrightarrow{\mathrm{OP}}&=\overrightarrow{\mathrm{OM}}+\overrightarrow{\mathrm{MP}}=x\mathbf i+y\mathbf j+z\mathbf k .
\end{aligned}
$$

Every vector can be written this way, and $\mathbf a=(a_1,a_2,a_3)$ means $a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$. The geometric rules of §2 become rules on components. Two vectors are equal exactly when all three components agree, and $\mathbf0=(0,0,0)$. For the sum, project the parallelogram on the $x$ axis: the side $\mathbf b$ placed at the head of $\mathbf a$ has the same $x$-extent $b_1$ wherever it is drawn, so the $x$ component of $\mathbf a+\mathbf b$ is $a_1+b_1$, and likewise for $y$ and $z$:

$$
\mathbf a+\mathbf b=(a_1+b_1,\,a_2+b_2,\,a_3+b_3),\qquad\lambda\mathbf a=(\lambda a_1,\lambda a_2,\lambda a_3),\qquad\mathbf a-\mathbf b=(a_1-b_1,\,a_2-b_2,\,a_3-b_3).
$$

The distributive law is then ordinary arithmetic:

$$
\begin{aligned}
\lambda(\mathbf a+\mathbf b)&=\big(\lambda(a_1+b_1),\,\lambda(a_2+b_2),\,\lambda(a_3+b_3)\big)\\
&=(\lambda a_1+\lambda b_1,\,\lambda a_2+\lambda b_2,\,\lambda a_3+\lambda b_3)\\
&=(\lambda a_1,\lambda a_2,\lambda a_3)+(\lambda b_1,\lambda b_2,\lambda b_3)\\
&=\lambda\mathbf a+\lambda\mathbf b .
\end{aligned}
$$

From §1, the magnitude and unit vector are

$$
|\mathbf a|=\sqrt{a_1^2+a_2^2+a_3^2},\qquad\hat{\mathbf a}=\frac{\mathbf a}{|\mathbf a|}=\Big(\frac{a_1}{|\mathbf a|},\frac{a_2}{|\mathbf a|},\frac{a_3}{|\mathbf a|}\Big),
$$

so **the direction cosines of $\mathbf a$ are the components of $\hat{\mathbf a}$**, $(l,m,n)=\hat{\mathbf a}$.

Three standard moves follow. A point with position vector $\mathbf a=\overrightarrow{\mathrm{OA}}$ and another with $\mathbf b$ are joined by $\overrightarrow{\mathrm{AB}}=\mathbf b-\mathbf a$ (§2). A quantity given as "magnitude $F$ in the direction of $\mathbf d$" is $\mathbf F=F\hat{\mathbf d}=F\,\mathbf d/|\mathbf d|$. Three points P, Q, R are **collinear** when $\overrightarrow{\mathrm{PQ}}=\lambda\overrightarrow{\mathrm{QR}}$ for some scalar $\lambda$: the two vectors are parallel and share the point Q, so they lie on one line, and $|\lambda|$ is the ratio $\mathrm{PQ}:\mathrm{QR}$.

### Basic component arithmetic (Example 4.10)

With $\mathbf a=(1,1,1)$, $\mathbf b=(-1,2,3)$, $\mathbf c=(0,3,4)$: $\mathbf a+\mathbf b=(0,3,4)$; $2\mathbf a-\mathbf b=(2+1,\,2-2,\,2-3)=(3,0,-1)$; $\mathbf a+\mathbf b-\mathbf c=(0,0,0)=\mathbf0$; and $|\mathbf c|=\sqrt{0+9+16}=5$, so $\hat{\mathbf c}=\big(0,\tfrac35,\tfrac45\big)$.

### A combination, its length and direction cosines (Example 4.11)

With $\mathbf a=(2,-3,1)$, $\mathbf b=(1,5,-2)$, $\mathbf c=(3,-4,3)$,

$$
\begin{aligned}
\mathbf d&=\mathbf a-2\mathbf b+3\mathbf c\\
&=(2,-3,1)-(2,10,-4)+(9,-12,9)\\
&=(2-2+9,\ -3-10-12,\ 1+4+9)\\
&=(9,-25,14).
\end{aligned}
$$

Its magnitude is $|\mathbf d|=\sqrt{81+625+196}=\sqrt{902}\approx30.03$, so

$$
\hat{\mathbf d}=\frac1{\sqrt{902}}(9,-25,14),
$$

and the direction cosines are $\big(\frac9{\sqrt{902}},\frac{-25}{\sqrt{902}},\frac{14}{\sqrt{902}}\big)\approx(0.300,-0.832,0.466)$.

### The tetrahedral molecule (Example 4.12)

The X atom of a molecule $\mathrm{XY_3}$ is at $(2\sqrt3+\sqrt2,\,0,\,-2+\sqrt6)$ and the Y atoms are at $\mathrm Y(\sqrt3,-2,-1)$, $\mathrm Y'(\sqrt3,2,-1)$, $\mathrm Y''(\sqrt2,0,\sqrt6)$. For the bond XY,

$$
\overrightarrow{\mathrm{XY}}=\overrightarrow{\mathrm{OY}}-\overrightarrow{\mathrm{OX}}=\big(-\sqrt3-\sqrt2,\ -2,\ 1-\sqrt6\big),
$$

$$
\begin{aligned}
|\overrightarrow{\mathrm{XY}}|^2&=(\sqrt3+\sqrt2)^2+(-2)^2+(1-\sqrt6)^2\\
&=(5+2\sqrt6)+4+(7-2\sqrt6)\\
&=16,
\end{aligned}
$$

so $\mathrm{XY}=4$. The same working gives $\mathrm{XY'}=\mathrm{XY''}=4$, and the Y–Y edges are also 4 (for instance $\overrightarrow{\mathrm{YY'}}=(0,4,0)$), so the molecule is a regular tetrahedron of edge 4. For part (b), with $\overrightarrow{\mathrm{Y'Y''}}=(\sqrt2-\sqrt3,\,-2,\,\sqrt6+1)$ and $\overrightarrow{\mathrm{Y''X}}=(2\sqrt3,\,0,\,-2)$,

$$
\overrightarrow{\mathrm{XY}}+\overrightarrow{\mathrm{YY'}}+\overrightarrow{\mathrm{Y'Y''}}+\overrightarrow{\mathrm{Y''X}}=\mathbf0,
$$

the polygon law for the closed path $\mathrm{X\to Y\to Y'\to Y''\to X}$. The printed question has $\overrightarrow{\mathrm{Y''Y}}$ as the last vector, a misprint: with it the last three terms cancel among themselves and the sum is $\overrightarrow{\mathrm{XY}}\ne\mathbf0$, so the closing vector must be $\overrightarrow{\mathrm{Y''X}}$, which is what the printed solution uses.

### Resultant and equilibrant of three forces (Example 4.13)

$\mathbf F_1=(1,1,1)$ N, $\mathbf F_2$ has magnitude 6 along $(1,2,-2)$, and $\mathbf F_3$ has magnitude 10 along $(3,-4,0)$. Since $|(1,2,-2)|=3$ and $|(3,-4,0)|=5$,

$$
\mathbf F_2=6\cdot\tfrac13(1,2,-2)=(2,4,-4),\qquad\mathbf F_3=10\cdot\tfrac15(3,-4,0)=(6,-8,0).
$$

$$
\begin{aligned}
\mathbf R&=(1,1,1)+(2,4,-4)+(6,-8,0)\\
&=(9,-3,-3)\ \text{N},
\end{aligned}
$$

with $|\mathbf R|=\sqrt{81+9+9}=3\sqrt{11}\approx9.95$ N. The **equilibrant**, the extra force that brings the total to zero, is $-\mathbf R=(-9,3,3)$ N.

### A displacement and a collinearity test (Exercises 12 and 19)

For $\mathrm P=(1,3,-7)$ and $\mathrm Q=(5,-2,4)$, $\overrightarrow{\mathrm{PQ}}=(4,-5,11)$, $|\mathrm{PQ}|=\sqrt{16+25+121}=\sqrt{162}=9\sqrt2\approx12.73$, and the direction cosines are $\frac1{9\sqrt2}(4,-5,11)\approx(0.314,-0.393,0.864)$.

For $\mathrm P(1,-3,4)$, $\mathrm Q(2,2,1)$, $\mathrm R(3,7,-2)$,

$$
\overrightarrow{\mathrm{PQ}}=(1,5,-3),\qquad\overrightarrow{\mathrm{QR}}=(1,5,-3),
$$

so $\overrightarrow{\mathrm{PQ}}=1\cdot\overrightarrow{\mathrm{QR}}$: P, Q, R are collinear, $\mathrm{PQ}:\mathrm{QR}=1:1$, and Q is the midpoint of PR.

## 5. The scalar product

The component of a vector $\mathbf a$ in a direction OP is $|\mathbf a|\cos\theta$, where $\theta$ is the angle between them. The work done by a constant force $\mathbf F$ whose point of application moves through the displacement $\mathbf a$ is the distance moved times the component of the force along it, $|\mathbf F||\mathbf a|\cos\theta$. That expression defines the **scalar product** (dot product):

$$
\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta,\qquad0\le\theta\le\pi .
$$

The result is a number, and the dot between the two vectors is essential: the product is defined only between two vectors.

![[m1054_dot_product_geometry.png|900]]

### The component form from the cosine rule

Let $\overrightarrow{\mathrm{OA}}=\mathbf a$ and $\overrightarrow{\mathrm{OB}}=\mathbf b$ with angle $\theta$ at O (panel (a) above). The third side is $\overrightarrow{\mathrm{BA}}=\mathbf a-\mathbf b$, and the cosine rule in triangle OAB is

$$
\mathrm{AB}^2=\mathrm{OA}^2+\mathrm{OB}^2-2(\mathrm{OA})(\mathrm{OB})\cos\theta .
$$

Write each length squared in components:

$$
(a_1-b_1)^2+(a_2-b_2)^2+(a_3-b_3)^2=(a_1^2+a_2^2+a_3^2)+(b_1^2+b_2^2+b_3^2)-2|\mathbf a||\mathbf b|\cos\theta .
$$

Expand the left-hand side:

$$
a_1^2-2a_1b_1+b_1^2+a_2^2-2a_2b_2+b_2^2+a_3^2-2a_3b_3+b_3^2=a_1^2+a_2^2+a_3^2+b_1^2+b_2^2+b_3^2-2|\mathbf a||\mathbf b|\cos\theta .
$$

Cancel the six squares that appear on both sides:

$$
-2a_1b_1-2a_2b_2-2a_3b_3=-2|\mathbf a||\mathbf b|\cos\theta .
$$

Divide by $-2$:

$$
\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta=a_1b_1+a_2b_2+a_3b_3 .
$$

Both forms must be known: the geometric one to interpret, the component one to compute.

### Properties, proved from the components

The order does not matter, $\mathbf a\cdot\mathbf b=\mathbf b\cdot\mathbf a$, because $a_ib_i=b_ia_i$ in each term. Scalars come out, $\mathbf a\cdot(\lambda\mathbf b)=(\lambda\mathbf a)\cdot\mathbf b=\lambda(\mathbf a\cdot\mathbf b)$, because $\lambda$ is a common factor of every term. There is no associative law: $\mathbf a\cdot\mathbf b$ is a scalar and cannot be dotted with a third vector, so $\mathbf a\cdot\mathbf b\cdot\mathbf c$ is meaningless. The product distributes over addition:

$$
\begin{aligned}
\mathbf a\cdot(\mathbf b+\mathbf c)&=a_1(b_1+c_1)+a_2(b_2+c_2)+a_3(b_3+c_3)\\
&=(a_1b_1+a_2b_2+a_3b_3)+(a_1c_1+a_2c_2+a_3c_3)\\
&=\mathbf a\cdot\mathbf b+\mathbf a\cdot\mathbf c .
\end{aligned}
$$

A vector dotted with itself has $\theta=0$:

$$
\mathbf a\cdot\mathbf a=a_1^2+a_2^2+a_3^2=|\mathbf a|^2,
$$

which is often written $\mathbf a^2$ or $a^2$; no other power of a vector exists. For the unit vectors,

$$
\mathbf i\cdot\mathbf i=\mathbf j\cdot\mathbf j=\mathbf k\cdot\mathbf k=1,\qquad\mathbf i\cdot\mathbf j=\mathbf j\cdot\mathbf k=\mathbf k\cdot\mathbf i=0 .
$$

### The component form from the unit vectors

The same formula follows without the cosine rule. Distributivity holds geometrically, because the projection of $\mathbf b+\mathbf c$ onto the direction of $\mathbf a$ is the sum of the projections of $\mathbf b$ and $\mathbf c$ (project the triangle of $\mathbf b$, $\mathbf c$ and $\mathbf b+\mathbf c$ onto that line). Expand the product of $\mathbf a=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$ and $\mathbf b=b_1\mathbf i+b_2\mathbf j+b_3\mathbf k$ term by term:

$$
\begin{aligned}
\mathbf a\cdot\mathbf b&=(a_1\mathbf i+a_2\mathbf j+a_3\mathbf k)\cdot(b_1\mathbf i+b_2\mathbf j+b_3\mathbf k)\\
&=a_1b_1\,\mathbf i\cdot\mathbf i+a_1b_2\,\mathbf i\cdot\mathbf j+a_1b_3\,\mathbf i\cdot\mathbf k\\
&\quad+a_2b_1\,\mathbf j\cdot\mathbf i+a_2b_2\,\mathbf j\cdot\mathbf j+a_2b_3\,\mathbf j\cdot\mathbf k\\
&\quad+a_3b_1\,\mathbf k\cdot\mathbf i+a_3b_2\,\mathbf k\cdot\mathbf j+a_3b_3\,\mathbf k\cdot\mathbf k\\
&=a_1b_1(1)+a_2b_2(1)+a_3b_3(1)+0\\
&=a_1b_1+a_2b_2+a_3b_3 .
\end{aligned}
$$

### Angles and perpendicular vectors

Rearranging the definition gives the angle between two non-zero vectors,

$$
\cos\theta=\frac{\mathbf a\cdot\mathbf b}{|\mathbf a||\mathbf b|}=\frac{a_1b_1+a_2b_2+a_3b_3}{\sqrt{a_1^2+a_2^2+a_3^2}\sqrt{b_1^2+b_2^2+b_3^2}} .
$$

The sign of $\mathbf a\cdot\mathbf b$ says whether $\theta$ is acute ($>0$), a right angle ($=0$) or obtuse ($<0$). Perpendicular vectors have $\cos\frac\pi2=0$, so $\mathbf a\cdot\mathbf b=0$. The converse needs care: $\mathbf a\cdot\mathbf b=0$ means either $\mathbf a=\mathbf0$, or $\mathbf b=\mathbf0$, or $\theta=\frac\pi2$, and perpendicularity follows only once the first two are ruled out.

For Example 4.18, $\mathbf a=(1,2,3)$ and $\mathbf b=(2,0,4)$:

$$
\begin{aligned}
\cos\theta&=\frac{2+0+12}{\sqrt{14}\sqrt{20}}\\
&=\frac{14}{\sqrt{280}}=\sqrt{\tfrac7{10}}=0.8367,\\
\theta&=33.2° .
\end{aligned}
$$

For Example 4.19, $(1,0,1)\cdot(0,1,0)=0$ and neither vector is zero, so they are perpendicular: the first lies in the $xz$-plane and the second along $Oy$.

> [!warning] A vector cannot be cancelled from a dot product
> From $\mathbf a\cdot\mathbf b=\mathbf a\cdot\mathbf c$ it follows only that $\mathbf a\cdot(\mathbf b-\mathbf c)=0$: either $\mathbf a=\mathbf0$, or $\mathbf b=\mathbf c$, or $\mathbf a\perp(\mathbf b-\mathbf c)$. In Example 4.20, $\mathbf a=(1,1,1)$, $\mathbf b=(3,2,-3)$, $\mathbf c=(-1,4,-1)$ give $\mathbf a\cdot\mathbf b=3+2-3=2$ and $\mathbf a\cdot\mathbf c=-1+4-1=2$, yet $\mathbf b\ne\mathbf c$; instead $\mathbf a$ is perpendicular to $\mathbf b-\mathbf c=(4,-2,-2)$.

Exercise 28(c) uses the perpendicular test to fix a parameter. With $\mathbf u=(4,0,-2)$ and $\mathbf v=(3,1,-1)$, the vectors $\mathbf u+\lambda\mathbf k$ and $\mathbf v-\lambda\mathbf i$ are perpendicular when

$$
\begin{aligned}
(4,\,0,\,-2+\lambda)\cdot(3-\lambda,\,1,\,-1)&=0\\
12-4\lambda+0+2-\lambda&=0\\
14-5\lambda&=0\\
\lambda&=\tfrac{14}5 .
\end{aligned}
$$

### Components, resolved parts and work

If $\hat{\mathbf u}$ is a unit vector, then

$$
\mathbf F\cdot\hat{\mathbf u}=|\mathbf F||\hat{\mathbf u}|\cos\theta=|\mathbf F|\cos\theta,
$$

which is the **component** (or **resolved part**) of $\mathbf F$ in the direction of $\hat{\mathbf u}$, the signed length ON in panel (b) of the figure. If the direction is given by a vector $\mathbf u$ that is not a unit vector, divide by its length first: the component is $\mathbf F\cdot\mathbf u/|\mathbf u|$. The vector part of $\mathbf F$ along $\mathbf u$ is that component times the unit vector, $(\mathbf F\cdot\hat{\mathbf u})\hat{\mathbf u}$. Dotting with $\mathbf i$ picks out the $x$ component, $\mathbf F\cdot\mathbf i=F_1$, which agrees with the ordinary meaning of a component.

The **work done** by a constant force $\mathbf F$ whose point of application moves through the displacement $\mathbf d$ is

$$
W=\mathbf F\cdot\mathbf d .
$$

**Example 4.22.** $\mathbf F=(3,-2,5)$ moves a particle from $\mathrm P(1,4,-1)$ to $\mathrm Q(-2,3,1)$. The displacement is $\overrightarrow{\mathrm{PQ}}=(-2,3,1)-(1,4,-1)=(-3,-1,2)$, and

$$
\begin{aligned}
W&=(3,-2,5)\cdot(-3,-1,2)\\
&=-9+2+10\\
&=3\ \text{units}.
\end{aligned}
$$

**Example 4.23.** For $\mathbf F=(2,-1,3)$: along $\mathbf i$ the component is $2$. Along $\big(\frac13,\frac23,\frac23\big)$, which is already a unit vector since $\frac19+\frac49+\frac49=1$, it is $\frac{2-2+6}3=2$. Along $(4,2,-1)$, of length $\sqrt{21}$, it is

$$
\frac{(2,-1,3)\cdot(4,2,-1)}{\sqrt{21}}=\frac{8-2-3}{\sqrt{21}}=\frac3{\sqrt{21}}\approx0.655 .
$$

**Exercise 32.** A force of 5 units along $(2,-3,1)$ is $\mathbf F=\frac5{\sqrt{14}}(2,-3,1)$. Its resolved part along $(3,2,1)$, also of length $\sqrt{14}$, is

$$
\frac5{\sqrt{14}}(2,-3,1)\cdot\frac{(3,2,1)}{\sqrt{14}}=\frac{5(6-6+1)}{14}=\frac5{14}\approx0.357\ \text{units}.
$$

**Specimen Test 14, Q5.** A 6 N force along $\mathbf i+2\mathbf j+\mathbf k$ (length $\sqrt6$) moves its point of application from $\mathrm A(0,1,0)$ to $\mathrm B(1,2,2)$:

$$
\mathbf F=\frac6{\sqrt6}(1,2,1)=\sqrt6\,(1,2,1)\ \text{N},\qquad\overrightarrow{\mathrm{AB}}=(1,1,2),
$$

$$
W=\sqrt6\,(1+2+2)=5\sqrt6\approx12.25\ \text{J}.
$$

### Lengths of sums: the cosine rule recovered

Dotting a sum with itself expands like a square, because of distributivity and commutativity:

$$
\begin{aligned}
|\mathbf b+\mathbf c|^2&=(\mathbf b+\mathbf c)\cdot(\mathbf b+\mathbf c)\\
&=\mathbf b\cdot\mathbf b+\mathbf b\cdot\mathbf c+\mathbf c\cdot\mathbf b+\mathbf c\cdot\mathbf c\\
&=b^2+2\,\mathbf b\cdot\mathbf c+c^2 .
\end{aligned}
$$

In Specimen Test 14 Q1(ii), $\mathbf b=\overrightarrow{\mathrm{BC}}$, $\mathbf c=\overrightarrow{\mathrm{CD}}$, and $\theta$ is the interior angle at C, between $\overrightarrow{\mathrm{CB}}=-\mathbf b$ and $\overrightarrow{\mathrm{CD}}=\mathbf c$. So $(-\mathbf b)\cdot\mathbf c=bc\cos\theta$, which means $\mathbf b\cdot\mathbf c=-bc\cos\theta$, and

$$
|\mathbf b+\mathbf c|=\sqrt{b^2+c^2-2bc\cos\theta},
$$

the cosine rule for the side $\mathrm{BD}=|\mathbf b+\mathbf c|$ of triangle BCD.

> [!check] Example 4.6 by the dot product
> With $|\mathbf F|=2$, $|\mathbf F'|=1$ and $60°$ between them, $|\mathbf F+\mathbf F'|^2=4+1+2(2)(1)\cos60°=7$, the same $\sqrt7$ N as the resolution in §2. The sign is $+$ here because $60°$ is the angle between the two vectors, not the interior angle of the triangle, which is $120°$.

The remaining Example 4.17 values are direct arithmetic with $\mathbf a=(1,-1,2)$, $\mathbf b=(-2,0,2)$, $\mathbf c=(3,2,1)$: $\mathbf a\cdot\mathbf c=3$, $\mathbf b\cdot\mathbf c=-4$, $(\mathbf a+\mathbf b)\cdot\mathbf c=-1=3+(-4)$, $\mathbf a\cdot(2\mathbf b+3\mathbf c)=2(2)+3(3)=13$ using $\mathbf a\cdot\mathbf b=2$, and $(\mathbf a\cdot\mathbf b)\mathbf c=(6,4,2)$, which is a vector parallel to $\mathbf c$.

## 6. The vector product

The **vector product** (cross product) of $\mathbf a$ and $\mathbf b$ is the vector

$$
\mathbf a\times\mathbf b=|\mathbf a||\mathbf b|\sin\theta\,\hat{\mathbf n},\qquad0\le\theta\le\pi,
$$

where $\hat{\mathbf n}$ is the unit vector perpendicular to both $\mathbf a$ and $\mathbf b$ such that $\mathbf a$, $\mathbf b$, $\hat{\mathbf n}$ form a right-handed set: curl the fingers of the right hand from $\mathbf a$ towards $\mathbf b$ through the angle $\theta$, and the thumb points along $\hat{\mathbf n}$. Compared with the scalar product, it uses $\sin\theta$ instead of $\cos\theta$, and the answer is a vector, not a number. Its magnitude $|\mathbf a|\,(|\mathbf b|\sin\theta)$ is base times height of the parallelogram on $\mathbf a$ and $\mathbf b$, panel (a) below.

![[m1054_cross_product_geometry.png|900]]

### Properties from the definition

Reversing the order reverses the sense of rotation from the first vector to the second, so the right-hand rule gives $-\hat{\mathbf n}$:

$$
\mathbf b\times\mathbf a=-\,\mathbf a\times\mathbf b .
$$

The product is **anti-commutative**, and the order always matters. Scalars come out, $\mathbf a\times(\lambda\mathbf b)=\lambda(\mathbf a\times\mathbf b)=(\lambda\mathbf a)\times\mathbf b$, and the product distributes over addition, $\mathbf a\times(\mathbf b+\mathbf c)=\mathbf a\times\mathbf b+\mathbf a\times\mathbf c$. The geometric proof of distributivity is long; the component form derived from it below can be checked independently to have the perpendicularity, length and handedness of the definition, which closes the loop. If $\mathbf a$ and $\mathbf b$ are parallel then $\theta=0$ or $\pi$ and $\sin\theta=0$, so $\mathbf a\times\mathbf b=\mathbf0$; in particular $\mathbf a\times\mathbf a=\mathbf0$. Conversely $\mathbf a\times\mathbf b=\mathbf0$ means $\mathbf a=\mathbf0$, or $\mathbf b=\mathbf0$, or $\mathbf a\parallel\mathbf b$. As with the dot product, $\mathbf a\times\mathbf b=\mathbf a\times\mathbf c$ does not give $\mathbf b=\mathbf c$; it gives $\mathbf a\times(\mathbf b-\mathbf c)=\mathbf0$, so $\mathbf a=\mathbf0$ or $\mathbf a\parallel(\mathbf b-\mathbf c)$ are also possible.

### The unit-vector table

For $\mathbf i\times\mathbf j$: the angle is $\frac\pi2$, so the magnitude is $1\cdot1\cdot1=1$; the only unit vectors perpendicular to both $\mathbf i$ and $\mathbf j$ are $\pm\mathbf k$; and the axes are right-handed, so the turn from $\mathbf i$ to $\mathbf j$ drives a screw along $+\mathbf k$. The same argument for the other pairs, with anti-commutativity and $\mathbf a\times\mathbf a=\mathbf0$, gives

$$
\begin{aligned}
&\mathbf i\times\mathbf i=\mathbf j\times\mathbf j=\mathbf k\times\mathbf k=\mathbf0,\\
&\mathbf i\times\mathbf j=\mathbf k,\qquad\mathbf j\times\mathbf k=\mathbf i,\qquad\mathbf k\times\mathbf i=\mathbf j,\\
&\mathbf j\times\mathbf i=-\mathbf k,\qquad\mathbf k\times\mathbf j=-\mathbf i,\qquad\mathbf i\times\mathbf k=-\mathbf j .
\end{aligned}
$$

The positive products run in the cyclic order $\mathbf i\to\mathbf j\to\mathbf k\to\mathbf i$; against that order the sign is negative.

### The component form

Expand $\mathbf a\times\mathbf b$ with distributivity and the scalar rule, keeping each product in its order:

$$
\begin{aligned}
\mathbf a\times\mathbf b&=(a_1\mathbf i+a_2\mathbf j+a_3\mathbf k)\times(b_1\mathbf i+b_2\mathbf j+b_3\mathbf k)\\
&=a_1b_1(\mathbf i\times\mathbf i)+a_1b_2(\mathbf i\times\mathbf j)+a_1b_3(\mathbf i\times\mathbf k)\\
&\quad+a_2b_1(\mathbf j\times\mathbf i)+a_2b_2(\mathbf j\times\mathbf j)+a_2b_3(\mathbf j\times\mathbf k)\\
&\quad+a_3b_1(\mathbf k\times\mathbf i)+a_3b_2(\mathbf k\times\mathbf j)+a_3b_3(\mathbf k\times\mathbf k)\\
&=0+a_1b_2\mathbf k-a_1b_3\mathbf j-a_2b_1\mathbf k+0+a_2b_3\mathbf i+a_3b_1\mathbf j-a_3b_2\mathbf i+0\\
&=(a_2b_3-a_3b_2)\mathbf i+(a_3b_1-a_1b_3)\mathbf j+(a_1b_2-a_2b_1)\mathbf k .
\end{aligned}
$$

The formula is remembered as a $3\times3$ determinant expanded along its first row (an accepted misuse of a determinant, since the first row holds vectors; see [[Determinants and Cofactors]]):

$$
\begin{aligned}
\mathbf a\times\mathbf b&=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}\\
&=\mathbf i\begin{vmatrix}a_2&a_3\\b_2&b_3\end{vmatrix}-\mathbf j\begin{vmatrix}a_1&a_3\\b_1&b_3\end{vmatrix}+\mathbf k\begin{vmatrix}a_1&a_2\\b_1&b_2\end{vmatrix}\\
&=(a_2b_3-a_3b_2)\mathbf i-(a_1b_3-a_3b_1)\mathbf j+(a_1b_2-a_2b_1)\mathbf k .
\end{aligned}
$$

The middle term carries the minus sign of the cofactor expansion, and $-(a_1b_3-a_3b_1)=a_3b_1-a_1b_3$ agrees with the line above.

> [!tip] Cross-product arithmetic without the determinant
> Write each vector's components twice in a row, $a_1\ a_2\ a_3\ a_1\ a_2$ above $b_1\ b_2\ b_3\ b_1\ b_2$. Starting from the second column, each pair of adjacent columns gives one component as (top left × bottom right) minus (top right × bottom left): $a_2b_3-a_3b_2$, then $a_3b_1-a_1b_3$, then $a_1b_2-a_2b_1$. Then check that the answer dots to zero with both inputs. For Example 4.25 below, $(10,9,7)\cdot(2,-3,1)=20-27+7=0$ and $(10,9,7)\cdot(1,2,-4)=10+18-28=0$.

### The component form has the geometric properties

Taking the component formula as given, the two geometric facts in the definition can be checked directly. It is perpendicular to $\mathbf a$:

$$
\begin{aligned}
\mathbf a\cdot(\mathbf a\times\mathbf b)&=a_1(a_2b_3-a_3b_2)+a_2(a_3b_1-a_1b_3)+a_3(a_1b_2-a_2b_1)\\
&=a_1a_2b_3-a_1a_3b_2+a_2a_3b_1-a_1a_2b_3+a_1a_3b_2-a_2a_3b_1\\
&=0,
\end{aligned}
$$

since the six terms cancel in pairs; the same expansion with $\mathbf b$ gives $\mathbf b\cdot(\mathbf a\times\mathbf b)=0$.

Its magnitude is $|\mathbf a||\mathbf b|\sin\theta$, through **Lagrange's identity**. Square and add the three components:

$$
\begin{aligned}
|\mathbf a\times\mathbf b|^2&=(a_2b_3-a_3b_2)^2+(a_3b_1-a_1b_3)^2+(a_1b_2-a_2b_1)^2\\
&=a_2^2b_3^2+a_3^2b_2^2+a_3^2b_1^2+a_1^2b_3^2+a_1^2b_2^2+a_2^2b_1^2\\
&\quad-2\,(a_2a_3b_2b_3+a_1a_3b_1b_3+a_1a_2b_1b_2).
\end{aligned}
$$

Separately, expand $|\mathbf a|^2|\mathbf b|^2-(\mathbf a\cdot\mathbf b)^2$:

$$
\begin{aligned}
|\mathbf a|^2|\mathbf b|^2-(\mathbf a\cdot\mathbf b)^2&=(a_1^2+a_2^2+a_3^2)(b_1^2+b_2^2+b_3^2)-(a_1b_1+a_2b_2+a_3b_3)^2\\
&=\big(a_1^2b_1^2+a_2^2b_2^2+a_3^2b_3^2+a_1^2b_2^2+a_1^2b_3^2+a_2^2b_1^2+a_2^2b_3^2+a_3^2b_1^2+a_3^2b_2^2\big)\\
&\quad-\big(a_1^2b_1^2+a_2^2b_2^2+a_3^2b_3^2+2a_1a_2b_1b_2+2a_1a_3b_1b_3+2a_2a_3b_2b_3\big)\\
&=a_1^2b_2^2+a_1^2b_3^2+a_2^2b_1^2+a_2^2b_3^2+a_3^2b_1^2+a_3^2b_2^2\\
&\quad-2\,(a_1a_2b_1b_2+a_1a_3b_1b_3+a_2a_3b_2b_3).
\end{aligned}
$$

The two results are the same nine terms, so

$$
|\mathbf a\times\mathbf b|^2=|\mathbf a|^2|\mathbf b|^2-(\mathbf a\cdot\mathbf b)^2 .
$$

Using $\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta$:

$$
\begin{aligned}
|\mathbf a\times\mathbf b|^2&=|\mathbf a|^2|\mathbf b|^2-|\mathbf a|^2|\mathbf b|^2\cos^2\theta\\
&=|\mathbf a|^2|\mathbf b|^2(1-\cos^2\theta)\\
&=|\mathbf a|^2|\mathbf b|^2\sin^2\theta .
\end{aligned}
$$

Since $0\le\theta\le\pi$, $\sin\theta\ge0$, and the positive square root gives

$$
|\mathbf a\times\mathbf b|=|\mathbf a||\mathbf b|\sin\theta .
$$

The right-handed sense is fixed by $\mathbf i\times\mathbf j=\mathbf k$ in the table, which the component formula reproduces ($(1,0,0)\times(0,1,0)=(0,0,1)$). The rearranged identity, $(\mathbf a\cdot\mathbf b)^2+|\mathbf a\times\mathbf b|^2=|\mathbf a|^2|\mathbf b|^2$, is James Exercise 49.

### First cross products (Example 4.24, parts (a) and (d))

With $\mathbf a=(2,1,0)$, $\mathbf b=(2,-1,1)$, $\mathbf c=(0,1,1)$:

$$
\begin{aligned}
\mathbf a\times\mathbf b&=\big(1\cdot1-0\cdot(-1),\ 0\cdot2-2\cdot1,\ 2\cdot(-1)-1\cdot2\big)\\
&=(1,-2,-4),\\
\mathbf b\times\mathbf c&=\big((-1)\cdot1-1\cdot1,\ 1\cdot0-2\cdot1,\ 2\cdot1-(-1)\cdot0\big)\\
&=(-2,-2,2).
\end{aligned}
$$

Check: $(1,-2,-4)\cdot(2,1,0)=2-2+0=0$ and $(1,-2,-4)\cdot(2,-1,1)=2+2-4=0$. The remaining parts are in §8.

### Products of three given vectors (Exercise 41)

With $\mathbf p=(1,1,1)$, $\mathbf q=(0,-1,2)$, $\mathbf r=(2,2,1)$,

$$
\begin{aligned}
\mathbf p\times\mathbf q&=\big(1\cdot2-1\cdot(-1),\ 1\cdot0-1\cdot2,\ 1\cdot(-1)-1\cdot0\big)=(3,-2,-1),\\
\mathbf p\times\mathbf r&=\big(1\cdot1-1\cdot2,\ 1\cdot2-1\cdot1,\ 1\cdot2-1\cdot2\big)=(-1,1,0),\\
\mathbf r\times\mathbf q&=\big(2\cdot2-1\cdot(-1),\ 1\cdot0-2\cdot2,\ 2\cdot(-1)-2\cdot0\big)=(5,-4,-2).
\end{aligned}
$$

Parts (d) and (e) dot a cross product with the third vector: $(\mathbf p\times\mathbf r)\cdot\mathbf q=(-1,1,0)\cdot(0,-1,2)=-1$, and $\mathbf q\cdot(\mathbf r\times\mathbf p)=\mathbf q\cdot(-\mathbf p\times\mathbf r)=+1$ by anti-commutativity. These are scalar triple products, whose cyclic symmetry and volume meaning are in [[Scalar Triple Product]] and [[MATH1054 M15 - Vectors II]]. Part (f) is in §8.

## 7. Normals, areas, moments and rotating bodies

### Unit normal to a plane

Since $\mathbf a\times\mathbf b$ is perpendicular to both $\mathbf a$ and $\mathbf b$, it is normal to the plane they span (provided they are not parallel), and the unit normals are

$$
\hat{\mathbf n}=\pm\frac{\mathbf a\times\mathbf b}{|\mathbf a\times\mathbf b|} .
$$

**Example 4.25.** For $\mathbf a=(2,-3,1)$, $\mathbf b=(1,2,-4)$,

$$
\begin{aligned}
\mathbf a\times\mathbf b&=\big((-3)(-4)-1\cdot2,\ 1\cdot1-2(-4),\ 2\cdot2-(-3)\cdot1\big)\\
&=(12-2,\ 1+8,\ 4+3)\\
&=(10,9,7),
\end{aligned}
$$

with $|\mathbf a\times\mathbf b|=\sqrt{100+81+49}=\sqrt{230}$, so $\hat{\mathbf n}=\pm\frac1{\sqrt{230}}(10,9,7)$. Lagrange's identity confirms the length: $|\mathbf a|^2|\mathbf b|^2-(\mathbf a\cdot\mathbf b)^2=14\cdot21-(-8)^2=294-64=230$.

**Specimen Test 14, Q6.** For $\mathbf a=(2,0,1)$, $\mathbf b=(-2,4,3)$,

$$
\begin{aligned}
\mathbf a\times\mathbf b&=\big(0\cdot3-1\cdot4,\ 1\cdot(-2)-2\cdot3,\ 2\cdot4-0\cdot(-2)\big)\\
&=(-4,-8,8),
\end{aligned}
$$

$|\mathbf a\times\mathbf b|=\sqrt{16+64+64}=12$, and a unit vector perpendicular to both is $\pm\frac13(-1,-2,2)$.

### Area of a parallelogram and a triangle

In a parallelogram ABCD with angle $\theta$ at A, the height above the base AB is $h=|\overrightarrow{\mathrm{AD}}|\sin\theta$, so

$$
\begin{aligned}
\text{area of ABCD}&=|\overrightarrow{\mathrm{AB}}|\,h\\
&=|\overrightarrow{\mathrm{AB}}||\overrightarrow{\mathrm{AD}}|\sin\theta\\
&=|\overrightarrow{\mathrm{AD}}\times\overrightarrow{\mathrm{AB}}| .
\end{aligned}
$$

The diagonal BD halves it, so the triangle ABD has area $\frac12|\overrightarrow{\mathrm{AD}}\times\overrightarrow{\mathrm{AB}}|$, the vector form of $\frac12bc\sin A$. The order inside the modulus does not matter, since reversing it only flips the sign.

**Example 4.26.** For the triangle $\mathrm P(1,3,2)$, $\mathrm Q(-2,1,3)$, $\mathrm R(3,-2,-1)$, take both sides from P:

$$
\overrightarrow{\mathrm{PQ}}=(-3,-2,1),\qquad\overrightarrow{\mathrm{PR}}=(2,-5,-3),
$$

$$
\begin{aligned}
\overrightarrow{\mathrm{PQ}}\times\overrightarrow{\mathrm{PR}}&=\big((-2)(-3)-1\cdot(-5),\ 1\cdot2-(-3)(-3),\ (-3)(-5)-(-2)\cdot2\big)\\
&=(6+5,\ 2-9,\ 15+4)\\
&=(11,-7,19),
\end{aligned}
$$

$$
\begin{aligned}
\text{area}&=\tfrac12\sqrt{121+49+361}\\
&=\tfrac12\sqrt{531}\\
&=\tfrac{3\sqrt{59}}2\approx11.52\ \text{square units}.
\end{aligned}
$$

### Moment of a force about a point

Let a force $\mathbf F$ act through a point P, and let $\mathbf r=\overrightarrow{\mathrm{AP}}$ run from a reference point A to P. The **moment** of $\mathbf F$ about A is

$$
\mathbf M_{\mathrm A}=\mathbf r\times\mathbf F .
$$

Its magnitude is the familiar force times perpendicular distance (panel (b) of the figure in §6). If $\theta$ is the angle between $\mathbf r$ and $\mathbf F$, the perpendicular distance from A to the line of action is $d=|\mathbf r|\sin\theta$, so

$$
\begin{aligned}
|\mathbf M_{\mathrm A}|&=|\mathbf r||\mathbf F|\sin\theta\\
&=|\mathbf F|\,(|\mathbf r|\sin\theta)\\
&=|\mathbf F|\,d .
\end{aligned}
$$

Its direction is along the axis through A about which the force tends to turn the body, with the right-hand-screw sense. The moment does not depend on which point of the line of action is called P: any other point is at $\mathbf r+\lambda\mathbf F$ from A, and

$$
\begin{aligned}
(\mathbf r+\lambda\mathbf F)\times\mathbf F&=\mathbf r\times\mathbf F+\lambda(\mathbf F\times\mathbf F)\\
&=\mathbf r\times\mathbf F+\mathbf0 .
\end{aligned}
$$

The components of $\mathbf M_{\mathrm A}$ are the moments about the three axes through A parallel to $Ox$, $Oy$, $Oz$. The $z$ component, for instance, is $r_1F_2-r_2F_1$, the planar rule "$x$ times $F_y$ minus $y$ times $F_x$" used for every two-dimensional moment in [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain|FEEG1002 statics]]. Moments about one point add like vectors, which is why equilibrium needs $\sum\mathbf M_{\mathrm A}=\mathbf0$ as one vector equation.

### A force of 4 units about A (Example 4.28)

A force of 4 units acts through $\mathrm P(2,3,-5)$ in the direction $(4,5,-2)$; find its moment about $\mathrm A(1,2,-3)$. The direction has length $\sqrt{16+25+4}=\sqrt{45}=3\sqrt5$, so

$$
\mathbf F=\frac4{3\sqrt5}(4,5,-2),\qquad\mathbf r=\overrightarrow{\mathrm{AP}}=(2,3,-5)-(1,2,-3)=(1,1,-2).
$$

Take the scalar outside and cross the integer vectors:

$$
\begin{aligned}
(1,1,-2)\times(4,5,-2)&=\big(1\cdot(-2)-(-2)\cdot5,\ (-2)\cdot4-1\cdot(-2),\ 1\cdot5-1\cdot4\big)\\
&=(-2+10,\ -8+2,\ 5-4)\\
&=(8,-6,1),
\end{aligned}
$$

$$
\mathbf M_{\mathrm A}=\frac4{3\sqrt5}(8,-6,1)=\Big(\frac{32}{\sqrt{45}},-\frac{24}{\sqrt{45}},\frac4{\sqrt{45}}\Big)\approx(4.770,\,-3.578,\,0.596),
$$

with $|\mathbf M_{\mathrm A}|=\frac4{3\sqrt5}\sqrt{101}\approx5.99$. The moments about axes through A parallel to $Ox$, $Oy$, $Oz$ are $4.770$, $-3.578$ and $0.596$. Dividing by $|\mathbf F|=4$ gives the perpendicular distance from A to the line of action, $d\approx1.50$.

> [!check] The moment does not depend on the point chosen on the line
> Take instead $\mathrm P'=\mathrm P+(4,5,-2)=(6,8,-7)$, also on the line of action. Then $\overrightarrow{\mathrm{AP'}}=(5,6,-4)$ and $(5,6,-4)\times(4,5,-2)=(-12+20,\ -16+10,\ 25-24)=(8,-6,1)$, the same as before. Also $(8,-6,1)\cdot(4,5,-2)=32-30-2=0$: the moment is perpendicular to the force.

**Exercise 52.** A force of 4 units through $\mathrm P(4,-1,2)$ along $(2,-1,4)$ (length $\sqrt{21}$), about $\mathrm A(3,-1,4)$: $\overrightarrow{\mathrm{AP}}=(1,0,-2)$, $(1,0,-2)\times(2,-1,4)=(0\cdot4-(-2)(-1),\ (-2)\cdot2-1\cdot4,\ 1\cdot(-1)-0\cdot2)=(-2,-8,-1)$, so $\mathbf M_{\mathrm A}=\frac4{\sqrt{21}}(-2,-8,-1)\approx(-1.746,-6.983,-0.873)$ with $|\mathbf M_{\mathrm A}|=\frac{4\sqrt{69}}{\sqrt{21}}\approx7.25$.

**Specimen Test 14, Q7.** The force $5\mathbf i+2\mathbf k$ N acts through $(2,6,1)$; about $(1,1,1)$ the position vector is $\mathbf r=(1,5,0)$ m, and

$$
\begin{aligned}
\mathbf M&=(1,5,0)\times(5,0,2)\\
&=\big(5\cdot2-0\cdot0,\ 0\cdot5-1\cdot2,\ 1\cdot0-5\cdot5\big)\\
&=(10,-2,-25)\ \text{N m}.
\end{aligned}
$$

### Velocity of a point on a rotating body

A rigid body turns with angular speed $\omega$ (rad/s) about a fixed axis through a point A. The **angular velocity** $\boldsymbol\omega$ is the vector of magnitude $\omega$ along the axis, in the sense a right-handed screw would advance when turned with the body. A point P with $\mathbf r=\overrightarrow{\mathrm{AP}}$ moves on a circle about the axis, centred at the foot N of the perpendicular from P to the axis, with speed $\omega\cdot\mathrm{NP}$ along the tangent. If $\phi$ is the angle between $\boldsymbol\omega$ and $\mathbf r$, the radius of that circle is $\mathrm{NP}=|\mathbf r|\sin\phi$, so

$$
\begin{aligned}
|\boldsymbol\omega\times\mathbf r|&=\omega|\mathbf r|\sin\phi\\
&=\omega\,\mathrm{NP},
\end{aligned}
$$

and $\boldsymbol\omega\times\mathbf r$ is perpendicular to the axis and to $\mathbf r$, which is the tangent direction, with the right-handed sense of the rotation. So

$$
\mathbf v=\boldsymbol\omega\times\mathbf r=\boldsymbol\omega\times\overrightarrow{\mathrm{AP}} .
$$

A must be on the axis, but which point of the axis does not matter: moving it along the axis changes $\mathbf r$ by $\lambda\boldsymbol\omega$, and $\boldsymbol\omega\times(\mathbf r+\lambda\boldsymbol\omega)=\boldsymbol\omega\times\mathbf r$. Both $\mathbf M$ and $\boldsymbol\omega$ point along the axis of the rotation they describe.

> [!warning] The order is fixed in both formulas
> The moment is $\mathbf r\times\mathbf F$ (position first) and the velocity is $\boldsymbol\omega\times\mathbf r$ (angular velocity first). Writing $\mathbf F\times\mathbf r$ or $\mathbf r\times\boldsymbol\omega$ gives the right magnitude and exactly the wrong direction. In both, $\mathbf r$ runs from the reference point (the moment centre, or a point on the axis) to the point of interest.

### A body turning about a skew axis (Example 4.29)

A body rotates at 5 rad/s about an axis along $(1,3,-2)$ through $\mathrm A(2,3,-1)$; find the velocity of $\mathrm P(-2,3,1)$. The axis direction has length $\sqrt{14}$, so

$$
\boldsymbol\omega=\frac5{\sqrt{14}}(1,3,-2),\qquad\overrightarrow{\mathrm{AP}}=(-2-2,\ 3-3,\ 1+1)=(-4,0,2).
$$

$$
\begin{aligned}
(1,3,-2)\times(-4,0,2)&=\big(3\cdot2-(-2)\cdot0,\ (-2)(-4)-1\cdot2,\ 1\cdot0-3\cdot(-4)\big)\\
&=(6,6,12),
\end{aligned}
$$

$$
\mathbf v=\frac5{\sqrt{14}}(6,6,12)=\frac{30}{\sqrt{14}}(1,1,2)\approx(8.02,\,8.02,\,16.04)\ \text{units/s},
$$

with $|\mathbf v|=\frac{30\sqrt6}{\sqrt{14}}\approx19.64$. As a check, $(6,6,12)\cdot(1,3,-2)=6+18-24=0$, so the velocity is perpendicular to the axis.

**Exercise 51.** At 6 rad/s about $(3,-2,1)$ through $\mathrm A(3,-2,5)$, the point $\mathrm P(3,-2,1)$ has $\overrightarrow{\mathrm{AP}}=(0,0,-4)$, and $(3,-2,1)\times(0,0,-4)=(8,12,0)$, so $\mathbf v=\frac6{\sqrt{14}}(8,12,0)\approx(12.83,\,19.24,\,0)$ with $|\mathbf v|\approx23.13$.

**Specimen Test 14, Q8.** At 4 rad/s about the axis from $(1,0,0)$ to $(2,3,2)$, the direction is $(1,3,2)$ of length $\sqrt{14}$, so $\boldsymbol\omega=\frac4{\sqrt{14}}(1,3,2)$ rad/s. For the point $(2,1,1)$, use $\mathrm A(1,0,0)$ on the axis: $\overrightarrow{\mathrm{AP}}=(1,1,1)$, $(1,3,2)\times(1,1,1)=(3-2,\ 2-1,\ 1-3)=(1,1,-2)$, and $\mathbf v=\frac4{\sqrt{14}}(1,1,-2)\approx(1.069,\,1.069,\,-2.138)$ m/s.

## 8. The triple vector product

Since $\mathbf b\times\mathbf c$ is a vector, it can be crossed with a third vector. The bracket matters: $\mathbf b\times\mathbf c$ is normal to the plane of $\mathbf b$ and $\mathbf c$, so $\mathbf a\times(\mathbf b\times\mathbf c)$, being perpendicular to that normal, lies in the plane of $\mathbf b$ and $\mathbf c$; by the same argument $(\mathbf a\times\mathbf b)\times\mathbf c$ lies in the plane of $\mathbf a$ and $\mathbf b$. These are different planes in general, so the cross product is **not associative**, and $\mathbf a\times\mathbf b\times\mathbf c$ without brackets is never written.

Because $\mathbf a\times(\mathbf b\times\mathbf c)$ lies in the plane of $\mathbf b$ and $\mathbf c$, it must be a combination of $\mathbf b$ and $\mathbf c$. The components give the coefficients. Let $\mathbf d=\mathbf b\times\mathbf c$, so

$$
d_1=b_2c_3-b_3c_2,\qquad d_2=b_3c_1-b_1c_3,\qquad d_3=b_1c_2-b_2c_1 .
$$

The $x$ component of $\mathbf a\times\mathbf d$ is $a_2d_3-a_3d_2$:

$$
\begin{aligned}
\big[\mathbf a\times(\mathbf b\times\mathbf c)\big]_1&=a_2(b_1c_2-b_2c_1)-a_3(b_3c_1-b_1c_3)\\
&=a_2b_1c_2-a_2b_2c_1-a_3b_3c_1+a_3b_1c_3\\
&=b_1(a_2c_2+a_3c_3)-c_1(a_2b_2+a_3b_3)\\
&=b_1(a_1c_1+a_2c_2+a_3c_3)-c_1(a_1b_1+a_2b_2+a_3b_3)\\
&=(\mathbf a\cdot\mathbf c)\,b_1-(\mathbf a\cdot\mathbf b)\,c_1,
\end{aligned}
$$

where the fourth line adds and subtracts $a_1b_1c_1$. The component formula for the cross product is unchanged by the cyclic relabelling $1\to2\to3\to1$, and so are both dot products, so the same working gives the $y$ and $z$ components with $b_2,c_2$ and $b_3,c_3$. Hence

$$
\mathbf a\times(\mathbf b\times\mathbf c)=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf a\cdot\mathbf b)\,\mathbf c,
$$

remembered as "BAC minus CAB": $\mathbf b(\mathbf a\cdot\mathbf c)-\mathbf c(\mathbf a\cdot\mathbf b)$. The other bracketing follows by anti-commutativity:

$$
\begin{aligned}
(\mathbf a\times\mathbf b)\times\mathbf c&=-\,\mathbf c\times(\mathbf a\times\mathbf b)\\
&=-\big[(\mathbf c\cdot\mathbf b)\mathbf a-(\mathbf c\cdot\mathbf a)\mathbf b\big]\\
&=(\mathbf a\cdot\mathbf c)\,\mathbf b-(\mathbf b\cdot\mathbf c)\,\mathbf a .
\end{aligned}
$$

In both, the vector in the middle of the triple, here $\mathbf b$, carries the positive sign.

### Non-associativity in numbers (Example 4.24, parts (b), (c), (e) and (f))

With $\mathbf a=(2,1,0)$, $\mathbf b=(2,-1,1)$, $\mathbf c=(0,1,1)$, the dot products are $\mathbf a\cdot\mathbf c=1$, $\mathbf b\cdot\mathbf c=0$, $\mathbf a\cdot\mathbf b=3$, and from §6, $\mathbf a\times\mathbf b=(1,-2,-4)$ and $\mathbf b\times\mathbf c=(-2,-2,2)$.

| Part | Expression | Value |
|---|---|---|
| (b) | $(\mathbf a\times\mathbf b)\times\mathbf c=(1,-2,-4)\times(0,1,1)$ | $(-2+4,\ 0-1,\ 1-0)=(2,-1,1)$ |
| (c) | $(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf b\cdot\mathbf c)\mathbf a$ | $1(2,-1,1)-0\,\mathbf a=(2,-1,1)$ |
| (e) | $\mathbf a\times(\mathbf b\times\mathbf c)=(2,1,0)\times(-2,-2,2)$ | $(2-0,\ 0-4,\ -4+2)=(2,-4,-2)$ |
| (f) | $(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c$ | $1(2,-1,1)-3(0,1,1)=(2,-4,-2)$ |

Parts (b) and (c) agree, parts (e) and (f) agree, and (b) differs from (e), which shows the non-associativity with numbers.

For Exercise 41(f), the identity gives $(\mathbf p\times\mathbf r)\times\mathbf q=(\mathbf p\cdot\mathbf q)\mathbf r-(\mathbf r\cdot\mathbf q)\mathbf p=1\cdot(2,2,1)-0\cdot\mathbf p=(2,2,1)$, the same as crossing directly, $(-1,1,0)\times(0,-1,2)=(2-0,\ 0+2,\ 1-0)=(2,2,1)$.

> [!tip] Where BAC minus CAB is used next
> In plane rigid-body motion, $\boldsymbol\omega=\omega\mathbf k$ and $\mathbf r$ lies in the $xy$-plane, so $\mathbf k\times(\mathbf k\times\mathbf r)=(\mathbf k\cdot\mathbf r)\mathbf k-(\mathbf k\cdot\mathbf k)\mathbf r=-\mathbf r$. That is why the centripetal term $\boldsymbol\omega\times(\boldsymbol\omega\times\mathbf r)$ in [[FEEG1002 D7 - Kinematics of Rigid Bodies]] reduces to $-\omega^2\mathbf r$, pointing at the axis.

## Terminology and alternative names

| Course term | Also called | Note |
|---|---|---|
| scalar product $\mathbf a\cdot\mathbf b$ | dot product, inner product | James uses all three |
| vector product $\mathbf a\times\mathbf b$ | cross product; $\mathbf a\wedge\mathbf b$ | the wedge notation is rare in engineering |
| component of $\mathbf F$ along $\mathbf u$ | resolved part, scalar projection | $\mathbf F\cdot\hat{\mathbf u}$; the vector projection is $(\mathbf F\cdot\hat{\mathbf u})\hat{\mathbf u}$ |
| $\mathbf i,\mathbf j,\mathbf k$ | $\hat{\mathbf e}_1,\hat{\mathbf e}_2,\hat{\mathbf e}_3$; $(x_1,x_2,x_3)$ for $(x,y,z)$ | suffix notation for many dimensions |
| moment of a force | torque | James uses both |

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M14 Solutions - Vectors I]] · Next: [[MATH1054 M15 - Vectors II]] (scalar triple product, lines, planes, differentiation of vectors)
- Concepts: [[Vector Algebra and Components]] · [[Scalar (Dot) Product]] · [[Vector (Cross) Product]] · [[Scalar Triple Product]] · [[Equations of Lines and Planes]] · [[Determinants and Cofactors]]
- Complex numbers as two-dimensional vectors (James §4.2.6): [[Argand Diagram]], [[MATH1054 M05 - Complex Numbers I]]
- Applied in FEEG1002: [[Free Body Diagram and Equilibrium]] · [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · [[FEEG1002 D3 - Work, Energy and Power]] ([[Work-Energy Principle]]) · [[FEEG1002 D5 - Angular Impulse and Momentum]] ([[Principle of Angular Impulse and Momentum]]) · [[FEEG1002 D7 - Kinematics of Rigid Bodies]] ([[Relative Velocity Equation for Rigid Bodies]])
- Later: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] · [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] · [[FEEG1004 A2 - Magnetism, Induction and the Lorentz Force]] (force $q\mathbf v\times\mathbf B$) · [[SESA3047 2.1 - Vector Operations and the Transport Theorem]] ([[Cross-Product Matrix]], [[Angular Velocity Vector]], [[Direction Cosine Matrix]])

## Sources

- MATH1054 Module Booklet, Module 14 (Vectors I): work scheme pp. 1–2 and Specimen Test 14 p. 3 (PDF pp. 52–54)
- James, *Modern Engineering Mathematics* (6th ed.): §4.1, §4.2.1–4.2.3 (pp. 230–241), §4.2.5 (pp. 242–248), §4.2.8 (pp. 251–257), §4.2.10 (pp. 259–268); Examples 4.1–4.29 and Exercises 9, 11, 12, 19, 27, 28, 31, 32, 41, 49, 51, 52

## Self-study tasks

### Core

- [ ] Exercises 11, 12 and 19 (Module 14 work scheme, James p. 250): component arithmetic, a displacement with its direction cosines, and a collinearity test. → [[MATH1054 M14 Solutions - Vectors I#Part B: Assigned exercises]] · [[MATH1054 M14 Solutions - Vectors I#Exercise 19: Collinearity]]
- [ ] Exercise 9 (Module 14 work scheme, James p. 241): the true wind from a cyclist's two apparent winds. → [[MATH1054 M14 Solutions - Vectors I#Exercise 9: The cyclist and the wind]] · [[#The cyclist and the wind (Exercise 9)]]
- [ ] Exercises 27, 28(a),(c), 31 and 32 (Module 14 work scheme, James p. 258): dot products, angles, a perpendicularity parameter, work and a resolved part. → [[MATH1054 M14 Solutions - Vectors I#Exercise 28]] · [[MATH1054 M14 Solutions - Vectors I#Exercise 31: Work done]] · [[MATH1054 M14 Solutions - Vectors I#Exercise 32: The resolved part]]
- [ ] Exercises 41, 51 and 52 (Module 14 work scheme, James p. 269): cross products, the velocity of a point on a rotating body and a moment about a point. → [[MATH1054 M14 Solutions - Vectors I#Exercise 51: Linear velocity]] · [[MATH1054 M14 Solutions - Vectors I#Exercise 52: Moment about A]]
- [ ] Specimen Test 14, Q1–Q8 (Module Booklet, Module 14), timed. → [[MATH1054 M14 Solutions - Vectors I#Part C: Specimen Test 14]]

### Further practice

- [ ] Examples 4.12 and 4.13 (Module 14 work scheme): rework the tetrahedral molecule and the three-force resultant without looking. → [[#The tetrahedral molecule (Example 4.12)]] · [[MATH1054 M14 Solutions - Vectors I#Example 4.13: Resultant of three forces]]
- [ ] Example 4.24 (Module 14 work scheme): all six parts, then confirm both BAC minus CAB forms. → [[MATH1054 M14 Solutions - Vectors I#Example 4.24: Cross products and the triple-product identities]] · [[#Non-associativity in numbers (Example 4.24, parts (b), (c), (e) and (f))]]
- [ ] James Exercise 49: show $(\mathbf a\cdot\mathbf b)^2+|\mathbf a\times\mathbf b|^2=|\mathbf a|^2|\mathbf b|^2$ (suggested, not set). → [[#The component form has the geometric properties]]
- [ ] James Exercise 47: show $(\mathbf a-\mathbf b)\times(\mathbf a+\mathbf b)=2\,\mathbf a\times\mathbf b$ by distributivity, $\mathbf a\times\mathbf a=\mathbf0$ and anti-commutativity, and interpret it as the parallelogram on the diagonals having twice the area (suggested, not set). → [[#Properties from the definition]]

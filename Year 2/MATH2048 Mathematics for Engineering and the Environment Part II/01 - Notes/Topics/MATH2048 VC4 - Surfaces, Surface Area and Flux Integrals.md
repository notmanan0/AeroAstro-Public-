---
title: "MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 18
tags:
  - math2048
  - vector-calculus
  - surface-integrals
  - flux
aliases: ["MATH2048 Lecture 27", "MATH2048 Lecture 28", "Parametrised surfaces", "Surface element dA", "dS"]
date: 2026-10-30
status: lectured
coverage: "Lecture 27 (2 Dec 2024): three ways to describe a surface, parametrising the cylinder and sphere, the normal from the cross product of tangent vectors, the area element dA, the area of a cylinder. Lecture 28 (3 Dec 2024): integrating a scalar field over a cylinder, flux integrals with the vector area element dS, the flux through a helicoid, and the shortcut for a surface given as a graph z(x, y). Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
next_topics: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
key_concepts: ["[[Flux Integrals]]", "[[Jacobian and Volume Elements]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 27.txt", "02 - Sources/Lectures/MATH2048 Lecture 28.txt", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture27_vector07.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture28_vector08.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.2.3–8.2.6)"]
---

# MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals

> [!abstract] Summary
> A surface is described by two parameters, $\mathbf r(s,t)$. The tangent vectors $\mathbf r_s$ and $\mathbf r_t$ span a small parallelogram whose area is $|\mathbf r_s\times\mathbf r_t|\,ds\,dt$, so the cross product $\mathbf N=\mathbf r_s\times\mathbf r_t$ gives both the normal and the area element $dA=|\mathbf N|\,ds\,dt$. The flux of a vector field through a surface is $\iint\mathbf F\cdot\hat{\mathbf n}\,dA=\iint\mathbf F\cdot\mathbf N\,ds\,dt$, where the vector area element $d\mathbf S=\mathbf N\,ds\,dt$ saves normalising $\mathbf N$; swapping the order of the cross product reverses the normal and the sign of the flux.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for a surface area, the integral of a scalar over a surface, or the flux of a vector field through a surface (2023/24 B2(a)–(d); PS10).
> - **Assumptions:** a parametrisation covering the surface once; the direction of the normal fixed by the question (up, outward) and checked.
> - **Method:** 1. Parametrise, $\mathbf r(s,t)$, with parameter ranges. 2. Compute $\mathbf r_s$, $\mathbf r_t$ and $\mathbf N=\mathbf r_s\times\mathbf r_t$; check its direction at one point. 3. Area or scalar integral: use $|\mathbf N|\,ds\,dt$. 4. Flux: substitute $x(s,t)$, $y(s,t)$, $z(s,t)$ into $\mathbf F$ and form $\mathbf F\cdot\mathbf N$. 5. Integrate over the parameter rectangle.
> - **Common mistakes:** not checking whether $\mathbf N$ points the required way (for the course's sphere, $\mathbf r_s\times\mathbf r_t$ points inwards); forgetting the factor $|\mathbf N|$ in $dA$.
> - **Practise:** [[#Flux through a helicoid]] · [[#4. The 2023-24 exam, question B2(a)–(d)]]

Line integrals add up a field along a one-dimensional curve. Most quantities of engineering interest live on surfaces instead: the lift on a wing integrates pressure over its skin, the flow out of a pipe is the flux of velocity through its cross-section, and heat or radiation transfer is a flux through a boundary. The approach copies the line integral. A curve needed one parameter; a surface is intrinsically two-dimensional, so it needs two.

The parameters map a simple flat region, usually a rectangle, onto the curved surface. The work is in finding how much each small piece of the rectangle is stretched by the mapping, which is the length of a cross product. After that, every surface integral is an ordinary double integral over the rectangle.

---

## 1. Describing a surface

There are three ways. A graph, $z=f(x,y)$, suits something like terrain height on a map, but fails for a sphere, where each $(x,y)$ inside has two values of $z$. A level surface, such as $x^2+y^2+z^2=a^2$, handles the sphere, but is often awkward to work with. The general choice, used for the rest of the course, is a parametrisation

$$
\mathbf r(s,t)=x(s,t)\,\mathbf i+y(s,t)\,\mathbf j+z(s,t)\,\mathbf k ,
$$

with $(s,t)$ ranging over a rectangle $a\leq s\leq b$, $c\leq t\leq d$. Not every surface maps nicely from a rectangle; a whole sphere can't be covered from a square without bad points at the poles, and some patches suit a triangle better. As with curves, the parametrisation is a matter of convenience and doesn't change the answer.

### The cylinder

A cylinder of radius $a$ and height $h$ about the $z$-axis is a stack of circles. Let $t$ be the height and $s$ the angle round each circle:

$$
\mathbf r(s,t)=a\cos s\,\mathbf i+a\sin s\,\mathbf j+t\,\mathbf k,\qquad-\pi\leq s\leq\pi,\quad0\leq t\leq h .
$$

The horizontal part has length $\sqrt{a^2\cos^2s+a^2\sin^2s}=a$, so every point is at distance $a$ from the axis, and as $s$ runs round the circle $x$ and $y$ sweep out all values between $-a$ and $a$.

### The sphere

A sphere of radius $a$ is sliced horizontally, with $t$ the angle down from the north pole, so $z=a\cos t$, which is $a$ at the pole $t=0$, $0$ on the equator and $-a$ at the south pole $t=\pi$. The slice at that height is a circle of radius $a\sin t$, zero at the poles and $a$ on the equator, parametrised by $s$:

$$
\mathbf r(s,t)=a\cos s\sin t\,\mathbf i+a\sin s\sin t\,\mathbf j+a\cos t\,\mathbf k,\qquad0\leq s\leq2\pi,\quad0\leq t\leq\pi .
$$

Then $|\mathbf r|^2=a^2\sin^2t(\cos^2s+\sin^2s)+a^2\cos^2t=a^2$. This follows the formula sheet, but spherical coordinates vary between sources, in which angle is measured from where and with which letter, so always check.

## 2. Normals and the area element

### The normal from two tangent vectors

On the surface, the lines of constant $t$ and the lines of constant $s$ form a grid. Differentiating with $t$ held fixed moves along a line of constant $t$, so $\mathbf r_s=\frac{\partial\mathbf r}{\partial s}$ is tangent to it; likewise $\mathbf r_t$ is tangent to the lines of constant $s$. Both lie in the surface, so their cross product is normal to it:

$$
\mathbf N=\frac{\partial\mathbf r}{\partial s}\times\frac{\partial\mathbf r}{\partial t}.
$$

Swapping the order reverses $\mathbf N$. One order gives the outward normal and the other the inward one, and which is which depends on the parametrisation, so draw a picture and check.

For the cylinder, $\mathbf r_s=-a\sin s\,\mathbf i+a\cos s\,\mathbf j$ and $\mathbf r_t=\mathbf k$, so

$$
\mathbf N=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\-a\sin s&a\cos s&0\\0&0&1\end{vmatrix}=a\cos s\,\mathbf i+a\sin s\,\mathbf j .
$$

At $s=0$, the point $(a,0,t)$, it is $a\,\mathbf i$; at $s=\pi$, the point $(-a,0,t)$, it is $-a\,\mathbf i$; at $s=\frac\pi2$ it is $a\,\mathbf j$. It always points away from the axis: this order gives the outward normal of the curved side, and says nothing about the end caps, which this parametrisation doesn't cover.

For the sphere, differentiate the parametrisation:

$$
\mathbf r_s=-a\sin s\sin t\,\mathbf i+a\cos s\sin t\,\mathbf j,\qquad\mathbf r_t=a\cos s\cos t\,\mathbf i+a\sin s\cos t\,\mathbf j-a\sin t\,\mathbf k .
$$

Expand $\mathbf r_t\times\mathbf r_s$ by minors:

$$
\mathbf r_t\times\mathbf r_s=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a\cos s\cos t&a\sin s\cos t&-a\sin t\\-a\sin s\sin t&a\cos s\sin t&0\end{vmatrix}
$$

$$
=\mathbf i\big(0+a^2\cos s\sin^2t\big)-\mathbf j\big(0-a^2\sin s\sin^2t\big)+\mathbf k\big(a^2\cos^2s\sin t\cos t+a^2\sin^2s\sin t\cos t\big)
$$

$$
=a^2\sin t\big(\cos s\sin t\,\mathbf i+\sin s\sin t\,\mathbf j+\cos t\,\mathbf k\big)=a^2\sin t\,\hat{\mathbf r}.
$$

So the normal is parallel to $\hat{\mathbf r}$ with magnitude $a^2\sin t$ (non-negative on $0\leq t\leq\pi$). With the parameters in the order above, the outward one is $\mathbf r_t\times\mathbf r_s$; the other order, $\mathbf r_s\times\mathbf r_t$, points inwards. A quick check on the equator, $t=\frac\pi2$, $s=0$: the point is $(a,0,0)$ and $\mathbf r_t\times\mathbf r_s=a^2\,\mathbf i$, outward.

### The area element

The small patch between $(s,t)$, $(s+\Delta s,t)$ and $(s,t+\Delta t)$ has edges, by a Taylor expansion,

$$
\mathbf r(s+\Delta s,t)-\mathbf r(s,t)=\frac{\partial\mathbf r}{\partial s}\Delta s+\dots,\qquad\mathbf r(s,t+\Delta t)-\mathbf r(s,t)=\frac{\partial\mathbf r}{\partial t}\Delta t+\dots
$$

The area of a parallelogram with edges $\mathbf a$ and $\mathbf b$ is $|\mathbf a\times\mathbf b|$, so the patch has area approximately

$$
\Big|\frac{\partial\mathbf r}{\partial s}\Delta s\times\frac{\partial\mathbf r}{\partial t}\Delta t\Big|=\Big|\frac{\partial\mathbf r}{\partial s}\times\frac{\partial\mathbf r}{\partial t}\Big|\Delta s\,\Delta t .
$$

In the limit,

$$
dA=|\mathbf N|\,ds\,dt .
$$

$|\mathbf N|$ says how much the mapping stretches each small square of the parameter rectangle: the bigger it is, the more that part of the surface counts. The sign of $\mathbf N$ is irrelevant here, because only its length enters.

### Areas of the cylinder and sphere

For the cylinder $|\mathbf N|=a$:

$$
A=\int_0^h\int_{-\pi}^{\pi}a\,ds\,dt=\int_0^h2\pi a\,dt=2\pi ah ,
$$

as expected. For the sphere $|\mathbf N|=a^2\sin t$, and

$$
A=\int_0^{2\pi}\int_0^\pi a^2\sin t\,dt\,ds=2\pi a^2\Big[-\cos t\Big]_0^\pi=4\pi a^2 .
$$

The order of the two integrals doesn't matter; choose whichever makes the integration easier.

### The area of a cone (PS10 Q1)

A cone with its vertex at the origin, base radius $a$ at height $h$, has radius $\frac ahz$ at height $z$. Use the angle $\theta$ and the height $z$ as parameters:

$$
\mathbf r=\frac ahz\cos\theta\,\mathbf i+\frac ahz\sin\theta\,\mathbf j+z\,\mathbf k,\qquad0\leq\theta\leq2\pi,\quad0\leq z\leq h .
$$

The tangents are

$$
\mathbf r_\theta=-\frac ahz\sin\theta\,\mathbf i+\frac ahz\cos\theta\,\mathbf j,\qquad\mathbf r_z=\frac ah\cos\theta\,\mathbf i+\frac ah\sin\theta\,\mathbf j+\mathbf k,
$$

and

$$
\mathbf r_\theta\times\mathbf r_z=\frac ahz\cos\theta\,\mathbf i+\frac ahz\sin\theta\,\mathbf j-\frac{a^2}{h^2}z\big(\sin^2\theta+\cos^2\theta\big)\mathbf k=\frac ahz\cos\theta\,\mathbf i+\frac ahz\sin\theta\,\mathbf j-\frac{a^2}{h^2}z\,\mathbf k .
$$

Its length is

$$
|\mathbf N|=\sqrt{\frac{a^2}{h^2}z^2+\frac{a^4}{h^4}z^2}=\frac{a}{h}z\sqrt{1+\frac{a^2}{h^2}}=\frac{a\sqrt{a^2+h^2}}{h^2}\,z,
$$

so

$$
A=\int_0^h\int_0^{2\pi}\frac{a\sqrt{a^2+h^2}}{h^2}\,z\,d\theta\,dz=\frac{a\sqrt{a^2+h^2}}{h^2}\cdot2\pi\cdot\frac{h^2}{2}=\pi a\sqrt{a^2+h^2}.
$$

That is $\pi a\ell$ with $\ell$ the slant height, the familiar result. As checks, $h\to0$ gives the flat disc $\pi a^2$, and unrolling the cone into a sector of radius $\ell$ and arc length $2\pi a$ gives area $\frac12\ell\cdot2\pi a$, the same.

## 3. Integrals over surfaces

### A scalar field over the cylinder

To integrate a scalar field $\phi$ over a surface, write it in terms of the parameters and multiply by $|\mathbf N|$. For $\phi=x^2z$ on the cylinder, $x=a\cos s$ and $z=t$, so $\phi=a^2t\cos^2s$, and with $|\mathbf N|=a$,

$$
\iint_S\phi\,dA=\int_{-\pi}^{\pi}\int_0^ha^3t\cos^2s\,dt\,ds=a^3\int_{-\pi}^{\pi}\cos^2s\,ds\int_0^ht\,dt .
$$

The integrand separates into a function of $s$ times a function of $t$, which is not guaranteed in general. With $\cos^2s=\frac12(1+\cos2s)$, the $\cos2s$ part integrates to zero over a full period and the $\frac12$ gives $\pi$; the $t$ integral gives $\frac{h^2}2$. So

$$
\iint_S x^2z\,dA=\frac{\pi a^3h^2}2 .
$$

The same steps for $\phi=xy^2$ give $a^4h\int_{-\pi}^{\pi}\cos s\sin^2s\,ds=a^4h\big[\tfrac13\sin^3s\big]_{-\pi}^{\pi}=0$.

### Flux and the vector area element

The flux of $\mathbf F$ through a surface counts only the part of $\mathbf F$ crossing it. A field running along the surface carries nothing through, and $\mathbf F\cdot\hat{\mathbf n}=0$; a field straight through it carries its full magnitude. So the flux is

$$
\iint_S\mathbf F\cdot\hat{\mathbf n}\,dA .
$$

$\mathbf F\cdot\hat{\mathbf n}$ is a scalar field, so this is a surface integral of the previous kind. But it can be shortened. Define the vector area element $d\mathbf S=\hat{\mathbf n}\,dA$. Since $\hat{\mathbf n}=\mathbf N/|\mathbf N|$ and $dA=|\mathbf N|\,ds\,dt$, the magnitudes cancel:

$$
d\mathbf S=\hat{\mathbf n}\,dA=\frac{\mathbf N}{|\mathbf N|}\,|\mathbf N|\,ds\,dt=\mathbf N\,ds\,dt=\Big(\frac{\partial\mathbf r}{\partial s}\times\frac{\partial\mathbf r}{\partial t}\Big)ds\,dt .
$$

No normalising is needed: compute $\mathbf N$, dot it with $\mathbf F$, integrate. The sign of $\mathbf N$ now matters, since reversing the normal reverses the flux, and it must be checked against the direction the question wants.

### Flux through a helicoid

Find the flux of $\mathbf F=x\,\mathbf i+y\,\mathbf j+(z-2y)\,\mathbf k$ through the helicoid

$$
\mathbf r=s\cos t\,\mathbf i+s\sin t\,\mathbf j+t\,\mathbf k,\qquad0\leq s\leq1,\quad0\leq t\leq2\pi ,
$$

a twisted ribbon like a spring or a spiral staircase. It is neither a graph nor a convenient level surface: above each point of the plane it passes at many heights. Here $s$ is the distance from the axis and $t$ both the angle and the height.

On the surface $x=s\cos t$, $y=s\sin t$, $z=t$, so

$$
\mathbf F=s\cos t\,\mathbf i+s\sin t\,\mathbf j+(t-2s\sin t)\,\mathbf k .
$$

The tangents are $\mathbf r_s=\cos t\,\mathbf i+\sin t\,\mathbf j$ and $\mathbf r_t=-s\sin t\,\mathbf i+s\cos t\,\mathbf j+\mathbf k$, so

$$
\mathbf N=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\cos t&\sin t&0\\-s\sin t&s\cos t&1\end{vmatrix}=\sin t\,\mathbf i-\cos t\,\mathbf j+\big(s\cos^2t+s\sin^2t\big)\,\mathbf k=\sin t\,\mathbf i-\cos t\,\mathbf j+s\,\mathbf k .
$$

Its $\mathbf k$ component $s$ is never negative, so this order gives the upward normal, the one taken when the question doesn't say. The dot product:

$$
\mathbf F\cdot\mathbf N=s\sin t\cos t-s\sin t\cos t+s(t-2s\sin t)=st-2s^2\sin t .
$$

Integrate in $t$ first, since $\sin t$ integrates to zero over a full period:

$$
\iint_S\mathbf F\cdot d\mathbf S=\int_0^1\Big[\frac{st^2}2+2s^2\cos t\Big]_0^{2\pi}ds=\int_0^12\pi^2s\,ds=\pi^2 .
$$

Integrating in $s$ first gives the same, as it must: $\int_0^1(st-2s^2\sin t)\,ds=\frac t2-\frac23\sin t$, and $\int_0^{2\pi}\big(\frac t2-\frac23\sin t\big)\,dt=\pi^2-0$.

![[m2048_vc_helicoid.png|620]]

### Flux through a funnel (PS10 Q4)

The funnel $x^2+y^2=z^2$, $0\leq z\leq9$, is a cone with $a=h$, opening upwards. Parametrise with $\mathbf r=z\cos\theta\,\mathbf i+z\sin\theta\,\mathbf j+z\,\mathbf k$; the cone working above with $a/h=1$ gives

$$
\mathbf r_\theta\times\mathbf r_z=z\cos\theta\,\mathbf i+z\sin\theta\,\mathbf j-z\,\mathbf k=x\,\mathbf i+y\,\mathbf j-z\,\mathbf k .
$$

At $(9,0,9)$ this is $(9,0,-9)$: away from the axis and downwards, which is out of the funnel, as the question asks. For $\mathbf F=-y\,\mathbf i+x\,\mathbf j+z\,\mathbf k$,

$$
\mathbf F\cdot\mathbf N=-xy+xy-z^2=-z^2,
$$

$$
\iint_S\mathbf F\cdot d\mathbf S=\int_0^9\int_0^{2\pi}(-z^2)\,d\theta\,dz=-2\pi\cdot\frac{9^3}{3}=-486\pi .
$$

The swirl part $-y\,\mathbf i+x\,\mathbf j$ runs round the funnel and carries nothing through it; the $z\,\mathbf k$ part points up, into the funnel against the outward normal, hence the negative sign.

![[m2048_vc_funnel_normal.png|640]]

### When the surface is a graph

If the surface is $z=f(x,y)$, use $x$ and $y$ themselves as the parameters, $\mathbf r=x\,\mathbf i+y\,\mathbf j+f(x,y)\,\mathbf k$. Then $\mathbf r_x=\mathbf i+f_x\,\mathbf k$ and $\mathbf r_y=\mathbf j+f_y\,\mathbf k$, and

$$
\mathbf N=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\1&0&f_x\\0&1&f_y\end{vmatrix}=-f_x\,\mathbf i-f_y\,\mathbf j+\mathbf k,\qquad d\mathbf S=\big(-f_x\,\mathbf i-f_y\,\mathbf j+\mathbf k\big)\,dx\,dy ,
$$

an upward normal. The flux is then a double integral over the shadow of the surface in the $xy$-plane. It is quicker when it applies, but the general parametrised form always works.

> [!check] SymPy
> Cylinder area $2\pi ah$, sphere area $4\pi a^2$, $\iint x^2z\,dA=\frac{\pi a^3h^2}2$, $\iint xy^2\,dA=0$, the helicoid flux $\pi^2$, and the graph normal $(-f_x,-f_y,1)$.

## 4. The 2023-24 exam, question B2(a)–(d)

The north hemisphere of the unit sphere is $\mathbf r=\sin s\cos t\,\mathbf i+\sin s\sin t\,\mathbf j+\cos s\,\mathbf k$, $0\leq s\leq\frac\pi2$, $0\leq t\leq2\pi$. Here $s$ is the polar angle and $t$ the azimuth, the reverse of the course's usual letters. The tangents are

$$
\mathbf r_s=\cos s\cos t\,\mathbf i+\cos s\sin t\,\mathbf j-\sin s\,\mathbf k,\qquad\mathbf r_t=-\sin s\sin t\,\mathbf i+\sin s\cos t\,\mathbf j ,
$$

and

$$
d\mathbf A=\mathbf r_s\times\mathbf r_t\,ds\,dt=\big(\sin^2s\cos t\,\mathbf i+\sin^2s\sin t\,\mathbf j+\sin s\cos s\,\mathbf k\big)\,ds\,dt ,
$$

which is $\sin s\,\hat{\mathbf r}$, outward. For $\mathbf F=3z\,\mathbf k=3\cos s\,\mathbf k$,

$$
\iint_S\mathbf F\cdot d\mathbf A=\int_0^{2\pi}\int_0^{\pi/2}3\sin s\cos^2s\,ds\,dt=2\pi\Big[-\cos^3s\Big]_0^{\pi/2}=2\pi .
$$

On the disc $x^2+y^2\leq1$, $z=0$, the field $3z\,\mathbf k$ is zero, so its flux is $0$. Part (e) uses the divergence theorem and is in [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem|VC5]].

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC3 - Line Integrals and Conservative Fields]] · Next: [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]
- Concepts: [[Flux Integrals]] · [[Jacobian and Volume Elements]] · [[Line Integrals]]

## Sources

- Lecture 27 (2 Dec 2024) and Lecture 28 (3 Dec 2024) recordings, Ian Hawke: `MATH2048 Lecture 27.txt`, `MATH2048 Lecture 28.txt`
- Slides `Lecture27_vector07.pdf`, `Lecture28_vector08.pdf`; lecture notes §8.2.3–8.2.6
- Problem Sheet 10; 2023/24 exam question B2

## Self-study tasks

Nothing was explicitly set. Lecture 27 left the integral of $xy^2$ over the cylinder unfinished (ll. 325–333).

### Core

- [ ] Lecturer-started (L27, ll. 312–333): finish $\iint xy^2\,dA$ over the cylinder. Answer: $0$. → [[#A scalar field over the cylinder]]
- [ ] Derive the sphere's normal and check that $\mathbf r_t\times\mathbf r_s=a^2\sin t\,\hat{\mathbf r}$ points outward. → [[#The normal from two tangent vectors]]
- [ ] PS10 Q1: the curved area of a cone of base radius $a$ and height $h$. Answer: $\pi a\sqrt{a^2+h^2}$. → [[#The area of a cone (PS10 Q1)]]
- [ ] 2023/24 B2(a)–(d). → [[#4. The 2023-24 exam, question B2(a)–(d)]]

### Further practice

- [ ] PS10 Q2: fluxes through the upper hemisphere $r=a$. Answers include $\frac{2\pi a^3}3$, $\pi a^2$ and $0$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] PS10 Q4: flux through the funnel $x^2+y^2=z^2$, $0\leq z\leq9$, outward. Answer: $-486\pi$. → [[#Flux through a funnel (PS10 Q4)]]
- [ ] Redo the helicoid flux integrating in $s$ first and check you still get $\pi^2$ (suggested, not lecturer-set). → [[#Flux through a helicoid]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lectures 27 and 28
> | Where | Transcript says | Correct |
> |---|---|---|
> | L27, ll. 17–18 | level surfaces called "this sort of parametric approach" | level surfaces are the implicit description; parametrisation is the third approach |
> | L27, l. 80 | $x$ "equal to 1" at $s=0$ | $a$, for a circle of radius $a$ |
> | L27, l. 263 | "dr by dt times delta s" | $\mathbf r_t\,\Delta t$ |
> | L27, l. 345 | "change the order of the S and C" | of $s$ and $t$ |
> | L28, l. 31 | "a circle of radius S" | radius $a$ |
> | L28, l. 95 | "cos squared as one half one minus two cos s" | $\cos^2s=\frac12(1+\cos2s)$; the sign doesn't affect this integral |
> | L28, l. 241 | "dr cross ds cross dr cross dt" | $\mathbf r_s\times\mathbf r_t$ |
> | L28, ll. 347–348 | the $\mathbf j$ component of the graph normal is "1 times dz dt" | $-f_y$; expanding the minor needs the minus sign |

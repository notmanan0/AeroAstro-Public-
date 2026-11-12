---
title: "MATH1054 M11 - Integration IV"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: topic
stream: "Block 1: Calculus"
order: 11
tags:
  - math1054
  - multiple-integrals
  - polar-coordinates
aliases: ["MATH1054 Module 11", "Integration IV", "Double integrals"]
date: 2026-09-27
status: lectured
coverage: "Module Booklet Module 11 work scheme (§§1–7: the double integral as a limit of sums, rectangular and non-rectangular regions, changing the order of integration, polar coordinates, triple integrals, applications to area, volume, mass, centre of mass and moments of inertia; Examples 1–5, Exercises A–G, Specimen Test 11); multiple integrals are not covered in James"
parent: ["[[MATH1054 Mathematics for Engineering and the Environment Hub]]"]
prerequisites: ["[[MATH1054 M10 - Integration III]]", "[[MATH1054 M03 - Differentiation I]]"]
next_topics: ["[[MATH1054 M14 - Vectors I]]"]
key_concepts: ["[[Double Integrals and Change of Order]]", "[[Jacobian and Volume Elements]]"]
tutorial_sheets: ["[[MATH1054 M11 Solutions - Integration IV]]"]
sources: ["02 - Sources/Course Booklets & Solutions/Module Booklet.pdf (Module 11, pp.29–42)"]
---

# MATH1054 M11 - Integration IV

> [!abstract] Summary
> A double integral $\iint_R f(x,y)\,\mathrm dx\,\mathrm dy$ is the limit of the sum $\sum f_i\,\delta S_i$ over small elements of a region $R$; for $f\geq0$ it is the volume under the surface $z=f(x,y)$ above $R$, and with $f=1$ it is the area of $R$. It is evaluated as two successive single integrals, the inner one along a strip with the outer variable held constant, and the whole difficulty lies in reading the limits off a sketch of $R$. Reversing the order of integration re-describes $R$ with strips the other way and can turn an impossible integral into an easy one. In polar coordinates the area element is $\mathrm dS=r\,\mathrm dr\,\mathrm d\theta$, and the same method extends to triple integrals and to the mass, centre of mass and moments of inertia of laminas and solids.

> [!summary]- Exam use: quick path
> - **Use it when:** a quantity is spread over a two- or three-dimensional region (area, volume under a surface, mass, centroid, second moment), or a single integral has no elementary antiderivative but came from a double integral that can be reversed.
> - **Assumptions:** $f$ is continuous on a bounded region $R$ whose boundary is made of a few smooth curves; each strip crosses the boundary exactly twice (otherwise split $R$); in polar coordinates $r\geq0$ and $\theta$ is in radians.
> - **Method:** 1. Draw every boundary named in the limits and shade $R$. 2. Choose the strip direction that gives the simplest limits and integrand. 3. Inner limits are functions of the outer variable; outer limits are numbers. 4. Integrate the inner integral with the outer variable constant, then integrate the result. 5. If the inner integral is impossible, reverse the order; if $R$ is circular or the integrand holds $x^2+y^2$, switch to polar and include the factor $r$.
> - **Common mistakes:** swapping the differentials and the limits together without re-describing $R$, which gives limits that depend on the wrong variable; dropping the $r$ in $r\,\mathrm dr\,\mathrm d\theta$.
> - **Practise:** [[#Example 2, a triangle both ways]] · [[MATH1054 M11 Solutions - Integration IV|Exercise E, reverse the order]]

A single integral $\int_a^b f(x)\,\mathrm dx$ adds up $f$ along an interval. Most physical quantities depend on more than one variable, so engineering needs integrals that add up a function over an area or a volume: the lift on a wing from the pressure over its planform, the mass of a plate whose thickness varies, the second moment of area of a beam section, the volume of fuel in a tank. The double integral is that sum, built in the same way as the single integral ([[MATH1054 M04 - Integration I|Module 4]]): cut the region into small pieces, multiply the value of the function on each piece by its size, add, and let the pieces shrink.

Nothing new is needed to evaluate one. A double integral is two single integrals done one after the other, so every technique from Modules 4, 9 and 10 (substitution, parts, partial fractions) still applies inside each stage. The geometry is the only addition: the limits of the inner integral describe where a strip enters and leaves the region, and they generally depend on where the strip is. Drawing the region is therefore not optional. Once the region is drawn, it can be swept in either direction, and choosing the direction well is the main skill of the topic.

Polar coordinates suit regions bounded by circles and rays from the origin, at the cost of a factor $r$ in the area element. That factor is the two-dimensional case of the Jacobian, which [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem|MATH2048 VC5]] generalises to cylindrical and spherical coordinates ([[Jacobian and Volume Elements]]). Triple integrals follow the same pattern with one more nesting. The applications in §7 (centroids and moments of inertia) are used in structures and dynamics: $I=\iint y^2\,\mathrm dA$ is the [[Second Moments of Area|second moment of area]] of a beam section.

---

## 1. The double integral as a limit of sums (Booklet §§1–2)

For a function of one variable, with $a=x_0<x_1<\dots<x_n=b$, $\delta x_i=x_i-x_{i-1}$ and $x_{i-1}\leq\xi_i\leq x_i$,

$$
\int_a^b f(x)\,\mathrm dx=\lim_{\delta x_i\to0}\ \sum_{i=1}^{n}f(\xi_i)\,\delta x_i ,
$$

which is the area between $y=f(x)$ and the $x$-axis for $f\geq0$.

The double integral is built the same way. A region $R$ of the $xy$-plane bounded by a closed curve is covered with a grid of lines parallel to the axes, spaced $\delta x$ and $\delta y$ apart. This cuts $R$ into $N$ small elements $\delta S_1,\dots,\delta S_N$, and away from the boundary each element is a rectangle with $\delta S_i=\delta x\,\delta y$. Pick any point $(x_i,y_i)$ inside the $i$-th element and write $f_i=f(x_i,y_i)$. For $f\geq0$, the product $f_i\,\delta S_i$ is the volume of a thin vertical column with base $\delta S_i$ and height $f_i$, so

$$
V_N=f_1\,\delta S_1+f_2\,\delta S_2+\dots+f_N\,\delta S_N=\sum_{i=1}^{N}f_i\,\delta S_i
$$

approximates the volume of the solid with base $R$ and top surface $z=f(x,y)$. If $V_N$ tends to a limit as $\delta x\to0$ and $\delta y\to0$ (so $N\to\infty$), that limit is the **double integral** of $f$ over $R$:

$$
\iint_R f(x,y)\,\mathrm dx\,\mathrm dy=\lim_{\delta x,\,\delta y\to0}\ \sum_{i=1}^{N}f_i\,\delta S_i .
$$

The limit exists, and does not depend on which point is chosen in each element, whenever $f$ is continuous on $R$ and the boundary of $R$ is a piecewise smooth curve (a merely continuous boundary curve can have positive area, and then the limit may fail to exist); every integral in this module meets those conditions. The element is written $\mathrm dS$ or $\mathrm dA$, and in Cartesian coordinates $\mathrm dS=\mathrm dx\,\mathrm dy$.

When $f=1$ everywhere, the integral is written $\iint_R\mathrm dx\,\mathrm dy$, and it has two readings that are numerically the same: the volume of a slab of uniform height $1$ standing on $R$, and the **area** of $R$.

![[m1054_m11_riemann_sum.png|900]]

The right-hand panel shows the sum for Booklet Example 1 below, $f=1+x+y$ on the square $1\leq x\leq2$, $0\leq y\leq1$, with $n\times n$ squares of side $h=1/n$ and each height taken at the lower-left corner $x_i=1+ih$, $y_j=jh$ ($i,j=0,\dots,n-1$). Because $\sum_i\sum_j h^2=1$, the sum splits into three parts:

$$
\begin{aligned}
V_N&=\sum_{i=0}^{n-1}\sum_{j=0}^{n-1}\big(1+x_i+y_j\big)h^2\\
&=1+h\sum_{i=0}^{n-1}x_i+h\sum_{j=0}^{n-1}y_j\\
&=1+h\Big(n+h\,\frac{n(n-1)}2\Big)+h^2\,\frac{n(n-1)}2\\
&=1+\Big(1+\frac{n-1}{2n}\Big)+\frac{n-1}{2n}\\
&=3-\frac1n .
\end{aligned}
$$

> [!check] The sum converges to the integral
> $V_N=2.9,\ 2.99,\ 2.999$ for $n=10,100,1000$, and the limit $3$ is the value of the double integral computed by iterated integration in §2. The corner sum underestimates because $f$ increases in both directions, and the error $1/n$ is proportional to the element size.

## 2. Iterated integrals on a rectangle (Booklet §3)

### From the sum to two single integrals

On a rectangle $a\leq x\leq b$, $c\leq y\leq d$, the elements can be grouped into rows. Number the grid so that element $(i,j)$ has corner $(x_i,y_j)$; then the sum can be added row by row, first along each row (fixed $y_j$, varying $x_i$) and then over the rows:

$$
\sum_{\text{all elements}}f\,\delta S=\sum_{j}\Big(\sum_{i}f(x_i,y_j)\,\delta x\Big)\delta y .
$$

As $\delta x\to0$, the bracket is a Riemann sum in $x$ alone with $y=y_j$ fixed, so it tends to $\int_a^bf(x,y_j)\,\mathrm dx$, a function of $y_j$ only. As $\delta y\to0$, the outer sum of that function times $\delta y$ tends to an integral over $y$:

$$
\iint_R f\,\mathrm dS=\int_{y=c}^{d}\Big(\int_{x=a}^{b}f(x,y)\,\mathrm dx\Big)\mathrm dy .
$$

This is an **iterated** (or repeated) integral. Geometrically, the inner integral is the area of the cross-section of the solid cut by the plane $y=\text{const}$, multiplying by $\mathrm dy$ gives the volume of a thin slice parallel to the $xz$-plane, and the outer integral adds the slices.

Grouping the same elements into columns instead gives

$$
\iint_R f\,\mathrm dS=\int_{x=a}^{b}\Big(\int_{y=c}^{d}f(x,y)\,\mathrm dy\Big)\mathrm dx ,
$$

slices parallel to the $yz$-plane. Both orders add the same columns, so for continuous $f$ they give the same number. The intermediate algebra is usually quite different.

The notation pairs integrals and differentials from the inside out: in $\int_c^d\!\int_a^b f\,\mathrm dx\,\mathrm dy$ the inner integral sign goes with the inner differential $\mathrm dx$, so $a$ and $b$ are limits on $x$ and that integral is done first, with $y$ treated as a constant. Writing the limits as $x=a$, $y=c$, or adding the brackets, removes any doubt.

### Constant limits and a product integrand

When the limits are all constants and $f(x,y)=g(x)\,h(y)$, the factor $h(y)$ is a constant for the inner integral and comes outside it:

$$
\begin{aligned}
\int_c^d\!\!\int_a^b g(x)\,h(y)\,\mathrm dx\,\mathrm dy&=\int_c^d h(y)\Big(\int_a^b g(x)\,\mathrm dx\Big)\mathrm dy\\
&=\Big(\int_a^b g(x)\,\mathrm dx\Big)\Big(\int_c^d h(y)\,\mathrm dy\Big),
\end{aligned}
$$

because the bracket is a number. The same holds with three factors in a triple integral (Exercise G, §6) and with polar limits (Specimen Test 11, Q4, §5). It fails as soon as a limit depends on the other variable.

### Example 1, a rectangle both ways

Evaluate $\displaystyle\int_{y=0}^{1}\int_{x=1}^{2}(1+x+y)\,\mathrm dx\,\mathrm dy$. All four limits are constants, so the region is the rectangle bounded by $x=1$, $x=2$, $y=0$, $y=1$. With $y$ fixed, the inner integral runs along a horizontal strip:

$$
\begin{aligned}
\int_1^2(1+x+y)\,\mathrm dx&=\Big[x+\tfrac12x^2+xy\Big]_{x=1}^{2}\\
&=(2+2+2y)-\big(1+\tfrac12+y\big)\\
&=\tfrac52+y .
\end{aligned}
$$

Then

$$
\int_0^1\Big(\tfrac52+y\Big)\mathrm dy=\Big[\tfrac52y+\tfrac12y^2\Big]_0^1=\tfrac52+\tfrac12=3 .
$$

In the other order the inner strip is vertical, $x$ is fixed and $0\leq y\leq1$:

$$
\begin{aligned}
\int_1^2\!\!\int_0^1(1+x+y)\,\mathrm dy\,\mathrm dx&=\int_1^2\Big[y+xy+\tfrac12y^2\Big]_{y=0}^{1}\mathrm dx\\
&=\int_1^2\Big(\tfrac32+x\Big)\mathrm dx\\
&=\Big[\tfrac32x+\tfrac12x^2\Big]_1^2\\
&=(3+2)-\big(\tfrac32+\tfrac12\big)=3 .
\end{aligned}
$$

The value $3$ is the volume of the solid standing on the rectangle with flat base $z=0$, sloping top $z=1+x+y$ and vertical sides $x=1$, $x=2$, $y=0$, $y=1$.

Exercises A and B apply the same steps. $\int_0^2\!\int_0^1(y+e^x)\,\mathrm dx\,\mathrm dy$ has inner integral $y+e-1$ and value $2e\approx5.4366$, and reversing it gives inner integral $2+2e^x$ and the same $2e$. $\int_0^{\pi/2}\!\int_0^{\pi/4}\sin(2x-y)\,\mathrm dx\,\mathrm dy$ has inner integral $\tfrac12(\cos y-\sin y)$ and value $0$: the integrand is positive on part of the rectangle and negative on the rest, and a double integral of a function that changes sign is a net signed volume.

## 3. Non-rectangular regions (Booklet §4)

### Vertical strips

Suppose $R$ lies between a lower curve $y=g_1(x)$ and an upper curve $y=g_2(x)$ that meet at $x=x_1$ and $x=x_2$, so that

$$
g_1(x)\leq y\leq g_2(x),\qquad x_1\leq x\leq x_2 .
$$

The column-by-column argument of §2 still works, but a column at position $x$ now runs only from $g_1(x)$ to $g_2(x)$. The inner integral is the area of the cross-section $APQB$ of the solid in the plane $x=\text{const}$,

$$
A(x)=\int_{y=g_1(x)}^{g_2(x)}f(x,y)\,\mathrm dy ,
$$

a function of $x$ only. The slice between $x$ and $x+\delta x$ has volume approximately $A(x)\,\delta x$, and adding the slices gives

$$
\iint_R f\,\mathrm dS=\int_{x=x_1}^{x_2}\Big(\int_{y=g_1(x)}^{g_2(x)}f(x,y)\,\mathrm dy\Big)\mathrm dx .
$$

### Horizontal strips

The same region can be described the other way. When both curves rise from left to right, as in the figure below, solving $y=g_2(x)$ for $x$ gives the left boundary $x=h_1(y)$ and solving $y=g_1(x)$ gives the right boundary $x=h_2(y)$ (the curves are the same; only the variable they are solved for changes). Then

$$
h_1(y)\leq x\leq h_2(y),\qquad y_1\leq y\leq y_2 ,
$$

and

$$
\iint_R f\,\mathrm dS=\int_{y=y_1}^{y_2}\Big(\int_{x=h_1(y)}^{h_2(y)}f(x,y)\,\mathrm dx\Big)\mathrm dy .
$$

![[m1054_m11_strips.png|900]]

Two rules follow from the construction. The inner limits may depend on the outer variable, because they say where a strip at that position enters and leaves $R$. The outer limits must be constants, because they say where the whole family of strips starts and stops. An answer that still contains $x$ or $y$ after both integrations means the limits were set up wrongly.

### Example 2, a triangle both ways

A solid of triangular cross-section with height $z=xy^2$ is bounded by the planes $z=0$, $x=0$, $y=0$ and $y=1-x$. Its volume is

$$
V=\int_{x=0}^{1}\int_{y=0}^{1-x}xy^2\,\mathrm dy\,\mathrm dx .
$$

The region comes from the four limits $x=0$, $x=1$, $y=0$, $y=1-x$; the integrand plays no part in finding it. It is the triangle with vertices $(0,0)$, $(1,0)$ and $(0,1)$. With $x$ fixed,

$$
\int_0^{1-x}xy^2\,\mathrm dy=x\Big[\tfrac13y^3\Big]_{y=0}^{1-x}=\tfrac13x(1-x)^3 .
$$

Expanding $(1-x)^3=1-3x+3x^2-x^3$,

$$
\begin{aligned}
V&=\tfrac13\int_0^1\big(x-3x^2+3x^3-x^4\big)\,\mathrm dx\\
&=\tfrac13\Big[\tfrac12x^2-x^3+\tfrac34x^4-\tfrac15x^5\Big]_0^1\\
&=\tfrac13\Big(\tfrac12-1+\tfrac34-\tfrac15\Big)\\
&=\tfrac13\cdot\tfrac1{20}=\tfrac1{60}.
\end{aligned}
$$

To reverse the order, fix $y$ and follow the line $y=\text{const}$ from left to right across the triangle: it enters at $x=0$ and leaves on the hypotenuse, which is $x=1-y$. Moving that line from the bottom of the triangle to the top sweeps $0\leq y\leq1$. So

$$
\begin{aligned}
V&=\int_{y=0}^{1}\int_{x=0}^{1-y}xy^2\,\mathrm dx\,\mathrm dy\\
&=\int_0^1y^2\Big[\tfrac12x^2\Big]_{x=0}^{1-y}\mathrm dy\\
&=\tfrac12\int_0^1y^2(1-2y+y^2)\,\mathrm dy\\
&=\tfrac12\Big[\tfrac13y^3-\tfrac12y^4+\tfrac15y^5\Big]_0^1\\
&=\tfrac12\Big(\tfrac13-\tfrac12+\tfrac15\Big)=\tfrac12\cdot\tfrac1{30}=\tfrac1{60}.
\end{aligned}
$$

> [!warning] Reversing the differentials is not reversing the order
> Writing $\int_{y=0}^{1-x}\int_{x=0}^{1}xy^2\,\mathrm dx\,\mathrm dy$, with the same limits attached to the swapped differentials, is meaningless: the outer limit $1-x$ contains the variable that has already been integrated out, so the result is not a number. The limits must be read again from the sketch, with strips in the new direction.

### Example 3, a strip that splits in two

Evaluate

$$
V=\int_{y=-1}^{1}\int_{x=0}^{y^2}(x+y)\,\mathrm dx\,\mathrm dy .
$$

The region is bounded by $y=-1$, $y=1$, $x=0$ and the parabola $x=y^2$: it is the area between the $y$-axis and the parabola, for $-1\leq y\leq1$. The inner integral is

$$
\int_0^{y^2}(x+y)\,\mathrm dx=\Big[\tfrac12x^2+xy\Big]_{x=0}^{y^2}=\tfrac12y^4+y^3 ,
$$

and

$$
\begin{aligned}
V&=\int_{-1}^{1}\Big(\tfrac12y^4+y^3\Big)\mathrm dy=\Big[\tfrac1{10}y^5+\tfrac14y^4\Big]_{-1}^{1}\\
&=\Big(\tfrac1{10}+\tfrac14\Big)-\Big(-\tfrac1{10}+\tfrac14\Big)=\tfrac15 .
\end{aligned}
$$

For the reverse order, take vertical strips. A vertical line at $0<x<1$ meets $R$ in two pieces, because the points with $-\sqrt x<y<\sqrt x$ lie to the right of the parabola and outside $R$. The lower piece runs from $y=-1$ to $y=-\sqrt x$ and the upper from $y=\sqrt x$ to $y=1$, so the $y$-integration splits:

$$
V=\int_{x=0}^{1}\Big\{\int_{y=-1}^{-\sqrt x}(x+y)\,\mathrm dy+\int_{y=\sqrt x}^{1}(x+y)\,\mathrm dy\Big\}\mathrm dx .
$$

The two inner integrals are

$$
\begin{aligned}
\int_{-1}^{-\sqrt x}(x+y)\,\mathrm dy&=\Big[xy+\tfrac12y^2\Big]_{-1}^{-\sqrt x}=\Big(-x^{3/2}+\tfrac12x\Big)-\Big(-x+\tfrac12\Big)=-x^{3/2}+\tfrac32x-\tfrac12,\\
\int_{\sqrt x}^{1}(x+y)\,\mathrm dy&=\Big[xy+\tfrac12y^2\Big]_{\sqrt x}^{1}=\Big(x+\tfrac12\Big)-\Big(x^{3/2}+\tfrac12x\Big)=-x^{3/2}+\tfrac12x+\tfrac12,
\end{aligned}
$$

which add to $-2x^{3/2}+2x$. Then

$$
V=\int_0^1\big(-2x^{3/2}+2x\big)\,\mathrm dx=\Big[-\tfrac45x^{5/2}+x^2\Big]_0^1=-\tfrac45+1=\tfrac15 .
$$

Here the first order is clearly simpler, because horizontal strips cross $R$ once and vertical ones twice. The integrand $x+y$ is negative on the whole lower half of $R$ (there $x\leq y^2\leq-y$), so $\tfrac15$ is a net signed volume: $\tfrac7{20}$ above the plane $z=0$ minus $\tfrac3{20}$ below it.

![[m1054_m11_example_regions.png|1000]]

### Exercise C, between a line and a parabola

$\displaystyle\int_{x=0}^{1}\int_{y=x}^{\sqrt x}(x^2+y^2)\,\mathrm dy\,\mathrm dx$ is taken over the region between the line $y=x$ (below) and the curve $y=\sqrt x$ (above), which meet at $(0,0)$ and $(1,1)$. The inner integral is

$$
\begin{aligned}
\Big[x^2y+\tfrac13y^3\Big]_{y=x}^{\sqrt x}&=x^{5/2}+\tfrac13x^{3/2}-x^3-\tfrac13x^3\\
&=x^{5/2}+\tfrac13x^{3/2}-\tfrac43x^3 ,
\end{aligned}
$$

and

$$
\int_0^1\Big(x^{5/2}+\tfrac13x^{3/2}-\tfrac43x^3\Big)\mathrm dx=\tfrac27+\tfrac2{15}-\tfrac13=\frac{30+14-35}{105}=\frac3{35}.
$$

With horizontal strips the same region is $y^2\leq x\leq y$, $0\leq y\leq1$, and $\int_0^1\!\int_{y^2}^{y}(x^2+y^2)\,\mathrm dx\,\mathrm dy$ also gives $\tfrac3{35}$.

## 4. Changing the order of integration (Booklet §4)

The procedure is the same every time:

1. Sketch $R$ from the given limits, drawing all four boundary curves.
2. Re-describe $R$ with strips in the other direction: for fixed values of the new outer variable, find where a strip enters and leaves $R$.
3. Invert each boundary curve so that it gives the new inner variable, for example $y=\sqrt x$ becomes $x=y^2$.
4. Read the new outer limits as the extreme values of the new outer variable over $R$, and split $R$ if a strip crosses the boundary more than twice.

There are two reasons to bother. Sometimes one order is shorter, because the integrand or the limits are simpler that way round, as in Example 3 and Exercise D. Sometimes the integral can only be done one way.

### Exercise D, a triangle both ways

Let $I=\iint_\Delta\dfrac xy\,\mathrm dx\,\mathrm dy$, where $\Delta$ is the inside of the triangle bounded by $x=1$, $y=2$ and $y=x$. The vertices are $(1,1)$, $(1,2)$ and $(2,2)$. Horizontal strips run from $x=1$ to $x=y$ for $1\leq y\leq2$, and vertical strips run from $y=x$ to $y=2$ for $1\leq x\leq2$.

With $x$ inner, $\frac1y$ is a constant factor for the first integration:

$$
\begin{aligned}
I&=\int_1^2\!\!\int_1^y\frac xy\,\mathrm dx\,\mathrm dy=\int_1^2\frac1y\cdot\frac{y^2-1}2\,\mathrm dy\\
&=\int_1^2\Big(\frac y2-\frac1{2y}\Big)\mathrm dy=\Big[\frac{y^2}4-\frac12\ln y\Big]_1^2\\
&=\Big(1-\tfrac12\ln2\Big)-\tfrac14=\tfrac34-\tfrac12\ln2 .
\end{aligned}
$$

With $y$ inner, the inner integral produces a logarithm:

$$
I=\int_1^2\!\!\int_x^2\frac xy\,\mathrm dy\,\mathrm dx=\int_1^2x\big(\ln2-\ln x\big)\,\mathrm dx .
$$

The first part is $\ln2\int_1^2x\,\mathrm dx=\tfrac32\ln2$, and by parts

$$
\int_1^2x\ln x\,\mathrm dx=\Big[\tfrac12x^2\ln x-\tfrac14x^2\Big]_1^2=2\ln2-\tfrac34 ,
$$

so $I=\tfrac32\ln2-2\ln2+\tfrac34=\tfrac34-\tfrac12\ln2\approx0.4034$, as before. The $x$-inner order avoids the integration by parts.

### Exercise E, the integral of e to the y cubed

$\displaystyle\int_0^1\!\!\int_{\sqrt x}^{1}e^{y^3}\,\mathrm dy\,\mathrm dx$ cannot be evaluated as written, because $e^{y^3}$ has no elementary antiderivative. The region is $\sqrt x\leq y\leq1$, $0\leq x\leq1$: above the curve $y=\sqrt x$ and below $y=1$. For fixed $y$, a horizontal strip runs from the $y$-axis to the curve, $0\leq x\leq y^2$, and $y$ runs from $0$ to $1$. So

$$
\begin{aligned}
\int_0^1\!\!\int_0^{y^2}e^{y^3}\,\mathrm dx\,\mathrm dy&=\int_0^1y^2e^{y^3}\,\mathrm dy\\
&=\Big[\tfrac13e^{y^3}\Big]_0^1=\tfrac13(e-1)\approx0.5728 .
\end{aligned}
$$

The $x$-integration of a function that does not depend on $x$ produced the length of the strip, $y^2$, which is exactly the factor needed for the substitution $u=y^3$.

![[m1054_double_integral_regions.png|800]]

The four panels show the regions of Exercises C, D, E and F with the strip that makes each integral work.

### Specimen Test 11, Q2 and Q3

The region between $y=x$ and $x=y^2$ (Q2) is described with $x$ fixed by $x\leq y\leq\sqrt x$, $0\leq x\leq1$, and with $y$ fixed by $y^2\leq x\leq y$, $0\leq y\leq1$; the two curves meet at $(0,0)$ and $(1,1)$, and $x=y^2$ is the upper boundary $y=\sqrt x$.

For Q3, $I=\int_{x=0}^1\!\int_{y=0}^{1-x^2}xy\,\mathrm dy\,\mathrm dx$ is taken over the curved triangle under the parabola $y=1-x^2$ in the first quadrant, with corners $(0,0)$, $(1,0)$ and $(0,1)$. Integrating $y$ first,

$$
\begin{aligned}
I&=\int_0^1\frac{x(1-x^2)^2}2\,\mathrm dx=\frac12\int_0^1\big(x-2x^3+x^5\big)\,\mathrm dx\\
&=\frac12\Big(\frac12-\frac12+\frac16\Big)=\frac1{12}.
\end{aligned}
$$

For fixed $y$, $x$ runs from $0$ to the parabola, $x=\sqrt{1-y}$, so

$$
I=\int_{y=0}^{1}\int_{x=0}^{\sqrt{1-y}}xy\,\mathrm dx\,\mathrm dy=\int_0^1y\cdot\frac{1-y}2\,\mathrm dy=\frac12\Big(\frac12-\frac13\Big)=\frac1{12}.
$$

![[m1054_spec11_regions.png|700]]

## 5. Polar coordinates (Booklet §5)

When $R$ is made of arcs of circles centred on the origin and straight lines through the origin, polar coordinates give constant limits. A point is located by its distance $r\geq0$ from the origin and the angle $\theta$ (radians) that its position vector makes with the positive $x$-axis, with

$$
x=r\cos\theta,\qquad y=r\sin\theta,\qquad x^2+y^2=r^2 .
$$

A double integral in polar coordinates needs three things: the region described by inequalities in $r$ and $\theta$, the integrand written as a function of $r$ and $\theta$, and the area element written in $r$ and $\theta$.

### The area element, derived

The grid lines are now circles $r=\text{const}$ and rays $\theta=\text{const}$. The element bounded by the arcs of radii $r$ and $r+\delta r$ and by the rays at $\theta$ and $\theta+\delta\theta$ is the difference of two circular sectors of angle $\delta\theta$, and a sector of radius $\rho$ and angle $\delta\theta$ has area $\tfrac12\rho^2\delta\theta$. So

$$
\begin{aligned}
\delta S&=\tfrac12(r+\delta r)^2\,\delta\theta-\tfrac12r^2\,\delta\theta\\
&=\tfrac12\big(2r\,\delta r+\delta r^2\big)\delta\theta\\
&=r\,\delta r\,\delta\theta+\tfrac12\,\delta r^2\,\delta\theta .
\end{aligned}
$$

The last term is of third order in small quantities and vanishes faster than the first in the limit of the sum, so

$$
\mathrm dS=\mathrm dx\,\mathrm dy\ \longrightarrow\ \mathrm dS=r\,\mathrm dr\,\mathrm d\theta ,
\qquad
\iint_R f\,\mathrm dS=\iint_R f(r\cos\theta,r\sin\theta)\,r\,\mathrm dr\,\mathrm d\theta .
$$

Geometrically the element is nearly a rectangle with a radial side $\delta r$ and an arc side $r\,\delta\theta$; the arc side grows with $r$ because a fixed angle subtends a longer arc further from the origin.

![[m1054_m11_polar_element.png|900]]

The same factor comes out of the Jacobian determinant of the map $(r,\theta)\mapsto(x,y)$, which measures how much a small parameter rectangle $\delta r\times\delta\theta$ is stretched:

$$
\begin{aligned}
\frac{\partial(x,y)}{\partial(r,\theta)}&=\begin{vmatrix}\partial x/\partial r&\partial x/\partial\theta\\ \partial y/\partial r&\partial y/\partial\theta\end{vmatrix}
=\begin{vmatrix}\cos\theta&-r\sin\theta\\ \sin\theta&r\cos\theta\end{vmatrix}\\
&=r\cos^2\theta+r\sin^2\theta=r .
\end{aligned}
$$

[[Jacobian and Volume Elements]] extends this to cylindrical ($\rho$) and spherical ($r^2\sin\theta$) coordinates.

> [!warning] The factor r is part of the element
> $\iint_R f\,\mathrm dr\,\mathrm d\theta$ without the $r$ is wrong even when $f=1$: for the unit disc it gives $\int_0^{2\pi}\!\int_0^1\mathrm dr\,\mathrm d\theta=2\pi$ instead of the area $\int_0^{2\pi}\!\int_0^1r\,\mathrm dr\,\mathrm d\theta=\pi$.

### The area inside a polar curve

For a region bounded by the curve $r=f(\theta)$ and the rays $\theta=\alpha$, $\theta=\beta$, every ray runs from the origin out to the curve, so

$$
\begin{aligned}
A&=\int_\alpha^\beta\!\!\int_0^{f(\theta)}r\,\mathrm dr\,\mathrm d\theta\\
&=\int_\alpha^\beta\Big[\tfrac12r^2\Big]_0^{f(\theta)}\mathrm d\theta\\
&=\tfrac12\int_\alpha^\beta f(\theta)^2\,\mathrm d\theta .
\end{aligned}
$$

### Example 4, part of an annulus

Evaluate $I=\iint_R\dfrac{y^2}{x^2}\,\mathrm dx\,\mathrm dy$, where $R$ is the part of the annulus $a^2\leq x^2+y^2\leq b^2$ in the first quadrant below the line $y=x$. The circles are $r=a$ and $r=b$, and the line $y=x$ is the ray $\theta=\pi/4$, so $R$ is $a\leq r\leq b$, $0\leq\theta\leq\pi/4$. The integrand is

$$
\frac{y^2}{x^2}=\frac{r^2\sin^2\theta}{r^2\cos^2\theta}=\tan^2\theta ,
$$

and with $\mathrm dS=r\,\mathrm dr\,\mathrm d\theta$,

$$
\begin{aligned}
I&=\int_{\theta=0}^{\pi/4}\int_{r=a}^{b}\tan^2\theta\,r\,\mathrm dr\,\mathrm d\theta
=\int_0^{\pi/4}\tan^2\theta\Big[\tfrac12r^2\Big]_{r=a}^{b}\mathrm d\theta\\
&=\frac{b^2-a^2}2\int_0^{\pi/4}\tan^2\theta\,\mathrm d\theta
=\frac{b^2-a^2}2\int_0^{\pi/4}\big(\sec^2\theta-1\big)\,\mathrm d\theta\\
&=\frac{b^2-a^2}2\Big[\tan\theta-\theta\Big]_0^{\pi/4}
=\frac{b^2-a^2}2\Big(1-\frac\pi4\Big)\\
&=\frac{(4-\pi)(b^2-a^2)}8 ,
\end{aligned}
$$

using $1+\tan^2\theta=\sec^2\theta$. In Cartesian coordinates the same region needs two or three pieces with square-root limits.

> [!check] Example 4 against a Cartesian grid
> For $a=1$, $b=2$ the formula gives $3(4-\pi)/8=0.3219$. A midpoint sum of $y^2/x^2$ over the points of a $4000\times4000$ Cartesian grid that lie in $R$ gives $0.3221$; the small excess comes from the grid cells cut by the curved boundary.

### Exercise F, the cardioid

The cardioid $r=a(1-\cos\theta)$, $0\leq\theta\leq2\pi$, passes through the origin at $\theta=0$ and reaches $r=2a$ at $\theta=\pi$. By the polar-curve area formula,

$$
\begin{aligned}
A&=\int_0^{2\pi}\!\!\int_0^{a(1-\cos\theta)}r\,\mathrm dr\,\mathrm d\theta=\tfrac12a^2\int_0^{2\pi}(1-\cos\theta)^2\,\mathrm d\theta\\
&=\tfrac12a^2\int_0^{2\pi}\big(1-2\cos\theta+\cos^2\theta\big)\,\mathrm d\theta .
\end{aligned}
$$

Over a full period $\int_0^{2\pi}\cos\theta\,\mathrm d\theta=0$, and $\int_0^{2\pi}\cos^2\theta\,\mathrm d\theta=\int_0^{2\pi}\tfrac12(1+\cos2\theta)\,\mathrm d\theta=\pi$, so

$$
A=\tfrac12a^2\big(2\pi-0+\pi\big)=\tfrac32\pi a^2 .
$$

The cardioid is traced by a point on a circle of radius $a/2$ rolling round a fixed circle of the same radius, and its area is six times the area $\tfrac14\pi a^2$ of that circle.

### Specimen Test 11, Q4

The element of area in plane polar coordinates is $\mathrm dS=r\,\mathrm dr\,\mathrm d\theta$. With constant limits and a product integrand, the integral separates:

$$
\int_{\theta=0}^{\pi}\int_{r=0}^{a}\sin\theta\,r\,\mathrm dr\,\mathrm d\theta=\Big[-\cos\theta\Big]_0^{\pi}\Big[\tfrac12r^2\Big]_0^{a}=2\cdot\tfrac12a^2=a^2 .
$$

## 6. Triple integrals (Booklet §6)

A triple integral $\iiint_V f(x,y,z)\,\mathrm dx\,\mathrm dy\,\mathrm dz$ is the limit of $\sum f_i\,\delta V_i$ over small boxes $\delta V_i=\delta x\,\delta y\,\delta z$ filling a solid $V$. It is evaluated as three nested single integrals whose limits generally depend on the variables still outside them. The procedure is:

1. Fix one variable, say $z$, within its range; geometrically this slices the solid with a plane perpendicular to the $z$-axis.
2. Find the range of a second variable, say $y$, across that slice; it may depend on $z$.
3. Find the range of the last variable, $x$, along a line in the slice; it may depend on $y$ and $z$.

With $f=1$ the integral is the volume of the solid, with $f=\rho$ (mass per unit volume) it is the mass, and $\bar x=\frac1V\iiint x\,\mathrm dV$ is the $x$-coordinate of the centroid.

### Example 5, a box

Evaluate $\iiint_B(xy^2+z^3)\,\mathrm dx\,\mathrm dy\,\mathrm dz$ over the box $0\leq x\leq a$, $0\leq y\leq b$, $0\leq z\leq c$. Every slice of a box is a rectangle, so all the limits are constants:

$$
\begin{aligned}
I&=\int_0^c\!\!\int_0^b\Big[\tfrac12x^2y^2+xz^3\Big]_{x=0}^{a}\mathrm dy\,\mathrm dz
=\int_0^c\!\!\int_0^b\Big(\tfrac12a^2y^2+az^3\Big)\mathrm dy\,\mathrm dz\\
&=\int_0^c\Big[\tfrac16a^2y^3+ayz^3\Big]_{y=0}^{b}\mathrm dz
=\int_0^c\Big(\tfrac16a^2b^3+abz^3\Big)\mathrm dz\\
&=\Big[\tfrac16a^2b^3z+\tfrac14abz^4\Big]_{z=0}^{c}
=\frac{a^2b^3c}6+\frac{abc^4}4 .
\end{aligned}
$$

The region of integration is a volume, but the integral is not that volume: it is, for example, the mass of the box when its density is $xy^2+z^3$.

### Exercise G, a product over a box

$\displaystyle\int_0^3\!\!\int_0^2\!\!\int_0^1x\,\mathrm dx\,\mathrm dy\,\mathrm dz$ has constant limits and an integrand that depends on $x$ only, so it factorises:

$$
\Big(\int_0^1x\,\mathrm dx\Big)\Big(\int_0^2\mathrm dy\Big)\Big(\int_0^3\mathrm dz\Big)=\tfrac12\cdot2\cdot3=3 .
$$

The box $[0,1]\times[0,2]\times[0,3]$ has volume $V=6$ and centroid $\bar x=\tfrac12$, and $\iiint x\,\mathrm dV=\bar x\,V=3$ agrees.

### A tetrahedron, with limits that depend on the outer variables

For the tetrahedron $x,y,z\geq0$, $x+y+z\leq1$, fix $x$ and $y$; a vertical line enters at $z=0$ and leaves through the slanted face $z=1-x-y$. The shadow of the solid on the $xy$-plane is the triangle of Example 2, $0\leq y\leq1-x$, $0\leq x\leq1$. So

$$
\begin{aligned}
V&=\int_0^1\!\!\int_0^{1-x}\!\!\int_0^{1-x-y}\mathrm dz\,\mathrm dy\,\mathrm dx
=\int_0^1\!\!\int_0^{1-x}(1-x-y)\,\mathrm dy\,\mathrm dx\\
&=\int_0^1\tfrac12(1-x)^2\,\mathrm dx=\Big[-\tfrac16(1-x)^3\Big]_0^1=\tfrac16 ,
\end{aligned}
$$

and in the same way $\iiint z\,\mathrm dV=\int_0^1\!\int_0^{1-x}\tfrac12(1-x-y)^2\,\mathrm dy\,\mathrm dx=\int_0^1\tfrac16(1-x)^3\,\mathrm dx=\tfrac1{24}$, so $\bar z=\frac{1/24}{1/6}=\tfrac14$: the centroid of a tetrahedron lies a quarter of the way up from the base.

## 7. Area, volume, mass, centre of mass and moments of inertia (Booklet §7)

Each application comes from the limit-of-sums definition by choosing what each element contributes.

For a region $R$ of the $xy$-plane, each element contributes its own area, so the area is $A=\iint_R\mathrm dx\,\mathrm dy$. Above $R$ and below a surface $z=f(x,y)>0$, each element carries a column of volume $f\,\delta S$, so the volume is $V=\iint_R f(x,y)\,\mathrm dx\,\mathrm dy$.

For a thin lamina occupying $R$ with density $\rho(x,y)$ (mass per unit area), the element $\delta S$ has mass $\delta m=\rho\,\delta S$, so the total mass is

$$
M=\iint_R\rho(x,y)\,\mathrm dx\,\mathrm dy .
$$

The centre of mass $(\bar x,\bar y)$ is the point at which the whole mass, concentrated, would have the same first moment about each axis as the lamina. The element $\delta m$ at $(x,y)$ has moment $x\,\delta m$ about the $y$-axis, so $M\bar x=\sum x\,\delta m$, and in the limit

$$
\bar x=\frac1M\iint_R x\,\rho\,\mathrm dx\,\mathrm dy,\qquad
\bar y=\frac1M\iint_R y\,\rho\,\mathrm dx\,\mathrm dy .
$$

For uniform density $\rho$ cancels and $(\bar x,\bar y)$ is the **centroid** of $R$, a property of the shape alone.

The moment of inertia of a mass $\delta m$ about an axis is $d^2\,\delta m$, where $d$ is its distance from the axis. The distance of $(x,y)$ from the $x$-axis is $|y|$ and from the $y$-axis is $|x|$, so

$$
I_x=\iint_R y^2\rho\,\mathrm dx\,\mathrm dy,\qquad
I_y=\iint_R x^2\rho\,\mathrm dx\,\mathrm dy .
$$

The distance from the origin is $\sqrt{x^2+y^2}$, so the polar moment of inertia about the axis through $O$ perpendicular to the lamina is

$$
I_0=\iint_R\big(x^2+y^2\big)\rho\,\mathrm dx\,\mathrm dy=I_x+I_y ,
$$

the perpendicular axis theorem. With $\rho=1$ these are the second moments of area used in beam bending ([[Second Moments of Area]]).

For a solid with density $\rho(x,y,z)$ (mass per unit volume) the same arguments give the volume $V=\iiint\mathrm dx\,\mathrm dy\,\mathrm dz$, the mass $M=\iiint\rho\,\mathrm dV$ and the centre of mass

$$
\bar x=\frac1M\iiint x\rho\,\mathrm dV,\qquad\bar y=\frac1M\iiint y\rho\,\mathrm dV,\qquad\bar z=\frac1M\iiint z\rho\,\mathrm dV ,
$$

with moments of inertia built from the squared distance from the chosen axis, for example $I_z=\iiint(x^2+y^2)\rho\,\mathrm dV$.

### A triangular lamina, uniform and graded

Take the triangle $x,y\geq0$, $x+y\leq1$ of Example 2, described by $0\leq y\leq1-x$, $0\leq x\leq1$. With uniform density $\rho=1$,

$$
\begin{aligned}
A&=\int_0^1\!\!\int_0^{1-x}\mathrm dy\,\mathrm dx=\int_0^1(1-x)\,\mathrm dx=\tfrac12 ,\\
\iint x\,\mathrm dA&=\int_0^1x(1-x)\,\mathrm dx=\tfrac12-\tfrac13=\tfrac16 ,\qquad\bar x=\frac{1/6}{1/2}=\tfrac13 ,\\
I_x&=\int_0^1\Big[\tfrac13y^3\Big]_0^{1-x}\mathrm dx=\int_0^1\tfrac13(1-x)^3\,\mathrm dx=\tfrac1{12} .
\end{aligned}
$$

By the symmetry of the triangle in the line $y=x$, $\bar y=\tfrac13$ and $I_y=\tfrac1{12}$, so $I_0=\tfrac16$. The centroid $(\tfrac13,\tfrac13)$ is the average of the three vertices, as it is for every triangle.

Let the density increase across the plate, $\rho=x$. Then

$$
\begin{aligned}
M&=\int_0^1x(1-x)\,\mathrm dx=\tfrac16 ,\\
\iint x\rho\,\mathrm dA&=\int_0^1x^2(1-x)\,\mathrm dx=\tfrac13-\tfrac14=\tfrac1{12} ,\qquad\bar x=\frac{1/12}{1/6}=\tfrac12 ,\\
\iint y\rho\,\mathrm dA&=\int_0^1x\cdot\tfrac12(1-x)^2\,\mathrm dx=\tfrac12\Big(\tfrac12-\tfrac23+\tfrac14\Big)=\tfrac1{24} ,\qquad\bar y=\frac{1/24}{1/6}=\tfrac14 ,
\end{aligned}
$$

and $I_x=\int_0^1\tfrac13x(1-x)^3\,\mathrm dx=\tfrac1{60}$, $I_y=\int_0^1x^3(1-x)\,\mathrm dx=\tfrac1{20}$. The centre of mass moves from $(\tfrac13,\tfrac13)$ to $(\tfrac12,\tfrac14)$, straight towards the heavy vertex $(1,0)$.

![[m1054_m11_lamina_centroids.png|900]]

### The second moment of a rectangular section

For a rectangle of width $b$ and depth $h$ with its centroid at the origin, about the horizontal centroidal axis,

$$
\begin{aligned}
I_x&=\int_{-h/2}^{h/2}\!\!\int_{-b/2}^{b/2}y^2\,\mathrm dx\,\mathrm dy=b\int_{-h/2}^{h/2}y^2\,\mathrm dy\\
&=b\Big[\tfrac13y^3\Big]_{-h/2}^{h/2}=b\Big(\frac{h^3}{24}+\frac{h^3}{24}\Big)=\frac{bh^3}{12} .
\end{aligned}
$$

About the base ($0\leq y\leq h$) the same integral gives $bh^3/3$. The cube of the depth is why a beam is stiffer on edge than flat.

### A quarter disc in polar coordinates

For the uniform quarter disc $0\leq r\leq a$, $0\leq\theta\leq\pi/2$, the area is $\int_0^{\pi/2}\!\int_0^ar\,\mathrm dr\,\mathrm d\theta=\tfrac14\pi a^2$, and

$$
\begin{aligned}
\iint x\,\mathrm dA&=\int_0^{\pi/2}\!\!\int_0^a(r\cos\theta)\,r\,\mathrm dr\,\mathrm d\theta
=\Big[\tfrac13r^3\Big]_0^a\Big[\sin\theta\Big]_0^{\pi/2}=\tfrac13a^3 ,\\
\bar x&=\frac{a^3/3}{\pi a^2/4}=\frac{4a}{3\pi}\approx0.424\,a ,
\end{aligned}
$$

with $\bar y=\bar x$ by symmetry. The polar moment is $I_0=\int_0^{\pi/2}\!\int_0^ar^2\cdot r\,\mathrm dr\,\mathrm d\theta=\tfrac\pi2\cdot\tfrac14a^4=\tfrac18\pi a^4$, so $I_x=I_y=\tfrac1{16}\pi a^4$. The $4a/3\pi$ result is the standard centroid of a semicircular or quarter-circular section, here obtained without any Cartesian square roots.

## Links

- Parent: [[MATH1054 Mathematics for Engineering and the Environment Hub]] · Solutions: [[MATH1054 M11 Solutions - Integration IV]]
- Previous: [[MATH1054 M10 - Integration III]] · Next: [[MATH1054 M14 - Vectors I]]
- Earlier: the definite integral as a limit of sums in [[MATH1054 M04 - Integration I]]; centroids of simple shapes by single integrals in [[Centroids and Solids of Revolution]]; integration by parts ([[Integration by Parts]]) and substitution ([[Integration by Substitution]]) inside each stage.
- Concepts: [[Double Integrals and Change of Order]] · [[Jacobian and Volume Elements]]
- Later: cylindrical and spherical volume elements and the divergence theorem in [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]; surface integrals in [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]; $I=\iint y^2\,\mathrm dA$ for beam sections in [[Second Moments of Area]]; moments of inertia of rigid bodies in [[SESA3047 3.3 - Rigid-Body Rotational Dynamics]].

## Sources

- MATH1054 Module Booklet, Module 11 (Integration IV), PDF pp. 29–42: Work Scheme A §§1–7, Examples 1–5, Exercises A–G, Specimen Test 11 (p. 42). Multiple integrals are not in James, *Modern Engineering Mathematics*, so the booklet is the whole source.
- Work Scheme B (Stroud, *Engineering Mathematics*, 6th ed., Programme 23, frames 1–46) covers the same double and triple integrals without the change of order.
- Worked solutions: [[MATH1054 M11 Solutions - Integration IV]].

## Self-study tasks

### Core

- [ ] Exercise C (Module 11 work scheme): $\int_0^1\!\int_x^{\sqrt x}(x^2+y^2)\,\mathrm dy\,\mathrm dx=\tfrac3{35}$. → [[#Exercise C, between a line and a parabola]] · [[MATH1054 M11 Solutions - Integration IV|solution]]
- [ ] Exercise D (Module 11 work scheme): set up $\iint_\Delta\frac xy\,\mathrm dS$ both ways and show $I=\tfrac34-\tfrac12\ln2$. → [[#Exercise D, a triangle both ways]] · [[MATH1054 M11 Solutions - Integration IV|solution]]
- [ ] Exercise E (Module 11 work scheme): $\int_0^1\!\int_{\sqrt x}^1e^{y^3}\,\mathrm dy\,\mathrm dx=\tfrac13(e-1)$ by reversing the order. → [[#Exercise E, the integral of e to the y cubed]] · [[MATH1054 M11 Solutions - Integration IV|solution]]
- [ ] Exercise F (Module 11 work scheme): the area of the cardioid $r=a(1-\cos\theta)$ is $\tfrac32\pi a^2$. → [[#Exercise F, the cardioid]] · [[MATH1054 M11 Solutions - Integration IV|solution]]
- [ ] Specimen Test 11, Q3: sketch, evaluate both ways, $I=\tfrac1{12}$. → [[#Specimen Test 11, Q2 and Q3]] · [[MATH1054 M11 Solutions - Integration IV#Part C: Specimen Test 11|solution]]

### Further practice

- [ ] Exercise A (Module 11 work scheme): $2e$ and $0$. → [[MATH1054 M11 Solutions - Integration IV#Exercise A: Evaluate directly]]
- [ ] Exercise B (Module 11 work scheme): Exercise A(i) with the order changed. → [[MATH1054 M11 Solutions - Integration IV#Exercise B: A(i) with the order changed]]
- [ ] Exercise G (Module 11 work scheme): $\iiint x\,\mathrm dV=3$ over the box. → [[#Exercise G, a product over a box]] · [[MATH1054 M11 Solutions - Integration IV|solution]]
- [ ] Specimen Test 11, Q1, Q2 and Q4: $\tfrac{35}6$, $\tfrac25$; the region between $y=x$ and $x=y^2$; $a^2$. → [[MATH1054 M11 Solutions - Integration IV#Q1: Double integrals]] · [[#Specimen Test 11, Q2 and Q3]] · [[MATH1054 M11 Solutions - Integration IV#Q4: Polar coordinates]]
- [ ] Booklet Examples 2 to 4 (Module 11 work scheme): rework each in both orders, or in Cartesian form for Example 4, before reading the solution. → [[#Example 2, a triangle both ways]] · [[#Example 3, a strip that splits in two]] · [[#Example 4, part of an annulus]]

## Transcript and slide slips

> [!warning] Booklet Example 3 is a net signed volume
> Where: [[#Example 3, a strip that splits in two]]
>
> Booklet p. 36 describes $\int_{-1}^{1}\!\int_0^{y^2}(x+y)\,\mathrm dx\,\mathrm dy$ as the volume under the surface $z=x+y$ above the shaded region. On the lower half of the region ($-1\leq y\leq0$, $0\leq x\leq y^2$) the surface lies below the plane $z=0$, so the value $\tfrac15$ is a net signed volume, $\tfrac7{20}-\tfrac3{20}$; the geometric volume between the surface and the plane is $\tfrac7{20}+\tfrac3{20}=\tfrac12$.

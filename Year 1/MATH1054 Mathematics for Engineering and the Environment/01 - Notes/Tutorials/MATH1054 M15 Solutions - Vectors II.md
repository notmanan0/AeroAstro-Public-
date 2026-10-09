---
title: "MATH1054 M15 Solutions - Vectors II"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: tutorial
stream: "Block 4: Vectors and Matrices"
tags:
  - math1054
  - tutorial-solutions
  - vectors
  - lines-and-planes
sheet: "Specimen Test 15 (booklet) + Module 15 work scheme: Examples 4.31–4.48, 9.20, 9.21; Exercises 57, 58, 59, 66, 68, 71, 72, 73, 79 (Ch.4), 32, 34, 35 (Ch.9); Booklet Exercise A"
theory_notes: ["[[MATH1054 M15 - Vectors II]]"]
key_concepts: ["[[Scalar Triple Product]]", "[[Equations of Lines and Planes]]", "[[Differentiation of Vectors]]"]
status: complete
sources: ["tmp/md/module_15_vectors_ii.md", "02 - Sources/Modern Engineering Mathematics.pdf (§4.3.3–4.4, §9.5)"]
---

# MATH1054 M15 Solutions - Vectors II

> [!abstract] Sheet Info
> The whole Module 15 work scheme. Triple products, intersections and distances were checked with SymPy `Matrix`/`solve`.
>
> **Key formulas**:
> - **Scalar triple product**: $[\mathbf a,\mathbf b,\mathbf c]=\mathbf a\cdot(\mathbf b\times\mathbf c)=\det[\mathbf a\ \mathbf b\ \mathbf c]$.
> - **Line**: $\mathbf r=\mathbf a+t\mathbf d$.
> - **Plane**: $\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n$.

## Theory Links
- [[MATH1054 M15 - Vectors II]] · [[Scalar Triple Product]] · [[Equations of Lines and Planes]] · [[Differentiation of Vectors]]

---

# Part A: Worked examples

## Example 4.31: Choose $\lambda$ so the vectors are coplanar
Three vectors are coplanar iff their triple product is zero:

$$\begin{vmatrix}2&-1&1\\1&2&-3\\3&\lambda&5\end{vmatrix}=2(10+3\lambda)+1(5+9)+1(\lambda-6)=7\lambda+28=0\ \Rightarrow\ \boxed{\lambda=-4}$$

## Example 4.34: Verify the triple vector product identity
With $\mathbf a=(3,-2,1)$, $\mathbf b=(-1,3,4)$, $\mathbf c=(2,1,-3)$:
- $\mathbf b\times\mathbf c=(-9-4,\ 8-3,\ -1-6)=(-13,5,-7)$
- $\mathbf a\times(\mathbf b\times\mathbf c)=(3,-2,1)\times(-13,5,-7)=(14-5,\ -13+21,\ 15-26)=\boxed{(9,8,-11)}$
- $\mathbf a\cdot\mathbf c=6-2-3=1$ and $\mathbf a\cdot\mathbf b=-3-6+4=-5$, so $(\mathbf a\cdot\mathbf c)\mathbf b-(\mathbf a\cdot\mathbf b)\mathbf c=(-1,3,4)+5(2,1,-3)=(9,8,-11)$ ✔

## Example 4.37: Do $L_1$ and $L_2$ intersect?
- $L_1$: $\mathbf r=(0,1,0)+s(1,2,-1)$
- $L_2$: $\mathbf r=(1,1,1)+t(-2,-2,0)$

Set them equal, component by component:
- $x$: $s=1-2t$
- $y$: $1+2s=1-2t$
- $z$: $-s=1$

So $s=-1$, and then $t=1$. Check the $y$-equation: $1-2=1-2$ ✔. All three equations agree, so the lines **intersect** at $\boxed{(-1,-1,1)}$.

## Example 4.38: Line AB and the coordinate planes
$\mathbf r=(1,4,6)+t(2,1,1)$.

| Plane | Condition | $t$ | Point |
|---|---|---|---|
| $x=0$ | $1+2t=0$ | $-\frac12$ | $(0,\frac72,\frac{11}2)$ |
| $y=0$ | $4+t=0$ | $-4$ | $(-7,0,2)$ |
| $z=0$ | $6+t=0$ | $-6$ | $(-11,-2,0)$ |

## Example 4.39: Find $\alpha$ so the lines intersect
- $L_1$: $(5,1,7)+s(1,-1,1)$
- $L_2$: $(3,1,3)+t(-4,2,\alpha-3)$

Equate components:
- $x$: $5+s=3-4t$
- $y$: $1-s=1+2t$, so $s=-2t$

Substituting into the $x$-equation: $5-2t=3-4t$, so $t=-1$ and $s=2$.
- $z$: $7+2=3-(\alpha-3)$, so $\alpha=\boxed{-3}$.

The intersection point is $(7,-1,9)$.

## Example 4.42: Shortest distance between skew lines, and the common perpendicular
- $L_1$: $\mathbf a_1=(0,9,2)$, $\mathbf d_1=(3,-1,1)$
- $L_2$: $\mathbf a_2=(-6,-5,10)$, $\mathbf d_2=(-3,2,4)$

The common normal is $\mathbf n=\mathbf d_1\times\mathbf d_2=(-4-2,\ -3-12,\ 6-3)=(-6,-15,3)\ \propto(2,5,-1)$. Then

$$d=\frac{|(\mathbf a_2-\mathbf a_1)\cdot\mathbf n|}{|\mathbf n|}=\frac{|(-6,-14,8)\cdot(2,5,-1)|}{\sqrt{30}}=\frac{90}{\sqrt{30}}=\boxed{3\sqrt{30}\approx16.43}$$

**The common perpendicular.** The feet are $\mathrm P=\mathbf a_1+s\mathbf d_1$ and $\mathrm Q=\mathbf a_2+t\mathbf d_2$, with $\vec{\mathrm{PQ}}\perp\mathbf d_1$ and $\vec{\mathrm{PQ}}\perp\mathbf d_2$. Solving gives $s=1$ and $t=-1$, so $\mathrm P=(3,8,3)$ and $\mathrm Q=(-3,-7,6)$.

$$\boxed{\mathbf r=(3,8,3)+\mu(2,5,-1)}\qquad\Big(\tfrac{x-3}2=\tfrac{y-8}5=\tfrac{z-3}{-1}\Big)$$

**Check**: $|\mathrm{PQ}|=|(-6,-15,3)|=\sqrt{270}=3\sqrt{30}$ ✔

## Example 4.44: The plane through $(1,1,1)$, $(0,1,2)$, $(-1,1,-1)$
$\mathbf n=(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)=(-1,0,1)\times(-2,0,-2)=(0,-4,0)\propto(0,1,0)$. Then $\mathbf r\cdot(0,1,0)=\mathbf a\cdot(0,1,0)=1$:

$$\boxed{y=1}$$

All three points have $y=1$ ✔.

## Example 4.46: Where the line $(2,1,1)+\lambda(0,1,2)$ meets the plane $\mathbf r\cdot(1,1,2)=3$
Substitute the line into the plane:

$$2+(1+\lambda)+2(1+2\lambda)=5+5\lambda=3\ \Rightarrow\ \lambda=-\tfrac25\ \Rightarrow\ \boxed{\big(2,\tfrac35,\tfrac15\big)}$$

## Example 4.47: The line of intersection of $x+y+z=5$ and $4x+y+2z=15$
- The direction is perpendicular to both normals: $(1,1,1)\times(4,1,2)=(2-1,\ 4-2,\ 1-4)=(1,2,-3)$.
- A point on both planes: set $z=1$. Then $x+y=4$ and $4x+y=13$, so $x=3$ and $y=1$. The point is $(3,1,1)$.

$$\boxed{\mathbf r=(3,1,1)+t(1,2,-3)},\qquad\frac{x-3}1=\frac{y-1}2=\frac{z-1}{-3}$$

## Example 4.48: Distance from $(2,-3,4)$ to $x+2y+2z=13$

$$d=\frac{|1(2)+2(-3)+2(4)-13|}{\sqrt{1+4+4}}=\frac{|-9|}3=\boxed3$$

## Example 9.20: $\mathbf r=\sin t\,\mathbf i+\cos t\,\mathbf j$
**Sketch**: $x^2+y^2=1$, so this is the unit circle. It starts at $(0,1)$ and goes **clockwise**.
- **(a)** $\dot{\mathbf r}=\cos t\,\mathbf i-\sin t\,\mathbf j$
- **(b)** $\ddot{\mathbf r}=-\sin t\,\mathbf i-\cos t\,\mathbf j=-\mathbf r$, pointing towards the centre (centripetal).
- **(c)** $|\dot{\mathbf r}|=1$: constant speed.
- **(d)** $|\mathbf r|=1$, so $\frac{\mathrm d}{\mathrm dt}|\mathbf r|=0$.

Note that (c) $\neq$ (d): $\big|\frac{\mathrm d\mathbf r}{\mathrm dt}\big|\neq\frac{\mathrm d|\mathbf r|}{\mathrm dt}$ in general.

## Example 9.21: Projectile motion
Integrate twice, using the initial conditions:
- $\dot{\mathbf r}=-gt\mathbf k+\mathbf V$
- $\mathbf r=\mathbf Vt-\tfrac12gt^2\mathbf k$

With $\mathbf V=(u,0,v)$: $x=ut$, $y=0$ and $z=vt-\tfrac12gt^2$. Eliminate $t=x/u$:

$$\boxed{z=\frac vu\,x-\frac{g}{2u^2}\,x^2}$$

The path is a parabola in the $xz$-plane ([[Projectile Motion]]).

---

# Part B: Assigned exercises

## Exercise 57: Volume of the parallelepiped

$$\begin{vmatrix}2&-3&4\\1&3&-1\\3&-1&2\end{vmatrix}=2(6-1)+3(2+3)+4(-1-9)=10+15-40=-15$$

The volume is the absolute value: $\boxed{15}$. The sign only records the handedness of the ordering.

## Exercise 58: Show the vectors are coplanar

$$\begin{vmatrix}3&2&-1\\5&-7&3\\11&-3&1\end{vmatrix}=3(-7+9)-2(5-33)-1(-15+77)=6+56-62=0$$

The triple product is zero, so the vectors are **coplanar** ✔. (In fact $(11,-3,1)=2(3,2,-1)+(5,-7,3)$.)

## Exercise 59: Find $\lambda$ for coplanarity

$$\begin{vmatrix}3&2&-1\\1&-1&3\\2&-3&\lambda\end{vmatrix}=3(-\lambda+9)-2(\lambda-6)-1(-3+2)=-5\lambda+40=0\ \Rightarrow\ \boxed{\lambda=8}$$

## Exercise 32 (Ch.9): $\mathbf r=(t,t^2,t^3)$

$$\dot{\mathbf r}=\boxed{(1,2t,3t^2)},\qquad\ddot{\mathbf r}=\boxed{(0,2,6t)}$$

## Exercise 34 (Ch.9, hard): Polar unit vectors
**Unit vectors.** $\hat{\mathbf r}$ points along OP at angle $\theta$: $\hat{\mathbf r}=\cos\theta\,\mathbf i+\sin\theta\,\mathbf j$. The vector $\hat{\boldsymbol\theta}$ is $\hat{\mathbf r}$ rotated by $+90°$: $\hat{\boldsymbol\theta}=-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j$ ✔.

**Their derivatives.** Use the chain rule with $\dot\theta=\omega$:

$$\frac{\mathrm d\hat{\mathbf r}}{\mathrm dt}=(-\sin\theta\,\mathbf i+\cos\theta\,\mathbf j)\,\omega=\omega\hat{\boldsymbol\theta},\qquad\frac{\mathrm d\hat{\boldsymbol\theta}}{\mathrm dt}=(-\cos\theta\,\mathbf i-\sin\theta\,\mathbf j)\,\omega=-\omega\hat{\mathbf r}$$

**Velocity**, from $\mathbf r=r\hat{\mathbf r}$ by the product rule:

$$\dot{\mathbf r}=\dot r\hat{\mathbf r}+r\frac{\mathrm d\hat{\mathbf r}}{\mathrm dt}=\boxed{\dot r\,\hat{\mathbf r}+r\omega\,\hat{\boldsymbol\theta}}$$

**Acceleration**, differentiating again:

$$\ddot{\mathbf r}=\ddot r\hat{\mathbf r}+\dot r\omega\hat{\boldsymbol\theta}+(\dot r\omega+r\dot\omega)\hat{\boldsymbol\theta}+r\omega(-\omega\hat{\mathbf r})=\boxed{(\ddot r-r\omega^2)\hat{\mathbf r}+(2\dot r\omega+r\dot\omega)\hat{\boldsymbol\theta}}$$

These terms are the centripetal acceleration ($-r\omega^2$) and the Coriolis term ($2\dot r\omega$). Both are needed in FEEG1002 ([[Normal and Tangential Coordinates]]) and in orbital mechanics.

## Exercise 35 (Ch.9): Constant magnitude implies $\mathbf a\perp\dot{\mathbf a}$
If $|\mathbf a|^2=\mathbf a\cdot\mathbf a=f^2+g^2=$ constant, differentiate:

$$2\mathbf a\cdot\dot{\mathbf a}=2(ff'+gg')=0$$

So $\mathbf a\cdot\dot{\mathbf a}=0$, and $\mathbf a\perp\dot{\mathbf a}$ (whenever both are non-zero) ✔. Example 9.20 is an instance: $|\mathbf r|=1$, and $\mathbf r\cdot\dot{\mathbf r}=\sin t\cos t-\cos t\sin t=0$. The velocity is tangent to the circle, so it is perpendicular to the radius.

## Booklet Exercise A: Path from the acceleration
Start from $\ddot{\mathbf r}=(\cos t,\sin t,0)$.
- **Integrate once**: $\dot{\mathbf r}=(\sin t,-\cos t,0)+\mathbf C$. At $t=0$, $(0,-1,0)+\mathbf C=(0,-1,1)$, so $\mathbf C=(0,0,1)$.
- So $\dot{\mathbf r}=(\sin t,-\cos t,1)$.
- **Integrate again**: $\mathbf r=(-\cos t,-\sin t,t)+\mathbf D$. At $t=0$, $(-1,0,0)+\mathbf D=(-1,0,0)$, so $\mathbf D=\mathbf0$.

$$\boxed{\mathbf r=(-\cos t,\,-\sin t,\,t)}$$

This is a **helix** on the cylinder $x^2+y^2=1$, rising one unit in $z$ per radian.

## Exercise 71: The line through $\mathbf a=(2,0,-1)$ and $\mathbf b=(1,2,3)$
- **Vector form**: $\mathbf r=(2,0,-1)+s(-1,2,4)$.
- **Cartesian form**: $\dfrac{x-2}{-1}=\dfrac y2=\dfrac{z+1}4$.

The line through $\mathbf c=(0,0,1)$ and $\mathbf d=(1,0,1)$ is $\mathbf r=(t,0,1)$, i.e. $y=0$ and $z=1$. On the first line, $y=0$ forces $s=0$, which gives $z=-1\neq1$. So the lines **do not intersect**.

## Exercise 66: A$(1,2,3)$ and B$(4,5,6)$
(a) Direction: $\vec{\mathrm{AB}}=(3,3,3)\propto\boxed{(1,1,1)}$.
(b) Vector form: $\boxed{\mathbf r=(1,2,3)+t(1,1,1)}$.
(c) Cartesian form: $\boxed{x-1=y-2=z-3}$.

## Exercise 68: Perpendicular lines
- $\mathbf d_1=(1,2,3)-(2,3,4)=(-1,-1,-1)$
- $\mathbf d_2=(2,3,-2)-(1,0,2)=(1,3,-4)$

$\mathbf d_1\cdot\mathbf d_2=-1-3+4=0$, so the lines are **perpendicular** ✔.

## Exercise 72: Shortest distance between the lines
- $\mathbf n=(2,1,-1)\times(3,2,1)=(1+2,\ -3-2,\ 4-3)=(3,-5,1)$
- $\mathbf a_2-\mathbf a_1=(-11,0,-2)$

$$d=\frac{|(-11,0,-2)\cdot(3,-5,1)|}{\sqrt{35}}=\frac{35}{\sqrt{35}}=\boxed{\sqrt{35}\approx5.916}$$

## Exercise 73: The plane through $(1,2,3)$, $(2,4,5)$, $(4,5,6)$
- $\mathbf u=(1,2,2)$ and $\mathbf v=(3,3,3)$.
- $\mathbf n=\mathbf u\times\mathbf v=(6-6,\ 6-3,\ 3-6)=(0,3,-3)\propto(0,1,-1)$.

**Vector form**: $\mathbf r=(1,2,3)+\lambda(1,2,2)+\mu(1,1,1)$, or equivalently $\mathbf r\cdot(0,1,-1)=-1$.
**Cartesian form**: $\boxed{y-z=-1}$ (i.e. $z=y+1$). Check: $4-5=5-6=2-3=-1$ ✔.

## Exercise 79: The plane through Q, perpendicular to PQ
**(a)** $\mathbf n=\vec{\mathrm{PQ}}=(1,-2,-4)-(3,1,2)=(-2,-3,-6)$. Then $\mathbf r\cdot\mathbf n=\mathbf b\cdot\mathbf n=-2+6+24=28$:

$$\boxed{2x+3y+6z=-28}$$

**(b)** $|\mathbf n|=7$, so the distance from $(-1,1,1)$ is

$$\frac{|2(-1)+3(1)+6(1)+28|}{7}=\frac{35}7=\boxed5$$

---

# Part C: Specimen Test 15

> [!note] Source
> Transcribed from the MATH1054 Module Booklet (the final page of Module 15), then solved and checked with SymPy, NumPy or SciPy.

## Q1: Triple products
**(i)** $\mathbf k\times\mathbf j=-\mathbf i$, so $\mathbf j\cdot(\mathbf k\times\mathbf j)=\boxed0$. Any triple product with a repeated vector is zero.

**(ii)** $\mathbf b\times\mathbf c=2\mathbf k\times\mathbf j=-2\mathbf i$, so $\mathbf a\cdot(\mathbf b\times\mathbf c)=(\mathbf i+\mathbf j)\cdot(-2\mathbf i)=\boxed{-2}$.

## Q2: A line and its intersections
**(i)** The direction is $\mathbf b-\mathbf a=-2\mathbf i+\mathbf j$:

$$\boxed{\mathbf r=(1,0,1)+\lambda(-2,1,0)}$$

**(ii)** The $yz$-plane is $x=0$: $1-2\lambda=0$, so $\lambda=\frac12$ and the point is $\boxed{(0,\tfrac12,1)}$.

**(iii)** Equate with $(3+s,-4+s,3-s)$:
- $z$: $1=3-s$, so $s=2$.
- $x$: $1-2\lambda=5$, so $\lambda=-2$.
- $y$: $\lambda=-4+s=-2$ ✔ (consistent).

The lines meet at $\boxed{(5,-2,1)}$.

## Q3: A plane from its normal and a point
$\mathbf n=(6,2,-3)$ and $\mathbf n\cdot(2,1,0)=14$, so $\mathbf r\cdot(6,2,-3)=14$, i.e. $6x+2y-3z=14$.

$|\mathbf n|=7$, so dividing by 7:

$$\boxed{\mathbf r\cdot\tfrac17(6,2,-3)=2}$$

The perpendicular distance from O to the plane is $\boxed{p=2}$.

## Q4: The plane through $(1,0,1)$, $(-3,1,12)$, $(2,-1,-4)$
$\mathbf n=(-4,1,11)\times(1,-1,-5)=(-5+11,\ 11-20,\ 4-1)=(6,-9,3)\propto(2,-3,1)$. Then:

$$\boxed{\mathbf r\cdot(2,-3,1)=3}\qquad(2x-3y+z=3)$$

The other two points check: $-6-3+12=3$ ✔ and $4+3-4=3$ ✔.

## Q5: $\mathbf r=(\cos t,\sin t,t)$ (a helix)

$$\dot{\mathbf r}=(-\sin t,\cos t,1),\qquad\ddot{\mathbf r}=(-\cos t,-\sin t,0),\qquad\dot{\mathbf r}\cdot\ddot{\mathbf r}=\sin t\cos t-\sin t\cos t=\boxed0$$

The dot product is zero because the speed $|\dot{\mathbf r}|=\sqrt2$ is constant.

## Q6: Velocity and position from the acceleration
Integrate $\ddot{\mathbf r}=(\sin2t,-\cos t,t^2)$ and fit $\dot{\mathbf r}(0)=(0,2,0)$:

$$\dot{\mathbf r}=\Big(\tfrac12-\tfrac12\cos2t,\ 2-\sin t,\ \tfrac13t^3\Big)=\boxed{\big(\sin^2t,\ 2-\sin t,\ \tfrac13t^3\big)}$$

Integrate again and fit $\mathbf r(0)=(0,0,1)$:

$$\boxed{\mathbf r=\Big(\tfrac t2-\tfrac14\sin2t,\ 2t+\cos t-1,\ \tfrac1{12}t^4+1\Big)}$$

## Q7

$$\frac{\mathrm d}{\mathrm dt}(\mathbf r\times\dot{\mathbf r})=\underbrace{\dot{\mathbf r}\times\dot{\mathbf r}}_{=\mathbf0}+\mathbf r\times\ddot{\mathbf r}=\frac{\mathrm d}{\mathrm dt}(t^2\mathbf i)\ \Rightarrow\ \boxed{\mathbf r\times\ddot{\mathbf r}=2t\,\mathbf i}$$

## Sources
- Transcribed problem statements: `tmp/md/module_15_vectors_ii.md`
- James, *Modern Engineering Mathematics* (6th ed.) §4.3.3–4.4, §9.5; MATH1054 Module Booklet, Module 15

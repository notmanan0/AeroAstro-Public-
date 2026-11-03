---
title: "MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 15
tags:
  - math2048
  - vector-calculus
  - gradient
aliases: ["MATH2048 Lecture 21", "MATH2048 Lecture 23", "Directional derivative", "Grad"]
date: 2026-10-30
status: lectured
coverage: "Lecture 21 (18 Nov 2024), first part: scalars and vectors as coordinate-free objects, why Cartesian bases are convenient, dot and cross products, scalar and vector fields, parametric curves and their tangent vectors. Lecture 23 (20 Nov 2024): local versus global, the directional derivative, the gradient, its link to level curves and to the directional derivative, and its linearity and product rule. Both Ian Hawke. Line integrals from Lecture 21 are in VC3."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 PDE5 - Laplace's Equation]]"]
next_topics: ["[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]", "[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
key_concepts: ["[[Gradient and Directional Derivative]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 21.txt", "02 - Sources/Lectures/MATH2048 Lecture 23.txt", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.1)"]
---

# MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives

> [!abstract] Summary
> A scalar field assigns a number to every point and a vector field a vector; both mean the same thing whatever coordinates describe them. The gradient $\nabla f=f_x\,\mathbf i+f_y\,\mathbf j+f_z\,\mathbf k$ turns a scalar field into a vector field that is normal to the level surfaces of $f$ and points the way $f$ increases fastest. The rate of change of $f$ in the direction of a unit vector $\hat{\mathbf n}$ is the directional derivative $\frac{\partial f}{\partial n}=\hat{\mathbf n}\cdot\nabla f$, so it is at most $|\nabla f|$ and is zero along a level surface.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for a gradient, a rate of change in a direction, a maximum rate of change, or a normal to a surface (2023/24 B1(a); PS8 Q1–Q4).
> - **Assumptions:** Cartesian coordinates; $f$ differentiable at the point; the direction vector made a unit vector.
> - **Method:** 1. Differentiate $f$ partially in $x$, $y$ and $z$. 2. Evaluate $\nabla f$ at the point. 3. For a direction $\mathbf v$, divide by $|\mathbf v|$ and dot with $\nabla f$. 4. The maximum rate is $|\nabla f|$, in the direction of $\nabla f$. 5. A normal to the surface $f=c$ is $\nabla f$.
> - **Common mistakes:** dotting with $\mathbf v$ instead of $\hat{\mathbf v}$; forgetting a term when a variable appears inside a composite function such as $\sin(yz)$.
> - **Practise:** [[#6. The 2023-24 exam, question B1(a)]] · [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus|PS8 Q1–Q4]]

Solving a PDE gives a field, a function of several variables, and that is rarely what is wanted (L21, ll. 1–22). From the velocity field around a wing you want the lift, and from a shock the impact on a surface. Getting those means integrating fields along curves and over surfaces and volumes, and describing how fields change from point to point: vector calculus. The last block of the module, given to all but the civil engineers, builds that toolkit.

The organising idea comes from Lecture 23 (ll. 1–45). Integrals describe global properties, averages over a region; derivatives describe local ones, rates of change at a point. In one variable both come with rules that make them useful, linearity, the product and chain rules, integration by parts. The derivatives of vector calculus are chosen so that those rules still hold. This note covers the first of them, the gradient.

---

## 1. Scalars, vectors and coordinates (L21)

A scalar at a point is a single number, and physically it is one that doesn't change with the coordinate system (ll. 23–32): the temperature at a point is the same whether the point is located in metres from a corner of the room or by latitude and longitude. A vector, to a mathematician, is a list of numbers, but physically it is an object with a meaning that doesn't depend on coordinates, even though its components do (ll. 33–52). A seat in the lecture theatre can be located as "four rows back and three in" or by three distances from a corner, or by an angle and distance from the lecturer; the place is the same, the numbers differ. Lengths don't change between coordinate systems; components do. Handwritten vectors are underlined, the slides use arrows, and exam papers use bold (ll. 53–57).

Cartesian coordinates use the basis vectors $\mathbf i$, $\mathbf j$, $\mathbf k$, so $\mathbf a=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$. Any three independent vectors would do as a basis, but the Cartesian ones have three conveniences (ll. 58–107). They have length 1, which any basis can be rescaled to have. They are orthogonal, so each component is found independently by a dot product with one basis vector; in a skewed basis, changing one component changes the others needed to reach the same point. Most importantly, they are the same at every point, so their derivatives are zero. Cylindrical and spherical bases are orthonormal too, but their directions change from point to point, which makes differentiating them unpleasant.

The length of $\mathbf a$ is $|\mathbf a|=\sqrt{a_1^2+a_2^2+a_3^2}$, and $\mathbf a/|\mathbf a|$ is the unit vector in its direction (ll. 108–111). Addition and scalar multiplication act component by component. The **dot product**

$$
\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta=a_1b_1+a_2b_2+a_3b_3
$$

is the length of one vector times the projection of the other onto it, so it vanishes for orthogonal vectors and $|\mathbf a|=\sqrt{\mathbf a\cdot\mathbf a}$ (ll. 121–136). The **cross product** builds a vector orthogonal to two others, which is how to find a normal to a surface such as a wing (ll. 137–168):

$$
\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}=(a_2b_3-a_3b_2)\,\mathbf i-(a_1b_3-a_3b_1)\,\mathbf j+(a_1b_2-a_2b_1)\,\mathbf k ,
$$

with magnitude $|\mathbf a||\mathbf b|\sin\theta$ and direction given by the right-hand rule. Swapping the order flips the sign, $\mathbf b\times\mathbf a=-\mathbf a\times\mathbf b$, which matters when deciding whether a normal points into or out of a body. Two vectors with zero cross product are parallel.

## 2. Fields (L21)

Solutions of PDEs give scalars and vectors everywhere, not at one point, and these are fields (ll. 170–186). A **scalar field** $\phi(x,y,z)$, or $\phi(x,y,z,t)$, takes a point and returns a number: temperature, pressure, density. Its value at a given physical point doesn't change with the coordinates, provided the inputs are corrected so they describe the same point. A **vector field** $\mathbf F(x,y,z)=F_1\,\mathbf i+F_2\,\mathbf j+F_3\,\mathbf k$ returns a vector at every point, so each component is itself a scalar function of position. Its meaning is fixed but its components change with the coordinates; a fluid velocity has different components in a frame moving with the flow (Lagrangian) and in a fixed one (Eulerian).

## 3. Parametric curves and tangent vectors (L21)

A curve is intrinsically one-dimensional, so it is described with one parameter rather than an equation in $x$, $y$, $z$, which may not exist in a usable form for a curve that loops or coils (ll. 187–238). Think of a particle moving along it: at "time" $t$ it is at

$$
\mathbf r(t)=x(t)\,\mathbf i+y(t)\,\mathbf j+z(t)\,\mathbf k,\qquad a\leq t\leq b ,
$$

starting at $A=\mathbf r(a)$ and ending at $B=\mathbf r(b)$. The convention is $a=0$, $b=1$, but any interval can be rescaled.

The parameter has nothing to do with the physics (ll. 239–275). The segment from $x=0$ to $x=1$ along the $x$-axis can be written $\mathbf r=t\,\mathbf i$ or $\mathbf r=s^2\,\mathbf i$, both for parameters running from 0 to 1. Both trace the same points, but at different speeds: $t=\frac13,\frac23$ reach $x=\frac13,\frac23$, while $s=\frac13,\frac23$ reach only $x=\frac19,\frac49$. Changing the parametrisation changes how fast you move along the curve, not the curve itself. In practice, choose whichever makes the curve simplest to write down.

Differentiating with respect to the parameter gives a tangent vector (ll. 278–307). The chord from $\mathbf r(t)$ to $\mathbf r(t+\Delta t)$ is $\mathbf r(t+\Delta t)-\mathbf r(t)$, and dividing by $\Delta t$ and letting $\Delta t\to0$ acts component by component, because only vector subtraction and scalar multiplication are involved:

$$
\frac{d\mathbf r}{dt}=\lim_{\Delta t\to0}\frac{\mathbf r(t+\Delta t)-\mathbf r(t)}{\Delta t}=\frac{dx}{dt}\,\mathbf i+\frac{dy}{dt}\,\mathbf j+\frac{dz}{dt}\,\mathbf k .
$$

As $\Delta t\to0$ the chord lines up with the curve, so $\frac{d\mathbf r}{dt}$ is tangent to it. Its length depends on the parametrisation but its direction does not. This tangent vector is what turns a work integral along a curve into an ordinary integral in [[MATH2048 VC3 - Line Integrals and Conservative Fields|VC3]].

## 4. The directional derivative (L23)

The simplest way to differentiate a scalar field is to restrict it to one direction, which makes it a function of one variable again (ll. 77–112). Move a distance $h$ from the point $\mathbf x_0$ in the direction of a unit vector $\hat{\mathbf n}$ and form the usual difference quotient:

$$
\frac{\partial f}{\partial n}\bigg|_{\mathbf x_0}=\lim_{h\to0}\frac{f(\mathbf x_0+h\hat{\mathbf n})-f(\mathbf x_0)}{h}.
$$

Choosing $\hat{\mathbf n}=\mathbf i$ moves only in $x$, holding $y$ and $z$ fixed, so the directional derivative is $\frac{\partial f}{\partial x}$; likewise $\mathbf j$ and $\mathbf k$ give $\frac{\partial f}{\partial y}$ and $\frac{\partial f}{\partial z}$ (ll. 113–125). Partial derivatives are directional derivatives along the axes.

The direction is a unit vector because only the direction should matter (ll. 125–142). In the limit definition itself a longer vector just rescales the step, but in the formula with the gradient below its length would multiply the answer, so normalising removes the ambiguity. The definition is made at one point $\mathbf x_0$, but it can be made at every point where $f$ is smooth enough, so the directional derivative of a scalar field is another scalar field (ll. 146–152).

## 5. The gradient (L23)

The **gradient** turns a scalar field into a vector field (ll. 153–171):

$$
\nabla f=\frac{\partial f}{\partial x}\,\mathbf i+\frac{\partial f}{\partial y}\,\mathbf j+\frac{\partial f}{\partial z}\,\mathbf k .
$$

It is often written as an operator, $\nabla=\mathbf i\frac{\partial}{\partial x}+\mathbf j\frac{\partial}{\partial y}+\mathbf k\frac{\partial}{\partial z}$, the symbol being called nabla or del. That does not mean the derivatives act on the basis vectors; each partial derivative is a component, acting on whatever is written to its right.

### The gradient is normal to level curves

Take $f=x^2+y^2$ in the plane (ll. 172–222). Its level curves, where $f$ is constant, are circles: $f=1$ has radius 1 and $f=16$ radius 4. At the bottom of the larger circle, $(0,-4)$, moving in $x$ stays on the circle to first order, and indeed $f_x=2x=0$ there, while $f_y=2y=-8$, so $\nabla f=-8\,\mathbf j$ points straight down, away from the centre. At a point lower right, $f_x>0$ and $f_y<0$, so $\nabla f$ points down and to the right; on the positive $x$-axis it points along $+\mathbf i$. In each case it is perpendicular to the circle and points outwards, towards larger $f$.

If $f$ is the height of a hill, its level curves are contours, and $\nabla f$ points straight uphill, perpendicular to the contour, the direction in which the height increases fastest. The figure shows this for the slightly less symmetric $x^2+2y^2$.

![[m2048_vc_gradient_level_curves.png|560]]

### Directional derivative from the gradient

The lecturer motivated the link with the picture: $\nabla f$ is the change in the steepest direction, so the change in direction $\hat{\mathbf n}$ should be its projection, $\hat{\mathbf n}\cdot\nabla f$ (ll. 223–255). The chain rule proves it. Write $\hat{\mathbf n}=(n_1,n_2,n_3)$ and let $g(h)=f(\mathbf x_0+h\hat{\mathbf n})$, so the directional derivative is $g'(0)$. Along the line, $x=x_0+hn_1$, $y=y_0+hn_2$, $z=z_0+hn_3$, so

$$
g'(h)=\frac{\partial f}{\partial x}\frac{dx}{dh}+\frac{\partial f}{\partial y}\frac{dy}{dh}+\frac{\partial f}{\partial z}\frac{dz}{dh}=n_1\frac{\partial f}{\partial x}+n_2\frac{\partial f}{\partial y}+n_3\frac{\partial f}{\partial z},
$$

and setting $h=0$,

$$
\frac{\partial f}{\partial n}=\hat{\mathbf n}\cdot\nabla f .
$$

This is where the unit vector matters: with $\mathbf n=\mathbf i$ it must return $\frac{\partial f}{\partial x}$, not a multiple of it (ll. 250–255).

Two results follow (ll. 262–277). Since $\hat{\mathbf n}\cdot\nabla f=|\nabla f|\cos\theta$ and $|\cos\theta|\leq1$,

$$
\Big|\frac{\partial f}{\partial n}\Big|\leq|\nabla f| ,
$$

with the largest increase, $|\nabla f|$, when $\hat{\mathbf n}$ points along $\nabla f$, and the largest decrease along $-\nabla f$. And if $\hat{\mathbf n}$ is tangent to a level surface, $f$ doesn't change in that direction, so $\hat{\mathbf n}\cdot\nabla f=0$ for every tangent direction: $\nabla f$ is normal to the level surface, which is what the circle example showed. A normal to the surface $f(x,y,z)=c$ at a point is therefore $\nabla f$ evaluated there.

### Linearity and the product rule

These are the properties the gradient is built to keep, and both are checked component by component (ll. 279–338). For constants $\alpha$, $\beta$, the $x$-component of $\nabla(\alpha f+\beta g)$ is

$$
\frac{\partial}{\partial x}(\alpha f+\beta g)=\alpha\frac{\partial f}{\partial x}+\beta\frac{\partial g}{\partial x},
$$

by linearity of ordinary partial derivatives, and the other components are the same with $y$ and $z$. Regrouping the $\alpha$ terms and the $\beta$ terms across components,

$$
\nabla(\alpha f+\beta g)=\alpha\nabla f+\beta\nabla g .
$$

For the product, the $x$-component of $\nabla(fg)$ is, by the ordinary product rule,

$$
\frac{\partial}{\partial x}(fg)=g\frac{\partial f}{\partial x}+f\frac{\partial g}{\partial x},
$$

and gathering the $g$ terms and the $f$ terms across components,

$$
\nabla(fg)=g\nabla f+f\nabla g .
$$

> [!tip] Radial fields
> For $r=\sqrt{x^2+y^2+z^2}$, $\frac{\partial r}{\partial x}=\frac xr$, and similarly for $y$ and $z$, so $\nabla r=\frac{\mathbf r}r=\hat{\mathbf r}$. By the chain rule, any function of $r$ alone has $\nabla f(r)=f'(r)\,\hat{\mathbf r}$: it points radially, as the circle example suggested.

## 6. The 2023-24 exam, question B1(a)

For $\phi=\sin(yz)+x^2y^2+z$ at $P(1,2,0)$:

$$
\nabla\phi=2xy^2\,\mathbf i+\big(z\cos(yz)+2x^2y\big)\,\mathbf j+\big(y\cos(yz)+1\big)\,\mathbf k .
$$

At $P$, $\cos0=1$, so $\nabla\phi=8\,\mathbf i+4\,\mathbf j+3\,\mathbf k$. The maximum rate of change is

$$
|\nabla\phi|=\sqrt{64+16+9}=\sqrt{89}\approx9.43 ,
$$

in the direction $(8,4,3)/\sqrt{89}$. Part (iii), the Laplacian, is in [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities|VC2]].

> [!check] PS8 Q2(b)
> $f=2x+3y^2+2xyz$ at $(1,2,1)$ in the direction $(2,2,1)$: $\nabla f=(2+2yz,\,6y+2xz,\,2xy)=(6,14,4)$, the direction has length 3, and $\frac{\partial f}{\partial n}=\frac{12+28+4}3=\frac{44}3$.

## Transcript slips

> [!warning] Lectures 21 and 23
> | Where | Transcript says | Correct |
> |---|---|---|
> | L21, ll. 197–198 | lift is "the total integral of the gradient of the pressure across that surface" | lift comes from integrating the pressure (times the normal) over the surface, not its gradient |
> | L21, l. 204 | "the surface integral around the curve of F dot dr ... that's work done" | a line integral; it is work, not lift |
> | L21, l. 235 | "zero less than or equal to t less than or equal to y" | $0\leq t\leq1$ |
> | L23, l. 170 | "DF DX in the X direction" for the third component | $\frac{\partial f}{\partial z}\,\mathbf k$ |
> | L23, l. 221 | "a level surface is pointing either in the direction of maximum increase or maximum decrease" | the gradient points that way; the level surface is perpendicular to it |
> | L23, ll. 304–306 | regrouping written wrongly, "Complete nonsense there" | $\alpha(f_x\mathbf i+f_y\mathbf j+\dots)+\beta(g_x\mathbf i+g_y\mathbf j+\dots)$ |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE5 - Laplace's Equation]] · Next: [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] · Line integrals: [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- Concepts: [[Gradient and Directional Derivative]] · [[Divergence, Curl and the Laplacian]]

## Sources

- Lecture 21 (18 Nov 2024) and Lecture 23 (20 Nov 2024) recordings, Ian Hawke: `MATH2048 Lecture 21.txt`, `MATH2048 Lecture 23.txt`
- Vector calculus slides; lecture notes §8.1
- Problem Sheet 8; 2023/24 exam question B1(a)

## Self-study tasks

Lecture 23 ended with "get used to calculating gradients of stuff" (l. 344); nothing more specific was set.

### Core

- [ ] PS8 Q1: gradients of $e^y\sin x$ and $x^3y^2\ln z$. Answers: $e^y\cos x\,\mathbf i+e^y\sin x\,\mathbf j$; $3x^2y^2\ln z\,\mathbf i+2x^3y\ln z\,\mathbf j+\frac{x^3y^2}z\mathbf k$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] PS8 Q2–Q3: directional derivatives and a maximum rate of change. Answers: $0$; $\frac{44}3$; $2\sqrt5$ along $(0,2,1)/\sqrt5$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] 2023/24 B1(a)(i)–(ii). → [[#6. The 2023-24 exam, question B1(a)]]

### Further practice

- [ ] PS8 Q4: the angle between the normals to $x^2+y^2+z^2=9$ and $z=x^2+y^2-3$ at $(2,-1,2)$. Answer: $\cos\theta=\frac{8\sqrt{21}}{63}$, $\theta\approx54.4^\circ$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] Prove $\frac{\partial f}{\partial n}=\hat{\mathbf n}\cdot\nabla f$ with the chain rule, and show $\nabla f(r)=f'(r)\hat{\mathbf r}$ (suggested, not lecturer-set). → [[#Directional derivative from the gradient]]

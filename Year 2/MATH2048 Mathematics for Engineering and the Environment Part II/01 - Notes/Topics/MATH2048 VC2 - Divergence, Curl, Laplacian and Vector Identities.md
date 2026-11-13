---
title: "MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 16
tags:
  - math2048
  - vector-calculus
  - divergence
  - curl
aliases: ["MATH2048 Lecture 24", "MATH2048 Lecture 25", "div", "curl", "Laplacian"]
date: 2026-10-30
status: lectured
coverage: "Lecture 24 (25 Nov 2024): divergence and curl built from the gradient by linearity and a product rule, their Cartesian formulas, a solenoidal example, divergence as expansion via the continuity equation, curl and vorticity. Lecture 25 (26 Nov 2024): the Laplacian of scalar and vector fields, where it appears, the eight vector identities with proofs of curl grad = 0 and div curl = 0, and uses of identities 2, 6 and 8 in fluid dynamics. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]"]
next_topics: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
key_concepts: ["[[Divergence, Curl and the Laplacian]]", "[[Gradient and Directional Derivative]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 24.txt", "02 - Sources/Lectures/MATH2048 Lecture 25.txt", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture24_vector04.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture25_vector05.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.1.8–8.1.11)"]
---

# MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities

> [!abstract] Summary
> A vector field can be differentiated in two ways, by analogy with the dot and cross products. The divergence $\nabla\cdot\mathbf F=\partial_xF_1+\partial_yF_2+\partial_zF_3$ is a scalar that measures local expansion (a source) or contraction (a sink); the curl $\nabla\times\mathbf F$, a determinant with $\mathbf i,\mathbf j,\mathbf k$ on top, is a vector that measures local rotation, the vorticity of a flow. The Laplacian $\nabla^2=\nabla\cdot\nabla$ is the sum of second derivatives and is what appears in the wave, heat and Navier–Stokes equations. Two identities, $\nabla\times\nabla f=\mathbf 0$ and $\nabla\cdot(\nabla\times\mathbf F)=0$, follow because mixed partial derivatives commute.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for a divergence, curl or Laplacian at a point, or to prove or use a vector identity (2023/24 B1(a)(iii); 2024/25 B1(a); PS9).
> - **Assumptions:** Cartesian coordinates; fields twice continuously differentiable for the identities.
> - **Method:** 1. Write out $F_1$, $F_2$, $F_3$. 2. Divergence: add $\partial_xF_1$, $\partial_yF_2$, $\partial_zF_3$. 3. Curl: expand the determinant by minors, derivative row acting on component row, with a minus on the $\mathbf j$ term. 4. Laplacian: add the three unmixed second derivatives. 5. Evaluate at the point last.
> - **Common mistakes:** dropping the minus sign on the $\mathbf j$ component of the curl; trying to take the gradient of a vector field, which this course doesn't define (2024/25 B1(a)(i)).
> - **Practise:** [[#The curl, by the same route]] · [[#4. Past exam questions]]

The gradient of [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives|VC1]] differentiates a scalar field. Vector fields are the more interesting case, and just as two vectors can be multiplied with a dot or a cross, a vector field can be differentiated in two ways. The divergence takes a vector field to a scalar field, like a dot product. The curl takes a vector field to a vector field, like a cross product.

Both are built from the gradient by requiring the two properties wanted of every derivative: linearity, and a product rule. In Cartesian coordinates the basis vectors are constant, so their derivatives vanish, and that alone fixes the formulas.

---

## 1. Divergence

### Building it from the gradient

Two properties are required. The first is linearity. The second is a product rule for a scalar field $f$ times a constant vector $\mathbf c$: the derivative of $f\mathbf c$ should be "derivative of $f$ times $\mathbf c$" plus "$f$ times derivative of $\mathbf c$", and the derivative of a constant is zero. Choosing the dot product for "times" gives the divergence:

$$
\nabla\cdot(f\mathbf c)=(\nabla f)\cdot\mathbf c .
$$

Now expand a general field in its components. By linearity,

$$
\nabla\cdot\mathbf F=\nabla\cdot(F_1\mathbf i)+\nabla\cdot(F_2\mathbf j)+\nabla\cdot(F_3\mathbf k).
$$

Each $F_n$ is a scalar field and $\mathbf i,\mathbf j,\mathbf k$ are constant, so by the product rule,

$$
\nabla\cdot\mathbf F=(\nabla F_1)\cdot\mathbf i+(\nabla F_2)\cdot\mathbf j+(\nabla F_3)\cdot\mathbf k .
$$

$(\nabla F_1)\cdot\mathbf i$ picks out the $\mathbf i$ component of $\nabla F_1$, which is $\partial_xF_1$, because $\mathbf i\cdot\mathbf i=1$ and $\mathbf j\cdot\mathbf i=\mathbf k\cdot\mathbf i=0$; likewise for the others. So

$$
\nabla\cdot\mathbf F=\frac{\partial F_1}{\partial x}+\frac{\partial F_2}{\partial y}+\frac{\partial F_3}{\partial z},
$$

the $x$-derivative of the $x$-component plus the same for $y$ and $z$, a scalar field.

### Zero divergence doesn't mean constant

An example is $\mathbf F=y^2z\,\mathbf i+xz\,\mathbf j-y^2\,\mathbf k$. It is certainly not constant: it is $\mathbf 0$ at the origin and $(1,1,-1)$ at $(1,1,1)$. But each component is independent of its own variable, so

$$
\nabla\cdot\mathbf F=0+0+0=0 .
$$

A field with zero divergence everywhere is called **solenoidal**, a name from electromagnetism.

### What divergence measures

In a fluid, a small element containing a fixed number of particles moves with the velocity field $\mathbf v$. If the arrows converge on a point, the velocity decreases through it along each axis, the divergence is negative, and the point is a sink; if they spread out from it, the divergence is positive and the point is a source. The continuity equation makes this precise:

$$
\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf v)=0 .
$$

Expand $\nabla\cdot(\rho\mathbf v)=\mathbf v\cdot\nabla\rho+\rho\nabla\cdot\mathbf v$ by the product rule (identity 4 below) and move the first part to the left:

$$
\frac{D\rho}{Dt}\equiv\frac{\partial\rho}{\partial t}+\mathbf v\cdot\nabla\rho=-\rho\,\nabla\cdot\mathbf v .
$$

$\frac{D}{Dt}$ is the material derivative, the rate of change seen moving with the flow. A positive divergence makes the density of the element fall, which with fixed mass means its volume is growing: the flow is expanding. Negative divergence means it is being compressed. An incompressible flow has $\nabla\cdot\mathbf v=0$.

## 2. Curl

### The curl, by the same route

Repeat the construction with the cross product in the product rule, $\nabla\times(f\mathbf c)=(\nabla f)\times\mathbf c$. Linearity and the constant basis give

$$
\nabla\times\mathbf F=(\nabla F_1)\times\mathbf i+(\nabla F_2)\times\mathbf j+(\nabla F_3)\times\mathbf k .
$$

Now $\mathbf i\times\mathbf i=\mathbf 0$, $\mathbf j\times\mathbf i=-\mathbf k$ and $\mathbf k\times\mathbf i=\mathbf j$, so

$$
(\nabla F_1)\times\mathbf i=\big(\partial_xF_1\,\mathbf i+\partial_yF_1\,\mathbf j+\partial_zF_1\,\mathbf k\big)\times\mathbf i=-\partial_yF_1\,\mathbf k+\partial_zF_1\,\mathbf j .
$$

The other two go the same way, using $\mathbf i\times\mathbf j=\mathbf k$, $\mathbf k\times\mathbf j=-\mathbf i$, $\mathbf i\times\mathbf k=-\mathbf j$ and $\mathbf j\times\mathbf k=\mathbf i$:

$$
(\nabla F_2)\times\mathbf j=\partial_xF_2\,\mathbf k-\partial_zF_2\,\mathbf i,\qquad(\nabla F_3)\times\mathbf k=-\partial_xF_3\,\mathbf j+\partial_yF_3\,\mathbf i .
$$

Each of the three terms gives two pieces, none along its own basis vector, six in all. Collecting the $\mathbf i$ pieces ($\partial_yF_3-\partial_zF_2$), the $\mathbf j$ pieces ($\partial_zF_1-\partial_xF_3$) and the $\mathbf k$ pieces ($\partial_xF_2-\partial_yF_1$), they are

$$
\nabla\times\mathbf F=\Big(\frac{\partial F_3}{\partial y}-\frac{\partial F_2}{\partial z}\Big)\mathbf i+\Big(\frac{\partial F_1}{\partial z}-\frac{\partial F_3}{\partial x}\Big)\mathbf j+\Big(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}\Big)\mathbf k ,
$$

which there is no need to memorise, because it is the determinant

$$
\nabla\times\mathbf F=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\partial_x&\partial_y&\partial_z\\F_1&F_2&F_3\end{vmatrix}.
$$

Expand it by minors along the top row, with the alternating signs $+,-,+$. In each $2\times2$ minor the derivatives act on the components, so the order matters: the top-left derivative acts on the bottom-right component, minus the top-right derivative acting on the bottom-left.

### Worked example

For $\mathbf F=xy^2\,\mathbf i+e^z\,\mathbf j+ye^z\sin x\,\mathbf k$:

$$
\nabla\times\mathbf F=\mathbf i\Big[\partial_y(ye^z\sin x)-\partial_z(e^z)\Big]-\mathbf j\Big[\partial_x(ye^z\sin x)-\partial_z(xy^2)\Big]+\mathbf k\Big[\partial_x(e^z)-\partial_y(xy^2)\Big].
$$

Term by term: $e^z\sin x-e^z$, then $ye^z\cos x-0$, then $0-2xy$. So

$$
\nabla\times\mathbf F=e^z(\sin x-1)\,\mathbf i-ye^z\cos x\,\mathbf j-2xy\,\mathbf k .
$$

A curl needs six derivatives and gives a vector; a divergence needs three and gives a scalar. At the point $(\frac\pi2,1,0)$, for instance, $e^0=1$, $\sin\frac\pi2=1$ and $\cos\frac\pi2=0$, so $\nabla\times\mathbf F=0\,\mathbf i-0\,\mathbf j-\pi\,\mathbf k=-\pi\,\mathbf k$.

### The position vector (PS9 Q1(ii) and Q3(ii))

For $\mathbf r=x\,\mathbf i+y\,\mathbf j+z\,\mathbf k$, each component is its own coordinate, so

$$
\nabla\cdot\mathbf r=\frac{\partial x}{\partial x}+\frac{\partial y}{\partial y}+\frac{\partial z}{\partial z}=3,
$$

a uniform expansion, and every curl component is a derivative of one coordinate with respect to a different one:

$$
\nabla\times\mathbf r=\Big(\frac{\partial z}{\partial y}-\frac{\partial y}{\partial z}\Big)\mathbf i+\Big(\frac{\partial x}{\partial z}-\frac{\partial z}{\partial x}\Big)\mathbf j+\Big(\frac{\partial y}{\partial x}-\frac{\partial x}{\partial y}\Big)\mathbf k=\mathbf 0 .
$$

That is the left panel of the figure below in three dimensions: spreading without spin. The rigid rotation $\mathbf v=-\Omega y\,\mathbf i+\Omega x\,\mathbf j$ is the opposite case: $\nabla\cdot\mathbf v=0$, and the only non-zero curl component is $\partial_x(\Omega x)-\partial_y(-\Omega y)=2\Omega$, so $\nabla\times\mathbf v=2\Omega\,\mathbf k$. The vorticity of a rigid rotation is twice its angular velocity.

### What curl measures

The curl measures local rotation. The curl of a fluid velocity is the **vorticity**, $\boldsymbol\omega=\nabla\times\mathbf v$. The motion of a small fluid element splits into expansion (the divergence), shear (deformation of a square into a parallelogram, which is what viscosity resists) and spin, which is what vorticity measures. The figure shows the three cases: a radial field spreads but doesn't spin, a rigid rotation spins with zero divergence, and a shear flow has zero divergence but non-zero curl, so a small paddle wheel placed in it turns even though every streamline is straight.

![[m2048_vc_div_curl_fields.png|900]]

Taking the curl of the incompressible Navier–Stokes equation with constant density,

$$
\frac{D\mathbf v}{Dt}=-\frac{\nabla p}\rho+\nabla\Phi+\nu\nabla^2\mathbf v ,
$$

kills the pressure and potential body-force terms, since each is a gradient and $\nabla\times\nabla f=\mathbf 0$ (identity 2 below). What is left says that, following the flow, vorticity changes only through viscosity. That is why vorticity is generated where viscosity matters, in boundary layers and at trailing edges, where vortices are shed and drag results.

## 3. The Laplacian and the vector identities

### The Laplacian

The Laplacian is a second derivative, the divergence of the gradient. With $\nabla f=(f_x,f_y,f_z)$, taking the $x$-derivative of the $x$-component and so on,

$$
\nabla^2f=\nabla\cdot\nabla f=\frac{\partial^2f}{\partial x^2}+\frac{\partial^2f}{\partial y^2}+\frac{\partial^2f}{\partial z^2}.
$$

It has already appeared throughout [[MATH2048 PDE5 - Laplace's Equation|Block 4]]: the wave and heat equations in several dimensions are $u_{tt}=c^2\nabla^2u$ and $u_t=\kappa^2\nabla^2u$, their static limit is Laplace's equation $\nabla^2u=0$, and with a source it is Poisson's equation, used for gravitational and electrostatic potentials. In Navier–Stokes, $\nu\nabla^2\mathbf v$ is the viscous term. Taking the divergence of incompressible Navier–Stokes kills the time-derivative and viscous terms, because $\nabla\cdot\mathbf v=0$, and leaves $\nabla^2p=0$ for the pressure when the density is constant; numerical codes use this, as a pressure projection, to keep the flow incompressible.

For $\phi=e^xy^3\sin z$, the gradient is $e^xy^3\sin z\,\mathbf i+3e^xy^2\sin z\,\mathbf j+e^xy^3\cos z\,\mathbf k$, and its divergence is

$$
\nabla^2\phi=e^xy^3\sin z+6e^xy\sin z-e^xy^3\sin z=6e^xy\sin z .
$$

In Cartesian coordinates the intermediate gradient can be skipped by differentiating twice directly, which leaves fewer chances to slip.

The Laplacian of a vector field is defined component by component:

$$
\nabla^2\mathbf F=\nabla^2F_1\,\mathbf i+\nabla^2F_2\,\mathbf j+\nabla^2F_3\,\mathbf k ,
$$

nine second derivatives in all. In non-Cartesian coordinates it is messier, another reason to work in Cartesians when possible.

### The identities

Eight identities hold, for scalar fields $f$, $g$ and vector fields $\mathbf F$, $\mathbf G$. Most are on the formula sheet and needn't be memorised.

| # | Identity |
|---|---|
| 1 | $\nabla(fg)=f\nabla g+g\nabla f$ |
| 2 | $\nabla\times(\nabla f)=\mathbf 0$ |
| 3 | $\nabla\times(g\mathbf F)=g\,\nabla\times\mathbf F+\nabla g\times\mathbf F$ |
| 4 | $\nabla\cdot(g\mathbf F)=\nabla g\cdot\mathbf F+g\,\nabla\cdot\mathbf F$ |
| 5 | $\nabla\cdot(\nabla\times\mathbf F)=0$ |
| 6 | $\nabla\times(\nabla\times\mathbf F)=\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$ |
| 7 | $\nabla(\mathbf F\cdot\mathbf G)=\mathbf F\times(\nabla\times\mathbf G)+\mathbf G\times(\nabla\times\mathbf F)+(\mathbf F\cdot\nabla)\mathbf G+(\mathbf G\cdot\nabla)\mathbf F$ |
| 8 | $\nabla\times(\mathbf F\times\mathbf G)=\mathbf F(\nabla\cdot\mathbf G)-\mathbf G(\nabla\cdot\mathbf F)+(\mathbf G\cdot\nabla)\mathbf F-(\mathbf F\cdot\nabla)\mathbf G$ |

Here $(\mathbf F\cdot\nabla)=F_1\partial_x+F_2\partial_y+F_3\partial_z$ is a scalar operator that acts on each component of whatever follows. All of them are coordinate-free statements, so proving them in Cartesian coordinates proves them everywhere.

### Proof that the curl of a gradient vanishes

Put the components of $\nabla f$ into the third row of the curl determinant:

$$
\nabla\times\nabla f=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\\partial_x&\partial_y&\partial_z\\f_x&f_y&f_z\end{vmatrix}=\big(\partial_yf_z-\partial_zf_y\big)\,\mathbf i-\big(\partial_xf_z-\partial_zf_x\big)\,\mathbf j+\big(\partial_xf_y-\partial_yf_x\big)\,\mathbf k .
$$

For a twice continuously differentiable $f$, mixed partial derivatives commute, $\frac{\partial^2f}{\partial y\,\partial z}=\frac{\partial^2f}{\partial z\,\partial y}$, so each bracket is zero and $\nabla\times\nabla f=\mathbf 0$. This is the curl test for conservative fields in [[MATH2048 VC3 - Line Integrals and Conservative Fields|VC3]]. The same argument shows any centrally symmetric field, $f(r)\hat{\mathbf r}=\nabla\int f\,dr$, has zero curl.

### Proof that the divergence of a curl vanishes

Take the divergence of the curl's components:

$$
\nabla\cdot(\nabla\times\mathbf F)=\partial_x\big(\partial_yF_3-\partial_zF_2\big)+\partial_y\big(\partial_zF_1-\partial_xF_3\big)+\partial_z\big(\partial_xF_2-\partial_yF_1\big).
$$

Group by component. The $F_1$ terms are $\partial_y\partial_zF_1-\partial_z\partial_yF_1=0$, the $F_2$ terms are $-\partial_x\partial_zF_2+\partial_z\partial_xF_2=0$, and the $F_3$ terms are $\partial_x\partial_yF_3-\partial_y\partial_xF_3=0$. So $\nabla\cdot(\nabla\times\mathbf F)=0$. Identities with repeated cross products, such as 6, also need the vector triple-product rules.

### Proof of the product rule for divergence (identity 4)

*(Suggested, not lecturer-set.)* Write $g\mathbf F=(gF_1,gF_2,gF_3)$ and apply the ordinary product rule to each term of the divergence:

$$
\nabla\cdot(g\mathbf F)=\partial_x(gF_1)+\partial_y(gF_2)+\partial_z(gF_3)
$$

$$
=\big(F_1\partial_xg+F_2\partial_yg+F_3\partial_zg\big)+g\big(\partial_xF_1+\partial_yF_2+\partial_zF_3\big)
$$

$$
=\nabla g\cdot\mathbf F+g\,\nabla\cdot\mathbf F .
$$

With $g=\rho$ and $\mathbf F=\mathbf v$ this is the step used in the continuity equation in §1.

### Identity 6 on an example (PS9 Q5(c))

For $\mathbf F=x^2\,\mathbf i+xy\,\mathbf j+xz\,\mathbf k$, compute the curl twice. First,

$$
\nabla\times\mathbf F=\big(\partial_y(xz)-\partial_z(xy)\big)\mathbf i-\big(\partial_x(xz)-\partial_z(x^2)\big)\mathbf j+\big(\partial_x(xy)-\partial_y(x^2)\big)\mathbf k=0\,\mathbf i-z\,\mathbf j+y\,\mathbf k .
$$

Then, with $\mathbf G=(0,-z,y)$,

$$
\nabla\times\mathbf G=\big(\partial_y(y)-\partial_z(-z)\big)\mathbf i-\big(\partial_x(y)-\partial_z(0)\big)\mathbf j+\big(\partial_x(-z)-\partial_y(0)\big)\mathbf k=2\,\mathbf i .
$$

Now the right-hand side of identity 6: $\nabla\cdot\mathbf F=2x+x+x=4x$, so $\nabla(\nabla\cdot\mathbf F)=4\,\mathbf i$; and $\nabla^2\mathbf F=(\nabla^2x^2,\nabla^2(xy),\nabla^2(xz))=(2,0,0)$. So $\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F=4\,\mathbf i-2\,\mathbf i=2\,\mathbf i$, the same.

### Why the identities are useful

The identities simplify the equations of fluid dynamics. Taking the curl of Navier–Stokes with variable density, identity 2 removes the gradient terms but leaves a baroclinic term $\frac1{\rho^2}\nabla\rho\times\nabla p$, which vanishes when surfaces of constant pressure and density line up, as in strongly stratified ocean and atmosphere layers; with small viscosity, vorticity is then conserved along the flow. Identity 6 with $\nabla\cdot\mathbf v=0$ turns $\nabla\times(\nabla\times\mathbf v)$ into $-\nabla^2\mathbf v$. In a frame rotating at a constant rate $\boldsymbol\Omega$, the Coriolis term $-2\boldsymbol\Omega\times\mathbf v$ appears, and identity 8 with $\nabla\cdot\mathbf v=0$ and $\boldsymbol\Omega$ constant reduces its curl to $2(\boldsymbol\Omega\cdot\nabla)\mathbf v=2\Omega\frac{\partial\mathbf v}{\partial z}$ with $z$ along the rotation axis. The vorticity then changes only through how the velocity varies along that axis, which is what makes rotating-frame models of the atmosphere and of propellers tractable.

## 4. Past exam questions

**2023/24 B1(a)(iii).** For $\phi=\sin(yz)+x^2y^2+z$,

$$
\nabla^2\phi=\partial_x(2xy^2)+\partial_y\big(z\cos yz+2x^2y\big)+\partial_z\big(y\cos yz+1\big)=2y^2+\big(2x^2-z^2\sin yz\big)-y^2\sin yz ,
$$

so $\nabla^2\phi=2(x^2+y^2)-(y^2+z^2)\sin yz$. At $P(1,2,0)$, $\sin0=0$ and $\nabla^2\phi=2(1+4)=10$.

**PS8 Q6.** For $f=e^z\sin y$, $\nabla f=e^z\cos y\,\mathbf j+e^z\sin y\,\mathbf k$ and $\nabla^2f=-e^z\sin y+e^z\sin y=0$: this $f$ is harmonic, a solution of Laplace's equation, which is why the $y$ and $z$ curvatures cancel exactly.

**2024/25 B1(a).** For $\mathbf F=\sin(y^2)\,\mathbf i+(1+e^{2z})\,\mathbf j+x^2\,\mathbf k$ at the origin: the gradient of a vector field is not defined in this course, so (i) cannot be computed. Each component is independent of its own variable, so $\nabla\cdot\mathbf F=0$ everywhere. The curl is

$$
\nabla\times\mathbf F=\big(0-2e^{2z}\big)\,\mathbf i-\big(2x-0\big)\,\mathbf j+\big(0-2y\cos y^2\big)\,\mathbf k ,
$$

which at the origin is $-2\,\mathbf i$.

> [!check] SymPy
> The L24 curl, the L25 Laplacian $6e^xy\sin z$, both past-paper answers and identities 2, 5 and 6 on PS9's fields all check symbolically.

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] · Next: [[MATH2048 VC3 - Line Integrals and Conservative Fields]]
- Concepts: [[Divergence, Curl and the Laplacian]] · [[Gradient and Directional Derivative]] · [[Conservative Vector Fields]] · [[Laplace's Equation]]

## Sources

- Lecture 24 (25 Nov 2024) and Lecture 25 (26 Nov 2024) recordings, Ian Hawke: `MATH2048 Lecture 24.txt`, `MATH2048 Lecture 25.txt`
- Slides `Lecture24_vector04.pdf`, `Lecture25_vector05.pdf`; lecture notes §8.1.8–8.1.11
- Problem Sheet 9; exam questions 2023/24 B1(a) and 2024/25 B1(a)

## Self-study tasks

Nothing was explicitly set. Lecture 25 suggested looking for identities whenever repeated vector operations appear (ll. 359–365).

### Core

- [ ] PS9 Q1 and Q3: divergences and curls, including $\nabla\cdot\mathbf r=3$ and $\nabla\times\mathbf r=\mathbf 0$. → [[#The position vector (PS9 Q1(ii) and Q3(ii))]] · [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] PS9 Q6–Q7: $\nabla^2(x^2y^2z^2)=2(y^2z^2+x^2z^2+x^2y^2)$ and $\nabla^2(y^2,x^2,z^2)=(2,2,2)$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] Prove identities 2 and 5 without notes. → [[#Proof that the curl of a gradient vanishes]]
- [ ] 2024/25 B1(a): all three parts, including why (i) can't be done. → [[#4. Past exam questions]]

### Further practice

- [ ] PS9 Q5: $\nabla\times(\nabla\times\mathbf F)$ for three fields, checking (c) with identity 6. Answers: $\mathbf 0$, $\mathbf 0$, $2\,\mathbf i$. → [[#Identity 6 on an example (PS9 Q5(c))]]
- [ ] Prove identity 4, $\nabla\cdot(g\mathbf F)=\nabla g\cdot\mathbf F+g\nabla\cdot\mathbf F$, and use it to derive $\frac{D\rho}{Dt}=-\rho\nabla\cdot\mathbf v$ from the continuity equation (suggested, not lecturer-set). → [[#Proof of the product rule for divergence (identity 4)]]

## Transcript and slide slips

### Transcript slips

> [!warning] Lectures 24 and 25
> | Where | Transcript says | Correct |
> |---|---|---|
> | L24, ll. 99–104 | the components of $\nabla F_1$ written wrongly | $\nabla F_1=\partial_xF_1\,\mathbf i+\partial_yF_1\,\mathbf j+\partial_zF_1\,\mathbf k$ |
> | L24, l. 218 | the cross-product construction gives "the thing that we call the gradient" | the curl, corrected at l. 221 |
> | L24, l. 300 | a plus sign on the $\mathbf j$ term | minus, corrected in the same line |
> | L24, l. 354 | the curl of electromagnetic fields "is linked to its helicity" | the curl of $\mathbf B$ is linked to current density (Ampère's law); helicity is $\int\mathbf A\cdot\mathbf B$ |
> | L24, l. 402 | "auticity" | vorticity |
> | L25, l. 111 | $\nabla^2\phi=6e^x\sin z$ | $6e^xy\sin z$; the lecturer adds the $y$ at l. 124 |
> | L25, ll. 249–255 | baroclinic term $\nabla p\times\nabla\rho/\rho^2$ | $\nabla\rho\times\nabla p/\rho^2$, the opposite order |
> | L25, l. 292 | rotating-frame term "plus 2 omega cross u" | $-2\boldsymbol\Omega\times\mathbf v$ on the right-hand side; the lecture also uses $\omega$ for both the rotation rate and the vorticity |

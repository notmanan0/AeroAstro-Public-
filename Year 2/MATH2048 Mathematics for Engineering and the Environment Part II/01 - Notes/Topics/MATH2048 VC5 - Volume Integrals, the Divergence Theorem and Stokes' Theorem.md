---
title: "MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 19
tags:
  - math2048
  - vector-calculus
  - divergence-theorem
  - stokes-theorem
  - jacobian
aliases: ["MATH2048 Lecture 29", "MATH2048 Lecture 30", "Gauss's theorem", "Green's theorem", "Jacobian"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
next_topics: []
key_concepts: ["[[Jacobian and Volume Elements]]", "[[Divergence Theorem]]", "[[Stokes' Theorem]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture30_vector10.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.3)"]
---

# MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem

> [!abstract] Summary
> **Volume integrals in curvilinear coordinates**: $dV=|J|\,ds\,dt\,du$, where $J$ is the Jacobian. In cylindrical coordinates $dV=\rho\,d\rho\,d\phi\,dz$; in spherical coordinates $dV=r^2\sin\theta\,dr\,d\theta\,d\phi$.
>
> **The two big theorems.** Each turns an integral of a derivative over a region into an integral over the region's boundary, like $\int_a^bf'=f(b)-f(a)$:
>
> $$\underbrace{\iiint_V\nabla\cdot\mathbf F\,dV=\mathop{\large ∯}_{\partial V}\mathbf F\cdot d\mathbf S}_{\text{Gauss (divergence)}}\qquad \underbrace{\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_{\partial S}\mathbf F\cdot d\mathbf r}_{\text{Stokes}}$$
>
> Green's theorem is Stokes's theorem in the plane.
>
> Examined in 2025/26 B2 (20 marks): Gauss on a hemisphere, the Jacobian for spherical coordinates, and a shifted domain.

## Key Concepts
- [[Jacobian and Volume Elements]] · [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Flux Integrals]]

---

## 1. Jacobians and volume elements (L29)
For new coordinates $(s,t,u)$ with $x=x(s,t,u)$, $y=y(s,t,u)$, $z=z(s,t,u)$:

$$
dV=\left|\frac{\partial(x,y,z)}{\partial(s,t,u)}\right|ds\,dt\,du,\qquad J=\det\begin{pmatrix}x_s&x_t&x_u\\y_s&y_t&y_u\\z_s&z_t&z_u\end{pmatrix}.
$$

**Cylindrical**, $x=\rho\cos\phi$, $y=\rho\sin\phi$, $z=z$:

$$J=\begin{vmatrix}\cos\phi&-\rho\sin\phi&0\\\sin\phi&\rho\cos\phi&0\\0&0&1\end{vmatrix}=\rho(\cos^2\phi+\sin^2\phi)=\rho .$$

**Spherical**, $x=r\sin\theta\cos\phi$, $y=r\sin\theta\sin\phi$, $z=r\cos\theta$ (the 2025/26 B2(c) derivation). Expand along the bottom row $(\cos\theta,\ -r\sin\theta,\ 0)$:

$$
J=\begin{vmatrix}\sin\theta\cos\phi&r\cos\theta\cos\phi&-r\sin\theta\sin\phi\\\sin\theta\sin\phi&r\cos\theta\sin\phi&r\sin\theta\cos\phi\\\cos\theta&-r\sin\theta&0\end{vmatrix}
=\cos\theta\,\big(r^2\sin\theta\cos\theta\big)+r\sin\theta\,\big(r\sin^2\theta\big)=r^2\sin\theta .
$$

The two $2\times2$ minors are:
- $r\cos\theta\cos\phi\cdot r\sin\theta\cos\phi+r\sin\theta\sin\phi\cdot r\cos\theta\sin\phi=r^2\sin\theta\cos\theta$;
- $\sin\theta\cos\phi\cdot r\sin\theta\cos\phi+r\sin\theta\sin\phi\cdot\sin\theta\sin\phi=r\sin^2\theta$.

Adding, $J=r^2\sin\theta(\cos^2\theta+\sin^2\theta)$. So $dV=r^2\sin\theta\,dr\,d\theta\,d\phi$ ✔ (SymPy `Matrix.det`).

**Examples**:
- Volume of a sphere: $\int_0^{2\pi}\int_0^\pi\int_0^ar^2\sin\theta\,dr\,d\theta\,d\phi=\frac43\pi a^3$.
- PS11 Q1 (spherical shell $1\leq r\leq2$ with a $\pi/3$ wedge removed): $\frac{5}{6}\cdot\frac{4\pi}{3}(8-1)=\frac{70\pi}{9}$.
- PS11 Q2 (between $z=0$ and $z=x^2+y^2$ inside $r=a$): $\int_0^{2\pi}\int_0^a r^2\cdot r\,dr\,d\theta=\frac{\pi a^4}{2}$.

## 2. The divergence theorem (L29, Notes §8.3.6)
Let $V$ be a bounded solid with closed boundary $\partial V$, and let $\hat{\mathbf n}$ point **outward**. Then

$$\boxed{\iiint_V(\nabla\cdot\mathbf F)\,dV=\mathop{\large ∯}_{\partial V}\mathbf F\cdot d\mathbf S}$$

In words: total source strength inside equals net outflow through the boundary.

> [!example] Notes Ex. 1: $\mathbf F=\mathbf r$ on the closed cylinder (radius $a$, height $h$)
> **The hard way**, face by face:
> - top face: $\mathbf F\cdot\mathbf k=h$, giving $\pi a^2h$;
> - bottom face: $\mathbf F\cdot(-\mathbf k)=-z=0$;
> - curved side: $\mathbf F\cdot\hat{\boldsymbol\rho}=a$, giving $a\cdot2\pi ah$.
>
> The total is $3\pi a^2h$.
>
> **The easy way**: $\nabla\cdot\mathbf r=3$, so the flux is $3V=3\pi a^2h$ ✔. In general, $\mathop{\large ∯}\mathbf r\cdot d\mathbf S=3\times$ the enclosed volume.

> [!example] Notes Ex. 2: an open surface, closed off with a disc
> $\mathbf F=2xy^2\,\mathbf i+z^3\,\mathbf j-x^2y\,\mathbf k$ through the upper hemisphere $S$ of radius $a$.
> 1. Add the disc $\tilde S$ at $z=0$, with outward normal $-\mathbf k$, to make a closed surface.
> 2. The divergence is $\nabla\cdot\mathbf F=2y^2$. Its volume integral is $\iiint2y^2\,dV$. Slice at fixed $y$: each slice is a half-disc of area $\frac\pi2(a^2-y^2)$, so the integral is $\int_{-a}^a\pi y^2(a^2-y^2)\,dy=\frac{4\pi a^5}{15}$.
> 3. On the disc, $\mathbf F\cdot(-\mathbf k)=x^2y$, which integrates to $0$ by symmetry.
>
> So $\iint_S\mathbf F\cdot d\mathbf S=\frac{4\pi a^5}{15}$ ✔ (SymPy, in spherical coordinates).

> [!example] PS11 Q3 (verify): $\mathbf F=x\,\mathbf i+y\,\mathbf j+z^2\,\mathbf k$ over the quarter cylinder $x,y\geq0$, $x^2+y^2\leq1$, $0\leq z\leq1$
> **Volume side.** $\nabla\cdot\mathbf F=2+2z$, so the volume integral is $\frac\pi4\int_0^1(2+2z)\,dz=\frac{3\pi}{4}$.
>
> **Surface side**, face by face:
> - top ($z=1$): $\mathbf F\cdot\mathbf k=1$, over area $\frac\pi4$;
> - curved side: $\mathbf F\cdot\hat{\boldsymbol\rho}=x^2+y^2=1$, over area $\frac\pi2$;
> - bottom and the two flat walls: $0$.
>
> The total is $\frac\pi4+\frac\pi2=\frac{3\pi}4$ ✔.

## 3. Stokes's theorem (L30, Notes §8.3.1)
Let $S$ be an orientable surface with boundary curve $\partial S$. Then

$$\boxed{\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_{\partial S}\mathbf F\cdot d\mathbf r}$$

**Orientation (right-hand rule)**: curl the fingers of your right hand along $\partial S$; your thumb then points along $\hat{\mathbf n}$. For an upward normal, $\partial S$ is traversed **anticlockwise when viewed from above**.

> [!warning] The notes' wording
> The Lecture Notes text says "clockwise relative to the normal". That is looking along $\hat{\mathbf n}$ from above its tip, so it is the same rule. The worked examples use $t:0\to2\pi$ anticlockwise with an upward normal.

> [!example] Notes/L30: paraboloid $z=9-x^2-y^2\geq0$, $\mathbf F=(2z-y)\,\mathbf i+(x+z)\,\mathbf j+(3x-2y)\,\mathbf k$
> **Surface side.**
> - $\nabla\times\mathbf F=(-2-1,\ 2-3,\ 1+1)=(-3,-1,2)$.
> - For the graph, $d\mathbf S=(2x,2y,1)\,dx\,dy$.
> - So $\iint(-6x-2y+2)\,dx\,dy$ over the disc $x^2+y^2\leq9$. The odd terms vanish, leaving $2\times$ the area, i.e. $2\cdot9\pi=18\pi$.
>
> **Line side.** Take $\mathbf r=(3\cos t,3\sin t,0)$. Then $\mathbf F\cdot\dot{\mathbf r}=9\sin^2t+9\cos^2t=9$, and $\int_0^{2\pi}9\,dt=18\pi$ ✔.
>
> The notes' text drops the $\pi$ (it shows "$=18$"); SymPy confirms $18\pi$.

![[m2048_vc_stokes_paraboloid.png|560]]

**Corollary**: two surfaces with the **same boundary** carry the same flux of $\nabla\times\mathbf F$. So you can swap a hard surface for an easy one, e.g. the flat disc instead of the paraboloid (also $18\pi$). This works because $\nabla\cdot(\nabla\times\mathbf F)=0$.

> [!example] PS11 Q4 (verify): upper unit hemisphere, $\mathbf F=2y\,\mathbf i-x\,\mathbf j+xz\,\mathbf k$
> **Surface side.** $\nabla\times\mathbf F=(0,-z,-3)$. Dotting with $\hat{\mathbf n}=\mathbf r$ gives $-yz-3z$. The $-yz$ term integrates to $0$ by symmetry, and $\iint z\,dA=\pi$, so the flux is $-3\pi$.
>
> **Line side.** On the unit circle, $\oint(2y\,dx-x\,dy)=\int_0^{2\pi}(-2\sin^2t-\cos^2t)\,dt=-2\pi-\pi=-3\pi$ ✔.

## 4. Green's theorem (Stokes in the plane)
Take $\mathbf F=(F_1(x,y),F_2(x,y),0)$ and $d\mathbf S=\mathbf k\,dx\,dy$:

$$\iint_S\Big(\frac{\partial F_2}{\partial x}-\frac{\partial F_1}{\partial y}\Big)dx\,dy=\oint_{\partial S}(F_1\,dx+F_2\,dy),$$

with $\partial S$ traversed anticlockwise.

*Proof outline (not examinable)*: split $\partial S$ into an upper curve $y_+(x)$ and a lower curve $y_-(x)$. Then $\oint F_1\,dx=-\iint\partial_yF_1\,dx\,dy$, and the $F_2$ term works the same way.

**Area trick**: $A=\frac12\oint(x\,dy-y\,dx)$.

## 5. Vector potential (Notes §8.3.7)
If $\nabla\cdot\mathbf G=0$ in a simply connected region, then $\mathbf G=\nabla\times\mathbf A$ for some vector potential $\mathbf A$. The flux of such a $\mathbf G$ through any **closed** surface is $0$, and it is the same through any two surfaces with a common boundary.

## Summary: the integral-theorem family
| Theorem | Statement | Reduces |
|---|---|---|
| Fundamental theorem for gradients | $\int_A^B\nabla\phi\cdot d\mathbf r=\phi(B)-\phi(A)$ | curve → endpoints |
| Green | $\iint(F_{2,x}-F_{1,y})\,dA=\oint F_1dx+F_2dy$ | plane region → boundary curve |
| Stokes | $\iint(\nabla\times\mathbf F)\cdot d\mathbf S=\oint\mathbf F\cdot d\mathbf r$ | surface → boundary curve |
| Gauss | $\iiint\nabla\cdot\mathbf F\,dV=\mathop{\large ∯}\mathbf F\cdot d\mathbf S$ | volume → boundary surface |

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] (PS11) · [[MATH2048 Past Paper Solutions]]
- Aero link: circulation and Kelvin's theorem via Stokes ([[Kelvin's Circulation Theorem]]); control-volume mass flux via Gauss.

## Sources
- Lectures 29–30; Lecture Notes §8.3. Every example was checked in SymPy (including the Jacobian determinant).

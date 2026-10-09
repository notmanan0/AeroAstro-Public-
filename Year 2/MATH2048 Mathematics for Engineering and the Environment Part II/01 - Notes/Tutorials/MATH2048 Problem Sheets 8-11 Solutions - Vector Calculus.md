---
title: "MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: tutorial
stream: "Block 5: Vector Calculus"
tags:
  - math2048
  - tutorial-solutions
  - vector-calculus
sheet: "PS8 (grad, div, line integrals), PS9 (div, curl, Laplacian), PS10 (area and flux), PS11 (volume, divergence and Stokes)"
theory_notes: ["[[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]]", "[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]", "[[MATH2048 VC3 - Line Integrals and Conservative Fields]]", "[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]", "[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
key_concepts: ["[[Gradient and Directional Derivative]]", "[[Divergence, Curl and the Laplacian]]", "[[Line Integrals]]", "[[Flux Integrals]]", "[[Divergence Theorem]]", "[[Stokes' Theorem]]"]
status: complete
sources: ["02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 8.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 9.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 10.pdf", "02 - Sources/Lectures & Problem Sheets/Problem Sheets/Problem Sheet 11.pdf"]
---

# MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus

> [!abstract] Sheet Info
> Every answer was computed symbolically in SymPy. Gradients, divergences and curls were checked by explicit differentiation. Integrals were checked by explicit parametrisation (`vc_check.py` in the session scratchpad). There are no printed answers, apart from the "show that" results in PS10 Q1 and PS11 Q2, which are both reproduced.

## Theory Links
- [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] · [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] · [[MATH2048 VC3 - Line Integrals and Conservative Fields]] · [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]] · [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]

---

# PS8: Gradient, divergence, line integrals

## Q1: Gradients
- (a) $\nabla(e^y\sin x)=e^y\cos x\,\mathbf i+e^y\sin x\,\mathbf j$.
- (b) $\nabla(x^3y^2\ln z)=3x^2y^2\ln z\,\mathbf i+2x^3y\ln z\,\mathbf j+\dfrac{x^3y^2}{z}\mathbf k$.

## Q2: Directional derivatives
**(a)** $f=\dfrac{x^2}{3+y}$, so $\nabla f=\Big(\dfrac{2x}{3+y},\,-\dfrac{x^2}{(3+y)^2}\Big)$. At $(0,0)$ this is $\mathbf 0$, so the rate is **0** in every direction. With $\hat{\mathbf v}=\frac{1}{\sqrt2}(1,1)$ the answer is $0$.

**(b)** $f=2x+3y^2+2xyz$ gives $\nabla f=(2+2yz,\ 6y+2xz,\ 2xy)$. At $(1,2,1)$ this is $(6,14,4)$.
- $|\mathbf v|=|(2,2,1)|=3$.
- $\hat{\mathbf v}\cdot\nabla f=\frac{12+28+4}{3}=\boxed{\frac{44}{3}}$.

## Q3: Maximum rate of change
$\nabla f=(6x,4y,2z)$, which at $(0,1,1)$ is $(0,4,2)$. The maximum rate is $|\nabla f|=\sqrt{20}=2\sqrt5$, in the direction $(0,2,1)/\sqrt5$.

## Q4: Angle between the normals at $(2,-1,2)$
- $\mathbf n_1=\nabla(x^2+y^2+z^2)=(4,-2,4)$, with $|\mathbf n_1|=6$.
- $\mathbf n_2=\nabla(x^2+y^2-z)=(4,-2,-1)$, with $|\mathbf n_2|=\sqrt{21}$.

$$\cos\theta=\frac{16+4-4}{6\sqrt{21}}=\frac{8}{3\sqrt{21}}=\frac{8\sqrt{21}}{63}\ \Rightarrow\ \theta\approx54.4^\circ .$$

## Q5
$\nabla\cdot\mathbf F=\partial_x(x^2y)+\partial_y(z)+\partial_z(-x-y+z)=2xy+0+1=2xy+1$.

## Q6: $f=e^z\sin y$
- $\nabla f=(0,\ e^z\cos y,\ e^z\sin y)$.
- $\nabla^2f=0-e^z\sin y+e^z\sin y=0$. So $f$ is **harmonic**.

## Q7: Line integrals
**(a)** $\mathbf F=(y+2,x,0)$ with $\mathbf r=(\sin t,\cos t,0)$, $0\leq t\leq\pi/2$.
- $\dot{\mathbf r}=(\cos t,-\sin t,0)$.
- $\mathbf F\cdot\dot{\mathbf r}=(\cos t+2)\cos t-\sin^2t=\cos2t+2\cos t$.
- $\int_0^{\pi/2}=\big[\tfrac12\sin2t+2\sin t\big]_0^{\pi/2}=\boxed{2}$.

**(b)** $\mathbf F=(x,y,-z)=\nabla\big(\frac{x^2+y^2-z^2}{2}\big)$ is conservative, so only the endpoints matter.
- $\mathbf r(-1)=(-1,3,-2)$ and $\mathbf r(1)=(1,3,2)$.
- $\phi$ takes the same value, $\frac{1+9-4}{2}=3$, at both ends.
- So the integral is $\boxed{0}$.

Direct check: $\mathbf F\cdot\dot{\mathbf r}=t+18t^3-12t^5$, which is odd, so its integral over $[-1,1]$ is $0$ ✔.

**(c)** $\mathbf F=(3z,y^2,6z)$ with $\mathbf r=(\cos t,\sin t,t/3)$, $0\leq t\leq4\pi$.
- $\mathbf F\cdot\dot{\mathbf r}=-t\sin t+\sin^2t\cos t+\frac{2t}{3}$.
- The three terms integrate to:
  - $\int_0^{4\pi}-t\sin t\,dt=\big[t\cos t-\sin t\big]_0^{4\pi}=4\pi$;
  - $\int\sin^2t\cos t\,dt=\big[\frac{\sin^3t}{3}\big]=0$;
  - $\int\frac{2t}{3}dt=\frac{16\pi^2}{3}$.

$$\boxed{4\pi+\frac{16\pi^2}{3}}\ \text{(SymPy ✔)}$$

---

# PS9: Divergence, curl, Laplacian
Throughout, $\mathbf F=x^2y\,\mathbf i+y^2z\,\mathbf j+z^2x\,\mathbf k$ and $\mathbf G=2y\,\mathbf i+3x^2yz\,\mathbf j+\cos x\,\mathbf k$ where they appear.

The useful derivatives are:
- $\nabla\cdot\mathbf G=0+3x^2z+0=3x^2z$.
- $\nabla\times\mathbf G=(0-3x^2y)\,\mathbf i+(0+\sin x)\,\mathbf j+(6xyz-2)\,\mathbf k=(-3x^2y,\ \sin x,\ 6xyz-2)$.
- $\nabla\times\mathbf F=(0-y^2)\,\mathbf i+(0-z^2)\,\mathbf j+(0-x^2)\,\mathbf k=(-y^2,-z^2,-x^2)$.

## Q1: Divergence
- (i) $\nabla\cdot\mathbf F=0+4xy+\dfrac{z}{\sqrt{x^2+z^2}}$.
- (ii) $\nabla\cdot\mathbf r=3$.

## Q2
**(i)** $\mathbf F(\nabla\cdot\mathbf G)=3x^2z\,\mathbf F=(3x^4yz,\ 3x^2y^2z^2,\ 3x^3z^3)$.

**(ii)** $(\mathbf F\cdot\nabla)\mathbf G$: apply $x^2y\,\partial_x+y^2z\,\partial_y+z^2x\,\partial_z$ to each component of $\mathbf G$:
- $G_1=2y$ gives $2y^2z$;
- $G_2=3x^2yz$ gives $x^2y(6xyz)+y^2z(3x^2z)+z^2x(3x^2y)=3x^2yz\,(2xy+yz+xz)$;
- $G_3=\cos x$ gives $-x^2y\sin x$.

## Q3: Curl
**(i)**

$$\nabla\times\mathbf F=\Big(0-0\Big)\mathbf i+\Big(y\sinh z-\frac{x}{\sqrt{x^2+z^2}}\Big)\mathbf j+\big(2y^2-\cosh z\big)\mathbf k .$$

**(ii)** $\nabla\times\mathbf r=\mathbf 0$. Indeed $\mathbf r=\nabla\big(\tfrac12r^2\big)$, so this follows from curl grad $=\mathbf 0$.

## Q4
**(i)** $\mathbf F\cdot(\nabla\times\mathbf G)=-3x^4y^2+y^2z\sin x+6x^2yz^3-2xz^2$.

**(ii)** $\mathbf G\cdot(\nabla\times\mathbf F)=-2y^3-3x^2yz^3-x^2\cos x$.

**(iii)** $(\mathbf F\times\nabla)\cdot\mathbf G=\sum_i(\mathbf F\times\nabla)_iG_i$. Expanding:

$$(F_2\partial_z-F_3\partial_y)G_1+(F_3\partial_x-F_1\partial_z)G_2+(F_1\partial_y-F_2\partial_x)G_3 .$$

Regrouping by $F_1$, $F_2$, $F_3$ gives $F_1(\partial_yG_3-\partial_zG_2)+\dots=\mathbf F\cdot(\nabla\times\mathbf G)$. So the answer is the same as (i).

**(iv)**

$$\mathbf F\times(\nabla\times\mathbf G)=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\x^2y&y^2z&z^2x\\-3x^2y&\sin x&6xyz-2\end{vmatrix}$$

$$=\big(y^2z(6xyz-2)-z^2x\sin x\big)\,\mathbf i+\big(-3x^3yz^2-x^2y(6xyz-2)\big)\,\mathbf j+\big(x^2y\sin x+3x^2y^3z\big)\,\mathbf k$$

SymPy ✔.

## Q5: curl curl
| $\mathbf F$ | $\nabla\times\mathbf F$ | $\nabla\times(\nabla\times\mathbf F)$ |
|---|---|---|
| (a) $y\,\mathbf j$ | $\mathbf 0$ | $\mathbf 0$ |
| (b) $-y\,\mathbf i+x\,\mathbf j+\mathbf k$ | $2\mathbf k$ | $\mathbf 0$ |
| (c) $x^2\mathbf i+xy\,\mathbf j+xz\,\mathbf k$ | $(0,-z,y)$ | $2\,\mathbf i$ |

Check (c) with the identity $\nabla(\nabla\cdot\mathbf F)-\nabla^2\mathbf F$: $\nabla(4x)-(2,0,0)=(2,0,0)$ ✔.

## Q6
$\nabla^2(x^2y^2z^2)=2y^2z^2+2x^2z^2+2x^2y^2$.

## Q7
$\nabla^2\mathbf F=(\nabla^2y^2,\ \nabla^2x^2,\ \nabla^2z^2)=2\,\mathbf i+2\,\mathbf j+2\,\mathbf k$.

---

# PS10: Area and flux integrals

## Q1: Cone of base radius $a$ and height $h$
**Parametrise.** $\mathbf r=\big(\tfrac ah z\cos\theta,\ \tfrac ah z\sin\theta,\ z\big)$ for $0\leq\theta\leq2\pi$, $0\leq z\leq h$.

**Normal.**
- $\mathbf r_\theta=\big(-\tfrac ah z\sin\theta,\ \tfrac ah z\cos\theta,\ 0\big)$ and $\mathbf r_z=\big(\tfrac ah\cos\theta,\ \tfrac ah\sin\theta,\ 1\big)$.
- $\mathbf r_\theta\times\mathbf r_z=\Big(\tfrac ah z\cos\theta,\ \tfrac ah z\sin\theta,\ -\tfrac{a^2}{h^2}z\Big)$.

**Area element.**

$$|\mathbf r_\theta\times\mathbf r_z|=\frac{a}{h}z\sqrt{1+\frac{a^2}{h^2}}=\frac{a\sqrt{a^2+h^2}}{h^2}\,z,\qquad dA=\frac{a\sqrt{a^2+h^2}}{h^2}\,z\,d\theta\,dz .$$

**Area.**

$$A=\frac{a\sqrt{a^2+h^2}}{h^2}\cdot2\pi\cdot\frac{h^2}{2}=\boxed{\pi a\sqrt{a^2+h^2}}\ ✔$$

## Q2: Flux through the upper hemisphere $r=a$, $z\geq0$, upward normal
The upward normal is $\hat{\mathbf n}=\mathbf r/a$, with $dA=a^2\sin\theta\,d\theta\,d\phi$. The outward normal points up on the upper hemisphere, as required.

**(a)** $\mathbf F=y\,\mathbf j$ gives $\mathbf F\cdot\hat{\mathbf n}=y^2/a$. The flux is

$$\frac1a\iint y^2\,dA=\frac1a\cdot\frac{a^2}{3}\cdot2\pi a^2=\boxed{\frac{2\pi a^3}{3}},$$

using the symmetry $\iint x^2=\iint y^2=\iint z^2=\frac13\iint a^2\,dA$.

**(b)** $\mathbf F=-y\,\mathbf i+x\,\mathbf j+\mathbf k$ gives $\mathbf F\cdot\hat{\mathbf n}=\frac{-xy+xy+z}{a}=\frac za$. Using $\iint z\,dA=\int_0^{2\pi}\int_0^{\pi/2}a\cos\theta\,a^2\sin\theta\,d\theta\,d\phi=\pi a^3$, the flux is $\boxed{\pi a^2}$.

*Physical check*: only the $\mathbf k$ part contributes net flux, and it equals the $\mathbf k$ flux through the base disc, $\pi a^2$.

**(c)** $\mathbf F=x^2\,\mathbf i+xy\,\mathbf j+xz\,\mathbf k=x\mathbf r$ gives $\mathbf F\cdot\hat{\mathbf n}=\frac{x\,r^2}{a}=ax$. The flux is $a\iint x\,dA=\boxed{0}$, since $x$ is odd.

All three checked by explicit parametrisation ✔.

## Q3: $\mathbf F=y\,\mathbf i+xz^3\,\mathbf j-zy^3\,\mathbf k$ on the disc $x^2+y^2\leq a^2$, $z=b$

$$\nabla\times\mathbf F=\big(-3zy^2-3xz^2\big)\,\mathbf i+0\,\mathbf j+\big(z^3-1\big)\,\mathbf k .$$

With $d\mathbf S=\mathbf k\,dA$ (upward):

$$\iint(\nabla\times\mathbf F)\cdot d\mathbf S=(b^3-1)\,\pi a^2 .$$

*Stokes check*: take the boundary circle $\mathbf r=(a\cos t,a\sin t,b)$. Then

$$\oint\mathbf F\cdot d\mathbf r=\int_0^{2\pi}\big(-a^2\sin^2t+a^2b^3\cos^2t\big)\,dt=\pi a^2(b^3-1)\ ✔$$

## Q4: Funnel $x^2+y^2=z^2$, $0\leq z\leq9$
**(a) Sketch.** An inverted cone with its vertex at the origin, opening upward to a circle of radius 9 at $z=9$. Its half-angle is $45^\circ$.

**(b) Outward normal.** Parametrise $\mathbf r=(z\cos\theta,\ z\sin\theta,\ z)$. Then

$$\mathbf r_\theta\times\mathbf r_z=(z\cos\theta,\ z\sin\theta,\ -z)=(x,\ y,\ -z).$$

This points away from the axis and downward, i.e. **outward** from the funnel. Normalised: $\hat{\mathbf n}=\frac{(x,y,-z)}{\sqrt2\,z}$.

**(c) Flux.** $\mathbf F=-y\,\mathbf i+x\,\mathbf j+z\,\mathbf k$ gives $\mathbf F\cdot(\mathbf r_\theta\times\mathbf r_z)=-xy+xy-z^2=-z^2$. So

$$\iint\mathbf F\cdot d\mathbf S=\int_0^9\int_0^{2\pi}-z^2\,d\theta\,dz=-2\pi\cdot\frac{729}{3}=\boxed{-486\pi}.$$

With the inward normal the answer would be $+486\pi$.

---

# PS11: Volume, divergence and Stokes

## Q1: Shell $1\leq r\leq2$ with a $\pi/3$ wedge removed

$$V=\int_0^{5\pi/3}\int_0^\pi\int_1^2r^2\sin\theta\,dr\,d\theta\,d\phi=\frac{5\pi}{3}\cdot2\cdot\frac{7}{3}=\boxed{\frac{70\pi}{9}}\ \Big(=\tfrac56\text{ of the full shell }\tfrac{28\pi}{3}\Big).$$

## Q2: Inside $x^2+y^2=a^2$, between $z=0$ and $z=x^2+y^2$

$$V=\int_0^{2\pi}\int_0^a\underbrace{r^2}_{\text{height}}\cdot\underbrace{r\,dr\,d\theta}_{dA}=2\pi\frac{a^4}{4}=\boxed{\frac{\pi a^4}{2}}\ ✔$$

## Q3: Verify Gauss for $\mathbf F=(x,y,z^2)$ on the quarter cylinder $x,y\geq0$, $x^2+y^2\leq1$, $0\leq z\leq1$
**Volume side.** $\nabla\cdot\mathbf F=2+2z$. In cylindrical coordinates,

$$\int_0^1\!\int_0^{\pi/2}\!\int_0^1(2+2z)\,r\,dr\,d\theta\,dz=\frac{\pi}{4}\cdot3=\frac{3\pi}{4}.$$

**Surface side**, five faces with outward normals:

| Face | $\hat{\mathbf n}$ | $\mathbf F\cdot\hat{\mathbf n}$ | Area | Contribution |
|---|---|---|---|---|
| top $z=1$ | $\mathbf k$ | $1$ | $\pi/4$ | $\pi/4$ |
| bottom $z=0$ | $-\mathbf k$ | $-z^2=0$ | | $0$ |
| curved $r=1$ | $(x,y,0)$ | $x^2+y^2=1$ | $\frac\pi2\cdot1$ | $\pi/2$ |
| $x=0$ | $-\mathbf i$ | $-x=0$ | | $0$ |
| $y=0$ | $-\mathbf j$ | $-y=0$ | | $0$ |

The total is $\frac{3\pi}{4}$ ✔, so the theorem is verified.

## Q4: Verify Stokes for $\mathbf F=2y\,\mathbf i-x\,\mathbf j+xz\,\mathbf k$ on the upper unit hemisphere
**Surface side.** $\nabla\times\mathbf F=(0-0,\ 0-z,\ -1-2)=(0,-z,-3)$. With the outward/upward normal $\hat{\mathbf n}=\mathbf r$, $(\nabla\times\mathbf F)\cdot\hat{\mathbf n}=-yz-3z$.
- $\iint-yz\,dA=0$ (odd in $y$).
- $\iint-3z\,dA=-3\pi$.

So the flux is $-3\pi$.

**Line side.** The boundary is the unit circle, traversed anticlockwise from above: $\mathbf r=(\cos t,\sin t,0)$. Then

$$\oint\mathbf F\cdot d\mathbf r=\int_0^{2\pi}\big[2\sin t(-\sin t)+(-\cos t)\cos t\big]dt=-2\pi-\pi=-3\pi\ ✔$$

*Shortcut*: by the corollary, the flat unit disc would give $\iint(-3)\,dA=-3\pi$ too.

## Sources
- PS8–PS11. Verified in SymPy.

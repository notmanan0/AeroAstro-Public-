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
aliases: ["MATH2048 Lecture 29", "MATH2048 Lecture 30", "Gauss's theorem", "Jacobian"]
date: 2026-10-30
status: lectured
coverage: "Lecture 29 (4 Dec 2024): volume integrals with a parametrisation, the Jacobian, cylindrical and spherical volume elements, the divergence theorem and outward normals, the closed cylinder both ways, closing an open hemisphere with a disc, and conservation laws from weak to strong form. Lecture 30 (9 Dec 2024): Stokes' theorem and the right-hand rule, the paraboloid example both ways, and the same-boundary corollary. Both Ian Hawke."
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
next_topics: []
key_concepts: ["[[Jacobian and Volume Elements]]", "[[Divergence Theorem]]", "[[Stokes' Theorem]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures/MATH2048 Lecture 29.txt", "02 - Sources/Lectures/MATH2048 Lecture 30.txt", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture30_vector10.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.2.7, §8.3)"]
---

# MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem

> [!abstract] Summary
> A volume described by three parameters has volume element $dV=|\det J|\,ds\,dt\,du$, where the Jacobian matrix $J$ holds the derivatives of $x$, $y$, $z$ with respect to the parameters; this gives $\rho\,d\rho\,d\phi\,dz$ in cylindrical and $r^2\sin\theta\,dr\,d\theta\,d\phi$ in spherical coordinates. The divergence theorem $\oiint_S\mathbf F\cdot d\mathbf S=\iiint_V\nabla\cdot\mathbf F\,dV$, with the outward normal, links the flux out of a closed surface to a volume integral. Stokes' theorem $\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_C\mathbf F\cdot d\mathbf r$, with normal and direction of travel related by the right-hand rule, links a surface to its boundary curve, so any two surfaces with the same edge give the same answer.

> [!summary]- Exam use: quick path
> - **Use it when:** asked for a volume or volume integral, a Jacobian, or a flux or circulation that one of the theorems makes easier (2023/24 B2(e); 2024/25 B2; 2025/26 B2; PS11).
> - **Assumptions:** fields smooth throughout the volume or surface; for the divergence theorem a closed surface with the outward normal; for Stokes an open surface whose boundary is traversed by the right-hand rule.
> - **Method:** 1. Decide which side is easier: for a flux, compute $\nabla\cdot\mathbf F$; for a curl flux, look at the boundary. 2. If the surface isn't closed, close it with a flat piece and subtract that flux. 3. Choose coordinates that fit the boundaries and write $dV$ or $d\mathbf S$. 4. Express the integrand in those coordinates. 5. Integrate, using symmetry to drop odd terms.
> - **Common mistakes:** using an inward normal in the divergence theorem; traversing the Stokes boundary the wrong way for the chosen normal.
> - **Practise:** [[#The closed cylinder both ways (L29)]] · [[#The paraboloid both ways (L30)]] · [[#4. Past exam questions B2]]

Line, surface and volume integrals all follow one pattern: parametrise the object, find how the parameters stretch length, area or volume, and integrate over a simple region of parameters (L30, ll. 5–9). The last two lectures add the third case and then the two results that make the block worthwhile, which the lecturer called "possibly the key result for this entire unit" (L29, l. 3).

Both theorems trade an integral over a region for one over its boundary, one dimension down. The divergence theorem links a volume to the closed surface around it, through the divergence, which measures sources. Stokes' theorem links a surface to the curve around its edge, through the curl, which measures rotation. Lecture 30 noted that they are really the same theorem in different dimensions, and the line integral of a conservative field in [[MATH2048 VC3 - Line Integrals and Conservative Fields|VC3]], $\int\nabla\phi\cdot d\mathbf r=\phi(B)-\phi(A)$, is the one-dimensional member of the family.

---

## 1. Volume integrals and the Jacobian (L29)

The course only integrates scalar fields over volumes, $\iiint_Vf\,dV$ (ll. 8–18). For a box, this is three nested ordinary integrals in $x$, $y$, $z$. For anything shaped differently, the limits in Cartesian coordinates become awkward or impossible, so describe the volume with three parameters chosen to make the limits simple:

$$
\mathbf r(s,t,u)=x(s,t,u)\,\mathbf i+y(s,t,u)\,\mathbf j+z(s,t,u)\,\mathbf k .
$$

### The volume element

A small box in parameter space, $ds\times dt\times du$, maps to a small parallelepiped whose edges, by the same Taylor expansion as for surfaces, are $\mathbf r_s\,ds$, $\mathbf r_t\,dt$ and $\mathbf r_u\,du$ (ll. 35–74). The volume of a parallelepiped is the absolute value of the determinant of its three edge vectors, so

$$
dV=|\det J|\,ds\,dt\,du,\qquad J=\begin{pmatrix}\partial_sx&\partial_tx&\partial_ux\\\partial_sy&\partial_ty&\partial_uy\\\partial_sz&\partial_tz&\partial_uz\end{pmatrix}.
$$

Writing the derivatives in rows instead of columns transposes $J$, which leaves the determinant unchanged. The order matters when $J$ is used to transform vectors, but not here.

### Cylindrical coordinates

$x=\rho\cos\phi$, $y=\rho\sin\phi$, $z=z$, with $\rho$ the distance from the axis now varying from 0 to the radius, unlike on the cylinder's surface (ll. 78–117). The Jacobian, columns in the order $\rho$, $\phi$, $z$:

$$
J=\begin{pmatrix}\cos\phi&-\rho\sin\phi&0\\\sin\phi&\rho\cos\phi&0\\0&0&1\end{pmatrix}.
$$

Expanding along the bottom row,

$$
\det J=\cos\phi\cdot\rho\cos\phi-(-\rho\sin\phi)\sin\phi=\rho\cos^2\phi+\rho\sin^2\phi=\rho ,
$$

so

$$
dV=\rho\,d\rho\,d\phi\,dz .
$$

### Spherical coordinates

$x=r\sin\theta\cos\phi$, $y=r\sin\theta\sin\phi$, $z=r\cos\theta$, with $\theta$ measured down from the north pole, $0\leq\theta\leq\pi$, and $\phi$ round the axis (ll. 117–124). The Jacobian, columns in the order $r$, $\theta$, $\phi$:

$$
J=\begin{pmatrix}\sin\theta\cos\phi&r\cos\theta\cos\phi&-r\sin\theta\sin\phi\\\sin\theta\sin\phi&r\cos\theta\sin\phi&r\sin\theta\cos\phi\\\cos\theta&-r\sin\theta&0\end{pmatrix}.
$$

Expand along the bottom row. The $\cos\theta$ entry's minor is

$$
r\cos\theta\cos\phi\cdot r\sin\theta\cos\phi-(-r\sin\theta\sin\phi)\,r\cos\theta\sin\phi=r^2\sin\theta\cos\theta .
$$

The $-r\sin\theta$ entry carries a minus sign from its position, and its minor is

$$
\sin\theta\cos\phi\cdot r\sin\theta\cos\phi-(-r\sin\theta\sin\phi)\sin\theta\sin\phi=r\sin^2\theta .
$$

So

$$
\det J=\cos\theta\cdot r^2\sin\theta\cos\theta+r\sin\theta\cdot r\sin^2\theta=r^2\sin\theta(\cos^2\theta+\sin^2\theta)=r^2\sin\theta ,
$$

and

$$
dV=r^2\sin\theta\,dr\,d\theta\,d\phi .
$$

This derivation is exactly what 2024/25 B2(a) and 2025/26 B2(c) ask for. The volume of a ball of radius $a$ then separates into three single integrals (ll. 136–153):

$$
V=\int_0^{2\pi}\!\!d\phi\int_0^\pi\sin\theta\,d\theta\int_0^ar^2\,dr=2\pi\cdot2\cdot\frac{a^3}3=\frac{4\pi a^3}3 .
$$

To integrate a scalar field instead, rewrite it in the new coordinates first and multiply by $dV$ (ll. 154–165). The same mapping of a simple reference element onto each real element, through its Jacobian, is how finite-element solvers such as Fluent handle arbitrary meshes (ll. 124–135).

## 2. The divergence theorem (L29)

For a volume $V$ enclosed by a closed surface $S$, with $\hat{\mathbf n}$ the **outward** normal (ll. 166–199),

$$
\oiint_S\mathbf F\cdot d\mathbf S=\iiint_V\nabla\cdot\mathbf F\,dV .
$$

It is also called Gauss's theorem. The circle on the double integral marks a closed surface, one that completely encloses the volume. The sign of a flux depends on the normal, while the volume integral has no normal at all, so only one choice can be right, and it is the outward normal; "outward" only makes sense because the surface is closed. The divergence of $\mathbf F$ must exist everywhere inside $V$.

The theorem is what the divergence measures. $\nabla\cdot\mathbf F$ at a point is the net outflow per unit volume from a tiny box there. Split $V$ into many such boxes and add up their outflows: across every internal face, what leaves one box enters its neighbour, so those fluxes cancel, and only the flux through the outer surface survives.

### The closed cylinder both ways (L29)

Find the flux of $\mathbf F=x\,\mathbf i+y\,\mathbf j+z\,\mathbf k$ out of the closed cylinder of radius $a$ and height $h$, $0\leq z\leq h$ (ll. 200–303). Directly, the surface has to be split into pieces on which the normal varies smoothly, because it jumps at the rims (ll. 210–233): the bottom $S_1$, the top $S_2$ and the curved side $S_3$.

On $S_1$ the outward normal is $-\mathbf k$, so $\mathbf F\cdot d\mathbf S=-z\,dA$, and $z=0$ there: no flux. On $S_2$ it is $+\mathbf k$ and $z=h$, so the flux is $h$ times the disc's area, $\pi a^2h$. On $S_3$, from [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals|VC4]], $d\mathbf S=(a\cos s\,\mathbf i+a\sin s\,\mathbf j)\,ds\,dt$ and on the surface $x=a\cos s$, $y=a\sin s$, so

$$
\iint_{S_3}\mathbf F\cdot d\mathbf S=\int_0^h\int_{-\pi}^{\pi}\big(a^2\cos^2s+a^2\sin^2s\big)\,ds\,dt=2\pi a^2h .
$$

The total is $0+\pi a^2h+2\pi a^2h=3\pi a^2h$.

With the theorem, $\nabla\cdot\mathbf F=1+1+1=3$, so

$$
\oiint_S\mathbf F\cdot d\mathbf S=\iiint_V3\,dV=3\cdot\pi a^2h ,
$$

with no calculation beyond the volume. This isn't just a contrived example (ll. 305–311): $\nabla\cdot\mathbf r=3$, so any part of a field pointing radially from the origin contributes 3 times the volume.

### Closing an open surface (L29)

The theorem needs a closed surface, but an open one can be closed artificially (ll. 312–333). Find the flux of $\mathbf F=2xy^2\,\mathbf i+z^3\,\mathbf j-x^2y\,\mathbf k$ out through the curved hemisphere $S$: $r=a$, $z\geq0$. Add the flat disc $\tilde S$ in the plane $z=0$. Together they enclose the half-ball $V$, so

$$
\iint_S\mathbf F\cdot d\mathbf S+\iint_{\tilde S}\mathbf F\cdot d\mathbf S=\iiint_V\nabla\cdot\mathbf F\,dV .
$$

The divergence is $\partial_x(2xy^2)+\partial_y(z^3)+\partial_z(-x^2y)=2y^2$ (ll. 334–346). In spherical coordinates $y^2=r^2\sin^2\theta\sin^2\phi$, and the half-ball has $0\leq\theta\leq\frac\pi2$ (ll. 347–395):

$$
\iiint_V2y^2\,dV=2\int_0^ar^4\,dr\int_0^{\pi/2}\sin^3\theta\,d\theta\int_0^{2\pi}\sin^2\phi\,d\phi=2\cdot\frac{a^5}5\cdot\frac23\cdot\pi=\frac{4\pi a^5}{15}.
$$

On the disc the outward normal of the half-ball points down, $d\mathbf S=-\mathbf k\,dA$, so $\mathbf F\cdot d\mathbf S=x^2y\,dA$ (ll. 397–419). The disc is symmetric in $y$ and $x^2y$ is odd in $y$, so its integral is zero. Hence

$$
\iint_S\mathbf F\cdot d\mathbf S=\frac{4\pi a^5}{15}-0=\frac{4\pi a^5}{15}.
$$

### Conservation laws: weak and strong form

The theorem is how the differential conservation laws of fluids and electromagnetism are derived (ll. 422–456). The mass in a fixed volume changes only by flux through its boundary:

$$
\frac{d}{dt}\iiint_V\rho\,dV=-\oiint_S\rho\mathbf v\cdot d\mathbf S .
$$

This is the weak, or integral, form; the only physics is the form of the flux. The divergence theorem turns the right-hand side into a volume integral:

$$
\iiint_V\Big(\frac{\partial\rho}{\partial t}+\nabla\cdot(\rho\mathbf v)\Big)\,dV=0 .
$$

This holds for every volume, so the integrand itself must vanish, which gives the strong, differential form, the continuity equation $\partial_t\rho+\nabla\cdot(\rho\mathbf v)=0$. The step needs the divergence to exist everywhere in $V$. At a shock it doesn't: the weak form still holds across the discontinuity but the strong form breaks down, which is why shock-capturing codes are built on the integral form.

## 3. Stokes' theorem (L30)

For an open surface $S$ with boundary curve $C$ (L30, ll. 17–72),

$$
\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\oint_C\mathbf F\cdot d\mathbf r .
$$

Now both sides have a direction to choose, the normal on the left and the way round the curve on the right, and they are tied by the right-hand rule: with the thumb along the normal, the fingers curl in the direction of travel (ll. 37–53). If the normal points up, $C$ is traversed anticlockwise seen from above. The surface must have an edge; a closed surface has no boundary, and then the left side is zero.

The reasoning mirrors the divergence theorem. The component of $\nabla\times\mathbf F$ along $\hat{\mathbf n}$ is the circulation per unit area round a tiny loop in the surface. Tile $S$ with tiny loops all traversed by the right-hand rule: each internal edge is traversed once each way by its two neighbours and cancels, leaving only the outer boundary $C$.

### The paraboloid both ways (L30)

Take $\mathbf F=(2z-y)\,\mathbf i+(x+z)\,\mathbf j+(3x-2y)\,\mathbf k$ on the paraboloid $z=9-x^2-y^2$, $z\geq0$, open at the bottom, with upward normal (ll. 73–121). Its curl is constant:

$$
\nabla\times\mathbf F=\big(-2-1\big)\,\mathbf i-\big(3-2\big)\,\mathbf j+\big(1-(-1)\big)\,\mathbf k=-3\,\mathbf i-\mathbf j+2\,\mathbf k .
$$

Surface side, as on the slides (ll. 239–288). The paraboloid is a graph, so from VC4 the upward $d\mathbf S=(-f_x,-f_y,1)\,dx\,dy=(2x,2y,1)\,dx\,dy$, and

$$
\iint_S(\nabla\times\mathbf F)\cdot d\mathbf S=\iint_{x^2+y^2\leq9}\big(-6x-2y+2\big)\,dx\,dy .
$$

The disc is symmetric and $-6x-2y$ is odd, so only the 2 survives: twice the disc's area, $2\cdot9\pi=18\pi$.

Line side (ll. 289–341). The boundary is the circle $x^2+y^2=9$, $z=0$, anticlockwise for an upward normal: $\mathbf r=3\cos t\,\mathbf i+3\sin t\,\mathbf j$, $0\leq t\leq2\pi$. On it $\mathbf F=-3\sin t\,\mathbf i+3\cos t\,\mathbf j+(9\cos t-6\sin t)\,\mathbf k$, and $\frac{d\mathbf r}{dt}=-3\sin t\,\mathbf i+3\cos t\,\mathbf j$, so

$$
\oint_C\mathbf F\cdot d\mathbf r=\int_0^{2\pi}\big(9\sin^2t+9\cos^2t\big)\,dt=18\pi .
$$

Both sides agree.

![[m2048_vc_stokes_paraboloid.png|620]]

### Any surface with the same boundary

The right-hand side depends only on the curve $C$, so the surface integral of a curl is the same over every surface with that boundary, provided the field is defined on all of them (ll. 350–389). Here the flat disc $z=0$, $x^2+y^2\leq9$, with normal $\mathbf k$, gives $\iint2\,dA=18\pi$ at once, which is why the slides' answer was twice the disc's area. To integrate a curl over an awkward surface, swap it for the flattest surface with the same edge, or for the line integral round the edge.

The lecture's own parametrisation, $\mathbf r=(3-s)\cos t\,\mathbf i+(3-s)\sin t\,\mathbf j+s\,\mathbf k$, $0\leq s\leq3$, was in fact a cone, radius shrinking linearly from 3 to 0 as the height rises to 3, not the paraboloid, which reaches height 9 (ll. 126–148). By the corollary it gives the same answer: with the upward normal $\mathbf r_t\times\mathbf r_s=(3-s)(\cos t\,\mathbf i+\sin t\,\mathbf j+\mathbf k)$, the curl flux is $\int_0^3\int_0^{2\pi}(3-s)(2-3\cos t-\sin t)\,dt\,ds=4\pi\cdot\frac92=18\pi$. In the plane, with $\mathbf F=F_1\,\mathbf i+F_2\,\mathbf j$ and $d\mathbf S=\mathbf k\,dx\,dy$, Stokes' theorem becomes Green's theorem, $\iint(\partial_xF_2-\partial_yF_1)\,dx\,dy=\oint(F_1\,dx+F_2\,dy)$.

> [!check] SymPy
> Both Jacobians, $3\pi a^2h$, $\frac{4\pi a^5}{15}$, and $18\pi$ by the paraboloid, the cone and the line integral.

## 4. Past exam questions B2

**2023/24 B2(e).** $\mathbf F=3z\,\mathbf k$ has $\nabla\cdot\mathbf F=3$. The hemisphere $S$ and the disc $\tilde S$ together enclose the half-ball, and VC4 found fluxes $2\pi$ through $S$ (outward) and $0$ through $\tilde S$. So $3V=2\pi+0$ and $V=\frac{2\pi}3$, the volume of a unit half-ball.

**2024/25 B2.** After the Jacobian in (a), the region $0\leq r\leq R$, $0\leq\theta\leq\alpha$, $0\leq\phi\leq\beta$ has

$$
V(\alpha,\beta)=\int_0^\beta d\phi\int_0^\alpha\sin\theta\,d\theta\int_0^Rr^2\,dr=\frac{R^3\beta}3\big(1-\cos\alpha\big).
$$

With $\beta=2\pi$, $V=\frac{2\pi R^3}3(1-\cos\alpha)$ rises from 0 like $\frac{\pi R^3}3\alpha^2$ for small $\alpha$, through $\frac{2\pi R^3}3$ (a hemisphere) at $\alpha=\frac\pi2$, to the whole ball $\frac{4\pi R^3}3$ at $\alpha=\pi$.

**2025/26 B2.** $\Phi=x^2+y^2+z^3$ gives $\mathbf F=\nabla\Phi=2x\,\mathbf i+2y\,\mathbf j+3z^2\,\mathbf k$ and $\nabla\cdot\mathbf F=4+6z$. Over the closed surface of the unit upper half-ball, Gauss gives $\iiint(4+6z)\,dV$. In spherical coordinates, $\iiint4\,dV=4\cdot\frac{2\pi}3=\frac{8\pi}3$ and

$$
\iiint6z\,dV=6\int_0^{2\pi}\!d\phi\int_0^{\pi/2}\cos\theta\sin\theta\,d\theta\int_0^1r^3\,dr=6\cdot2\pi\cdot\frac12\cdot\frac14=\frac{3\pi}2 ,
$$

so the integral is $\frac{8\pi}3+\frac{3\pi}2=\frac{25\pi}6$. For the half-ball centred on $(0,0,1)$, shift $z=z'+1$: the integrand becomes $10+6z'$ over the original half-ball, giving $10\cdot\frac{2\pi}3+\frac{3\pi}2=\frac{49\pi}6$ with no new integrals.

## Transcript slips

> [!warning] Lectures 29 and 30
> | Where | Transcript says | Correct |
> |---|---|---|
> | L29, ll. 38–39 | the volume element is "the magnitude of the Jacobian matrix" | the absolute value of its determinant |
> | L29, l. 173 | the theorem needs a "simply connected volume" | a bounded region with a closed, piecewise-smooth boundary; a region with a cavity works if the cavity's surface is included |
> | L29, l. 278 | the $\mathbf j$ term gives "a squared cos squared s" | $a^2\sin^2s$, corrected at l. 282 |
> | L29, l. 458 | slides on applying the theorem to "kills" | curls |
> | L30, ll. 126–148 | the paraboloid parametrised as radius $3-s$ at height $s$ | that surface is a cone of height 3; the paraboloid has height 9. The answer still agrees, by the same-boundary corollary |
> | L30, ll. 174–186, 219–225 | normal components "$s-3$", then "messed up a sign" | $\mathbf r_s\times\mathbf r_t=-(3-s)(\cos t,\sin t,1)$ points down; the upward normal is $\mathbf r_t\times\mathbf r_s$ |
> | L30, l. 121 | "minus 3y minus j plus 2k" | $-3\,\mathbf i-\mathbf j+2\,\mathbf k$ |

## Links

- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]
- Concepts: [[Jacobian and Volume Elements]] · [[Divergence Theorem]] · [[Stokes' Theorem]] · [[Flux Integrals]] · [[Conservative Vector Fields]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] · [[MATH2048 Past Paper Solutions]]

## Sources

- Lecture 29 (4 Dec 2024) and Lecture 30 (9 Dec 2024) recordings, Ian Hawke: `MATH2048 Lecture 29.txt`, `MATH2048 Lecture 30.txt`
- Slides `Lecture29_vector09.pdf`, `Lecture30_vector10.pdf`; lecture notes §8.2.7 and §8.3
- Problem Sheet 11; exam questions 2023/24 B2, 2024/25 B2 and 2025/26 B2

## Self-study tasks

Lecture 29 suggested reading the extra slides on applying the divergence theorem to curls (ll. 458–460), and Lecture 30 pointed back to them as the divergence-theorem version of the same-boundary result (ll. 383–389).

### Core

- [ ] Derive $dV=r^2\sin\theta\,dr\,d\theta\,d\phi$ from the Jacobian, as in 2024/25 B2(a) and 2025/26 B2(c). → [[#Spherical coordinates]]
- [ ] Rework the closed cylinder both ways. → [[#The closed cylinder both ways (L29)]]
- [ ] PS11 Q1–Q2: a shell with a wedge removed and the region under $z=x^2+y^2$. Answers: $\frac{70\pi}9$; $\frac{\pi a^4}2$. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] 2025/26 B2(a)–(e). → [[#4. Past exam questions B2]]

### Further practice

- [ ] PS11 Q3–Q4: verify Gauss on a quarter cylinder and Stokes on the upper unit hemisphere. → [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]
- [ ] Lecturer-suggested (L29, ll. 458–460; L30, ll. 383–389): read the extra slides on the divergence theorem applied to a curl, and show from $\nabla\cdot(\nabla\times\mathbf F)=0$ that the curl flux through any closed surface is zero. → [[#Any surface with the same boundary]]

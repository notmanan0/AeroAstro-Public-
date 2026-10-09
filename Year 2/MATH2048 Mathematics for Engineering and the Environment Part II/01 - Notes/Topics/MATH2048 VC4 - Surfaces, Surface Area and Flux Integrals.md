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
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC3 - Line Integrals and Conservative Fields]]"]
next_topics: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
key_concepts: ["[[Flux Integrals]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture27_vector07.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture28_vector08.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.2.3–8.2.6)"]
---

# MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals

> [!abstract] Summary
> Parametrise a surface as $\mathbf r(s,t)$. Then:
> - the tangent vectors are $\mathbf r_s$ and $\mathbf r_t$;
> - the **normal** is $\mathbf n=\mathbf r_s\times\mathbf r_t$;
> - the **area element** is $dA=|\mathbf r_s\times\mathbf r_t|\,ds\,dt$;
> - the **vector area element** is $d\mathbf S=\hat{\mathbf n}\,dA=(\mathbf r_s\times\mathbf r_t)\,ds\,dt$.
>
> The **flux** $\iint_S\mathbf F\cdot d\mathbf S$ measures the net flow through $S$. Always check that $\mathbf r_s\times\mathbf r_t$ points in the required direction (up or out), and swap the order to flip it.

## Key Concepts
- [[Flux Integrals]] · [[Jacobian and Volume Elements]]

---

## 1. Three ways to describe a surface (Notes §8.2.3)
1. **Graph**: $z=f(x,y)$.
2. **Level surface**: $F(x,y,z)=c$.
3. **Parametrised**: $(s,t)\mapsto\mathbf r(s,t)$. This is the form used for integrals.

**Standard parametrisations**:

| Surface | $\mathbf r(s,t)$ | $\mathbf r_s\times\mathbf r_t$ | $dA$ |
|---|---|---|---|
| Cylinder of radius $a$ | $(a\cos s,\ a\sin s,\ t)$ | $(a\cos s,\ a\sin s,\ 0)$ (outward) | $a\,ds\,dt$ |
| Sphere of radius $a$ ($\theta$ polar, $\phi$ azimuth) | $a(\sin\theta\cos\phi,\ \sin\theta\sin\phi,\ \cos\theta)$ | $\mathbf r_\theta\times\mathbf r_\phi=a^2\sin\theta\,\hat{\mathbf r}$ (outward) | $a^2\sin\theta\,d\theta\,d\phi$ |
| Graph $z=f(x,y)$ | $(x,\ y,\ f)$ | $(-f_x,\ -f_y,\ 1)$ (upward) | $\sqrt{1+f_x^2+f_y^2}\,dx\,dy$ |
| Cone of radius $a$, height $h$ | $\big(\tfrac{a}{h}z\cos\theta,\ \tfrac{a}{h}z\sin\theta,\ z\big)$ | $\mathbf r_\theta\times\mathbf r_z$ points out and down | $\frac{a}{h^2}\sqrt{a^2+h^2}\,z\,d\theta\,dz$ |

**Why $\mathbf r_s\times\mathbf r_t$?** It is normal because it is perpendicular to both tangent vectors. By Taylor's theorem, a small patch is a parallelogram with sides $\mathbf r_s\Delta s$ and $\mathbf r_t\Delta t$, so its area is $|\mathbf r_s\times\mathbf r_t|\Delta s\Delta t$.

## 2. Surface areas (L27)
- **Cylinder**: $\int_{-\pi}^{\pi}\int_0^ha\,dt\,ds=2\pi ah$.
- **Sphere**: $\int_0^{2\pi}\int_0^\pi a^2\sin\theta\,d\theta\,d\phi=2\pi a^2[-\cos\theta]_0^\pi=4\pi a^2$.
- **Cone** (PS10 Q1): $\int_0^{2\pi}\int_0^h\frac{a}{h^2}\sqrt{a^2+h^2}\,z\,dz\,d\theta=\pi a\sqrt{a^2+h^2}$ ✔.

## 3. Flux integrals (L28, Notes §8.2.6)
$$
\iint_S\mathbf F\cdot d\mathbf S=\iint\mathbf F(\mathbf r(s,t))\cdot(\mathbf r_s\times\mathbf r_t)\,ds\,dt .
$$
If $\mathbf F$ is a fluid velocity, this is the volume flow rate through $S$. The result does not depend on the parametrisation (a change of variables introduces exactly the Jacobian), **but it does depend on the orientation**.

**For a graph $z=f(x,y)$**:
$$
\iint_S\mathbf F\cdot d\mathbf S=\iint\mathbf F\cdot(-f_x\,\mathbf i-f_y\,\mathbf j+\mathbf k)\,dx\,dy\quad(\text{upward normal}).
$$

> [!example] Notes: helicoid $\mathbf r=(s\cos t,\ s\sin t,\ t)$, $0\leq s\leq1$, $0\leq t\leq2\pi$, with $\mathbf F=x\,\mathbf i+y\,\mathbf j+(z-2y)\,\mathbf k$
> 1. **Normal.** $\mathbf r_s=(\cos t,\sin t,0)$ and $\mathbf r_t=(-s\sin t,s\cos t,1)$, so $\mathbf r_s\times\mathbf r_t=(\sin t,\,-\cos t,\,s)$.
> 2. **Integrand.** $\mathbf F=(s\cos t,\ s\sin t,\ t-2s\sin t)$. Dotting with the normal, the first two terms cancel, leaving $st-2s^2\sin t$.
> 3. **Integrate.** $\int_0^1\int_0^{2\pi}(st-2s^2\sin t)\,dt\,ds=\int_0^1 2\pi^2 s\,ds=\boxed{\pi^2}$ ✔ (SymPy).

> [!tip] Think geometrically first
> For $\mathbf F=\mathbf r$ on the sphere $r=a$: $d\mathbf S=\hat{\mathbf r}\,dA$, so $\mathbf F\cdot d\mathbf S=a\,dA$. Hence the flux is $a\cdot4\pi a^2=4\pi a^3$, with no parametrisation needed.
>
> The same idea on the upper hemisphere (PS10 Q2), using $\hat{\mathbf n}=\mathbf r/a$:
> - (a) $\mathbf F=y\,\mathbf j$ gives $\frac1a\iint y^2dA=\frac{2\pi a^3}{3}$, using $\iint y^2dA=\frac13\iint r^2dA$ by symmetry.
> - (b) $\mathbf F=-y\,\mathbf i+x\,\mathbf j+\mathbf k$ gives $\mathbf F\cdot\hat{\mathbf n}=z/a$, so the flux is $\frac1a\iint z\,dA=\frac1a\pi a^3=\pi a^2$.
> - (c) $\mathbf F=x^2\,\mathbf i+xy\,\mathbf j+xz\,\mathbf k$ gives $\mathbf F\cdot\hat{\mathbf n}=\frac{x(x^2+y^2+z^2)}{a}=ax$, whose integral is $0$ by symmetry.
>
> All three were checked by explicit parametrisation in SymPy ✔.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC3 - Line Integrals and Conservative Fields]] · Next: [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] (PS10)

## Sources
- Lectures 27–28; Lecture Notes §8.2.3–8.2.6. All results verified in SymPy.

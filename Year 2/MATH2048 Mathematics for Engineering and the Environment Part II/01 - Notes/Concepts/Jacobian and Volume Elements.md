---
title: "Jacobian and Volume Elements"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: concept
stream: "Block 5: Vector Calculus"
aliases: ["Jacobian", "Spherical polar volume element", "Cylindrical coordinates", "Change of variables"]
tags: [math2048, concept, vector-calculus, exam-prep]
status: complete
parent_lectures: ["[[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem]]"]
related_concepts: ["[[Divergence Theorem]]", "[[Flux Integrals]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture29_vector09.pdf"]
---

# Jacobian and Volume Elements

## Definition

> [!note] Definition
>
> $$dV=\left|\frac{\partial(x,y,z)}{\partial(s,t,u)}\right|ds\,dt\,du,\qquad \frac{\partial(x,y,z)}{\partial(s,t,u)}=\det\begin{pmatrix}x_s&x_t&x_u\\y_s&y_t&y_u\\z_s&z_t&z_u\end{pmatrix}.$$

## Explanation
| System | Map | $\lvert J\rvert$ | $dV$ |
|---|---|---|---|
| Cylindrical $(\rho,\phi,z)$ | $(\rho\cos\phi,\ \rho\sin\phi,\ z)$ | $\rho$ | $\rho\,d\rho\,d\phi\,dz$ |
| Spherical $(r,\theta,\phi)$ | $(r\sin\theta\cos\phi,\ r\sin\theta\sin\phi,\ r\cos\theta)$ | $r^2\sin\theta$ | $r^2\sin\theta\,dr\,d\theta\,d\phi$ |
| Polar (2D) | $(r\cos\theta,\ r\sin\theta)$ | $r$ | $r\,dr\,d\theta$ |

**Spherical derivation** (2025/26 B2c): expand along the $z$ row, $(\cos\theta,\ -r\sin\theta,\ 0)$. The result is $r^2\sin\theta\cos^2\theta+r^2\sin^3\theta=r^2\sin\theta$. The full working is in [[MATH2048 VC5 - Volume Integrals, the Divergence Theorem and Stokes' Theorem|VC5]].

**Useful results**:
- The volume of a sphere is $\frac43\pi a^3$.
- Over a hemisphere, $\iiint z\,dV=\frac{\pi a^4}{4}$.
- **Shifting the origin** (e.g. $z=z'+1$) has Jacobian $1$. It is a quick way to handle offset domains, as in 2025/26 B2(e).

## Examples
- Shell $1\leq r\leq2$ with a $\pi/3$ wedge removed: volume $70\pi/9$.
- Solid under $z=x^2+y^2$ inside $r=a$: volume $\pi a^4/2$.

## Related
- [[Divergence Theorem]] · [[Flux Integrals]]

## Sources
- Lecture 29; PS11

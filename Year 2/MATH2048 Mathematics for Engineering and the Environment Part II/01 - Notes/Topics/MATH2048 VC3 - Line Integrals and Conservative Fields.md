---
title: "MATH2048 VC3 - Line Integrals and Conservative Fields"
module: "MATH2048 Mathematics for Engineering and the Environment Part II"
type: topic
stream: "Block 5: Vector Calculus"
order: 17
tags:
  - math2048
  - vector-calculus
  - line-integrals
  - conservative-fields
aliases: ["MATH2048 Lecture 22", "MATH2048 Lecture 26", "Work integral", "Potential function", "Path independence"]
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: ["[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]"]
next_topics: ["[[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]"]
key_concepts: ["[[Line Integrals]]", "[[Conservative Vector Fields]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture21_vector01.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture22_vector02.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture26_vector06.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.2.1–8.2.2, §8.3.2–8.3.3)"]
---

# MATH2048 VC3 - Line Integrals and Conservative Fields

> [!abstract] Summary
> **Line integral** (work done by a force field along a path):
> $$\int_C\mathbf F\cdot d\mathbf r=\int_a^b\mathbf F(\mathbf r(t))\cdot\dot{\mathbf r}(t)\,dt .$$
> Substitute the parametrisation, take the dot product with the tangent, and do an ordinary integral. In general the result **depends on the path**.
>
> **Conservative fields** $\mathbf F=\nabla\phi$ are the exception: $\int_A^B\mathbf F\cdot d\mathbf r=\phi(B)-\phi(A)$. The test (in a simply connected region) is **$\nabla\times\mathbf F=\mathbf 0$**. You find $\phi$ by partial integration.
>
> Examined in 2025/26 B1 (15 marks): show a field is not conservative, then evaluate a line integral.

## Key Concepts
- [[Line Integrals]] · [[Conservative Vector Fields]] · [[Gradient and Directional Derivative]]

---

## 1. Definition and recipe (L21–22, Notes §8.2.1)
Split the path into small chords $\Delta\mathbf r_j$ and sum $\mathbf F_j\cdot\Delta\mathbf r_j$. In the limit this is **work**, the generalisation of $W=\mathbf F\cdot\overrightarrow{AB}$.

**Recipe**:
1. Parametrise the path: $\mathbf r(t)=(x(t),y(t),z(t))$ for $a\leq t\leq b$, with the correct direction from start to end.
2. Substitute to get $\mathbf F(\mathbf r(t))$.
3. Compute $\dot{\mathbf r}(t)$.
4. Integrate $\int_a^b\mathbf F\cdot\dot{\mathbf r}\,dt$.

**Independent of parametrisation**: if $\tilde{\mathbf r}(s)=\mathbf r(f(s))$ with $f$ increasing, the chain rule gives $d\tilde{\mathbf r}/ds=\dot{\mathbf r}f'(s)$, and substituting back returns the same integral. **Reversing the direction flips the sign.**

### Worked examples (Notes Ex. 1–2): the same endpoints $(0,0,0)\to(2,1,3)$
$\mathbf F=2xy\,\mathbf i+(x^2-z^2)\mathbf j-3xz^2\,\mathbf k$.

**(a) Along the curve $\mathbf r=(2t,t^3,3t^2)$.**
- $\mathbf F=(4t^4,\ 4t^2-9t^4,\ -54t^5)$ and $\dot{\mathbf r}=(2,3t^2,6t)$.
- $\mathbf F\cdot\dot{\mathbf r}=8t^4+12t^4-27t^6-324t^6=20t^4-351t^6$.
- $\int_0^1=4-\frac{351}{7}=\boxed{-\frac{323}{7}}$.

**(b) Along the straight line $\mathbf r=(2t,t,3t)$.**
- $\mathbf F=(4t^2,-5t^2,-54t^3)$ and $\dot{\mathbf r}=(2,1,3)$.
- $\mathbf F\cdot\dot{\mathbf r}=3t^2-162t^3$.
- $\int_0^1=1-\frac{162}{4}=\boxed{-\frac{79}{2}}$.

Different answers, so this field is **path dependent**, and indeed $\nabla\times\mathbf F=(2z,\ 3z^2,\ 0)\neq\mathbf 0$. Both values were checked in SymPy.

> [!warning] Errata in the notes' text
> The notes' Example 1b as printed reuses Example 2's integrand and gets $6$, and Example 1a's minus sign is lost. The values above are the correct ones.

**(c) $\mathbf F=\nabla(xy^2z)=(y^2z,\,2xyz,\,xy^2)$ along either path** gives $6=\phi(2,1,3)-\phi(0,0,0)$ ✔. The result is path independent.

## 2. Gradient fields: the fundamental theorem (Notes §8.2.1)
**Proposition**: $\displaystyle\int_C\nabla\phi\cdot d\mathbf r=\phi(\mathbf r_B)-\phi(\mathbf r_A)$.

**Proof**: along the curve,
$$\nabla\phi\cdot\dot{\mathbf r}=\phi_x\dot x+\phi_y\dot y+\phi_z\dot z=\frac{d}{dt}\phi(\mathbf r(t))$$
by the chain rule. So the integral is $\big[\phi(\mathbf r(t))\big]_{t_0}^{t_1}$. ∎

**Physics**: with $\mathbf F=-\nabla V$, the work done equals the loss of potential energy. Energy is conserved, which is where the name **conservative** comes from.

## 3. Four equivalent characterisations (simply connected $U$)
| | Condition |
|---|---|
| 1 | $\int_{C_1}\mathbf F\cdot d\mathbf r=\int_{C_2}\mathbf F\cdot d\mathbf r$ for any two paths from $A$ to $B$ (path independence) |
| 2 | $\oint_C\mathbf F\cdot d\mathbf r=0$ for every closed curve |
| 3 | $\mathbf F=\nabla\phi$ for some scalar potential $\phi$ |
| 4 | $\nabla\times\mathbf F=\mathbf 0$ (curl-free) |

**Why they are equivalent**:
- 1 ⇔ 2: split a closed loop into two paths from $A$ to $B$, one of them reversed.
- 1 ⇒ 3: define $\phi(\mathbf r)=\int_A^{\mathbf r}\mathbf F\cdot d\mathbf r$. Differentiating along a small step in $x$ gives $\phi_x=F_1$.
- 3 ⇒ 4: curl grad $=\mathbf 0$.
- 4 ⇒ 2: Stokes, $\oint=\iint(\nabla\times\mathbf F)\cdot d\mathbf S=0$. This needs a spanning surface, which is where **simply connected** matters.

> [!warning] Simply connected is essential
> $\mathbf F=\dfrac{-y\,\mathbf i+x\,\mathbf j}{x^2+y^2}$ has $\nabla\times\mathbf F=\mathbf 0$ everywhere except the $z$-axis. Yet around the unit circle $\oint\mathbf F\cdot d\mathbf r=2\pi\neq0$, because the region with the axis removed has a hole.
>
> This is the point vortex from potential flow ([[Kelvin's Circulation Theorem]]).

## 4. Finding a potential (L26, Notes §8.3.3)
**Example**: $\mathbf F=(2xy+\cos2y)\,\mathbf i+(x^2+2y-2x\sin2y)\,\mathbf j$.
1. **Check it is conservative.** $(\nabla\times\mathbf F)_z=\partial_x(x^2+2y-2x\sin2y)-\partial_y(2xy+\cos2y)=2x-2\sin2y-2x+2\sin2y=0$ ✔.
2. **Integrate $\phi_x=F_1$ in $x$.** $\phi=x^2y+x\cos2y+f(y)$, where the "constant" can depend on $y$.
3. **Differentiate in $y$ and compare with $F_2$.** $\phi_y=x^2-2x\sin2y+f'(y)=F_2$, so $f'(y)=2y$ and $f=y^2+c$.
4. **Result.**
$$\phi=x^2y+x\cos2y+y^2+c .$$

In 3D, repeat the pattern: integrate in $x$, match the $y$ derivative, then match the $z$ derivative. Each "constant" is a function of the variables not yet integrated.

## 5. Exam 2025/26 B1: $\mathbf F=xyz\,\mathbf i+z^2\mathbf j+y^2\mathbf k$
**(a) Not conservative.**
$$\nabla\times\mathbf F=(2y-2z)\,\mathbf i+xy\,\mathbf j-xz\,\mathbf k\neq\mathbf 0 .$$
For example, at $(1,1,0)$ it equals $(2,1,0)$.

**(b) Along $\mathbf r=\big(3(t+1),\,t,\,t^2\big)$ from $t=0$ to $t=1$.** The full working is in [[MATH2048 Past Paper Solutions]]. The path cannot be shortcut, because the field is not conservative.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]] · Next: [[MATH2048 VC4 - Surfaces, Surface Area and Flux Integrals]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] (PS8 Q7) · [[MATH2048 Past Paper Solutions]]

## Sources
- Lectures 21–22, 26; Lecture Notes §8.2.1–8.2.2, §8.3.2–8.3.3. All integrals verified in SymPy.

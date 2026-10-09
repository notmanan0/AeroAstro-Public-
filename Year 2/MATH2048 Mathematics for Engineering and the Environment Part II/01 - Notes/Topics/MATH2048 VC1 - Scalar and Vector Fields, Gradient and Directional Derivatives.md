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
date: 2026-09-24
status: complete
parent: ["[[MATH2048 Mathematics for Engineering and the Environment Part II Hub]]"]
prerequisites: []
next_topics: ["[[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]"]
key_concepts: ["[[Gradient and Directional Derivative]]"]
tutorial_sheets: ["[[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]]"]
sources: ["02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture21_vector01.pdf", "02 - Sources/Lectures & Problem Sheets/Vector Calculus/Lecture23_vector03.pdf", "02 - Sources/Lectures & Problem Sheets/LectureNotesMATH2048.pdf (§8.1.1–8.1.7)"]
---

# MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives

> [!abstract] Summary
> A **scalar field** $\phi(x,y,z)$ assigns a number to each point (temperature, density, potential). A **vector field** $\mathbf F$ assigns a vector (force, velocity).
>
> The **gradient** $\nabla\phi=(\phi_x,\phi_y,\phi_z)$ packs all the rates of change of $\phi$ into one vector:
> - **directional derivative**: $\nabla_{\hat{\mathbf v}}\phi=\hat{\mathbf v}\cdot\nabla\phi$;
> - **steepest ascent**: $\nabla\phi$ points uphill, and the maximum rate of increase is $|\nabla\phi|$;
> - **level surfaces**: $\nabla\phi$ is **normal** to the surface $\phi=\text{const}$. This gives tangent planes and angles between surfaces.

## Key Concepts
- [[Gradient and Directional Derivative]] · [[Line Integrals]] (next the fields get integrated)

---

## 1. Vector algebra review (L21)
- **Components and length**: $\mathbf a=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$ and $|\mathbf a|=\sqrt{a_1^2+a_2^2+a_3^2}$.
- **Dot product**: $\mathbf a\cdot\mathbf b=a_1b_1+a_2b_2+a_3b_3=|\mathbf a||\mathbf b|\cos\theta$.
  - $\mathbf a\perp\mathbf b\iff\mathbf a\cdot\mathbf b=0$.
  - The projection of $\mathbf a$ onto $\mathbf b$ is $\mathbf a\cdot\hat{\mathbf b}$.
- **Cross product**: $\mathbf a\times\mathbf b=|\mathbf a||\mathbf b|\sin\theta\,\hat{\mathbf n}$, with $\hat{\mathbf n}$ given by the right-hand rule.
$$\mathbf a\times\mathbf b=\begin{vmatrix}\mathbf i&\mathbf j&\mathbf k\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}=(a_2b_3-a_3b_2)\mathbf i+(a_3b_1-a_1b_3)\mathbf j+(a_1b_2-a_2b_1)\mathbf k .$$
  - It is **anti-commutative**: $\mathbf a\times\mathbf b=-\mathbf b\times\mathbf a$.
  - $\mathbf a\times\mathbf a=\mathbf 0$.
  - $|\mathbf a\times\mathbf b|$ is the area of the parallelogram spanned by $\mathbf a$ and $\mathbf b$. This is why it appears in $dA$ (VC4).

## 2. Curves (L21)
- A **parametric curve** is $\mathbf r(t)=x(t)\mathbf i+y(t)\mathbf j+z(t)\mathbf k$ for $a\leq t\leq b$.
- Its **tangent vector** is $\dfrac{d\mathbf r}{dt}=\dot x\mathbf i+\dot y\mathbf j+\dot z\mathbf k$.
- The same geometric path has many parametrisations. Choose the most convenient: lines, circles $\mathbf r=(a\cos t,a\sin t)$, helices.

## 3. Directional derivative (L23, Notes §8.1.4)
**Definition**: $\nabla_{\mathbf v}\phi(\mathbf r_0)=\lim_{t\to0}\dfrac{\phi(\mathbf r_0+t\mathbf v)-\phi(\mathbf r_0)}{t}$.

**Derivation of the working formula**:
1. Let $f(t)=\phi(\mathbf r_0+t\mathbf v)$. Then the directional derivative is $f'(0)$.
2. The chain rule, with $x=r_1+tv_1$ and so on, gives
$$f'(0)=v_1\phi_x+v_2\phi_y+v_3\phi_z=\mathbf v\cdot\nabla\phi .$$

$$\boxed{\nabla\phi=\frac{\partial\phi}{\partial x}\mathbf i+\frac{\partial\phi}{\partial y}\mathbf j+\frac{\partial\phi}{\partial z}\mathbf k,\qquad \text{rate of change in direction }\hat{\mathbf v}=\hat{\mathbf v}\cdot\nabla\phi}$$

> [!warning] Normalise $\mathbf v$ first
> For the rate of change *per unit distance*, use $\hat{\mathbf v}=\mathbf v/|\mathbf v|$. For example, with $\mathbf v=2\mathbf i+2\mathbf j+\mathbf k$, divide by $3$.

## 4. Steepest ascent (Theorem 1)
$\hat{\mathbf v}\cdot\nabla\phi=|\nabla\phi|\cos\theta$, which lies between $-|\nabla\phi|$ and $|\nabla\phi|$:
- the **maximum** is at $\theta=0$, i.e. $\hat{\mathbf v}\parallel\nabla\phi$, with rate $|\nabla\phi|$;
- the **minimum** is along $-\nabla\phi$, the steepest descent.

## 5. Normal to level surfaces (Theorem 2)
Let $\mathbf v$ be tangent to the surface $\phi=c_0$ at $P$. Moving along the surface, $\phi$ does not change, so $\mathbf v\cdot\nabla\phi=0$ for every tangent $\mathbf v$. Therefore
$$\nabla\phi\ \text{is normal to }\phi=\text{const}.$$
This gives the geometric definition $\nabla\phi=\dfrac{\partial\phi}{\partial n}\hat{\mathbf n}$.

![[m2048_vc_gradient_level_curves.png|520]]

> [!example] Notes Example 1: $\phi=r=|\mathbf r|$
> $\partial_x(x^2+y^2+z^2)^{1/2}=x/r$, and similarly for $y$ and $z$. So $\nabla r=\mathbf r/r=\hat{\mathbf r}$.
> More generally, for any radial field, $\nabla f(r)=f'(r)\,\hat{\mathbf r}$.

> [!example] Tangent plane: $x^3y-yz^2+z^5=9$ at $P(3,-1,2)$
> $\nabla\phi=(3x^2y,\ x^3-z^2,\ 5z^4-2yz)$, which at $P$ is $(-27,23,84)$.
> The tangent plane is $\mathbf n\cdot(\mathbf r-\mathbf r_0)=0$, i.e. $-27x+23y+84z=64$.

> [!example] PS8 Q4: angle between surfaces at $(2,-1,2)$
> - The normal to $x^2+y^2+z^2=9$ is $(2x,2y,2z)=(4,-2,4)$.
> - Write $z=x^2+y^2-3$ as $g=x^2+y^2-z=3$. Its normal is $(2x,2y,-1)=(4,-2,-1)$.
>
> $$\cos\theta=\frac{16+4-4}{6\sqrt{21}}=\frac{8\sqrt{21}}{63},\qquad\theta\approx54.4^\circ .$$

**Properties**:
- Linearity: $\nabla(\phi+\psi)=\nabla\phi+\nabla\psi$.
- Product (Leibniz) rule: $\nabla(\phi\psi)=\phi\nabla\psi+\psi\nabla\phi$.

## Links
- Parent: [[MATH2048 Mathematics for Engineering and the Environment Part II Hub]] · Previous: [[MATH2048 PDE5 - Laplace's Equation]] · Next: [[MATH2048 VC2 - Divergence, Curl, Laplacian and Vector Identities]]
- Practice: [[MATH2048 Problem Sheets 8-11 Solutions - Vector Calculus]] (PS8 Q1–4, Q6)

## Sources
- Lectures 21, 23; Lecture Notes §8.1. All examples verified in SymPy.

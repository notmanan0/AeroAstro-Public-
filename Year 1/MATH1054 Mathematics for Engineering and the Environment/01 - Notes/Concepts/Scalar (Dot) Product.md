---
title: "Scalar (Dot) Product"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Dot product", "Scalar product", "Inner product"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M14 - Vectors I]]"]
related_concepts: ["[[Vector Algebra and Components]]", "[[Vector (Cross) Product]]", "[[Work-Energy Principle]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.2.8", "MATH1054 Module Booklet, Module 14"]
---

# Scalar (Dot) Product

The scalar product of two vectors is the number $\mathbf a\cdot\mathbf b=|\mathbf a||\mathbf b|\cos\theta$, where $\theta\in[0,\pi]$ is the angle between them; in components it is $a_1b_1+a_2b_2+a_3b_3$.

The two forms agree by the cosine rule. In the triangle with sides $\mathbf a$, $\mathbf b$ and $\mathbf a-\mathbf b$, $|\mathbf a-\mathbf b|^2=|\mathbf a|^2+|\mathbf b|^2-2|\mathbf a||\mathbf b|\cos\theta$. Writing the left side as $\sum(a_i-b_i)^2$ and expanding, the squares cancel against the right side and leave $-2\sum a_ib_i=-2|\mathbf a||\mathbf b|\cos\theta$. The same result follows by expanding $(a_1\mathbf i+a_2\mathbf j+a_3\mathbf k)\cdot(b_1\mathbf i+b_2\mathbf j+b_3\mathbf k)$ with $\mathbf i\cdot\mathbf i=\mathbf j\cdot\mathbf j=\mathbf k\cdot\mathbf k=1$ and $\mathbf i\cdot\mathbf j=\mathbf j\cdot\mathbf k=\mathbf k\cdot\mathbf i=0$: only the three matching terms survive.

From the component form the product is commutative, takes scalars out, distributes over addition, and gives $\mathbf a\cdot\mathbf a=|\mathbf a|^2$. Its uses all come from the $\cos\theta$:

- the angle between two vectors, $\cos\theta=\dfrac{\mathbf a\cdot\mathbf b}{|\mathbf a||\mathbf b|}$;
- the perpendicular test, $\mathbf a\cdot\mathbf b=0$ with neither vector zero;
- the component (resolved part) of $\mathbf F$ along a direction $\mathbf u$, $\mathbf F\cdot\hat{\mathbf u}=|\mathbf F|\cos\theta$;
- the work done by a constant force through a displacement $\mathbf d$, $W=\mathbf F\cdot\mathbf d$, the integrand of $\int\mathbf F\cdot d\mathbf r$ in the [[Work-Energy Principle]].

For $(1,2,3)$ and $(2,0,4)$ (James Example 4.18), $\cos\theta=\frac{2+0+12}{\sqrt{14}\sqrt{20}}=\frac{14}{\sqrt{280}}=0.8367$, so $\theta=33.2°$. The force $(3,-2,5)$ moving a particle from $(1,4,-1)$ to $(-2,3,1)$ (Example 4.22) has displacement $(-3,-1,2)$ and does work $-9+2+10=3$ units. With $\mathbf u=(4,0,-2)$ and $\mathbf v=(3,1,-1)$ (Exercise 28(c)), $\mathbf u+\lambda\mathbf k\perp\mathbf v-\lambda\mathbf i$ requires $(4,0,\lambda-2)\cdot(3-\lambda,1,-1)=14-5\lambda=0$, so $\lambda=\frac{14}5$.

The common trap is cancelling. From $\mathbf a\cdot\mathbf b=\mathbf a\cdot\mathbf c$ it follows only that $\mathbf a\cdot(\mathbf b-\mathbf c)=0$, so $\mathbf a$ may just be perpendicular to $\mathbf b-\mathbf c$: $(1,1,1)$ dotted with $(3,2,-3)$ and with $(-1,4,-1)$ gives 2 both times. A second slip is forgetting to divide by $|\mathbf u|$ when the direction for a component is not a unit vector.

## Related

- Topics: [[MATH1054 M14 - Vectors I]] (derivations and worked examples) · [[FEEG1002 D3 - Work, Energy and Power]] · [[MATH2048 VC1 - Scalar and Vector Fields, Gradient and Directional Derivatives]] (directional derivative $\hat{\mathbf n}\cdot\nabla f$)
- Concepts: [[Vector Algebra and Components]] · [[Vector (Cross) Product]] · [[Work-Energy Principle]] · [[Orthogonality of Trigonometric Functions]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §4.2.8; MATH1054 Module Booklet, Module 14

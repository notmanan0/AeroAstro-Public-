---
title: "Equations of Lines and Planes"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Vector equation of a line", "Equation of a plane", "Skew lines", "Distance point to plane"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M15 - Vectors II]]"]
related_concepts: ["[[Vector (Cross) Product]]", "[[Scalar Triple Product]]", "[[Vector Algebra and Components]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.3", "MATH1054 Module Booklet, Module 15"]
---

# Equations of Lines and Planes

A straight line through the point with position vector $\mathbf a$ in the direction $\mathbf d$ is the set of points $\mathbf r=\mathbf a+t\mathbf d$, $t\in\mathbb R$; a plane through $\mathbf a$ with normal $\mathbf n$ is the set of points with $\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n$.

The line equation is the triangle law: to reach a point P of the line, go to A and then a multiple $t$ of the direction. Through two points A and B the direction is $\mathbf b-\mathbf a$, which gives $\mathbf r=(1-t)\mathbf a+t\mathbf b$. Eliminating $t$ from the three components gives the Cartesian form

$$
\frac{x-a_1}{d_1}=\frac{y-a_2}{d_2}=\frac{z-a_3}{d_3},
$$

where a zero denominator means the matching numerator is zero. The plane equation says that the displacement $\mathbf r-\mathbf a$ from a known point lies in the plane and so is perpendicular to the normal: $(\mathbf r-\mathbf a)\cdot\mathbf n=0$, i.e. $\mathbf r\cdot\mathbf n=\mathbf a\cdot\mathbf n=p$, or $n_1x+n_2y+n_3z=p$ in components. With a unit normal, $p$ is the perpendicular distance from the origin. A plane through three points has normal $(\mathbf b-\mathbf a)\times(\mathbf c-\mathbf a)$.

Every intersection reduces to solving these equations together. Two lines are equated component by component, which gives three equations in two parameters: solve two and check the third, and if the third fails for non-parallel directions the lines are skew. A line meets a plane where $(\mathbf a+t\mathbf d)\cdot\mathbf n=p$, so $t=(p-\mathbf a\cdot\mathbf n)/(\mathbf d\cdot\mathbf n)$ unless $\mathbf d\cdot\mathbf n=0$ (the line is parallel to the plane). Two planes meet in a line with direction $\mathbf n_1\times\mathbf n_2$, through any point found by fixing one coordinate.

Every distance is the component of a joining vector along a unit normal. For a point $\mathbf p_0$ and the plane $\mathbf r\cdot\mathbf n=p$, choosing any point $\mathbf q$ of the plane gives

$$
D=|(\mathbf p_0-\mathbf q)\cdot\hat{\mathbf n}|=\frac{|\mathbf p_0\cdot\mathbf n-p|}{|\mathbf n|}=\frac{|n_1x_0+n_2y_0+n_3z_0-p|}{|\mathbf n|}.
$$

For skew lines the normal common to both is $\mathbf d_1\times\mathbf d_2$, and the same projection of $\mathbf a_2-\mathbf a_1$ gives

$$
D=\frac{|(\mathbf a_2-\mathbf a_1)\cdot(\mathbf d_1\times\mathbf d_2)|}{|\mathbf d_1\times\mathbf d_2|},
$$

a [[Scalar Triple Product|triple product]] over a length. It is the length of the common perpendicular, whose feet P and Q satisfy $\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_1=\overrightarrow{\mathrm{PQ}}\cdot\mathbf d_2=0$.

For example, the lines $(0,9,2)+t_1(3,-1,1)$ and $(-6,-5,10)+t_2(-3,2,4)$ have $\mathbf d_1\times\mathbf d_2=(-6,-15,3)\propto(2,5,-1)$, so $D=|(-6,-14,8)\cdot(2,5,-1)|/\sqrt{30}=90/\sqrt{30}=3\sqrt{30}\approx16.43$; the feet are $(3,8,3)$ and $(-3,-7,6)$ and the common perpendicular is $\mathbf r=(3,8,3)+\mu(2,5,-1)$ (James Example 4.42). The planes $x+y+z=5$ and $4x+y+2z=15$ meet in the line $\mathbf r=(3,1,1)+t(1,2,-3)$ (James Example 4.47), and the point $(2,-3,4)$ is at distance $|2-6+8-13|/3=3$ from $x+2y+2z=13$ (James Example 4.48).

The common trap is equating two lines, solving two of the three component equations and stopping: two equations in two unknowns usually have a solution, so skew lines then appear to meet. The other is using the same parameter letter for both lines, which forces them to pass through the matching points at the same parameter value.

## Related

- Topics: [[MATH1054 M15 - Vectors II]] (derivations and all work-scheme examples) · [[MATH1054 M14 - Vectors I]] · [[MATH1054 M17 - Matrices II]] (three planes as a linear system)
- Concepts: [[Vector (Cross) Product]] · [[Scalar (Dot) Product]] · [[Scalar Triple Product]] · [[Vector Algebra and Components]] · [[Rank and Consistency of Linear Systems]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §4.3.1 and §4.3.3; MATH1054 Module Booklet, Module 15 work scheme, items 5–8

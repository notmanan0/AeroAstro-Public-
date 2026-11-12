---
title: "Vector Algebra and Components"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 4: Vectors and Matrices"
aliases: ["Vectors", "Direction cosines", "Unit vector", "Position vector"]
tags: [math1054, concept, vectors]
status: complete
parent_lectures: ["[[MATH1054 M14 - Vectors I]]"]
related_concepts: ["[[Scalar (Dot) Product]]", "[[Vector (Cross) Product]]", "[[Equations of Lines and Planes]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §4.2", "MATH1054 Module Booklet, Module 14"]
---

# Vector Algebra and Components

A vector is a quantity with magnitude and direction that adds by the parallelogram rule; in right-handed Cartesian axes it is written by its components as $\mathbf a=(a_1,a_2,a_3)=a_1\mathbf i+a_2\mathbf j+a_3\mathbf k$, where $\mathbf i$, $\mathbf j$, $\mathbf k$ are unit vectors along the axes.

The components come from the triangle law applied twice: from O along $x$ to $(x,0,0)$, then along $y$ to $(x,y,0)$, then along $z$ to P gives $\overrightarrow{\mathrm{OP}}=x\mathbf i+y\mathbf j+z\mathbf k$. Projecting the parallelogram rule onto each axis shows that vectors add, subtract and scale component by component, $\mathbf a\pm\mathbf b=(a_1\pm b_1,\,a_2\pm b_2,\,a_3\pm b_3)$ and $\lambda\mathbf a=(\lambda a_1,\lambda a_2,\lambda a_3)$, so all the geometry of the triangle and polygon laws becomes arithmetic. Two applications of Pythagoras give the magnitude, $|\mathbf a|=\sqrt{a_1^2+a_2^2+a_3^2}$, and dividing by it gives the unit vector $\hat{\mathbf a}=\mathbf a/|\mathbf a|$.

The **direction cosines** $(l,m,n)$ are the cosines of the angles the vector makes with the three axes. Since $\cos\alpha=a_1/|\mathbf a|$ and so on, they are exactly the components of $\hat{\mathbf a}$, and

$$
l^2+m^2+n^2=\frac{a_1^2+a_2^2+a_3^2}{|\mathbf a|^2}=1,
$$

so any two of the angles fix the third up to sign.

Position vectors turn geometry into subtraction. If A and B have position vectors $\mathbf a$ and $\mathbf b$, then $\overrightarrow{\mathrm{AB}}=\mathbf b-\mathbf a$, end minus start, and a closed loop of vectors drawn head to tail sums to $\mathbf0$. Three points P, Q, R are collinear when $\overrightarrow{\mathrm{PQ}}=\lambda\overrightarrow{\mathrm{QR}}$, since the two vectors are then parallel and share Q. The resultant of several forces on a particle is their vector sum, and the equilibrant is its negative. For two moving points, $\mathbf r_{B/A}=\mathbf r_B-\mathbf r_A$ differentiates to the relative velocity: the velocity of B seen by A is $\mathbf v_B-\mathbf v_A$.

For $\mathrm P(2,-1,3)$ (James Example 4.1), $|\mathrm{OP}|=\sqrt{4+1+9}=\sqrt{14}\approx3.742$ and the direction cosines are $\frac1{\sqrt{14}}(2,-1,3)\approx(0.535,-0.267,0.802)$. For an aircraft flying at 400 knots that must track due west in a 50-knot NW wind (Example 4.7), the wind is $(25\sqrt2,-25\sqrt2)$ with $\mathbf i$ east, cancelling its southward part needs $400\sin\alpha=25\sqrt2$, so the heading is $\alpha=5.07°$ north of west, and the ground speed is $400\cos\alpha-25\sqrt2\approx363$ knots.

The common traps are direction conventions. A force "of magnitude $F$ in the direction $\mathbf d$" is $F\,\mathbf d/|\mathbf d|$, not $F\mathbf d$; a wind is named by where it comes from, so a NW wind blows towards the south-east; and $\overrightarrow{\mathrm{AB}}$ is $\mathbf b-\mathbf a$, not $\mathbf a-\mathbf b$.

## Related

- Topics: [[MATH1054 M14 - Vectors I]] (derivations and worked examples) · [[MATH1054 M15 - Vectors II]]
- Concepts: [[Scalar (Dot) Product]] · [[Vector (Cross) Product]] · [[Equations of Lines and Planes]] · [[Relative Velocity Equation for Rigid Bodies]] · [[Direction Cosine Matrix]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §4.2.1–4.2.5; MATH1054 Module Booklet, Module 14

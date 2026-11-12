---
title: "Centroids and Solids of Revolution"
module: "MATH1054 Mathematics for Engineering and the Environment"
type: concept
stream: "Block 1: Calculus"
aliases: ["Centroid", "Volume of revolution", "Centre of gravity", "Surface of revolution", "Arc length"]
tags: [math1054, concept, applications-of-integration]
status: complete
parent_lectures: ["[[MATH1054 M09 - Integration II]]"]
related_concepts: ["[[Integration by Substitution]]", "[[RMS Value]]", "[[First Moment of Area]]", "[[Double Integrals and Change of Order]]"]
sources: ["James, Modern Engineering Mathematics (6th ed.) §8.9", "02 - Sources/Formulae & Reference/Integration Formulae.md"]
---

# Centroids and Solids of Revolution

The centroid of a plane region is the point $(\bar x,\bar y)$ at which its whole area, concentrated, has the same first moments about the axes as the region itself; a solid of revolution is the solid swept out when a plane region is rotated a full turn about an axis, here the $x$-axis.

Every formula comes from cutting the region under $y=f(x)\geq0$, $a\leq x\leq b$, into vertical strips of width $\delta x$ and adding what each strip contributes. A strip of height $y$ has area $y\,\delta x$ and its own centroid at $(x,\,y/2)$, so its moments about the $y$- and $x$-axes are $xy\,\delta x$ and $(y\,\delta x)(y/2)=\frac12y^2\,\delta x$. Rotated about the $x$-axis, the same strip sweeps a disc of radius $y$ and volume $\pi y^2\,\delta x$ whose centre lies on the axis at $x$. Summing and letting $\delta x\to0$:

$$
A=\int_a^by\,\mathrm dx,\qquad\bar x=\frac1A\int_a^bxy\,\mathrm dx,\qquad\bar y=\frac1{2A}\int_a^by^2\,\mathrm dx,
$$

$$
V=\pi\int_a^by^2\,\mathrm dx,\qquad\bar X=\frac\pi V\int_a^bxy^2\,\mathrm dx,\qquad\bar Y=\bar Z=0.
$$

The factor $\frac12$ in $\bar y$ is the strip's centroid sitting at half its height, and $\bar Y=\bar Z=0$ is the symmetry of a solid of revolution about its axis. The centre of gravity of the solid equals its volume centroid when the density is uniform. Between two curves $y_l\leq y\leq y_u$, each strip has height $y_u-y_l$ and centroid at mid-height $\frac12(y_u+y_l)$, so its $x$-axis moment is $\frac12(y_u^2-y_l^2)\,\delta x$, and it sweeps a washer of volume $\pi(y_u^2-y_l^2)\,\delta x$.

The same strip picture gives the other applications in the module. The mean value of $f$ on $[a,b]$ is $\frac1{b-a}\int_a^bf\,\mathrm dx$, the height of the rectangle with the same area, and the RMS value is $\sqrt{\frac1{b-a}\int_a^bf^2\,\mathrm dx}$ ([[RMS Value]]). An element of curve is the hypotenuse $\delta s=\sqrt{\delta x^2+\delta y^2}$, so the arc length is $\int_a^b\sqrt{1+y'^2}\,\mathrm dx$, and rotating $\delta s$ at radius $y$ sweeps a band of area $2\pi y\,\delta s$, so the surface of revolution is $2\pi\int_a^by\sqrt{1+y'^2}\,\mathrm dx$.

For the region under $y=\sqrt{x-2}$ on $[2,5]$ (James Example 8.65), $A=2\sqrt3$, $\int_2^5xy\,\mathrm dx=\frac{38\sqrt3}5$ and $\int_2^5y^2\,\mathrm dx=\frac92$, so the area centroid is $\big(\frac{19}5,\frac{3\sqrt3}8\big)\approx(3.8,\ 0.650)$. The solid has $V=\frac{9\pi}2$ and $\int_2^5xy^2\,\mathrm dx=18$, so its centre of gravity is at $\bar X=4$, i.e. $(4,0,0)$. Two more from the module: the paraboloid reflector from $y=\sqrt x$ on $[0,1]$ has surface area $\frac\pi6\big(5\sqrt5-1\big)\approx5.330$ (Example 8.68), and the region between $y^2=4x$ and $y=2x$ has area centroid $\big(\frac25,1\big)$ and volume centroid $\bar X=\frac12$ (Exercise 135). All were checked with SymPy.

The trap is to treat the solid's centre of gravity as the rotated area centroid. The area weights each strip by $y$, the solid by $y^2$, so the wide end counts for more in the solid: $\bar x=3.8$ for the area but $\bar X=4$ for the solid above. A second trap is the washer: its volume is $\pi(y_u^2-y_l^2)\,\delta x$, not $\pi(y_u-y_l)^2\,\delta x$. Symmetry, a sketch and a dimension check ($A$ in length squared, $V$ in length cubed, centroids in length) catch most remaining slips.

![[m1054_centroid_regions.png|800]]

## Related

- Topics: [[MATH1054 M09 - Integration II]] (derivations of every formula, Examples 8.65–8.69, Exercises 131, 132, 135); [[MATH1054 M11 - Integration IV]] (the same centroids as double integrals)
- Concepts: [[Integration by Substitution]] · [[RMS Value]] · [[First Moment of Area]] · [[Double Integrals and Change of Order]] · [[Mass Moment of Inertia and Radius of Gyration]]
- Sources: James, *Modern Engineering Mathematics* (6th ed.) §8.9.1–8.9.6; MATH1054 Module Booklet, Module 9; [[Integration Formulae]].

---
title: "SESA2028 Structures Tutorial 1 - Energy Methods Solutions"
module: "SESA2028 Aerospace Materials & Structures"
type: tutorial-solution
stream: "Structures"
order: 1
tags: [sesa2028, structures, tutorial, energy-methods]
status: complete
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
topics: ["[[SESA2028 S7 - Strain Energy and Conservation of Energy]]", "[[SESA2028 S8 - Virtual Work and Castigliano Theorems]]"]
sources: ["02 - Sources/SESA2028 green coursework book.pdf, pp. 41-42"]
---

# SESA2028 Structures Tutorial 1 - Energy Methods Solutions

## Q1 - Simply supported beam with a point moment

The beam has $L=3$ m, an applied moment $M_0=9$ kNm at $a=2$ m, and $EI=30\ \mathrm{kN\,m^2}$. Moment equilibrium gives equal and opposite support reactions of magnitude $M_0/L=3$ kN.

Using a coordinate from the left support, the bending moment may be written

$$
M(x)=
\begin{cases}
-M_0x/L,&0\le x<a,\\[2mm]
M_0(1-x/L),&a<x\le L.
\end{cases}
$$

The signs depend on the sketch convention, but they disappear from $M^2$:

$$
U=\int_0^L\frac{M^2}{2EI}\,dx
=\frac{M_0^2}{2EI}
\left[
\int_0^a\frac{x^2}{L^2}\,dx+
\int_a^L\left(1-\frac{x}{L}\right)^2dx
\right].
$$

Hence

$$
U=\frac{M_0^2}{6EIL^2}\left[a^3+(L-a)^3\right].
$$

The rotation at the point where $M_0$ acts is its work-conjugate displacement:

$$
\theta_B=\frac{\partial U}{\partial M_0}
=\frac{M_0}{3EIL^2}\left[a^3+(L-a)^3\right].
$$

With $L=3$ m and $a=2$ m,

$$
\theta_B=\frac{9}{3(30)(3^2)}(2^3+1^3)
=\boxed{0.100\ \mathrm{rad}}.
$$

The direction follows the applied moment.

## Q2 - Quarter-circular cantilever

Let $\phi$ run from the free end ($0$) to the clamp ($\pi/2$), with $ds=R\,d\phi$. A horizontal force $F$ produces

$$
M(\phi)=FR\sin\phi.
$$

### Horizontal displacement

The bending energy is

$$
U=\int_0^{\pi/2}\frac{F^2R^2\sin^2\phi}{2EI}R\,d\phi
=\frac{F^2R^3}{2EI}\left(\frac\pi4\right)
=\frac{\pi F^2R^3}{8EI}.
$$

Castigliano gives

$$
u_x=\frac{\partial U}{\partial F}
=\boxed{\frac{\pi FR^3}{4EI}}.
$$

### Vertical displacement

Apply a downward unit virtual load at the free end. Its moment at the cut is

$$
m_y(\phi)=-R(1-\cos\phi).
$$

Then

$$
u_y=\int_0^{\pi/2}\frac{Mm_y}{EI}R\,d\phi
=-\frac{FR^3}{EI}\int_0^{\pi/2}\sin\phi(1-\cos\phi)\,d\phi.
$$

The integral equals $1/2$, so

$$
u_y=\boxed{-\frac{FR^3}{2EI}}.
$$

The negative sign says the displacement is opposite to the positive $y$ direction chosen in the question.

## Q3 - L-shaped cantilever

The vertical leg has length $L/4$ and carries the horizontal tip force $F$. Neglecting axial extension as intended by the question, there are two bending contributions to the horizontal tip displacement.

### Bending of the vertical leg

It behaves as a cantilever of length $L/4$:

$$
u_1=\frac{F(L/4)^3}{3EI}=\frac{FL^3}{192EI}.
$$

### Rotation of the horizontal leg

The vertical leg applies a constant end moment $F(L/4)$ to the horizontal member. Its end rotation is

$$
\theta=\frac{[F(L/4)]L}{EI}=\frac{FL^2}{4EI}.
$$

That rotation moves point A horizontally by

$$
u_2=\theta\frac L4=\frac{FL^3}{16EI}.
$$

Therefore

$$
u_x=u_1+u_2
=\left(\frac1{192}+\frac{12}{192}\right)\frac{FL^3}{EI}
=\boxed{\frac{13FL^3}{192EI}}.
$$

## Q4 - Slope and displacement at B

Take $x$ from A. Moment equilibrium gives $R_A=-1$ kN and $R_C=6$ kN. The bending-moment field is

$$
M(x)=
\begin{cases}
14-x,&0\le x\le2,\\
24-6x,&2\le x\le4,\\
0,&4\le x\le7,
\end{cases}
\qquad [M\text{ in kNm},\ x\text{ in m}].
$$

With $E=200$ GPa and $I=60\times10^6\ \mathrm{mm^4}$,

$$
EI=12{,}000\ \mathrm{kN\,m^2}.
$$

Integrating $EIv''=M$ on the first two spans gives

$$
EIv_1'=14x-\frac{x^2}{2}+C_1,\qquad
EIv_1=7x^2-\frac{x^3}{6}+C_1x,
$$

$$
EIv_2'=24x-3x^2+C_3,\qquad
EIv_2=12x^2-x^3+C_3x+C_4.
$$

Use $v(0)=0$, continuity of $v$ and $v'$ at $x=2$, and $v(4)=0$. This gives

$$
C_1=-\frac{71}{3},\qquad C_3=-\frac{101}{3},\qquad C_4=\frac{20}{3}.
$$

At B, $x=2$ m:

$$
\theta_B=v_1'(2)=\frac{7/3}{12{,}000}
=\boxed{1.94\times10^{-4}\ \mathrm{rad}},
$$

$$
v_B=v_1(2)=\frac{-62/3}{12{,}000}
=-1.72\times10^{-3}\ \mathrm m.
$$

Thus the displacement magnitude is

$$
\boxed{|v_B|=1.72\ \mathrm{mm}}.
$$

The negative sign is only the consequence of the selected positive-deflection direction.


---
title: "FEEG1002 A5 - Beam Deflection and Macaulay's Method"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 5
tags: [feeg1002, statics, beams, deflection, double-integration, macaulay, singularity-functions]
aliases: ["Statics 1 Lecture 9", "Statics 1 Lecture 10", "Beam deflection", "Double integration method", "Macaulay brackets"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 9 (25 Nov 2024, ll. 17–848: moment–curvature, sign convention, double integration, simply supported beam with a UDL and with an off-centre point load). Lecture 10 (Macaulay's method) was released as three recorded videos with no transcript; its content is written from deck 10 in full and the recap in Lecture 11 (ll. 13–93)"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]", "[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
next_topics: ["[[FEEG1002 A6 - Statically Indeterminate Beams]]"]
key_concepts: ["[[Macaulay's Method]]", "[[Standard Beam Deflections]]", "[[Moment Curvature Relation]]", "[[Elastic Curve]]", "[[Heaviside Step Function]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 09 - Beams, Deflection.pdf"
  - "02 - Sources/Statics 1/Lectures/Lecture 10 - Macaulay's Method.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 9 - Sttaics 1 - Beams, Deflection - November 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 11 - Statics 1 - Statically indeterminate beams - December 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 05 - Beam Deflection and Statically Indeterminate Beams - Solutions.pdf"
---

# FEEG1002 A5 - Beam Deflection and Macaulay's Method

> [!abstract] Summary
> Engineer's bending theory gives the local curvature of a beam, $1/R=M/EI$. For small slopes the curvature is the second derivative of the deflection $v$, and with $v$ measured downwards and sagging moments positive the two combine into $M=-EI\,d^2v/dx^2$. Integrating once gives the slope and twice the deflection, with constants fixed by known deflections and slopes at the supports. Where the bending moment changes form along the beam, each region brings two more constants and needs continuity conditions; Macaulay's method avoids this by writing $M$ as one expression with switch-on brackets $[x-a]^n$, so only two constants ever appear.

> [!summary]- Exam use: quick path
> - **Use it when:** the deflection or slope of a statically determinate beam is wanted at a point or along the beam, or the maximum deflection must be found.
> - **Assumptions:** engineer's bending theory holds (linear elastic, plane sections, uniform $EI$ unless stated); small slopes, so $\theta\approx dv/dx$ and $ds\approx dx$; $v$ positive downwards, $M$ sagging positive.
> - **Method:** 1. Find the reactions. 2. Cut once, after the last change in loading but before the end of the beam, and write $M(x)$ for the left part with Macaulay brackets. 3. Integrate $EI\,v''=-M$ twice, keeping the brackets intact. 4. Apply the boundary conditions, setting any bracket with $x<a$ to zero. 5. Evaluate $v$ where it is wanted; for the maximum, solve $dv/dx=0$.
> - **Common mistakes:** expanding a bracket, or keeping it when its argument is negative; forgetting that a UDL which stops before the cut needs a second, cancelling UDL.
> - **Practise:** [[#Example: the point load revisited with Macaulay brackets]] · [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q2 - Partial UDL and an overhang|Tutorial 5 Q2]]

A beam that is strong enough may still be useless if it sags too far. A ceiling that deflects a few millimetres goes unnoticed; one that deflects a few centimetres cracks its plaster and lets marbles roll to the middle of the room. The second engineering question about a beam, after whether it breaks, is therefore how far it bends.

Bending theory already contains the answer locally. Each short length of beam bends into a circular arc whose curvature is proportional to the bending moment there. The deflection at any point is the accumulation of all those local curvatures: curvature adds up to slope, and slope adds up to deflection. That is why the bending moment has to be known along the whole beam, not just at its maximum, and why finding the deflection means integrating twice.

The integration itself is routine. The work lies in writing the bending moment correctly and in fixing the constants of integration from what is known at the supports. A beam with several loads has a different expression for $M$ between each pair of loads, and handling them separately soon becomes unmanageable; Macaulay's brackets fold all of them into a single expression.

---

## 1. From bending moment to curvature

### Moment and curvature

Engineer's bending theory ([[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]]) assumes plane sections remain plane, so the beam is locally a segment of a circle of radius $R$, and gives

$$
\frac MI=\frac ER
$$

Rearranged, the curvature is set by the bending moment:

$$
\frac1R=\frac{M}{EI}
$$

The product $EI$ is the **flexural rigidity**. It combines the stiffness of the material, $E$, with that of the section's geometry, $I$; doubling either halves the curvature.

### Curvature and deflection

The **deflection** $v(x)$ is the vertical displacement of the neutral axis from its original straight position, measured downwards as positive (the same direction as $y$). Let $\theta$ be the angle between the tangent to the deflected beam and the $x$ axis. Along an arc of length $ds$, the tangent turns through $d\theta$, and for an arc of radius $R$

$$
ds=R\,d\theta
$$

$$
\frac1R=\frac{d\theta}{ds}
$$

The radius of curvature is large, so the deflected beam is nearly straight: $ds\approx dx$, and the slope angle is small, $\theta\approx\tan\theta=dv/dx$ in radians. Then

$$
\frac1R=\frac{d\theta}{ds}\approx\frac{d\theta}{dx}=\frac{d}{dx}\left(\frac{dv}{dx}\right)
$$

$$
\frac1R=\pm\frac{d^2v}{dx^2}
$$

with the sign still to be set by the convention.

### Sign convention

A positive (sagging) bending moment bends the beam into a smile. With $v$ downwards, a sagging beam read from left to right slopes downwards on the left, $dv/dx>0$, has $dv/dx=0$ at the lowest point and slopes upwards on the right, $dv/dx<0$. The slope decreases as $x$ increases, so $d^2v/dx^2<0$: a sagging moment produces negative curvature in these axes. The sign is chosen so that a positive bending moment gives negative curvature:

$$
\frac1R=-\frac{d^2v}{dx^2}
$$

Equate the two expressions for $1/R$:

$$
\frac{M}{EI}=-\frac{d^2v}{dx^2}
$$

$$
\boxed{M=-EI\frac{d^2v}{dx^2}}
$$

the relation between bending moment and deflection, written equivalently as $EI\,v''=-M$.

![[s1_deflection_sign_convention.png|900]]

### Solving by integration

Integrate $EI\,v''=-M$ once to get the slope:

$$
\frac{dv}{dx}=\frac{1}{EI}\left(\int-M\,dx+C_0\right)
$$

and again to get the deflection:

$$
v=\frac{1}{EI}\left(\int\left(\int-M\,dx\right)dx+C_0x+C_1\right)
$$

The constants of integration come from **boundary conditions**, the known values of deflection or slope at the ends of the beam:

| Support | Known values |
|---|---|
| Pin or roller | $v=0$ |
| Built-in | $v=0$ and $dv/dx=0$ |
| Free end | nothing on $v$; its zero $M$ and $Q$ are already in $M(x)$ |

## 2. Simply supported beam with a uniform load

A simply supported beam of span $L$, pinned at A ($x=0$) and on a roller at B ($x=L$), carries a uniformly distributed load $w$ (N/m).

### Bending moment

By symmetry each reaction is $R_A=R_B=wL/2$. Cut at $x$ and keep the left part. The load on it is $wx$, acting at its middle, $x/2$ from the cut. With clockwise moments about the cut equal to anticlockwise ones,

$$
M+wx\frac x2=\frac{wL}{2}x
$$

$$
M=\frac{wL}{2}x-\frac{wx^2}{2}
$$

There are no concentrated loads or moments, so this expression holds along the whole beam.

The same result comes from the load–shear–moment relations of [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Derivation|A3]]:

$$
\frac{dQ}{dx}=-w\quad\Rightarrow\quad Q=-wx+C_a
$$

$$
\frac{dM}{dx}=Q\quad\Rightarrow\quad M=-\frac{wx^2}{2}+C_ax+C_b
$$

$M(0)=0$ gives $C_b=0$ and $M(L)=0$ gives $C_a=wL/2$.

### Deflection

Start from the moment–deflection relation:

$$
EI\frac{d^2v}{dx^2}=-M=-\frac{wL}{2}x+\frac{wx^2}{2}
$$

Integrate once:

$$
EI\frac{dv}{dx}=-\frac{wL}{4}x^2+\frac{w}{6}x^3+C_0
$$

and again:

$$
EIv=-\frac{wL}{12}x^3+\frac{w}{24}x^4+C_0x+C_1
$$

Both supports prevent vertical movement. At A, $v(0)=0$:

$$
0=0+0+0+C_1\quad\Rightarrow\quad C_1=0
$$

At B, $v(L)=0$:

$$
0=-\frac{wL^4}{12}+\frac{wL^4}{24}+C_0L
$$

$$
C_0L=\frac{wL^4}{24}
$$

$$
C_0=\frac{wL^3}{24}
$$

So

$$
\boxed{v=\frac{1}{EI}\left(\frac{wL^3}{24}x-\frac{wL}{12}x^3+\frac{w}{24}x^4\right)=\frac{w}{24EI}\left(L^3x-2Lx^3+x^4\right)}
$$

The maximum is at mid-span by symmetry. Substitute $x=L/2$:

$$
v\!\left(\tfrac L2\right)=\frac{w}{24EI}\left(\frac{L^4}{2}-\frac{2L^4}{8}+\frac{L^4}{16}\right)=\frac{w}{24EI}\cdot\frac{8-4+1}{16}L^4
$$

$$
\boxed{v_{max}=\frac{5wL^4}{384EI}}
$$

The slope at the left support is $dv/dx=C_0/EI=wL^3/(24EI)$; by symmetry it is $-wL^3/(24EI)$ at the right support.

## 3. Simply supported beam with an off-centre point load

### Two regions

The beam now carries a single downward force $F$ a distance $a$ from A. Moments about each support give

$$
R_A=\frac{F(L-a)}{L},\qquad R_B=\frac{Fa}{L}
$$

The shear force jumps at the load, so the bending moment has a different expression either side of it, and the beam must be cut in two regions.

For $0<x<a$, only $R_A$ is to the left of the cut:

$$
M=\frac{F(L-a)}{L}x
$$

$$
EI\frac{d^2v}{dx^2}=-\frac{F(L-a)}{L}x
$$

$$
EI\frac{dv}{dx}=-\frac{F(L-a)}{L}\frac{x^2}{2}+C_0
$$

$$
EIv=-\frac{F(L-a)}{L}\frac{x^3}{6}+C_0x+C_1
$$

For $a<x<L$, the load $F$ is also to the left, a distance $x-a$ from the cut. Clockwise moments equal anticlockwise ones:

$$
\frac{F(L-a)}{L}x=M+F(x-a)
$$

$$
M=\frac{F(L-a)}{L}x-F(x-a)
$$

$$
EI\frac{d^2v}{dx^2}=-\frac{F(L-a)}{L}x+F(x-a)
$$

Integrate, treating $(x-a)$ as a single variable (differentiating the result confirms it):

$$
EI\frac{dv}{dx}=-\frac{F(L-a)}{L}\frac{x^2}{2}+F\frac{(x-a)^2}{2}+C_2
$$

$$
EIv=-\frac{F(L-a)}{L}\frac{x^3}{6}+F\frac{(x-a)^3}{6}+C_2x+C_3
$$

### Four constants and four conditions

Each equation is valid in one region only, and there are four constants. Two boundary conditions are available, $v(0)=0$ and $v(L)=0$. The other two come from **continuity**: a real beam has no sudden step and no kink, so the deflection and the slope must be the same from both sides at $x=a$. Zero slope under the load is not a valid condition, except when $a=L/2$ and the beam is symmetric.

$v(0)=0$, using the first region:

$$
C_1=0
$$

Equal slope at $x=a$; the $(x-a)^2$ term vanishes there:

$$
-\frac{F(L-a)}{L}\frac{a^2}{2}+C_0=-\frac{F(L-a)}{L}\frac{a^2}{2}+C_2
$$

$$
C_0=C_2
$$

Equal deflection at $x=a$; the $(x-a)^3$ term vanishes too:

$$
-\frac{F(L-a)}{L}\frac{a^3}{6}+C_0a=-\frac{F(L-a)}{L}\frac{a^3}{6}+C_2a+C_3
$$

$$
C_0a=C_2a+C_3
$$

$$
C_3=0
$$

$v(L)=0$, using the second region:

$$
0=-\frac{F(L-a)}{L}\frac{L^3}{6}+F\frac{(L-a)^3}{6}+C_2L
$$

$$
C_2L=\frac{F(L-a)L^2}{6}-\frac{F(L-a)^3}{6}
$$

$$
C_2=\frac{F(L-a)}{6L}\left(L^2-(L-a)^2\right)
$$

Expanding $L^2-(L-a)^2=2La-a^2=a(2L-a)$,

$$
C_0=C_2=\frac{Fa(L-a)(2L-a)}{6L}
$$

### Deflection under the load and the worst case

In the first region,

$$
EIv=-\frac{F(L-a)}{6L}x^3+\frac{F(L-a)}{6L}(2La-a^2)x=\frac{F(L-a)x}{6L}\left(2La-a^2-x^2\right)
$$

At the load, $x=a$:

$$
EIv(a)=\frac{F(L-a)a}{6L}\left(2La-2a^2\right)=\frac{F(L-a)a\cdot2a(L-a)}{6L}
$$

$$
\boxed{v(a)=\frac{Fa^2(L-a)^2}{3EIL}}
$$

The worst place for the load is at mid-span. With $a=L/2$:

$$
v_{max}=\frac{F(L/2)^2(L/2)^2}{3EIL}=\frac{FL^3}{48EI}
$$

and the slope at the left support is $C_0/EI=FL^2/(16EI)$, with the opposite sign at the right support.

### Where the maximum deflection is when the load is off centre

When the load is not central, the maximum deflection lies between the load and the mid-span, in the longer part of the beam. Take $a>L/2$, so the longer part is $0<x<a$. Setting the slope to zero in that region,

$$
\frac{d}{dx}\Big[x\left(2La-a^2-x^2\right)\Big]=2La-a^2-3x^2=0
$$

$$
x_m=\sqrt{\frac{a(2L-a)}{3}}
$$

which is less than $a$ whenever $a>L/2$. Substitute back, using $2La-a^2-x_m^2=\tfrac23a(2L-a)$:

$$
EIv_{max}=\frac{F(L-a)}{6L}\cdot\sqrt{\frac{a(2L-a)}{3}}\cdot\frac23a(2L-a)
$$

$$
v_{max}=\frac{\sqrt3\,F(L-a)\left[a(2L-a)\right]^{3/2}}{27EIL}
$$

With the load at mid-span this returns $FL^3/48EI$.

![[s1_point_load_deflection.png|900]]

This method clearly takes a lot of work: one section per change in load brings two more constants. A beam with three point loads and a distributed load would need four expressions for $v(x)$ and eight constants from boundary and continuity conditions, and the working grows quickly with each load.

## 4. Macaulay's method

### Switch-on brackets

The analysis would be much simpler if the bending moment could be described by a single function valid along the whole beam. **Macaulay's method** does this with step functions, written with square brackets that have a special meaning:

$$
[x-a]^n=\begin{cases}0 & x<a\\(x-a)^n & x\ge a\end{cases}
$$

The term switches on abruptly as $x$ reaches $a$; for $x\ge a$ the brackets behave as ordinary parentheses. Some textbooks use angle brackets $\langle x-a\rangle$ for the same thing. The bracket can never be negative: it is either zero or $x-a$. For $n=0$ the convention is

$$
[x-a]^0=\begin{cases}0 & x<a\\(x-a)^0=1 & x>a\end{cases}
$$

so $[x-a]^0$ is the unit step itself.

A downward force $F$ at $x=a$ contributes $-F[x-a]$ to the bending moment of the left part: nothing for cuts before the load, and $-F(x-a)$ for cuts after it.

![[s1_macaulay_brackets.png|900]]

### Rules

To keep their meaning, the square brackets must be:

1. not expanded;
2. kept intact during integration, integrating with respect to the bracket as a whole:

$$
\int F[x-a]\,dx=F\frac{[x-a]^2}{2},\qquad\int[x-a]^n\,dx=\frac{[x-a]^{n+1}}{n+1}
$$

When evaluating, including in the boundary conditions, any bracket whose argument is negative is zero.

### Procedure

1. Find the reactions from force and moment equilibrium, after drawing the FBD.
2. Take a single section after the last change in loading, but before the end of the beam.
3. Write the bending moment for the left part, including every load's contribution with its bracket. This one expression is valid for the whole beam.
4. Integrate $EI\,v''=-M$ twice, giving two constants.
5. Find them from the boundary conditions, then use $v(x)$ to find, for example, the maximum deflection.

### Example: the point load revisited with Macaulay brackets

For the simply supported beam with $F$ at $x=a$, cut in the region $a<x<L$:

$$
M=\frac{F(L-a)}{L}x-F[x-a]
$$

For $0<x<a$ the bracket is zero and this reduces to $F(L-a)x/L$, as derived before; one expression covers both regions, so there is no need to match slope and deflection at the load. Then

$$
EI\frac{d^2v}{dx^2}=-\frac{F(L-a)}{L}x+F[x-a]
$$

$$
EI\frac{dv}{dx}=-\frac{F(L-a)}{L}\frac{x^2}{2}+F\frac{[x-a]^2}{2}+C_0
$$

$$
EIv=-\frac{F(L-a)}{L}\frac{x^3}{6}+F\frac{[x-a]^3}{6}+C_0x+C_1
$$

valid for $0<x<L$. At $x=0$ the bracket is negative and vanishes, so $v(0)=0$ gives $C_1=0$. At $x=L$ the bracket is $L-a$:

$$
0=-\frac{F(L-a)}{L}\frac{L^3}{6}+F\frac{(L-a)^3}{6}+C_0L
$$

$$
C_0=\frac{F(L-a)}{6L}\left(L^2-(L-a)^2\right)=\frac{F(L-a)}{6L}(2La-a^2)
$$

the same constant as before, with no continuity conditions needed. So

$$
\boxed{v=\frac{1}{EI}\left[\frac{F(L-a)x}{6L}\left(2La-a^2-x^2\right)+F\frac{[x-a]^3}{6}\right]}
$$

Once $M$ has been written down, the deflection follows by routine integration; the only novelty is the brackets, which must be kept.

### Writing the bending moment for other loads

Writing $M$ correctly is most of the work; the common loads are tabulated with the reactions left as symbols.

Several point loads $F_1$, $F_2$, $F_3$ at $a$, $b$, $c$ on a simply supported beam, cut after the last one:

$$
M=R_Ax-F_1[x-a]-F_2[x-b]-F_3[x-c]
$$

A uniform load $w$ starting at $x=a$ and running past the cut. The load to the left of the cut is $w[x-a]$, and its resultant acts at the middle of the loaded length, $[x-a]/2$ from the cut:

$$
M=R_Ax-\frac{w[x-a]^2}{2}
$$

A uniform load that stops at $x=b$, before the end of the beam. A bracket, once started, cannot be stopped. The fix is to superpose a second, upward, uniform load $w$ from $x=b$ onwards, which cancels the first beyond $b$:

$$
M=R_Ax-\frac{w[x-a]^2}{2}+\frac{w[x-b]^2}{2}
$$

A concentrated moment $M_0$ at $x=a$, drawn anticlockwise. On the left part, the couple acts in the same sense as the positive $M$ on the cut face and so is subtracted:

$$
M=R_Ax-M_0[x-a]^0
$$

an anticlockwise couple makes the moment jump down by $M_0$, as in [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams#Consequences|A3]].

A combined case: an upward 4 kN reaction at the left end, 5 kN downwards at 2 m and 4 kN/m from 4 m to the end of the beam at 8 m, cut inside the distributed load:

$$
M=4x-5[x-2]-\frac{4[x-4]^2}{2}\ \mathrm{kN\,m}
$$

> [!tip] Checking a Macaulay expression
> Differentiate it. $dM/dx$ should be the shear force, jumping by each point load, and $d^2M/dx^2$ should be $-w$ wherever a distributed load is switched on. For the combined case, $dM/dx=4-5[x-2]^0-4[x-4]$: 4 kN to the left of the point load, $-1$ kN after it, then falling at 4 kN/m.

### Standard results

The double-integration results above, with the cantilever results derived in [[FEEG1002 A6 - Statically Indeterminate Beams#3. The superposition method|A6]], are the standard cases most often combined by superposition:

| Case | Maximum deflection | End slope | Maximum moment |
|---|---|---|---|
| Simply supported, central $F$ | $\dfrac{FL^3}{48EI}$ at mid-span | $\dfrac{FL^2}{16EI}$ | $\dfrac{FL}{4}$ |
| Simply supported, UDL $w$ | $\dfrac{5wL^4}{384EI}$ at mid-span | $\dfrac{wL^3}{24EI}$ | $\dfrac{wL^2}{8}$ |
| Cantilever, end load $F$ | $\dfrac{FL^3}{3EI}$ at the tip | $\dfrac{FL^2}{2EI}$ at the tip | $FL$ at the root |
| Cantilever, UDL $w$ | $\dfrac{wL^4}{8EI}$ at the tip | $\dfrac{wL^3}{6EI}$ at the tip | $\dfrac{wL^2}{2}$ at the root |

![[s1_standard_beam_cases.png|900]]

---

## Worked examples

### Worked example - floor beam under a uniform load

The steel I-beam of [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area#Example: the I-beam revisited|A4]] ($I=1.659\times10^{-6}$ m⁴, $E=210$ GPa) spans 3 m between simple supports and carries 5 kN/m. The flexural rigidity is

$$
EI=(210\times10^9)(1.659\times10^{-6})=3.484\times10^5\ \mathrm{N\,m^2}
$$

and the mid-span deflection

$$
v_{max}=\frac{5wL^4}{384EI}=\frac{5(5000)(3)^4}{384(3.484\times10^5)}=15.1\ \mathrm{mm}
$$

$1/200$ of the span. Because $v\propto L^4$, a 4 m span with the same load would deflect $(4/3)^4=3.2$ times as much, 47.8 mm.

### Worked example - off-centre point load

The same beam carries $F=6$ kN at $a=2$ m on a 3 m span. Under the load,

$$
v(a)=\frac{Fa^2(L-a)^2}{3EIL}=\frac{(6000)(2)^2(1)^2}{3(3.484\times10^5)(3)}=7.65\ \mathrm{mm}
$$

The maximum deflection is in the longer, left-hand part at

$$
x_m=\sqrt{\frac{a(2L-a)}{3}}=\sqrt{\frac{2(4)}{3}}=1.633\ \mathrm m
$$

$$
v_{max}=\frac{(6000)(1)(1.633)\left(2(3)(2)-2^2-1.633^2\right)}{6(3)(3.484\times10^5)}=8.33\ \mathrm{mm}
$$

> [!check] Close to mid-span
> The maximum sits only 0.13 m from mid-span, where $v=8.25$ mm. For a single point load on a simply supported beam the maximum is never more than $0.077L$ from mid-span: as the load approaches one support, $x_m$ tends to $L/\sqrt3=0.577L$ from the other. The mid-span value is therefore a good first estimate.

### Worked example - partial UDL with an overhang

Tutorial 5 Q2: a beam from $x=0$ to 5 m rests on a pin at $x=1$ m and a roller at $x=3$ m, and carries 6 kN/m over $2\le x\le4$ m; $EI=7$ MN m². Find the deflection at the free end, $x=5$ m.

**Reactions.** The 12 kN resultant acts at $x=3$ m, directly over the roller, so moments about the roller give $R_1=0$ and the roller carries $R_3=12$ kN.

**Bending moment.** Cut beyond $x=4$; the UDL stops at 4 m, so add a cancelling upward UDL from there:

$$
M=12[x-3]-\frac{6[x-2]^2}{2}+\frac{6[x-4]^2}{2}=12[x-3]-3[x-2]^2+3[x-4]^2
$$

**Integration**, keeping the brackets:

$$
EI\frac{d^2v}{dx^2}=-12[x-3]+3[x-2]^2-3[x-4]^2
$$

$$
EI\frac{dv}{dx}=-6[x-3]^2+[x-2]^3-[x-4]^3+C_0
$$

$$
EIv=-2[x-3]^3+\frac{[x-2]^4}{4}-\frac{[x-4]^4}{4}+C_0x+C_1
$$

**Boundary conditions.** At $x=1$ every bracket is negative, so $v(1)=0$ gives $C_0+C_1=0$. At $x=3$ only $[x-2]$ is positive:

$$
0=\frac{(1)^4}{4}+3C_0+C_1
$$

Subtracting the first condition, $2C_0=-\tfrac14$, so $C_0=-\tfrac18$ and $C_1=\tfrac18$.

**Deflection at the free end**, $x=5$, where all brackets are positive:

$$
EIv(5)=-2(2)^3+\frac{(3)^4}{4}-\frac{(1)^4}{4}-\frac58+\frac18=-16+20.25-0.25-0.5=3.5\ \mathrm{kN\,m^3}
$$

$$
v(5)=\frac{3.5\times10^3}{7\times10^6}=0.5\ \mathrm{mm}
$$

downwards.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]] · Next: [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Concepts: [[Macaulay's Method]] · [[Standard Beam Deflections]] · [[Moment Curvature Relation]] · [[Elastic Curve]] · [[Heaviside Step Function]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 A6 - Statically Indeterminate Beams|A6]] (Macaulay with unknown reactions) · [[FEEG1002 A7 - Euler Buckling of Struts|A7]] ($EI\,v''=-M$ with $M=Pv$)
- Year 2: [[SESA2028 S2 - Beam Deflection and Bending Design]] writes the same equation with $EI\,v''=M$ under its own convention; the [[Unit Load Method]] in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] gives a single deflection without the whole elastic curve; $[x-a]^0$ is the [[Heaviside Step Function]] of MATH2048 and the time shift of the [[Laplace Transform]]

## Sources

- `Lecture 09 - Beams, Deflection.pdf` (S1 Lectures 9a–9c, 27 slides) and `Lecture 10 - Macaulay's Method.pdf` (S1 Lectures 10a–10c, 23 slides), read in full.
- `FEEG1002 Lecture 9 - Sttaics 1 - Beams, Deflection - November 2024.txt` (Lecture 9): recap (ll. 17–100), moment–curvature and geometry (ll. 101–208), sign convention (ll. 209–273), integration and boundary conditions (ll. 274–306), uniform load (ll. 307–550), point load with continuity conditions (ll. 551–837), the case for Macaulay (ll. 838–848).
- Lecture 10 was released as three recorded videos (L9, ll. 6–16) and has no transcript. `FEEG1002 Lecture 11 - Statics 1 - Statically indeterminate beams - December 2024.txt`, ll. 13–93, recaps it: one expression for $M$, the bracket rules and the procedure.
- Tutorial Sheet 05 and its official solutions: Q1, Q2 and additional Q1–Q2 (the indeterminate questions are in A6).
- All numbers recomputed in Python; the symbolic results (constants, $v(a)$, $x_m$ and $v_{max}$) were checked with SymPy.

## Self-study tasks

### Core

- [ ] Derive $M=-EI\,d^2v/dx^2$, explaining why a sagging moment gives a negative second derivative (L9, ll. 157–273). → [[#Sign convention]]
- [ ] Derive the deflection of a simply supported beam under a UDL and show $v_{max}=5wL^4/384EI$ (L9, ll. 307–493). → [[#2. Simply supported beam with a uniform load]]
- [ ] Solve the four-constant problem for the off-centre point load before reading the solution (left as a "rainy weekend" puzzle, L9, ll. 734–741), and simplify $C_2$ (L9, ll. 809–810). Targets $C_0=C_2=Fa(L-a)(2L-a)/6L$, $C_1=C_3=0$. → [[#Four constants and four conditions]]
- [ ] Watch the Lecture 10 videos and redo the point-load example with Macaulay brackets (set in L9, ll. 6–16 and L11, ll. 3–7). → [[#Example: the point load revisited with Macaulay brackets]]
- [ ] Tutorial 5 Q1: tip deflection of a cantilever loaded at mid-length. Target $5FL^3/48EI$. → [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q1 - Cantilever with a load at midspan|Tutorial 5 Q1]]
- [ ] Tutorial 5 Q2: deflection of the free end with a partial UDL. Target 0.5 mm. → [[#Worked example - partial UDL with an overhang]] · [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Q2 - Partial UDL and an overhang|Tutorial 5 Q2]]

### Further practice

- [ ] Find where the maximum deflection occurs for an off-centre load (deck 10, slide 14, "requires further manipulation"). → [[#Where the maximum deflection is when the load is off centre]]
- [ ] Plot the UDL deflection curve in Python (suggested in L9, ll. 469–478). → [[#Deflection]]
- [ ] Tutorial 5 additional Q1: deflection under a linearly varying load. → [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Extra Q1 - Linearly varying load|Tutorial 5 Extra Q1]]
- [ ] Tutorial 5 additional Q2: deflection of the free end of the Tutorial 3 Q2 beam. Target 4.92 mm. → [[FEEG1002 Statics 1 Tutorial 5 - Beam Deflection and Statically Indeterminate Beams Solutions#Extra Q2 - Deflection of the Tutorial 3 Q2 beam|Tutorial 5 Extra Q2]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 9, ll. 31–32, 74–80, 203 and 619)
> Where: [[#Curvature and deflection]] · [[#Two regions]].
>
> In the recap, the "curvature of that circle" is said to be large compared with the beam's height (ll. 31–32); it is the radius of curvature that is large. At ll. 74–80 increasing the second moment of area is said always to reduce the stress; moving material outwards does, but adding a small protrusion far from the neutral axis can increase $y_{max}$ more than $I$ and raise $\sigma_{max}=My_{max}/I$. At l. 203 "dV dx would be the second derivative" should be $d\theta/dx=d^2v/dx^2$. At l. 619 the second region is said to start "after that distributed load"; it starts after the concentrated load.

> [!warning] Slide slip (deck 10, slide 22, Further Example E)
> Where: [[#Writing the bending moment for other loads]].
>
> The left reaction is given as 4 kN. For the beam as titled, simply supported over 8 m, moments about the right-hand end give $R_A=(5\times6+16\times2)/8=7.75$ kN; if the right-hand end, drawn hatched, were built in, compatibility would give 4.91 kN. Neither is 4 kN. The form of the Macaulay expression, $M=R_Ax-5[x-2]-4[x-4]^2/2$, is unaffected.

---
title: "FEEG1002 A3 - Shear Force and Bending Moment Diagrams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 3
tags: [feeg1002, statics, beams, shear-force, bending-moment, sfd, bmd]
aliases: ["Statics 1 Lecture 5", "Statics 1 Lecture 6", "SF and BM diagrams", "SFD and BMD", "Relationships between w, Q and M"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 5 (28 Oct 2024, ll. 20–702: beams, supports, loads, internal forces, sign convention, procedure) and Lecture 6 (4 Nov 2024, ll. 10–849: worked example, relations between w, Q and M, sketching); the Lecture 6c mathematical example (linearly varying load, maximum-moment caveat) was a video with no transcript and is written from slides 23–34 of deck 6"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
key_concepts: ["[[Shear Force and Bending Moment Relations]]", "[[Free Body Diagram and Equilibrium]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 05 - Beams, Shear Force and Bending Moment.pdf"
  - "02 - Sources/Statics 1/Lectures/Lecture 06 - Beams, Relationship w, SF and BM.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 5 - Statics 1 - Beams, Shear Force and Bending moment - October 2024.txt"
  - "02 - Sources/Lectures/FEEG1002 Lecture 6 - Statics 1 - Relationships w, SF and BM - Nov 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 03 - Beams, w, SF and BM - Solutions.pdf"
---

# FEEG1002 A3 - Shear Force and Bending Moment Diagrams

> [!abstract] Summary
> A beam carries load across its length by bending, and wherever it is cut the part on one side needs an internal shear force $Q$ and bending moment $M$ from the other side to stay in equilibrium. With $Q$ positive when it would turn a segment clockwise and $M$ positive when it sags the beam, cutting after every change of loading and balancing the left-hand part gives $Q(x)$ and $M(x)$, plotted as the shear force and bending moment diagrams. Equilibrium of a short slice gives $dQ/dx=-w$ and $dM/dx=Q$, so point loads make jumps in $Q$, couples make jumps in $M$, and $M$ is stationary where $Q=0$. For a uniform section the largest $|M|$ marks where the bending stress is greatest.

> [!summary]- Exam use: quick path
> - **Use it when:** a beam's internal forces are needed, especially the size and position of the largest bending moment for a stress or deflection calculation.
> - **Assumptions:** statically determinate beam; loads in the plane of the beam; distributed load $w$ positive downwards; course sign convention ($Q$ downward on the right-hand face of the left part, $M$ sagging positive).
> - **Method:** 1. FBD of the whole beam; replace distributed loads by their resultants to find the reactions only. 2. Go back to the original loading and cut, from the left, after every change in loading. 3. Draw positive $Q$ and $M$ on the cut face. 4. Vertical equilibrium of the left part gives $Q(x)$; moments about the cut face give $M(x)$. 5. Plot, and check against $dQ/dx=-w$, $dM/dx=Q$ and the end values.
> - **Common mistakes:** using the resultant of a distributed load inside a region where only part of it lies to the left of the cut; taking the stationary point of $M$ as the largest moment without checking supports, ends and jumps.
> - **Practise:** [[#Example: overhanging beam with a point load and a distributed load]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Q2 - UDL between supports with overhang loads|Tutorial 3 Q2]]

A beam is a slender member loaded across its length rather than along it: a floor joist under furniture, a wing under lift and the weight of its engines, a mast under wind, the stem of a hip implant in a thigh bone. The load has to travel sideways along the beam to the supports, and it does so by bending the beam. A beam must neither break nor sag too far, and both checks need the variation of internal force along the beam.

In a bar under tension the internal force is the same everywhere: cut it anywhere and the same force $F$ is needed to hold the cut-off piece, spread uniformly over the cross-section. In a beam the internal force changes from place to place. A piece cut from a cantilever carrying a weight at its free end needs an upward force to stop it falling and a moment to stop it rotating, and that moment grows with the distance from the weight. The internal resultants along the beam are found in the sections below; their distribution over the depth of the beam, as bending and shear stresses, is in [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]] and [[FEEG1002 A9 - Shear Stresses in Beams|A9]].

The shear force and bending moment diagrams are the beam engineer's main tool. They show at a glance where the beam is most heavily loaded, and they feed every later calculation: bending stress, deflection, and the indeterminate beams of [[FEEG1002 A6 - Statically Indeterminate Beams|A6]].

---

## 1. Beams, supports and loads

### Supports

Beam supports are idealisations of real connections. A **pin** support prevents translation in both directions but allows rotation, so it supplies a vertical and a horizontal reaction. A **roller** support allows the beam to slide along the surface and supplies only the reaction normal to it; a bridge sits on rollers at one end so that it can expand in hot weather without building up thermal stress. A beam on a pin at one end and a roller at the other is **simply supported**. A **built-in** support, also called fixed or clamped, prevents translation and rotation, and supplies a vertical force, a horizontal force and a reaction moment. A beam built in at one end and free at the other is a **cantilever**.

![[s1_support_types.png|900]]

Real supports sit between these ideals: a pin has friction, and a clamp is never perfectly rigid. Where it matters, analyse both bounding cases and design for the worse.

### Loads

A **concentrated** (point) load acts at a single point, in N. A **distributed load** $w$, in N/m, is spread along a length of beam; it may be uniform (a UDL) or vary with position, like snow piled against a balcony wall. A **couple**, or concentrated moment, is a pair of equal and opposite forces with a lever arm, such as two cables pulling on outrigger arms, drawn as a curved arrow and measured in N m.

## 2. Internal forces

### A bar in tension

At any section $x$ of a bar carrying tension $F$, the right-hand piece must pull on the left-hand piece with $F$ to keep it in equilibrium, whatever $x$ is. Each side of the cut pulls on the other with equal and opposite forces, and the internal force is spread uniformly over the section as the stress $F/A$, valid away from the ends of the bar. In bending, shearing and twisting the internal forces vary along the member, which raises two separate problems: how the internal force varies along the length, and how it is distributed over the cross-section (A4 and A9).

### Example: an offset tensile force

A cantilever is built in at its right-hand end and loaded at its free end by a horizontal force $F$, applied through a bracket a distance $d$ below the beam's axis. Cut at $x$ and keep the left part. Horizontal equilibrium needs an internal axial force $F$ on the cut face. The applied $F$ and the internal $F$ form a couple of arm $d$, so rotational equilibrium needs an internal moment

$$
M=Fd
$$

on the cut face, the same at every $x$. This internal moment is the **bending moment**. The stresses that make it up are not uniform over the section, which is the problem of A4.

### Example: a cantilever with an end load

The same cantilever, of length $L$, can instead carry a downward force of 1000 N at its free left end, with $x$ measured from that end. At a cut at $x$, the left part has 1000 N acting down on it. To hold it up, the right part must push up on the cut face with a vertical **shear force** of 1000 N, the same at every $x$. The 1000 N and the shear force are a distance $x$ apart, so they form a couple $1000x$ that the right part must resist with a bending moment of magnitude $1000x$ N m: zero at the free end and $1000L$ at the wall. The balancing moment on the left part is anticlockwise in the offset-force example and clockwise here, so a sign convention is needed.

## 3. The sign convention

Consider a beam segment cut at its left and right faces. The course convention is:

- A **positive shear force** $Q$ on a cut face would rotate the segment clockwise: it acts downwards on the right-hand face of the segment and upwards on its left-hand face.
- A **positive bending moment** $M$ produces **sagging**: anticlockwise on the right-hand face of the segment and clockwise on its left-hand face, bending the beam into a smile with compression on top and tension underneath.

![[s1_sign_convention.png|900]]

The convention must not be changed mid-problem, because the relations between load, shear force, bending moment and deflection all depend on it. Sagging is the natural positive choice for buildings, whose floors are loaded downwards.

Apply it to the cantilever. The left part (free end at $x=0$) has 1000 N down at its left end, and on its right-hand cut face the positive $Q$ points down and the positive $M$ is anticlockwise. Vertical equilibrium, down positive:

$$
Q+1000=0
$$

$$
Q=-1000\ \mathrm N
$$

Moments about the cut face, anticlockwise positive. The 1000 N acts a distance $x$ to the left of the cut and turns the part anticlockwise:

$$
M+1000x=0
$$

$$
M=-1000x\ \mathrm{N\,m}
$$

The shear force is negative and constant; the bending moment is negative (hogging, tension on top) and grows linearly to $-1000L$ at the wall.

## 4. Procedure for shear force and bending moment diagrams

The step-by-step procedure, which handles complicated loading systematically, is:

1. Calculate the support reactions. Draw the FBD, replacing each distributed load by its **resultant**: a uniform $w$ over a length $L_w$ is equivalent, for the reactions, to a single force $F=wL_w$ at the middle of that length. Use force and moment equilibrium.
2. Go back to the beam with its **original** loading, including the distributed loads. Starting from the left, cut the beam after every change in loading.
3. Insert positive $Q$ and $M$ on each cut face.
4. Consider all forces and moments to the left of $x$: vertical equilibrium gives $Q(x)$; rotational equilibrium gives $M(x)$. Take moments about the cut face, so that the unknown $Q$ does not enter the moment equation.
5. Plot the SF and BM diagrams from the expressions.

Never cut exactly at a point load: cut just before and just after it. The moment about the cut face of an upward force $F$ applied a distance $a$ from the left end is $F(x-a)$, so a single force gives $Q=F$ and $M=F(x-a)$ on the left part.

### Example: overhanging beam with a point load and a distributed load

A beam 7 m long has a pin at A ($x=0$) and a roller at B ($x=5$ m). It carries 5000 N downwards at $x=1$ m and 5000 N/m over the overhang from B to the free end, $5\le x\le7$.

**Step 1, reactions.** The distributed load has resultant $2\times5000=10\,000$ N at $x=6$ m. Vertical equilibrium:

$$
R_{Ay}+R_{By}=5000+10\,000=15\,000
$$

Moments about A:

$$
(5000)(1)+(10\,000)(6)=R_{By}(5)
$$

$$
R_{By}=13\,000\ \mathrm N,\qquad R_{Ay}=2000\ \mathrm N
$$

**Cut n–n′, $0\le x\le1$.** Only $R_{Ay}$ is to the left. With the left part's cut face carrying positive $Q$ (down) and $M$ (anticlockwise):

$$
Q=2000\ \mathrm N,\qquad M=2000x
$$

**Cut m–m′, $1\le x\le5$.** Now the 5000 N load is also to the left, at a distance $x-1$ from the cut. Vertical, with up and down forces balancing:

$$
Q+5000=2000
$$

$$
Q=-3000\ \mathrm N
$$

Moments about the cut, with clockwise moments of the left part equal to anticlockwise ones:

$$
M+5000(x-1)=2000x
$$

$$
M=5000-3000x
$$

**Cut o–o′, $5\le x\le7$.** To the left are both reactions, the point load and the part of the distributed load between B and the cut: $5000(x-5)$, whose own resultant acts at its middle, a distance $(x-5)/2$ from the cut. Vertical:

$$
Q+5000+5000(x-5)=2000+13\,000
$$

$$
Q=35\,000-5000x
$$

Moments about the cut:

$$
M+5000(x-1)+5000(x-5)\frac{x-5}{2}=2000x+13\,000(x-5)
$$

Expanding the bracket term, $2500(x-5)^2=2500x^2-25\,000x+62\,500$, so

$$
M=2000x+13\,000x-65\,000-5000x+5000-2500x^2+25\,000x-62\,500
$$

$$
M=-2500x^2+35\,000x-122\,500
$$

**Step 5, diagrams.** $Q$ is $+2000$ N to the point load, drops by 5000 to $-3000$ N, jumps up by 13 000 to $+10\,000$ N at B, and falls linearly to zero at the free end. $M$ rises linearly to $+2000$ N m under the point load, falls linearly through zero at $x=5/3$ m to $-10\,000$ N m at B, then curves back to zero at the free end.

![[s1_sfd_bmd_lecture_example.png|900]]

> [!check] End values
> At $x=7$: $Q=35\,000-35\,000=0$ and $M=-122\,500+245\,000-122\,500=0$. Both must vanish at a free end with no applied load, because there is no beam beyond it.

The largest bending moment is the hogging $-10$ kN m over support B, not the sagging $+2$ kN m under the load. If the beam has a uniform cross-section, the bending stress is greatest there. For statically indeterminate beams the reactions cannot be found in step 1 at all without first finding the deflected shape ([[FEEG1002 A6 - Statically Indeterminate Beams|A6]]).

## 5. Relations between distributed load, shear force and bending moment

The diagrams have discontinuities, jumps at point loads and couples, but between those points $w$, $Q$ and $M$ are linked by two differential relations that make the diagrams quick to sketch.

### Derivation

A slice between $x$ and $x+dx$ of a beam carrying a distributed load $w(x)$, positive downwards, has on its left face the shear force $Q$ (upwards, positive on a left-hand face) and the bending moment $M$ (clockwise); on its right face, $Q+dQ$ (downwards) and $M+dM$ (anticlockwise), both drawn positive. Over the short length $dx$ the load is effectively uniform, so it is a force $w\,dx$ acting at the middle of the slice.

![[s1_beam_element_wqm.png|900]]

Vertical equilibrium, with upward forces equal to downward ones:

$$
Q=Q+dQ+w\,dx
$$

$$
dQ=-w\,dx
$$

$$
\boxed{\frac{dQ}{dx}=-w(x)}
$$

The slope of the shear force diagram equals minus the distributed load. The minus sign is a consequence of the sign convention: a downward load reduces the shear force on successive right-hand faces.

Moments about the right-hand face, clockwise moments equal to anticlockwise ones. The left-face shear force $Q$ acts a distance $dx$ to the left and turns the slice clockwise, as does the left-face moment $M$; the right-face moment $M+dM$ is anticlockwise, and the load $w\,dx$, a distance $dx/2$ to the left, turns it anticlockwise:

$$
M+Q\,dx=w\,dx\frac{dx}{2}+M+dM
$$

$$
Q\,dx=\frac w2(dx)^2+dM
$$

The $(dx)^2$ term is vanishingly small compared with the others as $dx\to0$, so

$$
\boxed{\frac{dM}{dx}=Q}
$$

The slope of the bending moment diagram equals the shear force.

### Consequences

The bending moment is stationary where $dM/dx=0$, that is where the shear force crosses zero. That point is a local maximum or minimum of $M$, not necessarily the largest moment in the beam (see [[#When the mathematical maximum is not the largest moment]]).

Integrating $dM=Q\,dx$ between two points gives

$$
M(x_2)-M(x_1)=\int_{x_1}^{x_2}Q\,dx
$$

the change in bending moment equals the area under the shear force diagram. Starting from an end where $M=0$, the moment at $x$ is the accumulated area up to $x$, provided no couple has been applied in between.

Across a concentrated force the shear force jumps by the size of the force, upwards for an upward force; across an applied couple the bending moment jumps by the size of the couple. For the jump direction, cut just either side of a clockwise couple $C$ on the left part. Before it, $M^-$ balances the forces to the left; after it, the couple adds a clockwise moment that the anticlockwise $M$ must also balance, so

$$
M^+=M^-+C
$$

A clockwise couple makes $M$ jump up; an anticlockwise one makes it jump down. The same applies to the reaction moment at a built-in end. The bending moment is zero at any end that is free to rotate (a pin, a roller or a free end) unless a couple is applied there.

| On the beam | Shear force diagram | Bending moment diagram |
|---|---|---|
| No distributed load | horizontal | straight line |
| Uniform $w$ | straight line of slope $-w$ | parabola |
| Linearly varying $w$ | parabola | cubic |
| Point force | jump equal to the force | change of slope (kink) |
| Applied couple | no change | jump equal to the couple |
| $Q=0$ | crosses zero | local maximum or minimum |

### Procedure for sketching

1. Draw the FBD and find the reactions (forces and moments).
2. Draw the SF diagram from the jumps due to point loads (start at zero, and do not forget the reactions) and the slopes $-w$ from distributed loads.
3. Draw the BM diagram from its slope, read off the SF diagram: zero at an end free to rotate, jumps at applied and reaction moments, and changes between points equal to the areas under the SF diagram.

### Example: simply supported beam with a central point load

A simply supported beam of span $L$ carries $F$ at mid-span. By symmetry each reaction is $F/2$. The shear force jumps to $+F/2$ at the left support, stays constant, drops by $F$ to $-F/2$ under the load, and returns to zero at the right support. The bending moment starts at zero, rises with slope $F/2$, so $M=Fx/2$, and falls with slope $-F/2$, so $M=F(L-x)/2$. Its peak, under the load, is the area of the first rectangle of the SF diagram:

$$
M_{max}=\frac F2\cdot\frac L2=\frac{FL}{4}
$$

### Example: simply supported beam with a uniform load

A simply supported beam of span $L$ carries a UDL $w$. Each reaction is $wL/2$. The shear force starts at $+wL/2$ and falls with slope $-w$:

$$
Q=w\left(\frac L2-x\right)
$$

to $-wL/2$ at the right support, a total drop of $wL$, the whole load. The bending moment is the parabola

$$
M=\frac w2(Lx-x^2)
$$

zero at both supports and largest at mid-span, where $Q=0$. Its value there is the area of the shear force triangle from $0$ to $L/2$:

$$
M_{max}=\frac12\cdot\frac{wL}{2}\cdot\frac L2=\frac{wL^2}{8}
$$

![[s1_simple_beam_sfd_bmd.png|900]]

The overhanging-beam example shows the relations at work: the slope of $M$ is $+2000$, then $-3000$, then varies linearly in step with $Q$; the area under the SF diagram from 0 to 1 m is $+2000$ N m, from 1 to 5 m is $-12\,000$ N m, and from 5 to 7 m is $+10\,000$ N m, which takes $M$ from 0 to 2000 to $-10\,000$ and back to 0.

## 6. Using the relations mathematically

For complicated loads it is easier to integrate the relations than to cut the beam, using the boundary conditions to fix the constants.

### Example: linearly varying load

A simply supported beam of span $L$ carries a distributed load rising linearly from zero at $x=0$ to $W_B$ (N/m) at $x=L$. Find the SF and BM distributions and the maximum bending moment.

**Reactions.** The total load is the area of the triangle, $W_BL/2$. Its resultant acts at the centroid of the triangle. To verify the position, take the moment of the load about A and divide by the total:

$$
\bar x=\frac{\int_0^L x\,\frac{W_B}{L}x\,dx}{W_BL/2}=\frac{W_BL^2/3}{W_BL/2}=\frac23L
$$

Moments about A:

$$
R_BL=\frac{W_BL}{2}\cdot\frac{2L}{3}
$$

$$
R_B=\frac{W_BL}{3},\qquad R_A=\frac{W_BL}{2}-\frac{W_BL}{3}=\frac{W_BL}{6}
$$

**Shear force.** The load is the straight line

$$
w(x)=\frac{W_B}{L}x
$$

so

$$
\frac{dQ}{dx}=-\frac{W_B}{L}x
$$

$$
Q=-\frac{W_B}{2L}x^2+C_1
$$

**Bending moment.** Integrate again:

$$
\frac{dM}{dx}=Q=-\frac{W_B}{2L}x^2+C_1
$$

$$
M=-\frac{W_B}{6L}x^3+C_1x+C_2
$$

A simple support cannot supply a moment, so $M=0$ at both ends. At $x=0$ this gives $C_2=0$. At $x=L$:

$$
0=-\frac{W_B}{6L}L^3+C_1L
$$

$$
C_1=\frac{W_BL}{6}
$$

So

$$
Q=\frac{W_BL}{6}-\frac{W_B}{2L}x^2,\qquad M=\frac{W_BL}{6}x-\frac{W_B}{6L}x^3
$$

The constant $C_1$ is the left reaction, as it must be, since $Q(0^+)=R_A$; and $Q(L)=W_BL/6-W_BL/2=-W_BL/3=-R_B$, which fits the jump at the right support.

**Maximum moment.** $M$ is stationary where $Q=0$:

$$
\frac{W_BL}{6}=\frac{W_B}{2L}x^2
$$

$$
x^2=\frac{L^2}{3}
$$

$$
x=\frac{L}{\sqrt3}=0.577L
$$

Substitute into $M$:

$$
M_{max}=\frac{W_BL}{6}\cdot\frac{L}{\sqrt3}-\frac{W_B}{6L}\cdot\frac{L^3}{3\sqrt3}
$$

$$
M_{max}=\frac{W_BL^2}{6\sqrt3}\left(1-\frac13\right)=\frac{W_BL^2}{9\sqrt3}
$$

The maximum sits right of centre, towards the heavier end of the load.

![[s1_triangular_load_sfd_bmd.png|900]]

### When the mathematical maximum is not the largest moment

Setting $dM/dx=0$ finds stationary points only. The largest bending moment can also occur at a support, at a built-in end or at a jump in the SF diagram, where $dM/dx$ changes sign without passing through zero. A cantilever 2 m long, built in at its left end, carrying 4 kN/m and an upward force of 2 kN at its free end, shows the trap. Measuring $s$ from the free end, the right-hand part of length $s$ carries the 2 kN upwards and $4s$ downwards, and

$$
M=2s-2s^2\ \mathrm{kN\,m}
$$

This has a local maximum, $dM/ds=2-4s=0$ at $s=0.5$ m, where $M=+0.5$ kN m, but at the wall ($s=2$ m) $M=4-8=-4$ kN m, eight times larger in magnitude. Always check the diagram.

![[s1_max_moment_caveat.png|900]]

---

## Worked examples

### Worked example - linearly varying load with numbers

Take the linearly varying load with $W_B=6$ kN/m over $L=3$ m. Then

$$
R_A=\frac{6\times3}{6}=3\ \mathrm{kN},\qquad R_B=\frac{6\times3}{3}=6\ \mathrm{kN}
$$

and the maximum moment is at $x=3/\sqrt3=1.732$ m:

$$
M_{max}=\frac{6\times3^2}{9\sqrt3}=3.46\ \mathrm{kN\,m}
$$

> [!check] Direct substitution
> $M(1.732)=3(1.732)-\frac{6}{18}(1.732)^3=5.196-1.732=3.46$ kN m. For comparison, a uniform load of the same total, 9 kN, would give $wL^2/8=3\times9/8=3.38$ kN m at mid-span.

### Worked example - overhanging beam by sketching

Tutorial 3 Q1 has points A to F at $x=0$, 1, 2, 3, 4 and 5 m, a pin at B, a roller at D, 8 kN at C and 3 kN at the free end F. Moments about B, anticlockwise positive:

$$
-(1)(8)+2R_D-(4)(3)=0
$$

$$
R_D=10\ \mathrm{kN},\qquad R_B=11-10=1\ \mathrm{kN}
$$

There is no distributed load, so $Q$ is piecewise constant and $M$ piecewise linear. $Q$ is 0 on AB, jumps to $+1$ kN at B, drops to $-7$ kN at C, jumps to $+3$ kN at D and returns to 0 at F. $M$ starts at zero at the free end A and accumulates the SF areas: $M_B=0$, $M_C=+1$ kN m, $M_D=1-7=-6$ kN m, $M_F=-6+3\times2=0$. The design moment is the hogging 6 kN m over the roller.

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A2 - Pin-Jointed Trusses]] · Next: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]
- Concepts: [[Shear Force and Bending Moment Relations]] · [[Free Body Diagram and Equilibrium]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Used again in: [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]] ($M_{max}$ gives the bending stress) · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]] ($M(x)$ is integrated for the deflection) · [[FEEG1002 A9 - Shear Stresses in Beams|A9]] ($Q$ gives the shear stress)
- Year 2: [[SESA2028 S2 - Beam Deflection and Bending Design]] uses the same relations with $V$ for the shear force; the shear force feeds the [[Shear Flow]] of [[SESA2028 S3 - Shear Flow and Shear Centre]]; writing $M(x)$ for a real and a unit load is the core skill of [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- `Lecture 05 - Beams, Shear Force and Bending Moment.pdf` (S1 Lectures 5a–5c, 30 slides) and `Lecture 06 - Beams, Relationship w, SF and BM.pdf` (S1 Lectures 6a–6c, 34 slides), read in full. Slides 23–34 of deck 6 (Lecture 6c, the mathematical example and the maximum-moment caveat) were delivered as a recorded video with no transcript.
- `FEEG1002 Lecture 5 - Statics 1 - Beams, Shear Force and Bending moment - October 2024.txt` (Lecture 5): beam examples (ll. 20–74), supports (ll. 75–176), loads (ll. 177–213), internal forces (ll. 214–273), offset force (ll. 274–351), cantilever with end load (ll. 352–458), sign convention (ll. 459–498), diagrams (ll. 499–583), procedure and resultants (ll. 584–676), tutorial (ll. 686–702).
- `FEEG1002 Lecture 6 - Statics 1 - Relationships w, SF and BM - Nov 2024.txt` (Lecture 6): overhanging-beam example (ll. 10–366), indeterminate beams flagged (ll. 367–385), derivation of $dQ/dx=-w$ and $dM/dx=Q$ (ll. 438–591), maxima and areas (ll. 596–622), central point load (ll. 624–716), uniform load (ll. 717–813), moment jumps (ll. 814–841), tutorial and video (ll. 842–848).
- Tutorial Sheet 03 and its official solutions: Q1–Q3 and additional Q1–Q3.
- All numbers recomputed in Python; every SF and BM diagram is computed, not sketched.

## Self-study tasks

### Core

- [ ] Rework the overhanging-beam example by cutting at n–n′, m–m′ and o–o′, then check the end values (L6, ll. 10–335). → [[#Example: overhanging beam with a point load and a distributed load]]
- [ ] Derive $dQ/dx=-w$ and $dM/dx=Q$ from a slice, explaining where the minus sign and the dropped $(dx)^2$ term come from (L6, ll. 438–591; the meaning of $dQ$ and $dM$ at ll. 520–525). → [[#Derivation]]
- [ ] Tutorial 3 Q1: SF and BM diagrams for the overhanging beam with 8 kN and 3 kN loads (set in L5, ll. 686–702). Target $M_D=-6$ kN m. → [[#Worked example - overhanging beam by sketching]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Q1 - Overhanging beam with two point loads|Tutorial 3 Q1]]
- [ ] Tutorial 3 Q2: sketch the diagrams quickly using the relations (set in L6, ll. 842–845). Targets $M_{max}=+2.08$ kN m and $M_E=-8$ kN m. → [[#Procedure for sketching]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Q2 - UDL between supports with overhang loads|Tutorial 3 Q2]]
- [ ] Tutorial 3 Q3: integrate a parabolic distributed load. Target $M_{max}=15$ kN m. → [[#Example: linearly varying load]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Q3 - Parabolic distributed load|Tutorial 3 Q3]]

### Further practice

- [ ] Verify that the resultant of a linearly varying load acts at two-thirds of the span (deck 6, slide 26, "verify this"). → [[#Example: linearly varying load]]
- [ ] Verify that an anticlockwise applied moment, including the reaction moment at a built-in end, gives a downward jump in the BM diagram (deck 6, slide 21). → [[#Consequences]]
- [ ] Tutorial 3 additional Q1–Q3: equal and opposite loads, a cantilever with a UDL and a point load, and a beam with an applied couple. Targets 6 kN and 2 kN m; −98 kN m; a jump from −2 to +6 kN m. → [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Extra Q1 - Equal and opposite loads|Tutorial 3 Extra Q1]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Extra Q2 - Cantilever with UDL and point load|Extra Q2]] · [[FEEG1002 Statics 1 Tutorial 3 - Shear Force and Bending Moment Solutions#Extra Q3 - Point load and applied couple|Extra Q3]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 5, ll. 151–153, 342, 381, 444 and 502)
> Where: [[#Supports]] · [[#Example: an offset tensile force]] · [[#Example: a cantilever with an end load]] · [[#3. The sign convention]].
>
> The reactions at a built-in support are listed as "rotational, horizontal, … reaction moment"; they are a vertical force, a horizontal force and a reaction moment. In the offset-force example the internal moment is said to maintain "horizontal equilibrium" (l. 342); it maintains rotational equilibrium. In the cantilever example the shear force is said to maintain "horizontal equilibrium" (l. 381); it maintains vertical equilibrium. The "maximum of 1000 times L" at the wall (l. 444) is a magnitude; with the sign convention it is $-1000L$, hogging. At l. 502 the anticlockwise quantity on the cut face is called the "shear force M"; it is the bending moment.

> [!warning] Transcript slips (Lecture 6, ll. 44, 271, 403, 463, 599–604, 614–622 and 689–690)
> Where: [[#Example: overhanging beam with a point load and a distributed load]] · [[#Consequences]].
>
> The resultant of the distributed load is read as "10,000 meters" (l. 44) and the right reaction as "30,000" (l. 271); they are 10 000 N and 13 000 N. At l. 403 the bending moment is said to go "negative to negative"; it goes from positive to negative. At l. 463 "bending moment Q and M" should be "shear force Q and bending moment M". At ll. 599–604, $dM/dx=0$ is said to give "a maximum"; it gives a stationary point, a maximum or a minimum, and in the worked example the largest $|M|$ is at B, where $Q$ jumps from −3000 to +10 000 N without passing through zero. At ll. 614–622 the moment at a point is "the area under the curve"; that holds only measured from a point where $M=0$ with no couple in between, and the general statement $M(x_2)-M(x_1)=\int Q\,dx$ is given correctly at ll. 786–787. At ll. 689–690 the left support is called "the pin support, so it's a roller support"; it is the pin, and both supports leave the beam free to rotate, which is why $M=0$ there.

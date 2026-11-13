---
title: "FEEG1002 A7 - Euler Buckling of Struts"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 7
tags: [feeg1002, statics, buckling, euler, effective-length, stability, struts]
aliases: ["Statics 1 Lecture 12", "Buckling", "Euler critical buckling load", "P crit"]
date: 2026-11-05
status: lectured
coverage: "Statics 1 Lecture 12 (9 Dec 2024, ll. 10–631: instability of slender struts, pin-ended strut, Euler critical load, buckling modes, direction of buckling, effective length for built-in ends, truss brace design); slide deck 12 in full"
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]", "[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 A8 - Torsion of Circular Shafts]]"]
key_concepts: ["[[Euler Buckling]]", "[[Effective Length]]", "[[Slenderness Ratio]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources:
  - "02 - Sources/Statics 1/Lectures/Lecture 12 - Buckling.pdf"
  - "02 - Sources/Lectures/FEEG1002 Lecture 12 - Statics 1 - Buckling - December 2024.txt"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress.pdf"
  - "02 - Sources/Statics 1/Tutorials/Tutorial Sheet 06 - Buckling, Torsion and Shear Stress - Solutions.pdf"
---

# FEEG1002 A7 - Euler Buckling of Struts

> [!abstract] Summary
> A short, wide column under compression just shortens, but a long, slender strut becomes unstable at a critical load and suddenly bows sideways, usually well before the material reaches its allowable stress. Writing the bending moment on the deflected shape, $M=Pv$, turns $EI\,v''=-M$ into $v''+n^2v=0$ with $n^2=P/EI$; the boundary conditions of a pin-ended strut allow a non-zero deflection only when $\sin nL=0$, and the lowest such load is the Euler critical load $P_{crit}=\pi^2EI/L^2$. Other end conditions are handled with an effective length, the length of one half sine wave in the buckled shape: $P_{crit}=\pi^2EI/L_e^2$, with $L_e=2L$ built in and free, $L/2$ built in at both ends and $0.699L$ built in and pinned. The strut buckles about the axis of least second moment of area.

> [!summary]- Exam use: quick path
> - **Use it when:** a slender member is in compression (a column, a strut, a truss bar in compression) and its failure load is wanted.
> - **Assumptions:** perfectly straight, linear elastic strut; load exactly along the axis; small deflections, so $EI\,v''=-M$ holds; ends fixed against sideways movement unless free; the result gives the onset of buckling only.
> - **Method:** 1. Identify the end conditions and the effective length $L_e$ in each plane. 2. Find the second moment of area about both principal axes of the section. 3. Evaluate $P_{crit}=\pi^2EI/L_e^2$ for each plane and take the smallest. 4. Compare with the load the material could carry in compression, $\sigma_{allow}A$, to see which limit governs. 5. If an intermediate support restrains lateral movement, use the shorter half-wave as $L_e$.
> - **Common mistakes:** using the larger second moment of area; forgetting that $L_e$ is squared, so halving it quadruples the load.
> - **Practise:** [[#Worked example - tube strut with different end conditions]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q1 - Pin-ended I-section column|Tutorial 6 Q1]]

A short, fat cylinder squeezed between two plates shortens a little, bulging slightly sideways through the Poisson effect, and the deformation grows gradually as the force increases. A long, slender strut, such as a ruler held upright between the palms, also shortens at first. Once a critical force is exceeded it suddenly bows out sideways and collapses. The strut has become unstable: it has buckled.

Buckling differs in kind from failures analysed on the undeformed geometry (A1 to A6), where deformations are small enough not to change the forces. In a strut the deflection itself changes the bending moment. A strut that bows by $v$ puts the axial load a distance $v$ off the axis, which bends it further, which moves the load further off the axis. Below the critical load the beam's stiffness wins and the strut stays straight; above it the feedback wins and the strut collapses.

For a slender strut this happens long before the stress in the material reaches its allowable value, which is why buckling, not yielding, is the dominant failure mode of slender compression members: the struts of a truss, the pillars of a roof, the stringers of an aircraft panel.

---

## 1. The pin-ended strut

### Bending moment on the deflected shape

The strut is taken horizontal, with a pin at the left end ($x=0$) and a roller at the right end ($x=L$), loaded by a compressive force $P$ along its axis. At the onset of buckling the strut is effectively a beam bending under an axial load, and the load at which a deflected shape can stay in equilibrium, instead of returning to the straight, undeformed state, is the critical load. Let it have deflected into some shape $v(x)$, measured downwards as before.

The free body diagram of the whole strut has $P$ at each end and no transverse loads, so the pin carries only the axial reaction $P$. Cut at $x$ and keep the left part, with the positive bending moment $M$ (sagging, anticlockwise on the right-hand face) and the shear force $Q$ on the cut face. The axial load $P$ at the pin acts along the original axis, but the cut face has moved down by $v(x)$, so the line of action of $P$ is a distance $v$ from the centre of the cut. Rotational equilibrium about the cut face gives

$$
M=Pv
$$

![[s1_buckling_strut_fbd.png|900]]

As the deflection increases the bending moment increases too. That is the unstable feedback: if the extra bending outruns the beam's resistance, the strut bends further until it fails.

### The governing equation

Use the moment–deflection relation of [[FEEG1002 A5 - Beam Deflection and Macaulay's Method#Sign convention|A5]]:

$$
M=-EI\frac{d^2v}{dx^2}
$$

$$
EI\frac{d^2v}{dx^2}=-Pv
$$

$$
EI\frac{d^2v}{dx^2}+Pv=0
$$

This is a second-order ordinary differential equation in $v$. It cannot be integrated twice directly as in A5, because both $v$ and $d^2v/dx^2$ appear. Divide by $EI$:

$$
\frac{d^2v}{dx^2}+\frac{P}{EI}v=0
$$

and define

$$
n^2=\frac{P}{EI}
$$

which is positive because $P$, $E$ and $I$ are. Then

$$
\frac{d^2v}{dx^2}+n^2v=0
$$

### Solving it

One possible solution is $v=\sin(nx)$, since

$$
\frac{dv}{dx}=n\cos(nx),\qquad\frac{d^2v}{dx^2}=-n^2\sin(nx)=-n^2v
$$

and $\cos(nx)$ works in the same way. The general solution is the combination

$$
v=A\sin(nx)+B\cos(nx)
$$

with constants $A$ and $B$ fixed by the boundary conditions. (The choice of $n^2$ rather than $n$ in the definition is what makes this solution so neat.)

### Boundary conditions

Both ends are pinned, so the deflection is zero at each. At $x=0$:

$$
0=A\sin0+B\cos0=B
$$

$$
B=0
$$

At $x=L$:

$$
0=A\sin(nL)
$$

There are two distinct ways for this product to be zero.

The first is $A=0$: no lateral deflection at all. The strut stays straight, which is stable only below the critical load.

The second is $\sin(nL)=0$, which has infinitely many solutions:

$$
nL=0,\ \pi,\ 2\pi,\ 3\pi,\ \dots
$$

The first, $n=0$, means $P=0$ from $n^2=P/EI$: no load on the beam, a trivial solution. The next is $nL=\pi$. Then

$$
n^2=\frac{\pi^2}{L^2}=\frac{P}{EI}
$$

$$
\boxed{P=P_{crit}=\frac{\pi^2EI}{L^2}}
$$

the **Euler critical buckling load** for a pin-ended strut, named after Leonhard Euler (Basel 1707 – St Petersburg 1783). The deflected shape is

$$
v=A\sin\left(\frac{\pi x}{L}\right)
$$

half a sine wave.

### What the arbitrary amplitude means

At $P=P_{crit}$ the amplitude $A$ can take any value: the strut can sit in the straight position or in a bowed position of any size, and equilibrium holds in all of them. The strut is in **neutral equilibrium**, like a ball on a flat table, and the smallest disturbance moves it into a deflected shape with nothing to bring it back. That load is therefore the critical value that causes instability.

- For $P<P_{crit}$, $\sin(nL)=0$ cannot be satisfied, so $A=0$: the strut remains straight and stable in simple compression.
- For $P=P_{crit}$, the strut is in neutral equilibrium and can adopt a half sine wave of arbitrary amplitude.
- For $P>P_{crit}$, the strut is unstable and collapses.

The analysis uses small-deflection bending theory, which is strictly valid only for small deformations. That is enough to describe the onset of buckling, which is all that is needed, but it cannot predict how far the strut bows once it has buckled.

> [!warning] There is no such thing as a perfect strut
> The theory assumes a perfectly straight strut loaded exactly along its axis, a ball balanced on the tip of a pyramid. Real struts are slightly crooked and real loads slightly off-centre, so a real strut starts to bow before $P_{crit}$ and may fail below it. Even carefully aligned roof pillars should not be designed to reach $P_{crit}$; it is an upper bound.

### Higher modes

The higher roots give other shapes:

| $nL$ | $P$ | Shape |
|---|---|---|
| $\pi$ | $P_{crit}$ | half a sine wave |
| $2\pi$ | $4P_{crit}$ | one full sine wave |
| $3\pi$ | $9P_{crit}$ | one and a half sine waves |

since $P=n^2EI=(nL)^2EI/L^2$. Under normal circumstances these **buckling modes** are never reached, because the strut fails at $P_{crit}$ first. The exception is when lateral displacement is constrained. If the mid-point of a pin-ended strut is held so that it cannot move sideways (but can rotate), the half-wave shape becomes impossible; the strut must buckle in the full-wave mode, at four times the load.

![[s1_buckling_higher_modes.png|900]]

## 2. Direction of buckling

The critical load is proportional to the second moment of area of the cross-section:

$$
P_{crit}=\frac{\pi^2EI}{L^2}
$$

A strut with a non-circular section has different second moments about its two principal axes, and it buckles in the direction that has the smallest one. A flat strip or ruler, with $I=bt^3/12$ about one axis and $tb^3/12$ about the other, buckles by deflecting in its thin direction, so that the broad face bows, and never edgewise. The critical load also depends on the square of the length, so doubling the length of a strut divides its buckling load by four.

## 3. Boundary conditions and effective length

### The idea

The same procedure, the general solution with the boundary conditions of the particular problem, gives the critical load for any end conditions. More insight comes first from looking at the expected shape of deformation, and comparing it with the pin-ended strut, whose buckled shape is one half sine wave between the ends.

In general, the buckling load can be related to the reference case of the pin-ended strut through an **effective length** $L_e$:

$$
\boxed{P_{crit}=\frac{\pi^2EI}{L_e^2}}
$$

$L_e$ is the length of the equivalent pin-ended strut with the same critical load, which is the length of one half sine wave in the buckled shape.

### Built in at one end, free at the other

A column built into a wall at $x=0$ and free at $x=L$, where it carries the load $P$, behaves like a flagpole. At the built-in end the slope is zero, because rotation is suppressed; the free end can deflect and rotate.

The buckled shape is a quarter sine wave. Mirrored about the wall, the original and its image together form a half sine wave of length $2L$, a pin-ended strut twice as long. So

$$
L_e=2L,\qquad P_{crit}=\frac{\pi^2EI}{(2L)^2}=\frac{\pi^2EI}{4L^2}
$$

a quarter of the pin-ended value.

The same result follows formally. Let the free end deflect by $\delta$. The load acts along a line a distance $\delta$ from the original axis, so at a cut at $x$ its lever arm is $\delta-v$, and

$$
M=-P(\delta-v)
$$

hogging at the wall, where $M=-P\delta$. Then

$$
EI\frac{d^2v}{dx^2}=P(\delta-v)
$$

$$
\frac{d^2v}{dx^2}+n^2v=n^2\delta
$$

whose general solution is the homogeneous solution plus the constant particular solution $\delta$:

$$
v=A\sin(nx)+B\cos(nx)+\delta
$$

At the wall $v(0)=0$, so $B=-\delta$, and $dv/dx(0)=0$, so $An=0$ and $A=0$:

$$
v=\delta\left(1-\cos(nx)\right)
$$

At the free end $v(L)=\delta$:

$$
\delta\left(1-\cos(nL)\right)=\delta
$$

$$
\delta\cos(nL)=0
$$

A non-zero deflection needs $\cos(nL)=0$, whose lowest root is $nL=\pi/2$, giving $P=n^2EI=\pi^2EI/4L^2$ and the quarter-wave shape $1-\cos(\pi x/2L)$.

### Built in at both ends

Now both ends are built in, with no lateral movement of the supports. The slope is zero at $x=0$ and at $x=L$, since rotation is suppressed at both ends. The column follows a complete sine wave: a quarter wave out of each end and a half wave in the middle. The middle half wave, of length $L/2$, is the equivalent pin-ended strut:

$$
L_e=\frac12L,\qquad P_{crit}=\frac{\pi^2EI}{(L/2)^2}=\frac{4\pi^2EI}{L^2}
$$

four times the pin-ended value. The strut has to come out of each wall straight and then bend back, which takes more force.

Formally, each wall supplies a fixing moment $M_0$, so the bending moment at a cut is $M=Pv-M_0$ and

$$
\frac{d^2v}{dx^2}+n^2v=\frac{M_0}{EI}
$$

$$
v=A\sin(nx)+B\cos(nx)+\frac{M_0}{P}
$$

$v(0)=0$ gives $B=-M_0/P$ and $dv/dx(0)=0$ gives $A=0$, so $v=(M_0/P)(1-\cos nx)$. Then $v(L)=0$ needs $\cos(nL)=1$, whose lowest non-zero root is $nL=2\pi$, so $P=4\pi^2EI/L^2$; the slope $\sin(nL)$ then vanishes at $x=L$ as well.

### Built in at one end, pinned at the other

With one end built in and the other pinned, the shape is more complicated and is not a pure sine wave. The pinned end supplies a lateral reaction $H$ as well as $P$, so at a cut the bending moment from the right-hand part is $M=Pv+H(L-x)$, and

$$
\frac{d^2v}{dx^2}+n^2v=-\frac{H}{EI}(L-x)
$$

$$
v=A\sin(nx)+B\cos(nx)-\frac HP(L-x)
$$

The built-in end gives $v(0)=0$, so $B=HL/P$, and $dv/dx(0)=0$, so $An+H/P=0$ and $A=-H/(nP)$. The pinned end gives $v(L)=0$:

$$
-\frac{H}{nP}\sin(nL)+\frac{HL}{P}\cos(nL)=0
$$

$$
\tan(nL)=nL
$$

This has no neat closed-form root; numerically the lowest non-zero root is $nL=4.4934$, so

$$
P_{crit}=\frac{(4.4934)^2EI}{L^2}=2.046\frac{\pi^2EI}{L^2},\qquad L_e=\frac{\pi}{4.4934}L=0.699L
$$

between the two cases that bracket it, $\tfrac12L<L_e<L$.

### Summary

Increasing the constraint at the ends reduces the effective length and increases the critical buckling force. Writing $P_E=\pi^2EI/L^2$ for the pin-ended value ($F$ in the slides):

| End conditions | Buckled shape | $L_e$ | $P_{crit}$ |
|---|---|---|---|
| Built in, free | quarter sine wave | $2L$ | $\tfrac14P_E$ |
| Pinned, pinned | half sine wave | $L$ | $P_E$ |
| Built in, pinned | not a sine wave | $0.699L$ | $2.05P_E$ |
| Built in, built in (no sway) | full sine wave | $\tfrac12L$ | $4P_E$ |

![[s1_buckling_mode_shapes.png|900]]

Because $L_e$ enters squared, the end conditions often matter more than the choice of section. Only the cases where the shape is a sine wave are derived here; the built-in and pinned case is quoted.

## 4. Design implications: truss braces

A truss bar in compression is a pin-ended strut ([[FEEG1002 A2 - Pin-Jointed Trusses#Strength and buckling|A2]]). Its buckling load falls with the square of its length, while a bar in tension has no such limit. The diagonal braces of a truss are its longest members, so they should be arranged to be in tension, leaving the shorter members to carry the compression. Timber trusses are an exception: their joints are weaker in tension than the members are in buckling, and the braces are often set to be in compression for that reason.

---

## Worked examples

### Worked example - pin-ended I-section column

Tutorial 6 Q1 (I-beam buckling direction) is a stainless steel column 5 m long, pinned at both ends, $E=213$ GPa, with flanges 40 × 10 mm and a web 5 × 30 mm, 50 mm deep overall. Find the minimum buckling load, and the factor by which it rises if a pin at mid-height prevents sideways movement.

The section is doubly symmetric. About the axis parallel to the flanges, the flanges' centroids are 20 mm from it:

$$
I_{zz}=2\left(\frac{40(10)^3}{12}+400(20)^2\right)+\frac{5(30)^3}{12}=3.38\times10^{-7}\ \mathrm{m^4}
$$

About the web's axis, every part is centred on it and the flanges are 40 mm wide in this direction:

$$
I_{yy}=2\left(\frac{10(40)^3}{12}\right)+\frac{30(5)^3}{12}=1.07\times10^{-7}\ \mathrm{m^4}
$$

The column buckles about the weaker axis:

$$
P_{crit}=\frac{\pi^2(213\times10^9)(1.07\times10^{-7})}{(5)^2}=9.0\ \mathrm{kN}
$$

against 28.4 kN about the other axis. The average stress at buckling is $9000/950\times10^{-6}=9.5$ MPa, a tiny fraction of the yield stress of any steel: this column fails by buckling long before the material is in danger.

A pin at mid-height stops sideways movement there in both planes but not rotation. The half-wave mode is suppressed and the column must buckle in the full sine wave, with $L_e=L/2$:

$$
P_{crit}'=\frac{\pi^2EI}{(L/2)^2}=4P_{crit}=36.0\ \mathrm{kN}
$$

### Worked example - a ruler

A steel ruler 300 mm long, 25 mm wide and 1 mm thick ($E=200$ GPa) is pushed end to end between the palms, which act as pins. About its thin direction $I=25(1)^3/12=2.08$ mm⁴:

$$
P_{crit}=\frac{\pi^2(200\times10^9)(2.08\times10^{-12})}{(0.3)^2}=45.7\ \mathrm N
$$

On edge, $I=1(25)^3/12=1302$ mm⁴ and $P_{crit}$ would be 28.6 kN, but the ruler buckles flat long before that. The load needed to yield the ruler in compression, at 250 MPa over 25 mm², is 6.25 kN, more than a hundred times its buckling load.

### Worked example - tube strut with different end conditions

A steel tube, 50 mm outside and 44 mm inside diameter, 2.5 m long, $E=210$ GPa and yield stress 250 MPa, is used as a strut.

$$
I=\frac{\pi(50^4-44^4)}{64}=1.228\times10^{-7}\ \mathrm{m^4},\qquad A=\frac{\pi(50^2-44^2)}{4}=443\ \mathrm{mm^2}
$$

The load at which it would yield is $250\times443=110.7$ kN. The buckling loads are:

| End conditions | $L_e$ (m) | $P_{crit}$ (kN) | Governs |
|---|---|---|---|
| Built in, free | 5.0 | 10.2 | buckling |
| Pinned, pinned | 2.5 | 40.7 | buckling |
| Built in, pinned | 1.75 | 83.4 | buckling |
| Built in, built in | 1.25 | 162.9 | yield (110.7 kN) |

Built in at both ends, the tube is no longer slender in the buckling sense and the material yields first. A solid bar with the same area (23.7 mm diameter) has a second moment of area 7.9 times smaller, so pinned at both ends it would buckle at only 5.2 kN: hollow sections give far more $I$ for the same material.

### Worked example - which way round should the braces go

The example truss is a cantilever of three square bays, 1 unit on a side, pinned to a wall at the top-left joint, held by a wall roller at the bottom-left joint, with a load $F$ hanging from the bottom-right tip. Solving it by the method of joints with the diagonals running down to the right (as drawn), and again with them running up to the right:

| Members | Diagonals down to the right | Diagonals up to the right |
|---|---|---|
| Diagonals of the first two bays (length $\sqrt2$) | $+1.41F$ (tension) | $-1.41F$ (compression) |
| Loaded verticals (length 1) | $-F$ (compression) | $+F$ (tension) |
| Top chord | $+F$ to $+2F$ | $+2F$ to $+3F$ |
| Bottom chord | $-F$ to $-3F$ | $-F$ to $-2F$ |

The end diagonal, which meets the load, is in tension, $+1.41F$, in both arrangements, and one vertical is unloaded in each. With the diagonals running down to the right, the long members are in tension and the shorter verticals take the compression. Reversed, the diagonals become struts carrying $1.41F$ over a length $\sqrt2$ times that of a vertical, so their buckling load is halved while their force is 41 % higher. The braces as drawn are the right way round.

![[s1_truss_brace_orientation.png|900]]

---

## Links

- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Previous: [[FEEG1002 A6 - Statically Indeterminate Beams]] · Next: [[FEEG1002 A8 - Torsion of Circular Shafts]]
- Concepts: [[Euler Buckling]] · [[Effective Length]] · [[Slenderness Ratio]]
- Worked sheet: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]] · Formula list: [[FEEG1002 Formula Sheet]]
- Builds on: [[FEEG1002 A5 - Beam Deflection and Macaulay's Method|A5]] ($EI\,v''=-M$) · [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area|A4]] ($I$ of the section) · [[FEEG1002 A2 - Pin-Jointed Trusses|A2]] (bars in compression)
- Year 2: [[SESA2028 S5 - Euler Buckling and Effective Length]] rederives the eigenproblem and the effective lengths; imperfect struts, the [[Secant Formula]] and [[Beam-Column Amplification]] are in [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]], together with [[Plate Buckling]] of thin skins

## Sources

- `Lecture 12 - Buckling.pdf` (S1 Lectures 12a–12c, 26 slides), read in full.
- `FEEG1002 Lecture 12 - Statics 1 - Buckling - December 2024.txt` (Lecture 12): introduction (ll. 10–41), pin-ended strut and $M=Pv$ (ll. 42–117), solving the equation (ll. 118–198), boundary conditions and the Euler load (ll. 199–313), higher modes (ll. 315–341), stability summary and imperfect struts (ll. 342–383), direction of buckling (ll. 385–408), effective length (ll. 409–554), truss braces (ll. 555–605), exam scope (ll. 606–622).
- Tutorial Sheet 06 and its official solutions: Q1.
- All numbers recomputed in Python, including the root of $\tan nL=nL$ and a joint-equilibrium solve of both brace arrangements.

## Self-study tasks

### Core

- [ ] Derive the Euler load from $M=Pv$, including both ways $A\sin nL=0$ can be satisfied (L12, ll. 68–305; class question at ll. 232–240). → [[#1. The pin-ended strut]]
- [ ] Sketch the first three buckling modes with their loads, and explain why a mid-height restraint gives four times the load (L12, ll. 315–341). → [[#Higher modes]]
- [ ] Find the shape and effective length of a column built in at both ends (class question, L12, ll. 483–507). Target $L_e=L/2$. → [[#Built in at both ends]]
- [ ] Tutorial 6 Q1: minimum buckling load of the I-section column and the effect of a mid-height pin (direction of buckling flagged as a tutorial question in L12, l. 408). Targets 9.0 kN and a factor of 4. → [[#Worked example - pin-ended I-section column]] · [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions#Q1 - Pin-ended I-section column|Tutorial 6 Q1]]

### Further practice

- [ ] Decide which way round the diagonal braces of the cantilever truss should go, and justify it with bar forces (class vote, L12, ll. 560–600). → [[#Worked example - which way round should the braces go]]
- [ ] Derive the built-in–free and built-in–pinned results formally from the general solution (left at "do the math", L12, ll. 416–420 and 536–544). → [[#Built in at one end, free at the other]] · [[#Built in at one end, pinned at the other]]
- [ ] Practice exam questions on Blackboard (L12, ll. 610–612). Buckling, torsion and shear stresses in beams were not in the January exam (L12, ll. 613–616); they are tested by Tutorial 6 in week 18. → [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]

## Transcript and slide slips

> [!warning] Transcript slips (Lecture 12, ll. 106, 235, 276 and 505)
> Where: [[#Bending moment on the deflected shape]] · [[#Boundary conditions]] · [[#Built in at both ends]].
>
> At l. 106 "the deflection X" should be the deflection $v$. At l. 235 the solutions of $\sin nL=0$ are offered as multiples of $2\pi$; they are multiples of $\pi$, as l. 238 restates. At l. 276 "n times x is now pi over L" should be $n=\pi/L$, so that $nx=\pi x/L$. At l. 505 the critical load is read as "pi squared over E and I divided by half L squared"; it is $\pi^2EI/(L/2)^2$. (Whisper also renders $n$ as "M" at ll. 157–277.)

> [!warning] Slide notation (deck 12, slide 24)
> Where: [[#Summary]].
>
> The summary slide writes the critical loads as $\tfrac14F$, $F$ and $4F$, using $F$ for the pin-ended Euler load $\pi^2EI/L^2$, although $F$ was the applied compressive force on slides 2–3. The note writes $P_E$ for the reference value.

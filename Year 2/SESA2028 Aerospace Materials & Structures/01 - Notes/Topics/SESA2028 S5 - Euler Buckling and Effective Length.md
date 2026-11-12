---
title: "SESA2028 S5 - Euler Buckling and Effective Length"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 5
tags: [sesa2028, structures, buckling, stability]
date: 2026-10-30
status: lectured
coverage: "SL13 (2026-04-22, ll. 150–424) and SL14 (2026-04-24, ll. 1–200)"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S2 - Beam Deflection and Bending Design]]", "[[SESA2028 S7 - Strain Energy and Conservation of Energy]]"]
next_topics: ["[[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]"]
key_concepts: ["[[Euler Buckling]]", "[[Effective Length]]", "[[Slenderness Ratio]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 4 - Buckling Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL6 Instability and Euler buckling theory.pdf", "02 - Sources/Structures Lectures/SL7 buckling of beams with imperfection.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-22.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-24.txt"]
---

# SESA2028 S5 - Euler Buckling and Effective Length

> [!abstract] Summary
> Buckling is a structural instability, not a material failure: a perfectly straight column under axial compression stays straight up to a critical load and then deflects sideways, losing most of its stiffness. Writing the column's equilibrium in its deflected shape, $EIv''+Pv=0$, gives non-zero solutions only for $P=n^2\pi^2EI/L^2$, an eigenvalue problem whose lowest value is the Euler load $P_{cr}=\pi^2EI/L^2$ for pinned ends. Other supports change it through the effective length, $P_{cr}=\pi^2EI/(KL)^2$, and the slenderness ratio $KL/\kappa$ decides whether a column buckles or yields first.

> [!summary]- Exam use: quick path
> - **Use it when:** a strut or column carries compression and you need its critical load, critical stress or safety factor against buckling.
> - **Assumptions:** initially perfectly straight, uniform, homogeneous, isotropic and linear elastic; load through the centroid; small deflections; buckling about the axis of least $I$.
> - **Method:** 1. Identify the end conditions and $K$. 2. $I_{min}$ and $A$, $\kappa=\sqrt{I/A}$. 3. $P_{cr}=\pi^2EI_{min}/(KL)^2$. 4. $\sigma_{cr}=P_{cr}/A$ against $\sigma_Y$: the lower governs. 5. Safety factor $P_{cr}/P$.
> - **Common mistakes:** using $I_{max}$; forgetting $K=2$ for a cantilever column.
> - **Practise:** [[#Worked example: two columns]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q1 - Eccentrically loaded tubular column|Tutorial 4 Q1]]

Buckling is among the most important topics for thin-walled aerospace structures. A ruler held upright and pressed gently at its top does nothing; at some larger load it suddenly bows sideways, after which it carries little more.

Stability can be pictured as a ball on a landscape. In a valley a nudged ball rolls back (stable); on a hilltop it rolls away (unstable); on a flat plain it stays where it is put (neutral). All three balls are in equilibrium; what differs is what a small disturbance does. A straight column is in equilibrium at every load, but the landscape changes as the load grows: below the critical load the straight shape sits in a valley, above it on a hilltop, and exactly at the critical load the ground is flat, so a bent shape is just as acceptable as the straight one. That load is the buckling load.

## 1. Stability and equilibrium

### The rigid bar

A rigid bar of length $L$ is hinged at its base and loaded by a vertical force $F$ at its top. Upright, it is in equilibrium whichever way $F$ acts. Nudged sideways, a downward (compressive) $F$ pushes it further away, so the equilibrium is unstable; an upward (tensile) $F$ pulls it back, so it is stable. Buckling concerns compression only.

Add a horizontal spring of stiffness $k$ at the top. For a small sideways displacement $x$ of the top, the load's moment about the hinge, tending to topple the bar, is $Fx$, and the spring's restoring moment is $(kx)L$. So

$$
Fx<kxL\ \ \text{stable},\qquad Fx>kxL\ \ \text{unstable},\qquad Fx=kxL\ \ \text{neutral}.
$$

Equilibrium, $Fx=kxL$, has two families of solutions: $x=0$ at any load, and any $x$ at $F=kL$. The second branch meets the first at the **bifurcation point** $F_{cr}=kL$, where the straight configuration changes from stable to unstable. Changes in stability (buckling) occur at bifurcation points.

### The same result from energy

For a conservative system with total potential energy $\Pi$, equilibrium is $d\Pi/dq=0$ for the displacement $q$, and the second derivative classifies it: positive is stable (a valley), negative unstable (a hilltop), zero neutral. When the bar tilts by $\theta$, the spring stretches $L\sin\theta$ and stores $\tfrac12k(L\sin\theta)^2$; the top drops $L(1-\cos\theta)$, so the load loses potential energy $FL(1-\cos\theta)$:

$$
\Pi(\theta)=\tfrac12k(L\sin\theta)^2-FL(1-\cos\theta).
$$

Differentiate:

$$
\frac{d\Pi}{d\theta}=kL^2\sin\theta\cos\theta-FL\sin\theta=L\sin\theta\left(kL\cos\theta-F\right).
$$

This is zero at $\theta=0$ (the upright bar) or at $\cos\theta=F/kL$, a tilted position that exists only for $F\le kL$. The second derivative at $\theta=0$ is

$$
\left.\frac{d^2\Pi}{d\theta^2}\right|_{\theta=0}=kL^2-FL,
$$

positive for $F<kL$ and negative for $F>kL$: the upright bar is stable below $F_{cr}=kL$ and unstable above it, the same bifurcation load as the moment argument.

![[structures_s5_stability_and_slenderness.png|900]]

### Why buckling matters

Once a structure buckles, its stiffness, the slope of load against deflection, drops sharply, in columns and plates alike. Three categories appear. In classical (bifurcation) buckling the structure passes from its unbuckled shape to an infinitesimally close buckled one, as for a column. In snap-back buckling, seen in thin cylinders under axial compression and spheres under external pressure, the stiffness loss is so great that the buckled shape can only be held by returning to a lower load. In snap-through (oil-canning), as in a shallow curved beam loaded transversely, the structure jumps visibly from one equilibrium to another with much larger displacements. Real failures include glider wing skins buckling locally under compression, stainless-steel wine tanks buckling in an earthquake, and the container ship MOL Comfort, which broke in two in 2008 under severe hogging.

The critical load depends on $E$ and the geometry but not on the yield stress: buckling is a geometric (structural) failure, not a material one. A material with a higher yield stress does not buckle at a higher load.

## 2. The pinned column

A column of length $L$, pinned at both ends, carries an axial compressive load $P$ through its centroid. In a slightly deflected shape with lateral deflection $v(x)$, moment equilibrium of the free body below a cut at $x$, about the cut, gives

$$
M(x)-Pv(x)=0\quad\Longrightarrow\quad M(x)=Pv(x).
$$

The load now has a lever arm, $v$, which it did not have while the column was straight: that is the coupling between axial load and bending that drives buckling. With the moment–curvature relation of [[SESA2028 S2 - Beam Deflection and Bending Design#2. Moment, curvature and deflection|S2]], $M=-EI\,d^2v/dx^2$:

$$
-EI\frac{d^2v}{dx^2}=Pv\quad\Longrightarrow\quad EI\frac{d^2v}{dx^2}+Pv=0 .
$$

Divide by $EI$ and write $\mu^2=P/EI$:

$$
\frac{d^2v}{dx^2}+\mu^2v=0 .
$$

The general solution is

$$
v(x)=A\sin\mu x+B\cos\mu x ,
$$

as substituting back confirms: $v''=-\mu^2(A\sin\mu x+B\cos\mu x)=-\mu^2v$. The pins give two boundary conditions. At $x=0$, $v=0$:

$$
0=A\cdot0+B\cdot1\quad\Longrightarrow\quad B=0 .
$$

At $x=L$, $v=0$:

$$
A\sin\mu L=0 .
$$

Either $A=0$, the straight column $v\equiv0$, which satisfies equilibrium at any load, or

$$
\sin\mu L=0\quad\Longrightarrow\quad\mu L=n\pi,\quad n=1,2,3,\dots
$$

Square and use $\mu^2=P/EI$:

$$
P_n=\frac{n^2\pi^2EI}{L^2},\qquad v_n(x)=A\sin\frac{n\pi x}{L}.
$$

This is an eigenvalue problem: the loads $P_n$ are the eigenvalues and the half-sine shapes the eigenvectors, the buckling modes. The column stays straight until the lowest, $n=1$:

$$
\boxed{P_{cr}=\frac{\pi^2EI}{L^2}}
$$

the Euler load. Higher modes would need the column restrained at the nodes of the lower ones. The amplitude $A$ stays undetermined: linear theory says the column can take any small deflection at $P_{cr}$, the neutral equilibrium of §1, which is why the load–deflection graph of a perfect column is a horizontal line at $P_{cr}$. The result says that stiffer materials (higher $E$) resist buckling better, that the column buckles about the axis with the smaller second moment, so $I_{min}$ is used ([[Euler Buckling]]), and that the critical load falls as $1/L^2$.

## 3. Other end conditions and effective length

The same equilibrium, with the moments the supports add and different boundary conditions, gives a different critical load. It is written with an effective-length factor $K$ ([[Effective Length]]):

$$
P_{cr}=\frac{\pi^2EI}{(KL)^2}.
$$

### Fixed–free (a cantilever column)

The base is clamped at $x=0$ and the top is free; under $P$ the top deflects sideways by $\delta$. At a cut at height $x$ the load acts at lever arm $\delta-v$ and bends the column further towards the deflected side, so

$$
EI\frac{d^2v}{dx^2}=P(\delta-v)\quad\Longrightarrow\quad\frac{d^2v}{dx^2}+\mu^2v=\mu^2\delta .
$$

The general solution adds the particular solution $v=\delta$:

$$
v=A\sin\mu x+B\cos\mu x+\delta .
$$

At the clamp, $v(0)=0$ gives $B=-\delta$, and $v'(0)=0$ gives $A\mu=0$, so $A=0$:

$$
v=\delta\left(1-\cos\mu x\right).
$$

At the top, $v(L)=\delta$:

$$
\delta\left(1-\cos\mu L\right)=\delta\quad\Longrightarrow\quad\delta\cos\mu L=0 .
$$

For $\delta\ne0$, $\cos\mu L=0$, and the lowest root is $\mu L=\pi/2$:

$$
P_{cr}=\frac{\pi^2EI}{4L^2}=\frac{\pi^2EI}{(2L)^2},\qquad K=2 .
$$

The cantilever column of length $L$ buckles like one half of a pinned column of length $2L$.

### Fixed–fixed

Both ends are clamped, so each carries an end moment $M_0$ and the moment at a cut is $Pv-M_0$:

$$
EI\frac{d^2v}{dx^2}=-Pv+M_0\quad\Longrightarrow\quad\frac{d^2v}{dx^2}+\mu^2v=\frac{M_0}{EI}.
$$

The solution is $v=A\sin\mu x+B\cos\mu x+M_0/P$. At $x=0$, $v=0$ gives $B=-M_0/P$ and $v'=0$ gives $A=0$:

$$
v=\frac{M_0}{P}\left(1-\cos\mu x\right).
$$

At $x=L$, $v=0$ requires $\cos\mu L=1$ (and then $v'(L)=\tfrac{M_0}{P}\mu\sin\mu L=0$ too), so the lowest non-zero root is $\mu L=2\pi$:

$$
P_{cr}=\frac{4\pi^2EI}{L^2}=\frac{\pi^2EI}{(L/2)^2},\qquad K=0.5 .
$$

The buckled shape $1-\cos(2\pi x/L)$ has inflection points at $L/4$ and $3L/4$; the middle half between them is a pinned column of length $L/2$.

### Fixed–pinned

Clamped at $x=0$ and pinned at $x=L$, the column develops a horizontal reaction $H$ at the pin, which adds a moment $H(L-x)$:

$$
\frac{d^2v}{dx^2}+\mu^2v=\frac{H}{EI}(L-x),\qquad v=A\sin\mu x+B\cos\mu x+\frac HP(L-x).
$$

The clamp gives $v(0)=0$, so $B=-HL/P$, and $v'(0)=0$, so $A\mu-H/P=0$, $A=H/(P\mu)$. The pin gives $v(L)=0$:

$$
\frac{H}{P\mu}\sin\mu L-\frac{HL}{P}\cos\mu L=0\quad\Longrightarrow\quad\tan\mu L=\mu L .
$$

The lowest non-zero root, found numerically, is $\mu L=4.493$, so

$$
P_{cr}=\frac{4.493^2EI}{L^2}=\frac{20.19\,EI}{L^2}=\frac{2.05\,\pi^2EI}{L^2},\qquad K=\frac{\pi}{4.493}=0.70 .
$$

| Ends | $K$ | $P_{cr}$ |
|---|---|---|
| pinned–pinned | 1 | $\pi^2EI/L^2$ |
| fixed–free | 2 | $\pi^2EI/4L^2$ |
| fixed–pinned | 0.7 | $2.05\,\pi^2EI/L^2$ |
| fixed–fixed | 0.5 | $4\pi^2EI/L^2$ |

$KL$ is the length of the equivalent pinned column, the distance between inflection points of the buckled shape. Each extra rotational restraint shortens it.

![[structures_euler_buckling_end_conditions.png|720]]

## 4. Slenderness and the governing failure mode

The critical stress is $\sigma_{cr}=P_{cr}/A$. With the radius of gyration $\kappa=\sqrt{I/A}$, so that $I=A\kappa^2$,

$$
\sigma_{cr}=\frac{\pi^2EA\kappa^2}{A(KL)^2}=\frac{\pi^2E}{(KL/\kappa)^2}.
$$

The slenderness ratio $KL/\kappa$ gathers every geometric parameter ([[Slenderness Ratio]]). A high slenderness gives a low critical stress and a column that buckles; a low one means it will crush (yield) first. For a given load, check both: $\sigma=P/A$ against $\sigma_Y$ for material failure and against $\sigma_{cr}$ for buckling, and design to whichever is reached first. The two are equal at the transition slenderness

$$
\frac{\pi^2E}{(KL/\kappa)^2}=\sigma_Y\quad\Longrightarrow\quad\left(\frac{KL}{\kappa}\right)_t=\pi\sqrt{\frac{E}{\sigma_Y}},
$$

which for steel with $E=200$ GPa and $\sigma_Y=250$ MPa is $\pi\sqrt{800}=89$. Real columns near the transition fail below both curves, because imperfections and the onset of yield interact ([[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling|S6]]).

## Worked example: two columns

Both columns are steel, with $E=200$ GPa and $\sigma_Y=250$ MPa.

### Hollow circular cantilever column

A hollow circular column 3 m tall, clamped at the base and free at the top, has outer and inner diameters 100 mm and 80 mm and is loaded through its centroid. The section properties are

$$
A=\frac\pi4\left(100^2-80^2\right)=2827\text{ mm}^2,\qquad I=\frac{\pi}{64}\left(100^4-80^4\right)=2.898\times10^6\text{ mm}^4 .
$$

The section is round, so every axis has the same $I$. With $K=2$ for fixed–free,

$$
P_{cr}=\frac{\pi^2\times200\,000\times2.898\times10^6}{(2\times3000)^2}=158.9\text{ kN},
$$

while yield would need $\sigma_YA=250\times2827=707$ kN. The column buckles at 159 kN, at a stress of only $158\,900/2827=56$ MPa.

> [!check] Slenderness
> $\kappa=\sqrt{2.898\times10^6/2827}=32.0$ mm and $KL/\kappa=6000/32.0=187$, more than twice the transition value of 89, so buckling governs, as found. The eccentrically loaded version of this column is in [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling|S6]].

### Hollow square pinned column

A hollow square column 3 m long, pinned at both ends, 75 mm outside and 5 mm thick, carries 120 kN. The section properties are

$$
A=75^2-65^2=1400\text{ mm}^2,\qquad I=\frac{75^4-65^4}{12}=1.149\times10^6\text{ mm}^4,
$$

$$
\kappa=\sqrt{\frac{1.149\times10^6}{1400}}=28.7\text{ mm},\qquad\frac L\kappa=\frac{3000}{28.7}=105 .
$$

The axial stress is $120\,000/1400=85.7$ MPa, and

$$
P_{cr}=\frac{\pi^2\times200\,000\times1.149\times10^6}{3000^2}=252\text{ kN},
$$

a safety factor of $252/120=2.10$ against buckling and $250/85.7=2.92$ against yield. The critical stress is $\pi^2(200\,000)/105^2=180$ MPa, below $\sigma_Y$ because the slenderness exceeds 89. [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling|S6]] shows how an initial curvature erodes this margin.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S4 - Torsion of Thin-Walled Sections]] · Next: [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]
- Concepts: [[Euler Buckling]] · [[Effective Length]] · [[Slenderness Ratio]]
- Problems: [[SESA2028 Structures Tutorial 4 - Buckling Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Energy and stability: [[SESA2028 S7 - Strain Energy and Conservation of Energy]]

## Sources

- Slides: `SL6 Instability and Euler buckling theory.pdf` (stability, buckling categories, Euler derivation, effective lengths) and `SL7 buckling of beams with imperfection.pdf` (the two columns, slides 23 and 37).
- Transcripts: `SESA2028 Lecture 2026-04-22.txt` (ll. 150–424, stability and the start of the derivation) and `SESA2028 Lecture 2026-04-24.txt` (ll. 1–200, modes, end conditions, slenderness); the column examples were worked in `SESA2028 Lecture 2026-04-30.txt` (ll. 1–60).
- The root of $\tan\mu L=\mu L$ and both column examples were computed in Python (SciPy, NumPy). Figures: `generate_structures_s5_figures.py` and `generate_structures_figures.py` (end conditions).

## Self-study tasks

### Core

- [ ] Derive the Euler load and the buckling modes of a pinned column; the derivation was set to go through yourself (2026-04-22, ll. 385–424; 2026-04-24, ll. 1–120). → [[#2. The pinned column]]
- [ ] The hinged bar with a spring: stable, unstable and neutral equilibrium and the bifurcation load (2026-04-22, ll. 270–310). → [[#The rigid bar]]
- [ ] The hollow circular and hollow square columns (SL7 slides 23 and 37; 2026-04-30, ll. 1–60). → [[#Worked example: two columns]]
- [ ] Structures tutorial 4, Q1 part 1 (Euler load). → [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q1 - Eccentrically loaded tubular column|Tutorial 4 Q1]]

### Further practice

- [ ] Derive $P_{cr}$ for a fixed–free column from the same equation with $v(0)=0$, $v'(0)=0$ at the base (suggested in the lecture, 2026-04-24, ll. 140–160). → [[#Fixed–free (a cantilever column)]]
- [ ] Show that the fixed–pinned column needs $\tan\mu L=\mu L$ and find its lowest root (suggested, not lecturer-set). → [[#Fixed–pinned]]
- [ ] Use the potential energy of the spring-bar to classify the tilted equilibrium $\cos\theta=F/kL$ (suggested, not lecturer-set). → [[#The same result from energy]]

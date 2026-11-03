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
sources: ["02 - Sources/Structures Lectures/SL6 Instability and Euler buckling theory.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-22.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-04-24.txt"]
---

# SESA2028 S5 - Euler Buckling and Effective Length

> [!abstract] Summary
> Buckling is a structural instability, not a material failure: a perfectly straight column under axial compression stays straight up to a critical load and then deflects sideways, losing most of its stiffness. Solving the column's equilibrium in its deflected shape, $EIv''+Pv=0$, gives non-zero solutions only for $P=n^2\pi^2EI/L^2$, an eigenvalue problem whose lowest value is the Euler load $P_{cr}=\pi^2EI/L^2$ for pinned ends. Other supports change it through the effective length, $P_{cr}=\pi^2EI/(KL)^2$, and the slenderness ratio $KL/\kappa$ decides whether a column buckles or yields first.

> [!summary]- Exam use: quick path
> - **Use it when:** a strut or column carries compression and you need its critical load, critical stress or safety factor against buckling.
> - **Assumptions:** perfectly straight, centrally loaded, linear elastic, small deflections; buckling about the axis of least $I$.
> - **Method:** 1. Identify the end conditions and $K$. 2. $I_{min}$ and $A$, $\kappa=\sqrt{I/A}$. 3. $P_{cr}=\pi^2EI_{min}/(KL)^2$. 4. $\sigma_{cr}=P_{cr}/A$ against $\sigma_Y$: the lower governs. 5. Safety factor $P_{cr}/P$.
> - **Common mistakes:** using $I_{max}$; forgetting $K=2$ for a cantilever column.
> - **Practise:** [[#Worked example: two columns]] · [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q1 - Eccentrically loaded tubular column|Tutorial 4 Q1]]

Buckling is "one of the most important topics in the entire course" for thin-walled aerospace structures (2026-04-22, ll. 150–190). Push gently on a ruler held upright and nothing happens; push harder and at some load it suddenly bows sideways, after which it carries little more.

Stability can be pictured as a ball on a landscape. In a valley a nudged ball rolls back (stable); on a hilltop it rolls away (unstable); on a flat plain it stays where it is put (neutral). A straight column is in equilibrium at every load, but the landscape changes as the load grows: below the critical load the straight shape sits in a valley, above it on a hill, and exactly at the critical load the ground is flat and a bent shape is just as acceptable as the straight one. That is the buckling load.

## 1. Stability and equilibrium

For a conservative system with total potential energy $\Pi$, equilibrium is $d\Pi/dq=0$ for the displacement $q$, and the second derivative classifies it (2026-04-22, ll. 190–230): positive means stable, negative unstable, zero neutral ([[SESA2028 S7 - Strain Energy and Conservation of Energy|S7]] supplies the energy).

A rigid bar of length $L$ hinged at its base and loaded by a vertical force $F$ at the top is in equilibrium upright (ll. 230–270). Nudged sideways, a downward $F$ pushes it further away, unstable; an upward (tensile) $F$ pulls it back, stable. Add a horizontal spring of stiffness $k$ at the top. For a small sideways displacement $x$, the load's moment about the hinge is $Fx$ and the spring's restoring moment is $kxL$ (ll. 270–310), so

$$
Fx<kxL\ \ \text{stable},
\qquad
Fx>kxL\ \ \text{unstable},
\qquad
Fx=kxL\ \ \text{neutral}.
$$

Equilibrium $Fx=kxL$ has two solutions: $x=0$ at any load, and any $x$ at $F=kL$. The second branch meets the first at the bifurcation point $F_{cr}=kL$, where stability changes from stable to unstable: buckling.

Buckling matters because the stiffness, the slope of load against deflection, drops sharply once it occurs, in columns and in plates alike (ll. 310–350). Snap-back buckling, in thin cylinders and spherical shells, shows the load capacity dropping so far that the deflection runs backwards; snap-through, in a shallow curved beam loaded transversely, jumps between two stable states, as a lab video showed. Wing skins develop local buckles under compression and tanks buckle under external load. Buckling concerns compression only. The critical load depends on $E$ and the geometry but not on the yield stress: it is a geometric (structural) failure, not a material one (ll. 350–385).

## 2. The pinned column

A column of length $L$, pinned at both ends, carries an axial compressive load $P$ (2026-04-22, ll. 385–424; 2026-04-24, ll. 1–120). Cut at $x$ in the deflected shape, with lateral deflection $v(x)$. Moment equilibrium of the free body gives

$$
M_x-Pv=0
\quad\Longrightarrow\quad
M_x=Pv .
$$

With the moment–curvature relation $M_x=-EI\,d^2v/dx^2$,

$$
EI\frac{d^2v}{dx^2}+Pv=0 .
$$

Write $\mu^2=P/EI$:

$$
\frac{d^2v}{dx^2}+\mu^2v=0,
\qquad
v=A\sin\mu x+B\cos\mu x .
$$

The supports give $v(0)=0$, so $B=0$, and $v(L)=0$, so

$$
A\sin\mu L=0 .
$$

Either $A=0$, the straight column, which satisfies equilibrium at any load, or

$$
\sin\mu L=0
\quad\Longrightarrow\quad
\mu L=n\pi
\quad\Longrightarrow\quad
P_n=\frac{n^2\pi^2EI}{L^2},
\qquad
v=A\sin\frac{n\pi x}{L}.
$$

This is an eigenvalue problem: the loads $P_n$ are the eigenvalues and the half-sine shapes the eigenvectors, the buckling modes (2026-04-24, ll. 41–120). The column stays straight until the lowest one, $n=1$,

$$
\boxed{P_{cr}=\frac{\pi^2EI}{L^2}}
$$

the Euler load. Higher modes need the column restrained at the nodes of the lower ones. The amplitude $A$ stays undetermined: linear theory says the column can take any small deflection at $P_{cr}$, the neutral equilibrium of section 1. Buckling occurs about the axis with the smaller second moment, so use $I_{min}$ ([[Euler Buckling]]).

## 3. Other end conditions and effective length

The same differential equation with different boundary conditions gives a different critical load, written with an effective-length factor $K$ (ll. 121–160; [[Effective Length]]):

$$
P_{cr}=\frac{\pi^2EI}{(KL)^2}.
$$

| Ends | $K$ | $P_{cr}$ |
|---|---|---|
| pinned–pinned | 1 | $\pi^2EI/L^2$ |
| fixed–free | 2 | $\pi^2EI/4L^2$ |
| fixed–pinned | 0.7 | $2.05\,\pi^2EI/L^2$ |
| fixed–fixed | 0.5 | $4\pi^2EI/L^2$ |

$KL$ is the length of the equivalent pinned column: a cantilever column of length $L$ buckles like one half of a pinned column of length $2L$.

## 4. Slenderness and the governing failure mode

The critical stress is $\sigma_{cr}=P_{cr}/A$. With the radius of gyration $\kappa=\sqrt{I/A}$ (ll. 161–200; [[Slenderness Ratio]]),

$$
\sigma_{cr}=\frac{\pi^2E}{(KL/\kappa)^2}.
$$

The slenderness ratio $KL/\kappa$ gathers every geometric parameter. A high slenderness gives a low critical stress and susceptibility to buckling; a low one means the column will crush (yield) first. For a given load, check both: $\sigma=P/A$ against $\sigma_Y$ for material failure and against $\sigma_{cr}$ for buckling, and design to whichever is reached first.

## Worked example: two columns

Both from the SL7 slides and SL15 (2026-04-30, ll. 1–60), steel with $E=200$ GPa and $\sigma_Y=250$ MPa, recomputed in Python.

A hollow circular column 3 m tall, clamped at the base and free at the top, has $D_o=100$ mm and $D_i=80$ mm, loaded through its centroid (slide 23). The section properties are

$$
A=\frac\pi4\left(100^2-80^2\right)=2827\text{ mm}^2,
\qquad
I=\frac{\pi}{64}\left(100^4-80^4\right)=2.898\times10^6\text{ mm}^4 .
$$

With $K=2$,

$$
P_{cr}=\frac{\pi^2\times200\,000\times2.898\times10^6}{(2\times3000)^2}=158.9\text{ kN},
$$

while yield would need $\sigma_YA=707$ kN. The column buckles at 159 kN, at a stress of only 56 MPa. The eccentric case is in [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling|S6]].

A hollow square column 3 m long, pinned at both ends, 75 mm outside and 5 mm thick, carries 120 kN (slide 37):

$$
A=75^2-65^2=1400\text{ mm}^2,
\qquad
I=\frac{75^4-65^4}{12}=1.149\times10^6\text{ mm}^4,
\qquad
\kappa=28.7\text{ mm},
\qquad
\frac L\kappa=105 .
$$

The axial stress is $120\,000/1400=85.7$ MPa, and

$$
P_{cr}=\frac{\pi^2\times200\,000\times1.149\times10^6}{3000^2}=252\text{ kN},
$$

a safety factor of 2.10 against buckling (and 2.92 against yield). S6 shows how an initial curvature erodes this.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S4 - Torsion of Thin-Walled Sections]]
- Next: [[SESA2028 S6 - Imperfect Columns, Beam-Columns and Plate Buckling]]
- Concepts: [[Euler Buckling]] · [[Effective Length]] · [[Slenderness Ratio]]
- Year 1 foundation: the Euler load appears in statics as a compression check

![[structures_euler_buckling_end_conditions.png|720]]

## Sources

- Structures slides `SL6 Instability and Euler buckling theory.pdf` and `SL7 buckling of beams with imperfection.pdf` (examples), with transcripts `SESA2028 Lecture 2026-04-22.txt` (ll. 150–424) and `SESA2028 Lecture 2026-04-24.txt` (ll. 1–200)
- Examples recomputed in Python

## Self-study tasks

### Core

- [ ] Derive the Euler load and buckling modes of a pinned column ("try to look at this derivation from your side", 2026-04-22, ll. 385–424; 2026-04-24, ll. 1–120). → [[#2. The pinned column]]
- [ ] The hinged bar with a spring: stable, unstable and neutral equilibrium and the bifurcation load (ll. 270–310). → [[#1. Stability and equilibrium]]
- [ ] The hollow circular and hollow square columns (slides 23 and 37; 2026-04-30, ll. 1–60). → [[#Worked example: two columns]]
- [ ] Structures tutorial 4, Q1 part 1 (Euler load). → [[SESA2028 Structures Tutorial 4 - Buckling Solutions#Q1 - Eccentrically loaded tubular column|Tutorial 4 Q1]]

### Further practice

- [ ] Derive $P_{cr}$ for a fixed–free column from the same equation with $v(0)=0$, $v'(0)=0$ at the base (suggested in the lecture, 2026-04-24, ll. 140–160). → [[#3. Other end conditions and effective length]]

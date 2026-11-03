---
title: "SESA2028 S2 - Beam Deflection and Bending Design"
module: "SESA2028 Aerospace Materials & Structures"
type: topic
stream: "Structures"
order: 2
tags: [sesa2028, structures, deflection, beam, structures-lab]
date: 2026-10-30
status: lectured
coverage: "Statics review video (2026-01-27) and the structures lab videos (2026-03-01); deflection integration as used in SL7–SL8"
parent: ["[[SESA2028 Aerospace Materials & Structures Hub]]"]
prerequisites: ["[[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]"]
next_topics: ["[[SESA2028 S3 - Shear Flow and Shear Centre]]"]
key_concepts: ["[[Moment Curvature Relation]]", "[[Elastic Curve]]", "[[Section Modulus]]"]
tutorial_sheets: ["[[SESA2028 Structures Tutorial 2 - Bending Solutions]]"]
sources: ["02 - Sources/Structures Lectures/SL2 Bending stress and deflection.pdf", "02 - Sources/Lectures/SESA2028 Lecture 2026-01-27 - Review of Statics key concepts_default.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-01 - structures lab-explanation.txt", "02 - Sources/Lectures/SESA2028 Lecture 2026-03-01 - Structures Lab_experimental setup.txt"]
---

# SESA2028 S2 - Beam Deflection and Bending Design

> [!abstract] Summary
> Beam deflection comes from integrating the moment–curvature relation twice, $EI\,v''=-M$ with $y$ downward, and fixing the constants from the supports; for unsymmetrical sections the two planes are coupled as in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending|S1]]. A design must pass two independent checks: the extreme-fibre stress $|M|c/I$ against an allowable stress, and the deflection against a stiffness limit, and for slender beams stiffness often governs. The structures lab uses the cantilever compliance $L^3/3EI$ to measure the principal second moments of an unsymmetrical beam from a Mohr's circle of deflections, and locates its shear centre.

> [!summary]- Exam use: quick path
> - **Use it when:** a beam needs a deflection, a slope, or a section sized for both strength and stiffness.
> - **Assumptions:** Euler–Bernoulli (slender, plane sections, no shear deformation), linear elastic, small deflection, bending about a principal axis unless stated.
> - **Method:** 1. Reactions from a free-body diagram. 2. $M(x)$ by cutting the beam. 3. $EIv''=-M$, integrate twice. 4. Constants from $v$ and $v'$ at supports, plus continuity. 5. Check $\sigma_{max}=M_{max}c/I$ and $v_{max}$ against their limits.
> - **Common mistakes:** mixing the $y$-up and $y$-down sign conventions; sizing for stress and forgetting the deflection limit.
> - **Practise:** [[#Worked example: stress or stiffness?]]

This year the bending theory itself was a review: a recorded "Review of statics key concepts" video asked students to revisit Statics 1 and 2 before the structures lectures (2026-01-27), and deflection integration then appeared within the unsymmetrical-bending lectures and the structures lab. The note collects that material and the lab theory.

How far a diving board dips at its tip depends on how hard it is bent along its whole length, not just at one point: each small piece bends according to the moment it carries, and the tip deflection is the sum of all those small bends. Integrating curvature once gives slope, twice gives deflection, and the supports fix where the integration starts. Stress, by contrast, is local: it depends only on the moment at the worst section. That is why a beam can be strong enough and still too floppy.

## 1. Statics review

The review video recaps what the structures half assumes (2026-01-27, ll. 1–150). Stress is a point quantity, force per unit area on a plane, with three normal and three shear components; strain is also a point quantity, $\varepsilon_{ij}=\tfrac12(\partial u_i/\partial x_j+\partial u_j/\partial x_i)$, which equals the normalised extension only when it is uniform. Poisson's ratio is $\nu=-\varepsilon_{yy}/\varepsilon_{xx}$ under uniaxial load. "Linear" means stress proportional to strain, "elastic" that unloading returns to the origin, "isotropic" the same stiffness in every direction. Equilibrium, $\sum F=0$ and $\sum M=0$, holds for a whole body and for any part cut from it, which is how internal forces are found. A positive shear force at a cut face produces clockwise rotation of the segment; a sagging moment is positive. Axial members have $\sigma=F/A$ and $\delta=FL/EA$, with buckling as an extra check in compression; beams have $\sigma=My/I$; circular shafts $\tau=Tr/J$. Linear elastic stresses from separate loads superpose, Mohr's circle gives principal stresses, and indeterminate problems need compatibility as well as equilibrium. The video ends with a review example to attempt before checking the posted solution.

## 2. Moment, curvature and deflection

Take $y$ (and the deflection $v$) positive downward, as in the lectures, with a sagging moment positive (slides 20–21). Plane sections remain plane and the beam bends into an arc of radius $R$, so a fibre at distance $y$ below the neutral axis has strain $y/R$ and stress $Ey/R$. The moment of that stress about the neutral axis is

$$
M=\int_A\sigma y\,dA=\frac ER\int_Ay^2\,dA=\frac{EI}{R}.
$$

For small slopes the curvature is the second derivative of the deflection. A sagging beam with $v$ downward is concave towards $-y$, so

$$
\frac1R=-\frac{d^2v}{dx^2}
\quad\Longrightarrow\quad
EI\frac{d^2v}{dx^2}=-M(x).
$$

With $y$ upward the sign flips to $EIv''=+M$; Year 1 ([[FEEG1002 A5 - Beam Deflection and Macaulay's Method]]) uses the downward form. Whichever is used, the check is physical: a downward-loaded cantilever must deflect down. For an unsymmetrical section, replace $M/EI$ by the coupled curvatures of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#6. Deflection|S1]].

Load, shear, moment, slope and deflection form one chain:

$$
\frac{dQ}{dx}=-w(x),
\qquad
\frac{dM}{dx}=Q(x),
\qquad
\theta=\frac{dv}{dx},
\qquad
EI\frac{d\theta}{dx}=-M(x),
$$

with $w$ the distributed load per unit length. Point loads make jumps in $Q$, point moments jumps in $M$; slope and deflection stay continuous unless there is a hinge.

| Location | Conditions |
|---|---|
| fixed end | $v=0$, $v'=0$ |
| simple support | $v=0$ (and $M=0$ at an end support) |
| free end, unloaded | $M=0$, $Q=0$ |
| internal point, no hinge | $v$ and $v'$ continuous |
| internal hinge | $v$ continuous, $M=0$ |

## 3. Two standard cases

These are checks, not substitutes for the method.

Cantilever, fixed at $x=0$, tip load $F$ downward at $x=L$ (slide 21). Cutting at $x$ and taking moments of the free part, the moment is hogging:

$$
M(x)=-F(L-x).
$$

Then

$$
EIv''=F(L-x).
$$

Integrate with $v'(0)=0$:

$$
EIv'=F\left(Lx-\frac{x^2}{2}\right).
$$

Integrate with $v(0)=0$:

$$
EIv=F\left(\frac{Lx^2}{2}-\frac{x^3}{6}\right).
$$

At the tip,

$$
v(L)=\frac{FL^3}{3EI},
\qquad
v'(L)=\frac{FL^2}{2EI}.
$$

Simply supported span $L$ under a uniform load $w$: the reactions are $wL/2$, and the sagging moment is

$$
M(x)=\frac{wL}{2}x-\frac{wx^2}{2}.
$$

Integrate $EIv''=-M$ twice:

$$
EIv=-\frac{wLx^3}{12}+\frac{wx^4}{24}+C_1x+C_2 .
$$

$v(0)=0$ gives $C_2=0$; $v(L)=0$ gives $C_1=wL^3/24$. At midspan,

$$
v\!\left(\tfrac L2\right)=\frac{1}{EI}\left(-\frac{wL^4}{96}+\frac{wL^4}{384}+\frac{wL^4}{48}\right)=\frac{5wL^4}{384EI}.
$$

The cantilever under a uniform load, used in the S1 example, gives $wL^4/8EI$, and under a tip moment $M_0$, $M_0L^2/2EI$.

## 4. The two design checks

The stress check uses the largest moment and the extreme fibre distance $c$ on each side:

$$
\sigma_{max}=\frac{|M|_{max}\,c}{I}=\frac{|M|_{max}}{Z},
\qquad
Z=\frac Ic,
$$

where $Z$ is the section modulus ([[Section Modulus]]). For an unsymmetrical section use the general stress of S1 at every corner. The stiffness check compares the largest deflection with a limit, such as a fraction of the span or a clearance. Because $I$ weights area by the square of its distance from the neutral axis, depth is the efficient way to add both strength ($Z\propto h^2$) and stiffness ($I\propto h^3$). The two maxima need not occur at the same place: for a cantilever, the stress peaks at the root and the deflection at the tip.

## 5. The structures lab

The lab tests cantilevers of rectangular, channel and angle section on the STS-7 rig: a bending test that measures the principal second moments, and a torsion test that locates the shear centre (2026-03-01 lab explanation and set-up videos).

For bending, the beam is clamped in a chuck that rotates in steps of $22.5°$, a 300 g load (2.943 N, a 20 g hanger and fourteen 20 g weights) hangs at the tip, and two gauges at 45° give the vertical and horizontal deflections $\delta_u$ and $\delta_v$, which the VDAS software computes; the gauges are zeroed before each load. Dividing by the load gives compliances, $u=\delta_u/\Delta W$ and $v=\delta_v/\Delta W$. From the tilted-beam analysis of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#1. The tilted rectangle|S1]], with principal second moments $I_{xp}$ and $I_{yp}$ and the chuck angle $\theta$ measured from a principal axis,

$$
u=\frac{L^3}{3E}\left(\frac{\cos^2\theta}{I_{xp}}+\frac{\sin^2\theta}{I_{yp}}\right)=OC+R\cos2\theta,
\qquad
v=R\sin2\theta,
$$

with centre and radius

$$
OC=\frac{L^3}{6E}\left(\frac1{I_{xp}}+\frac1{I_{yp}}\right),
\qquad
R=\frac{L^3}{6E}\left|\frac1{I_{xp}}-\frac1{I_{yp}}\right| .
$$

Plotting $(u,v)$ for five or six chuck angles gives a circle. Where it crosses the $u$ axis, $v=0$: the load lies along a principal axis, and the compliance is pure bending, $L^3/3EI$. So

$$
OC\pm R=\frac{L^3}{3EI_{p}}
\quad\Longrightarrow\quad
I_{xp}=\frac{L^3}{3E(OC-R)},
\qquad
I_{yp}=\frac{L^3}{3E(OC+R)} .
$$

The angle from the starting position to that crossing is $2\theta$ on the circle and $\theta$ on the beam, which locates the principal axes. In the lab's notation $u$ is vertical and $v$ horizontal, the reverse of some lecture slides.

For the shear centre, an arm fixed to the tip lets the 300 g load hang at offsets from $-25$ to $+25$ mm in 5 mm steps; two vertical gauges read $\delta_1$ and $\delta_2$ on either side. Plotting both against the load position gives two straight lines whose intersection, where $\delta_1=\delta_2$ and the section does not twist, is the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]). For a channel it lies outside the section.

## Worked example: stress or stiffness?

Not from the lectures: an aluminium cantilever, $L=1$ m, $E=70$ GPa, rectangular section $b=25$ mm wide, carries $F=1$ kN at the tip. The allowable stress is 200 MPa and the tip deflection must not exceed $L/250=4$ mm. Find the depth $h$.

With $I=bh^3/12$ and $c=h/2$, the stress check is

$$
\sigma_{max}=\frac{FL\,(h/2)}{bh^3/12}=\frac{6FL}{bh^2}\le200
\quad\Longrightarrow\quad
h^2\ge\frac{6\times1000\times1000}{25\times200}=1200
\quad\Longrightarrow\quad
h\ge34.6\text{ mm}.
$$

The stiffness check is

$$
v_{tip}=\frac{FL^3}{3EI}=\frac{4FL^3}{Ebh^3}\le4
\quad\Longrightarrow\quad
h^3\ge\frac{4\times1000\times10^9}{70\,000\times25\times4}=5.71\times10^5
\quad\Longrightarrow\quad
h\ge82.9\text{ mm}.
$$

Stiffness governs by a wide margin: at $h=83$ mm the stress is only 35 MPa. Light, slender aerospace structures are often designed by stiffness, buckling or fatigue rather than by static strength.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]]
- Previous: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]
- Next: [[SESA2028 S3 - Shear Flow and Shear Centre]]
- Concepts: [[Moment Curvature Relation]] · [[Elastic Curve]] · [[Section Modulus]] · [[Shear Centre]]
- Year 1 foundation: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Energy methods for deflections: [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- Structures slides `SL2 Bending stress and deflection.pdf` (slides 20–23), the statics review video `SESA2028 Lecture 2026-01-27 - Review of Statics key concepts_default.txt`, and the lab videos `SESA2028 Lecture 2026-03-01 - structures lab-explanation.txt` and `... - Structures Lab_experimental setup.txt`
- Worked example computed by hand and checked in Python

## Self-study tasks

### Core

- [ ] Attempt the statics review example before looking at its solution (review video, ll. 141–150). → [[#1. Statics review]]
- [ ] Derive the cantilever and simply supported deflections by integration. → [[#3. Two standard cases]]
- [ ] Structures lab: plot the Mohr's circle of compliances, find $I_{xp}$, $I_{yp}$ and the principal-axis angle, and locate the shear centre of the channel (lab videos, 2026-03-01). → [[#5. The structures lab]]

### Further practice

- [ ] Repeat the worked example for a steel beam and say which check governs (suggested, not lecturer-set). → [[#Worked example: stress or stiffness?]]

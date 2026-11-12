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
> Beam deflection comes from integrating the moment–curvature relation twice, $EI\,v''=-M$ with $y$ downward, and fixing the constants from the supports; for unsymmetrical sections the two planes are coupled as in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending|S1]]. A design must pass two independent checks, the extreme-fibre stress $|M|c/I$ against an allowable stress and the deflection against a stiffness limit, and for slender beams stiffness often governs. In the structures lab the cantilever compliance $L^3/3EI$ gives the principal second moments of an unsymmetrical beam from a circle of compliances, and the shear centre of a channel is located.

> [!summary]- Exam use: quick path
> - **Use it when:** a beam needs a deflection, a slope, or a section sized for both strength and stiffness; or you are processing the structures-lab bending data.
> - **Assumptions:** Euler–Bernoulli (slender, plane sections remain plane, no shear deformation), linear elastic, small deflection and slope, bending about a principal axis unless stated.
> - **Method:** 1. Reactions from a free-body diagram. 2. $M(x)$ by cutting the beam, segment by segment. 3. $EIv''=-M$, integrate twice. 4. Constants from $v$ and $v'$ at supports, plus continuity. 5. Check $\sigma_{max}=M_{max}c/I$ and $v_{max}$ against their limits.
> - **Common mistakes:** mixing the $y$-up and $y$-down sign conventions; sizing for stress and forgetting the deflection limit.
> - **Practise:** [[#Worked example: stress or stiffness?]] · [[SESA2028 Structures Tutorial 2 - Bending Solutions#Q1.3 - Coupled tip deflection|Tutorial 2 Q1.3]]

How far a diving board dips at its tip depends on how hard it is bent along its whole length, not just at one point. Each short piece bends according to the moment it carries, and the tip deflection is the accumulated effect of all those small bends. Integrating the curvature once gives the slope, and again gives the deflection; the supports fix where each integration starts. Stress, by contrast, is local: it depends only on the moment at the worst section. That is why a beam can be strong enough and still too flexible.

## 1. Statics review

Stress is a point quantity: force per unit area on a particular plane, with three normal components ($\sigma_{xx}$, $\sigma_{yy}$, $\sigma_{zz}$) and three independent shear components. Strain is also a point quantity, defined for small strains as

$$
\varepsilon_{ij}=\frac12\left(\frac{\partial u_i}{\partial x_j}+\frac{\partial u_j}{\partial x_i}\right),
$$

so $\varepsilon_{xx}=\partial u_x/\partial x$ and $\varepsilon_{xy}=\tfrac12(\partial u_x/\partial y+\partial u_y/\partial x)$. The familiar $\Delta L/L_0$ is strictly an extension, equal to the strain only when the strain is uniform. Poisson's ratio is $\nu=-\varepsilon_{yy}/\varepsilon_{xx}$ for a bar loaded along $x$ and free to contract sideways.

Hooke's law links stress and strain: $\sigma=E\varepsilon$ in one dimension, and in three dimensions

$$
\varepsilon_{xx}=\frac1E\left[\sigma_{xx}-\nu\left(\sigma_{yy}+\sigma_{zz}\right)\right],\qquad\varepsilon_{xy}=\frac{1+\nu}{E}\sigma_{xy}.
$$

Linear means stress proportional to strain, elastic that unloading returns to the origin, and isotropic that $E$ and $\nu$ are the same in every direction.

Equilibrium, $\sum\mathbf F=\mathbf 0$ and $\sum\mathbf M=\mathbf 0$, holds for a whole body and for any part cut from it, which is how internal forces are found. A positive shear force $Q$ at a cut face rotates the segment clockwise, and a positive bending moment produces sagging. The basic stress and deformation results are $\sigma=F/A$ and $\delta=FL/EA$ for axial members (with buckling, $P_{crit}=\pi^2EI/L_e^2$, as an extra check in compression), $\sigma=My/I$ and $EIv''=-M$ for beams, and $\tau=Tr/J$, $\phi=TL/GJ$ for circular shafts, with $I=bh^3/12$ for a rectangle and $I=\pi R^4/4$, $J=\pi R^4/2$ for a solid circle. Linear elastic stresses from separate loads superpose; Mohr's circle gives the principal stresses and the maximum shear stress (its radius). Geometric constraints link deformations: two bars between the same rigid plates share one displacement, and two bars in series add their extensions. A statically indeterminate problem needs all three of equilibrium, geometric compatibility and Hooke's law; conservation of energy ([[SESA2028 S7 - Strain Energy and Conservation of Energy|S7]]) is a fourth tool.

## 2. Moment, curvature and deflection

Here $y$ and the deflection $v$ are positive downward, and a sagging moment is positive. Plane sections remain plane and the beam bends into an arc of radius $R$, so a fibre at distance $y$ below the neutral axis has strain $y/R$ and stress $Ey/R$ ([[SESA2028 S1 - Section Properties and Unsymmetrical Bending#3. The neutral axis passes through the centroid|S1]]). The moment of that stress about the neutral axis is

$$
M=\int_A\sigma y\,dA=\frac ER\int_Ay^2\,dA=\frac{EI}{R}.
$$

The exact curvature of the deflected shape is

$$
\frac1R=\frac{\pm v''}{\left(1+v'^2\right)^{3/2}},
$$

and for small slopes, $v'^2\ll1$, the denominator is 1. A sagging beam with $v$ downward hangs lowest in the middle, so $v$ has a maximum there and $v''<0$ while the moment is positive. The sign must therefore be negative:

$$
\frac1R=-\frac{d^2v}{dx^2}\quad\Longrightarrow\quad EI\frac{d^2v}{dx^2}=-M(x).
$$

With $y$ upward the sign flips, $EIv''=+M$. Whichever convention is used, the physical check is the same: a downward-loaded cantilever must deflect down. For an unsymmetrical section, replace $M/EI$ by the coupled curvatures of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#6. Deflection|S1]].

Load, shear, moment, slope and deflection form one chain:

$$
\frac{dQ}{dx}=-w(x),\qquad\frac{dM}{dx}=Q(x),\qquad\theta=\frac{dv}{dx},\qquad EI\frac{d\theta}{dx}=-M(x),
$$

with $w$ the distributed load per unit length (positive downward). Point loads make jumps in $Q$ and point moments jumps in $M$; the slope and deflection stay continuous unless there is a hinge.

| Location | Conditions |
|---|---|
| fixed end | $v=0$, $v'=0$ |
| simple support | $v=0$ (and $M=0$ at an end support) |
| free end, unloaded | $M=0$, $Q=0$ |
| internal point, no hinge | $v$ and $v'$ continuous |
| internal hinge | $v$ continuous, $M=0$ |

## 3. Standard cases by integration

These are checks on the method, not substitutes for it.

### Cantilever with a tip load

A cantilever fixed at $x=0$ carries a downward load $F$ at $x=L$. Cutting at $x$ and taking moments of the free part beyond the cut, the load acts at lever arm $L-x$ and bends the beam hogging, so

$$
M(x)=-F(L-x).
$$

Then $EIv''=-M$ gives

$$
EIv''=F(L-x).
$$

Integrate once:

$$
EIv'=F\left(Lx-\frac{x^2}{2}\right)+C_1 .
$$

The root does not rotate, $v'(0)=0$, so $C_1=0$. Integrate again:

$$
EIv=F\left(\frac{Lx^2}{2}-\frac{x^3}{6}\right)+C_2 .
$$

The root does not move, $v(0)=0$, so $C_2=0$. At the tip, $x=L$:

$$
v(L)=\frac{F}{EI}\left(\frac{L^3}{2}-\frac{L^3}{6}\right)=\frac{FL^3}{3EI},\qquad v'(L)=\frac{F}{EI}\left(L^2-\frac{L^2}{2}\right)=\frac{FL^2}{2EI}.
$$

### Simply supported span under a uniform load

A span $L$ carries a uniform load $w$. By symmetry the reactions are $wL/2$, and the sagging moment at $x$ is

$$
M(x)=\frac{wL}{2}x-\frac{wx^2}{2}.
$$

So

$$
EIv''=-\frac{wL}{2}x+\frac{wx^2}{2}.
$$

Integrate once:

$$
EIv'=-\frac{wL}{4}x^2+\frac{w}{6}x^3+C_1 .
$$

Integrate again:

$$
EIv=-\frac{wL}{12}x^3+\frac{w}{24}x^4+C_1x+C_2 .
$$

At $x=0$, $v=0$, so $C_2=0$. At $x=L$, $v=0$:

$$
0=-\frac{wL^4}{12}+\frac{wL^4}{24}+C_1L\quad\Longrightarrow\quad C_1=\frac{wL^3}{24}.
$$

At midspan:

$$
EIv\!\left(\tfrac L2\right)=-\frac{wL}{12}\cdot\frac{L^3}{8}+\frac w{24}\cdot\frac{L^4}{16}+\frac{wL^3}{24}\cdot\frac L2=wL^4\left(-\frac{1}{96}+\frac{1}{384}+\frac{1}{48}\right).
$$

Over the denominator 384 the bracket is $(-4+1+8)/384=5/384$, so

$$
v\!\left(\tfrac L2\right)=\frac{5wL^4}{384EI}.
$$

The slope there is $EIv'(L/2)=-wL^3/16+wL^3/48+wL^3/24=0$, as symmetry requires.

> [!check] Same answer by energy
> Castigliano's theorem with a dummy load at midspan gives the same $5wL^4/384EI$ ([[SESA2028 S8 - Virtual Work and Castigliano Theorems#Midspan deflection under a uniform load|S8]]). The integration route needs boundary conditions; the energy route needs only the moment distribution.

### Other cases used in the module

The cantilever under a uniform load $w$ has $M=-w(L-x)^2/2$, and the same double integration (done in [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#Tip deflection|S1]]) gives $v_{tip}=wL^4/8EI$. Under a tip moment $M_0$ the moment is constant, $EIv''=-M_0$ with a hogging (negative) $M_0$ giving $v=|M_0|x^2/2EI$ and $v_{tip}=M_0L^2/2EI$. The simply supported beam with a central load gives $FL^3/48EI$ ([[SESA2028 S7 - Strain Energy and Conservation of Energy#Central load on a simply supported beam|S7]]).

## 4. The two design checks

The stress check uses the largest moment and the extreme fibre distance $c$ on each side of the neutral axis:

$$
\sigma_{max}=\frac{|M|_{max}\,c}{I}=\frac{|M|_{max}}{Z},\qquad Z=\frac Ic,
$$

where $Z$ is the section modulus ([[Section Modulus]]). For an unsymmetrical section use the general stress of S1 at every corner. The stiffness check compares the largest deflection with a limit, such as a fraction of the span or a clearance.

Because $I$ weights area by the square of its distance from the neutral axis, depth is the efficient way to add both strength and stiffness. For a rectangle $b\times h$, $Z=bh^2/6$ and $I=bh^3/12$: doubling the depth makes the beam four times stronger and eight times stiffer, whereas doubling the width only doubles both. The two maxima need not occur at the same place: for a cantilever the stress peaks at the root and the deflection at the tip.

### Worked example: stress or stiffness?

An aluminium cantilever ($E=70$ GPa), $L=1$ m long with a rectangular section $b=25$ mm wide, carries $F=1$ kN at the tip. The allowable stress is 200 MPa and the tip deflection must not exceed $L/250=4$ mm. Find the depth $h$. (Suggested exercise, not from the lectures.)

The largest moment is at the root, $FL=10^6$ N mm. With $I=bh^3/12$ and $c=h/2$, the stress check is

$$
\sigma_{max}=\frac{FL\,(h/2)}{bh^3/12}=\frac{6FL}{bh^2}\le200 .
$$

Rearrange for $h$:

$$
h^2\ge\frac{6\times1000\times1000}{25\times200}=1200\quad\Longrightarrow\quad h\ge34.6\text{ mm}.
$$

The stiffness check is

$$
v_{tip}=\frac{FL^3}{3EI}=\frac{FL^3}{3E\,bh^3/12}=\frac{4FL^3}{Ebh^3}\le4 .
$$

Rearrange:

$$
h^3\ge\frac{4\times1000\times10^9}{70\,000\times25\times4}=5.71\times10^5\quad\Longrightarrow\quad h\ge82.9\text{ mm}.
$$

Stiffness governs by a wide margin.

> [!check] What the stiff design does to the stress
> At $h=83$ mm the root stress is $6\times10^6/(25\times83^2)=34.8$ MPa, a sixth of the allowable, and the tip deflection is exactly 4 mm. Light, slender aerospace structures are often sized by stiffness, buckling or fatigue rather than by static strength.

## 5. The structures lab

The lab tests cantilevers of rectangular, channel and angle section on the STS-7 rig: a bending test that measures the principal second moments, and a torsion test that locates the shear centre.

### Bending test: a circle of compliances

The beam is clamped in a chuck that rotates in steps of $22.5°$. A 300 g load hangs at the tip: a 20 g hanger plus fourteen 20 g weights, $0.300\times9.81=2.943$ N. Two dial gauges at $45°$ to the vertical, zeroed before each load, read $\delta_1$ and $\delta_2$. A gauge along the unit vector $(\cos45°,\sin45°)$ reads the projection of the tip displacement onto it, so

$$
\delta_1=\frac{\delta_u+\delta_v}{\sqrt2},\qquad\delta_2=\frac{\delta_u-\delta_v}{\sqrt2},
$$

and the vertical and horizontal deflections follow by adding and subtracting:

$$
\delta_u=\frac{\delta_1+\delta_2}{\sqrt2},\qquad\delta_v=\frac{\delta_1-\delta_2}{\sqrt2}.
$$

The VDAS software does this conversion.

> [!check] The demonstration reading
> In the set-up video, at $0°$ the gauges read $\delta_1=-0.93$ mm and $\delta_2=-0.82$ mm. Then $\delta_u=(-0.93-0.82)/\sqrt2=-1.24$ mm and $|\delta_v|=0.11/\sqrt2=0.08$ mm, matching the software's $-1.2$ mm and 0.08 mm. The small horizontal value at $0°$ is measurement error for a section loaded along a principal axis.

Dividing by the load gives the compliances $u=\delta_u/W$ and $v=\delta_v/W$. From the tilted-beam analysis of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#1. The tilted rectangle|S1]], with principal second moments $I_{xp}$, $I_{yp}$ and the angle $\theta$ between the load and a principal axis,

$$
u=\frac{L^3}{3E}\left(\frac{\cos^2\theta}{I_{xp}}+\frac{\sin^2\theta}{I_{yp}}\right)=OC+R\cos2\theta,\qquad v=R\sin2\theta,
$$

with centre and radius

$$
OC=\frac{L^3}{6E}\left(\frac1{I_{xp}}+\frac1{I_{yp}}\right),\qquad R=\frac{L^3}{6E}\left|\frac1{I_{xp}}-\frac1{I_{yp}}\right| .
$$

Plotting $(u,v)$ for the chuck angles gives a circle. Where it crosses the $u$ axis, $v=0$: the load lies along a principal axis and the compliance is pure bending, $L^3/3EI$. So the two crossings give

$$
OC-R=\frac{L^3}{3EI_{max}},\qquad OC+R=\frac{L^3}{3EI_{min}},
$$

that is,

$$
I_{max}=\frac{L^3}{3E(OC-R)},\qquad I_{min}=\frac{L^3}{3E(OC+R)} .
$$

The angle on the circle from the starting point to a crossing is $2\theta$; on the beam it is $\theta$, which locates the principal axes relative to the chuck. In the lab's notation $u$ is vertical and $v$ horizontal, the reverse of some lecture slides.

![[structures_s2_lab_compliance_circle.png|760]]

The figure shows what this procedure gives for the angle section of [[SESA2028 S1 - Section Properties and Unsymmetrical Bending#Worked example: an angle-section cantilever|S1]] as a 1 m aluminium cantilever. With $I_{max}=26.8\times10^6$ and $I_{min}=4.03\times10^6$ mm⁴, $OC-R=1.78\times10^{-4}$ mm/N and $OC+R=11.8\times10^{-4}$ mm/N. The starting position ($0°$, load along the section's own $y$ axis) is $2\times19.6°=39.3°$ round the circle from the stiff crossing, and its vertical compliance, $2.9\times10^{-4}$ mm/N, is the coupled value $L^3I_y/3E(I_yI_z-I_{yz}^2)$ of S1.

### Torsion test: locating the shear centre

An arm fixed to the tip lets the 300 g load hang at offsets from $-25$ to $+25$ mm in 5 mm steps, entered in the software with the $\pm$ buttons. Two vertical gauges read $\delta_1$ and $\delta_2$ on either side of the section. If the load passes to one side of the shear centre, the section twists as well as bends and the two gauges differ. Plotting both readings against the load position gives two straight lines; at their intersection $\delta_1=\delta_2$, the section translates without twisting, and that offset is the shear centre ([[SESA2028 S3 - Shear Flow and Shear Centre|S3]]). For a channel it lies outside the section, on the side away from the flanges.

## Links

- Parent: [[SESA2028 Aerospace Materials & Structures Hub]] · Previous: [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]] · Next: [[SESA2028 S3 - Shear Flow and Shear Centre]]
- Concepts: [[Moment Curvature Relation]] · [[Elastic Curve]] · [[Section Modulus]] · [[Shear Centre]]
- Problems: [[SESA2028 Structures Tutorial 2 - Bending Solutions]] · Formulae: [[SESA2028 Formula Sheet]]
- Year 1 foundation: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]] · [[FEEG1002 A5 - Beam Deflection and Macaulay's Method]] · [[FEEG1002 A6 - Statically Indeterminate Beams]]
- Energy methods for deflections: [[SESA2028 S7 - Strain Energy and Conservation of Energy]] · [[SESA2028 S8 - Virtual Work and Castigliano Theorems]]

## Sources

- Slides: `SL2 Bending stress and deflection.pdf` (moment–curvature and deflection, slides 20–23) and `SL1 Introduction, motivation & Review.pdf` (statics review, slides 25–34).
- Recordings: the statics review video `SESA2028 Lecture 2026-01-27 - Review of Statics key concepts_default.txt`, and the lab videos `SESA2028 Lecture 2026-03-01 - structures lab-explanation.txt` (theory) and `SESA2028 Lecture 2026-03-01 - Structures Lab_experimental setup.txt` (procedure and the demonstration reading).
- Integrations checked with SymPy; the worked example and the compliance circle computed in Python. Figure: `generate_structures_s2_figures.py`.

## Self-study tasks

### Core

- [ ] Attempt the statics review example before looking at its posted solution (review video, ll. 141–150; it is the offset crank of SL1). → [[SESA2028 S7 - Strain Energy and Conservation of Energy#Offset crank: combined bending and torsion|S7 worked solution]]
- [ ] Derive the cantilever and simply supported deflections by integration. → [[#3. Standard cases by integration]]
- [ ] Structures lab: plot the circle of compliances, find $I_{xp}$, $I_{yp}$ and the principal-axis angle, and locate the shear centre of the channel (lab videos, 2026-03-01). → [[#5. The structures lab]]

### Further practice

- [ ] Repeat the stress-or-stiffness example for a steel beam and say which check governs (suggested, not lecturer-set). → [[#Worked example: stress or stiffness?]]
- [ ] Convert the demonstration gauge readings to $\delta_u$ and $\delta_v$ by hand (suggested, not lecturer-set). → [[#Bending test: a circle of compliances]]

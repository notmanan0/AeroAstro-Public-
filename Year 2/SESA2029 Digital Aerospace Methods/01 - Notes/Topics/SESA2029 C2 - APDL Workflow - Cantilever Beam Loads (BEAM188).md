---
title: "SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 23
tags:
  - sesa2029
  - apdl
  - beam-element
  - workflow
aliases: ["APDL cantilever beam", "BEAM188 workflow", "Elliptical load APDL"]
date: 2026-10-30
status: lectured
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]", "[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
next_topics: ["[[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]"]
key_concepts: ["[[Euler-Bernoulli Beam Element]]", "[[Mesh Convergence and Grid Independence]]", "[[Elliptic Lift Distribution]]"]
tutorial_sheets: []
sources: ["Own APDL scripts (generalised)", "ANSYS Element Reference: BEAM188, SECTYPE/SECDATA, SFBEAM", "02 - Sources/Lectures/SESA2029 Lecture Computer lab1_Spring Analysis Video.txt", "02 - Sources/Lectures/SESA2029 Lecture Computer lab1_Cantilever_Beam.txt"]
---

# SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)

> [!abstract] Summary
> Lab 1 models a wing spar as a cantilever of BEAM188 elements with an H (I) section, clamped at the root, first under a tip point load, then, for the coursework, under a uniform and an elliptical line load of the same total. Each run is checked against beam theory: tip deflections $WL^3/3EI$, $WL^3/8EI$ and $0.0967\,WL^3/EI$. The elliptical load, closest to a real lift distribution, can be applied as scaled nodal forces or, better, as element-wise linear `SFBEAM` pressures whose discrete total is exact. Units are mm, N and MPa, and the parameter values are illustrative.

> [!summary]- Exam use: quick path
> - **Use it when:** setting up the lab 1 beam, its load cases or its convergence study.
> - **Assumptions:** linear elastic steel, clamped root, BEAM188 (Timoshenko) elements.
> - **Method:** 1. `ET,1,188`, `SECTYPE,BEAM,I`, `SECDATA`. 2. Two key points, a line, `LESIZE` divisions, `LMESH`. 3. Clamp all DOF at the root node. 4. Tip `F`, or `SFBEAM` line loads. 5. Read the tip `UY` and max `S,EQV`; compare with beam theory.
> - **Common mistakes:** wrong `SFBEAM` face key or sign (check `PLDISP` and the reactions); judging stress without `/ESHAPE,1`.
> - **Practise:** [[#1. Model and hand checks]]


## 1. Model and hand checks
- Length $L = 250$ mm, steel ($E = 210$ GPa $= 2.1\times10^5$ MPa, $\nu = 0.3$), total load $W = 1000$ N. The modulus is a typical value for steel; check the figure given on your lab sheet.
- Section `SECTYPE,1,BEAM,I` with `SECDATA,W1,W2,W3,t1,t2,t3`:
  - bottom-flange width, top-flange width, overall depth;
  - bottom-flange, top-flange and web thicknesses.

| Case | Section | $I$ [mm⁴] | Beam theory | Tip deflection |
|---|---|---|---|---|
| tip load $W$ | 10,10,10,4.9,4.9,4.9 | 833.3 | $\delta = \dfrac{WL^3}{3EI}$ | 29.8 mm |
| UDL, total $W$ | 10,10,10,3,3,3 | 796 | $\delta = \dfrac{WL^3}{8EI}$ | 11.7 mm |
| elliptical, total $W$ | 10,10,10,3,3,3 | 796 | $\delta = 0.0967\dfrac{WL^3}{EI}$ | 9.04 mm |

For the I-section, $I = \dfrac{W_1H^3-(W_1-t_w)(H-2t_f)^3}{12}$: the full rectangle minus the two empty strips beside the web. With $W_1=H=10$ mm and $t=4.9$ mm,

$$
I=\frac{10\times10^3-5.1\times0.2^3}{12}=\frac{10\,000-0.04}{12}=833.3\ \mathrm{mm^4},
$$

and with $t=3$ mm, $I=(10\,000-7\times4^3)/12=796.0\ \mathrm{mm^4}$.

### Where the three tip-deflection formulas come from

All three follow from one result. A point load $P$ at distance $a$ from the root of a cantilever deflects the tip by

$$
\delta_{tip}=\frac{Pa^2(3L-a)}{6EI},
$$

which gives $PL^3/3EI$ for $a=L$. A distributed load $q(a)$ is a set of point loads $q(a)\,\mathrm da$, so by superposition

$$
\delta_{tip}=\frac{1}{6EI}\int_0^Lq(a)\,a^2(3L-a)\,\mathrm da.
$$

For a uniform load $q=W/L$:

$$
\delta_{tip}=\frac{W}{6EIL}\int_0^L\left(3La^2-a^3\right)\mathrm da=\frac{W}{6EIL}\left(L^4-\frac{L^4}{4}\right)=\frac{WL^3}{8EI}.
$$

For the elliptical load $q(a)=q_0\sqrt{1-(a/L)^2}$, the total is a quarter-ellipse area, $W=\pi q_0L/4$, so $q_0=4W/\pi L$. With $\xi=a/L$,

$$
\delta_{tip}=\frac{q_0L^4}{6EI}\int_0^1\sqrt{1-\xi^2}\,\xi^2(3-\xi)\,\mathrm d\xi=\frac{q_0L^4}{6EI}\left(3\cdot\frac{\pi}{16}-\frac{2}{15}\right)=\frac{q_0L^4}{6EI}\times0.45572,
$$

using $\int_0^1\xi^2\sqrt{1-\xi^2}\,\mathrm d\xi=\pi/16$ and $\int_0^1\xi^3\sqrt{1-\xi^2}\,\mathrm d\xi=2/15$. Substituting $q_0$,

$$
\delta_{tip}=\frac{4}{\pi}\times\frac{0.45572}{6}\frac{WL^3}{EI}=0.0967\,\frac{WL^3}{EI}.
$$

For the same total load the three cases deflect in the ratio $\tfrac13:0.0967:\tfrac18=0.333:0.097:0.125$; the elliptical load, concentrated towards the root, deflects the tip least. The table values follow: $\delta=1000\times250^3/(3\times2.1\times10^5\times833.3)=29.8$ mm, $1000\times250^3/(8\times2.1\times10^5\times796)=11.7$ mm and $0.0967\times1000\times250^3/(2.1\times10^5\times796)=9.04$ mm.

> [!check] Shear deflection is negligible here
> BEAM188 adds shear deformation, roughly $WL/(GA_w)$ with $G=E/2(1+\nu)=80\,800$ MPa and a web area of about $4.9\times10=49$ mm²: $1000\times250/(80\,800\times49)=0.063$ mm, 0.2 % of the 29.8 mm bending deflection. A slender spar is an Euler–Bernoulli beam to within the accuracy of the lab, so the FE tip deflection should match the table closely once the mesh has converged.

BEAM188 is a Timoshenko beam (it includes shear deformation), so it is slightly more flexible than Euler–Bernoulli for stubby sections. It converges with `LESIZE` divisions: sweep 20 → 200 → 2000.

## 2. Workflow 1: tip point load
```apdl
FINISH
/CLEAR,ALL
/PREP7
/TITLE, Cantilever beam - tip point load
beam_len = 250          ! mm
num_div  = 200          ! element divisions (convergence: 20 / 200 / 2000)
tip_fy   = -1000        ! N (negative = downward)
ex_mat   = 2.1e5        ! MPa
pr_mat   = 0.30
sec1 = 10 $ sec2 = 10 $ sec3 = 10          ! flange widths, overall depth
sec4 = 4.9 $ sec5 = 4.9 $ sec6 = 4.9       ! flange and web thicknesses
ET,1,188                                    ! BEAM188
MP,EX,1,ex_mat
MP,PRXY,1,pr_mat
SECTYPE,1,BEAM,I,H_SECT
SECDATA,sec1,sec2,sec3,sec4,sec5,sec6
TYPE,1 $ MAT,1 $ SECNUM,1
K,1,0,0,0
K,2,beam_len,0,0
L,1,2
LESIZE,ALL,,,num_div
LMESH,ALL
NSEL,S,LOC,X,beam_len                       ! robust tip-node lookup
*GET,n_tip,NODE,0,NUM,MIN
ALLSEL,ALL
FINISH
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,ALL,0                                 ! clamp: all 6 DOF at the root
ALLSEL,ALL
F,n_tip,FY,tip_fy
SOLVE
FINISH
/POST1
SET,LAST
/ESHAPE,1                                   ! draw the real cross-section
PLDISP,1
PLNSOL,S,EQV
*GET,uy_tip,NODE,n_tip,U,Y
*VWRITE,uy_tip
('TIP DEFLECTION UY (mm) = ',E16.8)
FINISH
```

(In APDL a dollar sign separates several commands on one line.)

## 3. Workflow 2: uniform line load
Same model, rebuilt from `/CLEAR` so that no tip force remains, with the thinner section (`sec4..6 = 3`, `num_div = 20`). Replace the load step:

```apdl
w_total = 1000
q_udl   = -w_total/beam_len                 ! N/mm
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,ALL,0
ALLSEL,ALL
ESEL,ALL
SFBEAM,ALL,1,PRES,q_udl                     ! uniform pressure on load face 1
ALLSEL,ALL
SOLVE
FINISH
/POST1
SET,LAST
*GET,uy_tip,NODE,n_tip,U,Y
*VWRITE,uy_tip,q_udl
('TIP DEFLECTION UY (mm) = ',E16.8,/,'LINE LOAD q (N/mm) = ',E16.8)
```

> [!warning] Load key and sign
> `SFBEAM`'s load key (1 or 2) selects the face relative to the element's local axes. Which one is "down" depends on the beam orientation. Always check that `PLDISP` deflects the way you expect and that the reactions (`PRRSOL`) sum to the applied total.

## 4. Workflow 3a: elliptical load as nodal forces (quick)
Each node gets a force ∝ $\sqrt{1-(x/L)^2}$, scaled so the forces sum to $W$:

```apdl
! ... PREP7 as Workflow 1 (thin section), num_div = 100, then:
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,ALL,0
ALLSEL,ALL
*GET,n_max,NODE,0,NUM,MAX
*DIM,coeff,ARRAY,n_max
sum_c = 0
*DO,i,1,n_max
  *GET,x_loc,NODE,i,LOC,X
  term = 1-(x_loc/beam_len)**2
  *IF,term,LT,0,THEN
    term = 0
  *ENDIF
  coeff(i) = SQRT(term)
  sum_c = sum_c+coeff(i)
*ENDDO
w0 = 1000/sum_c                             ! scale: sum of nodal forces = 1000 N
*DO,i,1,n_max
  F,i,FY,-w0*coeff(i)
*ENDDO
SOLVE
```

This is simple, but it lumps the load at nodes. The end nodes should really carry half-weights (trapezoid rule), so it converges only as the mesh refines.

## 5. Workflow 3b: elliptical load as SFBEAM pressures (recommended)
A linear pressure varies over each element, and $q_0$ is chosen so the trapezoidal integral over the actual mesh equals $W$ exactly:

```apdl
beam_len = 250 $ num_div = 100 $ w_total = 1000
! ... PREP7 as Workflow 1 (thin section) ...
dx = beam_len/num_div
sumraw = 0
*DO,eid,1,num_div                           ! integrate the unit-amplitude shape
  xi = (eid-1)*dx $ xj = eid*dx
  ti = 1-(xi/beam_len)**2 $ tj = 1-(xj/beam_len)**2
  *IF,ti,LT,0,THEN
    ti = 0
  *ENDIF
  *IF,tj,LT,0,THEN
    tj = 0
  *ENDIF
  sumraw = sumraw+0.5*(SQRT(ti)+SQRT(tj))*dx
*ENDDO
q0 = w_total/sumraw                          ! peak line load, mesh-exact total
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,ALL,0
ALLSEL,ALL
*DO,eid,1,num_div                            ! element eid spans [xi, xj] (LMESH numbering from the root)
  xi = (eid-1)*dx $ xj = eid*dx
  ti = 1-(xi/beam_len)**2 $ tj = 1-(xj/beam_len)**2
  *IF,ti,LT,0,THEN
    ti = 0
  *ENDIF
  *IF,tj,LT,0,THEN
    tj = 0
  *ENDIF
  SFBEAM,eid,2,PRES,-q0*SQRT(ti),-q0*SQRT(tj)   ! linear variation I->J
*ENDDO
SOLVE
FINISH
/POST1
SET,LAST
*GET,uy_tip,NODE,n_tip,U,Y
*VWRITE,uy_tip,q0
('TIP DEFLECTION UY (mm) = ',E16.8,/,'PEAK LINE LOAD q0 (N/mm) = ',E16.8)
```

Check: the continuous ellipse has $q_0 = 4W/(\pi L) = 5.093$ N/mm. The mesh-exact $q_0$ approaches this as `num_div` increases, and the tip deflection approaches $0.0967\,WL^3/EI$.

> [!tip] Why this matters aerodynamically
> An elliptical spanwise lift distribution minimises induced drag ([[Elliptic Lift Distribution]]). Compared with a UDL of the same total, the elliptical load puts less force near the tip. That gives a smaller root bending moment ($4WL/3\pi\approx0.424WL$ vs $0.5WL$) and a smaller tip deflection (9.0 vs 11.7 mm here).

## 6. Mesh convergence
Wrap the model in a `*DO` over `num_div` (e.g. 20, 200, 1000, 2000) and write the tip deflection and max `S,EQV` to a file ([[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]).
- Displacement converges quickly, but not in one element: BEAM188 uses linear (Timoshenko) interpolation by default, unlike the cubic Euler–Bernoulli element of [[SESA2029 B5 - Euler-Bernoulli Beam Element|B5]], which is exact for nodal loads. Hence the 20, 200, 2000 sweep.
- The root von Mises stress also converges quickly, because a beam model has no geometric singularity.

## Lab 1 warm-up springs and the coursework spar

Two warm-up problems use COMBIN14 spring–damper elements, whose stiffness is a real constant (spring video, ll. 1–206). In the first, three springs (spring 1 is 100 kN/m) join four nodes 1 m apart, fully fixed at nodes 1 and 4, with 50 kN in $+x$ at node 3; the nodes and elements are created directly, each element given its real-constant set, and the reactions are checked against the load and hand calculation before repeating with 6 and 12 springs. In the second, three springs and a rigid bar carry 4000 lb in $-x$: a 1000 lb/in spring between nodes 1 and 2 and two 500 lb/in springs from node 2 to nodes 3 and 4, which are coincident, with nodes 1, 3 and 4 fixed. The hand solution checks the run: the three springs act in parallel on node 2, so

$$
u_2=\frac{-4000}{1000+500+500}=-2\text{ in},
$$

with reactions of 2000 lb at node 1 and 1000 lb at each of nodes 3 and 4, summing to the applied 4000 lb.

The coursework spar (cantilever video, ll. 1–161) uses BEAM188 (two nodes; BEAM189 has three and quadratic interpolation), an H section with 10 mm flanges and depth and 2 mm walls, linear elastic isotropic steel with $\nu=0.3$, key points at 0 and 200 mm (the coursework uses 2xx mm from the student ID), 20 divisions, all DOF fixed at the root node and 2000 N in $y$ at the tip. Listing the nodal solution gives $u_x$, $u_y$ and the rotation at every node. The von Mises stress needs the cross-section displayed (PlotCtrls → Style → Size and Shape) to show its distribution; it peaks at the root at 5780 MPa, far above yield, so the coursework's first task is to resize the section until it does not yield. The second task applies the uniform and elliptical loads, the third finds how many elements are needed for convergence.

> [!check] Hand check on the root stress of the demonstration spar
> The root moment is $M=2000\times200=4\times10^5$ N mm and the extreme fibre is at $c=5$ mm. For the 2 mm-wall H section, bending about the axis parallel to the flanges gives $I=(10\times10^3-8\times6^3)/12=689$ mm⁴ and $\sigma=Mc/I=2900$ MPa; bending about the axis along the web gives $I=2\times2\times10^3/12+6\times2^3/12=337$ mm⁴ and $\sigma=5930$ MPa. The model's 5780 MPa is close to the second, so the load in that model bends the section about its weak axis. Before resizing, plot the section with `/ESHAPE,1` to see which way it is oriented and use the matching $I$ in the hand check. For the near-solid 4.9 mm section in the table the two values of $I$ are within 2 % (833 against 819 mm⁴), but for the 3 mm section they are 796 and 509 mm⁴, so the orientation changes the UDL and elliptical checks by more than 50 %.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]] · Next: [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]
- Theory: [[SESA2029 B5 - Euler-Bernoulli Beam Element]] · [[Matrix Displacement Method]]

## Sources
- Own APDL beam scripts, generalised (dimensions changed to round illustrative values)
- ANSYS Element Reference (BEAM188), Command Reference (SECDATA, SFBEAM)

## Self-study tasks

### Core

- [ ] Lab 1 coursework task 1: size the H section so the root stress stays below yield (cantilever video, ll. 150–161). → [[#2. Workflow 1: tip point load]]
- [ ] Task 2: compare tip, uniform and elliptical loads of the same total (briefing, 2026-01-30 10:49). → [[#3. Workflow 2: uniform line load]] · [[#5. Workflow 3b: elliptical load as SFBEAM pressures (recommended)]]
- [ ] Task 3: element convergence study (cantilever video, ll. 91–100). → [[#6. Mesh convergence]]

### Further practice

- [ ] Check the spring examples by hand, including the reactions (spring video). → [[#Lab 1 warm-up springs and the coursework spar]]

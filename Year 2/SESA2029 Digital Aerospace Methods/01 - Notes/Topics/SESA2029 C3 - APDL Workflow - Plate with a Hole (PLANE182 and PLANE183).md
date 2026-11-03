---
title: "SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 24
tags:
  - sesa2029
  - apdl
  - plane-stress
  - stress-concentration
  - workflow
aliases: ["APDL plate with hole", "PLANE182 workflow", "Stress concentration APDL"]
date: 2026-10-30
status: lectured
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]", "[[SESA2029 B6 - 2D and 3D Elements]]"]
next_topics: ["[[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]"]
key_concepts: ["[[Stress Concentration Factor and Factor of Safety]]", "[[Plane Stress and Plane Strain]]", "[[Mesh Convergence and Grid Independence]]"]
tutorial_sheets: []
sources: ["Own APDL scripts (generalised)", "ANSYS Element Reference: PLANE182, PLANE183", "02 - Sources/Lectures/SESA2029 Lecture Computer lab2_Plane Stress Video.txt", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-20 - 0959.txt (bulk-stress correction)"]
---

# SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)

> [!abstract] Summary
> Lab 2 models a thin aluminium plate with a circular hole in tension, the classic stress-concentration problem standing in for a window in a fuselage panel or a hole in a wing rib. It is meshed in plane stress with thickness (PLANE182, `KEYOPT(3)=3`), built from a rectangle minus a circle, loaded by a negative edge pressure, and post-processed for the peak von Mises stress, the stress concentration factor $K_t=\sigma_{max}/\sigma_{bulk}$ and the factor of safety. Repeating it with PLANE183 and refining at the hole gives the convergence study; moving the hole gives the coursework sensitivity study. Units here are mm, N and MPa.

> [!summary]- Exam use: quick path
> - **Use it when:** setting up lab 2, computing $K_t$ and FoS, or checking an FE peak stress by hand.
> - **Assumptions:** plane stress, linear elastic, hole far from the loaded edges.
> - **Method:** 1. PLANE182 with thickness as a real constant. 2. `RECTNG`, `CYL4`, `ASBA`. 3. Mesh, refined on the hole edge. 4. Restrain the left edge without over-constraint; tension as negative pressure on the right edge. 5. $K_t$ with the far-field (bulk) stress, FoS $=\sigma_Y/\sigma_{max}$.
> - **Common mistakes:** dividing by the minimum stress in the plate instead of the bulk stress; using the coarse-mesh peak.
> - **Practise:** [[#1. Model]]


## 1. Model
- Aluminium plate, $1000\times400$ mm, thickness 10 mm ($E = 70$ GPa, $\nu = 0.33$).
- Hole of radius 80 mm, centre $(x_h, y_h)$. Moving the hole off-centre is a parameter change.
- Left edge restrained; right edge pulled with $\sigma = 120$ MPa.

Hand check (centred hole), with hole diameter $d = 160$ mm and plate width $W = 400$ mm, so $d/W = 0.4$:
- Infinite plate: $K_t = 3$ (Kirsch; [[Stress Concentration Factor and Factor of Safety]]).
- Finite width, net-section value (Heywood's approximation): $K_{t,net}\approx2+(1-d/W)^3 = 2.22$.
- Gross value: $K_{t,gross} = K_{t,net}/(1-d/W)\approx3.7$.

So expect $\sigma_{max}\approx3.7\times120\approx440$ MPa.

## 2. Script
```apdl
FINISH
/CLEAR,ALL
/PREP7
/TITLE, Plate with a hole - plane stress
! ---------------- parameters ----------------
plate_len = 1000        ! mm
width     = 400         ! mm
thick     = 10          ! mm
radius    = 80          ! mm
x_hole    = plate_len/2
y_hole    = width/2     ! change to move the hole towards an edge
h_global  = 10          ! global element size (mm)
h_hole    = 2           ! local size on the hole edge (mm)
p_tens    = 120         ! MPa applied tension
sig_y     = 460         ! MPa yield stress (for FoS)
elem      = 182         ! 182 = 4-node linear, 183 = 8-node quadratic
! ---------------- element / material ----------------
ET,1,elem
KEYOPT,1,3,3            ! plane stress WITH thickness
R,1,thick               ! thickness as a real constant
MP,EX,1,70000
MP,PRXY,1,0.33
! ---------------- geometry ----------------
RECTNG,0,plate_len,0,width          ! area 1
CYL4,x_hole,y_hole,radius           ! area 2 (the hole)
ASBA,1,2                            ! plate minus hole
! ---------------- mesh ----------------
AESIZE,ALL,h_global
LSEL,S,RADIUS,,radius               ! lines on the hole (by radius of curvature)
LESIZE,ALL,h_hole                   ! local refinement
ALLSEL,ALL
MSHAPE,0,2D                         ! quadrilaterals
MSHKEY,0                            ! free meshing
AMESH,ALL
FINISH
! ---------------- BCs and load ----------------
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,UX,0                          ! symmetry-like restraint of the left edge ...
NSEL,R,LOC,Y,0
D,ALL,UY,0                          ! ... plus ONE point in y (no Poisson over-constraint)
NSEL,S,LOC,X,plate_len
SF,ALL,PRES,-p_tens                 ! negative pressure = tension (pulls outward)
ALLSEL,ALL
SOLVE
FINISH
! ---------------- post ----------------
/POST1
SET,LAST
/EFACET,2                           ! smoother display for 183 midside nodes
PLDISP,1
PLNSOL,S,EQV
NSORT,S,EQV
*GET,s_max,SORT,0,MAX               ! peak von Mises (at the hole edge)
NSEL,S,LOC,X,plate_len
NSEL,R,LOC,Y,width/2
*GET,n_far,NODE,0,NUM,MIN
*GET,s_nom,NODE,n_far,S,EQV         ! far-field (bulk) stress, should be ~p_tens
ALLSEL,ALL
kt  = s_max/s_nom
fos = sig_y/s_max
*VWRITE,s_max,s_nom,kt,fos
('SMAX=',F10.3,'  SNOM=',F10.3,'  KT=',F7.3,'  FOS=',F7.3)
FINISH
```

## 3. Things that go wrong (and why)
- The fixed-edge variant `D,ALL,ALL,0` on the whole left edge is simpler, but it stops that edge contracting laterally (Poisson). The result is spurious stress peaks at the two left corners ([[Boundary Conditions and Rigid Body Modes]]). They are far from the hole, but don't mistake them for $\sigma_{max}$. The script above avoids them.
- Nominal stress. Use the far-field value at the loaded edge. By equilibrium it equals the applied 120 MPa. Never use the minimum stress in the plate: the low-stress "shadow" beside the hole would inflate $K_t$. If you want the net-section $K_t$, divide by $\sigma\,W/(W-d)$ instead, and state which one you used.
- Peak location. For tension in $x$, the peak sits at the top and bottom of the hole (90° from the load axis), where $\sigma_{xx}\approx3\sigma$ locally. Probe there when refining.
- A hole near an edge raises $K_t$ sharply as the ligament thins. This case is only accessible by FE, not by the infinite-plate formula.
- Element order: at the same `h_hole`, PLANE183 captures the curved hole edge and the quadratic stress gradient better. Compare 182 and 183 in the convergence study.

## 4. Convergence and sensitivity studies
Loop over `h_hole` (e.g. 8, 4, 2, 1, 0.5 mm) and both element types. Log `s_max`, `kt` and the number of nodes ([[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]). $K_t$ should flatten, because a round hole is not a singularity. Then sweep `radius`, `x_hole` and `y_hole` to map $K_t$ and FoS against the geometry.

> [!tip] Quarter model
> With a centred hole, the problem is symmetric about both centre lines. Model one quarter:
> - $u_x = 0$ on the vertical symmetry line and $u_y = 0$ on the horizontal one;
> - tension on the outer edge.
>
> This gives 4× fewer DOF and no rigid-body modes. Symmetry BCs are exactly the "no over-constraint" support.

## What the lab 2 video does

The video's plate (ll. 1–170) is 1 m by 0.4 m, 0.01 m thick, aluminium with $E=70$ GPa, $\nu=0.33$ and yield strength 460 MPa, with a hole of radius 0.08 m centred at (0.5, 0.21), slightly above centre, in SI units. PLANE182 is set to plane stress with thickness and the thickness given as a real constant. A free mesh with element size 0.02 m (961 elements) triggers a warning that triangles may be too stiff in bending, harmless here because nothing bends. The left edge is fixed in all DOF (the simple, slightly over-constrained version; see section 3) and $-1\times10^8$ Pa pressure on the right edge pulls with 100 MPa.

The element solution gives a maximum $\sigma_x$ of 377 MPa at the top of the hole. The nodal von Mises maximum is 359 MPa, the element value 360 MPa: nodal solutions are averaged and continuous, element solutions are extrapolated from the integration points and jump between elements. That 377 MPa agrees with the finite-width hand check of section 1, $K_{t,gross}\approx3.7$ times 100 MPa, so the coarse mesh is already close. A path from (0.5, 0.29) at the top of the hole to (0.5, 0.4) at the plate edge, 100 divisions, maps $\sigma_x$ along the ligament for plotting or export to Excel; sorted nodal listings give the extremes. Global refinement takes the mesh to 3842 elements, and local refinement at the hole uses the nodes attached to the hole's lines. In the video's convergence study, a 20 mm element gives about 97 % of the largest peak found and 10 mm about 99.6 %, a trade against computing cost. The coursework then moves the hole towards the edge until the plate yields.

> [!warning] Coursework correction (2026-02-20 09:59, ll. 386–400)
> The coursework load is 120 MPa, and the bulk stress for $K_t$ is therefore 120 MPa, as force equilibrium and the nodal stress on the loaded edge confirm. An earlier value of 83 MPa, read at the lower boundary, was wrong.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]] · Next: [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]
- Theory: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] (SCF section) · [[SESA2029 B6 - 2D and 3D Elements]] · [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]

## Sources
- Own APDL plate scripts, generalised (dimensions and loads made round and illustrative; BC improved to avoid over-constraint)
- Heywood's finite-width approximation; Pilkey, *Peterson's Stress Concentration Factors*

## Self-study tasks

### Core

- [ ] Lab 2 convergence study with global and local refinement (video, ll. 136–166). → [[#4. Convergence and sensitivity studies]]
- [ ] Coursework: $K_t$ and FoS against hole size and position, using a bulk stress of 120 MPa (2026-02-20 09:59, ll. 386–400). → [[#3. Things that go wrong (and why)]]

### Further practice

- [ ] Compare the FE peak with the Heywood finite-width estimate for your own plate. → [[#1. Model]]

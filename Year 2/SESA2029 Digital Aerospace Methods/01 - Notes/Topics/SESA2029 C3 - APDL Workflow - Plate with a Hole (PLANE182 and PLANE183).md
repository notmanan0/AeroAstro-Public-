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
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]", "[[SESA2029 B6 - 2D and 3D Elements]]"]
next_topics: ["[[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]"]
key_concepts: ["[[Stress Concentration Factor and Factor of Safety]]", "[[Plane Stress and Plane Strain]]", "[[Mesh Convergence and Grid Independence]]"]
tutorial_sheets: []
sources: ["Own APDL scripts (generalised)", "ANSYS Element Reference: PLANE182, PLANE183"]
---

# SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)

> [!abstract] Summary
> A rectangular plate with a circular hole in uniaxial tension: the classic **stress-concentration** problem, standing in for cut-outs in fuselage skins and spar webs.
>
> The workflow:
> - models it in **plane stress with thickness** (`KEYOPT(3)=3`);
> - builds the geometry with `RECTNG`, `CYL4` and the Boolean `ASBA`;
> - free-meshes with quads, refined locally at the hole;
> - applies tension as a negative edge pressure;
> - reads $\sigma_{max}$ (von Mises), the nominal stress, $K_t$ and the factor of safety.
>
> Running it with linear **PLANE182** and quadratic **PLANE183** at the same size shows the accuracy gain from p-refinement.
>
> Units: **mm, N, MPa**.

## Key Concepts
- [[Stress Concentration Factor and Factor of Safety]] · [[Plane Stress and Plane Strain]] · [[Mesh Convergence and Grid Independence]] · [[Stress Singularities]]

---

## 1. Model
- Aluminium plate, $1000\times400$ mm, thickness 10 mm ($E = 70$ GPa, $\nu = 0.33$).
- Hole of radius 80 mm, centre $(x_h, y_h)$. Moving the hole off-centre is a parameter change.
- Left edge restrained; right edge pulled with $\sigma = 120$ MPa.

**Hand check (centred hole)**, with hole diameter $d = 160$ mm and plate width $W = 400$ mm, so $d/W = 0.4$:
- Infinite plate: $K_t = 3$ (Kirsch; [[Stress Concentration Factor and Factor of Safety]]).
- Finite width, **net-section** value (Heywood's approximation): $K_{t,net}\approx2+(1-d/W)^3 = 2.22$.
- **Gross** value: $K_{t,gross} = K_{t,net}/(1-d/W)\approx3.7$.

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
- **The fixed-edge variant** `D,ALL,ALL,0` on the whole left edge is simpler, but it stops that edge contracting laterally (Poisson). The result is spurious stress peaks at the two left corners ([[Boundary Conditions and Rigid Body Modes]]). They are far from the hole, but don't mistake them for $\sigma_{max}$. The script above avoids them.
- **Nominal stress.** Use the **far-field** value at the loaded edge. By equilibrium it equals the applied 120 MPa. Never use the minimum stress in the plate: the low-stress "shadow" beside the hole would inflate $K_t$. If you want the **net-section** $K_t$, divide by $\sigma\,W/(W-d)$ instead, and state which one you used.
- **Peak location.** For tension in $x$, the peak sits at the top and bottom of the hole (90° from the load axis), where $\sigma_{xx}\approx3\sigma$ locally. Probe there when refining.
- **A hole near an edge** raises $K_t$ sharply as the ligament thins. This case is only accessible by FE, not by the infinite-plate formula.
- **Element order**: at the same `h_hole`, PLANE183 captures the curved hole edge and the quadratic stress gradient better. Compare 182 and 183 in the convergence study.

## 4. Convergence and sensitivity studies
Loop over `h_hole` (e.g. 8, 4, 2, 1, 0.5 mm) and both element types. Log `s_max`, `kt` and the number of nodes ([[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]). $K_t$ should flatten, because a round hole is **not** a singularity. Then sweep `radius`, `x_hole` and `y_hole` to map $K_t$ and FoS against the geometry.

> [!tip] Quarter model
> With a centred hole, the problem is symmetric about both centre lines. Model one quarter:
> - $u_x = 0$ on the vertical symmetry line and $u_y = 0$ on the horizontal one;
> - tension on the outer edge.
>
> This gives 4× fewer DOF and no rigid-body modes. Symmetry BCs are exactly the "no over-constraint" support.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]] · Next: [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]
- Theory: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]] (SCF section) · [[SESA2029 B6 - 2D and 3D Elements]] · [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]

## Sources
- Own APDL plate scripts, generalised (dimensions and loads made round and illustrative; BC improved to avoid over-constraint)
- Heywood's finite-width approximation; Pilkey, *Peterson's Stress Concentration Factors*

---
title: "SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 25
tags:
  - sesa2029
  - apdl
  - shell-element
  - modal-analysis
  - workflow
aliases: ["APDL wing shell model", "SHELL181 wing", "Wing modal APDL"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]", "[[SESA2029 B6 - 2D and 3D Elements]]", "[[SESA2029 B8 - Modal Analysis]]"]
next_topics: ["[[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]"]
key_concepts: ["[[Plate, Shell and Membrane Elements]]", "[[Natural Frequencies and Mode Shapes]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: []
sources: ["Own APDL scripts (generalised)", "ANSYS Element Reference: SHELL181, SHELL281"]
---

# SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)

> [!abstract] Summary
> A uniform, untapered wing is modelled as a thin **shell skin**:
> - an aerofoil section of splines at the root is extruded along the span;
> - it is meshed with **SHELL181** (4-node linear) or **SHELL281** (8-node quadratic);
> - it is clamped at the root and loaded with different upper and lower surface pressures (net lift).
>
> The **static** run gives the tip deflection and the von Mises stress on the TOP and BOT shell surfaces, and hence the **FoS**. `ASUM` gives the skin area, and area × thickness × density gives the **mass**. The **modal** run (Block Lanczos) gives the first natural frequencies and mode shapes: bending, then torsion.
>
> Two geometry routes:
> - **A**: area → copy → skin (`AL`, `AGEN`, `ASKIN`);
> - **B**: drag the section lines along a spanwise path (`ADRAG`). This one is automation-friendly because it tags upper and lower skins as components.
>
> Units: **SI (m, N, Pa, kg/m³)**. Values are illustrative.

## Key Concepts
- [[Plate, Shell and Membrane Elements]] · [[Natural Frequencies and Mode Shapes]] · [[Stress Concentration Factor and Factor of Safety]] · [[Stress Singularities]]

---

## 1. Parameters and common set-up
```apdl
FINISH
/CLEAR,ALL
/PREP7
/TITLE, Wing shell - static and modal
span       = 10.0       ! m (semi-span, z direction)
mesh_size  = 0.25       ! m  (convergence: 0.5 / 0.25 / 0.125 / 0.0625)
skin_t     = 0.02       ! m  shell thickness
elem_shell = 181        ! 181 linear, 281 quadratic
num_modes  = 6
p_top      = 2000       ! Pa on the upper skin
p_bot      = 7000       ! Pa on the lower skin (net upward load)
ex_mat     = 6.9e10     ! Pa  aluminium
pr_mat     = 0.30
dens_mat   = 2700       ! kg/m^3  (REQUIRED for modal)
sig_y      = 250e6      ! Pa
ET,1,elem_shell
MP,EX,1,ex_mat
MP,PRXY,1,pr_mat
MP,DENS,1,dens_mat
SECTYPE,1,SHELL
SECDATA,skin_t
TYPE,1 $ MAT,1 $ SECNUM,1
! root section keypoints (x = chordwise, y = thickness, z = span)
K,1,0,0,0
K,2,2,0,0
K,3,2.3,0.2,0
K,4,1.9,0.45,0
K,5,1,0.25,0
```

(The section points can be replaced by any aerofoil's coordinates, e.g. an imported NACA table.)

## 2a. Geometry method A: area, copy, skin
```apdl
SPLINE,2,3,4,5,1        ! upper surface -> lines 1..4
SPLINE,1,2              ! lower surface -> line 5
AL,1,2,3,4,5            ! area 1 = root section
AGEN,2,1,,,,,span       ! copy to the tip -> area 2 (lines 6..10)
ASKIN,1,6               ! skin patches between matching root/tip lines -> areas 3..7
ASKIN,2,7
ASKIN,3,8
ASKIN,4,9
ASKIN,5,10              ! areas 3-6 = upper skin, area 7 = lower skin
! ADELE,1,2             ! optional: delete root/tip caps for an open skin (keep them as end ribs otherwise)
ESIZE,mesh_size
AMESH,ALL
```

## 2b. Geometry method B: drag along a path
```apdl
SPLINE,2,3,4,5,1
*GET,l_upper,LINE,0,NUM,MAX
SPLINE,1,2
*GET,l_lower,LINE,0,NUM,MAX
K,101,2,0,span
L,2,101                                 ! spanwise drag path
*GET,l_path,LINE,0,NUM,MAX
LSEL,S,LINE,,l_upper
ADRAG,ALL,,,,,,l_path                    ! upper skin
ASLL,S                                   ! areas attached to the selected lines
CM,UPPER_AREAS,AREA
ALLSEL,ALL
LSEL,S,LINE,,l_lower
ADRAG,ALL,,,,,,l_path                    ! lower skin
ASLL,S
CM,LOWER_AREAS,AREA
ALLSEL,ALL
AESIZE,ALL,mesh_size
AMESH,ALL
SAVE,wing_mesh,db                        ! lets the modal run RESUME the meshed model
```

(If `ASLL` also picks up unwanted areas in your version, select the new areas by location instead, e.g. `ASEL,S,LOC,Y,...`.)

## 3. Static solution
```apdl
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,Z,0
D,ALL,ALL,0                     ! clamped root
ALLSEL,ALL
! method A:  ASEL,S,AREA,,3,6 $ SFA,ALL,1,PRES,p_top $ ASEL,S,AREA,,7 $ SFA,ALL,1,PRES,p_bot
CMSEL,S,UPPER_AREAS             ! method B
SFA,ALL,1,PRES,p_top
CMSEL,S,LOWER_AREAS
SFA,ALL,1,PRES,p_bot
ALLSEL,ALL
SOLVE
FINISH
```

## 4. Post-processing: deflection, stress, FoS, mass
```apdl
/POST1
SET,LAST
/ESHAPE,1
PLDISP,1
NSEL,S,LOC,Z,span
NSORT,U,Y,0,1                   ! sort tip nodes by |UY|
*GET,uy_tip,SORT,0,MAX
ALLSEL,ALL
SHELL,TOP
NSORT,S,EQV
*GET,s_top,SORT,0,MAX
SHELL,BOT
NSORT,S,EQV
*GET,s_bot,SORT,0,MAX
s_max = s_top
*IF,s_bot,GT,s_top,THEN
  s_max = s_bot
*ENDIF
fos = sig_y/s_max
FINISH
/PREP7
ASEL,ALL
ASUM                             ! total shell area
*GET,a_tot,AREA,0,AREA
mass   = a_tot*skin_t*dens_mat   ! kg
weight = mass*9.81               ! N
ALLSEL,ALL
FINISH
*VWRITE,uy_tip,s_max,fos,mass
('TIP |UY|=',E12.4,' m  SMAX=',E12.4,' Pa  FOS=',F8.3,'  MASS=',F10.2,' kg')
```

A first estimate of the skin volume is $2c\,l\,t$ (two surfaces × chord × span × thickness). `ASUM` gives the exact developed area, including the curved surfaces and any end caps.

## 5. Modal solution
```apdl
! same session (BCs still applied)            | or restart:  RESUME,wing_mesh,db
/SOLU
ANTYPE,MODAL
MODOPT,LANB,num_modes           ! Block Lanczos
MXPAND,num_modes,,,YES          ! expand shapes + element results
NSEL,S,LOC,Z,0
D,ALL,ALL,0                     ! (re)apply the root clamp
ALLSEL,ALL
SOLVE
FINISH
/POST1
SET,LIST                        ! table of natural frequencies
*DIM,freq,ARRAY,num_modes
*DO,i,1,num_modes
  *GET,freq(i),MODE,i,FREQ
  SET,1,i
  PLDISP,1                      ! view each mode shape
*ENDDO
FINISH
```

**Interpreting the modes**:
- mode 1 is usually **first flap-wise bending**;
- then in-plane (chord-wise) bending and/or **first torsion**;
- then second bending.

The mode-shape amplitudes and modal "stresses" are relative only ([[Natural Frequencies and Mode Shapes]]).

## 6. Studies and what to expect
| Study | Change | Expected trend |
|---|---|---|
| Element type × mesh | SHELL181 vs 281, `mesh_size` halved each run | 281 converges faster for bending and curvature; linear shells need finer meshes; stresses at the clamped root corners may **not** converge (singularity) |
| Skin thickness | `skin_t` sweep | stress ∝ ≈1/t (bending: $\sigma\sim M/t$ per unit width), so FoS rises and mass rises ∝ t: the weight–safety trade-off |
| Material | $E$, $\rho$, $\sigma_Y$ for aluminium, steel, CFRP | find the **minimum thickness** meeting a FoS target (e.g. 1.5), then compare masses: specific strength $\sigma_Y/\rho$ decides |
| Frequencies | thickness, material | $f\propto\sqrt{K/M}$. For uniform skin thickening, $K$ and $M$ both scale with $t$, so the bending frequency stays nearly constant; $E/\rho$ (specific stiffness) sets $f$ |

> [!warning] Four wing-specific traps
> 1. **Pressure direction**: `SFA` pressure acts along the area's normal. If the wing deflects the wrong way, flip the signs of `p_top`/`p_bot` or reverse the normals. Turn on pressure symbols (*PlotCtrls → Symbols*) to see the arrows.
> 2. **Root stress singularity**: the clamped edge meets a sharp change at the root. Peak stress there **rises with refinement**, so assess convergence and FoS slightly outboard ([[Stress Singularities]]).
> 3. **Trailing-edge elements**: the thin, sharp trailing edge creates high-aspect-ratio or warped elements. Check the element shapes, or switch to SHELL281 ([[FE Element Quality Checks]]).
> 4. **No density, no modes**: `MP,DENS` is mandatory for modal analysis.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]] · Next: [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]
- Theory: [[SESA2029 B6 - 2D and 3D Elements]] · [[SESA2029 B8 - Modal Analysis]] · [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- Verify the wing model before trusting it: [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]

## Sources
- Own APDL wing scripts, generalised (span, thickness and file names made generic)
- ANSYS Element Reference (SHELL181, SHELL281); Command Reference (ADRAG, ASKIN, MODOPT, MXPAND)

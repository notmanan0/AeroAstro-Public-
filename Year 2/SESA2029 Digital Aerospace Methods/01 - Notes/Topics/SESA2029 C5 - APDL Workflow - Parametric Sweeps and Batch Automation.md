---
title: "SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 26
tags:
  - sesa2029
  - apdl
  - automation
  - parametric-study
  - workflow
aliases: ["APDL automation", "APDL sweeps", "APDL macros", "Mesh convergence automation"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]", "[[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]"]
next_topics: ["[[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]"]
key_concepts: ["[[Mesh Convergence and Grid Independence]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: []
sources: ["Own APDL automation scripts (master .inp + case .mac pattern)", "ANSYS Command Reference: *DO, *USE, *CFOPEN, *VWRITE"]
---

# SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation

> [!abstract] Summary
> Mesh-convergence and design-sensitivity studies need the same model rebuilt many times. Automate it with two files:
> - a **master** `.inp` that holds the parameter lists and the loops;
> - a **case macro** `.mac` that builds, solves and post-processes **one** case from its arguments `ARG1…ARG9` and appends one row to a results file.
>
> Results go to plain text through `*CFOPEN`/`*VWRITE`, ready for Python or Excel. Typical studies:
> - mesh size × element order (convergence);
> - hole radius and position ($K_t$, FoS);
> - skin thickness × material (FoS, mass, frequencies, minimum thickness to meet a FoS target).

## Key Concepts
- [[Mesh Convergence and Grid Independence]] · [[Stress Concentration Factor and Factor of Safety]] · [[h- and p-Refinement]]

---

## 1. Architecture
```mermaid
flowchart LR
  M["master.inp: parameters, *DIM lists, *CFOPEN header"] -->|"*DO over lists"| C["*USE,case.mac,ARG1..ARG5"]
  C --> R["reset model: LSCLEAR / ACLEAR / ADELE"]
  R --> B["build geometry + mesh from ARGs"] --> S["BCs, loads, SOLVE"] --> P["*GET outputs"] --> W["*VWRITE one row"]
  W -->|"next case"| M
```

**How to run**:
1. Put `master.inp` and `case.mac` in the **working directory** (*File → Change Directory*).
2. Run *File → Read Input From… → master.inp*, or type `/INPUT,master,inp`.
3. Open the results `.txt` in Python. Keep the GUI plots for spot checks only.

## 2. Case macro: plate with a hole (`plate_case.mac`)
`ARG1` = local mesh size at the hole, `ARG2` = radius, `ARG3` = hole $x$, `ARG4` = hole $y$, `ARG5` = element type (182/183).

```apdl
! ---------- plate_case.mac ----------
/PREP7
LSCLEAR,ALL                 ! remove loads/BCs from the previous case
ACLEAR,ALL                  ! remove previous mesh
ADELE,ALL,,,1               ! remove areas + their lines/keypoints
NUMSTR,DEFA                 ! restart entity numbering
ET,1,ARG5
KEYOPT,1,3,3
R,1,thick
MP,EX,1,70000
MP,PRXY,1,0.33
RECTNG,0,plate_len,0,width
CYL4,ARG3,ARG4,ARG2
ASBA,1,2
AESIZE,ALL,h_global
LSEL,S,RADIUS,,ARG2
LESIZE,ALL,ARG1
ALLSEL,ALL
MSHAPE,0,2D
MSHKEY,0
AMESH,ALL
*GET,n_nodes,NODE,0,COUNT
FINISH
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,X,0
D,ALL,UX,0
NSEL,R,LOC,Y,0
D,ALL,UY,0
NSEL,S,LOC,X,plate_len
SF,ALL,PRES,-p_tens
ALLSEL,ALL
SOLVE
FINISH
/POST1
SET,LAST
NSORT,S,EQV
*GET,s_max,SORT,0,MAX
NSEL,S,LOC,X,plate_len
NSEL,R,LOC,Y,width/2
*GET,n_far,NODE,0,NUM,MIN
*GET,s_nom,NODE,n_far,S,EQV
ALLSEL,ALL
kt  = s_max/s_nom
fos = sig_y/s_max
*CFOPEN,plate_results,txt,,APPEND
*VWRITE,ARG5,ARG1,ARG2,ARG3,ARG4,n_nodes,s_max,kt,fos
(F5.0,2X,F7.3,2X,F7.2,2X,F8.2,2X,F8.2,2X,F9.0,2X,E13.5,2X,F7.3,2X,F7.3)
*CFCLOS
FINISH
```

## 3. Master: mesh convergence × element order, then geometry sweeps (`plate_master.inp`)
```apdl
FINISH
/CLEAR,ALL
plate_len = 1000 $ width = 400 $ thick = 10
h_global  = 10   $ p_tens = 120 $ sig_y = 460
r_base = 80 $ x_base = plate_len/2 $ y_base = width/2
*CFOPEN,plate_results,txt                      ! new file + header
*VWRITE
('ELEM  H_HOLE  RADIUS  X_HOLE   Y_HOLE   NODES    SMAX        KT      FOS')
*CFCLOS
! --- 1) convergence: local size x element order ---
*DIM,h_list,ARRAY,5
h_list(1) = 8,4,2,1,0.5
*DIM,e_list,ARRAY,2
e_list(1) = 182,183
*DO,ie,1,2
  *DO,ih,1,5
    *USE,plate_case.mac,h_list(ih),r_base,x_base,y_base,e_list(ie)
  *ENDDO
*ENDDO
! --- 2) hole radius sweep at the converged size ---
*DIM,r_list,ARRAY,5
r_list(1) = 40,60,80,100,120
*DO,ir,1,5
  *USE,plate_case.mac,1,r_list(ir),x_base,y_base,183
*ENDDO
! --- 3) hole position sweeps ---
*DIM,y_list,ARRAY,5
y_list(1) = 200,170,140,120,100                ! towards the lower edge (radius 80 -> ligament shrinks)
*DO,iy,1,5
  *USE,plate_case.mac,1,r_base,x_base,y_list(iy),183
*ENDDO
```

> [!warning] APDL automation gotchas
> - **`/CLEAR` inside a loop wipes the loop's parameters.** Reset the *model* instead (`LSCLEAR`, `ACLEAR`, `ADELE,ALL,,,1`, `NUMSTR,DEFA`). If you must clear, bracket it with `PARSAV,ALL,keep,parm` … `PARRES,CHANGE,keep,parm`.
> - Booleans renumber entities, so select by **location or radius**, never by a remembered number.
> - The `*VWRITE` format line **must** follow immediately. Array arguments pass by value (`h_list(ih)` is fine).
> - Guard against failed solves (non-converged or singular). Test a returned value and write a sentinel (e.g. −1) so the table keeps its shape.
> - Keep each study's output in its own file, or add a study-ID column.
> - Save one representative contour per study as an image (`/SHOW,PNG` … `PLNSOL` … `/SHOW,CLOSE`) rather than hundreds.

## 4. Wing study: thickness × material with a minimum-thickness search
The case macro `wing_case.mac` follows [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]] with `ARG1` = element type, `ARG2` = mesh size, `ARG3` = skin thickness, `ARG4` = material index. It writes the element, mesh, $t$, material, mass, tip deflection, $\sigma_{max}$, FoS and $f_1$–$f_3$, and **stores `fos` and `mass` as parameters** for the master to use.

```apdl
! ---------- wing_master.inp (outline) ----------
fos_target = 1.5
*DIM,mat_E,ARRAY,3 $ *DIM,mat_PR,ARRAY,3 $ *DIM,mat_RHO,ARRAY,3 $ *DIM,mat_SY,ARRAY,3
mat_E(1)   = 69e9,  200e9, 135e9           ! aluminium, steel, CFRP (quasi-isotropic, illustrative)
mat_PR(1)  = 0.33,  0.30,  0.30
mat_RHO(1) = 2700,  7850,  1600
mat_SY(1)  = 250e6, 350e6, 600e6
*DIM,t_list,ARRAY,6
t_list(1)  = 0.005,0.01,0.02,0.03,0.05,0.10
*DIM,t_min,ARRAY,3                          ! minimum thickness per material meeting fos_target
*DO,im,1,3
  t_min(im) = -1                             ! sentinel: not achieved
  *DO,it,1,6
    *USE,wing_case.mac,181,0.25,t_list(it),im   ! (inside: MP from mat_*(ARG4); sets fos, mass)
    *IF,t_min(im),LT,0,THEN
      *IF,fos,GE,fos_target,THEN
        t_min(im) = t_list(it)               ! first (thinnest) passing thickness
      *ENDIF
    *ENDIF
  *ENDDO
*ENDDO
*CFOPEN,wing_minimums,txt
*VWRITE,t_min(1),t_min(2),t_min(3)
('T_MIN  AL=',F8.4,'  STEEL=',F8.4,'  CFRP=',F8.4,'  (m, -1 = not met)')
*CFCLOS
```

**Reading the results**:
- **Mass at the minimum thickness** is the real comparison between materials. It scales roughly as $\rho/\sigma_Y$ for a strength-limited design.
- Frequencies scale as $\sqrt{E/\rho}$ and hardly change with uniform skin thickening ([[Natural Frequencies and Mode Shapes]]).
- Mass (and weight = 9.81 × mass) and FoS both rise with thickness: the design trade-off.

## 5. Post-processing the text output in Python
```python
import numpy as np, matplotlib.pyplot as plt
d = np.loadtxt("plate_results.txt", skiprows=1)
for elem in (182, 183):
    s = d[(d[:, 0] == elem) & (d[:, 2] == 80) & (d[:, 4] == 200)]
    fig, ax = plt.subplots(figsize=(7, 4.5), constrained_layout=True)
    ax.semilogx(s[:, 5], s[:, 7], "o-", lw=2, label=f"PLANE{int(elem)}")
    ax.set_xlabel("number of nodes"); ax.set_ylabel("$K_t$"); ax.legend(); ax.grid(True, ls="--", alpha=0.5)
    fig.savefig(f"kt_convergence_{int(elem)}.png", dpi=300, bbox_inches="tight"); plt.close(fig)
```

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]] · Next: [[SESA2029 C6 - APDL Workflow - FE Model Verification Checks]]
- What the sweeps are for: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]] · [[Mesh Convergence and Grid Independence]]

## Sources
- Own APDL automation scripts (master `.inp` + case `.mac` pattern), generalised and rewritten to avoid `/CLEAR` inside loops
- ANSYS Command Reference (*DO, *USE, *CFOPEN, *VWRITE, PARSAV/PARRES, NUMSTR)

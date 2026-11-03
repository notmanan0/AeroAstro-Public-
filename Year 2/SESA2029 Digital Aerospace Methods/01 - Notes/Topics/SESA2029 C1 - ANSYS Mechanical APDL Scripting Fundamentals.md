---
title: "SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 22
tags:
  - sesa2029
  - apdl
  - ansys
  - workflow
aliases: ["APDL basics", "APDL scripting", "Mechanical APDL command reference"]
date: 2026-10-30
status: lectured
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
next_topics: ["[[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]"]
key_concepts: ["[[Matrix Displacement Method]]", "[[Boundary Conditions and Rigid Body Modes]]", "[[Shape Functions]]"]
tutorial_sheets: []
sources: ["Own APDL scripts (generalised)", "02 - Sources/FEM Lectures/FEA.txt (L7 APDL demonstration)", "ANSYS Mechanical APDL Command Reference", "02 - Sources/Lectures/SESA2029 Lecture Software_Intro.txt", "02 - Sources/Lectures/SESA2029 Lecture 2026-01-30 - 1049.txt", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-20 - 0959.txt (APDL demonstration)"]
---

# SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals

> [!abstract] Summary
> APDL, the ANSYS Parametric Design Language, drives Mechanical APDL with plain-text commands that follow a fixed processor cycle: begin level, `/PREP7` for the model, `/SOLU` for loads and solution, `/POST1` for results. The labs are done through the menus, and scripting is not required for the coursework, but every menu action is logged as a command, so a cleaned and parametrised log becomes a script that rebuilds the whole model when one number changes. This note is the toolkit; C2 to C6 are complete workflows built from it.

> [!summary]- Exam use: quick path
> - **Use it when:** turning a lab model into a script, or debugging a run that will not solve.
> - **Assumptions:** one consistent unit set; Mechanical APDL (not Workbench).
> - **Method:** 1. `FINISH` and `/CLEAR`. 2. Parameters at the top. 3. `/PREP7`: element, material, geometry, mesh. 4. `/SOLU`: supports, loads, `SOLVE`. 5. `/POST1`: `SET,LAST`, plot, `*GET` the numbers.
> - **Common mistakes:** applying `D` or `SOLVE` with only part of the model selected (`ALLSEL` first); mixed units.
> - **Practise:** [[#1. From GUI to script]] · [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]


## 1. From GUI to script
1. Build one model interactively.
2. Open the Session Editor (or the `jobname.log` file). It records every GUI action as a command, including mistakes and view changes.
3. Clean it: delete the view and zoom commands and dead ends. Replace `FLST/FITEM` pick lists with explicit entities (e.g. `SPLINE,2,3,4,5,1`).
4. Parametrise: put every dimension, material value, mesh size and load at the top as named parameters.
5. Paste blocks into the command window one stage at a time (geometry, then mesh, then solve, then post), checking each step. Or run the whole file with *File → Read Input From…* (`/INPUT,fname,ext`).
6. Unsure what a command does? Select it and press F1, or look it up in the Command Reference. Its fields work like a function's arguments.

## 2. Processor cycle and skeleton
```apdl
FINISH
/CLEAR,ALL                 ! fresh database (also clears parameters)
/TITLE, My analysis
! ---------- parameters (units: pick ONE consistent set) ----------
L_len   = 250              ! mm
E_mat   = 2.1e5            ! MPa  (mm-N-MPa set; density would be tonne/mm^3)
nu_mat  = 0.30
/PREP7                     ! ---------- pre-processor ----------
ET,1,188                   ! element type
MP,EX,1,E_mat              ! material 1
MP,PRXY,1,nu_mat
! SECTYPE / SECDATA (beams, shells)  or  R (real constants, e.g. PLANE182 thickness)
! geometry (K, L, A, V ...) -> mesh controls -> xMESH
FINISH
/SOLU                      ! ---------- solution ----------
ANTYPE,STATIC              ! or MODAL
! D (displacement BCs), F (nodal forces), SF/SFA/SFBEAM (pressures), ACEL (gravity)
SOLVE
FINISH
/POST1                     ! ---------- general post-processor ----------
SET,LAST
PLDISP,1                   ! deformed + undeformed outline
PLNSOL,S,EQV               ! von Mises contour
FINISH
```

## 3. Units
FE software has no units, so choose a consistent set and keep to it:

| Set | Length | Force | Stress / $E$ | Density | Typical use |
|---|---|---|---|---|---|
| SI | m | N | Pa | kg/m³ | shells and wings, modal work |
| mm-N-MPa | mm | N | MPa (N/mm²) | tonne/mm³ (e.g. steel $7.85\times10^{-9}$) | beams and plates in mm |

Mixing mm geometry with Pa moduli gives stresses wrong by $10^6$.

## 4. Command glossary
| Group | Commands | Notes |
|---|---|---|
| Session | `FINISH`, `/CLEAR`, `/PREP7`, `/SOLU`, `/POST1`, `/TITLE`, `SAVE`/`RESUME` | `SAVE,name,db` after meshing lets later runs `RESUME` |
| Element and material | `ET`, `KEYOPT`, `R`, `MP`, `SECTYPE`/`SECDATA`, `TYPE`/`MAT`/`SECNUM`/`REAL` | thickness goes in `R` for PLANE182/183 with `KEYOPT(3)=3`, but in `SECDATA` for SHELL181/281 and beam sections |
| Geometry | `K`, `L`, `SPLINE`, `AL`, `A`, `RECTNG`, `CYL4`, `ASBA`, `AGEN`, `ASKIN`, `ADRAG`, `VEXT` | Booleans (`ASBA` = area minus area) renumber entities, so select by location, not number |
| Meshing | `LESIZE`, `ESIZE`, `AESIZE`, `MSHAPE`, `MSHKEY`, `LMESH`/`AMESH`/`VMESH`, `ACLEAR`, `NUMMRG` | `MSHAPE,0,2D` + `MSHKEY,0` = free quads; `MSHKEY,1` = mapped |
| Selection | `NSEL`, `ESEL`, `LSEL`, `ASEL`, `KSEL`, `ALLSEL`, `NSLE`, `ASLL`, `CM`/`CMSEL` | `S` = new set, `R` = reselect, `A` = add, `U` = unselect; always `ALLSEL` before `SOLVE` |
| Loads and BCs | `D`, `DDELE`, `F`, `SF`, `SFA`, `SFBEAM`, `ACEL`, `LSCLEAR` | `D,ALL,ALL,0` fixes every DOF of the selected nodes |
| Solution | `ANTYPE`, `MODOPT`, `MXPAND`, `NLGEOM`, `NSUBST`, `SOLVE` | modal needs `MP,DENS` |
| Post | `SET`, `PLDISP`, `PLNSOL`, `PRNSOL`, `NSORT`, `PRRSOL`, `FSUM`, `SHELL`, `/ESHAPE`, `/EFACET`, `ETABLE`/`PLETAB` | `/ESHAPE,1` renders beam and shell thickness |
| Parameters and programming | `*GET`, `*SET`, `*DIM`, `*DO`/`*ENDDO`, `*IF`/`*ELSEIF`/`*ENDIF`, `*EXIT`, `*USE`, `*CREATE`/`*END`, `*VWRITE`, `*CFOPEN`/`*CFCLOS`, `PARSAV`/`PARRES` | APDL arithmetic: `**` is the power; `SQRT`, `SIN`, `ABS`, `NINT` … |

## 5. Robust selection and *GET patterns
```apdl
! node at a location (never assume numbering after re-meshing)
NSEL,S,LOC,X,L_len
*GET,n_tip,NODE,0,NUM,MIN      ! lowest-numbered selected node
ALLSEL,ALL

! scalar results
*GET,uy_tip,NODE,n_tip,U,Y     ! displacement
NSORT,S,EQV                    ! sort selected nodes by von Mises ...
*GET,s_max,SORT,0,MAX          ! ... and grab the maximum
*GET,f1,MODE,1,FREQ            ! natural frequency of mode 1 (after SET,LIST / modal solve)
ASUM                           ! area properties of selected areas ...
*GET,a_tot,AREA,0,AREA         ! ... total area (then mass = a_tot*t*rho)
*GET,n_count,NODE,0,COUNT      ! how many nodes are selected
```

## 6. Loops, conditionals, output
```apdl
*DIM,h_list,ARRAY,4
h_list(1) = 20,10,5,2           ! fills h_list(1..4)
*CFOPEN,convergence,txt,,APPEND ! open (append) a text file
*DO,i,1,4
  h = h_list(i)
  ! ... rebuild mesh with size h, solve, *GET s_max ...
  *IF,s_max,GT,1e9,THEN          ! guard against a failed solve
    s_max = -1
  *ENDIF
  *VWRITE,h,s_max
  (F10.3,2X,E16.8)
*ENDDO
*CFCLOS
```

- The `*VWRITE` format line must follow immediately, in Fortran-style parentheses: `F` fixed, `E` exponent, `X` spaces, `/` newline, text in quotes.
- `*DO` loops can nest (up to 20 levels deep).
- Macro arguments `ARG1`–`ARG9` are local to a `*USE`d macro.

## 7. Common pitfalls (from experience)
- Model won't solve / "zero pivot": missing supports, so a rigid-body mode ([[Boundary Conditions and Rigid Body Modes]]). Check that `D` was applied to a *selected* set, and `ALLSEL` before `SOLVE`.
- Deflection in the wrong direction: pressure sign vs the shell/area normal. A positive `SF`/`SFA` pressure pushes *into* the face. Flip the sign or reverse the normals (`ENORM`/`AREVERSE`). For beams, check the `SFBEAM` load key against the beam orientation.
- Changing a parameter changes nothing in the plot: results weren't re-read. Issue `SET,LAST` again after re-solving, or re-run from `/CLEAR`.
- No modal results: `MP,DENS` missing, so $[M] = 0$.
- Cannot reopen a job: a stale lock or internal file. Relaunch with a new job name and `RESUME` the `.db` from inside the program.
- Crashes at fine meshes: too many DOF for memory or the licence, or distorted elements. Check with `SHPP,SUMMARY` / `CHECK` before solving ([[FE Element Quality Checks]]).
- Stress keeps rising with refinement: a singularity (sharp corner, point load). Don't use it as the convergence metric ([[Stress Singularities]]).
- `/CLEAR` inside a loop wipes your loop parameters. Rebuild with `ACLEAR`/`ADELE`/`LSCLEAR` instead, or save and restore them with `PARSAV`/`PARRES` ([[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]).

## What the software videos and briefing cover

The Software_Intro video sets the scene (ll. 1–157). ANSYS is not on the standard virtual desktop: use the older VDI service (VMware Horizon client, server `vdi.soton.ac.uk`), or install ANSYS from `software.soton.ac.uk`, connected to the university VPN during installation and every launch so the licence can be found. Launch through the Mechanical APDL Product Launcher, which sets the working directory (a new folder per project) and the job name that prefixes every output file, and offers batch mode, in which an input file runs without the user interface and writes an output file. Workbench can run APDL command snippets before or after its own solve, but APDL gives direct access to the mesh and specialist elements.

In the interface, commands are a name followed by comma-separated arguments, with blank fields taking defaults; Help documents every command and the processor it belongs to. `FINISH` returns to the begin level; `/PREP7`, `/SOLU` and `/POST1` enter the processors (`/POST26` is the time-history post-processor for transients). Parameters are defined with `=` or `*SET`, must start with a letter, use only letters, digits and underscores, and have at most 32 characters; `**` is the power operator; array parameters must be dimensioned before they are filled or read from a file. Start scripts with `FINISH` and `/CLEAR`, end them with `/EXIT` to close ANSYS automatically, comment with `!`, and recover any command from the log file (List → Files → Log File). Save scripts as `.inp` or `.txt` and run them with File → Read Input From.

The FEA coursework briefing (2026-01-30 10:49) describes the three labs and their coursework extensions: lab 1 spring and cantilever-beam models (beam section sizing to avoid yield, tip, uniform and elliptical loads, element convergence; [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)|C2]]); lab 2 plate with a hole (mesh sensitivity, hole size and position, factor of safety and stress concentration factor; [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)|C3]]); lab 3 shell wing (SHELL181 against SHELL281, skin thickness, materials and minimum thickness; [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]]). Each student's dimensions come from their ID: the beam semi-span is 2xx mm with xx the last two digits. The report is at most 10 pages, about three per lab, marked 30, 30 and 40, due on 16 March. Scripting "we are not expected for this course"; the Session Editor is for advanced users, though it pays off in later projects that run thousands of cases. Dr Yuan demonstrated it between the lectures of 2026-02-20 for the lab 2 parametric study ([[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation|C5]]).

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Next: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- Theory each workflow implements: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]

## Sources
- Own APDL scripts (generalised and parametrised); FEA lecture APDL demonstration (transcript `FEA.txt`, L7)
- ANSYS Mechanical APDL Command Reference and Element Reference

## Self-study tasks

Nothing in this note was set as a separate exercise; the tasks come from the lab sheets.

### Core

- [ ] Install or access ANSYS and run the lab 1 spring example before the first lab (briefing, 2026-01-30 10:49). → [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- [ ] Find the commands for one lab model in the log file and save them as a script (Software_Intro, ll. 136–157). → [[#1. From GUI to script]]

### Further practice

- [ ] Parametrise one dimension of your script and rerun it (suggested, not lecturer-set). → [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]

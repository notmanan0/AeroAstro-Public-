---
title: "SESA2029 C6 - APDL Workflow - FE Model Verification Checks"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part C: APDL Workflows"
order: 27
tags:
  - sesa2029
  - apdl
  - verification
  - workflow
aliases: ["APDL model checks", "Free-free modal APDL", "Unit gravity check APDL"]
date: 2026-10-30
status: lectured
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B10 - FE Verification, Validation and Model Updating]]", "[[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]"]
next_topics: []
key_concepts: ["[[FE Model Verification Checks]]", "[[FE Element Quality Checks]]", "[[Boundary Conditions and Rigid Body Modes]]"]
tutorial_sheets: []
sources: ["02 - Sources/FEM Lectures/Lecture_12_Validation and Verification_final(1).pdf", "ANSYS Command Reference: NUMMRG, SHPP, CHECK, IRLF, ACEL, FSUM, PRRSOL", "02 - Sources/Lectures/SESA2029 Lecture 2026-03-06 - 1055.txt"]
---

# SESA2029 C6 - APDL Workflow - FE Model Verification Checks

> [!abstract] Summary
> This note turns the verification checklist of FEA Lecture 12 into APDL commands to run before trusting any model, such as the lab 3 wing. Housekeeping merges coincident key points and nodes and checks element shapes; the total mass is compared with a hand estimate and the reactions with the applied loads; a free–free modal analysis should give exactly six rigid-body modes; unit gravity and unit enforced displacement checks expose loose or illegally grounded nodes; and a hand calculation on a simplified version of the problem closes the loop.

> [!summary]- Exam use: quick path
> - **Use it when:** about to report results from a model built by hand or by script.
> - **Assumptions:** a linear model; for the modal checks, density defined.
> - **Method:** 1. `NUMMRG` and shape checks. 2. Mass and reaction balance. 3. Free–free modal: six near-zero frequencies. 4. Unit gravity and unit displacement. 5. Hand check.
> - **Common mistakes:** more than six zero modes ignored (a loose part); forgetting to remove supports for the free–free run.
> - **Practise:** [[#4. Free–free modal check]]


## 1. Housekeeping: geometry and mesh
```apdl
/PREP7
NUMMRG,KP                ! merge coincident keypoints (do this BEFORE meshing)
! ... mesh ...
NUMMRG,NODE              ! merge coincident nodes created by separate meshes
                         !   (careful: don't merge intentionally coincident nodes, e.g. spring ends)
SHPP,SUMMARY             ! element shape-testing summary (aspect ratio, angles, warping)
CHECK,ESEL,WARN          ! list elements that fail warning limits
/PSYMB,ESYS,1            ! show element coordinate systems (check consistent shell normals)
EPLOT
```

Shape-test warnings compromise accuracy. Errors must be fixed, for example by switching to quadratic elements, remeshing the trailing edge, or reducing the local size ([[FE Element Quality Checks]]).

## 2. Mass check
```apdl
/SOLU
ANTYPE,STATIC
IRLF,-1                  ! precalculate masses: prints a mass summary during SOLVE
SOLVE
```

Or use `ASUM` × thickness × density for shells. Compare with a hand estimate (e.g. $2ctl\rho$ for a wing skin). A factor of 1000 error means a unit problem ([[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals]]).

## 3. Reaction balance
```apdl
/POST1
SET,LAST
PRRSOL                   ! list reactions at constrained nodes
NSEL,S,LOC,Z,0           ! root nodes
FSUM                     ! sum of nodal forces on the selection = reaction totals
ALLSEL,ALL
```

The sum of reactions must equal the applied loads (e.g. net pressure × projected area for the wing). If it doesn't, loads are going missing or the pressure is acting on the wrong face.

## 4. Free–free modal check
```apdl
/SOLU
DDELE,ALL,ALL            ! remove ALL displacement constraints
ANTYPE,MODAL
MODOPT,LANB,12           ! ask for more than 6 so the first flexible modes are visible
MXPAND,12,,,YES
SOLVE
FINISH
/POST1
SET,LIST                 ! expect 6 frequencies ~0 Hz, then a clear jump
```

- Pass: 6 near-zero modes (e.g. $10^{-4}$ Hz). Tiny non-zero values are round-off.
- Fail:
  - more than 6 near-zero modes means a part is disconnected, e.g. an engine pylon not attached (12 modes);
  - fewer than 6 means illegal grounding, i.e. a stray constraint.

Animate the extra zero modes (`SET,1,i` + `PLDISP`) to see *which* part floats.

## 5. Unit gravity check (three load cases)
```apdl
! re-apply the real supports first
/SOLU
ANTYPE,STATIC
NSEL,S,LOC,Z,0
D,ALL,ALL,0
ALLSEL,ALL
ACEL,9.81,0,0            ! 1 g in X   (then repeat with ACEL,0,9.81,0 and ACEL,0,0,9.81)
SOLVE
FINISH
/POST1
SET,LAST
PLDISP,1                 ! smooth, plausible sag; no isolated nodes flying off
NSEL,S,LOC,Z,0
FSUM                     ! reaction = total weight in that direction
ALLSEL,ALL
```

Isolated large displacements reveal loosely connected DOF: bad springs, MPC or constraint equations, or unmerged nodes.

## 6. Unit enforced displacement check
```apdl
/SOLU
DDELE,ALL,ALL
NSEL,S,LOC,Z,0
D,ALL,UX,1.0             ! translate the support set by 1 unit in X
D,ALL,UY,0 $ D,ALL,UZ,0 $ D,ALL,ROTX,0 $ D,ALL,ROTY,0 $ D,ALL,ROTZ,0
ALLSEL,ALL
SOLVE                    ! with no other loads the whole model should translate rigidly
FINISH
/POST1
SET,LAST
PLNSOL,U,X               ! should be 1.0 everywhere
PLNSOL,S,EQV             ! should be ~0 everywhere (non-zero = spurious grounding / constraint)
```

Repeat for $y$, $z$ and unit rotations. A rotation needs consistent translations at off-axis support nodes. Any stress means some DOF is illegally grounded.

## 7. Hand-calculation check
Before any study, run a simplified case with a closed-form answer:
- wing as a cantilever with a UDL: $\delta_{tip} = wL^4/8EI$ and $M_{root} = wL^2/2$;
- plate with a centred hole: $K_t\approx3$ (large plate) or the Heywood finite-width value;
- modal: $f_1 = \dfrac{1.875^2}{2\pi}\sqrt{\dfrac{EI}{mL^4}}$ for a uniform cantilever, where $m$ is the mass per unit length.

Order-of-magnitude agreement confirms units, loads and BCs. Close agreement confirms the element choice.

## Where this comes from

The checks are those of [[SESA2029 B10 - FE Verification, Validation and Model Updating|B10]] (2026-03-06 10:55, ll. 51–225): accuracy checks such as coincident nodes and elements, wrong connections and distorted elements; then the free–free modal, unit enforced displacement, unit gravity and thermal checks of mathematical soundness. The lecture names them and shows the free–free result on a wing; the commands here are one way to run them in Mechanical APDL. None was set as a lab task, but the free–free check costs one modal run and catches the commonest modelling error, a part that is not connected.

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 C5 - APDL Workflow - Parametric Sweeps and Batch Automation]]
- Theory: [[SESA2029 B10 - FE Verification, Validation and Model Updating]] · [[FE Model Verification Checks]]

## Sources
- FEA Lecture 12 checks (free–free modal, unit enforced displacement, unit gravity), implemented in APDL
- ANSYS Command Reference (NUMMRG, SHPP, CHECK, IRLF, ACEL, FSUM, PRRSOL, DDELE)

## Self-study tasks

No check was set as an exercise.

### Further practice

- [ ] Run the free–free modal and mass checks on your lab 3 wing (suggested, not lecturer-set). → [[#4. Free–free modal check]] · [[#2. Mass check]]

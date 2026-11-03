---
title: "SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 12
tags: [sesa2029, fea, matrix-displacement-method]
aliases: ["Matrix displacement method", "Direct stiffness method", "MDM", "FEA Lectures 1-3"]
date: 2026-10-30
status: lectured
coverage: "FEA weeks 1–2 (2026-01-30 10:00; 2026-02-06 09:59)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: []
next_topics: ["[[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]"]
key_concepts: ["[[Matrix Displacement Method]]", "[[Global Stiffness Matrix Assembly]]", "[[Boundary Conditions and Rigid Body Modes]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_3_Matrix_displacement_method.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-01-30 - 1000.txt", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-06 - 0959.txt", "Logan, A First Course in the Finite Element Method, Ch. 2–3"]
---

# SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method

> [!abstract] Summary
> The finite element method splits a structure into simple elements joined at nodes, writes each element's force–displacement relation $\{F\}^e=[K]^e\{d\}^e$, and assembles them into one global system $\{F\}=[K]\{d\}$ by enforcing displacement compatibility and force equilibrium at shared nodes. The matrix displacement (direct stiffness) method does this for bars, where $k=EA/L$. Once enough displacements are constrained to stop rigid-body motion the system can be solved for the nodal displacements, and strains, stresses and reactions follow by back-substitution.

> [!summary]- Exam use: quick path
> - **Use it when:** a question gives a bar (or spring) structure and asks for element matrices, the assembled global matrix, boundary conditions or a displacement.
> - **Assumptions:** linear elastic bars carrying axial force only, small displacements, one degree of freedom per node along the bar axis.
> - **Method:** 1. Sketch and number the nodes and elements. 2. Write each $[K]^e=\frac{EA}{L}\begin{bmatrix}1&-1\\-1&1\end{bmatrix}$. 3. Add each element's entries into the global rows and columns of its DOF. 4. Put applied loads in $\{F\}$ and supports in $\{d\}$, and strike out the rows and columns of zero displacements. 5. Solve, then back-substitute for reactions and member stresses.
> - **Common mistakes:** placing an element block in the wrong rows and columns when the DOF numbering is not consecutive; trying to solve before any displacement is constrained (singular $[K]$, "zero pivot").
> - **Practise:** [[#Worked example: two bars clamped at both ends]] · [[SESA2029 FEA Worked Examples]]

Part B of the module, taught by Dr J. Yuan (formerly at Airbus and Imperial College, now in the Rolls-Royce University Technology Centre in computational engineering), moves from fluids to structures (2026-01-30 10:00, ll. 1–30). Aircraft structures deform in flight, which changes their aerodynamics too, so the two halves of the module meet in aeroelasticity.

FEA treats a structure as a network of springs. A single bar under axial load behaves exactly like a spring of stiffness $EA/L$. A real structure is too complicated to solve as one piece, but it can be cut into pieces that are each simple enough to describe by such a stiffness, and then put back together by insisting on two things at every joint: the pieces that meet there move together, and the forces they exert balance the load applied there. The bookkeeping that does this is matrix algebra, which is what makes the method programmable.

## 1. What FEA is and why aerospace uses it

The finite element method is a computer-based numerical method for approximate solutions of engineering problems defined by ordinary or partial differential equations (2026-01-30 10:00, ll. 71–100). Analytical solutions exist only for simple, idealised structures such as a uniform beam; aerospace structures are rarely like that, and increasingly use composites, metamaterials and topology-optimised shapes. The method divides the structure into elements, each with its own geometry and properties, and assembles them. An A350 wing, for example, has glass fibre in the leading edge, carbon-fibre panels and aluminium spars, which no closed-form solution handles (2026-02-06 09:59, ll. 171–185).

Courant proposed the method in 1943, and aerospace engineers developed it; the direct stiffness method of Turner, Clough, Martin and Topp at Boeing put it in matrix form for computer programming, which is why "direct stiffness method" and "matrix displacement method" (MDM) are used interchangeably (2026-02-06 09:59, ll. 21–35).

> [!warning] Lecture slip (2026-02-06 09:59, ll. 21–30)
> The slide and transcript date the direct stiffness paper to 1959 ("Turner, Croft and the top"). The paper by Turner, Clough, Martin and Topp appeared in 1956. Courant's 1943 paper was a mathematical one on equilibrium and vibration problems (its example was torsion), rather than an aerospace vibration analysis as the lecture implies.

FEA is used across the design cycle, from material properties through components such as ribs and panels to assemblies (2026-01-30 10:00, ll. 71–140). Once validated, a model predicts behaviour under many loading cases far more cheaply and quickly than testing, shows what happens inside the structure where measurements are hard, identifies weaknesses, propagates uncertainty in material properties for robust design, and supplies the material-, component- and assembly-level evidence that certification demands. The analysis types are structural (linear and nonlinear stress), thermal (temperature and thermal-stress distributions, critical in turbines above 1000 °C), and dynamic: modal analysis for natural frequencies and mode shapes, such as the nodal-diameter modes of a bladed disc, and transient analysis for forced response and vibration stress, which feeds fatigue life (ll. 141–190).

### The FEA procedure

Every analysis has three stages (2026-01-30 10:00, ll. 191–230). Pre-processing creates or imports the geometry (from SolidWorks or CATIA, say), defines material properties, discretises the geometry into a mesh with a chosen element type, and applies boundary conditions, both displacement constraints such as a clamped wing root and loads such as pressure. A badly chosen element type or mesh can give results unlike experiment, so the model must be checked by a convergence study and validated against tests. The solution stage solves the system of equations for the unknown nodal displacements. Post-processing turns displacements into strains and stresses, and checks, for example, that the maximum stress stays below yield.

Each element carries its own equation $\{F\}^e=[K]^e\{d\}^e$, where $\{F\}^e$ holds the forces at the element's nodes, $\{d\}^e$ the nodal displacements and $[K]^e$ is an $n\times n$ stiffness matrix (ll. 231–260). For an 8-node brick with three degrees of freedom (DOF) per node, $n=24$. Assembling the elements gives a global system whose number of equations equals the total number of DOF, possibly millions; more elements give more accuracy and more cost.

The size of a model is the number of nodes times the DOF per node, and it sets the computational cost, so estimate it before meshing (2026-02-06 09:59, ll. 146–160). Large models need techniques such as domain decomposition and high-performance computing. In the software, points that define the geometry are key points; once the mesh exists, the points where elements join are nodes.

### Assessment and the labs

Part B has twelve lectures over six weeks and three computer labs in weeks 2, 4 and 6: 1D springs and beams, a 2D plate with a hole (like a fuselage panel or wing rib), and a 3D wing in static and modal analysis (2026-01-30 10:00, ll. 41–70, 271–300; see [[SESA2029 C1 - ANSYS Mechanical APDL Scripting Fundamentals|C1]]–[[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)|C4]]). The FEA coursework, a 10-page lab report, is 30 % of the module, due Monday of week 8 (16 March). The one-hour exam is 40 % (20 % CFD, 20 % FEA): about 30 minutes for FEA, 25 marks over about eight questions, half on key concepts and terms and half on hand calculations with the methods of weeks 2 and 3. Two example sheets and a mock paper (week 6) support it.

## 2. The single-DOF bar

A bar of cross-section $A$, length $L$ and Young's modulus $E$ is fixed at one end and pulled by an axial force $F$ at the other (2026-02-06 09:59, ll. 51–95). A bar can deform and carry force only along its axis, which is what makes it the basic element of pin-jointed frames and space trusses. Three relations describe it:

$$
\sigma=\frac FA\quad\text{(equilibrium)},
\qquad
\varepsilon=\frac uL\quad\text{(compatibility)},
\qquad
\sigma=E\varepsilon\quad\text{(constitutive)}.
$$

Put the constitutive law into equilibrium:

$$
F=\sigma A=E\varepsilon A.
$$

Replace the strain by compatibility:

$$
F=\frac{EA}{L}u=ku,
\qquad
k=\frac{EA}{L}.
$$

The constant of proportionality between force and extension is the stiffness. Once $u$ is known, the strain $u/L$ and the stress $E\varepsilon$ follow. The same three ingredients, equilibrium, compatibility and a constitutive law, build every element in Part B.

## 3. The two-DOF bar element

Now let both ends move, as for a bar attached to supporting structure or a Formula 1 suspension link (ll. 96–145). The nodes $i$ and $j$ have axial displacements $u_i$ and $u_j$ and nodal forces $F_i$ and $F_j$. The extension is $u_j-u_i$, so the tension in the bar is

$$
F=k(u_j-u_i).
$$

Equilibrium of the bar, by Newton's third law, requires the nodal forces to be equal and opposite:

$$
F_i=-F,
\qquad
F_j=F.
$$

Substitute the tension:

$$
F_i=k u_i-k u_j,
\qquad
F_j=-k u_i+k u_j.
$$

In matrix form,

$$
\begin{Bmatrix}F_i\\F_j\end{Bmatrix}=\begin{bmatrix}k&-k\\-k&k\end{bmatrix}\begin{Bmatrix}u_i\\u_j\end{Bmatrix},
\qquad
\{F\}^e=[K]^e\{d\}^e .
$$

$\{F\}$ and $\{d\}$ are one-dimensional arrays and $[K]$ is two-dimensional, with size equal to the element's number of DOF: $2\times2$ for this bar, $4\times4$ for a two-node beam with a deflection and a rotation at each node ([[SESA2029 B5 - Euler-Bernoulli Beam Element|B5]]).

## 4. Assembling two bars

Two bars of the same length but different areas form a stepped bar, discretised as element 1 (nodes 1–2, stiffness $k_1$) and element 2 (nodes 2–3, $k_2$) (ll. 161–230). Each element has its own matrix; this freedom to give every element its own area, length and material is the point of the method. The model has three nodes with one DOF each, $\{d\}=\{u_1\ u_2\ u_3\}^T$, so the global matrix is $3\times3$.

Two principles are imposed. Compatibility: element 1's node $j$ and element 2's node $i$ are the same node and have the same displacement $u_2$. Each element's equations can then be written in terms of the three global DOF by padding with rows and columns of zeros:

$$
\begin{Bmatrix}F^{(1)}_i\\F^{(1)}_j\\0\end{Bmatrix}=\begin{bmatrix}k_1&-k_1&0\\-k_1&k_1&0\\0&0&0\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix},
\qquad
\begin{Bmatrix}0\\F^{(2)}_i\\F^{(2)}_j\end{Bmatrix}=\begin{bmatrix}0&0&0\\0&k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix}.
$$

Equilibrium: the external force at each node equals the sum of the element forces there, so at the shared node

$$
F_2=F^{(1)}_j+F^{(2)}_i .
$$

Adding the two padded equations therefore adds the matrices:

$$
\begin{Bmatrix}F_1\\F_2\\F_3\end{Bmatrix}=\begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_1\\u_2\\u_3\end{Bmatrix}.
$$

In practice the expansion is not written out: each element's entries are added into the global rows and columns of its DOF, and overlapping entries sum. The global matrix is square, symmetric and banded. Keep the DOF numbering consistent between the nodes and the matrix, or rows and columns end up in the wrong places (ll. 361–405; [[Global Stiffness Matrix Assembly]]).

Bars at an angle need the angle taken into account in the force equilibrium (ll. 231–235). The lecture does not develop it, but for a bar at angle $\theta$ with $c=\cos\theta$, $s=\sin\theta$ and two DOF $(u,v)$ per node, the extension is the displacement difference resolved along the bar,

$$
\delta=c(u_j-u_i)+s(v_j-v_i),
$$

the axial force $k\delta$ has components $ck\delta$ and $sk\delta$, and collecting terms gives

$$
[K]^e=\frac{EA}{L}\begin{bmatrix}c^2&cs&-c^2&-cs\\cs&s^2&-cs&-s^2\\-c^2&-cs&c^2&cs\\-cs&-s^2&cs&s^2\end{bmatrix},
$$

which reduces to the axial bar for $\theta=0$. Assembly is identical.

## 5. Boundary conditions and solution

The boundary conditions are of two kinds: the forces applied to the model, in $\{F\}$, and the displacement constraints, in $\{d\}$ (ll. 231–250). A clamped beam end has zero deflection and rotation; a simply supported end has zero deflection but can rotate. Getting them right matters more than anything else downstream: when a model is updated to match experiment, the boundary conditions are usually what needs changing, and they will be assessed in the exam. The unspecified displacements are the unknowns, and the model cannot be solved until enough displacements are constrained; otherwise $[K]$ is singular, the structure can move as a rigid body, and the software stops with a zero-pivot error ([[Boundary Conditions and Rigid Body Modes]]).

Take the stepped bar fixed at node 1 and loaded by $F$ at node 3 (ll. 251–290). The reaction at node 1 is not yet known and is left out of the force vector; it is recovered later:

$$
\begin{Bmatrix}R_1\\0\\F\end{Bmatrix}=\begin{bmatrix}k_1&-k_1&0\\-k_1&k_1+k_2&-k_2\\0&-k_2&k_2\end{bmatrix}\begin{Bmatrix}0\\u_2\\u_3\end{Bmatrix}.
$$

Every term multiplying $u_1=0$ vanishes, so for a zero displacement the corresponding row and column can be struck out:

$$
\begin{Bmatrix}0\\F\end{Bmatrix}=\begin{bmatrix}k_1+k_2&-k_2\\-k_2&k_2\end{bmatrix}\begin{Bmatrix}u_2\\u_3\end{Bmatrix}.
$$

Add the two equations:

$$
F=k_1u_2
\quad\Longrightarrow\quad
u_2=\frac F{k_1}.
$$

The second equation gives $u_3$:

$$
F=k_2(u_3-u_2)
\quad\Longrightarrow\quad
u_3=\frac F{k_1}+\frac F{k_2},
$$

springs in series, as expected. Back-substitution then gives the reaction from the struck-out first row, $R_1=-k_1u_2=-F$, and the member forces from each element equation, for example $F^{(2)}=k_2(u_3-u_2)=F$, with stress $F^{(e)}/A_e$.

The method is general (ll. 291–305): it applies to bars, beams, shear panels and solids, as long as the element matrices are known, and it can be programmed "without much in terms of the thinking". Every analysis repeats the same steps:

1. Form the element matrices.
2. Assemble the global matrix.
3. Apply the boundary conditions.
4. Solve for the displacement DOF.
5. Back-substitute for the nodal and reaction forces.
6. Apply element equilibrium to get element forces and stresses.

## Worked example: two bars clamped at both ends

This is example sheet 1's question, worked in the lecture (ll. 306–405). Bar 1 has area $2A$, bar 2 area $A$, both length $L$ and modulus $E$; both outer ends are clamped and an axial load $P$ acts at the junction.

The element stiffnesses are

$$
k_1=\frac{2AE}{L},
\qquad
k_2=\frac{AE}{L}.
$$

Assembled,

$$
\begin{Bmatrix}R_1\\P\\R_3\end{Bmatrix}=\frac{AE}{L}\begin{bmatrix}2&-2&0\\-2&3&-1\\0&-1&1\end{bmatrix}\begin{Bmatrix}0\\u_2\\0\end{Bmatrix}.
$$

The 3 in the middle is $2+1$, the contributions of both elements to node 2. With $u_1=u_3=0$, strike out rows and columns 1 and 3:

$$
P=\frac{3AE}{L}u_2
\quad\Longrightarrow\quad
u_2=\frac{PL}{3AE}.
$$

The lecture stops there; the back-substitution completes it. The reactions come from rows 1 and 3:

$$
R_1=-\frac{2AE}{L}u_2=-\frac{2P}{3},
\qquad
R_3=-\frac{AE}{L}u_2=-\frac P3 .
$$

They sum to $-P$, balancing the load. Bar 1 carries $k_1u_2=2P/3$ in tension, so $\sigma_1=(2P/3)/(2A)=P/(3A)$; bar 2 carries $P/3$ in compression, so $\sigma_2=-P/(3A)$. The stresses are equal in magnitude because both bars have the same strain magnitude $u_2/L$.

With $E=70$ GPa, $A=100$ mm², $L=0.5$ m and $P=10$ kN, a NumPy assembly and solve gives $u_2=0.238$ mm, $R_1=-6.67$ kN, $R_3=-3.33$ kN and $\sigma=\pm33.3$ MPa, matching the formulas.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous (Part A): [[SESA2029 A11 - CFD Errors, Verification, Validation and Mesh Quality]]
- Next: [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]]
- Concepts: [[Matrix Displacement Method]] · [[Global Stiffness Matrix Assembly]] · [[Boundary Conditions and Rigid Body Modes]]
- The energy route to the same matrices: [[SESA2029 B3 - Principle of Minimum Total Potential Energy]]
- In the lab: [[SESA2029 C2 - APDL Workflow - Cantilever Beam Loads (BEAM188)]]
- Solving the linear system: [[SESA2029 A3 - Iterative Solution of the Steady Heat Equation]]

## Sources

- FEA Lecture 3 slides, `Lecture_3_Matrix_displacement_method.pdf`, with transcripts `SESA2029 Lecture 2026-01-30 - 1000.txt` (introduction and assessment) and `SESA2029 Lecture 2026-02-06 - 0959.txt` (MDM) (Dr J. Yuan)
- Logan, *A First Course in the Finite Element Method*, Ch. 2–3
- Worked example checked with NumPy

## Self-study tasks

### Core

- [ ] Derive the $2\times2$ bar stiffness matrix from equilibrium, compatibility and the constitutive law (2026-02-06 09:59, ll. 51–145). → [[#2. The single-DOF bar]] · [[#3. The two-DOF bar element]]
- [ ] Example sheet 1, two-bar question: element matrices, assembly, boundary conditions, junction displacement ("kind of similar questions you will do during the exams", ll. 306–335). → [[#Worked example: two bars clamped at both ends]]
- [ ] The second MDM question on example sheet 1 (ll. 401–410). → [[SESA2029 FEA Worked Examples]]
- [ ] Lab 1: estimate the number of DOF in your model from the elements used (ll. 151–160). → [[#The FEA procedure]]

### Further practice

- [ ] Assemble a three-bar stepped bar with a load at each joint and recover every reaction and member stress (suggested, not lecturer-set). → [[#4. Assembling two bars]] · [[#5. Boundary conditions and solution]]
- [ ] Derive the inclined-bar stiffness matrix and check it for $\theta=90°$ (suggested, not lecturer-set). → [[#4. Assembling two bars]]

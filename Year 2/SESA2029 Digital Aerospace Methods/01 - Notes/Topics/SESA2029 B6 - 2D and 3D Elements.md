---
title: "SESA2029 B6 - 2D and 3D Elements"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 17
tags:
  - sesa2029
  - fea
  - element-types
aliases: ["2D elements", "3D elements", "Element selection", "Plane stress plane strain"]
date: 2026-09-24
status: complete
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
next_topics: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
key_concepts: ["[[Plane Stress and Plane Strain]]", "[[Plate, Shell and Membrane Elements]]", "[[Solid Elements (Tetrahedra and Hexahedra)]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# SESA2029 B6 - 2D and 3D Elements

> [!abstract] Summary
> Beams are a good first-order model, but they miss warping, local stress concentrations and cross-section deformation. Those need 2D or 3D elements.
>
> **2D, in-plane only** (2 translational DOF per node):
> - **plane stress**: thin, with $\sigma_z = 0$;
> - **plane strain**: thick or long, with $\varepsilon_z = 0$;
> - **membrane**: very thin film or fabric; in-plane load only, no bending.
>
> **2D with bending**:
> - **plates**: flat, carry transverse load in bending; 3 DOF per node $(w,\theta_x,\theta_y)$;
> - **shells**: may be curved, carry membrane + bending; up to 6 DOF per node. Use when $t\lesssim L/20$.
>
> **3D solids**: tets and hexes with 3 translational DOF per node, in linear or quadratic order. They are poor in bending unless you use several elements through the thickness, and unsuited to large thin structures.
>
> Choosing the element (category **and** order) is the first and most important FE decision.

## Key Concepts
- [[Plane Stress and Plane Strain]] · [[Plate, Shell and Membrane Elements]] · [[Solid Elements (Tetrahedra and Hexahedra)]] · [[h- and p-Refinement]]

---

## 1. Plane stress vs plane strain (L8)
Both use 2 DOF per node $(u,v)$ in the $x$–$y$ plane. General 3D Hooke's law, restricted to the plane:

**Plane stress** means $\sigma_z = \tau_{xz} = \tau_{yz} = 0$. It suits thin plates loaded in their plane: a plate with a hole, a fillet, skins and webs.

$$
\begin{Bmatrix}\sigma_x\\\sigma_y\\\tau_{xy}\end{Bmatrix} = \frac{E}{1-\nu^2}\begin{bmatrix}1&\nu&0\\\nu&1&0\\0&0&\frac{1-\nu}{2}\end{bmatrix}\begin{Bmatrix}\varepsilon_x\\\varepsilon_y\\\gamma_{xy}\end{Bmatrix},\qquad\varepsilon_z = -\frac{\nu}{1-\nu}(\varepsilon_x+\varepsilon_y)\neq0
$$

**Plane strain** means $\varepsilon_z = \gamma_{xz} = \gamma_{yz} = 0$. It suits long or thick bodies with uniform section: dams, tunnels, pipes under line load. It is rare in aerospace.

$$
\begin{Bmatrix}\sigma_x\\\sigma_y\\\tau_{xy}\end{Bmatrix} = \frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&\frac{1-2\nu}{2}\end{bmatrix}\begin{Bmatrix}\varepsilon_x\\\varepsilon_y\\\gamma_{xy}\end{Bmatrix},\qquad\sigma_z = \nu(\sigma_x+\sigma_y)\neq0
$$

Both are written $\{\sigma\} = [D]\{\varepsilon\}$. Picking the wrong option on the same element (ANSYS PLANE182/183 **KEYOPT(3)**) changes the answer. See [[Plane Stress and Plane Strain]].

| Element | Out-of-plane stress | Out-of-plane strain | Use | DOF/node |
|---|---|---|---|---|
| Plane stress | zero | non-zero | thin, in-plane loaded | 2 |
| Plane strain | non-zero | zero | long or thick | 2 |
| Membrane | zero | non-zero | very thin films, fabrics, deployable solar arrays | 2 (in-plane) |

## 2. In-plane element shapes (L8)
- **CST** (constant-strain triangle): 3 corner nodes, 6 DOF. Linear displacement gives **constant strain** in each element. It is stiff and needs a fine mesh.
- **LST** (linear-strain triangle): 6 nodes (corners + midsides), quadratic displacement. It is more accurate and copes better with distorted or sharp geometry.
- **Q4 / PQB** (plane quadrilateral bilinear): 4 nodes. Cheaper than the LST and fine for mildly varying stress.
- **Q8**: 8 nodes (quadratic), with curved edges allowed.

ANSYS equivalents:
- **PLANE182**: 4-node quad, which can degenerate to a 3-node triangle, though that is not recommended.
- **PLANE183**: 8-node quad, degenerating to a 6-node triangle (LST).
- **KEYOPT(3)**: 0 = plane stress, 2 = plane strain, 3 = plane stress **with thickness** (thickness given as a real constant).

> [!example] Linear vs quadratic (L9 benchmark)
> A tapered cantilever was modelled at the **same mesh density** with both elements:
>
> | Element | Mid-length (target 8333 psi) | Fixed end (target 7407 psi) |
> |---|---|---|
> | PLANE182 | 8164 (98.0%) | 7151 (96.5%) |
> | PLANE183 | 8364 (100.4%) | 7409 (100.0%) |
>
> Higher order means more accuracy for the same mesh, and more tolerance of distortion.

## 3. Plates and shells (L8)
- **Plate**: like a beam in 2D. It bends in **two directions** and twists, carries **transverse** load only, and **must be flat**. DOF per node: transverse $w$ and rotations $\theta_x$, $\theta_y$.
- **Shell**: may be **curved**, and carries **membrane + bending** (and twisting) together. The simplest shell superposes a membrane (plane-stress) element and a plate-bending element. Used for fuselages, tanks, roofs and wing skins.
  - **SHELL181**: 4 nodes, **6 DOF per node** (3 translations + 3 rotations). Linear, efficient for large models, good for mild curvature.
  - **SHELL281**: 8 nodes, quadratic. Better for curvature and bending; more expensive.
  - Both can be switched to membrane-only by KEYOPT.

**Rules for shells**:
- use them when the thickness satisfies $t\lesssim w/20$, where $w$ is the longest structural dimension;
- in-plane and bending stresses are accurate, but **through-thickness normal stress is not**;
- transverse shear is recovered from equilibrium;
- results can be requested at the TOP, MID or BOT surfaces (APDL `SHELL,TOP`).

The shell element's normal direction defines which face is "top". It matters for pressure loads.

See [[Plate, Shell and Membrane Elements]].

## 4. 3D solid elements (L8)
- **Hexahedra** (bricks): 8 nodes (linear) or 20 (quadratic). Accurate and efficient, but hard to mesh around complex shapes. They degenerate to wedges and prisms.
- **Tetrahedra**: 4 nodes (linear) or 10 (quadratic). They mesh anything automatically; the linear tet is stiff and inaccurate, so use the 10-node version.
- Every node has **3 translational DOF only**. Rotation is represented by the relative motion of several nodes.

**Limitations**:
- **Distortion**: meshing can distort elements, which ruins accuracy. Keep the **aspect ratio ≤ 3 (linear) or ≤ 5 (quadratic)**. Quadratic elements tolerate distortion better, so switch to them if the linear mesh fails checks.
- **Bending**: one solid element through the thickness cannot bend properly. Use **≥ 3 linear or ≥ 2 quadratic** elements through the thickness.
- So solids are **not ideal for large thin structures** (beams, thin pressure vessels, skins, solar panels).

> [!example] Thin-walled beam, same load (L8)
> Beam and shell models gave a peak stress of about 1014–1085 (consistent between them). A single-layer brick mesh gave ≈2000 and a tet mesh ≈2225: roughly double, and wrong.
>
> Right element, right answer. See [[Solid Elements (Tetrahedra and Hexahedra)]].

## 5. Summary of elements (L8)
| Category | Type | Nodes | DOF / capability |
|---|---|---|---|
| 1D | Truss (bar) | 2 | axial force only; any orientation in 3D |
| 1D | Beam | 2 (3) | 6 DOF/node in 3D: 3 translations + 3 rotations |
| 2D | Plane stress / strain | 3–4 (6–8) | 2 translational DOF/node in their plane |
| 2D | Membrane | 3–4 | any orientation; in-plane load only |
| 2D | Plate | 3–4 (8) | $w,\theta_x,\theta_y$; flat; bending |
| 2D | Shell | 3–8 | all translations and rotations except the drilling rotation about the normal (real codes add a drilling DOF) |
| 3D | Solid (tet, wedge, hex) | 4–20 | translations only |

## Links
- Parent: [[SESA2029 Digital Aerospace Methods Hub]] · Previous: [[SESA2029 B5 - Euler-Bernoulli Beam Element]] · Next: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- APDL: PLANE182/183 in [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]] · SHELL181/281 in [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]
- The CFD cell-shape equivalents: [[Structured, Unstructured and Hybrid Grids]]

## Sources
- FEA Lecture 8, `02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf`; Lecture 9 p. 10 (PLANE182/183 benchmark); transcript `FEA.txt`
- ANSYS Mechanical APDL Element Reference (PLANE182, PLANE183, SHELL181, SHELL281)

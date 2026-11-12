---
title: "SESA2029 B6 - 2D and 3D Elements"
module: "SESA2029 Digital Aerospace Methods"
type: topic
stream: "Part B: Finite Element Analysis"
order: 17
tags: [sesa2029, fea, element-types]
aliases: ["2D elements", "3D elements", "Element selection", "Plane stress plane strain", "FEA Lecture 8"]
date: 2026-10-30
status: lectured
coverage: "FEA week 4 (2026-02-20 11:03)"
parent: ["[[SESA2029 Digital Aerospace Methods Hub]]"]
prerequisites: ["[[SESA2029 B5 - Euler-Bernoulli Beam Element]]"]
next_topics: ["[[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]"]
key_concepts: ["[[Plane Stress and Plane Strain]]", "[[Plate, Shell and Membrane Elements]]", "[[Solid Elements (Tetrahedra and Hexahedra)]]", "[[h- and p-Refinement]]"]
tutorial_sheets: ["[[SESA2029 FEA Worked Examples]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf", "02 - Sources/Lectures/SESA2029 Lecture 2026-02-20 - 1103.txt", "ANSYS Mechanical APDL Element Reference (PLANE182, PLANE183, SHELL181, SHELL281)"]
---

# SESA2029 B6 - 2D and 3D Elements

> [!abstract] Summary
> Beams are a good first approximation for slender structures but cannot show warping, local stress concentrations or cross-section deformation, so 2D and 3D elements are needed. In-plane 2D elements (plane stress for thin parts, plane strain for long thick ones, membranes for films) have two translations per node; plates add bending of flat sheets; shells combine membrane and bending action on curved surfaces with up to six DOF per node and are the usual choice for thin aerospace structures. Solid tetrahedra and hexahedra have only translations, need several elements through the thickness to bend correctly, and are not suited to large thin structures, so choosing the element type and order is the first decision in any FE model.

> [!summary]- Exam use: quick path
> - **Use it when:** asked which element to use for a structure, to distinguish plane stress from plane strain, or to explain why solids are poor for thin parts.
> - **Assumptions:** linear elastic, isotropic; plane stress means $\sigma_z=\tau_{xz}=\tau_{yz}=0$, plane strain means $\varepsilon_z=\gamma_{xz}=\gamma_{yz}=0$.
> - **Method:** 1. Is it slender? Beam. 2. Thin and loaded in its plane? Plane stress (or membrane if it cannot bend). 3. Thin and bending, flat or curved? Plate or shell; shells if $t\lesssim L/20$. 4. Thick or complex 3D? Solids, quadratic if the mesh distorts. 5. Check the solid aspect ratio and the elements through the thickness.
> - **Common mistakes:** selecting plane strain (KEYOPT(3)) for a thin plate; one layer of linear solids through a thin wall.
> - **Practise:** [[#Worked example: the same strain under plane stress and plane strain]]

Choosing the element type is the practical decision in any FE model (2026-02-20 11:03, ll. 1–20). Aerospace structures are dominated by beams and shells because they are thin-walled; nuclear and civil structures can afford thick sections because weight matters less.

An element can only deform in the ways its nodes allow. A beam treats each cross-section as rigid, so it cannot show a section distorting or stress piling up round a hole; in lab 2 the stress concentration changes with the hole's position, which no beam could capture (ll. 11–25). A sheet of paper resists being stretched in its own plane but bends easily, so an element for thin sheets needs separate stiffness for stretching and for bending. A solid block element has no notion of bending at all and must build it out of several layers of nodes moving relative to each other.

## 1. Plane stress and plane strain

In-plane 2D elements describe position with two coordinates, have two translational DOF per node, and are connected at common nodes and edges; lab 2's plate with a hole uses PLANE182 (ll. 31–45). The same element offers two assumptions, chosen by KEYOPT(3), and the wrong one gives wrong results ([[Plane Stress and Plane Strain]]).

Plane stress applies to thin bodies loaded in their own plane, such as wing skins, fuselage panels and the plate with a hole: the normal and shear stresses perpendicular to the plane are zero (ll. 46–70),

$$
\sigma_z=\tau_{xz}=\tau_{yz}=0 .
$$

Hooke's law for the remaining components is

$$
\varepsilon_x=\frac{\sigma_x-\nu\sigma_y}{E},
\qquad
\varepsilon_y=\frac{\sigma_y-\nu\sigma_x}{E},
\qquad
\gamma_{xy}=\frac{2(1+\nu)}{E}\tau_{xy}.
$$

Multiply the second by $\nu$ and add it to the first:

$$
\varepsilon_x+\nu\varepsilon_y=\frac{(1-\nu^2)\sigma_x}{E}
\quad\Longrightarrow\quad
\sigma_x=\frac{E}{1-\nu^2}(\varepsilon_x+\nu\varepsilon_y),
$$

and similarly for $\sigma_y$, so

$$
\begin{Bmatrix}\sigma_x\\\sigma_y\\\tau_{xy}\end{Bmatrix}=\frac{E}{1-\nu^2}\begin{bmatrix}1&\nu&0\\\nu&1&0\\0&0&\frac{1-\nu}{2}\end{bmatrix}\begin{Bmatrix}\varepsilon_x\\\varepsilon_y\\\gamma_{xy}\end{Bmatrix}.
$$

The through-thickness strain is not zero; from $\varepsilon_z=-\nu(\sigma_x+\sigma_y)/E$,

$$
\varepsilon_z=-\frac{\nu}{1-\nu}(\varepsilon_x+\varepsilon_y),
$$

the geometrical relation that eliminates it.

Plane strain applies to long or thick bodies of uniform section loaded uniformly along their length, such as a dam or a tunnel: the strains perpendicular to the plane are zero (ll. 71–95),

$$
\varepsilon_z=\gamma_{xz}=\gamma_{yz}=0 .
$$

Setting $\varepsilon_z=(\sigma_z-\nu\sigma_x-\nu\sigma_y)/E=0$ gives the out-of-plane stress,

$$
\sigma_z=\nu(\sigma_x+\sigma_y)\neq0 .
$$

Substitute it into $\varepsilon_x=(\sigma_x-\nu\sigma_y-\nu\sigma_z)/E$:

$$
E\varepsilon_x=\sigma_x-\nu\sigma_y-\nu^2\sigma_x-\nu^2\sigma_y=(1-\nu^2)\sigma_x-\nu(1+\nu)\sigma_y=(1+\nu)\left[(1-\nu)\sigma_x-\nu\sigma_y\right],
$$

and likewise $E\varepsilon_y=(1+\nu)\left[(1-\nu)\sigma_y-\nu\sigma_x\right]$. In matrix form,

$$
\frac{E}{1+\nu}\begin{Bmatrix}\varepsilon_x\\\varepsilon_y\end{Bmatrix}=\begin{bmatrix}1-\nu&-\nu\\-\nu&1-\nu\end{bmatrix}\begin{Bmatrix}\sigma_x\\\sigma_y\end{Bmatrix}.
$$

The $2\times2$ matrix has determinant $(1-\nu)^2-\nu^2=1-2\nu$, so its inverse is $\frac{1}{1-2\nu}\begin{bmatrix}1-\nu&\nu\\\nu&1-\nu\end{bmatrix}$. The shear relation $\tau_{xy}=G\gamma_{xy}$ with $G=E/2(1+\nu)$ is unchanged, and $\tfrac{E}{2(1+\nu)}=\tfrac{E}{(1+\nu)(1-2\nu)}\cdot\tfrac{1-2\nu}{2}$. Together,

$$
\begin{Bmatrix}\sigma_x\\\sigma_y\\\tau_{xy}\end{Bmatrix}=\frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&\frac{1-2\nu}{2}\end{bmatrix}\begin{Bmatrix}\varepsilon_x\\\varepsilon_y\\\gamma_{xy}\end{Bmatrix}.
$$

Aerospace examples are rare; a very thick engine component might qualify (ll. 86–95).

## 2. Membranes and in-plane element shapes

A membrane element is for very thin structures such as fabrics and films, for example the deployable solar panels of a spacecraft (ll. 96–110). It carries in-plane force only: tension, compression and in-plane shear, but no bending and no transverse shear. In ANSYS it is a KEYOPT option of the SHELL181 element rather than a separate element.

| Element | Out-of-plane stress | Out-of-plane strain | Typical use |
|---|---|---|---|
| Plane stress | zero | non-zero | thin, loaded in plane |
| Plane strain | non-zero | zero | long or thick |
| Membrane | zero | non-zero | very thin films and fabrics, in 3D space |

In-plane elements come in several shapes (ll. 106–125). The constant strain triangle (CST) has three corner nodes with two DOF each; its displacement is linear, so its strain is constant. The linear strain triangle (LST) adds mid-side nodes, six in all, and handles sharp geometry and distortion better. The four-node plane quadrilateral bilinear (PQB) element has fewer nodes than the LST, so it is cheaper but less able to follow distortion. ANSYS implements these in PLANE182 (four-node, degenerating to a triangle) and PLANE183 (eight-node, degenerating to a six-node triangle).

## 3. Plates and shells

Plate and shell elements resist bending and out-of-plane motion (ll. 121–165; [[Plate, Shell and Membrane Elements]]). A plate element is like a beam in two dimensions: it bends in two directions and twists, with three DOF per node, the transverse displacement $w$ and the rotations $\theta_x$ and $\theta_y$. It carries transverse load only, not in-plane load, and it must be flat.

A shell element can be curved and carries both membrane and bending forces. The simplest shell combines a membrane (plane-stress) element with a plate-bending element, giving five or six DOF per node so that every motion can be represented. Shells are the most widely used of all elements, for roofs, tanks, fuselages and lab 3's wing, at a higher cost than plates. SHELL181 is a four-node shell with six DOF per node, three translations and three rotations, when the "bending and membrane" option is selected; an eight-node version (SHELL281) uses higher-order interpolation (ll. 151–165).

Shells are recommended when the thickness is at most about a twentieth of the longest dimension, true of skins, fuselages and many rib plates (ll. 166–180). They give accurate in-plane and bending stresses, and transverse shear is recovered from equilibrium in post-processing, but the through-thickness normal stress is not accurate; if that matters, use solids.

## 4. Solid elements

The two basic solids are the hexahedron (hex or brick), with eight corner nodes and higher-order versions with more, and the tetrahedron (tet), with four corner nodes and higher-order versions (ll. 181–200; [[Solid Elements (Tetrahedra and Hexahedra)]]). Bricks can degenerate into wedges for arbitrary geometry, but tets are more flexible and mesh irregular shapes with sharp changes most easily, as in the B2 bracket. Every element family comes in two orders: lower-order elements use linear polynomials and higher-order ones quadratic, with mid-side nodes and more accurate stress recovery, as with two- and three-node beams.

Every node of a solid has three translational DOF and no rotations (ll. 196–215). A solid can rotate, but only through the relative motion of several nodes: no node carries a rotation of its own, so a rotation cannot be applied or read at a single node.

Two limitations follow (ll. 211–250). Meshing can distort solid elements, and too much distortion ruins accuracy; ANSYS warns when it happens. The aspect ratio, longest over shortest side, should be at most 3 for linear elements and at most 5 for quadratic ones, so if a linear mesh fails the checks, switch to quadratic elements, accepting more DOF for more tolerance. And a single solid element does not capture bending: at least three linear or two quadratic elements are needed through the thickness. Solids are therefore not ideal for large thin structures: beams, thin pressure vessels, aircraft skins and fuselages, solar panels.

![[dam_solid_bending_layers.png|820]]

The figure shows why, with a small plane-stress code standing in for linear bricks: a thin cantilever ($L/h=10$, $\nu=0.3$, tip shear load) meshed with fully integrated four-node quadrilaterals. A linear element cannot take up the curved shape of a bent fibre, so it bends by shearing instead, and that spurious shear makes it too stiff. With one element through the thickness and 20 along the length the tip deflection is only 84 % of the beam-theory value; three layers raise it to 90 %, after which more layers barely help, and the rest of the deficit only goes as the elements are shortened along the beam (97 % with 40 along and eight through). Linear solids need several layers and short elements, and even then they converge slowly in bending, which is the point of the three-layer rule.

A thin cantilever modelled four ways in ANSYS makes the same point from another angle (slide 29): the solid models disagree with the beam and shell models, which agree with each other. The maximum stresses on the contour legends are 1875 for beam elements and 1814 for shells, which agree within about 3 %, but 2113 for bricks and 2125 for tetrahedra, 13 to 17 % higher, with the tet model visibly misbehaving. For a very thin structure the beam or shell answer is the one to trust, subject as always to a convergence study.

## 5. Summary of element types

| Category | Type | Nodes | DOF and capability |
|---|---|---|---|
| 1D | Truss (bar) | 2 | any orientation in 3D; axial force only |
| 1D | Beam | 2 | six DOF per node in 3D: three translations, three rotations |
| 2D | Plane stress or strain | 3 or 4 | two translations per node, in their plane |
| 2D | Membrane | 3 or 4 | any orientation in 3D; in-plane load only |
| 2D | Plate | 3, 4 or 8 | $w$, $\theta_x$, $\theta_y$; flat; bending |
| 2D | Shell | 3 to 8 | all translations and rotations except rotation about the normal |
| 3D | Solid (tet, wedge, hex) | 4 to 20 | translations only |

See [[SESA2029 B7 - Meshing, Convergence and Mesh Checks|B7]] for meshing strategies and [[SESA2029 B8 - Modal Analysis|B8]] for modal analysis (ll. 251–268).

## Worked examples

### Worked example: the same strain under plane stress and plane strain

*(Suggested, not lecturer-set.)* The KEYOPT(3) choice changes the stresses substantially for the same strain. An aluminium region ($E=70$ GPa, $\nu=0.33$) has $\varepsilon_x=10^{-3}$, $\varepsilon_y=0$, $\gamma_{xy}=0$.

Under plane stress,

$$
\sigma_x=\frac{E}{1-\nu^2}\varepsilon_x=\frac{70\,000}{1-0.1089}\times10^{-3}=78.6\text{ MPa},
\qquad
\sigma_y=\nu\sigma_x=25.9\text{ MPa},
$$

and the plate thins: $\varepsilon_z=-\frac{0.33}{0.67}\times10^{-3}=-4.9\times10^{-4}$.

Under plane strain,

$$
\sigma_x=\frac{E(1-\nu)}{(1+\nu)(1-2\nu)}\varepsilon_x=\frac{70\,000\times0.67}{1.33\times0.34}\times10^{-3}=103.7\text{ MPa},
$$

$$
\sigma_y=\frac{E\nu}{(1+\nu)(1-2\nu)}\varepsilon_x=51.1\text{ MPa},
\qquad
\sigma_z=\nu(\sigma_x+\sigma_y)=51.1\text{ MPa}.
$$

Preventing the out-of-plane strain makes the material 32 % stiffer in $x$ and adds a through-thickness stress, so modelling a thin plate as plane strain overestimates its stiffness and changes every stress.

With equal biaxial strain, $\varepsilon_x=\varepsilon_y=10^{-3}$, the difference grows. Plane stress gives

$$
\sigma_x=\sigma_y=\frac{E}{1-\nu^2}(1+\nu)\varepsilon_x=\frac{E}{1-\nu}\varepsilon_x=\frac{70\,000}{0.67}\times10^{-3}=104.5\ \mathrm{MPa},
\qquad
\varepsilon_z=-\frac{0.33}{0.67}\times2\times10^{-3}=-9.9\times10^{-4},
$$

while plane strain gives

$$
\sigma_x=\sigma_y=\frac{E(1-\nu+\nu)}{(1+\nu)(1-2\nu)}\varepsilon_x=\frac{70\,000}{1.33\times0.34}\times10^{-3}=154.8\ \mathrm{MPa},
\qquad
\sigma_z=\nu(\sigma_x+\sigma_y)=102.2\ \mathrm{MPa}.
$$

The plane-strain stresses are 48 % higher.

> [!check] Plane strain stiffens without limit as $\nu\to\tfrac12$
> The plane-strain factor $(1+\nu)(1-2\nu)$ goes to zero as $\nu\to\tfrac12$, the incompressible limit, so the biaxial stiffness grows without bound: a material that cannot change volume and cannot strain out of plane cannot change its in-plane area either, so equal biaxial strain is impossible (only strains with $\varepsilon_x+\varepsilon_y=0$, such as shear, remain). The plane-stress factor $1-\nu^2$ stays finite. For $\nu=0$ the two matrices coincide, since there is then no Poisson coupling to the third direction.

## Links

- Parent: [[SESA2029 Digital Aerospace Methods Hub]]
- Previous: [[SESA2029 B5 - Euler-Bernoulli Beam Element]]
- Next: [[SESA2029 B7 - Meshing, Convergence and Mesh Checks]]
- Concepts: [[Plane Stress and Plane Strain]] · [[Plate, Shell and Membrane Elements]] · [[Solid Elements (Tetrahedra and Hexahedra)]] · [[h- and p-Refinement]]
- In the labs: [[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]] · [[SESA2029 C4 - APDL Workflow - Shell Wing Static and Modal (SHELL181 and SHELL281)]]
- The CFD cell-shape equivalents: [[Structured, Unstructured and Hybrid Grids]]

## Sources

- FEA Lecture 8 slides, `Lecture_8_ 2D_3D_elements_final.pdf` (thin-cantilever values read from the slide-29 legends), with transcript `SESA2029 Lecture 2026-02-20 - 1103.txt` (Dr J. Yuan)
- ANSYS Mechanical APDL Element Reference
- Worked example computed with NumPy. Figures: `01 - Notes/Figures/generate_dam_b6_figures.py` (own Q4 plane-stress solver)

## Self-study tasks

### Core

- [ ] Explain plane stress and plane strain, with an example of each, and write their stress–strain matrices (2026-02-20 11:03, ll. 46–95). → [[#1. Plane stress and plane strain]]
- [ ] Compare plate and shell elements and state when shells are appropriate (ll. 121–180). → [[#3. Plates and shells]]
- [ ] Explain the two limitations of solid elements (ll. 211–250). → [[#4. Solid elements]]
- [ ] Continue the lab 2 assignment and the example sheets (ll. 261–268). → [[SESA2029 FEA Worked Examples]]

### Further practice

- [ ] Derive the plane-strain matrix from 3D Hooke's law. → [[#1. Plane stress and plane strain]]
- [ ] Repeat the worked example with $\varepsilon_x=\varepsilon_y=10^{-3}$ (suggested, not lecturer-set). → [[#Worked example: the same strain under plane stress and plane strain]]

## Transcript and slide slips

> [!warning] Lecture slip (2026-02-20 11:03, ll. 51–55)
> Where: [[#1. Plane stress and plane strain]].
>
> Introducing plane strain, the dam and tunnel are described as "very thin". Plane strain is the assumption for long or thick bodies, where the material along the length prevents out-of-plane strain; thin bodies are plane stress.

> [!warning] Lecture slip (2026-02-20 11:03, ll. 241–250)
> Where: [[#4. Solid elements]].
>
> The values are read out as 1085 and 1014 for the beam and shell, and about 2000 and 2025 for the solids, which would make the solids double. The slide's legends give 1875 (beam), 1814 (shell), 2113 (brick) and 2125 (tet). The conclusion, that solids are unreliable for thin structures, stands; the discrepancy is smaller than stated.

> [!warning] Slide slip: node counts of solids (Lecture 8 slide 30)
> Where: [[#5. Summary of element types]].
>
> The summary table lists 8 to 20 nodes for solid elements. A linear tetrahedron has 4 nodes and a linear wedge 6, so the range is 4 to 20, as in the table above.

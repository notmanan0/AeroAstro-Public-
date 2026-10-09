---
title: "Plane Stress and Plane Strain"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["plane stress", "plane strain", "D matrix", "constitutive matrix", "KEYOPT(3)"]
tags: [sesa2029, concept, fea, element-types]
status: complete
parent_lectures: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
related_concepts: ["[[Plate, Shell and Membrane Elements]]", "[[Solid Elements (Tetrahedra and Hexahedra)]]", "[[Von Mises and Tresca Yield Criteria]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Plane Stress and Plane Strain

## Definition

> [!note] Definition
> 2D idealisations with 2 in-plane DOF per node:
> - **plane stress**: $\sigma_z = \tau_{xz} = \tau_{yz} = 0$, for thin bodies loaded in-plane;
> - **plane strain**: $\varepsilon_z = \gamma_{xz} = \gamma_{yz} = 0$, for long or thick bodies with uniform section.

## Explanation

$$\text{Plane stress: }[D] = \frac{E}{1-\nu^2}\begin{bmatrix}1&\nu&0\\\nu&1&0\\0&0&\frac{1-\nu}{2}\end{bmatrix},\qquad\varepsilon_z = -\frac{\nu}{1-\nu}(\varepsilon_x+\varepsilon_y)$$

$$\text{Plane strain: }[D] = \frac{E}{(1+\nu)(1-2\nu)}\begin{bmatrix}1-\nu&\nu&0\\\nu&1-\nu&0\\0&0&\frac{1-2\nu}{2}\end{bmatrix},\qquad\sigma_z = \nu(\sigma_x+\sigma_y)$$

- **Plane stress** suits skins, webs, plates with holes and fillets: most aerospace 2D problems.
- **Plane strain** suits dams, tunnels and long pipes under line load, and is rare in aerospace.
- **Membrane**: very thin (films, fabrics, deployable arrays). In-plane load only; zero out-of-plane stress.
- **ANSYS PLANE182/183 KEYOPT(3)**: 0 = plane stress, 2 = plane strain, 3 = plane stress with thickness (via `R`). Choosing wrongly changes the stresses.
- **Element shapes**: CST (3-node, constant strain), LST (6-node), Q4 (bilinear), Q8 (quadratic).

## Examples

- A plate with a hole in tension is plane stress: PLANE182 with KEYOPT(3)=3 and a 10 mm thickness ([[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]]).

## Related

- Parent lectures: [[SESA2029 B6 - 2D and 3D Elements]]
- Related concepts: [[Plate, Shell and Membrane Elements]] · [[Solid Elements (Tetrahedra and Hexahedra)]] · [[Von Mises and Tresca Yield Criteria]]

**Related (SESA2028 materials):** [[Plane Strain Constraint]] (why $K_{Ic}$ is a plane-strain value; shear lips)

## Sources

- 02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf
- 02 - Sources/FEM Lectures/FEA.txt

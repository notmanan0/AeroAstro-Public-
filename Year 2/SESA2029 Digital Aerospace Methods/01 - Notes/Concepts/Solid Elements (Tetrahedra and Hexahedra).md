---
title: "Solid Elements (Tetrahedra and Hexahedra)"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["solid elements", "tetrahedral elements", "hexahedral elements", "brick elements", "tet10", "hex8", "hex20"]
tags: [sesa2029, concept, fea, element-types]
status: lectured
parent_lectures: ["[[SESA2029 B6 - 2D and 3D Elements]]"]
related_concepts: ["[[Plate, Shell and Membrane Elements]]", "[[FE Element Quality Checks]]", "[[h- and p-Refinement]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_8_ 2D_3D_elements_final.pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Solid Elements (Tetrahedra and Hexahedra)

Solid elements are the 3D continuum elements of FE analysis, tetrahedra and hexahedra (with wedges and pyramids between them), whose nodes carry only translations.

3D continuum elements with 3 translational DOF per node and no rotations:
- tetrahedra: 4 nodes linear, 10 quadratic;
- hexahedra (bricks): 8 nodes linear, 20 quadratic;
- degenerate wedges and prisms.

- Tets mesh arbitrary complex geometry automatically (e.g. brackets). Always prefer the 10-node version, because linear tets are overly stiff.
- Hexes are more accurate per DOF but hard to generate around complex shapes.
- Distortion limits: aspect ratio ≤ 3 (linear), ≤ 5 (quadratic). Angles must not approach 0° or 180°.
- Bending: at least 3 linear or 2 quadratic elements through the thickness. Rotations come from the relative motion of nodes, not from nodal rotation DOF.
- They are unsuitable for large thin structures (skins, thin pressure vessels, beams), where shells and beams are both cheaper and more accurate.
- Use solids when the through-thickness stress matters, or for chunky parts (lugs, fittings, nuclear or civil sections).

- Thin cantilever, same load (FEA Lecture 8, slide 29): beam and shell models give contour maxima of 1875 and 1814, bricks 2113 and tetrahedra 2125, 13 to 17 % higher; the lecture read the values as about 1000 and 2000 ([[SESA2029 B6 - 2D and 3D Elements]]).

## Related

- Parent lectures: [[SESA2029 B6 - 2D and 3D Elements]]
- Related concepts: [[Plate, Shell and Membrane Elements]] · [[FE Element Quality Checks]] · [[h- and p-Refinement]]

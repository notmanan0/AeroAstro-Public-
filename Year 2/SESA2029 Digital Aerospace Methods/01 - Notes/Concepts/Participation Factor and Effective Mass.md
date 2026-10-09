---
title: "Participation Factor and Effective Mass"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["participation factor", "effective mass", "modal effective mass", "mass participation"]
tags: [sesa2029, concept, fea, modal-analysis]
status: complete
parent_lectures: ["[[SESA2029 B8 - Modal Analysis]]"]
related_concepts: ["[[Natural Frequencies and Mode Shapes]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Participation Factor and Effective Mass

## Definition

> [!note] Definition
>
> $$\gamma_i = \{\phi\}_i^T[M]\{D\},\qquad M_{\mathrm{eff},i} = \frac{\gamma_i^2}{\{\phi\}_i^T[M]\{\phi\}_i}\;(= \gamma_i^2\text{ if mass-normalised})$$
>
> $\{D\}$ is a unit displacement (or rotation) in one global direction. $\gamma_i$ measures how strongly mode $i$ responds to excitation in that direction.

## Explanation

- A large $\gamma_i$ or $M_{\mathrm{eff},i}$ means the mode is readily excited by base motion or forces in that direction.
- $\sum_iM_{\mathrm{eff},i}$ → total mass as modes are added. **Extract modes until the cumulative effective mass exceeds about 90% of the total**: a practical criterion for "enough modes".
- **Design use**:
  - spacecraft: reduce the participation of modes excited by launch or base loads to improve stability;
  - aero-engines: reduce the participation of noise-radiating modes;
  - change the geometry, BCs or mass distribution accordingly.
- ANSYS prints a participation-factor table per direction (frequency, factor, effective mass, cumulative ratio).

## Examples

- 2-DOF ($m_1 = 2$ kg, $m_2 = 1$ kg): $\gamma = \{1.7157,\,-0.2379\}$, so $M_{\mathrm{eff}} = \{2.9436,\,0.0566\}$ kg, summing to 3 kg. Mode 1 carries 98% ([[SESA2029 FEA Worked Examples]]).

## Related

- Parent lectures: [[SESA2029 B8 - Modal Analysis]]
- Related concepts: [[Natural Frequencies and Mode Shapes]]

## Sources

- 02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt

---
title: "Natural Frequencies and Mode Shapes"
module: "SESA2029 Digital Aerospace Methods"
type: concept
stream: "Part B: Finite Element Analysis"
aliases: ["natural frequency", "mode shape", "eigenvalue problem", "modal analysis", "mass normalisation"]
tags: [sesa2029, concept, fea, modal-analysis]
status: complete
parent_lectures: ["[[SESA2029 B8 - Modal Analysis]]"]
related_concepts: ["[[Participation Factor and Effective Mass]]", "[[Damping Ratio and Natural Frequency]]", "[[Characteristic Equation and Eigenvalues]]"]
sources: ["02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf", "02 - Sources/FEM Lectures/FEA.txt"]
---

# Natural Frequencies and Mode Shapes

## Definition

> [!note] Definition
> For a linear undamped structure, free vibration $[M]\{\ddot u\}+[K]\{u\} = 0$ with $\{u\} = \{\phi\}\sin(\omega t+\theta)$ gives
>
> $$([K]-\omega_i^2[M])\{\phi\}_i = 0,\qquad f_i = \frac{\omega_i}{2\pi}$$
>
> The eigenvalues $\omega_i^2$ give the natural frequencies. The eigenvectors $\{\phi\}_i$ are the mode shapes.

## Explanation

- $n$ DOF give $n$ modes. The first few (default 6) usually dominate the response.
- **Normalisation**: mass-normalised ($\{\phi\}_i^T[M]\{\phi\}_i = 1$, what ANSYS reports) or unit-max. Only the **shape** is meaningful: modal displacements and stresses are relative.
- **Dependence**: $f\propto\sqrt{K/M}$. Stiffer structures and clamped (vs simply supported) BCs give higher frequencies; more mass gives lower ones. The first-mode estimate is $\omega_0\approx\sqrt{k/m}$.
- **Resonance**: excitation near $f_i$ amplifies the response. This affects fatigue, noise, flutter (mode coalescence) and rotor critical speeds.
- **Needs density**: without `MP,DENS`, $[M] = 0$ and there are no modes.
- **Validation**: hammer or shaker tests give FRF peaks and experimental mode shapes. Target frequencies within about 5% and **MAC** > about 0.8.

## Examples

- Flexible research wing: 4.2 Hz (1st bending), 28.5 Hz (2nd bending), 40.7 Hz (1st torsion), 82.3 Hz (3rd bending).
- 2-DOF system: 4.78 Hz (in phase) and 12.43 Hz (out of phase).

![[dam_modal_2dof.png|500]]

## Related

- Parent lectures: [[SESA2029 B8 - Modal Analysis]]
- Related concepts: [[Participation Factor and Effective Mass]] · [[Damping Ratio and Natural Frequency]] · [[Characteristic Equation and Eigenvalues]]
- SDOF theory: [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]

## Year 1 foundation
- Single-DOF natural frequency $\sqrt{k/m}$ and equivalent stiffness: [[FEEG1002 D6 - Single Degree of Freedom Vibration]].

## Sources

- 02 - Sources/FEM Lectures/Lecture_10_Modal_Analysis_2_final(1).pdf
- 02 - Sources/FEM Lectures/FEA.txt

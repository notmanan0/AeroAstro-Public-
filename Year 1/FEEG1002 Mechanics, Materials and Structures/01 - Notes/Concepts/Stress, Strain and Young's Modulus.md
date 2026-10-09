---
title: "Stress, Strain and Young's Modulus"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part A: Statics 1"
aliases: ["engineering stress", "engineering strain", "Hooke's law 1D", "Poisson's ratio", "shear modulus", "axial stiffness"]
tags: [feeg1002, concept, statics, stress, strain, hookes-law]
status: complete
parent_lectures: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
related_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Stress Concentration Factor and Factor of Safety]]", "[[Generalised Hooke's Law]]"]
sources: []
---

# Stress, Strain and Young's Modulus

## Definition

> [!note] Definition
> $$\sigma = \frac{F}{A},\quad \tau = \frac{F_s}{A},\quad \varepsilon = \frac{\Delta L}{L_0},\quad \gamma = \frac{\Delta S}{H_0}\approx\varphi$$
> For a linear elastic material in **uniaxial** stress: $\sigma = E\varepsilon$, $\varepsilon_{lat} = -\nu\varepsilon$ and $\tau = G\gamma$, with $G = \dfrac{E}{2(1+\nu)}$.

## Explanation

- Stress normalises force by area, so a failure criterion ($\sigma\le\sigma_y/K_{SF}$) becomes independent of part size. Strain normalises deformation, so it is independent of length.
- **A bar is a spring**: $F = \dfrac{EA}{L}\Delta L$. The axial stiffness $k = EA/L$ carries straight into truss deformation, bolt preload and FEA bar elements.
- $E$, $\nu$ and $G$ are material properties; $A$ and $L$ are geometry. Stiffness needs both.
- **Sign convention**: tension is positive.
- **Limits**: the uniaxial Hooke's law ignores the Poisson coupling of multiaxial stress. In 2D and 3D use [[Generalised Hooke's Law]].
- **Stress is local**: holes and notches raise it by $K_T$ ([[Stress Concentration Factor and Factor of Safety]]).

## Examples

- Bolt preload (Tutorial 1 Q3): 4000 N in an M6 bolt 350 mm long gives $\Delta L = 0.237$ mm, about ½ turn.
- Double shear pin: $\tau = (F/2)/(\pi d^2/4)$.
- Two bars in parallel (Tutorial 1 extra Q3): $F = 2(EA/L)D$.

## Related

- Topic notes: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]
- Concepts: [[Free Body Diagram and Equilibrium]] · [[Stress Concentration Factor and Factor of Safety]] · [[Generalised Hooke's Law]]
- Year 2: [[Strain Energy]] $U = F^2L/2EA$ ([[SESA2028 S7 - Strain Energy and Conservation of Energy]]) · bar element stiffness in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] · material properties in [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]

## Sources

- Statics 1 Lecture 2a–b

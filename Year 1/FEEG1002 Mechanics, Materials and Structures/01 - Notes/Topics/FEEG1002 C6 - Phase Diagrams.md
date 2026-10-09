---
title: "FEEG1002 C6 - Phase Diagrams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 21
tags: [feeg1002, materials, phase-diagrams, lever-rule, eutectic, solidification]
aliases: ["Materials Lectures 8 and 9", "Tie lines and lever rule", "Binary phase diagrams"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C3 - Diffusion]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
next_topics: ["[[FEEG1002 C7 - Steels and Precipitation Hardening]]"]
key_concepts: ["[[Tie Lines and Lever Rule]]", "[[Eutectic and Eutectoid Reactions]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 08 - Phase Diagrams 1 - Solid Solubility.pdf", "02 - Sources/Materials/Lectures/Lecture 09 - Phase Diagrams 2 - Partial Solubility.pdf"]
---

# FEEG1002 C6 - Phase Diagrams

> [!abstract] Summary
> A binary phase diagram is an equilibrium temperature-composition map. At a point: identify the phase field; use a horizontal **tie line** to read phase compositions; use the **lever rule** to obtain phase fractions. Microstructure requires a fourth step: follow the alloy vertically downward and track what forms at each boundary.

## Key Concepts
- [[Tie Lines and Lever Rule]] · [[Eutectic and Eutectoid Reactions]]

---

## 1. Definitions
- A **phase** is a homogeneous region with uniform crystal structure and composition.
- A phase diagram predicts the equilibrium phases after sufficiently slow cooling; it does not give the kinetics.
- A **microconstituent** is a recognisable part of a microstructure and may contain more than one phase (e.g. pearlite or a eutectic mixture).
- **Liquidus**: cooling crosses it when the first solid appears. **Solidus**: the last liquid disappears.

## 2. Complete solid solubility
For a point in $\alpha+L$, draw a horizontal tie line. Its endpoints give $C_\alpha$ and $C_L$. Mass conservation,

$$f_\alpha C_\alpha+f_LC_L=C_0,\qquad f_\alpha+f_L=1,$$

gives

$$f_\alpha=\frac{C_L-C_0}{C_L-C_\alpha},\qquad f_L=\frac{C_0-C_\alpha}{C_L-C_\alpha}$$

(equivalent forms with numerator/denominator signs reversed are fine).

> [!tip] The opposite-arm rule
> The fraction of a phase is the length of the tie-line arm **opposite** that phase, divided by the whole tie line. Check by moving toward a boundary: the phase named beyond that boundary must approach 100%.

![[m6_eutectic_lever_rule.png|800]]

## 3. Equilibrium versus non-equilibrium solidification
- Under equilibrium cooling, solute redistributes by diffusion in both liquid and solid.
- Under practical faster cooling, diffusion in the liquid remains easy but is slow in the solid. The interior and edge of a dendrite can retain different compositions: **coring**.
- Homogenisation heat treatment reduces coring by solid-state diffusion.

## 4. Partial solubility and the eutectic
Two terminal solid solutions $\alpha$ and $\beta$ meet a eutectic at one composition $C_E$ and temperature $T_E$:

$$L\rightarrow\alpha+\beta$$

- At the eutectic composition the entire liquid transforms isothermally into a fine lamellar two-phase microconstituent.
- **Hypoeutectic** ($C_0<C_E$): primary $\alpha$ dendrites form first; remaining liquid reaches $C_E$ and becomes eutectic.
- **Hypereutectic** ($C_0>C_E$): primary $\beta$ forms first, then eutectic.
- Lamellae keep diffusion distances short because $\alpha$ and $\beta$ have different compositions.

## 5. Primary fraction versus total phase fraction
These are different questions.

- **Primary $\alpha$ just above $T_E$**: use the tie line between $C_{\alpha E}$ and $C_E$.
- **Total $\alpha$ just below $T_E$**: use the tie line between $C_{\alpha E}$ and $C_{\beta E}$.

For Pb-Sn at 35 wt% Sn:

$$f_{primary\ \alpha}=\frac{61.9-35}{61.9-18.3}=61.7\%,$$

while below the eutectic

$$f_{total\ \alpha}=\frac{97.8-35}{97.8-18.3}=79.0\%.$$

The extra $\alpha$ lies inside the eutectic constituent.

## 6. A reliable exam workflow
1. Mark $C_0$ and $T$.
2. Name the phase field.
3. Draw the tie line and read endpoint compositions.
4. Apply the lever rule only if a fraction is requested.
5. For microstructure, start above the liquidus and follow the vertical composition line downward, stating what nucleates and what transforms.

> [!warning] Common traps
> - “Composition of $\alpha$” is read at the $\alpha$ boundary, not at $C_0$.
> - Three phases coexist at an invariant point, not over an area in a binary diagram at constant pressure.
> - Pure metals and stoichiometric compounds have fixed composition and a single melting point; most alloys solidify over a range.

## Links
- Previous: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]] · Next: [[FEEG1002 C7 - Steels and Precipitation Hardening]]
- Worked problems: [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions]]

## Sources
- Materials Lectures 8–9; audited against [[FEEG1002 Materials L08 Contact Sheet.png]] and [[FEEG1002 Materials L09 Contact Sheet.png]].


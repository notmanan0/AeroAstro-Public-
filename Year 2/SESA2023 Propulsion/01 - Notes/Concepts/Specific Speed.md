---
title: "Specific Speed"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 4: Turbomachinery and Propellers"
aliases: ["shape factor", "Ns", "machine selection"]
tags: [sesa2023, concept, turbomachinery, dimensional-analysis]
status: complete
parent_lectures: ["[[SESA2023 W09 - Turbomachinery Characteristics - Coefficients, Similarity and Maps]]"]
related_concepts: ["[[Dimensional Analysis of Turbomachines]]", "[[Flow and Work Coefficients]]"]
sources: ["02 - Sources/Lectures/Week 09 - Turbomachinery Characteristics.pdf"]
---
# Specific Speed

## Definition

> [!note] Definition
> A combination of $\phi$ and $\psi$ that **eliminates the size $D$**, so it can be evaluated from the duty ($Q$, $\Delta p$, $\Omega$) before the machine is designed:
> $$N_s = \frac{\phi^{1/2}}{\psi^{3/4}} = \frac{Q^{1/2}\,\Omega}{(\Delta p/\rho)^{3/4}}\quad(\Omega\text{ in rad/s, SI units})$$

## Explanation
- It is better called a **shape factor**: each machine type has its best efficiency at a particular $N_s$.
- **Low $N_s$**: low flow and high head (low $\phi$, high $\psi$), which needs positive-displacement or **centrifugal/radial** machines with short blades and a large radius ratio. Example: a vacuum-cleaner fan.
- **High $N_s$**: high flow and low head (high $\phi$, low $\psi$), which needs **axial** machines and propellers with few, long, widely spaced blades. Example: a windmill or propeller.
- **Rough bands**:

  | $N_s$ | Machine |
  |---|---|
  | < 0.4 | centrifugal |
  | ~0.4–2 | mixed flow |
  | > 2 | axial |

- **Compressible machines**: use the **inlet** volume flow, since $Q$ changes through the machine.
- **Why aero engines are axial**: best efficiency at high mass flow per frontal area, and stages can be stacked to reach high pressure ratio at acceptable weight. Small helicopter engines use centrifugal stages (lower $N_s$), at the cost of losses between stages.
- **Legacy question** (2015-16 Q1(i)), radial vs axial compressors:
  - Radial: about 10:1 per stage, robust, short, tolerant of damage, but a large diameter and inter-stage losses.
  - Axial: under 2:1 per stage but stackable, small frontal area, higher efficiency at high flow, but fragile and more costly.

## Related
- [[Dimensional Analysis of Turbomachines]] · [[Flow and Work Coefficients]]

## Sources
- Week 9 handout §9.4; Lectures 25–26

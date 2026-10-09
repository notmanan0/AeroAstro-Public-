---
title: "Friction and Heat Addition in Constant-Area Ducts"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["Fanno flow", "Rayleigh flow", "thermal choking", "frictional choking"]
tags: [sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]"]
related_concepts: ["[[Critical Conditions and Choked Flow]]", "[[Normal Shock Waves]]", "[[Entropy Change of a Perfect Gas]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf"]
---
# Friction and Heat Addition in Constant-Area Ducts

## Definition

> [!note] Definition
> Steady 1-D flow in a constant-area duct, with a dimensionless friction $f$ and heating $q$:
> $$\rho_1u_1 = \rho_2u_2,\quad p_1(1+\gamma M_1^2-f) = p_2(1+\gamma M_2^2),\quad h_1\Big(1+\tfrac{\gamma-1}{2}M_1^2+q\Big) = h_2\Big(1+\tfrac{\gamma-1}{2}M_2^2\Big)$$

## Explanation
- **Both friction and heating drive the flow towards $M = 1$**.
  - Subsonic flow **accelerates**, and $p$ and $\rho$ fall.
  - Supersonic flow **decelerates**, and $p$, $\rho$ and $T$ rise. Alternatively it jumps subsonic through a normal shock, if the back pressure is high.
- **Choking**: for each $M_1$ there is a maximum $f$ or $q$ that makes $M_2 = 1$. Adding more forces the upstream flow to change (less mass flow). This is the frictional (Fanno) or thermal (Rayleigh) analogue of nozzle choking.
- **Cooling** ($q<0$) does the opposite and always has a solution: it accelerates supersonic flow and decelerates subsonic flow.
- **The temperature exception**: heating subsonic flow with $1/\gamma<M^2<1$ *lowers* $T$, because the heat goes mostly into KE.
- $p_0$ always falls with friction (entropy rises). Subsonic outlets with $M_2>1$ are **inaccessible** ($\Delta s<0$).
- **Physical picture**: the growing boundary-layer displacement thickness acts like a converging nozzle.
- **Engine relevance**:
  - Heat release in a **ramjet or scramjet combustor** is Rayleigh-like, which is why the combustor $\Gamma_c<1$ even without friction.
  - Too much heat at a supersonic combustor inlet causes thermal choking (unstart).

![[prop_duct_friction_heating.png|700]]

## Related
- [[Critical Conditions and Choked Flow]] · [[Normal Shock Waves]] · [[Entropy Change of a Perfect Gas]]

## Sources
- Week 4 notes §3.2; Kundu et al. *Fluid Mechanics* Figs. 16.x

---
title: "Solid Propellant Burning Rate"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["Saint-Robert's law", "Vieille's law", "burning index", "pressure exponent", "erosive burning", "grain design"]
tags: [sesa2023, concept, rockets, solid-propellant]
status: complete
parent_lectures: ["[[SESA2023 W11 - Solid Propellants and Rocket Nozzle Design]]"]
related_concepts: ["[[Rocket Performance Parameters]]", "[[Rocket Nozzle Geometry]]"]
sources: ["02 - Sources/Lectures/Week 11 - Rockets.pdf"]
---
# Solid Propellant Burning Rate

## Definition

> [!note] Definition
> The **burning rate** $r$ is the speed at which the grain surface regresses normal to itself (mm/s). Empirically,
>
> $$r = aP_c^{\,n}\qquad(\text{Saint-Robert's law})$$
>
> Here $a$ is the *temperature coefficient* (depending on composition and initial temperature) and $n$ is the *burning index* (pressure exponent).

## Explanation
- **Measurement**: strand (Crawford) burners, small ballistic evaluation motors, or instrumented full-scale motors. The data are straight lines on log–log axes, sometimes piecewise (the double-base "plateau").
- **Interpretation of $n$**:
  - $n = 0$ is flat burning: $r$ is independent of $P_c$.
  - $n<0$: $r$ falls with $P_c$ (rare; useful for reignition).
  - $0.2<n<0.8$ is the practical range.
  - As $n\to1$, gas generation becomes very sensitive to $P_c$.
  - $n>1$ gives no stable equilibrium (runaway or extinction).
  - Very low $n$ risks extinction.
- **Why**: the gas generated, $\rho_pA_br = \rho_pA_baP_c^n$, must equal the nozzle outflow, $P_cA_t/C^*$. So $P_c\propto(A_b/A_t)^{1/(1-n)}$. For $n<1$ this is stable; for $n\ge1$ it isn't.
- **Grain design**: the thrust follows the burning **area** $A_b(t)$. A circular port gives a progressive thrust curve (the area grows). Stars, wagon wheels and slotted grains are shaped for neutral or regressive thrust.
- **Initial temperature $T_p$**: a hot grain burns faster, with higher thrust and a shorter burn. The **total impulse is about the same** (slightly higher). The case must survive the hot-day overpressure. Non-uniform $T_p$ gives thrust misalignment.
- **Erosive burning**: cross-flow raises the heat transfer and hence $r$. It happens in tubular grains, near the aft end, early in the burn (small port), and matters when $A_p/A_t<4$.
- **Acceleration** normal to the surface (spin, manoeuvres) cracks the grain, increasing area and $r$. It is noticeable at 5–10 g and can double $r$ above 30 g.

![[prop_burning_rate.png|560]]

## Related
- [[Rocket Performance Parameters]] · [[Rocket Nozzle Geometry]]

## Sources
- Week 11 notes §11.3; Lecture 33

---
title: "Electric (Ion) Propulsion"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 5: Rockets"
aliases: ["ion thruster", "gridded ion engine", "electrostatic propulsion", "Hall thruster"]
tags: [sesa2023, concept, rockets, legacy]
status: complete
parent_lectures: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
related_concepts: ["[[Rocket Performance Parameters]]", "[[Tsiolkovsky Rocket Equation]]"]
sources: ["02 - Sources/Lectures/Week 10 - Rockets.pdf", "03 - Exams & Past Papers/SESA2023-201617-02-SESA2023W1.pdf"]
---
# Electric (Ion) Propulsion

> [!warning] Legacy content
> Examined in 2016-17 Q2 and 2017-18 Q3, but not in the current (2021+) lecture notes, which explicitly leave electric propulsion out.

## Definition

> [!note] Definition
> Ions (e.g. singly charged xenon) are accelerated through a net potential $V_b$ by electrostatic grids:
>
> $$v = \sqrt{\frac{2qV_b}{m_i}},\qquad\dot m = \frac{I_bm_i}{q},\qquad F = \dot mv\cos\theta_{div} = I_b\sqrt{\frac{2m_iV_b}{q}}\cos\theta_{div}$$

## Explanation
- **Energy vs power**: chemical rockets are **energy-limited**, because the propellant's own chemical energy sets $c_e\lesssim4.5$ km/s. Electric thrusters are **power-limited**: the energy comes from solar or nuclear electricity, $P = I_bV_b$.
- **Thrust per power**: $F/P = 2/v$ (ideal). So a high $I_{sp}$ (tens of km/s) gives a tiny thrust (mN to N) for realistic power. That means long burn times, but huge propellant savings through Tsiolkovsky.
- **Constraints**:
  - space-charge limits on current density (Child's law), so a large grid area is needed;
  - grid erosion (lifetime);
  - beam neutralisation (a cathode);
  - power and thermal mass.
- **Divergence**: the lecture-style $\cos\theta$ factor for a beam half-angle $\theta$. The rocket-nozzle $(1+\cos\alpha)/2$ gives almost the same answer at 15°.

## Examples
- 2016-17 Q2(ii), two thrusters, Xe (131.3 amu), 21 A, 1.8 kV, 15° divergence:
  - $v = 51.4$ km/s ($I_{sp}\approx5240$ s);
  - $\dot m = 2.86\times10^{-5}$ kg/s each;
  - $F = 1.42$ N each, **2.84 N total**.

## Related
- [[Rocket Performance Parameters]] · [[Tsiolkovsky Rocket Equation]]

## Sources
- 2016-17 and 2017-18 papers; Goebel & Katz, *Fundamentals of Electric Propulsion*

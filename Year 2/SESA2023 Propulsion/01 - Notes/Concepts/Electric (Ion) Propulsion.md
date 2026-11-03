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

An ion thruster accelerates ions, for example singly charged xenon, through a net potential $V_b$ with electrostatic grids:

$$
v = \sqrt{\frac{2qV_b}{m_i}},\qquad\dot m = \frac{I_bm_i}{q},\qquad F = \dot mv\cos\theta_{div} = I_b\sqrt{\frac{2m_iV_b}{q}}\cos\theta_{div} .
$$

This is legacy content, examined in 2016-17 Q2 and 2017-18 Q3 but explicitly left out of the current (2021 onwards) lecture notes.

Chemical rockets are energy-limited: the propellant's own chemical energy sets $c_e\lesssim4.5$ km/s. Electric thrusters are power-limited instead, with the energy coming from solar or nuclear electricity, $P = I_bV_b$. Ideally $F/P = 2/v$, so a high specific impulse (tens of km/s) gives only a tiny thrust (mN to N) for realistic power: long burn times, but huge propellant savings through Tsiolkovsky. The practical constraints are the space-charge limit on current density (Child's law), which needs a large grid area, grid erosion, which sets the lifetime, beam neutralisation by a cathode, and the mass of the power and thermal systems. Beam divergence is taken as a $\cos\theta$ factor for a half-angle $\theta$; the rocket-nozzle factor $(1+\cos\alpha)/2$ gives almost the same answer at 15°.

In 2016-17 Q2(ii), two xenon thrusters (131.3 amu) at 21 A, 1.8 kV and 15° divergence give $v = 51.4$ km/s ($I_{sp}\approx5240$ s), $\dot m = 2.86\times10^{-5}$ kg/s each and $F = 1.42$ N each, 2.84 N in total.

## Related

- [[Rocket Performance Parameters]] · [[Tsiolkovsky Rocket Equation]]

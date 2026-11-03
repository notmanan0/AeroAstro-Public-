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

The **burning rate** $r$ of a solid propellant is the speed, in mm/s, at which the grain surface regresses normal to itself. Empirically it follows Saint-Robert's law, $r = aP_c^{\,n}$, where $a$ is the temperature coefficient, set by the composition and initial temperature, and $n$ is the burning index (pressure exponent).

It is measured with strand (Crawford) burners, small ballistic evaluation motors or instrumented full-scale motors, and the data plot as straight lines on log–log axes, sometimes piecewise, as in the double-base plateau. The value of $n$ decides how the motor behaves. With $n = 0$ (flat burning) the rate doesn't depend on pressure, and $n<0$, which is rare, is useful for reignition. The practical range is $0.2<n<0.8$. As $n\to1$ the gas generation becomes very sensitive to chamber pressure, $n>1$ has no stable equilibrium (it runs away or goes out), and a very low $n$ risks extinction. The reason is the mass balance: the gas generated, $\rho_pA_br = \rho_pA_baP_c^n$, must equal the nozzle outflow $P_cA_t/C^*$, so $P_c\propto(A_b/A_t)^{1/(1-n)}$, which is stable only for $n<1$.

The thrust follows the burning area $A_b(t)$, which is what grain design controls. A circular port gives a progressive thrust curve as its area grows; star, wagon-wheel and slotted grains are shaped for neutral or regressive thrust. A hot grain burns faster, with higher thrust and a shorter burn but about the same (slightly higher) total impulse, and the case must survive the hot-day overpressure; a non-uniform grain temperature gives thrust misalignment. Erosive burning, where cross-flow raises the heat transfer and so $r$, happens in tubular grains near the aft end early in the burn, when the port is small, and matters when $A_p/A_t<4$. Acceleration normal to the burning surface, from spin or manoeuvres, cracks the grain and increases the area and rate; it is noticeable at 5–10 g and can double $r$ above 30 g.

![[prop_burning_rate.png|560]]

## Related

- [[Rocket Performance Parameters]] · [[Rocket Nozzle Geometry]]

---
title: "Steady-flow Energy Equation"
module: "SESA1016 Thermofluids"
type: concept
stream: "Conservation Laws"
aliases: ["SFEE", "flow energy equation"]
tags: [sesa1016, concept, energy]
status: complete
parent_lectures: ["[[SESA1016 T13 - Conservation of Energy and Propulsion]]"]
related_concepts: ["[[Internal Energy and Enthalpy]]", "[[Control-volume Analysis Workflow]]", "[[Major and Minor Head Losses]]"]
sources: ["02 - Sources/Lectures/Chapter 13.pdf"]
---

# Steady-flow Energy Equation

The steady-flow energy equation (SFEE) is the first law for a control volume in steady flow: the heat added minus the shaft work done by the fluid equals the change in total enthalpy flow between outlet and inlet.

$$
\dot Q-\dot W_x=\dot m\left(h_{tot,out}-h_{tot,in}\right),\qquad h_{tot}=h+\tfrac12V^2+gz
$$

It comes from the control-volume energy balance, $\dot Q-\dot W=$ accumulation $+$ net energy outflow, in two steps. In steady flow the accumulation is zero. The work is split into shaft work $\dot W_x$, delivered through a rotating shaft or similar, and flow work, the work the fluid does pushing its way out of and into the control volume, $\dot m(pv)_{out}-\dot m(pv)_{in}$. The flow work combines with the internal energy carried across the boundary to make enthalpy, so the equation is written in $h$ rather than $u$.

The usual simplifications follow from what a device does. A nozzle or diffuser has no shaft work and little heat transfer, so $h+\tfrac12V^2$ is constant through it. A well-insulated turbine or compressor has negligible heat transfer and kinetic-energy change, so $\dot W_x=\dot m(h_{in}-h_{out})=\dot mc_p(T_{in}-T_{out})$. A heat exchanger has no shaft work, so the heat lost by one stream is the enthalpy gained by the other. For an incompressible fluid with no heat transfer and no shaft work, the SFEE reduces to the Bernoulli equation plus a loss term.

## Related

- [[SESA1016 T13 - Conservation of Energy and Propulsion#Total enthalpy and the SFEE|T13 SFEE]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Simplified forms|simplified forms]] · [[SESA1016 T13 - Conservation of Energy and Propulsion#Worked example - industrial gas turbine|gas turbine example]] · [[SESA1016 T15 - Flow in Conduits#The SFEE for a pump|SFEE for a pump]]
- [[Internal Energy and Enthalpy]] · [[Control-volume Analysis Workflow]] · [[Major and Minor Head Losses]] · [[Bernoulli Equation]]

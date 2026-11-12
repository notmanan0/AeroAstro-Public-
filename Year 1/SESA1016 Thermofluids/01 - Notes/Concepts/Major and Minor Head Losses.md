---
title: "Major and Minor Head Losses"
module: "SESA1016 Thermofluids"
type: concept
stream: "Internal Flow"
aliases: ["head loss", "pipe losses"]
tags: [sesa1016, concept, pipe-flow]
status: complete
parent_lectures: ["[[SESA1016 T15 - Flow in Conduits]]"]
related_concepts: ["[[Darcy Friction Factor]]", "[[Pressure and Head]]", "[[Steady-flow Energy Equation]]"]
sources: ["02 - Sources/Lectures/Chapter 15.pdf"]
---

# Major and Minor Head Losses

Head losses are the mechanical energy per unit weight that a pipe system dissipates: major losses from wall friction along straight pipe, $h_f=f\dfrac LD\dfrac{\bar V^2}{2g}$, and minor losses from fittings such as bends, valves, entrances and exits, $h_m=K\dfrac{\bar V^2}{2g}$.

Both scale with the dynamic head $\bar V^2/2g$. The friction loss grows with length, through the [[Darcy Friction Factor]]; a fitting's loss is concentrated where the flow separates and mixes, and the loss coefficient $K$ is measured for each fitting type. The word minor refers to the usual case of long pipes; in a short pipe with several valves and bends the minor losses can dominate.

For a whole system the losses add, in pressure form

$$
\Delta p_{loss}=\sum f\frac LD\tfrac12\rho\bar V^2+\sum K\tfrac12\rho\bar V^2,
$$

with $\bar V$ taken in each pipe section. They enter the energy balance between two points as $p_1/\rho g+\bar V_1^2/2g+z_1+h_p=p_2/\rho g+\bar V_2^2/2g+z_2+h_L$, where $h_p$ is the head added by a pump. The required pump power is then $\dot W=\rho g\dot{\mathcal V}h_p$ for an ideal pump, divided by the pump efficiency for a real one.

On a head diagram the energy grade line slopes down steadily along straight pipe, steps down at each fitting and steps up at a pump; the hydraulic grade line sits $\bar V^2/2g$ below it.

![[tf_conduit_head_loss.png|760]]

## Related

- [[SESA1016 T15 - Flow in Conduits#Head loss|head loss]] · [[SESA1016 T15 - Flow in Conduits#7. Minor losses|T15 §7]] · [[SESA1016 T15 - Flow in Conduits#8. Pumping power|pumping power]] · [[SESA1016 T15 - Flow in Conduits#Worked example - minor-loss coefficient of a valve|valve K example]]
- [[Darcy Friction Factor]] · [[Pressure and Head]] · [[Steady-flow Energy Equation]]

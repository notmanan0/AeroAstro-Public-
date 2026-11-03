---
title: "Supersonic Wind Tunnel"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 3: Nozzles and the Method of Characteristics"
aliases: ["second throat", "wind-tunnel starting", "starting shock", "Ludwieg tube", "supersonic diffuser"]
tags: [sesa3029, concept, wind-tunnel, nozzle]
status: complete
parent_lectures: ["[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
related_concepts: ["[[Isentropic Nozzle Flow]]", "[[Critical Conditions and Choked Flow]]", "[[Normal-Shock Jump Relations]]"]
sources: ["02 - Sources/Lectures/Lecture2-7.pdf"]
---

# Supersonic Wind Tunnel

A supersonic wind tunnel runs from a reservoir through a Laval nozzle (the first throat, $A_{t1}$) into the test section, and then through a diffuser with a **second throat** $A_{t2}$. When the tunnel starts up, a normal shock stands in the test section. To start the tunnel properly that shock has to be swallowed through the second throat, which needs

$$\frac{A_{t2}}{A_{t1}}\ \ge\ \frac{p_{01}}{p_{02}}\Big|_{\text{normal shock at }M_{test}}.$$

The condition comes from the choked mass flow, $\dot m\propto p_0A^*/\sqrt{T_0}$. Both throats pass the same mass flow and $T_0$ does not change across the shock, so $p_{01}A_{t1}=p_{02}A_{t2}$. The shock has lowered the stagnation pressure, so the second throat has to be bigger. If $A_{t2}<A_{t1}$, the second throat chokes first and the test section never goes supersonic.

The slides work it at $M=3$: $A_{test}/A_{t1}=4.2346$ and $A_{test}/A_{t2}=A/A^*(0.4752)=1.3908$, so $A_{t2}/A_{t1}=3.045=1/0.3283$. The ratio climbs quickly with Mach number: 1.39 at $M=2$, 3.05 at $M=3$, 7.2 at $M=4$ and 16.2 at $M=5$. That is why high-Mach facilities use variable-geometry diffusers or run for only a short time.

A **Ludwieg tube** is one such short-duration facility. Bursting a diaphragm sends an expansion wave back into a long storage tube, and the gas behind it is accelerated through a Laval nozzle. The run lasts about 0.1 s, until the expansion reflects off the closed end of the tube and comes back.

![[at_wind_tunnel_starting.png|760]]

## Related

- [[Isentropic Nozzle Flow]] · [[Critical Conditions and Choked Flow]] · [[Normal-Shock Jump Relations]] · [[SESA2022 Wind Tunnel Lab Summary]]
- Detail: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#7. The supersonic wind tunnel (slides 8–11)|W04 §7]]

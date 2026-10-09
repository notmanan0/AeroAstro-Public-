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

## Definition

> [!note] Definition
> A supersonic wind tunnel runs: reservoir → Laval nozzle (first throat $A_{t1}$) → test section → diffuser with a **second throat** $A_{t2}$. To **start**, the normal shock that first stands in the test section must be swallowed, which needs
>
> $$\frac{A_{t2}}{A_{t1}}\ \ge\ \frac{p_{01}}{p_{02}}\Big|_{\text{normal shock at }M_{test}}.$$

## Explanation

- Choked mass flow is $\dot m\propto p_0A^*/\sqrt{T_0}$. With $T_0$ unchanged across the shock, $p_{01}A_{t1}=p_{02}A_{t2}$.
- **Slide route at $M=3$:** $A_{test}/A_{t1}=4.2346$ and $A_{test}/A_{t2}=A/A^*(0.4752)=1.3908$, so $A_{t2}/A_{t1}=3.045$. This equals $1/0.3283$.
- If $A_{t2}<A_{t1}$, the second throat chokes first and the test section never goes supersonic.
- The ratio grows fast with $M$: 1.39 at $M=2$, 3.05 at $M=3$, 7.2 at $M=4$, 16.2 at $M=5$. Hence variable-geometry diffusers and short-duration facilities.
- **Ludwieg tube:** a burst diaphragm sends an expansion wave back into a long storage tube. The gas behind it is accelerated through a Laval nozzle, and the run lasts about 0.1 s, until the expansion reflects back from the closed end.

![[at_wind_tunnel_starting.png|760]]

## Related

- [[Isentropic Nozzle Flow]] · [[Critical Conditions and Choked Flow]] · [[Normal-Shock Jump Relations]] · [[SESA2022 Wind Tunnel Lab Summary]]
- Detail: [[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow#7. The supersonic wind tunnel (slides 8–11)|W04 §7]]

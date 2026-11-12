---
title: "Thrust-to-Weight Ratio"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["T/W", "Thrust to Weight Ratio", "Thrust Loading"]
tags: [sesa1015, concept, constraint-analysis, aircraft-performance]
status: complete
parent_lectures: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]", "[[SESA1015 M08 - Glide and Climb Performance]]", "[[SESA1015 M09 - Take-off and Landing Performance]]"]
related_concepts: ["[[Aircraft Constraint Diagram]]", "[[Wing Loading]]", "[[Take-off Ground Run]]"]
sources: ["Mechanics of Flight Course Notes §7.2–7.3", "Older lecture deck, pp. 220–224"]
---

# Thrust-to-Weight Ratio

The thrust to weight ratio $T/W$ is the installed engine thrust divided by the aircraft weight, a dimensionless measure of how much propulsive force is available per newton of aircraft.

It appears wherever thrust has to overcome something proportional to weight. In steady level flight $T=D$, so the ratio needed is $D/W=1/(L/D)$, and its least value over all speeds is $1/(L/D)_{\max}=2\sqrt{KC_{D0}}$. In a steady climb $T-D=W\sin\gamma$, so

$$
\frac TW=\frac DW+\sin\gamma=\frac DW+\frac{V_V}{V},
$$

and the surplus $(T-D)/W$ is the specific excess thrust of [[SESA1015 M08 - Glide and Climb Performance|M08]]. On the take-off ground run, with lift and drag neglected, the acceleration is $g(T/W-\mu)$, which integrates to $s_1=V_2^2/[2g(T/W-\mu)]$ and gives the take-off requirement $T/W=V_2^2/(2gs_1)+\mu$ ([[Take-off Ground Run]]). A ratio above 1 allows a vertical climb.

In constraint analysis $T/W$ is the vertical axis of the [[Aircraft Constraint Diagram]], paired with [[Wing Loading]] on the horizontal axis. The value read at the design point is converted to an engine size by $T=W(T/W)$: the 15 kg UAV of the course spreadsheet needs $T/W=0.386$, so $T=0.386\times147.15=56.8$ N. Because thrust changes with altitude and speed, a $T/W$ quoted for sizing is normally the sea-level static value at take-off weight, and requirements at other conditions are divided by the thrust lapse $\alpha=T_h/T_{SL}$ and multiplied by the weight fraction before they are compared with it.

For propeller aircraft the analogous ratio is power to weight, $P/W$, since the engine delivers power rather than thrust ([[SESA1015 M07 - Propeller Aircraft Range and Endurance|M07]]).

## Related

- Topics: [[SESA1015 M12 - Aircraft Constraint Analysis]] · [[SESA1015 M08 - Glide and Climb Performance]] · [[SESA1015 M09 - Take-off and Landing Performance]]
- Concepts: [[Aircraft Constraint Diagram]] · [[Wing Loading]] · [[Take-off Ground Run]] · [[Minimum Drag and Minimum Power]]
- Sources: course notes §7.2 (pp. 37–38) and §7.3 (pp. 40–41); older lecture deck, pp. 220–224

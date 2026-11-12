---
title: "Aircraft Constraint Diagram"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Constraint Diagram", "T/W versus W/S Diagram", "Constraint Map", "Design Space"]
tags: [sesa1015, concept, constraint-analysis, aircraft-design]
status: complete
parent_lectures: ["[[SESA1015 M12 - Aircraft Constraint Analysis]]"]
related_concepts: ["[[Thrust-to-Weight Ratio]]", "[[Wing Loading]]", "[[Parabolic Drag Polar]]", "[[Take-off Ground Run]]", "[[Load Factor and Turn Performance]]"]
sources: ["Mechanics of Flight Lecture Slides version 2, p. 180", "Older lecture deck, pp. 220–225", "Mechanics of Flight - Constraint Analysis.xlsx"]
---

# Aircraft Constraint Diagram

A constraint diagram is a plot of required thrust to weight ratio $T/W$ against wing loading $W/S$ on which every performance requirement is drawn as a boundary, so that the region satisfying all of them, and the cheapest point in it, can be read off at once.

The two ratios are used because the requirements depend on them and not on the aircraft's absolute size. Wing loading fixes the lift coefficient at a given dynamic pressure, $C_L=n(W/S)/q$, and with a parabolic polar the drag per unit weight becomes

$$
\frac DW=\frac{qC_{D0}}{W/S}+\frac{Kn^2}{q}\,\frac WS .
$$

That expression gives the U-shaped curves: cruise ($n=1$), a level turn at load factor $n$, and a climb, which adds the gradient $V_V/V$. The left branch is profile drag on an oversized wing; the right branch is induced drag on an overloaded one, and the bottom of the cruise curve is at $T/W=2\sqrt{KC_{D0}}=1/(L/D)_{\max}$. The take-off ground run gives $T/W=V_2^2/(2gs_1)+\mu$, a horizontal line when $V_2$ is specified. The approach or stall speed gives $W/S\leq\frac12\rho V_s^2C_{L\max}$, a vertical line that caps the wing loading.

Each boundary has an acceptable side (above a thrust curve, left of the stall line), and the feasible region is where all of them overlap. Its floor is the upper envelope of the thrust curves; whichever curve forms the envelope at a given $W/S$ is the sizing constraint there. A design point is chosen on the edge of the region, usually near the corner at the highest permitted wing loading and the least thrust, with some margin for uncertain estimates of $C_{L\max}$, $C_{D0}$ and installed thrust. The wing area and thrust then follow as $S=W/(W/S)$ and $T=W(T/W)$, and the original performance formulas are rechecked with those values.

For the 15 kg UAV of the course spreadsheet the stall line is at 151.6 N/m² (15.45 kg/m²), the take-off line at $T/W=0.386$, and the take-off line is the floor of the feasible region from 61.3 N/m² to the stall limit. The design point (151.6 N/m², 0.386) gives a 0.97 m² wing and 56.8 N of thrust. Two traps recur: all curves must refer to the same weight and the same thrust rating before they are overlaid (landing weight and thrust lapse with altitude change both axes), and the course plot's axis is in kg/m² even where it is labelled N/m².

## Related

- Topic: [[SESA1015 M12 - Aircraft Constraint Analysis]] · Solutions: [[SESA1015 T08 - Constraint Analysis Solutions]]
- Concepts: [[Thrust-to-Weight Ratio]] · [[Wing Loading]] · [[Parabolic Drag Polar]] · [[Minimum Drag and Minimum Power]] · [[Take-off Ground Run]] · [[Load Factor and Turn Performance]]
- Sources: Slides v2, p. 180; older lecture deck, pp. 220–225; `Mechanics of Flight - Constraint Analysis.xlsx`

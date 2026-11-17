---
title: "Types of Heat Exchangers"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 5: Heat transfer"
aliases: ["heat exchanger types", "parallel flow", "parallel-flow heat exchanger", "co-current flow", "counter flow", "counterflow", "counter-flow heat exchanger", "countercurrent flow", "crossflow", "cross-flow heat exchanger", "mixed and unmixed flow", "shell and tube heat exchanger", "shell-and-tube heat exchanger", "concentric tube heat exchanger", "double-pipe heat exchanger"]
tags: [sesa3029, concept, heat-transfer, heat-exchanger]
status: complete
parent_lectures: ["[[SESA3029 W09f - Heat Exchangers]]"]
related_concepts: ["[[Overall Heat Transfer Coefficient]]", "[[Log Mean Temperature Difference]]", "[[Heat Exchanger Effectiveness and NTU]]", "[[Heat Capacity Rate]]"]
sources: ["02 - Sources/Lectures/Lecture5.8(1).pdf", "02 - Sources/Lectures/Lecture5.10.pdf"]
---

# Types of Heat Exchangers

A heat exchanger transfers heat between two fluids at different temperatures without mixing them; the types differ in the geometry and in the relative directions of the two flows.

A **concentric tube** (double-pipe) exchanger puts one fluid in an inner tube and the other in the annulus around it. In **parallel flow** both enter at the same end and move the same way: the temperature difference is largest at the inlet and decays exponentially towards the outlet, and the cold outlet can never exceed the hot outlet. In **counter flow** they enter at opposite ends: the hot inlet faces the cold outlet, the difference stays more uniform, and the cold outlet can exceed the hot outlet. For the same four terminal temperatures counter flow has the larger log mean temperature difference and needs less area; for the same NTU and capacity ratio it has the higher effectiveness. The two coincide only when one stream is at a constant temperature.

In **crossflow** the two fluids move perpendicular to one another, typically gas across a bank of liquid-carrying tubes. Plate fins make the cross-flow fluid **unmixed**, confined to the interfin spacing with no transverse motion; without fins it is **mixed**, free to move transversely, and mixing can significantly change the heat transfer. A **shell-and-tube** exchanger packs many tubes into a shell, with baffles to direct the shell-side fluid across the tubes and multi-pass tube arrangements to improve the heat transfer. It is generally heavy and not preferred for aerospace use, but it is the standard power-station condenser: the W09f example has 30 000 tubes of two passes each, 4.51 m per pass.

![[at_w09f_crossflow_shell_tube.png|760]]

## Related

- Parent lecture: [[SESA3029 W09f - Heat Exchangers#2. Types of heat exchangers|W09f §2]]
- Related concepts: [[Overall Heat Transfer Coefficient]] · [[Log Mean Temperature Difference]] · [[Heat Exchanger Effectiveness and NTU]] · [[Heat Capacity Rate]]

## Sources

- `Lecture5.8(1).pdf`, slides 2–4 and 7–8, 16; `Lecture5.10.pdf`, slides 2 and 7.

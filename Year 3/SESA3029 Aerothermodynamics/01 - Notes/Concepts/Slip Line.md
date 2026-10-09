---
title: "Slip Line"
module: "SESA3029 Aerothermodynamics"
type: concept
stream: "Block 2: Oblique Shocks and Expansions"
aliases: ["slip lines", "contact discontinuity", "contact surface", "shear layer (inviscid)", "jet boundary"]
tags: [sesa3029, concept, slip-line]
status: complete
parent_lectures: ["[[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method]]", "[[SESA3029 W04 - Laval Nozzle, Under- and Over-Expanded Flow]]"]
related_concepts: ["[[Mach Reflection]]", "[[Shock-Expansion Theory]]", "[[Over- and Under-Expanded Jets]]"]
sources: ["02 - Sources/Lectures/Lecture2-3.pdf", "02 - Sources/Lectures/Lecture2-7.pdf"]
---

# Slip Line

## Definition

> [!note] Definition
> A **slip line** (contact discontinuity) is a streamline across which **pressure and flow direction are continuous** but velocity, temperature, density and entropy may jump. No mass crosses it.

## Explanation

The two conditions come from force balance and kinematics:

- a pressure difference across a massless interface would accelerate it without limit, so the pressures must match;
- if the directions differed, the streams would overlap or separate, so they must be parallel.

Nothing requires equal speeds in inviscid flow. Physically, viscosity smears the jump into a shear layer.

**Where slip lines appear:**

- behind the triple point of a [[Mach Reflection]];
- after two shocks cross, at the shock–shock interaction ($\Delta\theta=5.83^\circ$ for the Lecture 2.3 example at $M=3$, $18^\circ$ and $12^\circ$);
- behind the trailing edge of an aerofoil in the [[Shock-Expansion Theory]];
- at the edge of a free jet, where $p=p_\infty$ ([[Over- and Under-Expanded Jets]]).

**Wave reflection.**

| Boundary | Incident wave | Reflected wave |
|---|---|---|
| solid wall | shock | shock |
| solid wall | fan | fan |
| **constant-pressure** slip line (free jet edge) | shock | **fan** |
| **constant-pressure** slip line (free jet edge) | fan | **compression** |

The last two rows are the origin of shock diamonds.

## Related

- [[Mach Reflection]] · [[Shock-Expansion Theory]] · [[Over- and Under-Expanded Jets]]
- Detail: [[SESA3029 W03 - Shock Reflections, Expansion Waves and the Shock-Expansion Method#3. Shock–shock interaction and slip lines|W03 §3]]

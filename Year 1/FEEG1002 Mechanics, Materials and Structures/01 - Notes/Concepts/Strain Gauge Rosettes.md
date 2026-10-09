---
title: "Strain Gauge Rosettes"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["rosette", "0/45/90 rosette", "delta rosette", "0/60/120 rosette", "strain gauge"]
tags: [feeg1002, concept, statics-2, strain-gauges, measurement]
status: complete
parent_lectures: ["[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Mohr's Circle]]", "[[Generalised Hooke's Law]]", "[[Wheatstone Bridge and Strain Gauges]]"]
sources: []
---

# Strain Gauge Rosettes

## Definition

> [!note] Definition
> Three gauges at known angles measure three normal strains, which fix the 2D strain state through the transformation equation $\varepsilon(\theta) = \varepsilon_{xx}\cos^2\theta + \varepsilon_{yy}\sin^2\theta + 2\varepsilon_{xy}\sin\theta\cos\theta$.
>
> | Type | $\varepsilon_{xx}$ | $\varepsilon_{yy}$ | $\varepsilon_{xy}$ |
> |---|---|---|---|
> | 0/45/90 | $\varepsilon_A$ | $\varepsilon_B$ | $\varepsilon_C - \tfrac12(\varepsilon_A+\varepsilon_B)$ |
> | 0/60/120 | $\varepsilon_A$ | $\tfrac13[2(\varepsilon_B+\varepsilon_C)-\varepsilon_A]$ | $(\varepsilon_B-\varepsilon_C)/\sqrt3$ |

## Explanation

- A single gauge reads the normal strain along one line only ($\Delta R/R = k\varepsilon$, $k\approx2$); it cannot sense shear directly.
- Align $x$ with one gauge to eliminate one unknown. Otherwise, solve three simultaneous equations.
- A gauge at $+60^\circ$ is the same as one at $-120^\circ$: a line has no direction.
- Next steps:
  1. principal strains from Mohr's circle;
  2. stresses from the inverse plane-stress Hooke's law;
  3. $\sigma_{eq}$ and the safety factor ([[FEEG1002 B6 - Yield Criteria]]).
- **Torsion**: two gauges at ±45° give $\varepsilon_{xy} = (\varepsilon_I - \varepsilon_{II})/2$.

## Examples

- Prosthetic socket (Statics 2 Tutorial 6): $\varepsilon_{xx} = 253$, $\varepsilon_{yy} = 307$, $\varepsilon_{xy} = -446$ με.
- Hydraulic press (Tutorial 8 Q1): SF = 2.0, so the maximum load is 900 MN.

![[s2_strain_rosettes.png|760]]

## Related

- Topic notes: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]
- Concepts: [[Stress Transformation Equations]] · [[Mohr's Circle]] · [[Generalised Hooke's Law]] · [[Wheatstone Bridge and Strain Gauges]]
- Year 2: [[Wheatstone Bridge and Strain Gauges]] and the [[Measurement Chain]] in [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] · test data for [[Model Updating]]

## Sources

- Statics 2 Lecture 7a–c

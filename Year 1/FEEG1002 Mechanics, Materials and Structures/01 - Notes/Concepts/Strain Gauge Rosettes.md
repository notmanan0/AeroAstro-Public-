---
title: "Strain Gauge Rosettes"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["rosette", "0/45/90 rosette", "delta rosette", "0/60/120 rosette", "strain gauge", "gauge factor"]
tags: [feeg1002, concept, statics-2, strain-gauges, measurement]
status: complete
parent_lectures: ["[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
related_concepts: ["[[Stress Transformation Equations]]", "[[Mohr's Circle]]", "[[Generalised Hooke's Law]]", "[[Wheatstone Bridge and Strain Gauges]]", "[[Von Mises Yield Criterion]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 07 - Strain Measurement.pdf"]
---

# Strain Gauge Rosettes

A strain gauge rosette is a set of three strain gauges at known angles on one backing; their three normal-strain readings fix the three in-plane strain components $\varepsilon_{xx}$, $\varepsilon_{yy}$ and $\varepsilon_{xy}$ at the point where it is bonded.

A single foil gauge changes resistance in proportion to the normal strain along its own line, $\Delta R/R=k\varepsilon$, with gauge factor $k$ near 2, and is read with a Wheatstone bridge. It cannot sense shear, and its reading depends on its direction through the strain transformation equation $\varepsilon(\theta)=\varepsilon_{xx}\cos^2\theta+\varepsilon_{yy}\sin^2\theta+2\varepsilon_{xy}\sin\theta\cos\theta$. Writing that equation once for each gauge gives three equations for three unknowns. Aligning $x$ with one gauge removes one unknown; the strains can then be rotated into any other axes. A gauge measures along a line, so $\theta$ and $\theta\pm180^\circ$ are the same gauge.

The two standard layouts give closed forms. For the 0/45/90 rosette, with A at 0°, C at 45° and B at 90° in the labelling used here,

$$
\varepsilon_{xx}=\varepsilon_A,\qquad \varepsilon_{yy}=\varepsilon_B,\qquad \varepsilon_{xy}=\varepsilon_C-\tfrac12(\varepsilon_A+\varepsilon_B)
$$

and for the 0/60/120 rosette, with A, B and C at 0°, 60° and 120°,

$$
\varepsilon_{xx}=\varepsilon_A,\qquad \varepsilon_{yy}=\frac{2(\varepsilon_B+\varepsilon_C)-\varepsilon_A}{3},\qquad \varepsilon_{xy}=\frac{\varepsilon_B-\varepsilon_C}{\sqrt3}
$$

Labels differ between sources, so match each reading to its angle before substituting.

The usual chain continues from the strains: principal strains from Mohr's circle for strain, stresses from the inverse plane-stress Hooke's law (the gauged surface is free, so it is in plane stress), and an equivalent stress and safety factor from the von Mises criterion, which does not depend on how the rosette was oriented. For a shaft in torsion two gauges at ±45° are enough, since they read the principal strains $\pm\varepsilon_{xy}$ directly.

![[s2_strain_rosettes.png|800]]

## Related

- [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#6. Strain gauge rosettes|rosettes in B5]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#1. Electrical strain gauges|gauges and the bridge]] · [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - prosthetic socket rosette|Tutorial 6 example]] · [[FEEG1002 B6 - Yield Criteria#Worked example - hydraulic press frame|rosette to safety factor]]
- [[Stress Transformation Equations]] · [[Mohr's Circle]] · [[Generalised Hooke's Law]] · [[Wheatstone Bridge and Strain Gauges]] · [[Von Mises Yield Criterion]]
- Year 1 electronics: [[FEEG1004 E3 - Strain Gauges, Bridges, Pressure and Flow Sensors]]

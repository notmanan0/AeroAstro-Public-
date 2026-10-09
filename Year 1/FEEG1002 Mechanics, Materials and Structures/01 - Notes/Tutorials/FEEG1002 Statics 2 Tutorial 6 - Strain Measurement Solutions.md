---
title: "FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, strain-gauges, rosettes]
sheet: "Statics-2 Tutorial problem sheet 6"
theory_notes: ["[[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]"]
key_concepts: ["[[Strain Gauge Rosettes]]", "[[Mohr's Circle]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 06 - Strain Measurement.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 06 - Strain Measurement - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions

> [!abstract] Sheet Info
> One rosette problem. Answers reproduced ✔ (253, 307, −446 με), with the principal strains added and a back-check of all three gauge readings.

## Theory Links
- [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]] · [[Strain Gauge Rosettes]]

---

## Q1: Rosette on a prosthetic socket, $\varepsilon_1 = 480$, $\varepsilon_2 = -120$, $\varepsilon_3 = 80$ με
Geometry from the figure: gauge 1 at $-15^\circ$, gauge 2 at $+30^\circ$ and gauge 3 at $+75^\circ$ to $x$. The gauges are 45° apart.

**Step 1: work in axes aligned with gauge 1.** In $x^*y^*$ ($x^*$ along gauge 1) the rosette is a standard 0/45/90° rosette:

$$
\varepsilon_{x^*x^*} = \varepsilon_1 = 480,\qquad \varepsilon_{y^*y^*} = \varepsilon_3 = 80,\qquad \varepsilon_{x^*y^*} = \varepsilon_2 - \tfrac12(\varepsilon_1+\varepsilon_3) = -120 - 280 = -400\ \mu\varepsilon
$$

**Step 2: rotate into $xy$.** $x$ is 15° anticlockwise from $x^*$, so $\theta = +15^\circ$:

$$
\varepsilon_{xx} = 480\cos^215^\circ + 80\sin^215^\circ + 2(-400)\sin15^\circ\cos15^\circ = \mathbf{253}\ \mu\varepsilon
$$

$$
\varepsilon_{yy} = 480\sin^215^\circ + 80\cos^215^\circ - 2(-400)\sin15^\circ\cos15^\circ = \mathbf{307}\ \mu\varepsilon
$$

$$
\varepsilon_{xy} = -(480-80)\sin15^\circ\cos15^\circ + (-400)(\cos^215^\circ - \sin^215^\circ) = \mathbf{-446}\ \mu\varepsilon\ ✔
$$

**Check**: $\varepsilon_{xx} + \varepsilon_{yy} = 560 = \varepsilon_{x^*x^*} + \varepsilon_{y^*y^*}$. The sum of normal strains is invariant ✔. Putting 253, 307 and −446 back into the transformation equation at −15°, 30° and 75° returns 480, −120 and 80 exactly.

**Principal strains** (added): centre 280 με and $R = \sqrt{27^2 + 446^2} = 447$ με, so $\varepsilon_I = 727$ με and $\varepsilon_{II} = -167$ με. The engineering shear strain is $\gamma_{xy} = 2\varepsilon_{xy} = -893$ με.

![[s2_t6_strain_vs_angle.png|700]]

![[s2_strain_rosettes.png|860]]

> [!tip] Convert to stress for design
> With the socket material's $E$ and $\nu$, use the inverse plane-stress Hooke's law ([[Generalised Hooke's Law]]). Then compare $\sigma_{eq}$ with the yield or fatigue limit ([[FEEG1002 B6 - Yield Criteria]]). Tutorial 8 Q1 runs that full chain.

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 6

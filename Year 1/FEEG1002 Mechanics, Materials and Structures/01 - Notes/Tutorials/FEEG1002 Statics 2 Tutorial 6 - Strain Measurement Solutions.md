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

> [!abstract] Sheet info
> One rosette problem. All three answers match the official solution (253, 307 and $-446$ με), checked numerically; the principal strains and a back-check of all three gauge readings are added.

## Q1 Rosette on a prosthetic socket

*Taught in:* [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#The 0/45/90 rosette]] and [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Rosettes in other axes]] · worked in full at [[FEEG1002 B5 - Strain Measurement and Strain Rosettes#Worked example - prosthetic socket rosette]].

From the sheet's figure, gauge 1 is at $-15^\circ$, gauge 2 at $+30^\circ$ and gauge 3 at $+75^\circ$ to $x$, reading $\varepsilon_1=480$, $\varepsilon_2=-120$ and $\varepsilon_3=80$ με. The gauges are 45° apart.

**Axes along gauge 1.** In $x^*y^*$, with $x^*$ along gauge 1, the layout is a 0/45/90 rosette with gauge 2 at 45° and gauge 3 at 90°:

$$
\varepsilon_{x^*x^*}=\varepsilon_1=480,\qquad \varepsilon_{y^*y^*}=\varepsilon_3=80,\qquad \varepsilon_{x^*y^*}=\varepsilon_2-\tfrac12(\varepsilon_1+\varepsilon_3)=-400\ \mu\varepsilon
$$

**Rotate into xy.** The $x$ axis is 15° anticlockwise from $x^*$, so $\theta=+15^\circ$:

$$
\varepsilon_{xx}=480\cos^215^\circ+80\sin^215^\circ+2(-400)\sin15^\circ\cos15^\circ=253\ \mu\varepsilon
$$

$$
\varepsilon_{yy}=480\sin^215^\circ+80\cos^215^\circ-2(-400)\sin15^\circ\cos15^\circ=307\ \mu\varepsilon
$$

$$
\varepsilon_{xy}=-(480-80)\sin15^\circ\cos15^\circ+(-400)\left(\cos^215^\circ-\sin^215^\circ\right)=-446\ \mu\varepsilon
$$

**Checks.** $\varepsilon_{xx}+\varepsilon_{yy}=560=\varepsilon_{x^*x^*}+\varepsilon_{y^*y^*}$, the strain invariant. Substituting 253, 307 and $-446$ back into the transformation equation at $-15^\circ$, $30^\circ$ and $75^\circ$ returns 480, $-120$ and 80 με exactly.

**Principal strains (added).** The strain circle has centre 280 με and radius $\sqrt{27^2+446^2}=447$ με, so $\varepsilon_I=727$ με and $\varepsilon_{II}=-167$ με, with $\varepsilon_I$ at $\theta_p=-46.7^\circ$ to $x$. The engineering shear strain is $\gamma_{xy}=2\varepsilon_{xy}=-893$ με.

![[s2_t6_strain_vs_angle.png|850]]

With the socket material's $E$ and $\nu$, the inverse plane-stress law would give the stresses ([[FEEG1002 B3 - Generalised Hooke's Law#Stresses from strains|B3]]) and von Mises the equivalent stress ([[FEEG1002 B6 - Yield Criteria|B6]]); Tutorial 8 Q1 runs that full chain.

## Sources

- `Tutorial Sheet 06 - Strain Measurement.pdf` and its solutions.

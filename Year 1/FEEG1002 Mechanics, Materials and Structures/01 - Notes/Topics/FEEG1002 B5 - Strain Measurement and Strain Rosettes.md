---
title: "FEEG1002 B5 - Strain Measurement and Strain Rosettes"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 14
tags: [feeg1002, statics-2, strain-gauges, rosettes, strain-transformation]
aliases: ["Statics 2 Lecture 7", "Strain gauges", "Strain rosette", "Strain transformation"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]", "[[FEEG1002 B3 - Generalised Hooke's Law]]"]
next_topics: ["[[FEEG1002 B6 - Yield Criteria]]"]
key_concepts: ["[[Strain Gauge Rosettes]]", "[[Mohr's Circle]]", "[[Wheatstone Bridge and Strain Gauges]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 07 - Strain Measurement.pdf"]
---

# FEEG1002 B5 - Strain Measurement and Strain Rosettes

> [!abstract] Summary
> Stress cannot be measured directly; strain can. An electrical-resistance **strain gauge** reads the normal strain along one line, $\Delta R/R = k\varepsilon$, usually through a Wheatstone bridge.
> Strains transform with **exactly the same equations** as stresses, provided the tensor shear strain $\varepsilon_{xy} = \gamma_{xy}/2$ is used. A single gauge therefore sees a strain that varies with angle.
> In 2D there are three unknowns ($\varepsilon_{xx}$, $\varepsilon_{yy}$, $\varepsilon_{xy}$), so **three gauges** in known directions (a **rosette**) fix the complete strain state. [[Generalised Hooke's Law]] then turns it into stresses.

## Key Concepts
- [[Strain Gauge Rosettes]] · [[Mohr's Circle]] · [[Wheatstone Bridge and Strain Gauges]]

---

## 1. Strain gauges (L7a)
- In a tensile test the strain is uniform, so $\varepsilon = \Delta L/L$. In general the field is non-uniform, and we need local gradients $\varepsilon_{xx}\approx(u_2 - u_1)/\Delta x$ over tiny distances.
- A foil gauge is a wire zig-zagging back and forth. Stretching it makes it longer and thinner, so its resistance rises:

$$\frac{\Delta R}{R} = k\,\varepsilon_{xx},\qquad k\approx2\ \text{(gauge factor)}$$

- It is read with a **Wheatstone bridge**, either balanced (adjust $R_2$ until $V_G = 0$, so $R_x = R_2R_3/R_1$) or from the out-of-balance voltage. Resolution is about 1 με.
- Watch for **debonding** and **temperature compensation** (thermal strain in the gauge and substrate, [[Thermal Strain]]).
- A gauge is **unidirectional**: it measures the normal strain along its axis only, and **cannot measure shear directly**.

## 2. Strain transformation (L7b)

$$
\varepsilon_{x'x'} = \varepsilon_{xx}\cos^2\theta + \varepsilon_{yy}\sin^2\theta + 2\varepsilon_{xy}\sin\theta\cos\theta
$$

$$
\varepsilon_{x'y'} = -(\varepsilon_{xx}-\varepsilon_{yy})\sin\theta\cos\theta + \varepsilon_{xy}(\cos^2\theta-\sin^2\theta)
$$

- These are identical to the stress equations of [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]].
- **Mohr's circle for strain**: normal strain to the right, $\varepsilon_{xy} = \tfrac12\gamma_{xy}$ positive downwards. It works for both plane stress and plane strain.
- **Principal strains** lie in the same directions as the principal stresses, for an isotropic material.

> [!example] Torsion: measuring shear with normal-strain gauges
> A shaft in torsion is in pure shear, so its Mohr's circle is centred on the origin. Gauges at +45° and −45° read $\varepsilon_I > 0$ and $\varepsilon_{II} = -\varepsilon_I$. Then
>
> $$\varepsilon_{xy} = R = \frac{\varepsilon_I - \varepsilon_{II}}{2}$$
>
> This is how torque transducers work.

## 3. Rosettes (L7c)
Three independent readings give three equations. Align $x$ with one gauge to remove an unknown.

| Rosette | Result |
|---|---|
| 0/45/90° | $\varepsilon_{xx} = \varepsilon_A$, $\varepsilon_{yy} = \varepsilon_B$, $\varepsilon_{xy} = \varepsilon_C - \tfrac12(\varepsilon_A+\varepsilon_B)$ |
| 0/60/120° (delta) | $\varepsilon_{xx} = \varepsilon_A$, $\varepsilon_{yy} = \dfrac{2(\varepsilon_B+\varepsilon_C) - \varepsilon_A}{3}$, $\varepsilon_{xy} = \dfrac{\varepsilon_B-\varepsilon_C}{\sqrt3}$ |

Derivation of the 0/45/90° case: $\varepsilon_C = \varepsilon_{xx}\cos^245^\circ + \varepsilon_{yy}\sin^245^\circ + 2\varepsilon_{xy}\sin45^\circ\cos45^\circ = \tfrac12\varepsilon_A + \tfrac12\varepsilon_B + \varepsilon_{xy}$.

A gauge measures the stretch along a **line**, so $+60^\circ$ and $-120^\circ$ are the same gauge.

![[s2_strain_rosettes.png|900]]

> [!example] Tutorial 6: prosthetic socket, gauges at −15°, 30° and 75° reading 480, −120 and 80 με
> 1. The gauges are 45° apart, so work in $x^*y^*$ aligned with gauge 1:
>    - $\varepsilon_{x^*x^*} = 480$ and $\varepsilon_{y^*y^*} = 80$;
>    - $\varepsilon_{x^*y^*} = -120 - \tfrac12(560) = -400$ με.
> 2. Rotate by $+15^\circ$ into $xy$: $\varepsilon_{xx} = 253$, $\varepsilon_{yy} = 307$, $\varepsilon_{xy} = -446$ με.
>
> Principal strains: $\varepsilon_{I,II} = 280\pm447 = 727, -167$ με.

![[s2_t6_strain_vs_angle.png|680]]

## 4. Full-field methods
Gauges give single points. **Digital image correlation (DIC)** tracks a speckle pattern with cameras (in 3D with stereo-vision) to get the whole displacement field and differentiate it for strain. It is ideal for validating FE models.

## Year 2 bridge
- **Instrumentation**: [[SESA2027 C1 - Sensing Systems, Sensor Principles and Sensor Fusion]] and [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]] cover the bridge circuit, amplification and ADC in detail ([[Wheatstone Bridge and Strain Gauges]], [[Measurement Chain]], [[ADC Quantisation and Resolution]]).
- **Model validation**: strain gauges and DIC are the experimental side of [[Verification and Validation]] and [[Model Updating]] in [[SESA2029 B10 - FE Verification, Validation and Model Updating]].
- **Structural health monitoring**: in-flight wing-root gauges and fatigue load monitoring feed the lifing of [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]] ([[Miner's Rule]]).

## Links
- Previous: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]] · Next: [[FEEG1002 B6 - Yield Criteria]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 6 - Strain Measurement Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]

## Sources
- Statics 2 Lecture 7a–c (strain gauges; strain transformation; rosettes)

---
title: "FEEG1002 B6 - Yield Criteria"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 15
tags: [feeg1002, statics-2, yield, tresca, von-mises, safety-factor]
aliases: ["Statics 2 Lecture 8", "Tresca", "Von Mises", "Equivalent stress", "Limit analysis"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
next_topics: ["[[FEEG1002 C1 - Atoms and Bonding]]"]
key_concepts: ["[[Von Mises and Tresca Yield Criteria]]", "[[Principal Stresses]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]]", "[[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 08 - Yield Criteria.pdf"]
---

# FEEG1002 B6 - Yield Criteria

> [!abstract] Summary
> A tensile test gives one number, $\sigma_Y$. A **yield criterion** reduces any multiaxial stress state to one comparable number. Both classic criteria for **ductile** metals depend on **shear**, not hydrostatic pressure, and are written in principal stresses, so they do not depend on orientation.
> - **Tresca** (maximum shear): $\max(|\sigma_I-\sigma_{II}|, |\sigma_I-\sigma_{III}|, |\sigma_{II}-\sigma_{III}|) = \sigma_Y$. A hexagon in plane stress; conservative.
> - **von Mises** (RMS shear, or distortion energy): $\sigma_{eq} = \sqrt{\sigma_{xx}^2 + \sigma_{yy}^2 - \sigma_{xx}\sigma_{yy} + 3\sigma_{xy}^2} = \sigma_Y$. An ellipse in plane stress; more accurate for most metals.
>
> Linear elasticity then gives the safety factor and the failure load directly: $SF = \sigma_Y/\sigma_{eq}$ and $F_{max} = SF\cdot F$.

## Key Concepts
- [[Von Mises and Tresca Yield Criteria]] · [[Principal Stresses]] · [[Stress Concentration Factor and Factor of Safety]]

---

## 1. The problem (L8a)
- Until now: compare one stress with an allowable value, e.g. $\sigma = F/A$, $My/I$ or $TR/J$.
- The tensile test gives $\sigma_Y$, usually the **0.2% offset** yield strength because the elastic limit is hard to pin down ([[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]).
- How do we compare a 3D stress state with it? The answer is phenomenological, based on experiment, and it depends on the material:
  - **ductile** metals yield by **shear** slip;
  - **brittle** materials fail by **normal** stress.

## 2. Tresca: maximum shear stress (L8a)
- **Observation**: ductile metals in tension slip on 45° planes, where $\tau_{max} = \sigma/2$. At yield in tension, $\tau_{max} = \sigma_Y/2$.
- **Criterion**: yield when the largest shear on **any** plane reaches $\sigma_Y/2$:
$$\tau_{max} = \tfrac12\max\left(|\sigma_I-\sigma_{II}|, |\sigma_I-\sigma_{III}|, |\sigma_{II}-\sigma_{III}|\right) < \frac{\sigma_Y}{2}$$
- **Plane stress** ($\sigma_{III} = 0$), where the out-of-plane shear can govern:
  - same signs: $\max(|\sigma_I|, |\sigma_{II}|) < \sigma_Y$;
  - opposite signs: $|\sigma_I - \sigma_{II}| < \sigma_Y$.
  - Together these form a **hexagon** in the ($\sigma_I$, $\sigma_{II}$) plane.

## 3. von Mises (L8b)
Instead of only the **largest** shear, use the RMS of the maximum shears on the three principal planes. This is equivalent to the distortional strain energy.

$$
\sigma_{eq} = \sqrt{\tfrac12\left[(\sigma_I-\sigma_{II})^2 + (\sigma_I-\sigma_{III})^2 + (\sigma_{II}-\sigma_{III})^2\right]} < \sigma_Y
$$

In plane stress:

$$
\sigma_{eq} = \sqrt{\sigma_I^2 + \sigma_{II}^2 - \sigma_I\sigma_{II}} = \sqrt{\sigma_{xx}^2 + \sigma_{yy}^2 - \sigma_{xx}\sigma_{yy} + 3\sigma_{xy}^2}
$$

- An **ellipse** through the six corners of the Tresca hexagon.
- The two agree for uniaxial and equibiaxial stress and differ most in **pure shear**:
  - Tresca: $\tau_Y = 0.5\sigma_Y$;
  - von Mises: $\tau_Y = \sigma_Y/\sqrt3 = 0.577\sigma_Y$.
  - Measured ratios for Al 1100, 2014, 6061 and AISI 302 steel are 0.575–0.583, which supports von Mises.
- Under von Mises, $\sigma_I$ can exceed $\sigma_Y$ if $\sigma_{II}$ has the same sign (the bulge of the ellipse).

![[s2_yield_loci.png|620]]

## 4. 3D view and limitations
- In principal-stress space the von Mises surface is a **cylinder** around the hydrostatic line $\sigma_I = \sigma_{II} = \sigma_{III}$. Pure hydrostatic stress never causes yield; only the **difference** between principal stresses (distortion) matters.
- **Brittle** materials need different criteria (e.g. maximum principal stress). They are also much stronger in compression than in tension (cast iron, concrete), which breaks the symmetry assumed here. Compare the flat brittle fracture with the 45° ductile shear lip in [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]].

## 5. Limit analysis and safety factor (L8c)
Linear elasticity means **stress ∝ load**, so one analysis at load $F$ is enough.

> [!example] L8: plate with a hole (150 mm wide, 40 mm hole, $t = 10$ mm, $\sigma_Y = 500$ MPa, $F = 150$ kN)
> The FE model gives a peak $\sigma_{eq} = 299.5$ MPa at the hole edge, so
> $$SF = \frac{\sigma_Y}{\sigma_{eq}} = \frac{500}{299.5} = 1.67,\qquad F_{max} = SF\cdot F = 250.4\ \text{kN}$$

![[s2_plate_hole_von_mises.png|560]]

A design safety factor depends on:
- material knowledge and quality control;
- the accuracy of the model and its dimensions;
- whether the application is safety-critical;
- fatigue, which static design ignores;
- standards and codes of practice.

> [!example] Tutorial 7: 36 mm shaft with $F = 200$ kN compression plus torque $T$ ($\sigma_Y = 250$ MPa)
> - $\sigma_{yy} = -196.5$ MPa and $\sigma_{xy} = 2T/\pi R^3$.
> - $\sigma_{eq} = \sqrt{\sigma_{yy}^2 + 3\sigma_{xy}^2} = \sigma_Y$ gives $T = \dfrac{\pi R^3}{2}\sqrt{\dfrac{\sigma_Y^2 - \sigma_{yy}^2}{3}} = 817.5$ N m.

![[s2_t7_torsion_axial_envelope.png|660]]

## Year 2 bridge
- [[Von Mises and Tresca Yield Criteria]] (SESA2029) is the vault's main concept note. Von Mises is the default contour output of the FE software in [[SESA2029 B2 - Linear Elastic FE Analysis - Procedure, Boundary Conditions and Yield]] and the APDL workflows ([[SESA2029 C3 - APDL Workflow - Plate with a Hole (PLANE182 and PLANE183)]] runs the same kind of plate-with-a-hole model in APDL).
- **Thick cylinders and shrink fits** are checked with Tresca or von Mises at the bore ([[SESA2028 S10 - Thick Cylinders and Shrink Fits]]); **spinning discs** at the bore and rim ([[SESA2028 S11 - Spinning Discs]]).
- **Beyond yield**: once yield is predicted, SESA2028 asks whether a crack or fatigue governs first ([[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]], [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]). A static safety factor alone is not a life prediction ([[Goodman Relation]]).
- **Singularities**: a sharp re-entrant corner gives a von Mises peak that grows with mesh refinement ([[Stress Singularities]]). Limit analysis must use a converged, physical stress.

## Links
- Previous: [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]] · Next (Materials): [[FEEG1002 C1 - Atoms and Bonding]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 7 - Yield Criteria Solutions]] · [[FEEG1002 Statics 2 Tutorial 8 - Revision Problems Solutions]]

## Sources
- Statics 2 Lecture 8a–c (Tresca; von Mises; failure load and safety factors)

---
title: "FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 23
tags: [feeg1002, materials, fracture, griffith, stress-intensity, toughness, dbtt]
aliases: ["Materials Lectures 12 and 13", "Griffith fracture", "Fracture toughness"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
next_topics: ["[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
key_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Ductile-to-Brittle Transition]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 12 - Failure of Materials 1 - Brittle vs Ductile and Griffiths.pdf", "02 - Sources/Materials/Lectures/Lecture 13 - Failure of Materials 2 - Fracture Mechanics.pdf"]
---

# FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics

> [!abstract] Summary
> Ductile fracture absorbs energy through plastic flow, void nucleation and coalescence; brittle fracture propagates rapidly by cleavage with little warning. A crack concentrates stress. Griffith balances released elastic energy against new surface energy, while engineering fracture mechanics packages the crack-tip field into $K=Y\sigma\sqrt{\pi a}$ and compares it with $K_{IC}$.

## Key Concepts
- [[Griffith Criterion and Fracture Toughness]] · [[Ductile-to-Brittle Transition]]

---

## 1. Recognising fracture mode

| Ductile | Brittle |
|---|---|
| significant plastic strain and necking | little plastic strain (often $<5\%$) |
| dimpled surface from microvoid coalescence | flat cleavage facets or intergranular path |
| slow/stable crack growth before final overload | rapid, unstable and catastrophic |
| cup-and-cone tensile failure | fracture roughly normal to maximum tensile stress |

Cup-and-cone development: necking concentrates stress; voids nucleate around hard inclusions; voids grow and coalesce into an internal crack; remaining ligaments fail by shear.

## 2. Stress concentration at a sharp flaw
For an elliptical crack/notch the local peak scales approximately as

$$\sigma_m\approx2\sigma_0\sqrt{\frac{a}{\rho_t}}$$

so a longer crack ($a\uparrow$) or sharper tip ($\rho_t\downarrow$) intensifies stress. Perfectly sharp elastic cracks imply a singular local stress, so the physically useful parameter is the amplitude of the crack-tip field.

## 3. Griffith energy balance
For a central through-crack of total length $2a$ in a thin, ideally brittle plate:
- forming two new crack faces costs surface energy $U_S=4a\gamma$ per unit thickness;
- crack growth releases elastic strain energy proportional to $\sigma^2\pi a^2/E$.

Instability occurs when the energy released by a small extension equals/exceeds the energy needed for new surface:

$$\sigma_f=\sqrt{\frac{2E\gamma}{\pi a}}$$

Thus fracture stress varies as $a^{-1/2}$: once an unstable crack grows, progressively less applied stress is needed.

## 4. Stress intensity and fracture toughness
Mode-I crack opening is described by

$$K_I=Y\sigma\sqrt{\pi a}$$

- $Y$: dimensionless geometry/loading factor;
- $a$: crack-size definition consistent with that $Y$;
- failure when $K_I=K_C$;
- $K_{IC}$ is the plane-strain fracture toughness, a conservative material property when linear-elastic conditions and sufficient thickness hold.

Rearrangements used in design:

$$\sigma_f=\frac{K_{IC}}{Y\sqrt{\pi a}},\qquad a_c=\frac1\pi\left(\frac{K_{IC}}{Y\sigma}\right)^2$$

![[m8_fracture_toughness.png|760]]

> [!example] X-ray detection limit in the tutorial
> An internal crack of total length 1.6 mm has $a=0.8$ mm. With $K_C=65$ MPa$\sqrt{\text m}$ and $Y=1$,
>
> $$\sigma_f=\frac{65}{\sqrt{\pi(0.8\times10^{-3})}}=1.30\ \text{GPa}$$
>
> This exceeds the 375 MPa yield strength, so the plate generally yields before the LEFM fast-fracture prediction is reached. Once widespread plasticity occurs, the linear-elastic $K$ calculation is no longer sufficient.

## 5. Ductile-to-brittle transition (DBTT)
- Ideal brittle-fracture stress is comparatively temperature-insensitive.
- FCC yield stress is weakly temperature-dependent because many close-packed slip systems operate.
- BCC/HCP dislocation glide becomes difficult at low temperature, so $\sigma_y$ rises.
- When $\sigma_y$ rises above the fracture stress, cleavage occurs before plastic relaxation: the material becomes brittle.

Effects on DBTT:
- solution, precipitation and work hardening raise $\sigma_y$ without equivalent fracture improvement $\rightarrow$ transition temperature rises;
- grain refinement raises yield strength **and** impedes cleavage $\rightarrow$ transition temperature falls.

Charpy impact energy measures absorbed energy and reveals the transition curve; it is not $K_{IC}$.

> [!warning] Validity before arithmetic
> Confirm crack definition, geometry factor, units, mode and LEFM validity. Fracture toughness is not the area under a tensile stress-strain curve.

## Links
- Previous: [[FEEG1002 C7 - Steels and Precipitation Hardening]] · Next: [[FEEG1002 C9 - Fatigue, Creep and Corrosion]]
- Worked problems: [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]

## Sources
- Materials Lectures 12–13; audited against [[FEEG1002 Materials L12 Contact Sheet.png]] and [[FEEG1002 Materials L13 Contact Sheet.png]].

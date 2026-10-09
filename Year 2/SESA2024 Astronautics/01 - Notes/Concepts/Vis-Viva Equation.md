---
title: "Vis-Viva Equation"
module: "SESA2024 Astronautics"
type: concept
stream: "Mission Analysis"
aliases: ["energy equation", "orbital energy", "specific orbital energy", "escape velocity", "circular velocity"]
tags: [sesa2024, concept, orbital-mechanics]
status: complete
parent_lectures: ["[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]"]
related_concepts: ["[[Hohmann Transfer]]", "[[Orbital Angular Momentum]]", "[[Orbit Equation and Conic Sections]]"]
sources: ["02 - Sources/Lectures/Chapter 5/SESA2024 Astronautics - Chapter 5_Orbital energy_V1.pdf"]
---

# Vis-Viva Equation

## Definition

> [!note] Definition
> $$\varepsilon = \frac{V^2}{2}-\frac{\mu}{r} = -\frac{\mu}{2a}\qquad\Longleftrightarrow\qquad V^2 = \mu\left(\frac2r-\frac1a\right)$$
> This holds for **all conics**. It is given on every recent exam formula sheet.

## Explanation
- Gravity is conservative: $KE+PE$ is constant, with $PE = -\mu m/r$ (zero at infinity).
- $\varepsilon = -\mu/2a$ follows from $r_pV_p = r_aV_a$ (workbook Ch5 Q2).
- **Special speeds**:
  - circular: $V_c = \sqrt{\mu/r}$;
  - escape: $V_{esc} = \sqrt{2\mu/r}$;
  - $V_p = \sqrt{\dfrac{2\mu r_a}{r_p(r_p+r_a)}}$ and $V_a = \sqrt{\dfrac{2\mu r_p}{r_a(r_p+r_a)}}$.
- **At a common point, the larger orbit is the faster one.** A tangential burn therefore raises the opposite side of the orbit.
- Given $(r, V)$ you get $a$; given an apsis as well, you get $e$.

## Examples
- 200 km circle: 7.784 km/s. Ellipse to 40 000 km: $V_p$ = 10.302 and $V_a$ = 1.461 km/s.
- Missile or satellite? $r_a$ = 7378 km and $V$ = 5.589 km/s give $a$ = 5189 km and $r_p$ = 3000 km < $R_E$, so a **missile**.
- Starship IFT-2: apogee at 148 km with 6760 m/s gives $a$ = 5213 km, suborbital.

![[ast_visviva_speed.png|620]]

## Related
- [[Hohmann Transfer]] · [[Orbital Angular Momentum]] · [[Orbit Equation and Conic Sections]]

## Year 1 foundation
- Energy plus angular momentum between perigee and apogee: [[FEEG1002 D5 - Angular Impulse and Momentum]].

## Sources
- Chapter 5 Lectures 9–10

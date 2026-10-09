---
title: "FEEG1002 A9 - Shear Stresses in Beams"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 9
tags: [feeg1002, statics, beams, shear-stress, first-moment-of-area]
aliases: ["Statics 1 Lecture 14", "Shear stress in beams", "tau = QAy/Ib"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]]"]
next_topics: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
key_concepts: ["[[Shear Stress Distribution in Beams]]", "[[First Moment of Area]]", "[[Shear Flow]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 14 - Shear Stresses in Beams.pdf"]
---

# FEEG1002 A9 - Shear Stresses in Beams

> [!abstract] Summary
> The shear force $Q$ is the resultant of shear stresses $\sigma_{yx}$ acting on the cut face. By moment equilibrium of a small element, equal **complementary** shear stresses $\sigma_{xy}$ must act on horizontal planes. When $M$ varies along the beam, the bending stress differs on the two ends of a longitudinal strip. Only a horizontal shear stress on the strip's inner face can balance the difference, which gives
>
> $$\tau = \sigma_{xy} = \frac{Q\,A_s\bar y}{I\,b}$$
>
> For a rectangle this is a **parabola**, zero at the surfaces and $\tfrac32\tau_{avg}$ at the neutral axis: exactly where the bending stress is zero.

## Key Concepts
- [[Shear Stress Distribution in Beams]] · [[First Moment of Area]] · [[Shear Flow]]

---

## 1. Four loading cases for slender members (L14a)

| Loading | Stress |
|---|---|
| Tension | $\sigma_{xx} = F/A$ |
| Pure bending | $\sigma_{xx} = My/I$ |
| Torsion | $\tau = Tr/J$ |
| Transverse shear | $\sigma_{xy} = QA_s\bar y/Ib$ (this lecture) |

## 2. Why horizontal shear exists
- **Complementary shear**: an element with shear on its vertical faces only would spin. Moment equilibrium demands $\sigma_{xy} = \sigma_{yx}$.
- **Solid block vs a stack of loose strips** under the same load: loose strips slide over each other, the ends become stepped (plane sections do **not** stay plane), and the stack is far more flexible. Leaf springs exploit this. The shear stress transmitted between layers is what makes a solid beam stiff.

## 3. Derivation (L14b)
Take a beam element $dx$ carrying constant $Q$ but with $M$ changing to $M + \frac{dM}{dx}dx$. Isolate the strip of area $A_s$ **below** level $y$:

$$
\int_{A_s}\sigma_{xx}\,dA + \sigma_{xy}\,b\,dx = \int_{A_s}\left(\sigma_{xx} + \frac{\partial\sigma_{xx}}{\partial x}dx\right)dA
$$

Using $\partial\sigma_{xx}/\partial x = (dM/dx)\,y/I = Qy/I$:

$$
\boxed{\sigma_{xy} = \frac{Q}{Ib}\int_{A_s}y\,dA = \frac{Q\,A_s\bar y}{I\,b}}
$$

- $A_s\bar y$ is the [[First Moment of Area]] of the area *beyond* level $y$ about the neutral axis. $b$ is the width *at* level $y$.
- Strictly exact only for constant $Q$, but accurate for slender beams.

## 4. Rectangular section (L14c)
With $A_s = b(d/2 - y)$ and $\bar y = \tfrac12(d/2 + y)$:

$$
\sigma_{xy} = \frac{6Q}{bd^3}\left(\frac{d^2}{4} - y^2\right) = \frac32\,\frac{Q}{A}\left[1 - \left(\frac{y}{d/2}\right)^2\right]
$$

Define the shear stress coefficient $K$ by $\tau_{max} = K\tau_{avg}$:

| Section | $K$ |
|---|---|
| Rectangle | 3/2 |
| Solid circle | 4/3 |
| Thin-walled tube | 2 |

![[s1_beam_shear_stress.png|940]]

## 5. Which stress governs?
For a rectangular cantilever with end load $F$:

$$
\sigma_{xx,max} = \frac{6FL}{bd^2}\ (y = \pm d/2),\qquad \sigma_{xy,max} = \frac{3F}{2bd}\ (y = 0),\qquad \frac{\sigma_{xx,max}}{\sigma_{xy,max}} = \frac{4L}{d}
$$

For a slender beam ($L/d\sim10$) bending stress is about 40× the shear stress, so shear rarely causes failure. It **does** govern:
- glued laminates, where the glue line sits at the neutral axis;
- welds, rivets and screws joining flanges to webs;
- short deep beams;
- thin webs.

> [!example] Tutorial 6 Q3: two 50 mm square timbers glued, $F = 2$ kN at midspan, $L = 1.5$ m
> - $Q = F/2$ everywhere, so $\tau_{glue} = \tfrac32\dfrac{F/2}{2d^2} = 0.30$ MPa.
> - Shear flow along the glue line: $\tau d = 15$ kN/m.
> - Screws with a 4 mm core and $\tau_{allow} = 200$ MPa carry 2.51 kN each, so about 6 per metre are needed: spacing **16.7 cm**.

> [!note] I-beams need more
> In an I-beam most of the shear force is carried by the **web**, and the flanges carry horizontal shear flow. The simple formula with $b = t_w$ gives the web distribution. The flange behaviour is deferred to Year 2.

## Year 2 bridge
- [[SESA2028 S3 - Shear Flow and Shear Centre]] turns $\tau$ into **shear flow** $q = \tau t$ for thin-walled sections, $q(s) = -\frac{Q}{I}\int_0^s ty\,ds$. That is the same first-moment-of-area integral, run around the wall from a free edge ([[Shear Flow]]).
- For sections that are not symmetric about the load line, the shear force must pass through the [[Shear Centre]] to avoid twisting. A channel does not twist only if loaded through a point outside its web.
- Combined $\sigma_{xx}$ and $\sigma_{xy}$ at one point form a 2D stress state. The principal stresses and a yield check ([[FEEG1002 B4 - Stress Transformation and Mohr's Circle]], [[FEEG1002 B6 - Yield Criteria]]) decide failure where both are significant, e.g. at a flange–web junction.

## Links
- Previous: [[FEEG1002 A8 - Torsion of Circular Shafts]] · Next (Statics 2): [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 6 - Buckling, Torsion and Shear Stress Solutions]]

## Sources
- Statics 1 Lecture 14a–c (introduction; derivation; rectangular example)

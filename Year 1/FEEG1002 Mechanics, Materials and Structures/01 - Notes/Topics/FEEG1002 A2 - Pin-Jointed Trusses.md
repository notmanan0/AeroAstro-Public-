---
title: "FEEG1002 A2 - Pin-Jointed Trusses"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 2
tags: [feeg1002, statics, trusses, method-of-joints, method-of-sections, truss-deformation]
aliases: ["Statics 1 Lecture 3", "Statics 1 Lecture 4", "Trusses", "Method of Joints", "Method of Sections"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]"]
key_concepts: ["[[Method of Joints and Method of Sections]]", "[[Static Determinacy]]", "[[Williot Displacement Diagram]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 03 - Pin-Jointed Trusses, Method of Joints.pdf", "02 - Sources/Statics 1/Lectures/Lecture 04 - Pin-Jointed Trusses, Method of Sections.pdf"]
---

# FEEG1002 A2 - Pin-Jointed Trusses

> [!abstract] Summary
> A truss is a set of straight bars joined at pins. With friction-free pins and loads applied **only at the joints**, each bar is a **two-force member** carrying pure axial tension or compression and no moment.
> - **Method of joints**: isolate one joint at a time (two equations per joint).
> - **Method of sections**: cut through up to three bars and use moments to isolate one unknown at a time.
> - **Determinacy**: $2j = r + m$ tells you whether statics alone is enough.
> - **Deformation**: once the bar forces are known, $\Delta L = FL/EA$ for each bar. Compatibility at the pins (the displacement or Williot diagram) then gives the joint displacements.

## Key Concepts
- [[Method of Joints and Method of Sections]] · [[Static Determinacy]] · [[Williot Displacement Diagram]] · [[Free Body Diagram and Equilibrium]]

---

## 1. Model assumptions (L3a)
- Every member is a straight **bar** joined to others by **frictionless pins**, so a member carries no moment and only an axial force.
- External loads and reactions act **only at joints**. A load mid-bar would bend it, and the member would then have to be treated as a beam ([[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]).
- Deformations are **small**, so equilibrium is written on the undeformed geometry.
- Self-weight is usually neglected. That is fine for a bike frame but not always for a bridge.

**Sign convention.** Replace each cut bar by a force drawn **away from the joint**, i.e. assume tension. A negative answer means **compression**: the bar pushes on the joint.

## 2. Method of joints (L3b)
1. Draw the FBD of the whole truss and find the reactions.
2. Start at a joint with **at most two unknown** bar forces.
3. Apply $\sum F_H = 0$ and $\sum F_V = 0$ at that joint. Move on to the next joint whose unknowns are now down to two.

> [!example] L3 three-bar truss (A = wall roller, B = pin, 200 N upwards at C, $\theta = \tan^{-1}(5/10) = 26.6^\circ$)
> - Reactions: $V_B = -200$ N (it acts downwards), $H_B = 400$ N, $H_A = -400$ N.
> - Joint C: $\sin\theta\,F_{BC} + 200 = 0$ gives $F_{BC} = -447$ N (compression). Then $F_{AC} = -\cos\theta\,F_{BC} = +400$ N (tension).
> - Joint B: $F_{AB} = 0$. AB is a **zero-force member**, but it still holds joint A in place if the load ever reverses.

![[s1_truss_three_bar_forces.png|720]]

## 3. Method of sections (L4a)
Best when only a few bar forces are wanted in a big truss.
1. Find the reactions from the whole-truss FBD.
2. Cut through **no more than three** bars (and never through a joint). Replace the cut bars by tensile forces.
3. Use $\sum M$ about the point where **two of the unknown bar lines meet**, so the third force is the only unknown. Then use $\sum F_V$ or $\sum F_H$ for a bar whose partners are both parallel to the other direction.

> [!example] L4 example: $F$ at the centre of a five-joint truss
> - Reactions are $F/2$ at A and C.
> - $\sum M_B$: $-(2L)(F/2) - LF_{ED} = 0$, so $F_{ED} = -F$.
> - $\sum F_V$: $F_{EB}\sin45^\circ = F/2$, so $F_{EB} = \tfrac{\sqrt2}{2}F$.
> - $\sum M_E$: $F_{AB} = +F/2$.
>
> Sanity check: the top chord of a simply supported truss is squeezed and the bottom chord stretched, just like the top and bottom fibres of a sagging beam.

![[s1_truss_method_of_sections.png|860]]

![[s1_t2_q2_warren_truss.png|860]]

## 4. Mechanisms, determinate and indeterminate trusses (L4b)
For a plane pin-jointed frame with $j$ joints, $r$ reaction components and $m$ members:

$$
2j = r + m\ \text{(statically determinate)},\qquad r+m < 2j\ \text{(mechanism)},\qquad r+m>2j\ \text{(statically indeterminate)}
$$

- A **mechanism** moves without the bars stretching and cannot carry general loads. That is useful in machines, fatal in structures.
- An **indeterminate** frame has redundant members. It will still stand if one bar is removed, which helps safety. Its bar forces depend on the bar stiffnesses, and a misfit bar causes assembly stresses. Solving it needs compatibility, which is not covered in FEEG1002.
- The test is **necessary but not sufficient**: a frame can pass it while one bay is over-braced and another is a mechanism. Always look at the geometry.

![[s1_truss_static_determinacy.png|900]]

## 5. Truss deformation (L4c)
1. Find each bar's extension from its force: $\Delta L = \dfrac{FL}{EA}$.
2. The bars must stay pinned together (**compatibility**). Rotate each bar about its fixed end with its new length and find where the arcs intersect.
3. Displacements are tiny compared with the bar lengths, so replace each arc by a **straight line perpendicular to the bar**. This is the displacement (Williot) diagram.

For the L3 truss ($A = 10^{-4}$ m², $E = 70$ GPa): $\Delta L_{AC} = +571\ \mu$m and $\Delta L_{BC} = -714\ \mu$m. Then

$$
\Delta X_C = \Delta L_{AC} = 571\ \mu\text{m},\qquad \Delta Y_C = \frac{\cos\theta\,\Delta L_{AC} + |\Delta L_{BC}|}{\sin\theta} = 2.74\ \text{mm (upwards)}
$$

The lecture gives only the formula; the number here comes from solving $\mathbf u_C\cdot\mathbf e_{AC} = \Delta L_{AC}$ and $\mathbf u_C\cdot\mathbf e_{BC} = \Delta L_{BC}$.

![[s1_williot_displacement.png|880]]

> [!tip] Why the vertical displacement is so much larger
> Bars AC and BC meet at only 26.6°. Small length changes along two nearly parallel directions pin down the joint position badly in the direction normal to them, which amplifies the displacement by about $1/\sin\theta$. Shallow trusses are floppy.

## 6. Design implications
- A bar in compression usually fails by **buckling** long before it yields ([[FEEG1002 A7 - Euler Buckling of Struts]]).
- Arrange the long diagonals so they carry **tension**. L12 asks which way round to put the braces: the long members should be in tension.
- A truss puts its material where the loads flow, giving a high stiffness-to-weight ratio. Wing ribs and space frames use the same logic.

## Year 2 bridge
- **Energy methods replace the displacement diagram.** In [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] the [[Unit Load Method]] gives $\delta = \sum \dfrac{F\,f\,L}{EA}$ for any joint in any direction, with no geometric construction. It reproduces the 2.74 mm above.
- **Indeterminate trusses** are solved in [[SESA2028 S8 - Virtual Work and Castigliano Theorems]] by making a redundant bar force satisfy compatibility ([[Castigliano Second Theorem]]).
- **The Matrix Displacement Method** ([[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]]) assembles the bar stiffness $EA/L$ into $\mathbf K\mathbf u = \mathbf F$ ([[Global Stiffness Matrix Assembly]]). It handles determinate and indeterminate trusses the same way.

## Links
- Previous: [[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]] · Next: [[FEEG1002 A3 - Shear Force and Bending Moment Diagrams]]
- Worked problems: [[FEEG1002 Statics 1 Tutorial 2 - Trusses Solutions]]

## Sources
- Statics 1 Lectures 3a–b (pin-jointed trusses, method of joints) and 4a–c (method of sections; mechanisms and indeterminacy; truss deformation)

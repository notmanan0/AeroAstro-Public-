---
title: "FEEG1002 A1 - Forces, Equilibrium, Stress and Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part A: Statics 1"
order: 1
tags: [feeg1002, statics, equilibrium, free-body-diagram, stress, strain]
aliases: ["Statics 1 Lecture 1", "Statics 1 Lecture 2", "Forces and Equilibrium", "Stress and Strain"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1002 A2 - Pin-Jointed Trusses]]"]
key_concepts: ["[[Free Body Diagram and Equilibrium]]", "[[Stress, Strain and Young's Modulus]]", "[[Stress Concentration Factor and Factor of Safety]]"]
tutorial_sheets: ["[[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]]"]
sources: ["02 - Sources/Statics 1/Lectures/Lecture 01 - Forces and Equilibrium.pdf", "02 - Sources/Statics 1/Lectures/Lecture 02 - Stress and Strain.pdf"]
---

# FEEG1002 A1 - Forces, Equilibrium, Stress and Strain

> [!abstract] Summary
> Every structural question in this module asks two things: **is it strong enough?** and **does it deform too much?** Both start with the forces. A **free body diagram (FBD)** isolates the body and replaces its supports with reactions. For a static body the resultant force and moment are zero, which gives three equations in 2D. Forces become **stress** $\sigma = F/A$ once divided by area, so a failure limit becomes a property of the material rather than of the part. Deformation becomes **strain** $\varepsilon = \Delta L/L_0$. For a linear elastic bar, $\sigma = E\varepsilon$ links the two, and the bar behaves like a spring of stiffness $EA/L$.

## Key Concepts
- [[Free Body Diagram and Equilibrium]] · [[Stress, Strain and Young's Modulus]] · [[Stress Concentration Factor and Factor of Safety]]

---

## 1. Forces on bodies (L1a)

- **Newton's third law**: the force of A on B is equal in size and opposite in direction to the force of B on A. Support reactions exist because of this law.
- **External forces** act on the body from outside, e.g. gravity, supports and other bodies. **Internal forces** act between parts of the body, e.g. the tension in a crane cable.
- Where you draw the FBD boundary decides which forces are external. Cut through the cable and its tension becomes external to the part you kept, which is how internal forces are revealed.

### FBD procedure
1. Isolate the object of interest from its surroundings.
2. Replace every support by its reaction forces and/or moments.
3. Draw unknown reactions in an assumed positive direction. A negative answer simply means the force acts the other way.

![[s1_support_types.png|760]]

| Support | Prevents | Reactions |
|---|---|---|
| Pinned | $x$ and $y$ translation | $R_x$, $R_y$ |
| Roller / slider | translation normal to the surface | $R_y$ only; it can be up **or down** |
| Built-in (fixed) | translation and rotation | $R_x$, $R_y$, $M$ |

## 2. Equilibrium (L1a–b)

Statics means **no acceleration** (Newton's first law). The *resultant* external force and moment must therefore be zero:

$$
\sum F_V = 0,\qquad \sum F_H = 0,\qquad \sum M_A = 0\quad\text{(about any point A)}
$$

- These are the three independent equations for a 2D rigid body, so at most **three unknown reactions** can be found by statics alone. See [[FEEG1002 A6 - Statically Indeterminate Beams]] for what happens when there are more.
- Choose the moment point so that as many unknowns as possible pass through it. Each unknown whose line of action passes through the point drops out.
- Pick a positive direction for each sum and stick to it.

> [!example] L1 example 3: portal crane with an off-centre load
> The load $F_G$ sits at distance $b$ from support A and $c$ from support B. Taking moments about A gives $(b+c)F_B = bF_G$, so
>
> $$F_B = \frac{b}{b+c}F_G,\qquad F_A = \frac{c}{b+c}F_G$$
>
> The support **nearer** the load carries more of it (the lever rule). With $b = c$, each support carries $F_G/2$.

![[s1_crane_tipping_fbd.png|820]]

> [!example] Tutorial 1 Q1: crane tipping (see [[FEEG1002 Statics 1 Tutorial 1 - Forces, Equilibrium, Stress and Strain Solutions]])
> The crane tips when the rear-axle reaction $F_B$ falls to zero, so take moments about the front axle A:
>
> $$4F_{g,\text{box}} - 3F_{g,\text{crane}} + 5F_B = 0 \;\Rightarrow\; m_{box,max} = \tfrac34(5000) = 3750\ \text{kg}$$

## 3. Stress (L2a)

Force alone cannot tell you whether a part breaks: a bar twice as wide carries twice the force. Normalise by area:

$$
\sigma = \frac{F}{A}\quad[\text{Pa} = \text{N/m}^2],\qquad \tau = \frac{F_{shear}}{A}
$$

- $\sigma$ is **positive in tension** and negative in compression. $\tau$ is shear stress, which acts in the plane of the cut.
- **Design stress**: $\sigma_{max,design} = \sigma_{max,material}/K_{SF}$ with safety factor $K_{SF} > 1$. Typical values: A36 steel has $\sigma_y = 250$ MPa and UTS 400 MPa; an aluminium alloy has $\sigma_y = 400$ MPa and UTS 500 MPa.
- **Stress is local**, $\sigma(x,y) = \delta F/\delta A$. Abrupt geometry changes concentrate it: $\sigma_{max} = K_T\,\sigma_{mean}$, and $K_T = 3$ for a small hole in a wide plate.

![[s1_stress_concentration_hole.png|640]]

- **Double shear.** In a pinned hinge (fork and eye) the pin must shear on **two** planes before it can pull out, so each plane carries $F/2$. Tutorial 1 Q2 designs the rod and pin to be equally strong: rod $D = 4.0$ mm, pin $D = 3.6$ mm.
- On a general cut the stress is a **vector** with a normal component and two shear components. Describing that properly needs the stress tensor of [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]].

## 4. Strain and Hooke's law (L2b)

$$
\varepsilon = \frac{\Delta L}{L_0}\ (\text{dimensionless}),\qquad \sigma = E\varepsilon,\qquad F = \frac{EA}{L}\,\Delta L
$$

- Strain removes the size effect: a bar twice as long stretches twice as far at the **same** strain.
- The Young's modulus $E$ is the slope of the linear elastic part of the stress–strain curve. It is an intrinsic **material** property (see [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]).
- $EA/L$ is the axial stiffness, and a bar is exactly a spring. This is the building block for truss deformation in [[FEEG1002 A2 - Pin-Jointed Trusses]].
- **Poisson's ratio**: $\varepsilon_{yy} = \varepsilon_{zz} = -\nu\,\varepsilon_{xx}$. A stretched bar gets thinner.
- **Shear strain**: $\gamma = \Delta S/H_0 = \tan\varphi\approx\varphi$. Then $\tau = G\gamma$, with shear modulus $G = \dfrac{E}{2(1+\nu)}$.

![[s1_stress_strain_definitions.png|820]]

> [!warning] Scope
> $\sigma = E\varepsilon$ in this form holds only for **uniaxial** stress in a linear elastic material. With stresses in two or three directions, the Poisson coupling adds terms. That is the generalised Hooke's law of [[FEEG1002 B3 - Generalised Hooke's Law]].

> [!example] Tutorial 1 Q3: bolt clamping force
> For a 6 mm bolt, 350 mm long, with $E = 209$ GPa and 0.5 mm pitch, carrying 4000 N:
> - $\sigma = 141.5$ MPa and $\varepsilon = 6.77\times10^{-4}$;
> - $\Delta L = 0.237$ mm, so the nut needs $0.47\approx\tfrac12$ turn.
>
> Real plates compress too. The bolt then stretches less for the same number of turns, so more turning is needed.

## Year 2 bridge

| FEEG1002 idea | Where it grows in Year 2 |
|---|---|
| FBD, three equilibrium equations | Every structures topic, starting with [[SESA2028 S1 - Section Properties and Unsymmetrical Bending]]. In [[SESA2027 A1 - Dynamic Systems and Aircraft Equations of Motion]] the resultant is no longer zero: $\sum F = m\dot v$ |
| $\sigma = F/A$, safety factor, $K_T$ | [[Stress Concentration Factor and Factor of Safety]] (SESA2029 FEA). In [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]] a crack is the extreme stress raiser |
| $F = (EA/L)\Delta L$ | Bar strain energy $U = F^2L/2EA$ in [[SESA2028 S7 - Strain Energy and Conservation of Energy]]; the bar stiffness matrix in [[SESA2029 B1 - Introduction to FEA and the Matrix Displacement Method]] |
| $G = E/2(1+\nu)$ | Torsion in [[SESA2028 S4 - Torsion of Thin-Walled Sections]] |

## Links
- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Next: [[FEEG1002 A2 - Pin-Jointed Trusses]]
- Formula summary: [[FEEG1002 Formula Sheet]]

## Sources
- Statics 1 Lectures 1a–b (Forces and equilibrium) and 2a–b (Stress; Strain and 1D Hooke's law)

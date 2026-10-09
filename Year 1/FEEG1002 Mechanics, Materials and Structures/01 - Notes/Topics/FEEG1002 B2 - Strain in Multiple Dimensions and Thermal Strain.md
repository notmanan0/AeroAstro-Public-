---
title: "FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 11
tags: [feeg1002, statics-2, strain, shear-strain, volumetric-strain, thermal-strain]
aliases: ["Statics 2 Lecture 2", "Statics 2 Lecture 3", "Strain components", "Thermal stress"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]]"]
next_topics: ["[[FEEG1002 B3 - Generalised Hooke's Law]]"]
key_concepts: ["[[Strain Components and Volumetric Strain]]", "[[Thermal Strain]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 02 - Strain in Multiple Dimensions.pdf", "02 - Sources/Statics 2/Lectures/Lecture 03 - Thermal Strains.pdf"]
---

# FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain

> [!abstract] Summary
> Strain measures **deformation**: relative movement of neighbouring points. It is the displacement **gradient**, so a rigid-body translation or rotation produces none.
> - Normal strains $\varepsilon_{xx} = \partial u_x/\partial x$ are stretches.
> - Shear strains $\gamma_{xy} = \partial u_x/\partial y + \partial u_y/\partial x$ are the loss of a right angle. The tensor shear strain is $\varepsilon_{xy} = \gamma_{xy}/2$.
> - Small-strain volume change is $\varepsilon_{vol} = \varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$.
>
> A temperature change produces an isotropic **thermal strain** $\alpha\Delta T$. It is stress-free if the body can expand; if it is constrained, superposition of free expansion and mechanical correction gives the stress.

## Key Concepts
- [[Strain Components and Volumetric Strain]] · [[Thermal Strain]]

---

## 1. Normal strain and volume change (L2a)
- Bar in tension: $\varepsilon_L = \Delta L/L_0 > 0$ and $\varepsilon_W = \Delta W/W_0 < 0$ (Poisson contraction).
- 3D element: $\varepsilon_{xx} = \Delta L_x/L_{x0}$, and likewise in $y$ and $z$.
- **Volumetric strain**:
$$\varepsilon_{vol} = \frac{V - V_0}{V_0} = (1+\varepsilon_{xx})(1+\varepsilon_{yy})(1+\varepsilon_{zz}) - 1 \approx \varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$$
  The products are second order, which is the small-strain assumption.
- **Strain is local**, so in a non-uniform field $\varepsilon_{xx} = \dfrac{du_x}{dx}$. Equal displacement everywhere means pure translation, and no strain.
- **Magnitudes are tiny**: an aluminium alloy with $E = 70$ GPa at yield (250 MPa) is at $\varepsilon = 0.0036 = 0.36\% = 3600\ \mu\varepsilon$.

## 2. Shear strain (L2b)

![[s2_strain_definitions.png|900]]

- The engineering shear strain is the **decrease** in the angle between the $x$ and $y$ faces:
$$\gamma_{xy} = \alpha + \beta = \frac{\partial u_x}{\partial y} + \frac{\partial u_y}{\partial x}$$
- $\gamma_{xy} > 0$ means the angle between the left and bottom faces gets smaller.
- **Rigid rotation**: $\alpha$ and $\beta$ are equal and opposite, so $\gamma_{xy} = 0$. No deformation.
- Shear alone changes **no volume** (a deck of cards sliding).
- **Tensor shear strain**: $\varepsilon_{xy} = \tfrac12\gamma_{xy}$, the symmetric deformation of each face with rotation removed. **Watch the factor of 2.** Transformation equations and Mohr's circle use $\varepsilon_{xy}$, not $\gamma_{xy}$ ([[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]).
- 3D: three normal strains and three shear strains, $\varepsilon_{xy}$, $\varepsilon_{xz}$, $\varepsilon_{yz}$.

## 3. Thermal strain (L3a)

$$
\varepsilon_T = \frac{\delta_T}{L_{ref}} = \alpha\,(T - T_{ref}),\qquad \alpha\ \text{in}\ \text{K}^{-1}
$$

- It is **isotropic**: $\varepsilon_{xx} = \varepsilon_{yy} = \varepsilon_{zz} = \varepsilon_T$. The body scales up uniformly and there is no thermal shear.
- **Stress-free if unconstrained.** Stress appears only when the expansion is resisted.
- **Fully constrained bar**:
$$\delta_T + \delta_F = \alpha\Delta TL + \frac{FL}{EA} = 0\;\Rightarrow\;\sigma = -E\alpha\Delta T$$
  This does not depend on the length or the area.

### Superposition recipe
1. Release the constraint and let each part expand freely by $\alpha\Delta TL$.
2. Apply the unknown forces that restore compatibility, each giving $FL/EA$.
3. Solve:
   - **compatibility** (total lengths or gaps);
   - **equilibrium**: parts **in series** carry the **same force**; parts **in parallel** (bonded side by side) have forces that **sum to zero** and **equal** total extensions.

> [!example] L3 rail: 10 m steel rails ($E = 200$ GPa, $\alpha = 11.7\times10^{-6}$/°C) laid at 6 °C with 3 mm gaps; find the stress at 48 °C
> - Free expansion $\delta_T = 11.7\times10^{-6}(42)(10) = 4.9$ mm, more than the 3 mm gap.
> - So the rail must be compressed by 1.9 mm: $\sigma = \dfrac{E}{L}\delta_F = \dfrac{200\times10^9}{10}(-0.0019) = -38$ MPa.
> - The rail is stress-free until the gap closes at 31.6 °C. Too much compression and the track **buckles** ([[FEEG1002 A7 - Euler Buckling of Struts]]).

![[s2_thermal_rail.png|880]]

> [!example] Tutorial 2 Q1: aluminium shell bonded to a brass core, heated by 180 °C
> - $\alpha_{Al} > \alpha_{brass}$: the shell wants to grow more but is held back, so it goes into compression while the core is stretched.
> $$F_{Al}\left(\frac{1}{A_{Al}E_{Al}} + \frac{1}{A_{Br}E_{Br}}\right) = (\alpha_{Br} - \alpha_{Al})\Delta T$$
> - Result: $\sigma_{Al} = -8.15$ MPa and $\sigma_{core} = +38.8$ MPa. With a stiffer, lower-$\alpha$ steel core, $\sigma_{Al} = -56.2$ MPa.

![[s2_t2_bimaterial_thermal.png|700]]

## Year 2 bridge
- **Thermal stress in hot sections**: turbine discs and blades see large temperature gradients. [[SESA2028 S11 - Spinning Discs]] and the thermal barrier coatings of [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]] ([[Thermal Barrier Coatings]]) have to cope with $\alpha$ mismatch between coating and substrate.
- **Shrink fits** ([[Shrink Fit]], [[SESA2028 S10 - Thick Cylinders and Shrink Fits]]) exploit thermal strain deliberately. The **interference** there plays the role of the rail gap: a compatibility condition fixes the contact pressure.
- **Strain–displacement relations** in polar form, $\varepsilon_r = du/dr$ and $\varepsilon_\theta = u/r$ ([[Polar Strain-Displacement Relations]]), and [[Strain Compatibility]] extend §1–2 to axisymmetric bodies ([[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]]).
- **Spacecraft**: the thermal cycling of structures in sunlight and eclipse ([[SESA2024 Astronautics Hub]]) is driven by exactly this $\alpha\Delta T$ mismatch.

## Links
- Previous: [[FEEG1002 B1 - Stress in Multiple Dimensions and Thin-Walled Pressure Vessels]] · Next: [[FEEG1002 B3 - Generalised Hooke's Law]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions]]

## Sources
- Statics 2 Lectures 2a–b (normal and shear strain) and 3a–b (thermal strain; rail example)

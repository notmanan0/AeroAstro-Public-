---
title: "FEEG1002 B3 - Generalised Hooke's Law"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part B: Statics 2"
order: 12
tags: [feeg1002, statics-2, hookes-law, plane-stress, plane-strain, bulk-modulus]
aliases: ["Statics 2 Lecture 4", "Generalised Hooke's law", "Plane stress", "Plane strain", "Bulk modulus"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
next_topics: ["[[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]"]
key_concepts: ["[[Generalised Hooke's Law]]", "[[Plane Stress and Plane Strain]]"]
tutorial_sheets: ["[[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 04 - Generalised Hooke's Law.pdf"]
---

# FEEG1002 B3 - Generalised Hooke's Law

> [!abstract] Summary
> For a **homogeneous, isotropic, linear elastic** material, a normal stress produces strain in its own direction plus Poisson contraction in the other two. By superposition:
> $$\varepsilon_{xx} = \frac{1}{E}\left[\sigma_{xx} - \nu(\sigma_{yy}+\sigma_{zz})\right],\qquad \varepsilon_{xy} = \frac{1+\nu}{E}\sigma_{xy}$$
> Only **two** constants ($E$, $\nu$) are independent; $G$ and $K$ follow from them. Two reduced forms matter:
> - **plane stress** (thin plates): $\sigma_{zz} = 0$ but $\varepsilon_{zz}\ne0$;
> - **plane strain** (long dams, tunnels): $\varepsilon_{zz} = 0$ but $\sigma_{zz}\ne0$.

## Key Concepts
- [[Generalised Hooke's Law]] · [[Plane Stress and Plane Strain]] · [[Stress, Strain and Young's Modulus]]

---

## 1. Why a generalised law? (L4a)
- A tensile test gives $E$ (and $\nu$); a torsion test gives $G$. Each involves a **single** stress component.
- Real components (plates, vessels, shafts under combined load) have several stresses at once. They interact through the Poisson effect.
- Assumptions:
  - **homogeneous**: the same everywhere;
  - **isotropic**: the same in every direction. True for metals, **not** for wood or fibre composites;
  - **linear elastic**.

## 2. Plane stress (L4a)
Plane stress means $\sigma_{zz} = \sigma_{xz} = \sigma_{yz} = 0$. It holds for thin plates, and for thin-walled vessels, where the radial stress is about $p$ and negligible.

Superpose the effect of $\sigma_{xx}$ (stretching $x$, contracting $y$ and $z$) with that of $\sigma_{yy}$:

$$
\varepsilon_{xx} = \frac{1}{E}(\sigma_{xx} - \nu\sigma_{yy}),\quad \varepsilon_{yy} = \frac{1}{E}(\sigma_{yy} - \nu\sigma_{xx}),\quad \varepsilon_{zz} = -\frac{\nu}{E}(\sigma_{xx}+\sigma_{yy}),\quad \varepsilon_{xy} = \frac{1+\nu}{E}\sigma_{xy}
$$

Inverted, to give stresses from **measured** strains (strain gauges, [[FEEG1002 B5 - Strain Measurement and Strain Rosettes]]):

$$
\sigma_{xx} = \frac{E}{1-\nu^2}(\varepsilon_{xx} + \nu\varepsilon_{yy}),\qquad \sigma_{yy} = \frac{E}{1-\nu^2}(\varepsilon_{yy} + \nu\varepsilon_{xx}),\qquad \sigma_{xy} = \frac{E}{1+\nu}\varepsilon_{xy}
$$

- The shear strain comes from $\gamma = \sigma_{xy}/G$ with $G = E/2(1+\nu)$ and $\varepsilon_{xy} = \gamma/2$.
- Normal stresses cause no shear strain, and shear stress causes no normal strain. That decoupling is special to isotropy.
- The plate **thins** ($\varepsilon_{zz}\neq0$) even though $\sigma_{zz} = 0$.

## 3. Full 3D Hooke's law (L4b)

$$
\varepsilon_{xx} = \tfrac1E[\sigma_{xx} - \nu(\sigma_{yy}+\sigma_{zz})],\quad \varepsilon_{yy} = \tfrac1E[\sigma_{yy} - \nu(\sigma_{xx}+\sigma_{zz})],\quad \varepsilon_{zz} = \tfrac1E[\sigma_{zz} - \nu(\sigma_{xx}+\sigma_{yy})]
$$

$$
\varepsilon_{xy} = \frac{1+\nu}{E}\sigma_{xy},\qquad \varepsilon_{xz} = \frac{1+\nu}{E}\sigma_{xz},\qquad \varepsilon_{yz} = \frac{1+\nu}{E}\sigma_{yz}
$$

Inverse:

$$
\sigma_{xx} = \frac{E}{(1+\nu)(1-2\nu)}\left[(1-\nu)\varepsilon_{xx} + \nu(\varepsilon_{yy}+\varepsilon_{zz})\right],\ \dots,\qquad \sigma_{xy} = \frac{E}{1+\nu}\varepsilon_{xy}
$$

## 4. Volume change and the bulk modulus
Substituting into $\varepsilon_{vol} = \varepsilon_{xx}+\varepsilon_{yy}+\varepsilon_{zz}$:

$$
\varepsilon_{vol} = \frac{1-2\nu}{E}(\sigma_{xx}+\sigma_{yy}+\sigma_{zz})
$$

Under **hydrostatic** stress $\sigma_H$ (e.g. deep water):

$$
\varepsilon_{vol} = \frac{\sigma_H}{K},\qquad K = \frac{E}{3(1-2\nu)}
$$

- $\nu\to0.5$ makes the material **incompressible** ($K\to\infty$): rubber, with $\nu = 0.499$.
- The theoretical range is $-1 < \nu < 0.5$.

| Material | $E$ | $\nu$ |
|---|---|---|
| Steel | 210 GPa | 0.30 |
| Aluminium | 70 GPa | 0.34 |
| Copper | 130 GPa | 0.33 |
| Titanium | 105 GPa | 0.34 |
| Low-density polymer foam | 30 kPa | 0.35 |
| Natural rubber | 20 MPa | 0.499 (non-linear at large strain) |

![[s2_elastic_constants.png|640]]

## 5. Plane strain (L4b)
Plane strain means $\varepsilon_{zz} = \varepsilon_{xz} = \varepsilon_{yz} = 0$. It suits long bodies whose axial expansion is suppressed: tunnels, dams, rolled plates.
- Setting $\varepsilon_{zz} = 0$ in the 3D law **generates** $\sigma_{zz} = \nu(\sigma_{xx}+\sigma_{yy})$.
- Contrast the two cases:
  - **plane stress**: $\sigma_{zz} = 0$, $\varepsilon_{zz}\ne0$ (the plate thins);
  - **plane strain**: $\varepsilon_{zz} = 0$, $\sigma_{zz}\ne0$ (the walls push back).

> [!example] Tutorial 3: acrylic submersible hull at 100 m ($E = 3.2$ GPa, $\nu = 0.37$, $R = 1.1$ m, $t = 0.14$ m, $L = 15$ m)
> - Net pressure $-\rho gh = -0.981$ MPa, so $\sigma_{xx} = -3.85$ MPa and $\sigma_{yy} = -7.71$ MPa.
> - Plane-stress Hooke: $\varepsilon_{xx} = -313\ \mu\varepsilon$ and $\varepsilon_{yy} = -1963\ \mu\varepsilon$.
> - So $\Delta L = -4.7$ mm and $\Delta D = \varepsilon_{yy}D = -4.3$ mm.
> - Caveat: $t/R = 0.127 > 0.1$, so thin-wall theory is only approximate.

## Year 2 bridge
- **Cylindrical coordinates**: [[SESA2028 S9 - Continuum Mechanics in Cylindrical Coordinates]] writes the same law with $(r,\theta,z)$ and uses plane-stress (thin disc) or plane-strain (long cylinder) versions in the Lamé problems ([[Lame Equations]], [[Plane Strain Constraint]]).
- **Fracture**: plane strain at a thick crack front raises the constraint and lowers the apparent toughness. That is why $K_{IC}$ is measured in thick specimens ([[Fracture Toughness and LEFM Validity]], [[SESA2028 M1 - Fracture, Toughness and Fracture Mechanics]]).
- **FEA element choice**: plane-stress vs plane-strain elements in [[SESA2029 B6 - 2D and 3D Elements]] and [[Plane Stress and Plane Strain]]. The $\mathbf D$ matrix of the element is exactly the inverse law in §2–3.
- **Anisotropy**: composites break the isotropy assumption. [[SESA2028 M4 - Polymer Matrix Composites]] needs $E_1\neq E_2$ and more independent constants ([[Rule of Mixtures]]).

## Links
- Previous: [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]] · Next: [[FEEG1002 B4 - Stress Transformation and Mohr's Circle]]
- Worked problems: [[FEEG1002 Statics 2 Tutorial 3 - Generalised Hooke's Law Solutions]]

## Sources
- Statics 2 Lecture 4a–b (plane stress; 3D Hooke's law and plane strain)

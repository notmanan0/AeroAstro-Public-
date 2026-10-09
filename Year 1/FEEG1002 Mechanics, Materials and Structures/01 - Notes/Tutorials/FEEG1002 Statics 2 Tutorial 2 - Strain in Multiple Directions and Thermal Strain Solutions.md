---
title: "FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part B: Statics 2"
tags: [feeg1002, tutorial-solutions, statics-2, thermal-strain]
sheet: "Statics-2 Tutorial problem sheet 2"
theory_notes: ["[[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]]"]
key_concepts: ["[[Thermal Strain]]", "[[Strain Components and Volumetric Strain]]"]
status: complete
sources: ["02 - Sources/Statics 2/Tutorials/Tutorial Sheet 02 - Strain in Multiple Directions and Thermal Strain.pdf", "02 - Sources/Statics 2/Tutorials/Tutorial Sheet 02 - Strain in Multiple Directions and Thermal Strain - Solutions.pdf"]
---

# FEEG1002 Statics 2 Tutorial 2 - Strain in Multiple Directions and Thermal Strain Solutions

> [!abstract] Sheet Info
> Two thermal-stress problems with opposite structures:
> - **parallel**: bonded shell and core, with equal extensions and forces summing to zero;
> - **series**: a stepped rod between walls, with equal forces and total extension zero.
>
> All answers are reproduced ✔. The stress in the brass core, which the sheet does not give, is added.

## Theory Links
- [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain]] · [[Thermal Strain]]

**Method**: (1) release the constraint and let each part expand freely by $\alpha\Delta TL$; (2) add the mechanical deformation $FL/EA$ with tension-positive forces; (3) impose compatibility and equilibrium.

---

## Q1: Aluminium shell bonded to a brass core, heated from 15 °C to 195 °C
Data: shell $E = 70$ GPa, $\alpha = 23.6\times10^{-6}$/°C, OD 60 mm; core $E = 105$ GPa, $\alpha = 20.9\times10^{-6}$/°C, Ø25 mm. Axial effects only.

**(a)** The parts are bonded, so their extensions are equal. There is no external load, so $F_{Al} + F_{Br} = 0$.

$$
\alpha_{Al}L\Delta T + \frac{F_{Al}L}{A_{Al}E_{Al}} = \alpha_{Br}L\Delta T - \frac{F_{Al}L}{A_{Br}E_{Br}}\;\Rightarrow\; F_{Al}\left(\frac{1}{A_{Al}E_{Al}} + \frac{1}{A_{Br}E_{Br}}\right) = (\alpha_{Br} - \alpha_{Al})\Delta T
$$

- Areas: $A_{Al} = \tfrac\pi4(0.06^2 - 0.025^2) = 2.337\times10^{-3}$ m² and $A_{Br} = 4.909\times10^{-4}$ m².
- $F_{Al} = -19.05$ kN, so $\sigma_{Al} = \mathbf{-8.15}$ **MPa** ✔ (compressive).
- The core carries $+19.05$ kN, so $\sigma_{Br} = +38.8$ MPa (tensile).

**Why compressive?** Aluminium wants to expand more ($\alpha_{Al} > \alpha_{Br}$). The bonded pair settles at a common length **between** the two free lengths, so the aluminium is squashed back and the brass pulled forward.

**(b) Steel core** ($E = 200$ GPa, $\alpha = 11.7\times10^{-6}$/°C): the $\alpha$ mismatch is larger and the core is stiffer, giving $\sigma_{Al} = \mathbf{-56.2}$ **MPa** ✔, about 7× larger, and $\sigma_{steel} = +268$ MPa.

![[s2_t2_bimaterial_thermal.png|700]]

---

## Extra Q1: Steel AB (Ø30, 250 mm) + brass BC (Ø50, 300 mm) between rigid walls, $\Delta T = +50$ °C
**(a)** The walls fix the total length, $\delta_{st} + \delta_{br} = 0$. The parts are in series, so the force is the same in both:

$$
F\left(\frac{L_{st}}{A_{st}E_{st}} + \frac{L_{br}}{A_{br}E_{br}}\right) = -(\alpha_{st}L_{st} + \alpha_{br}L_{br})\Delta T\;\Rightarrow\; F = \mathbf{-142.6}\ \text{kN}\ ✔
$$

**(b)** $\sigma_{st} = F/A_{st} = \mathbf{-201.8}$ **MPa** and $\sigma_{br} = \mathbf{-72.7}$ **MPa** ✔. The same force acts on a smaller area in the steel.

**(c)** Total strain = thermal + mechanical:

$$\varepsilon_{st} = \alpha_{st}\Delta T + \frac{\sigma_{st}}{E_{st}} = -4.24\times10^{-4},\qquad \varepsilon_{br} = \alpha_{br}\Delta T + \frac{\sigma_{br}}{E_{br}} = +3.53\times10^{-4}$$

The brass **extends** and the steel **shortens**: the brass wins.

**(d)** Point B: $\delta_B = \varepsilon_{st}L_{st} = -0.106$ mm, i.e. B moves **0.106 mm towards A**. Check: $\varepsilon_{br}L_{br} = +0.106$ mm ✔

> [!tip] Sanity check on the stresses
> −202 MPa in the steel is close to typical steel yield (250 MPa), with nothing but a 50 °C rise. Fully constrained heating is dangerous, which is why pipelines need expansion bends and bridges need expansion joints.

## Sources
- Source sheet and official solutions: Statics-2 Tutorial problem sheet 2

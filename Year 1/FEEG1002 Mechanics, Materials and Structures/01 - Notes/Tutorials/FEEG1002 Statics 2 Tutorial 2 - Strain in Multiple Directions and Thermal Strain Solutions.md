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

> [!abstract] Sheet info
> Two thermal-stress problems with opposite structures: parts bonded in parallel (equal extensions, forces summing to zero) and parts in series between walls (equal forces, total extension zero). All answers match the official solutions, checked numerically; the stress in the core of Q1, which the sheet does not give, is added.

The method for both: release the constraint and let each part expand freely by $\alpha\Delta TL$; add a mechanical deformation $FL/EA$ with every force taken as tensile; then impose compatibility and equilibrium and let the signs come out ([[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Superposition for constrained assemblies|B2]]).

## Q1 Aluminium shell bonded to a brass core

*Taught in:* [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Superposition for constrained assemblies]] (parallel case) · worked in full at [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Worked example - aluminium shell bonded to a brass core]].

Data: shell $E=70$ GPa, $\alpha=23.6\times10^{-6}$ °C⁻¹, outer diameter 60 mm; core $E=105$ GPa, $\alpha=20.9\times10^{-6}$ °C⁻¹, diameter 25 mm; stress-free at 15 °C, heated to 195 °C, axial effects only.

**(a)** The parts are bonded, so their total extensions are equal; there is no external load, so $F_{Al}+F_{br}=0$:

$$
\alpha_{Al}\Delta TL+\frac{F_{Al}L}{A_{Al}E_{Al}}=\alpha_{br}\Delta TL-\frac{F_{Al}L}{A_{br}E_{br}}
$$

$$
F_{Al}\left(\frac{1}{A_{Al}E_{Al}}+\frac{1}{A_{br}E_{br}}\right)=(\alpha_{br}-\alpha_{Al})\Delta T
$$

With $A_{Al}=\tfrac\pi4(0.06^2-0.025^2)=2.337\times10^{-3}$ m², $A_{br}=4.909\times10^{-4}$ m² and $\Delta T=180$ °C:

$$
F_{Al}=-19.05\ \mathrm{kN},\qquad \sigma_{Al}=\frac{F_{Al}}{A_{Al}}=-8.15\ \mathrm{MPa},\qquad \sigma_{br}=\frac{-F_{Al}}{A_{br}}=+38.8\ \mathrm{MPa}
$$

The aluminium wants to expand more than the brass, but the bonded pair settles at a common length between the two free lengths, so the shell is held back in compression and the core pulled along in tension.

**(b)** With a steel core ($E=200$ GPa, $\alpha=11.7\times10^{-6}$ °C⁻¹) the mismatch in $\alpha$ is larger and the core stiffer, so $\sigma_{Al}=-56.2$ MPa, about seven times larger, and the steel core carries $+268$ MPa.

![[s2_t2_bimaterial_thermal.png|800]]

## Additional Q1 Steel and brass rod between rigid supports

*Taught in:* [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Superposition for constrained assemblies]] (series case) · worked in full at [[FEEG1002 B2 - Strain in Multiple Dimensions and Thermal Strain#Worked example - steel and brass in series between walls]].

Data: AB steel, 250 mm long, 30 mm diameter, $E=200$ GPa, $\alpha=11.7\times10^{-6}$ °C⁻¹; BC brass, 300 mm, 50 mm diameter, $E=105$ GPa, $\alpha=20.9\times10^{-6}$ °C⁻¹; $\Delta T=+50$ °C.

**(a)** The supports fix the total length, $\delta_s+\delta_b=0$, and the parts in series carry the same force $F$:

$$
F\left(\frac{L_s}{A_sE_s}+\frac{L_b}{A_bE_b}\right)=-\Delta T\left(\alpha_sL_s+\alpha_bL_b\right)
$$

$$
F=-142.6\ \mathrm{kN}
$$

**(b)** $\sigma_s=F/A_s=-201.8$ MPa and $\sigma_b=F/A_b=-72.6$ MPa; the same force acts on the smaller steel area.

**(c)** Total strain is thermal plus mechanical:

$$
\varepsilon_s=\alpha_s\Delta T+\frac{\sigma_s}{E_s}=-4.24\times10^{-4},\qquad \varepsilon_b=\alpha_b\Delta T+\frac{\sigma_b}{E_b}=+3.53\times10^{-4}
$$

so the brass extends and the steel shortens.

**(d)** Point B moves by $\varepsilon_sL_s=-0.106$ mm, that is 0.106 mm towards A (upwards in the sheet's figure). The brass gives the same magnitude, $\varepsilon_bL_b=+0.106$ mm, as compatibility requires.

The steel stress of $-202$ MPa is close to the yield stress of a mild steel after only a 50 °C rise, which is why pipelines need expansion bends and bridges expansion joints.

## Sources

- `Tutorial Sheet 02 - Strain in Multiple Directions and Thermal Strain.pdf` and its solutions.

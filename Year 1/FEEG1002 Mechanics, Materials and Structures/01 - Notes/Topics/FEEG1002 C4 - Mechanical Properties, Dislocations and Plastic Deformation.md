---
title: "FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 19
tags: [feeg1002, materials, tensile-test, dislocations, slip, plasticity, alloying]
aliases: ["Materials Lectures 5 and 6", "Mechanical properties and dislocations"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]", "[[FEEG1002 A1 - Forces, Equilibrium, Stress and Strain]]"]
next_topics: ["[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
key_concepts: ["[[Engineering Stress-Strain Properties]]", "[[Dislocations and Slip Systems]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 05 - Elastic and Plastic Mechanical Properties.pdf", "02 - Sources/Materials/Lectures/Lecture 06 - Plastic Deformation and Alloying.pdf"]
---

# FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation

> [!abstract] Summary
> Elastic deformation stretches bonds and is reversible; plastic deformation changes atomic neighbours and is permanent. A tensile test supplies $E$, $\nu$, yield strength, UTS, ductility, resilience and toughness. Metals deform plastically because **dislocations** let slip proceed one atomic row at a time.

## Key Concepts
- [[Engineering Stress-Strain Properties]] · [[Dislocations and Slip Systems]]

---

## 1. Engineering stress and strain

$$\sigma=\frac{F}{A_0},\qquad \varepsilon=\frac{L-L_0}{L_0},\qquad E=\frac{d\sigma}{d\varepsilon}\quad\text{(linear elastic region)}$$

Poisson's ratio links transverse contraction to axial extension:

$$\nu=-\frac{\varepsilon_{transverse}}{\varepsilon_{axial}}$$

True quantities use the instantaneous dimensions:

$$\sigma_T=\frac{F}{A},\qquad \varepsilon_T=\ln\frac{L}{L_0}$$

Before necking, assuming constant volume, $\sigma_T=\sigma(1+\varepsilon)$ and $\varepsilon_T=\ln(1+\varepsilon)$.

## 2. Mechanical properties from the curve
- **Yield strength**: onset of appreciable plasticity, commonly the 0.2% proof stress. Low-carbon steel may show upper and lower yield points.
- **UTS**: maximum engineering stress; diffuse necking starts here.
- **Ductility**: plastic strain before fracture, reported as percentage elongation or reduction of area. Below about 5% elongation is conventionally brittle.
- **Modulus of resilience**: elastic energy per unit volume, $U_r=\sigma_y^2/(2E)$ for linear elasticity.
- **Toughness**: total area under the stress-strain curve to fracture. It is not the same as fracture toughness $K_{IC}$.

![[m4_stress_strain_properties.png|760]]

> [!warning] Engineering stress falls after UTS because it still divides by $A_0$. The local **true stress** in the neck can continue rising.

## 3. Defects are useful
- **Point**: vacancies, self-interstitials, substitutional and interstitial solutes.
- **Line**: edge and screw dislocations, described by a Burgers vector $\mathbf b$.
- **Planar/volume**: grain boundaries, inclusions, pores and cracks.

Defects are not merely damage. They control diffusion, yield, strengthening, phase transformation and fracture.

## 4. Dislocation glide and slip
Sliding two perfect atomic planes simultaneously would require enormous stress. A dislocation moves the mismatch progressively, breaking and reforming only a row of bonds at a time.

- Slip is easiest on densely packed planes and directions.
- FCC has 12 $\{111\}\langle110\rangle$ slip systems and remains ductile over a wide temperature range.
- BCC has no close-packed plane; motion is thermally activated and its yield stress rises strongly at low temperature.
- HCP has too few easily activated independent systems at low temperature; deformation may require non-basal slip or twinning.
- **Mechanical twinning** shears successive atomic planes by different amounts and is more important in BCC/HCP at low temperature.

## 5. Alloying and solid solutions
The Hume-Rothery tendencies for extensive substitutional solubility are:
- atomic radii within about 15%;
- same crystal structure;
- similar electronegativity;
- compatible valence.

Solute atoms strain the lattice. Their stress fields interact with dislocation stress fields and impede glide:
- small substitutional atoms favour compressed regions;
- large atoms favour tensile regions;
- small atoms such as C occupy interstices and strongly distort BCC iron.

In steel, carbon atmospheres pin dislocations. Extra stress is required for initial breakaway (upper yield), followed by easier Lüders-band propagation at the lower yield stress.

> [!example] Elastic copper rod
> For $\sigma=276$ MPa, $E=110$ GPa, $L=305$ mm and $\nu=0.34$:
>
> $$\Delta L=\frac{\sigma}{E}L=0.765\ \text{mm},\qquad \Delta d=-\nu\frac{\sigma}{E}d=-0.00853\ \text{mm}\quad(d=10\ \text{mm})$$

## Design bridge to Statics
- $E$ controls deflection in [[FEEG1002 A4 - Engineer's Bending Theory and Second Moment of Area]].
- $\sigma_y$ is the comparison value in [[FEEG1002 B6 - Yield Criteria]].
- UTS is not normally the service design limit for a ductile component: permanent deformation begins first.
- Static yield checks do not cover fatigue, creep, corrosion or fracture.

## Links
- Previous: [[FEEG1002 C3 - Diffusion]] · Next: [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]
- Worked problems: [[FEEG1002 Materials Tutorial 2 - Mechanical Properties and Strengthening Solutions]]

## Sources
- Materials Lectures 5–6; audited against [[FEEG1002 Materials L05 Contact Sheet.png]] and [[FEEG1002 Materials L06 Contact Sheet.png]].

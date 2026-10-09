---
title: "Oxidation Rate Laws"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, oxidation, high-temperature, corrosion]
status: complete
parent: ["[[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]]"]
related: ["[[Evans Diagram and Passivation]]", "[[Thermal Barrier Coatings]]", "[[Gamma Prime Strengthening]]"]
---

# Oxidation Rate Laws

![[Figures/materials_oxidation_rate_laws.png]]

Dry oxidation at high temperature is still electrochemical: the **anode** is at the metal/oxide interface ($\mathrm{M\to M^{n+}+ne^-}$) and the **cathode** at the oxide/gas interface ($\mathrm{O_2+4e^-\to2O^{2-}}$). The oxide between them is both the electrolyte and the barrier. It is measured by **thermogravimetry**: weight gain per unit area $w$ against time.

## Rate laws

| Law | Equation | Scale | Examples |
|---|---|---|---|
| Linear | $w=k_Lt$ | porous or cracked, non-protective; reaction-controlled | K, Ta, Nb, Mg |
| Parabolic | $w^2=k_pt+C$ | thick, coherent, adherent; diffusion through a thickening layer controls it | Fe, Cu, Ni |
| Logarithmic | $w=k_e\log(Ct+A)$ | thin, highly protective; growth almost stops | Al, Cr ($\mathrm{Al_2O_3}$, $\mathrm{Cr_2O_3}$), Fe and Cu at modest $T$ |

## Oxide defect chemistry

- **Cation-defective** scales: metal ions diffuse outwards, so new oxide grows at the **outer** surface.
- **Anion-defective** scales: oxygen ions diffuse inwards, so new oxide grows at the **metal/oxide** interface.

$\mathrm{Cr_2O_3}$ and $\mathrm{Al_2O_3}$ have almost no defects, so they block both. A **dilute** Cr addition forms a mixed, defective oxide that can oxidise *faster* than plain metal. Above about 12 % Cr, a continuous $\mathrm{Cr_2O_3}$ layer forms.

## Failure of the scale

Oxides are ceramics. Differences in thermal expansion and lattice spacing cause **cracking and spallation** on thermal cycling, exposing fresh metal and changing parabolic behaviour back towards linear. Reactive elements (Y, Hf) and bond coats improve adhesion.

**Kinetics dominate.** The ranking of metals by oxidation resistance resembles the electrochemical series but does not match it (Al is very reactive yet very resistant).

---
title: "Evans Diagram and Passivation"
module: "SESA2028 Aerospace Materials & Structures"
type: concept
stream: "Materials"
tags: [sesa2028, materials, corrosion, polarisation, passivation]
status: complete
parent: ["[[SESA2028 M3 - Corrosion, Wear and Surface Engineering]]"]
related: ["[[Nernst Equation and Galvanic Series]]", "[[Localised Corrosion]]", "[[Stainless Steel Classes]]"]
---

# Evans Diagram and Passivation

## Polarisation and the Evans diagram

![[Figures/materials_evans_diagram.png]]

When current flows, ion depletion or build-up next to each electrode shifts its potential. The **anodic** reaction becomes more positive and the **cathodic** reaction more negative as the current rises. On a plot of $E$ against $\log i$ (an Evans diagram) the two polarisation lines cross at the **corrosion potential $E_{corr}$** and **corrosion current density $i_{corr}$**.

- A large $i_{corr}$ means fast corrosion. By Faraday, the rate is proportional to $i$.
- **Polarisation is beneficial**: steeper lines give a lower $i_{corr}$.
- The rate is often **cathode-limited**, by the supply of $\mathrm O_2$ or $\mathrm H^+$.
- Lowering temperature can *reduce* polarisation, so some couples corrode faster in the cold (the lecture's baked-bean tin in the fridge).

## Passivation

![[Figures/materials_passivation_curve.png]]

Metals such as stainless steel (> 12 % Cr), Al, Ti and Ni form a thin, protective oxide once their potential passes a critical value. Their anodic curve has an **active nose**, then a **passive** region (current drops by orders of magnitude), then a **transpassive** region (the film breaks down).

| Cathodic line crosses | Behaviour |
|---|---|
| Active region | corrodes rapidly |
| Passive region | **stable**: the film forms and **re-forms instantly if scratched** |
| Transpassive region | film unstable, not repaired, so pitting and general attack |

In **reducing** or oxygen-starved conditions (crevices, under deposits) the cathodic line falls into the active region, so stainless steel can corrode. Why $\mathrm{Cr_2O_3}$ protects: it is coherent, adherent and almost defect-free, and blocks both ions and electrons.

---
title: "FEEG1002 C10 - Polymers - Structure and Mechanics"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 25
tags: [feeg1002, materials, polymers, glass-transition, viscoelasticity, thermoplastics]
aliases: ["Materials Lectures 16 and 17", "Polymer structure and mechanics", "Polymer viscoelasticity"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]", "[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
next_topics: ["[[FEEG1002 C11 - Ceramics and Composites]]"]
key_concepts: ["[[Polymer Glass Transition and Viscoelasticity]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 16 - Polymer Structure and Types.pdf", "02 - Sources/Materials/Lectures/Lecture 17 - Polymer Mechanics.pdf"]
---

# FEEG1002 C10 - Polymers - Structure and Mechanics

> [!abstract] Summary
> Polymer backbones have strong covalent bonds, but bulk mechanics is governed mainly by weaker bonds, entanglements and crosslinks between long chains. Consequently properties depend strongly on **temperature and time**. Below $T_g$ chain motion is frozen and the polymer is glassy; above $T_g$ it is viscoelastic/rubbery; near $T_m$ a thermoplastic flows.

## Key Concepts
- [[Polymer Glass Transition and Viscoelasticity]]

---

## 1. Chains and molecular weight
- Carbon backbone bonds are tetrahedral (about 109°), so a nominally linear molecule forms a 3D coil.
- Polymerisation produces a distribution of chain lengths.
- Number-average molecular weight: $M_n=\sum x_iM_i$.
- Weight-average molecular weight: $M_w=\sum w_iM_i$.
- Long chains increase entanglement and generally raise strength/viscosity.

## 2. Three structural classes

| Class | Structure | Heating/mechanics |
|---|---|---|
| thermoplastic | linear/branched chains held by secondary bonds | remelts; chain sliding gives creep and ductility |
| elastomer | lightly crosslinked flexible chains | large reversible strain; entropy favours recoiling |
| thermoset | dense 3D covalent network | stiff, dimensionally stable, no remelting; often brittle |

## 3. Amorphous and semicrystalline polymers
- Perfect crystal packing is prevented by chain length variation, branching and tangling.
- Regular chains can fold into lamellae; lamellae radiate from nuclei to make **spherulites** separated by amorphous material.
- Crystallinity improves packing, stiffness, strength and chemical resistance; crystallites act like physical crosslinks.
- Amorphous material has a glass transition $T_g$; crystalline regions persist until melting $T_m$.

![[m10_polymer_temperature.png|820]]

## 4. Thermoplastic deformation
Temperature and loading rate control whether chains have time to rearrange.

- $T<T_g$: glassy, high modulus, small strain to brittle fracture.
- $T_g<T\ll T_m$: yielding, cold drawing and large viscoelastic/plastic strain.
- near $T_m$: low stiffness/strength and viscous flow.

At stable necking, tangled amorphous chains uncoil, align and pack more closely in the neck. The oriented neck becomes stiffer and transfers the deformation front into adjacent unoriented material, so the neck propagates at nearly constant load.

## 5. Viscoelasticity
Polymers have elastic storage plus time-dependent chain motion.

- **Creep**: strain rises under constant stress.
- **Stress relaxation**: stress falls under constant strain.
- Simple exponential relaxation:

$$\sigma(t)=\sigma_0e^{-t/\tau},\qquad E_r(t)=\frac{\sigma(t)}{\varepsilon_0}$$

Higher temperature and longer time both allow more rearrangement (**time-temperature equivalence**). Semicrystalline polymers retain more modulus above the amorphous $T_g$ because crystallites constrain the chains until $T_m$.

## 6. Damping
Stress and strain are out of phase when chain rearrangement lags the load; the hysteresis area is dissipated energy.

- Thermoplastics have high damping where segmental motion is active, often $T_g<T<T_m$.
- Thermosets have lower damping because the network restricts motion.
- Blends/copolymers can broaden the useful damping-temperature range.

> [!example] Rubber relaxation
> If stress falls from 0.20 to 0.15 MPa in 24 h, $\tau=-24/\ln(0.15/0.20)=83.4$ h. Reaching 0.10 MPa takes 57.8 h from the start, so **33.8 h more**.

> [!warning] Common traps
> - A polymer's room-temperature label “brittle” or “ductile” is incomplete without $T/T_g$ and loading time/rate.
> - Thermosets do not melt into a processable liquid; sufficient heat degrades the network.
> - $T_g$ is not $T_m$.

## Links
- Previous: [[FEEG1002 C9 - Fatigue, Creep and Corrosion]] · Next: [[FEEG1002 C11 - Ceramics and Composites]]
- Worked problems: [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]

## Sources
- Materials Lectures 16–17; audited against [[FEEG1002 Materials L16 Contact Sheet.png]] and [[FEEG1002 Materials L17 Contact Sheet.png]].


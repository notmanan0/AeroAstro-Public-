---
title: "FEEG1002 C1 - Atoms and Bonding"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 16
tags: [feeg1002, materials, atoms, bonding, valence, material-properties]
aliases: ["Materials Lectures 1 and 2", "Atomic bonding"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: []
next_topics: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
key_concepts: ["[[Atomic Bonding and Interatomic Potential]]"]
tutorial_sheets: []
sources: ["02 - Sources/Materials/Lectures/Lecture 01 - Introduction, Atoms and Bonding.pdf", "02 - Sources/Materials/Lectures/Lecture 02 - Atoms and Bonding.pdf"]
---

# FEEG1002 C1 - Atoms and Bonding

> [!abstract] Summary
> A material's macroscopic properties begin with its electrons. **Valence electrons** control bonding; the depth and curvature of the bond-energy well control melting temperature and elastic modulus.
> - **Ionic**: electrons transfer, leaving oppositely charged ions; strong and non-directional.
> - **Covalent**: electron pairs are shared locally; strong and directional.
> - **Metallic**: positive ion cores share delocalised electrons; non-directional bonding permits slip and provides conductivity.
> - **Secondary bonds**: van der Waals and hydrogen bonding are weaker, but dominate the interaction between polymer chains.

## Key Concepts
- [[Atomic Bonding and Interatomic Potential]]

---

## 1. Atomic structure and valence
- The nucleus contains **protons** and **neutrons**; electrons occupy quantised shells and orbitals.
- Atomic number $Z$ is the number of protons. The tabulated atomic weight is the abundance-weighted mean of naturally occurring isotopes.
- Atoms tend toward stable outer-shell configurations. Elements in the same periodic-table group therefore have similar valence and chemistry.
- EDX identifies which elements are present from their characteristic X-ray energies; it does not directly reveal the bond type or crystal structure.

## 2. Interatomic force and energy
Attraction and short-range electron-cloud repulsion balance at the equilibrium spacing $r_0$:

$$F_A(r_0)+F_R(r_0)=0,qquad F=-\frac{dU}{dr}$$

- The minimum energy $U(r_0)=-E_0$ defines the **bond energy** required to separate the atoms.
- A deeper well generally gives a higher melting temperature.
- A steeper well near $r_0$ gives a larger elastic modulus because more force is required for a small change in spacing.
- An asymmetric well also explains thermal expansion: the average spacing moves to larger $r$ as vibration amplitude increases.

![[m1_bonding_energy.png|880]]

## 3. Primary bonds

| Bond | Electron model | Directionality | Typical consequences |
|---|---|---|---|
| Ionic | electron transfer; Coulomb attraction between cations and anions | largely non-directional | high melting point, insulating, hard, brittle |
| Covalent | localised shared electron pair | strongly directional | high stiffness and strength; often brittle/insulating |
| Metallic | delocalised electron sea around ion cores | non-directional | electrical/thermal conductivity, ductility, reflectivity |

> [!example] NaCl
> Na has one outer electron and Cl needs one. Transfer gives Na$^+$ and Cl$^-$; electrostatic attraction holds the lattice together. The lattice must remain charge neutral.

> [!example] Diamond versus aluminium
> Diamond's strong 3D covalent network gives $E\sim1$ TPa and a very high melting/sublimation temperature. Aluminium's weaker metallic bonds give $E\approx69$ GPa and permit dislocation slip, so it is ductile.

## 4. Secondary bonds
- **Instantaneous/induced dipoles** produce van der Waals attraction.
- **Permanent polar molecules** can induce dipoles in neighbours.
- **Hydrogen bonding** is a particularly strong secondary interaction when H is bonded to electronegative atoms.

Secondary bonds are weak individually but numerous. In a thermoplastic the covalent backbone is strong, while chain-to-chain bonding is mostly secondary; this is why chain sliding, temperature and time dominate polymer mechanics in [[FEEG1002 C10 - Polymers - Structure and Mechanics]].

## 5. Bonding predicts material classes
- **Metals**: mobile electrons conduct; non-directional bonds tolerate changes of neighbours during slip; alloying is often possible.
- **Polymers**: low density, low modulus and low melting/softening temperatures arise from loose molecular packing and weak interchain forces.
- **Ceramics**: ionic/covalent bonds resist slip and chemical attack; the price is brittleness because a crack-tip stress cannot be relaxed by plastic flow.

> [!warning] Common traps
> - Atomic weight is not simply “protons + neutrons + electrons”; electron mass is negligible and the table reports an isotope-weighted mean.
> - Strong bonding raises modulus, but strength also depends on defects and microstructure.
> - A strong bond does not guarantee toughness: diamond is stiff but brittle.

## Year 2 bridge
- Materials selection maps compare stiffness, density, strength and fracture toughness rather than bond type alone.
- Bonding underlies corrosion ([[FEEG1002 C9 - Fatigue, Creep and Corrosion]]), ceramic stability ([[FEEG1002 C11 - Ceramics and Composites]]) and polymer $T_g$ ([[FEEG1002 C10 - Polymers - Structure and Mechanics]]).

## Links
- Parent: [[FEEG1002 Mechanics, Materials and Structures Hub]] · Next: [[FEEG1002 C2 - Crystal Structures and Crystallography]]

## Sources
- Materials Lectures 1–2; audited against [[FEEG1002 Materials L01 Contact Sheet.png]] and [[FEEG1002 Materials L02 Contact Sheet.png]].


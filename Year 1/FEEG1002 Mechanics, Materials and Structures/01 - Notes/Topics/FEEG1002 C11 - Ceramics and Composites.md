---
title: "FEEG1002 C11 - Ceramics and Composites"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 26
tags: [feeg1002, materials, ceramics, glass, composites, rule-of-mixtures]
aliases: ["Materials Lectures 18 and 19", "Ceramics and fibre composites"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C1 - Atoms and Bonding]]", "[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]"]
next_topics: ["[[FEEG1002 D1 - Linear Motion of Particles]]"]
key_concepts: ["[[Ceramic Flaw Sensitivity]]", "[[Composite Rule of Mixtures]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 18 - Ceramics.pdf", "02 - Sources/Materials/Lectures/Lecture 19 - Composites.pdf"]
---

# FEEG1002 C11 - Ceramics and Composites

> [!abstract] Summary
> Ceramics use strong ionic/covalent bonds: they are hard, temperature/environment resistant and excellent in compression, but dislocation motion is restricted so tensile flaws cause brittle fracture. Composites combine a reinforcement and matrix; aligned continuous fibres give an isostrain longitudinal modulus and a much smaller isostress transverse modulus.

## Key Concepts
- [[Ceramic Flaw Sensitivity]] · [[Composite Rule of Mixtures]]

---

## 1. Ceramic bonding and structures
- Ceramics combine metallic cations and non-metallic anions; charge neutrality must be satisfied.
- Coordination number depends on cation/anion radius ratio $r_c/r_a$: surrounding anions must contact the cation without overlapping.
- Examples: NaCl has coordination 6; CaF$_2$ has coordination 8.
- Silicates use SiO$_4^{4-}$ tetrahedra. Sharing corners creates chains, sheets or 3D networks.

## 2. Glasses
Silica glass is an amorphous network of tetrahedra. Network modifiers such as Na$_2$O and CaO break Si-O-Si bridges, introduce non-bridging oxygens and reduce network connectivity, viscosity, $T_g$ and melting/working temperature.

Glasses soften over a range near $T_g$ rather than showing a crystal's sharp melting transition.

## 3. Ceramic mechanics
- strong bonds $\rightarrow$ hardness, wear/temperature/oxidation resistance;
- charge/order constraints make dislocation slip difficult;
- little plasticity is available to blunt a crack;
- tensile strength is flaw-controlled and scattered; compression closes cracks, so compressive strength may be an order of magnitude higher.

The weakest critical flaw controls failure. A larger component samples more material and is more likely to contain a severe flaw, so strength is size- and reliability-dependent.

![[m11_ceramic_strength.png|760]]

> [!important] Do not design a brittle ceramic at its mean measured strength. Specify an acceptable failure probability/Weibull basis and use the corresponding lower-tail strength with suitable factors.

Concrete is a ceramic composite: aggregate in cement matrix. Steel reinforcement supplies tensile capacity; prestressing deliberately places the concrete in compression.

## 4. Composite roles and classifications
- **Reinforcement** carries high directional load and must be well protected and bonded.
- **Matrix** transfers load, maintains shape, protects the reinforcement and absorbs/distributes damage.
- Types include particulate, continuous/discontinuous fibres and structural laminates/sandwiches.
- Properties depend on constituents, interface, volume fraction, orientation, distribution and processing defects.

## 5. Continuous aligned fibre modulus
Let $V_f+V_m=1$.

**Longitudinal loading: isostrain** ($\varepsilon_f=\varepsilon_m=\varepsilon_c$):

$$E_L=V_fE_f+V_mE_m$$

**Transverse idealisation: isostress** ($\sigma_f=\sigma_m=\sigma_c$):

$$\frac1{E_T}=\frac{V_f}{E_f}+\frac{V_m}{E_m},\qquad E_T=\frac{E_fE_m}{V_fE_m+V_mE_f}$$

![[m11_composite_moduli.png|760]]

Therefore $E_L\gg E_T$ when stiff fibres sit in a compliant matrix. Cross-ply or quasi-isotropic laminates trade maximum axial performance for multidirectional stiffness/strength.

> [!example] 40% glass / 60% polyester
> With $E_f=69$ GPa and $E_m=3.4$ GPa:
>
> $$E_L=29.64\ \text{GPa},\qquad E_T=5.49\ \text{GPa}$$
>
> Under 50 MPa longitudinal composite stress on 250 mm², the total load is 12.5 kN. Isostrain gives fibre stress 116.4 MPa and matrix stress 5.74 MPa; their loads are **11.64 kN** and **0.860 kN**.

> [!warning] Common traps
> - “Strong ceramic” usually refers to compression/hardness, not reliable tensile toughness.
> - Use volume fractions, not mass fractions, in these rule-of-mixtures equations.
> - Longitudinal is isostrain; transverse series idealisation is isostress.
> - A rule of mixtures is an ideal bound/approximation; voids and poor interfaces lower real performance.

## Year 2 bridge
- Composite micromechanics, short-fibre length and laminate design continue in [[SESA2028 M4 - Polymer Matrix Composites]] and [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates]].

## Links
- Previous: [[FEEG1002 C10 - Polymers - Structure and Mechanics]] · Next strand: [[FEEG1002 D1 - Linear Motion of Particles]]
- Worked problems: [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions]]

## Sources
- Materials Lectures 18–19; audited against [[FEEG1002 Materials L18 Contact Sheet.png]] and [[FEEG1002 Materials L19 Contact Sheet.png]].

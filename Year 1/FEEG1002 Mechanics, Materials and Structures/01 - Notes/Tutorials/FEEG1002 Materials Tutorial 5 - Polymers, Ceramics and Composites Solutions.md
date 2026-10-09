---
title: "FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, polymers, ceramics, composites]
sheet: "Materials Tutorial Sheet 5"
theory_notes: ["[[FEEG1002 C10 - Polymers - Structure and Mechanics]]", "[[FEEG1002 C11 - Ceramics and Composites]]"]
key_concepts: ["[[Polymer Glass Transition and Viscoelasticity]]", "[[Ceramic Flaw Sensitivity]]", "[[Composite Rule of Mixtures]]"]
status: complete
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 05 - Polymers Ceramics Composites.pdf"]
---

# FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions

> [!abstract] Sheet Info
> Seven questions on temperature-dependent thermoplastic response, stress relaxation, crystallinity, rule-of-mixtures calculations and brittle ceramic/glass behaviour.

## Theory Links
- [[FEEG1002 C10 - Polymers - Structure and Mechanics]] · [[FEEG1002 C11 - Ceramics and Composites]]

---

## Q1: Amorphous PP, $T_g=-10^\circ$C, $T_m=175^\circ$C

| Test temperature | Regime and expected tensile curve |
|---|---|
| -60°C | well below $T_g$: steep elastic slope, high apparent strength, very small strain to brittle fracture |
| 21°C | above $T_g$: lower modulus, yield/neck, long cold-drawing plateau, then orientation hardening and large elongation |
| 120°C | far above $T_g$ and approaching $T_m$: very low modulus/yield stress, strong rate dependence and extensive viscous/viscoelastic flow |

At 21°C, amorphous coils begin to uncoil and align in the neck. Alignment packs chains more closely and raises local stiffness, so load transfers to adjacent unnecked material. The neck therefore propagates stably rather than localising immediately to fracture.

![[m10_polymer_temperature.png|780]]

## Q2: Time dependence and stress relaxation
### (a) Why time matters
Polymer chains need time to rotate, uncoil, disentangle and slide. A slow test allows more rearrangement and gives lower apparent stiffness/strength and more creep; a rapid test looks stiffer/more brittle. Raising temperature has a similar effect (time-temperature equivalence).

### (b) Rubber stress relaxation

$$\sigma(t)=\sigma_0e^{-t/\tau}$$

With $\sigma(24)/\sigma_0=0.15/0.20=0.75$:

$$\tau=-\frac{24}{\ln0.75}=83.43\ \text h$$

For $\sigma=0.10$ MPa:

$$t=-\tau\ln(0.10/0.20)=57.83\ \text h$$

Additional time:

$$\boxed{57.83-24=33.83\ \text h}$$

## Q3: Relaxation modulus and crystallinity
For fixed observation time, $E_r(t)$ falls as temperature rises: glassy plateau below $T_g$, sharp drop through the glass transition, then rubbery/flow regimes. A semicrystalline polymer retains a larger modulus above the amorphous $T_g$ because crystallites act as physical crosslinks and constrain the amorphous chains; its modulus falls decisively only as crystals melt near $T_m$.

## Q4: 40 vol% glass / 60 vol% polyester
Given $V_f=0.40$, $E_f=69$ GPa, $V_m=0.60$, $E_m=3.4$ GPa.

### (a) Longitudinal and transverse moduli

$$E_L=V_fE_f+V_mE_m=0.4(69)+0.6(3.4)=\boxed{29.64\ \text{GPa}}$$

$$E_T=\frac{E_fE_m}{V_fE_m+V_mE_f}=\frac{69(3.4)}{0.4(3.4)+0.6(69)}=\boxed{5.49\ \text{GPa}}$$

### (b) Phase loads under $\sigma_c=50$ MPa, $A=250$ mm²
Longitudinal loading is isostrain:

$$\varepsilon_c=\frac{\sigma_c}{E_L}=\frac{50}{29640}=1.6869\times10^{-3}$$

Phase stresses:

$$\sigma_f=E_f\varepsilon=116.40\ \text{MPa},\qquad \sigma_m=E_m\varepsilon=5.735\ \text{MPa}$$

Phase areas: $A_f=0.4(250)=100$ mm², $A_m=150$ mm².

$$\boxed{F_f=11.64\ \text{kN}},\qquad \boxed{F_m=0.860\ \text{kN}}$$

Check: $F_f+F_m=12.50$ kN $=\sigma_cA$.

![[m11_composite_moduli.png|760]]

## Q5: High strength but low ceramic impact toughness
Ionic/covalent bonds are strong and dislocation motion is very difficult, giving hardness and high compressive strength. But the same lack of slip means a crack-tip stress cannot be relaxed by plastic flow; pre-existing flaws intensify tensile stress and propagate unstably. The material can carry high stress in a favourable test yet absorb little energy before fracture.

## Q6: Why soda-lime glass softens below high-silica glass
Na$_2$O and CaO act as network modifiers. They break Si-O-Si bridges, create non-bridging oxygens and lower network connectivity. Chains/tetrahedral groups can rearrange more easily, reducing viscosity, $T_g$ and the melting/working temperature compared with a 96% silica network.

## Q7: Portland-cement strength distribution
Ceramic/cement failure follows a weakest-link population of pores, cracks and inclusions. Random maximum flaw size produces a broad, often Weibull-like strength distribution; specimen volume and processing history also matter.

The mean is unsafe because a substantial fraction fails below it. Design to an acceptable low failure probability using a lower percentile/characteristic statistical strength plus appropriate factors, and account for component size and environment.

![[m11_ceramic_strength.png|740]]

## Sources
- Materials Tutorial Sheet 5. Numerical values independently recalculated from the supplied data.

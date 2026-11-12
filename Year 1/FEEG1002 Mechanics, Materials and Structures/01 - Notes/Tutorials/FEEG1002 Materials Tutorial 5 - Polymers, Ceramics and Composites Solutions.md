---
title: "FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions"
module: "FEEG1002 Mechanics, Materials and Structures"
type: tutorial
stream: "Part C: Materials"
tags: [feeg1002, tutorial-solutions, materials, polymers, ceramics, glass, composites]
sheet: "Materials Tutorial Sheet 5"
theory_notes: ["[[FEEG1002 C10 - Polymers - Structure and Mechanics]]", "[[FEEG1002 C11 - Ceramics and Composites]]"]
key_concepts: ["[[Polymer Glass Transition and Viscoelasticity]]", "[[Ceramic Flaw Sensitivity]]", "[[Composite Rule of Mixtures]]"]
status: complete
date: 2026-11-05
sources: ["02 - Sources/Materials/Tutorials/Tutorial Sheet 05 - Polymers Ceramics Composites.pdf"]
---

# FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions

> [!abstract] Sheet info
> Seven questions: polymer stress–strain behaviour against temperature, stress relaxation, the relaxation modulus, a rule-of-mixtures composite, and three questions on ceramics and glass. The sheet prints no answers; the two calculations (Q2 and Q4) were checked in Python. Q1–Q3 use [[FEEG1002 C10 - Polymers - Structure and Mechanics|C10]]; Q4–Q7 use [[FEEG1002 C11 - Ceramics and Composites|C11]].

## Q1 - Polypropylene at three temperatures

Taught in: [[FEEG1002 C10 - Polymers - Structure and Mechanics#4. Stress–strain behaviour and temperature]].

The amorphous PP has $T_g=-10$ °C and $T_m=175$ °C, so the three test temperatures fall in the three regimes.

![[m10_stress_strain_temperature.png|900]]

- **−60 °C, below $T_g$.** The van der Waals forces between chains are strong enough to stop chain sliding. The curve is a steep straight line (bonds and chain segments stretching) up to brittle fracture at a small strain, with the highest stress of the three and little energy absorbed.
- **21 °C, between $T_g$ and $T_m$.** Chain sliding is possible once a yield stress overcomes the inter-chain bonding. The curve has a lower initial slope, a yield point, a drop as a neck forms, a long plateau of cold drawing at roughly constant stress as the neck propagates, then a rise in stress as the drawn chains lock up, and fracture at a very large strain.
- **120 °C, approaching $T_m$.** The inter-chain forces are very weak. The modulus and flow stress are very low and the polymer flows viscously to very large strains, with no distinct yield or stable neck; it just thins and elongates.

**Stable neck growth at 21 °C.** When the neck forms, the tangled amorphous chains in it straighten out and align along the load, and pack closer together. Aligned, closely packed chains attract each other more strongly, so the necked material becomes stiffer and stronger than the unnecked material beside it. The load is passed on to the shoulder of the neck, where the chains are still tangled and the yield stress is lower, so that region yields and draws next. The neck therefore travels along the specimen at roughly constant load instead of thinning to failure as in a metal, until the whole gauge length has been drawn. The drawn region often turns white as voids open between the straightening chains.

## Q2 - Time dependence and stress relaxation

Taught in: [[FEEG1002 C10 - Polymers - Structure and Mechanics#5. Viscoelasticity]].

**(a) Why time matters.** A polymer deforms by its chains sliding past each other, and sliding needs time: van der Waals bonds break at local high-stress points, a chain moves a little, and the load passes on. Under a constant load the strain keeps increasing (creep), and at a constant strain the stress keeps falling (stress relaxation). So a polymer has no single modulus or strength: a slow test gives the chains time to rearrange and the polymer looks softer and weaker, while a fast test looks stiffer and more brittle. A raised temperature has the same effect as a longer time. Any polymer property has to be quoted with its time (or rate) and temperature.

**(b) Further relaxation time.** The stress relaxes as

$$
\sigma(t)=\sigma_0\exp\left(-\frac t\tau\right)
$$

From 0.20 to 0.15 MPa in 24 h:

$$
\frac{0.15}{0.20}=\exp\left(-\frac{24}{\tau}\right)
$$

$$
\tau=-\frac{24}{\ln0.75}=\frac{24}{0.2877}=83.4\ \mathrm h
$$

The time to fall from 0.20 to 0.10 MPa is

$$
t=-\tau\ln\frac{0.10}{0.20}=83.4\times0.693=57.8\ \mathrm h
$$

so the further time beyond the first 24 h is

$$
57.8-24=\boxed{33.8\ \mathrm h}
$$

> [!check] Each step is a constant ratio
> Going from 0.15 to 0.10 MPa is a ratio of $2/3$, so it takes $-\tau\ln(2/3)=83.4\times0.405=33.8$ h directly. An exponential takes equal times for equal ratios, whatever the starting stress.

## Q3 - Relaxation modulus and crystallinity

Taught in: [[FEEG1002 C10 - Polymers - Structure and Mechanics#The relaxation modulus]].

![[m10_relaxation_modulus.png|900]]

At a fixed time (say 10 s), the relaxation modulus $E_r=\sigma(t)/\varepsilon_0$ of an amorphous thermoplastic falls with temperature through five regions. Below $T_g$ it is glassy, with a high, nearly constant $E_r$ (no chain sliding). Around $T_g$ it is leathery, and $E_r$ falls steeply, by orders of magnitude, as chain sliding becomes possible. Above that is a rubbery plateau, where only the entanglements hold the chains, then rubbery flow, and finally viscous flow, where $E_r$ drops to very low values.

A more crystalline polymer keeps a much higher $E_r$ to a much higher temperature. It shows only a small dip at $T_g$, from its remaining amorphous regions, and then holds its modulus until its crystals melt at $T_m$, where it drops sharply. The difference arises because in crystalline regions the chains are aligned and closely packed, with much stronger van der Waals bonding between them; they cannot slide past each other above $T_g$, and they act as stiff blocks, and as physical cross-links, tying the amorphous chains between them. In an amorphous polymer nothing prevents sliding once the glass transition is passed.

## Q4 - Glass–polyester composite

Taught in: [[FEEG1002 C11 - Ceramics and Composites#4. Moduli of continuous aligned fibre composites]] and [[FEEG1002 C11 - Ceramics and Composites#Load carried by the fibres]].

$V_f=0.40$, $E_f=69$ GPa, $V_m=0.60$, $E_m=3.4$ GPa.

**(a) Moduli.** Longitudinally (isostrain):

$$
E_L=E_mV_m+E_fV_f=3.4\times0.60+69\times0.40=2.04+27.6=\boxed{29.6\ \mathrm{GPa}}
$$

Transversely (isostress):

$$
E_T=\frac{E_mE_f}{E_fV_m+E_mV_f}=\frac{3.4\times69}{69\times0.60+3.4\times0.40}=\frac{234.6}{42.76}=\boxed{5.49\ \mathrm{GPa}}
$$

**(b) Loads in each phase.** Along the fibres the strain is the same in both phases:

$$
\varepsilon=\frac{\sigma_c}{E_L}=\frac{50}{29\,640}=1.687\times10^{-3}
$$

$$
\sigma_f=E_f\varepsilon=69\,000\times1.687\times10^{-3}=116.4\ \mathrm{MPa}
$$

$$
\sigma_m=E_m\varepsilon=3400\times1.687\times10^{-3}=5.74\ \mathrm{MPa}
$$

The fibres occupy $0.40\times250=100$ mm² and the matrix 150 mm², so

$$
F_f=116.4\times100=\boxed{11.64\ \mathrm{kN}},\qquad F_m=5.74\times150=\boxed{0.86\ \mathrm{kN}}
$$

The total, 12.50 kN, equals $\sigma_cA=50\times250$, and the fibres carry 93 % of it. As a check, $F_f/F_m=E_fV_f/(E_mV_m)=27.6/2.04=13.5$.

![[m11_composite_moduli.png|900]]

## Q5 - Strong but not tough

Taught in: [[FEEG1002 C11 - Ceramics and Composites#Why ceramics are brittle]].

Ceramics have strong ionic or covalent bonds, and slip would bring like-charged ions next to each other, so dislocations can hardly move. That makes them hard and very strong, especially in compression, where flaws are pushed shut. But it also means they cannot deform plastically. In an impact test, toughness is the energy absorbed up to fracture, and in a metal most of that energy goes into plastic deformation. A ceramic has none: there is nothing to blunt the stress concentration at the notch or at its inherent flaws, so as soon as the local stress at a flaw reaches the fracture stress a crack runs straight through, absorbing only the small surface energy of the new faces. High strength with low toughness is the signature of a material that stores elastic energy and then releases it in one go.

## Q6 - Soda-lime against silica glass

Taught in: [[FEEG1002 C11 - Ceramics and Composites#Silicates and glasses]] and [[FEEG1002 C11 - Ceramics and Composites#Thermal behaviour and working temperatures]].

![[m11_glass_viscosity.png|900]]

Silica glass is a three-dimensional network of SiO₄ tetrahedra joined at their corners by bridging oxygens, each shared between two tetrahedra; 96 % silica glass is almost entirely this connected network. The Na₂O and CaO in soda-lime glass are network modifiers. The Na⁺ and Ca²⁺ ions satisfy the charges of oxygens that are then bonded to only one silicon, non-bridging oxygens, which cuts the links of the network. A less connected network can flow at a lower temperature: its viscosity at any temperature is lower, so its strain, annealing, softening and working points, its $T_g$ and its melting range are all lower. That is why soda-lime glass can be worked at about 1000 °C, where 96 % silica glass is still far too viscous.

## Q7 - Strength distribution of Portland cement

Taught in: [[FEEG1002 C11 - Ceramics and Composites#Scatter in strength and statistical design]].

Cement is a brittle ceramic: it cannot yield, so its strength is set by the largest flaw (pore, crack, poorly bonded particle) in each specimen, through $\sigma_f\propto K_{IC}/\sqrt{\pi a}$. Flaw sizes vary at random from specimen to specimen, so the strengths of nominally identical specimens are spread out, here from about 1.4 to 3.4 MPa around a peak near 2.45 MPa. Larger specimens are more likely to contain a large flaw and so are weaker on average.

The average strength is not a safe design value because, by definition, a large fraction of parts (roughly half) are weaker than the average and would fail at it. Instead the designer chooses an acceptable probability of failure, finds the stress at which only that small fraction fails from the statistics of the distribution (Weibull analysis), and designs below it, allowing also for the size of the real component. Inspecting parts and rejecting those with flaws above the critical size for the service stress narrows the distribution, and putting the material into compression, as in pre-stressed concrete, avoids the problem.

![[m11_ceramic_strength.png|900]]

## Sources

- `Tutorial Sheet 05 - Polymers Ceramics Composites.pdf`: Q1–Q7, including the glass viscosity chart and the cement strength histogram. No solutions are provided. Q2 and Q4 were calculated in Python; the strength range in Q7 was read from the sheet's histogram. The curves sketched for Q1 and Q3 are qualitative.

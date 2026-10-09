---
title: "FEEG1002 C9 - Fatigue, Creep and Corrosion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 24
tags: [feeg1002, materials, fatigue, creep, corrosion, paris-law]
aliases: ["Materials Lectures 14 and 15", "Time dependent failure", "Fatigue creep corrosion"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]]", "[[FEEG1002 C3 - Diffusion]]"]
next_topics: ["[[FEEG1002 C10 - Polymers - Structure and Mechanics]]"]
key_concepts: ["[[S-N Curves and Paris Law]]", "[[Creep]]", "[[Galvanic Corrosion and Passivation]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 14 - Failure of Materials 3 - Fatigue.pdf", "02 - Sources/Materials/Lectures/Lecture 15 - Failure of Materials 4 - Creep and Corrosion.pdf"]
---

# FEEG1002 C9 - Fatigue, Creep and Corrosion

> [!abstract] Summary
> Materials can fail below their static yield stress because the load repeats (**fatigue**), because stress acts for a long time at high homologous temperature (**creep**), or because electrochemical reactions remove/weaken material (**corrosion**). These mechanisms interact: corrosion pits initiate fatigue and creep cracks can grow along oxidised grain boundaries.

## Key Concepts
- [[S-N Curves and Paris Law]] · [[Creep]] · [[Galvanic Corrosion and Passivation]]

---

## 1. Fatigue loading and life
$$\Delta\sigma=\sigma_{max}-\sigma_{min},\qquad \sigma_a=\frac{\Delta\sigma}{2},\qquad \sigma_m=\frac{\sigma_{max}+\sigma_{min}}2$$

Fatigue has three stages:
1. crack initiation ($N_i$), often at a surface defect/notch;
2. stable crack propagation ($N_p$);
3. rapid final fracture once the remaining ligament or $K_{max}$ becomes critical.

$$N_f=N_i+N_p$$

- High-cycle/low-stress life is often initiation dominated.
- Low-cycle/high-strain fatigue contains appreciable plastic strain and propagation can dominate.

## 2. S-N design
An S-N curve plots stress amplitude against cycles to failure on a log-$N$ axis.

- **Fatigue life**: $N_f$ at a specified stress.
- **Fatigue strength**: allowable stress at a specified life.
- **Fatigue limit**: horizontal asymptote below which essentially infinite life is assumed (seen in many steels/Ti alloys, not universal).

![[m9_fatigue_sn.png|760]]

S-N data scatter strongly and smooth laboratory coupons omit real stress concentrations, surface finish, residual stress, environment and mean stress. Use appropriate design curves and factors—not a single best-fit line.

## 3. Damage-tolerant crack growth
For a known crack under cyclic stress,
$$\Delta K=K_{max}-K_{min}=Y\Delta\sigma\sqrt{\pi a}$$
with compressive $K_{min}$ commonly taken as zero for this introductory treatment. In the stable Region-II regime,
$$\frac{da}{dN}=A(\Delta K)^m$$
where $A,m$ are material/environment constants. Integrating from detected $a_i$ to critical $a_c$ predicts inspection interval or remaining propagation life.

## 4. Creep
Creep is time-dependent strain under sustained stress, important roughly above $0.3$–$0.4T_m$ for metals and $0.4$–$0.5T_m$ for ceramics (absolute temperatures). Polymers may creep near or above $T_g$ even near room temperature.

Stages:
- **primary**: rate falls as strain hardening develops;
- **secondary**: approximately constant rate; usually most service life;
- **tertiary**: rate accelerates through necking, cavitation/damage and section loss to rupture.

![[m9_creep_curve.png|760]]

The steady rate combines stress sensitivity and Arrhenius temperature dependence:
$$\dot\varepsilon_s=K_2\sigma^n\exp\left(-\frac{Q_c}{RT}\right)$$

Mechanisms include lattice/grain-boundary diffusion, dislocation climb and grain-boundary sliding. Therefore stress exponent $n$ and activation energy $Q_c$ help identify the mechanism.

## 5. Electrochemical corrosion
At the **anode**, metal oxidises and dissolves:
$$M\rightarrow M^{n+}+ne^-$$
At the **cathode**, a reduction reaction consumes electrons, for example
$$2H^++2e^-\rightarrow H_2$$
The electron path, ion-conducting electrolyte, anode and cathode form a corrosion cell. Standard electrode potentials describe ideal reference conditions; the **galvanic series** ranks actual alloys in a specified environment such as seawater.

Eight lecture categories: uniform, galvanic, crevice, pitting, intergranular, selective leaching, tribocorrosion and stress-corrosion cracking.

## 6. Passivation and protection
- Al, Cr and Ti form adherent, coherent, slow-growing protective oxides.
- Stainless steel contains enough Cr (about 12% minimum) to form a Cr$_2$O$_3$ film.
- Zn or Mg can be a **sacrificial anode**, corroding to protect steel.
- Impressed-current cathodic protection drives the structure cathodic.
- Coatings interrupt electrolyte/electron access, but damaged coatings can create a small-anode/large-cathode problem.
- Detail to drain water, avoid crevices and isolate dissimilar metals.

> [!warning] Common traps
> - The more negative/active member of a galvanic pair is the anode under the relevant environmental series; passivation can reverse expectations from standard potentials.
> - Creep temperature comparisons use kelvin ratios.
> - A static safety factor does not predict fatigue life.

## Year 2 bridge
- Variable-amplitude fatigue, Miner damage, mean-stress corrections and more detailed fracture mechanics continue in [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]].
- Larson-Miller rupture methods, oxidation kinetics and superalloys continue in [[SESA2028 M8 - High Temperature Materials - Creep, Oxidation and Superalloys]].

## Links
- Previous: [[FEEG1002 C8 - Fracture - Brittle, Ductile and Fracture Mechanics]] · Next: [[FEEG1002 C10 - Polymers - Structure and Mechanics]]
- Worked problems: [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions]]

## Sources
- Materials Lectures 14–15; audited against [[FEEG1002 Materials L14 Contact Sheet.png]] and [[FEEG1002 Materials L15 Contact Sheet.png]].


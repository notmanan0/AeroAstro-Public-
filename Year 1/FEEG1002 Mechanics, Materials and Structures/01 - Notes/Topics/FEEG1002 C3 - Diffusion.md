---
title: "FEEG1002 C3 - Diffusion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: topic
stream: "Part C: Materials"
order: 18
tags: [feeg1002, materials, diffusion, fick, arrhenius, carburising]
aliases: ["Materials Lecture 4", "Fick's laws", "Arrhenius diffusion"]
date: 2026-09-25
status: complete
parent: ["[[FEEG1002 Mechanics, Materials and Structures Hub]]"]
prerequisites: ["[[FEEG1002 C2 - Crystal Structures and Crystallography]]"]
next_topics: ["[[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]"]
key_concepts: ["[[Fick's Laws and Arrhenius Diffusion]]"]
tutorial_sheets: ["[[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 04 - Diffusion.pdf"]
---

# FEEG1002 C3 - Diffusion

> [!abstract] Summary
> Diffusion is thermally activated atomic transport down a chemical-potential/concentration gradient. Fick's first law gives steady flux; Fick's second law governs changing concentration. The diffusion coefficient is extremely temperature-sensitive:
>
> $$J=-D\frac{dC}{dx},\qquad \frac{\partial C}{\partial t}=D\frac{\partial^2C}{\partial x^2},\qquad D=D_0e^{-Q/RT}$$

## Key Concepts
- [[Fick's Laws and Arrhenius Diffusion]]

---

## 1. Mechanisms
- **Vacancy diffusion**: a substitutional atom jumps into an adjacent vacancy. It requires a vacancy and sufficient activation energy.
- **Interstitial diffusion**: a small atom such as H, C or N jumps between interstitial sites. It is usually much faster because there are many empty sites and the atom is small.
- **Grain-boundary diffusion** is fast because the boundary is disordered, high-energy and rich in free volume/vacancies.

Typical comparison at 500°C in $\alpha$-Fe: interstitial carbon diffuses roughly $10^9$ times faster than substitutional iron.

## 2. Steady-state diffusion: Fick's first law

$$J=-D\frac{dC}{dx}$$

- $J$: atomic or mass flux per unit area per time.
- $D$: diffusion coefficient, m²/s.
- The minus sign states that net transport is from high to low concentration.
- For a linear concentration drop across thickness $L$, $J=-D(C_2-C_1)/L$.

## 3. Non-steady diffusion: Fick's second law
Mass conservation applied to the flux gives

$$\frac{\partial C}{\partial t}=D\frac{\partial^2C}{\partial x^2}$$

for constant $D$. A surface treatment such as carburising produces a concentration profile that spreads with a characteristic distance $x\sim\sqrt{Dt}$.

> [!tip] Scaling rule
> To double the diffusion depth at the same temperature requires roughly four times the time because $x\propto\sqrt t$.

## 4. Temperature dependence

$$D=D_0\exp\left(-\frac{Q}{RT}\right)$$

Taking logs gives a straight-line plot:

$$\ln D=\ln D_0-\frac{Q}{R}\frac1T$$

- slope $=-Q/R$ on a $\ln D$ versus $1/T$ graph;
- $T$ must be absolute temperature in kelvin;
- doubling temperature does **not** merely double $D$.

![[m3_diffusion_arrhenius.png|760]]

## 5. Structural factors
Diffusion becomes faster with:
- higher temperature;
- smaller solute atoms;
- interstitial rather than substitutional motion;
- more open/less densely packed structures;
- more vacancies and grain-boundary area;
- lower activation energy and, broadly, lower melting temperature.

> [!example] Carbon in iron
> At 900°C, interstitial C diffuses faster in BCC $\alpha$-Fe than in more closely packed FCC $\gamma$-Fe, even though carbon solubility is larger in the FCC phase. **Solubility and diffusivity are different properties.**

## 6. Where diffusion reappears
- solidification and coring in [[FEEG1002 C6 - Phase Diagrams]];
- pearlite formation and heat treatment in [[FEEG1002 C7 - Steels and Precipitation Hardening]];
- annealing in [[FEEG1002 C5 - Strengthening Mechanisms and Annealing]];
- creep and protective oxide growth in [[FEEG1002 C9 - Fatigue, Creep and Corrosion]].

> [!warning] Common traps
> - Use kelvin in the Arrhenius exponential.
> - Faster kinetics do not change the equilibrium phases shown by a phase diagram; they change how quickly equilibrium is approached.
> - A negative Fick-law flux is a direction, not a negative amount of material.

## Links
- Previous: [[FEEG1002 C2 - Crystal Structures and Crystallography]] · Next: [[FEEG1002 C4 - Mechanical Properties, Dislocations and Plastic Deformation]]
- Worked problems: [[FEEG1002 Materials Tutorial 1 - Crystal Structures and Diffusion Solutions]]

## Sources
- Materials Lecture 4; audited against [[FEEG1002 Materials L04 Contact Sheet.png]].


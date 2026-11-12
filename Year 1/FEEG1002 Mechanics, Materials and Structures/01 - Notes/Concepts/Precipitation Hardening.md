---
title: "Precipitation Hardening"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["age hardening", "ageing", "solution treatment", "supersaturated solid solution", "GP zones", "peak ageing", "over-ageing", "under-ageing", "coherent precipitates"]
tags: [feeg1002, concept, materials, strengthening, heat-treatment]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C7 - Steels and Precipitation Hardening]]", "[[FEEG1002 C5 - Strengthening Mechanisms and Annealing]]"]
related_concepts: ["[[Strengthening Mechanisms in Metals]]", "[[Fick's Laws and Arrhenius Diffusion]]", "[[Tie Lines and Lever Rule]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 11 - Precipitation Hardening.pdf", "02 - Sources/Materials/Lectures/Lecture 07 - Strengthening Mechanisms and Annealing.pdf"]
---

# Precipitation Hardening

Precipitation hardening (age hardening) is strengthening an alloy by a controlled heat treatment that forms a fine, uniform dispersion of second-phase particles inside the grains, where they obstruct dislocations; the standard example is Al–4 wt% Cu.

The alloy must have a phase diagram in which a single-phase field, on cooling, crosses a sloping solvus into a two-phase field: α in Al–Cu holds up to about 5.6 wt% Cu at 548 °C but very little at room temperature. Slow cooling would put the excess copper into coarse θ (CuAl₂) on the grain boundaries, which does little for strength, so the treatment has three steps. Solution treatment at about 550 °C, inside the α field, dissolves all the copper. A quench to room temperature leaves no time for diffusion, so the α is supersaturated with copper. Ageing at about 120 °C, below the solvus, lets the copper diffuse short distances and cluster throughout the grains, through the sequence GP zones → θ″ → θ′ → θ.

![[m7_ageing_curve.png|900]]

How a particle resists a dislocation depends on its coherency. Small coherent particles strain the surrounding lattice and are cut by a dislocation pushed hard enough; large incoherent ones cannot be cut, so the dislocation bows out between them and leaves a loop around each, which needs a stress that falls as the particles get further apart. The yield strength against ageing time therefore rises to a peak, at the best combination of particle number, size, spacing and coherency, then falls as the particles coarsen: before the peak the alloy is under-aged, after it over-aged.

Ageing is diffusion-controlled, so its rate follows the Arrhenius form: at a higher ageing temperature the peak comes sooner but is lower (about a minute at 260 °C, a month at 121 °C for the alloy considered), and the choice is a compromise between strength and furnace time. It also does not stop when the treatment ends. A part that runs warm in service keeps ageing, over-ages, and loses strength, so a design margin can disappear in service.

## Related

- [[FEEG1002 C7 - Steels and Precipitation Hardening#5. Precipitation hardening|precipitation hardening]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Choosing the alloy from the phase diagram|choosing the alloy]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#The three-stage heat treatment|the three-stage treatment]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#The precipitation sequence|precipitation sequence]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#The ageing curve|the ageing curve]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Ageing temperature and time|temperature and time]] · [[FEEG1002 C7 - Steels and Precipitation Hardening#Over-ageing in service|over-ageing in service]] · [[FEEG1002 C5 - Strengthening Mechanisms and Annealing#Coherent and incoherent precipitates|coherent and incoherent precipitates]]
- [[FEEG1002 Materials Tutorial 3 - Phase Diagrams Solutions#Q4 - Precipitation hardening|Tutorial 3, Q4]]
- [[Strengthening Mechanisms in Metals]] · [[Fick's Laws and Arrhenius Diffusion]] · [[Tie Lines and Lever Rule]]
- Year 2: the SESA2028 note [[Year 2/SESA2028 Aerospace Materials & Structures/01 - Notes/Concepts/Precipitation Hardening|Precipitation Hardening]] and [[SESA2028 M6 - Light Alloys - Aluminium, Magnesium, Beryllium and Titanium]]

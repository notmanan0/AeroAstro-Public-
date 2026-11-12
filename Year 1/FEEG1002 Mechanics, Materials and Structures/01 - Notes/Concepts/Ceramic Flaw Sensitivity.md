---
title: "Ceramic Flaw Sensitivity"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["brittleness of ceramics", "scatter in ceramic strength", "statistical design", "Weibull analysis", "pre-stressed concrete", "radius ratio", "coordination number"]
tags: [feeg1002, concept, materials, ceramics]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C11 - Ceramics and Composites]]"]
related_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Atomic Bonding and Interatomic Potential]]", "[[Composite Rule of Mixtures]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 18 - Ceramics.pdf"]
---

# Ceramic Flaw Sensitivity

A ceramic's strength in tension is set by its largest flaw, because it cannot deform plastically to blunt the stress concentration at a crack tip; flaw sizes vary from piece to piece, so the strengths of nominally identical parts scatter widely and design has to be statistical.

The brittleness comes from the bonding. In an ionic ceramic, sliding one plane of ions over the next by one spacing would bring like charges side by side, and they repel strongly, so dislocations can move only in a very few directions and in practice only at very high temperatures. With no plasticity, a flaw in tension raises the local stress until it reaches the fracture stress, and the part breaks suddenly through $\sigma_f\propto K_{IC}/\sqrt{\pi a}$. In compression the flaws are pushed shut, so ceramics are often ten times stronger in compression than in tension. Pre-stressed concrete uses this: steel tensioned before the concrete sets leaves the concrete in residual compression, which any tensile service load must cancel first.

![[m11_ceramic_strength.png|900]]

Because each specimen fails at its own worst flaw, strengths scatter: for one typical ceramic an average of 660 MPa with results from 390 to 800 MPa. Larger parts are more likely to contain a large flaw, so they are weaker on average. Designing at the average strength would mean roughly half the parts failing, so instead the strengths are described statistically (Weibull analysis), an acceptable probability of failure is chosen, the critical flaw size for the service stress is found from $a_c=\frac1\pi(K_{IC}/Y\sigma)^2$, and every part is inspected and rejected if it holds a larger flaw. Ceramics can also fail by slow crack growth: cracks grow under sustained load until $K_I$ reaches $K_{IC}$.

## Related

- [[FEEG1002 C11 - Ceramics and Composites#Why ceramics are brittle|why ceramics are brittle]] · [[FEEG1002 C11 - Ceramics and Composites#Strong in compression, weak in tension|strong in compression]] · [[FEEG1002 C11 - Ceramics and Composites#Concrete and pre-stressing|concrete and pre-stressing]] · [[FEEG1002 C11 - Ceramics and Composites#Scatter in strength and statistical design|scatter and statistical design]] · [[FEEG1002 C11 - Ceramics and Composites#Radius ratio and coordination number|radius ratio]] · [[FEEG1002 C11 - Ceramics and Composites#Worked example - pre-stressed concrete|pre-stressed concrete example]]
- [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q5 - Strong but not tough|Tutorial 5, Q5]] · [[FEEG1002 Materials Tutorial 5 - Polymers, Ceramics and Composites Solutions#Q7 - Strength distribution of Portland cement|Q7]]
- [[Griffith Criterion and Fracture Toughness]] · [[Atomic Bonding and Interatomic Potential]] · [[Composite Rule of Mixtures]]

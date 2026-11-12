---
title: "Tresca Yield Criterion"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part B: Statics 2"
aliases: ["Tresca criterion", "maximum shear stress criterion", "Tresca hexagon"]
tags: [feeg1002, concept, statics-2, yield, tresca]
status: complete
parent_lectures: ["[[FEEG1002 B6 - Yield Criteria]]"]
related_concepts: ["[[Von Mises Yield Criterion]]", "[[Principal Stresses]]", "[[Mohr's Circle]]", "[[Von Mises and Tresca Yield Criteria]]"]
sources: ["02 - Sources/Statics 2/Lectures/Lecture 08 - Yield Criteria.pdf"]
---

# Tresca Yield Criterion

The Tresca criterion states that a ductile material yields when the maximum shear stress on any plane reaches half the uniaxial yield stress, that is when $\max(|\sigma_I-\sigma_{II}|,|\sigma_I-\sigma_{III}|,|\sigma_{II}-\sigma_{III}|)=\sigma_Y$.

It rests on the observation that ductile metals in tension yield by slip on planes at about 45°, where Mohr's circle puts the largest shear stress. In a tensile test that shear stress is $\sigma_Y/2$ at yield, so Tresca takes $\sigma_Y/2$ as the critical shear stress for any stress state. In 3D each pair of principal stresses has a Mohr's circle, and the maximum shear stress is the radius of the largest of the three.

In plane stress the third principal stress is $\sigma_{III}=0$ and the condition becomes $\max(|\sigma_I-\sigma_{II}|,|\sigma_I|,|\sigma_{II}|)<\sigma_Y$. When $\sigma_I$ and $\sigma_{II}$ have the same sign the governing shear acts on a plane through the thickness and the condition is $\max(|\sigma_I|,|\sigma_{II}|)<\sigma_Y$; when they have opposite signs the in-plane shear governs and the condition is $|\sigma_I-\sigma_{II}|<\sigma_Y$. Plotted against $\sigma_I$ and $\sigma_{II}$ these give a hexagon. Pure shear reaches it at $\sigma_I=-\sigma_{II}=\sigma_Y/2$, so Tresca predicts a shear yield stress of $0.5\sigma_Y$.

Tresca is intuitive and conservative: its hexagon lies inside the von Mises ellipse, touching it only at uniaxial and equal biaxial states. It is less convenient because the principal stresses are needed and the governing term has to be chosen, and it ignores the shear stresses on the other principal planes. Forgetting the out-of-plane term in a pressure vessel wall, where both principal stresses are tensile, halves the predicted equivalent stress and gives an unsafe design.

![[s2_tresca_three_circles.png|850]]

## Related

- [[FEEG1002 B6 - Yield Criteria#1. The Tresca criterion|Tresca in B6]] · [[FEEG1002 B6 - Yield Criteria#Worked example - liquid hydrogen tank|vessel wall example]]
- [[Von Mises Yield Criterion]] · [[Principal Stresses]] · [[Mohr's Circle]]
- Year 2: [[Von Mises and Tresca Yield Criteria]] in finite element practice

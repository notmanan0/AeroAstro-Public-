---
title: "S-N Curves and Paris Law"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part C: Materials"
aliases: ["fatigue", "S–N curve", "fatigue limit", "fatigue life", "fatigue strength", "stress range", "stress amplitude", "Paris law", "fatigue crack growth", "damage-tolerant design", "ΔK"]
tags: [feeg1002, concept, materials, fatigue]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 C9 - Fatigue, Creep and Corrosion]]"]
related_concepts: ["[[Griffith Criterion and Fracture Toughness]]", "[[Paris Law]]", "[[S-N Curve and Basquin Law]]"]
sources: ["02 - Sources/Materials/Lectures/Lecture 14 - Failure of Materials 3 - Fatigue.pdf"]
---

# S-N Curves and Paris Law

Fatigue is failure under a fluctuating stress after many cycles, with the maximum stress below the yield strength; the S–N curve describes it as cycles to failure against stress amplitude, and the Paris law describes it as the growth rate of a crack that is already there.

A cycle between $\sigma_{max}$ and $\sigma_{min}$ has stress range $\Delta\sigma=\sigma_{max}-\sigma_{min}$ and stress amplitude $\sigma_a=\Delta\sigma/2$. The S–N curve, from rotating-bending tests on polished specimens, plots amplitude $S$ against cycles to failure $N$ on a log scale, and three quantities are read from it. The fatigue limit is the stress below which failure never occurs, where the curve becomes horizontal; only some alloys have one, notably steels (35–60 % of the tensile strength) and titanium alloys. The fatigue life is the number of cycles to failure at a given stress (read across, then down). The fatigue strength is the stress that causes failure at a given number of cycles (read up, then across), the measure used for alloys with no fatigue limit, such as aluminium alloys, typically at $10^7$ cycles. The fatigue limit and the fatigue strength are easily confused: the first is a stress with no failure at all, the second a stress for a given life.

![[m9_sn_curves.png|900]]

Damage-tolerant design assumes every structure contains cracks and asks how fast they grow. The crack tip is described by the stress intensity factor, so the cycle gives a range

$$
\Delta K=Y\Delta\sigma\sqrt{\pi a},\qquad \frac{da}{dN}=A(\Delta K)^m
$$

where the Paris law holds in region II of the log–log plot of growth rate against $\Delta K$, with $A$ and $m$ material constants ($m$ typically 2 to 4 for metals). A crack grows only while it is pulled open, so a compressive $\sigma_{min}$ is taken as zero. Integrating the Paris law from the initial (detectable) crack length $a_0$ to the critical length $a_c=\frac1\pi(K_{IC}/Y\sigma_{max})^2$ gives the life, which sets the inspection interval.

## Related

- [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Cyclic stress|cyclic stress]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#How a fatigue crack starts|how a crack starts]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#S–N curves|S–N curves]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#What affects fatigue life|what affects fatigue life]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Damage-tolerant design|damage-tolerant design]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#The Paris law|the Paris law]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Integrating the Paris law|integrating it]] · [[FEEG1002 C9 - Fatigue, Creep and Corrosion#Worked example - lifing a cracked plate with the Paris law|lifing example]]
- [[FEEG1002 Materials Tutorial 4 - Failure of Materials Solutions#Q5 - Reading the S–N curve|Tutorial 4, Q5]]
- [[Griffith Criterion and Fracture Toughness]]
- Year 2: [[S-N Curve and Basquin Law]] · [[Paris Law]] · [[SESA2028 M2 - Fatigue - Fracture Surfaces, Mechanisms and Lifing]]

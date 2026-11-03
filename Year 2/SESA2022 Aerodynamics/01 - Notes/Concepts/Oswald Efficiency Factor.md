---
title: "Oswald Efficiency Factor"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["span efficiency", "Oswald factor", "e", "delta and tau factors", "induced drag factor", "lift slope factor", "span efficiency factor"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Elliptic Lift Distribution]]", "[[Downwash and Induced Drag]]", "[[Maximum Lift-to-Drag Ratio]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-06.txt … 2025-11-13.txt (2025-26 transcripts)"]
---

# Oswald Efficiency Factor

The span efficiency factor $e$ measures how close a wing's induced drag comes to the elliptic ideal,

$$
C_{D_i} = \frac{C_L^2}{\pi eAR},\qquad e = \frac{1}{1+\delta},\qquad \delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2\ge0,
$$

and $\tau$ is the matching lift-slope factor, $a = a_0/[1+\frac{a_0}{\pi AR}(1+\tau)]$.

Only elliptic loading gives $e = 1$. Lifting-line theory typically gives 0.95–0.99 for other wings, and a whole aircraft, with its fuselage and viscous effects, typically 0.7–0.85. The Fourier coefficients say which way a wing departs from elliptic. For a symmetric wing only odd $n$ appear, and $B_3>0$ means less loading at mid-span and more outboard, which suggests a rectangular or low-taper planform, while $B_3<0$ means more centre-loaded than elliptic, which suggests a highly tapered or washed-out wing. $\delta$ and $\tau$ are both small and similar, so exam questions often say "assume $\delta = \tau$"; rectangular wings of aspect ratio 6–8 have $\delta\approx0.05$ and $\tau\approx0.15$–$0.2$.

Past-paper uses: $e = 0.9865$ with $B_3<0$ ([[SESA2022 Exam 2021-22 Solutions]] B Q2); $e = 0.9785$ with $B_3>0$ ([[SESA2022 Exam 2024-25 Solutions]] Q4); inferring $a_0$ from $a$ with $\tau$ ([[SESA2022 Exam 2013-14 Solutions]], [[SESA2022 Exam 2014-15 Solutions]], [[SESA2022 Exam 2023-24 Solutions]] B Q4); and [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T5 - Finite Wing Theory#Induced drag|T5 §3]]
- [[Elliptic Lift Distribution]] · [[Downwash and Induced Drag]] · [[Maximum Lift-to-Drag Ratio]]

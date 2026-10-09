---
title: "Oswald Efficiency Factor"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 5: Finite Wing Theory"
aliases: ["span efficiency", "Oswald factor", "e", "delta and tau factors", "induced drag factor", "lift slope factor"]
tags: [sesa2022, concept, finite-wing-theory]
status: complete
parent_lectures: ["[[SESA2022 T5 - Finite Wing Theory]]"]
related_concepts: ["[[Elliptic Lift Distribution]]", "[[Downwash and Induced Drag]]", "[[Maximum Lift-to-Drag Ratio]]"]
sources: ["02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf"]
---

# Oswald Efficiency Factor

## Definition

> [!note] Definition
> The span efficiency factor $e$ measures how close a wing's induced drag is to the elliptic ideal:
>
> $$C_{D_i} = \frac{C_L^2}{\pi eAR},\qquad e = \frac{1}{1+\delta},\qquad \delta = \sum_{n\ge2}n\left(\frac{B_n}{B_1}\right)^2\ge0$$
>
> $\tau$ is the corresponding **lift-slope factor**: $a = \dfrac{a_0}{1+\frac{a_0}{\pi AR}(1+\tau)}$.

## Explanation
- $e = 1$ only for elliptic loading. Otherwise $e<1$, typically 0.95–0.99 from lifting-line theory. For a whole aircraft (including fuselage and viscous effects), typical values are 0.7–0.85.
- **Reading the Fourier coefficients** (symmetric wing, odd $n$ only):
  - $B_3>0$: less loading at mid-span, more outboard. That suggests a **rectangular** or low-taper planform.
  - $B_3<0$: more centre-loaded than elliptic. That suggests a **highly tapered** or washed-out wing.
- $\delta$ and $\tau$ are both small and similar, so exams often say "assume $\delta = \tau$". Rectangular wings of $AR$ 6–8 have $\delta\approx0.05$ and $\tau\approx0.15$–$0.2$.

## Examples
- $e = 0.9865$ ($B_3<0$): [[SESA2022 Exam 2021-22 Solutions]] B Q2.
- $e = 0.9785$ ($B_3>0$): [[SESA2022 Exam 2024-25 Solutions]] Q4.
- Inferring $a_0$ from $a$ with $\tau$: [[SESA2022 Exam 2013-14 Solutions]], [[SESA2022 Exam 2014-15 Solutions]] and [[SESA2022 Exam 2023-24 Solutions]] B Q4.
- [[SESA2022 Examples Sheet 5 - Finite Wing Theory Solutions]].

## Related
- Parent lectures: [[SESA2022 T5 - Finite Wing Theory]]
- Related concepts: [[Elliptic Lift Distribution]], [[Downwash and Induced Drag]], [[Maximum Lift-to-Drag Ratio]]

## Sources
- `02 - Sources/Airfoils and Wings/Topic 5 Finite wing theory_v3_pdf.pdf`

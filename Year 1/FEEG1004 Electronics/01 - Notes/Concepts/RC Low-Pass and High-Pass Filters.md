---
title: "RC Low-Pass and High-Pass Filters"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["low-pass filter", "high-pass filter", "cut-off frequency", "corner frequency", "-3 dB", "first-order filter", "RL filter"]
tags: [feeg1004, concept, ac-circuits, filters]
status: complete
parent_lectures: ["[[FEEG1004 D3 - AC Filters and Bode Plots]]"]
related_concepts: ["[[Complex Impedance]]", "[[Bode Plot]]", "[[Decibels]]", "[[Transfer Function]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf"]
---

# RC Low-Pass and High-Pass Filters

## Definition

> [!note] Definition
>
> $$H_{LP} = \frac{1}{1 + j\omega RC},\qquad H_{HP} = \frac{j\omega RC}{1 + j\omega RC},\qquad \omega_c = \frac{1}{RC}:\ |H| = \tfrac{1}{\sqrt2}\ (-3\ \mathrm{dB}),\ \angle H = \mp45°$$

## Explanation
- A **complex potential divider**: the output is taken across C (low-pass) or R (high-pass).
- **Recognise** a filter from its limits: ω → 0 (C open, L short) and ω → ∞ (C short, L open).
- The Bode magnitude asymptotes are flat, then **∓20 dB/decade** past the corner.
- **RL equivalents**: series R with shunt L is high-pass; series L with shunt R is low-pass; $\omega_c = R/L$.
- A **load** on the output changes both the gain and the corner (Thévenin: $K$ and $R_1\parallel R_L$).

![[ee_d3_bode_rc_filters.png|700]]

## Examples
- −20 dB at 50 Hz with 1 kΩ needs 31.7 µF ($f_c$ = 5.03 Hz).
- Tutorial 8 Q1: a loaded low-pass with $K$ = 0.909 and $\omega_c$ = 110 rad/s.

## Related
- Topic notes: [[FEEG1004 D3 - AC Filters and Bode Plots]]
- Concepts: [[Complex Impedance]] · [[Potential Divider]]
- Year 2: [[Bode Plot]] · [[Transfer Function]] · [[Digital Filtering]] · [[Complementary Filter]] · [[Nyquist Sampling and Aliasing]]

## Sources
- AC Analysis 03 slides; Niu AC notes (RC filters)

---
title: "Complex Impedance"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["impedance", "reactance", "Z = R + jX", "generalised Ohm's law", "CIVIL", "inductive load", "capacitive load"]
tags: [feeg1004, concept, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
related_concepts: ["[[Phasor Representation]]", "[[RC Low-Pass and High-Pass Filters]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22-23 AC Analysis 02 - Impedance and Phasor Analysis - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Complex Impedance

## Definition

> [!note] Definition
> $$\mathbf V = Z\mathbf I,\qquad Z = R + jX,\qquad Z_R = R,\quad Z_L = j\omega L,\quad Z_C = \frac{1}{j\omega C} = -\frac{j}{\omega C}$$

## Explanation
- The real part is **resistance** and the imaginary part is **reactance** (opposition to AC through energy storage).
- **CIVIL**: a capacitor has I leading V; an inductor has V leading I (both by 90°).
- $X > 0$ means an **inductive** load (current lags); $X < 0$ a **capacitive** load (current leads). What matters is the net reactance.
- Frequency limits: L is a short at DC and open at high frequency; C is open at DC and a short at high frequency.
- Series and parallel rules, dividers and every DC theorem carry over with complex arithmetic.

![[ee_d2_reactance_frequency.png|640]]

## Examples
- Tutorial 7 Q3: 200 Ω + 150 mH + 2 µF at 400 Hz gives 268∠41.7° Ω.
- Niu Ex. 1: 3.6 + j4.8 − j6.25 = 3.88∠−21.9° Ω.

## Related
- Topic notes: [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- Concepts: [[Capacitance]] · [[Inductance]] · [[Phasor Representation]] · [[RC Low-Pass and High-Pass Filters]]
- Year 2: [[Transfer Function]]

## Sources
- AC Analysis 02–03 slides; Niu AC notes (Figs 11–19)

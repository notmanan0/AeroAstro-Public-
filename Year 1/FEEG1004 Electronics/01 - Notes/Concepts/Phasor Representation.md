---
title: "Phasor Representation"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["phasor", "complex phasor", "V angle theta", "Euler's formula", "phasor diagram"]
tags: [feeg1004, concept, ac-circuits, complex-numbers]
status: complete
parent_lectures: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]", "[[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]"]
related_concepts: ["[[Complex Impedance]]", "[[RMS Value]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf"]
---

# Phasor Representation

## Definition

> [!note] Definition
>
> $$v(t) = \sqrt2V\cos(\omega t + \theta) = \Re\{\sqrt2\,\mathbf Ve^{j\omega t}\},\qquad \mathbf V = Ve^{j\theta} = V\angle\theta = V\cos\theta + jV\sin\theta$$

## Explanation
- All quantities in a linear AC circuit share $\omega$, so the $e^{j\omega t}$ factor cancels. Only the complex amplitude (rms magnitude and phase) remains.
- $d/dt\to j\omega$ and $\int dt\to1/j\omega$: differential equations become algebra.
- Phasors add as vectors: KCL and KVL hold for phasors, not for magnitudes.
- **Leads/lags**: a larger angle leads.
- **Convert** sine to cosine first: $\sin x = \cos(x - 90°)$.

![[ee_d1_phasors.png|700]]

## Examples
- $60\angle0 + 40\angle-60°$ = 87.2∠−23.4° V.
- Tutorial 7 Q1: $83.6\sin(400t - 15°)$ gives 59.1∠−105° V.

## Related
- Topic notes: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]
- Concepts: [[Complex Impedance]] · [[RMS Value]]
- Year 2: [[Frequency Response Function]] · [[Complex Fourier Series]]

## Sources
- AC Analysis 01 slides; Niu AC notes (Figs 7–9)

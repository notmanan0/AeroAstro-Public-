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
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf", "02 - Sources/S2 AC Analysis/S2 AC Analysis Lecture Notes 2021 - Niu.pdf", "AC Analysis 01 slides", "Niu AC notes (Figs 7–9)"]
---

# Phasor Representation

A phasor is the complex number that holds the rms magnitude and phase of a sinusoid at a known angular frequency $\omega$.

$$
v(t) = \sqrt2V\cos(\omega t + \theta) = \Re\{\sqrt2\,\mathbf Ve^{j\omega t}\},\qquad \mathbf V = Ve^{j\theta} = V\angle\theta = V\cos\theta + jV\sin\theta
$$

Every voltage and current in a linear AC circuit shares the same $\omega$, so the factor $e^{j\omega t}$ cancels from every equation and only the complex amplitude remains. Differentiation becomes multiplication by $j\omega$ and integration becomes division by $j\omega$, which turns the circuit's differential equations into algebra. Phasors add as vectors, so KCL and KVL hold for the phasors but not for their magnitudes. Of two phasors, the one with the larger angle leads. A waveform given as a sine is converted to a cosine before its phase is read off, using $\sin x = \cos(x - 90°)$.

![[ee_d1_phasors.png|700]]

Adding $60\angle0 + 40\angle-60°$ as complex numbers gives 87.2∠−23.4° V. In Tutorial 7 Q1, $83.6\sin(400t - 15°)$ becomes $83.6\cos(400t - 105°)$, with phasor 59.1∠−105° V rms.

## Related

- [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] · [[FEEG1004 D2 - Impedance and Phasor Circuit Analysis]]
- [[Complex Impedance]] · [[RMS Value]]
- Year 2: [[Frequency Response Function]] · [[Complex Fourier Series]]
- Sources: AC Analysis 01 slides; Niu AC notes (Figs 7–9)

---
title: "Random Vibration and Acceleration PSD"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Astronautics"
aliases: ["Power spectral density", "PSD", "Acceleration PSD", "g RMS", "Dynamic acceleration", "Random vibration"]
tags: [sesa1015, concept, astronautics, launch, vibration]
status: complete
parent_lectures: ["[[SESA1015 A03 - Launch Environment]]"]
related_concepts: ["[[Launch Environment Loads]]", "[[Sound Pressure Level]]", "[[RMS Value]]", "[[Resonance]]"]
sources: ["Astronautics Part 2 (Environment), p. 42"]
---

# Random Vibration and Acceleration PSD

Random vibration is an acceleration that never repeats and has no single frequency; it is described by its acceleration power spectral density $G(f)$, the mean-square acceleration per hertz of bandwidth, in $g^2$/Hz, and its RMS value is $g_{RMS}=\sqrt{\int G\,df}$.

The definition works like a bank of narrow filters: the part of the signal in a band $\Delta f$ around $f$ has mean square $G(f)\Delta f$, and because the bands are uncorrelated their mean squares add, so the total mean square is the area under the PSD. Launch-vehicle envelopes are drawn as straight lines on log–log axes. A segment from $(f_1,G_1)$ to $(f_2,G_2)$ is the power law $G=G_1(f/f_1)^m$ with $m=\log(G_2/G_1)/\log(f_2/f_1)$, whose area is $\frac{G_1f_1}{m+1}[(f_2/f_1)^{m+1}-1]$ for $m\neq-1$ and $G_1f_1\ln(f_2/f_1)$ for $m=-1$. Slopes are quoted in dB per octave, $3.01m$, so $+6$ dB/oct is $m\approx2$ and a flat plateau is $m=0$.

The Ariane envelope on p. 42 (corners near 24, 160, 700 and 2000 Hz, plateau 0.04 $g^2$/Hz) has an area of about 51 $g^2$, so $g_{RMS}\approx7.1$ g; the Shuttle envelope (plateau 0.025 $g^2$/Hz from 130 to 300 Hz) gives about 8.1 $g^2$ and 2.8 g. If the signal is Gaussian, it stays within $\pm3g_{RMS}$ 99.7% of the time, so peaks near 21 g occur on the Ariane envelope.

Two traps are common. A PSD value is not an acceleration and cannot be compared directly with a peak or a load factor; it must be integrated over a band first. And the input PSD is not what a component feels: a part with a natural frequency inside the plateau responds far more strongly than the input, by an amount set by its damping ([[Resonance]]), which is why spacecraft are given minimum natural-frequency requirements and are shaken on a test table to the envelope before flight.

## Related

- Topic: [[SESA1015 A03 - Launch Environment]] (§3)
- Concepts: [[Launch Environment Loads]] · [[Sound Pressure Level]] · [[RMS Value]] · [[Resonance]] · [[Damping Ratio and Natural Frequency]]
- Builds on: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Sources: Astronautics Part 2, p. 42

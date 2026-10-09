---
title: "RMS Value"
module: "FEEG1004 Electronics"
type: concept
stream: "Part D: AC Circuit Analysis"
aliases: ["root mean square", "rms", "effective value", "Vp/sqrt2"]
tags: [feeg1004, concept, ac-circuits]
status: complete
parent_lectures: ["[[FEEG1004 D1 - AC Waveforms, RMS and Phasors]]"]
related_concepts: ["[[Phasor Representation]]", "[[Active, Reactive and Apparent Power]]"]
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf"]
---

# RMS Value

## Definition

> [!note] Definition
>
> $$V_{rms} = \sqrt{\frac{1}{T}\int_0^Tv^2\,dt},\qquad V_{rms} = \frac{V_p}{\sqrt2}\approx0.707V_p\ \text{(sinusoid)}$$
>
> It is the DC value that gives the same average power in a resistor.

## Explanation
- For a sinusoid, $p = v^2/R$ averages to $V_p^2/2R$, hence the factor $1/\sqrt2$.
- **Quoted AC values are rms**: 230 V mains is 325 V peak; meters read rms. In this course phasor magnitudes are rms.
- **Other shapes differ**. A square wave has rms = peak. A half-wave rectified sine has an average of only $V_p/\pi$ (used by rectifier meters, Tutorial 3 Q4).

![[ee_d1_ac_waveform_rms.png|700]]

## Examples
- $230\sqrt2\cos(100\pi t + \pi/6)$ is 230 V rms at 50 Hz.
- A 2463 V peak turbo-generator EMF is 1742 V rms.

## Related
- Topic notes: [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] · [[FEEG1004 D4 - AC Power and Power Factor]]
- Concepts: [[Phasor Representation]] · [[Active, Reactive and Apparent Power]]

## Sources
- AC Analysis 01 slides; Niu AC notes (Fig. 2)

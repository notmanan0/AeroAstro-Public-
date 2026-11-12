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
sources: ["02 - Sources/S2 AC Analysis/S2-W22 AC Analysis 01 - Phasors and Complex Numbers - Lecture Slides.pdf", "Niu AC notes, Fig. 2"]
---

# RMS Value

The rms (root mean square) value of a periodic voltage or current is the DC value that would deliver the same average power to a resistor.

$$
V_{rms} = \sqrt{\frac{1}{T}\int_0^Tv^2\,dt},\qquad V_{rms} = \frac{V_p}{\sqrt2}\approx0.707V_p\ \text{(sinusoid)}
$$

For a sinusoid the instantaneous power $p = v^2/R$ averages to $V_p^2/2R$ over a cycle, which is where the factor $1/\sqrt2$ comes from. Quoted AC values are rms unless stated otherwise: 230 V mains is 325 V peak, meters read rms, and phasor magnitudes are rms throughout.

The factor $1/\sqrt2$ belongs to the sinusoid only. A square wave has an rms value equal to its peak, and a half-wave rectified sine has an average of only $V_p/\pi$, which is the quantity a rectifier meter responds to (Tutorial 3 Q4).

![[ee_d1_ac_waveform_rms.png|700]]

The waveform $230\sqrt2\cos(100\pi t + \pi/6)$ is 230 V rms at 50 Hz, and a turbo-generator EMF of 2463 V peak is 1742 V rms.

## Related

- [[FEEG1004 D1 - AC Waveforms, RMS and Phasors]] · [[FEEG1004 D4 - AC Power and Power Factor]]
- [[Phasor Representation]] · [[Active, Reactive and Apparent Power]]
- Sources: AC Analysis 01 slides; Niu AC notes (Fig. 2)

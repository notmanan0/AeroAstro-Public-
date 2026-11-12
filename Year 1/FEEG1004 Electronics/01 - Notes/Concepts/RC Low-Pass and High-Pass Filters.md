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
sources: ["02 - Sources/S2 AC Analysis/S2-W24 AC Analysis 03 - Filters and Loads - Lecture Slides.pdf", "Niu AC notes, RC filters"]
---

# RC Low-Pass and High-Pass Filters

A first-order RC filter is a complex potential divider of a resistor and a capacitor: taking the output across $C$ gives a low-pass filter, and taking it across $R$ gives a high-pass filter.

$$
H_{LP} = \frac{1}{1 + j\omega RC},\qquad H_{HP} = \frac{j\omega RC}{1 + j\omega RC},\qquad \omega_c = \frac{1}{RC}:\ |H| = \tfrac{1}{\sqrt2}\ (-3\ \mathrm{dB}),\ \angle H = \mp45°
$$

A filter can be recognised from its two limits. As $\omega\to0$ a capacitor is an open circuit and an inductor a short; as $\omega\to\infty$ the capacitor is a short and the inductor open. Whichever limit leaves the output connected to the input is the pass band. On a Bode plot the magnitude asymptotes are flat in the pass band and fall at 20 dB/decade (low-pass) or rise at 20 dB/decade (high-pass) on the other side of the corner.

The same circuits can be built with an inductor. A series $R$ with a shunt $L$ is high-pass, a series $L$ with a shunt $R$ is low-pass, and the corner is at $\omega_c = R/L$. A load on the output changes both the gain and the corner: replacing the source and divider by their Thévenin equivalent gives a gain $K$ and an effective resistance $R_1\parallel R_L$.

![[ee_d3_bode_rc_filters.png|700]]

To attenuate 50 Hz by 20 dB with a 1 kΩ resistor needs 31.7 µF, which puts $f_c$ at 5.03 Hz. Tutorial 8 Q1 is a loaded low-pass filter with $K$ = 0.909 and $\omega_c$ = 110 rad/s.

## Related

- [[FEEG1004 D3 - AC Filters and Bode Plots]]
- [[Complex Impedance]] · [[Potential Divider]]
- Year 2: [[Bode Plot]] · [[Transfer Function]] · [[Digital Filtering]] · [[Complementary Filter]] · [[Nyquist Sampling and Aliasing]]
- Sources: AC Analysis 03 slides; Niu AC notes (RC filters)

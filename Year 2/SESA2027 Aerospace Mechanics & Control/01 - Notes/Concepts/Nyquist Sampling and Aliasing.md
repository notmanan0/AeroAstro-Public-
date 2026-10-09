---
title: "Nyquist Sampling and Aliasing"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["Nyquist", "Nyquist frequency", "aliasing", "sampling theorem", "anti-aliasing filter", "Shannon"]
tags: [sesa2027, concept, sensors, digitisation]
status: complete
parent_lectures: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[ADC Quantisation and Resolution]]", "[[Digital Filtering]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# Nyquist Sampling and Aliasing

## Definition

> [!note] Definition
> Sampling at $f_s = 1/T_s$ can represent only frequencies up to the **Nyquist frequency** $f_N = f_s/2$. The Nyquist–Shannon criterion for no aliasing is
>
> $$f_s>2f_{max}$$
>
> A component at $f>f_N$ appears after sampling at the **alias frequency**
>
> $$f_{alias} = |f-mf_s|,\qquad m\in\mathbb Z\ \text{chosen so that}\ 0\le f_{alias}\le f_N$$

## Explanation
- **Aliasing is a folding**: high-frequency content (vibration, EMI) reappears as a false **low-frequency** signal. The flight computer "sees motion that is not physically there".
- **It is irreversible**: after sampling, the alias and a real signal at that frequency give identical samples.
- **Anti-aliasing filter**: an **analogue** low-pass placed **before** the ADC, with $f_c\le f_N$, i.e. $\tau = RC\ge1/(\pi f_s)$.
  - It costs phase lag in the control band.
  - A higher $f_s$ allows a higher $f_c$, so less lag.
- **Practice**: sample at about $10f_{max}$, not just $2f_{max}$, to leave room for the filter roll-off and to limit the delay.

## Examples
- PS C Q10: manoeuvres up to 8 Hz need $f_s>16$ Hz. At $f_s = 50$ Hz, $f_N = 25$ Hz, and a 70 Hz vibration aliases to $|70-50| = 20$ Hz ([[SESA2027 Part C Problem Sheet Solutions]]).

![[amc_psc_q10_aliasing.png|620]]

## Related
- [[ADC Quantisation and Resolution]] · [[Digital Filtering]] · [[Gain and Phase Margins]] · [[Measurement Chain]]

## Sources
- Lectures 2.07, 3.07

---
title: "Nyquist Sampling and Aliasing"
module: "SESA2027 Aerospace Mechanics & Control"
type: concept
stream: "Part C: Sensing Systems"
aliases: ["Nyquist", "Nyquist frequency", "aliasing", "sampling theorem", "anti-aliasing filter", "Shannon", "folding frequency"]
tags: [sesa2027, concept, sensors, digitisation]
status: complete
parent_lectures: ["[[SESA2027 B4 - Robustness, Stability vs Manoeuvrability and Design Process]]", "[[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering]]"]
related_concepts: ["[[ADC Quantisation and Resolution]]", "[[Digital Filtering]]", "[[Gain and Phase Margins]]"]
sources: ["02 - Sources/Lectures/Lecture 2.07.pdf", "02 - Sources/Lectures/Lecture 3.07.pdf"]
---

# Nyquist Sampling and Aliasing

Sampling at $f_s = 1/T_s$ can only represent frequencies up to the **Nyquist frequency** $f_N = f_s/2$, so the Nyquist–Shannon condition for no aliasing is $f_s>2f_{max}$. A component above $f_N$ shows up after sampling at the alias frequency

$$
f_{alias} = |f-mf_s|,\qquad m\in\mathbb Z\ \text{chosen so that}\ 0\le f_{alias}\le f_N .
$$

Aliasing folds high-frequency content, such as structural vibration or EMI, back into a false low-frequency signal, so the flight computer sees motion that isn't physically there. It can't be undone after sampling, because the alias and a real signal at that frequency give identical samples. In PS C Q10, manoeuvres up to 8 Hz need $f_s>16$ Hz; at $f_s = 50$ Hz, $f_N = 25$ Hz and a 70 Hz vibration aliases to $|70-50| = 20$ Hz, inside the control band ([[SESA2027 Part C Problem Sheet Solutions]]).

The defence is an analogue low-pass anti-alias filter before the ADC, with its cut-off at or below $f_N$, which for an RC filter means $\tau = RC\ge1/(\pi f_s)$. That filter adds phase lag in the control band, and a higher sampling rate allows a higher cut-off and less lag. In practice systems sample at around $10f_{max}$ rather than the bare $2f_{max}$, to leave room for the filter's roll-off and keep the delay down.

![[amc_psc_q10_aliasing.png|620]]

## Related

- Why $f$ and $f-mf_s$ give the same samples: [[SESA2027 C3 - Signal Conditioning, Digitisation and Digital Filtering#5. Time transformation: sampling and aliasing|C3 §5]]
- [[ADC Quantisation and Resolution]] · [[Digital Filtering]] · [[Gain and Phase Margins]] · [[Measurement Chain]]

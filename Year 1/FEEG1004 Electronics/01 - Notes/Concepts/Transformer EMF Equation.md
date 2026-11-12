---
title: "Transformer EMF Equation"
module: "FEEG1004 Electronics"
type: concept
stream: "Part C: Electric Machines"
aliases: ["4.44 f N Phi", "EMF equation", "peak flux density", "core saturation"]
tags: [feeg1004, concept, machines, transformer]
status: complete
parent_lectures: ["[[FEEG1004 C3 - Transformers and AC Power Transmission]]"]
related_concepts: ["[[Ideal Transformer]]", "[[Magnetic Flux and Flux Density]]"]
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf", "Sharkh notes §3.5 example", "02 - Sources/Tutorial Sheets/Tutorial Sheet 05 - Electric Machines 1 - Faraday, Generators & Transformers.pdf"]
---

# Transformer EMF Equation

The transformer EMF equation gives the RMS voltage induced in a winding of $N$ turns linked by a sinusoidal flux $\Phi = \Phi_m\sin2\pi ft$:

$$
E_{rms} = \frac{2\pi}{\sqrt2}fN\Phi_m = 4.44\,fN\Phi_m,\qquad B_m = \frac{\Phi_m}{A_{core}}
$$

Read the other way round, the applied voltage fixes the flux amplitude, $\Phi_m = V/(4.44fN)$. The peak flux density $B_m$ must stay below about 1.5 T, or the core saturates and the magnetising current and core losses rise steeply. A 500 V, 50 Hz winding of 400 turns on a 60 cm² core has $\Phi_m$ = 5.63 mWb and $B_m$ = 0.94 T. A 230 V, 50 Hz winding of 70 turns on 100 cm² reaches $B_m$ = 1.48 T, at the limit.

The equation also sets how transformer size scales with frequency. At a higher $f$ less flux, and so a smaller core, handles the same voltage, which is why aircraft use compact 400 Hz transformers and switch-mode converters working at kHz use tiny ones.

![[ee_c3_transformer_transmission.png|700]]

## Related

- [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- [[Ideal Transformer]] · [[RMS Value]] · [[Magnetic Flux and Flux Density]]
- Sources: Sharkh notes §3.5 example; Tutorial Sheet 5

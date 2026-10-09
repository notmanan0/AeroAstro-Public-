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
sources: ["02 - Sources/S2 Machines/S2 Electric Machines Notes - Sharkh.pdf"]
---

# Transformer EMF Equation

## Definition

> [!note] Definition
> For a sinusoidal flux $\Phi = \Phi_m\sin2\pi ft$ linking $N$ turns:
>
> $$E_{rms} = \frac{2\pi}{\sqrt2}fN\Phi_m = 4.44\,fN\Phi_m,\qquad B_m = \frac{\Phi_m}{A_{core}}$$

## Explanation
- The applied voltage **fixes** the flux amplitude: $\Phi_m = V/(4.44fN)$.
- Keep $B_m$ below about 1.5 T or the core saturates, and the magnetising current and losses soar.
- **Frequency scaling**: at higher $f$, less flux (a smaller core) handles the same voltage. Hence compact 400 Hz aircraft transformers and tiny kHz switch-mode converters.

## Examples
- 500 V, 50 Hz, 400 turns, 60 cm²: $\Phi_m$ = 5.63 mWb, $B_m$ = 0.94 T.
- 230 V, 50 Hz, 70 turns, 100 cm²: $B_m$ = 1.48 T, at the limit.

![[ee_c3_transformer_transmission.png|700]]

## Related
- Topic notes: [[FEEG1004 C3 - Transformers and AC Power Transmission]]
- Concepts: [[Ideal Transformer]] · [[RMS Value]] · [[Magnetic Flux and Flux Density]]

## Sources
- Sharkh notes §3.5 example; Tutorial Sheet 5

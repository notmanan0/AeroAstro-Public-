---
title: "Logarithmic Decrement"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["log decrement", "Delta = ln(x1/x2)", "damping from decay", "zeta = Delta/2pi"]
tags: [feeg1002, concept, dynamics, vibration, damping]
status: complete
parent_lectures: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Frequency Response Function]]"]
sources: []
---

# Logarithmic Decrement

## Definition

> [!note] Definition
> For an underdamped free response, successive peaks decay by the constant ratio $e^{\zeta\omega_nT_d}$:
>
> $$\Delta = \ln\frac{x_1}{x_2} = \frac1n\ln\frac{x_1}{x_{n+1}}\approx2\pi\zeta\quad(\zeta\ll1);\qquad \text{exactly } \zeta = \frac{\Delta}{\sqrt{4\pi^2 + \Delta^2}}$$

## Explanation

- Use **many cycles** $n$ for accuracy.
- It applies equally to displacement, velocity or acceleration peaks, since all share the envelope $e^{-\zeta\omega_nt}$.
- If the frequency is known, $n = f_n\times$ (elapsed time).
- Decay to a fraction $r$ takes $t = \ln(1/r)/(\zeta\omega_n)$, and $\zeta\omega_n = c/2m$. So the decay time scales with $m/c$, independent of $k$.

## Examples

- **Speed camera** (Lecture 6): 2 → 0.02 m/s over 19.7 cycles gives $\Delta = 0.234$ and $\zeta = 0.0372$.
- **Tutorial 6 Q5**: a tenfold decay over 5 cycles gives $\Delta = 0.461$ and $\zeta = 0.0733$.

![[d_log_decrement.png|700]]

## Related

- Topic notes: [[FEEG1002 D6 - Single Degree of Freedom Vibration]]
- Concepts: [[Damping Ratio and Natural Frequency]] · [[Equivalent Spring Stiffness]] · [[Frequency Response Function]]
- Year 2: Pole real part $-\zeta\omega_n$ and time to half amplitude in [[Damping Ratio and Natural Frequency]] · mode damping from flight-test time histories, [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]

## Sources

- Dynamics Lecture 6.2b

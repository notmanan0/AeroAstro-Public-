---
title: "Logarithmic Decrement"
module: "FEEG1002 Mechanics, Materials and Structures"
type: concept
stream: "Part D: Dynamics"
aliases: ["log decrement", "Delta = ln(x1/x2)", "damping from decay", "zeta = Delta/2pi", "logarithmic decay", "free-decay method"]
tags: [feeg1002, concept, dynamics, vibration, damping]
status: complete
date: 2026-11-05
parent_lectures: ["[[FEEG1002 D6 - Single Degree of Freedom Vibration]]"]
related_concepts: ["[[Damping Ratio and Natural Frequency]]", "[[Equivalent Spring Stiffness]]", "[[Frequency Response Function]]"]
sources: ["02 - Sources/Dynamics/Lectures/Lecture 06 - SDOF Vibration.pdf"]
---

# Logarithmic Decrement

The logarithmic decrement $\Delta$ is the natural logarithm of the ratio of two successive peaks of an underdamped free vibration; it measures the damping ratio from a decaying record.

$$
\Delta=\ln\frac{x_1}{x_2}=\frac{2\pi\zeta}{\sqrt{1-\zeta^2}}\approx2\pi\zeta
$$

The underdamped response is $x(t)=e^{-\zeta\omega_nt}(A_1\cos\omega_dt+A_2\sin\omega_dt)$. Successive peaks are one damped period $T_d=2\pi/\omega_d$ apart, and the bracket repeats exactly over that period, so the ratio of any two successive peaks is fixed by the envelope alone, $x_1/x_2=e^{\zeta\omega_nT_d}$. Taking logs and using $\omega_d=\omega_n\sqrt{1-\zeta^2}$ gives the result above. For light damping $\zeta\approx\Delta/2\pi$. The exact inverse follows from squaring, $\Delta^2(1-\zeta^2)=4\pi^2\zeta^2$, so $\zeta=\Delta/\sqrt{4\pi^2+\Delta^2}$.

A single pair of peaks gives a poor estimate, so the decrement is measured over $n$ cycles. The logs of the successive ratios add, so

$$
\Delta=\frac1n\ln\frac{x_1}{x_{n+1}}
$$

If the record is given as a time rather than a count, $n=f_n\times$ (elapsed time), with $f_n$ in Hz. Velocity peaks decay by the same factor per cycle, since the velocity carries the same envelope and the same periodic bracket.

For the speed camera on its post ($f_n=6.57$ Hz), the velocity falls from 2 m/s to 0.02 m/s in 3 s, which is 19.7 cycles. Then $\Delta=\ln100/19.7=0.234$ and $\zeta\approx0.037$, light enough for the approximation to hold.

The decay rate of the envelope is $\zeta\omega_n=c/2m$, so the time for the vibration to die away is set by $m/c$ and does not depend on the stiffness. A frequent slip is to put $\omega_d$ into the envelope or to mix rad/s and Hz when counting cycles.

![[d_log_decrement.png|700]]

## Related

- [[FEEG1002 D6 - Single Degree of Freedom Vibration#Logarithmic decrement|derivation in D6]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Damping ratio and the three regimes|damping ratio and regimes]] · [[FEEG1002 D6 - Single Degree of Freedom Vibration#Speed camera on a cantilever post|speed camera]]
- [[Equivalent Spring Stiffness]]
- Year 2: [[Damping Ratio and Natural Frequency]] (pole real part $-\zeta\omega_n$) · [[Frequency Response Function]] · mode damping from flight-test records, [[SESA2027 A3 - Longitudinal Dynamic Modes - SPO and Phugoid]]

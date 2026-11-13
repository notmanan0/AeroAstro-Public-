---
title: "Elevator Angle to Trim"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Elevator to trim", "Trim gradient", "Tailplane angle to trim", "Stick-fixed longitudinal control"]
tags: [sesa1015, concept, trim, elevator]
date: 2026-11-07
status: complete
parent_lectures: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
related_concepts: ["[[Static Margin and Tail Volume]]", "[[Neutral Point and Static Margin]]"]
sources: ["Mechanics of Flight Course Notes §8.1.3 and §8.2.1, pp. 54–56", "Mechanics of Flight Lecture Slides v2, pp. 212–217"]
---

# Elevator Angle to Trim

The elevator angle to trim is the elevator deflection $\eta$ (the slides' $\delta_e$, positive trailing edge down) that makes the pitching moment about the CG zero at the angle of attack a flight condition needs. It changes with speed at a rate proportional to the static margin.

Setting $C_{m_G}=0$ in the moment equation with a tailplane gives

$$
\bar Va_{2T}\,\eta=C_{m0}+(h-h_0)a_1\alpha-\bar Va_{1T}\left[\alpha_s+\alpha\left(1-\frac{d\varepsilon}{d\alpha}\right)\right],
$$

or, grouped with the zero-lift moment $C_{M_0}=C_M+V_{HT}a_T(\varepsilon_0-i_H)$,

$$
\delta_e=\frac{C_{M_0}+(dC_{M_{CG}}/d\alpha)\,\alpha_{req}}{V_{HT}\,(dC_{L_T}/d\delta_e)},\qquad\alpha_{req}=\frac{2W}{\rho SV^2a}.
$$

On an all-moving tailplane the setting $\alpha_s$ is varied instead, with $a_{1T}$ in place of $a_{2T}$. Graphically the elevator shifts the $C_{m_G}$–$\alpha$ line up or down without changing its slope, so it moves the trim point; moving the CG changes the slope instead.

In level flight $V^2C_L$ is constant, so $dC_L/dV=-2C_L/V$. Combining that with $d\eta/d\alpha=-a_1K_n/(\bar Va_{2T})$ from the trim equation gives the trim gradient

$$
\frac{d\eta}{dV}=\frac{2C_L}{V}\,\frac{K_n}{\bar Va_{2T}}.
$$

A stable aircraft needs more trailing-edge-down elevator as it speeds up and more up-elevator to fly slower; the gradient is steepest at low speed (high $C_L$) and with a large static margin (forward CG). At the neutral point the gradient vanishes, which is how flight tests locate it. For an example aircraft ($W=22.7$ kN, $S=19$ m², $a=0.08$/deg, $C_{M_0}=0.06$, $dC_{M_{CG}}/d\alpha=-0.0133$/deg, $V_{HT}=0.34$, $dC_{L_T}/d\delta_e=0.04$/deg) at 61 m/s, $\alpha_{req}=6.55°$, $\delta_e=-2.00°$ (2° trailing edge up) and $d\eta/dV=0.21$° per m/s.

The largest up-elevator is needed at the stall, $\alpha=\alpha_{stall}$, and with the CG furthest forward, which is how elevator power sets the forward CG limit. The download the tail then carries must be added to the wing lift, which costs trim drag.

![[mof_m11_elevator_trim_speed.png|850]]

## Related

- Topic: [[SESA1015 M11 - Longitudinal Trim and Static Stability]] · Solutions: [[SESA1015 T07 - Trim and Static Stability Solutions]]
- Concepts: [[Static Margin and Tail Volume]]
- Later: [[Neutral Point and Static Margin]] (flight-test margin from $d\eta/dC_L$) · [[Stick-Fixed vs Stick-Free Stability]] (SESA2022)

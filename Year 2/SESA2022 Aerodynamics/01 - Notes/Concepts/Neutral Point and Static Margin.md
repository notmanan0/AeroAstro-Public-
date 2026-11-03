---
title: "Neutral Point and Static Margin"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["neutral point", "static margin", "H_s", "h_n", "pitch stiffness", "tail volume ratio"]
tags: [sesa2022, sesa2027, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[Stick-Fixed vs Stick-Free Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf", "02 - Sources/Lectures/SESA2022 Lecture 2025-11-14.txt … 2025-11-25.txt (2025-26 transcripts)"]
---

# Neutral Point and Static Margin

The **neutral point** $h_n$ is the CG position at which the aircraft's pitching moment doesn't change with incidence, $dC_{M_{CG}}/d\alpha = 0$, so the aircraft is neutrally stable. The **static margin** $H_s$ is the non-dimensional distance of the CG ahead of it:

$$
h_n = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad H_s = h_n-h,\qquad \frac{dC_{M_{CG}}}{dC_{L^*}} = -H_s .
$$

The aircraft is statically stable if $H_s>0$, with the CG ahead of the neutral point. The neutral point is in effect the aerodynamic centre of the whole aircraft.

It comes from the moment slope, $dC_{M_{CG}}/d\alpha = C_{L^*_\alpha}(h-h_0)-C_{L_{T,\alpha}}K$, in which the wing term is destabilising when the CG is aft of the wing's aerodynamic centre and the tail term is stabilising. Stick fixed, the tail lift slope is $C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)$ with $k = a_1\pi A_Te_T/(\pi A_Te_T+a_1)$, so downwash from the wing ($\epsilon_\alpha$) reduces the tail's effectiveness and moves $h_n$ forward. Transports typically have $H_s\approx0.05$–$0.15$; relaxed-stability fighters such as the X-29 and F-16 have negative margins and need fly-by-wire. More margin means more stability but a larger trim load and less manoeuvrability ([[Stability vs Manoeuvrability]]).

In flight test the stick-fixed margin is measured from the elevator angle needed to trim,

$$
H_{s,fixed} = -Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}},
$$

by plotting $d\eta/dC_{L^*}$ against CG position and extrapolating to zero. In SESA2027 the pitch-stiffness derivative $M_w = -H_sC_{L^*_\alpha}$ links the static margin to the short-period frequency ([[Short Period Oscillation]]). Practice: [[SESA2022 Examples Sheet 6 - Static Stability Solutions]] and [[SESA2022 Static Stability Past Paper Questions Solutions]].

## Related

- Full derivation and worked examples: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability#Neutral point and static margin|T6 §3]]
- [[Stick-Fixed vs Stick-Free Stability]] · [[Manoeuvre Point and Manoeuvre Margin]] · [[Aerodynamic Centre and Centre of Pressure]]

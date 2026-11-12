---
title: "Static Margin and Tail Volume"
module: "SESA1015 Intro to Aero & Astro"
type: concept
stream: "Mechanics of Flight"
aliases: ["Tail Volume Coefficient", "Tail volume ratio", "First-Year Static Margin", "C of G margin", "V_HT"]
tags: [sesa1015, concept, static-margin, tail-volume, stability]
date: 2026-09-27
status: complete
parent_lectures: ["[[SESA1015 M11 - Longitudinal Trim and Static Stability]]"]
related_concepts: ["[[Neutral Point and Static Margin]]", "[[Elevator Angle to Trim]]", "[[Downwash and Induced Drag]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["Mechanics of Flight Course Notes §8.1–8.2, pp. 49–55", "Mechanics of Flight Lecture Slides v2, pp. 203–211"]
---

# Static Margin and Tail Volume

The tail volume coefficient $\bar V=S_Tl_T/(S\bar c)$ (the slides' $V_{HT}$) measures how much pitching moment a tailplane of area $S_T$ at arm $l_T$ behind the wing aerodynamic centre can produce, relative to the wing. The static margin $K_n=h_n-h$ is the distance of the centre of gravity ahead of the neutral point, as a fraction of the wing chord; the aircraft is statically stable in pitch, stick fixed, when it is positive.

With nose-up moments positive and positions measured from the wing leading edge in chords, the moment about the CG of a wing-body-tail combination is $C_{m_G}=C_{m0}+(h-h_0)C_L-\bar VC_{L_T}$. The tail sits in the wing's downwash, so its angle of attack is $\alpha_T=\alpha(1-d\varepsilon/d\alpha)+\alpha_s$, and with $C_L=a_1\alpha$, $C_{L_T}=a_{1T}\alpha_T+a_{2T}\eta$ the slope of the moment curve is

$$
\frac{dC_{m_G}}{d\alpha}=a_1(h-h_0)-\bar Va_{1T}\left(1-\frac{d\varepsilon}{d\alpha}\right).
$$

The wing term destabilises when the CG is behind the wing AC; the tail term always stabilises. Setting the slope to zero defines the neutral point,

$$
h_n=h_0+\bar V\,\frac{a_{1T}}{a_1}\left(1-\frac{d\varepsilon}{d\alpha}\right),
$$

and subtracting the two equations gives $dC_{m_G}/d\alpha=-a_1K_n$, or $dC_{m_G}/dC_L=-K_n$. The neutral point is the aerodynamic centre of the whole aircraft and the rearmost allowable CG. A bigger tail, a longer tail arm, a more effective tail ($a_{1T}$) and less downwash all move it aft and raise the margin for a given CG.

Sizing runs the other way. A required margin fixes $h_n=h+K_n$, the neutral-point equation gives $\bar V=(h_n-h_0)(a_1/a_{1T})/(1-d\varepsilon/d\alpha)$, and $S_T=\bar VS\bar c/l_T$, with $\bar c=S/b=\sqrt{S/A}$ for a wing of aspect ratio $A$. For Revision Q8 ($h=0.51$, $K_n=0.18$, $a_1=4.92$, $a_{1T}=5.02$, $d\varepsilon/d\alpha=0.21$, $S=1.39$ m², $A=7$, $l_T=0.93$ m) this gives $\bar V=0.546$ and $S_T=0.364$ m².

A large margin is not free: it needs large elevator angles to change the trimmed speed (the trim gradient $d\eta/dV$ is proportional to $K_n$), costs trim drag because the tail must push down harder, and makes the aircraft less manoeuvrable. The forward CG limit is set by elevator power at maximum $C_L$, the aft limit by the neutral point less a safety margin. A common slip is to measure $l_T$ from the CG instead of from the wing AC, as the course defines it; another is to drop the factor $1-d\varepsilon/d\alpha$.

## Related

- Topic: [[SESA1015 M11 - Longitudinal Trim and Static Stability]] · Solutions: [[SESA1015 T07 - Trim and Static Stability Solutions]]
- Concepts: [[Elevator Angle to Trim]] · [[Aerodynamic Centre and Centre of Pressure]] · [[Downwash and Induced Drag]]
- Later: [[Neutral Point and Static Margin]] (SESA2022, with stick-free margins) · [[Stick-Fixed vs Stick-Free Stability]] · [[Stability vs Manoeuvrability]]

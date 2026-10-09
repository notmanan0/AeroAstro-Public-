---
title: "Neutral Point and Static Margin"
module: "SESA2022 Aerodynamics"
type: concept
stream: "Topic 6: Aircraft Aerodynamics and Static Stability"
aliases: ["neutral point", "static margin", "H_s", "h_n", "pitch stiffness"]
tags: [sesa2022, sesa2027, concept, stability]
status: complete
parent_lectures: ["[[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]]", "[[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]"]
related_concepts: ["[[Stick-Fixed vs Stick-Free Stability]]", "[[Manoeuvre Point and Manoeuvre Margin]]", "[[Aerodynamic Centre and Centre of Pressure]]"]
sources: ["02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf"]
---

# Neutral Point and Static Margin

## Definition

> [!note] Definition
> The **neutral point** $h_n$ is the CG position at which the aircraft's pitching moment doesn't change with incidence, $dC_{M_{CG}}/d\alpha = 0$ (neutral static stability). The **static margin** is the non-dimensional distance of the CG ahead of it:
>
> $$h_n = h_0+K\frac{C_{L_{T,\alpha}}}{C_{L^*_\alpha}},\qquad H_s = h_n-h,\qquad \frac{dC_{M_{CG}}}{dC_{L^*}} = -H_s$$
>
> The aircraft is statically stable if $H_s>0$ (CG ahead of the neutral point).

## Explanation
- **Moment slope**: $\dfrac{dC_{M_{CG}}}{d\alpha} = C_{L^*_\alpha}(h-h_0)-C_{L_{T,\alpha}}K$.
  - The wing term is destabilising when the CG is aft of the wing AC.
  - The tail term is stabilising.
- **Tail lift slope** (stick fixed): $C_{L_{T,\alpha}} = k(1-\epsilon_\alpha)$ with $k = a_1\frac{\pi A_Te_T}{\pi A_Te_T+a_1}$. Wing downwash ($\epsilon_\alpha$) reduces tail effectiveness and moves $h_n$ forward.
- The neutral point is the **aerodynamic centre of the whole aircraft**.
- **Typical values**: $H_s\approx0.05$–$0.15$ for transports. Negative values are relaxed-stability fighters (X-29, F-16) that need fly-by-wire.
- **Trade-off**: more margin means more stability but a larger trim load and less manoeuvrability. See [[Stability vs Manoeuvrability]].
- **Flight-test measurement**:

$$
H_{s,fixed} = -Kk\frac{a_2}{a_1}\frac{d\eta}{dC_{L^*}}
$$

  Plot $d\eta/dC_{L^*}$ against CG position and extrapolate to zero.
- **In SESA2027**: the pitch-stiffness derivative $M_w = -H_sC_{L^*_\alpha}$ links static margin to the short-period frequency (see [[Short Period Oscillation]]).

## Examples
- [[SESA2022 Examples Sheet 6 - Static Stability Solutions]]
- [[SESA2022 Static Stability Past Paper Questions Solutions]]

## Related
- Parent lectures: [[SESA2022 T6 - Aircraft Aerodynamics and Static Stability]], [[SESA2027 A2 - Longitudinal State-Space Model and Aerodynamic Derivatives]]
- Related concepts: [[Stick-Fixed vs Stick-Free Stability]], [[Manoeuvre Point and Manoeuvre Margin]], [[Aerodynamic Centre and Centre of Pressure]]

## Sources
- `02 - Sources/Stability/Topic 6 Aircraft aerodynamics and static stability_v2.pdf`

---
title: "Stagnation Properties"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["total temperature", "total pressure", "T0", "p0", "stagnation enthalpy"]
tags: [sesa2023, concept, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]"]
related_concepts: ["[[Speed of Sound and Mach Number]]", "[[Critical Conditions and Choked Flow]]", "[[Steady Flow Energy Equation]]", "[[Normal Shock Waves]]"]
sources: ["02 - Sources/Lectures/Week 03 - Gas Dynamics I - Compressible Flow, Shocks and Nozzles.pdf"]
---
# Stagnation Properties

## Definition

> [!note] Definition
> The state a flow would reach if brought to rest **isentropically**:
> $$h_0 = h+\tfrac12V^2,\quad \frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2,\quad \frac{p_0}{p} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{\gamma}{\gamma-1}},\quad \frac{\rho_0}{\rho} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{1}{\gamma-1}}$$

## Explanation
- **$T_0$ is constant** whenever there is no heat or shaft work (the SFEE), **even across shocks and friction**.
- **$p_0$ is constant** only if the flow is also isentropic. Any loss (friction, shock, mixing) shows up as a drop in $p_0$, i.e. entropy generation.
- In the **engine frame**, the free stream has $T_{01} = T_a(1+\tfrac{\gamma-1}{2}M_0^2)$ and $p_{01} = p_a(\cdot)^{\gamma/(\gamma-1)}$. This "ram" rise is why ramjets work. At M 0.8 it gives a $p_0$ ratio of 1.52; at M 2, 7.82; at M 3.2, 49.4.
- Every property has a static and a stagnation value. In a moving frame they differ; "pressure" alone means static.
- Rearranged: $T_0 = T+V^2/(2c_p)$, so $V = \sqrt{2c_p(T_0-T)}$. This is how the jet velocity is found in every nozzle.
- **Flow functions** (data book p. 11 and Tables 19–22):
  $$\frac{V}{\sqrt{c_pT_0}} = \sqrt{\gamma-1}\,M\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{-1/2},\qquad\frac{\dot m\sqrt{c_pT_0}}{Ap_0} = \frac{\gamma}{\sqrt{\gamma-1}}M\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{-\frac{\gamma+1}{2(\gamma-1)}}$$

## Examples
- M 2 at 250 K and 0.5 bar: $T_0 = 450$ K and $p_0 = 3.91$ bar.
- Sphere in a 500 m/s, 300 K, 1 bar tunnel (PS3 Q3.2): the flow is supersonic (M 1.44), so the nose reads $p_{02}$ behind a normal shock, **319 kPa**, not the isentropic 337 kPa.

## Related
- [[Speed of Sound and Mach Number]] · [[Critical Conditions and Choked Flow]] · [[Steady Flow Energy Equation]] · [[Normal Shock Waves]]

## Sources
- Week 3 notes §3.2.4; Lecture 7; Data Book p. 11

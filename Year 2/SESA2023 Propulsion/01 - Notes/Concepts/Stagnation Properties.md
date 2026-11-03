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

The stagnation state of a flow is the state it would reach if it were brought to rest isentropically:

$$
h_0 = h+\tfrac12V^2,\quad \frac{T_0}{T} = 1+\frac{\gamma-1}{2}M^2,\quad \frac{p_0}{p} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{\gamma}{\gamma-1}},\quad \frac{\rho_0}{\rho} = \left(1+\frac{\gamma-1}{2}M^2\right)^{\frac{1}{\gamma-1}} .
$$

$T_0$ stays constant whenever there is no heat transfer or shaft work, by the steady-flow energy equation, even across shocks and with friction. $p_0$ stays constant only if the flow is also isentropic, so any loss, from friction, a shock or mixing, appears as a drop in $p_0$, which is entropy generation. Every property has a static and a stagnation value, which differ in a moving frame; "pressure" on its own means static pressure.

In the engine's frame the free stream arrives with $T_{01} = T_a(1+\tfrac{\gamma-1}{2}M_0^2)$ and $p_{01} = p_a(1+\tfrac{\gamma-1}{2}M_0^2)^{\gamma/(\gamma-1)}$. This ram rise is why ramjets work: the stagnation pressure ratio is 1.52 at M 0.8, 7.82 at M 2 and 49.4 at M 3.2. Rearranged, $T_0 = T+V^2/(2c_p)$ gives $V = \sqrt{2c_p(T_0-T)}$, which is how the jet velocity is found in every nozzle. The Data Book (p. 11 and Tables 19–22) tabulates the flow functions

$$
\frac{V}{\sqrt{c_pT_0}} = \sqrt{\gamma-1}\,M\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{-1/2},\qquad\frac{\dot m\sqrt{c_pT_0}}{Ap_0} = \frac{\gamma}{\sqrt{\gamma-1}}M\Big(1+\tfrac{\gamma-1}{2}M^2\Big)^{-\frac{\gamma+1}{2(\gamma-1)}} .
$$

At M 2, 250 K and 0.5 bar, $T_0 = 450$ K and $p_0 = 3.91$ bar. In PS3 Q3.2, a sphere in a 500 m/s, 300 K, 1 bar tunnel is in supersonic flow (M 1.44), so its nose reads $p_{02}$ behind a normal shock, 319 kPa, not the isentropic 337 kPa.

## Related

- [[Speed of Sound and Mach Number]] · [[Critical Conditions and Choked Flow]] · [[Steady Flow Energy Equation]] · [[Normal Shock Waves]]

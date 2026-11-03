---
title: "Intake Pressure Recovery"
module: "SESA2023 Propulsion"
type: concept
stream: "Section 1: Introduction and Fundamentals"
aliases: ["diffuser", "intake", "Pitot intake", "external compression intake", "pressure recovery", "Gamma_d"]
tags: [sesa2023, concept, intakes, compressible-flow]
status: complete
parent_lectures: ["[[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]"]
related_concepts: ["[[Oblique Shock Waves]]", "[[Normal Shock Waves]]", "[[Component Stagnation Pressure Ratios]]", "[[Isentropic Efficiency]]"]
sources: ["02 - Sources/Lectures/Week 04 - Gas Dynamics II - Friction, Heat Transfer, Oblique Shocks and Intakes.pdf", "02 - Sources/Lectures/Week 06-07 - Jet Engines.pdf"]
---

# Intake Pressure Recovery

An intake (diffuser) slows the captured air to about M 0.4–0.5 at the compressor face, or 0.2–0.3 at a ramjet combustor, and is judged by its stagnation-pressure recovery $\Gamma_d = p_{02}/p_{01}$ or its adiabatic efficiency $\eta_d$.

It has to decelerate and compress the flow while delivering a uniform, stable exit flow, which often matters more than the loss itself, with little loss of $p_0$, low drag and weight, and tolerance of incidence and yaw. Subsonic intakes, used on all civil aircraft, are diverging ducts. A short duct is good for friction and weight, but its steep adverse pressure gradient separates the boundary layer, raising the loss and distortion and reducing the effective area ratio, so the half-angle is limited to about 10°, typically 5–7°. Through the intake $T_{02} = T_{01}$ and $p_2\approx p_{02} = \Gamma_dp_a(1+\tfrac{\gamma-1}{2}M^2)^{\gamma/(\gamma-1)}$. At 6 km and M 0.85 with $\eta_d = 0.9$, the W04 example gives $\Gamma_d = 0.957$ and a length of 1.11 m ([[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]).

Supersonic intakes come in three types:

| Type | How | Where it works | Notes |
|---|---|---|---|
| Normal-shock (Pitot) | Subsonic intake with a normal shock at the lip | up to M ≈ 1.7–1.8 | Loss under 10 % below M 1.5. Subcritical: the shock moves out and the flow spills. A shock swallowed inside loses more $p_0$ and $\dot m$ |
| External compression | $n$ ramp oblique shocks plus a final weak normal shock | high supersonic | More shocks give less loss, but the exit flow is more inclined and the subsonic duct loses more, so there is an optimum $n$. No starting problem; adapts to Mach |
| Mixed compression | External obliques, then an internal convergent section (stays supersonic) and internal ramps | | Shorter and lighter, but efficiency depends strongly on flight Mach. Ideal C–D intakes suffer starting problems |

A Pitot intake loses the stagnation pressure of a normal shock,

$$
\frac{p_{01}}{p_{0a}} = \left[\frac{\frac{\gamma+1}{2}M^2}{1+\frac{\gamma-1}{2}M^2}\right]^{\frac{\gamma}{\gamma-1}}\left[\frac{2\gamma}{\gamma+1}M^2-\frac{\gamma-1}{\gamma+1}\right]^{\frac{1}{1-\gamma}},
$$

which is 0.93 at M 1.5, 0.72 at M 2 and 0.33 at M 3. In [[SESA2023 Problem Sheet 4 Solutions]] Q4.3, a ramjet with a normal-shock inlet at M 3.42 has $p_{02}/p_{01} = 0.227$, so 13.7 bar becomes 3.1 bar. Other values: a measured ramjet with $\Gamma_d = 0.600$ ([[SESA2023 Exam 2023-24 Solutions]] Q2), and a 95 % isentropic intake efficiency at M 2 giving $\Gamma_d = 0.924$ ([[SESA2023 Exam 2013-14 Solutions]] Q3).

Legacy exams ask about the SR-71's J58, which handled its whole speed range with a translating inlet spike that positioned the shocks and kept them at the cowl, bypass doors, and fourth-stage compressor bleed routed through six bypass tubes to the afterburner. At high Mach that made it a turbo-ramjet, with most of the thrust coming from the inlet, afterburner and ejector.

## Related

- [[Oblique Shock Waves]] · [[Normal Shock Waves]] · [[Component Stagnation Pressure Ratios]] · [[Isentropic Efficiency]]

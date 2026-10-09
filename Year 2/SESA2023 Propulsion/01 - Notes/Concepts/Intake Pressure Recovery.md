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

## Definition

> [!note] Definition
> An intake (diffuser) decelerates the captured air to about M 0.4–0.5 at the compressor face (0.2–0.3 at a ramjet combustor). It is judged by its **stagnation-pressure recovery** $\Gamma_d = p_{02}/p_{01}$, or by its adiabatic efficiency $\eta_d$.

## Explanation
**Requirements**:
- decelerate and compress;
- uniform, stable exit flow (often more important than the loss itself);
- low $p_0$ loss, drag and weight;
- tolerate incidence and yaw.

**Subsonic intakes** (all civil aircraft):
- $dA/dx>0$.
- Short is good for friction and weight, but a steep adverse pressure gradient separates the boundary layer, giving higher loss, distortion and a smaller effective area ratio.
- The half-angle is limited to about 10°, typically 5–7°.
- $T_{02} = T_{01}$, and $p_2\approx p_{02} = \Gamma_dp_a(1+\tfrac{\gamma-1}{2}M^2)^{\gamma/(\gamma-1)}$.

**Supersonic intakes**:

| Type | How | Where it works | Notes |
|---|---|---|---|
| Normal-shock (Pitot) | Subsonic intake with a normal shock at the lip | up to M ≈ 1.7–1.8 | Loss under 10 % below M 1.5. Subcritical: the shock moves out and the flow spills. A shock swallowed inside loses more $p_0$ and $\dot m$ |
| External compression | $n$ ramp oblique shocks plus a final weak normal shock | high supersonic | More shocks give less loss, but the exit flow is more inclined and the subsonic duct loses more, so there is an optimum $n$. No starting problem; adapts to Mach |
| Mixed compression | External obliques, then an internal convergent section (stays supersonic) and internal ramps | | Shorter and lighter, but efficiency depends strongly on flight Mach. Ideal C–D intakes suffer "starting" problems |

**Normal-shock loss** (Pitot intake):

$$\frac{p_{01}}{p_{0a}} = \left[\frac{\frac{\gamma+1}{2}M^2}{1+\frac{\gamma-1}{2}M^2}\right]^{\frac{\gamma}{\gamma-1}}\left[\frac{2\gamma}{\gamma+1}M^2-\frac{\gamma-1}{\gamma+1}\right]^{\frac{1}{1-\gamma}}$$

This gives 0.93 at M 1.5, 0.72 at M 2 and 0.33 at M 3. See the shock tables.

**The SR-71 J58 (legacy exams)** handled the whole speed range with:
- a translating inlet **spike** that positions the shocks and keeps them at the cowl;
- bypass doors;
- 4th-stage compressor bleed routed through six bypass tubes to the afterburner, which turns it into a turbo-ramjet at high Mach (most of the thrust comes from the inlet, afterburner and ejector).

## Examples
- Subsonic intake at 6 km and M 0.85, $\eta_d = 0.9$: $\Gamma_d = 0.957$, $L = 1.11$ m ([[SESA2023 W04 - Friction, Heat Addition, Oblique Shocks and Intakes]]).
- Ramjet with a normal-shock inlet at M 3.42: $p_{02}/p_{01} = 0.227$, so 13.7 bar becomes **3.1 bar** ([[SESA2023 Problem Sheet 4 Solutions]] Q4.3).
- Measured ramjet: $\Gamma_d = 0.600$ ([[SESA2023 Exam 2023-24 Solutions]] Q2).
- Intake isentropic efficiency 95 % at M 2 gives $\Gamma_d = 0.924$ ([[SESA2023 Exam 2013-14 Solutions]] Q3).

## Related
- [[Oblique Shock Waves]] · [[Normal Shock Waves]] · [[Component Stagnation Pressure Ratios]] · [[Isentropic Efficiency]]

## Sources
- Week 4 intake notes §3.1–3.3; Lecture 12

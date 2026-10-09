---
title: "SESA2024 10 - Thermal Control"
module: "SESA2024 Astronautics"
type: topic
stream: "Spacecraft Subsystems"
order: 10
tags:
  - sesa2024
  - thermal-control
aliases: ["Chapter 10", "Thermal subsystem", "TCS"]
date: 2026-09-25
status: complete
parent: ["[[SESA2024 Astronautics Hub]]"]
prerequisites: ["[[SESA2024 08 - Electrical Power Subsystem]]"]
next_topics: ["[[SESA2024 11 - Payload and Orbit Selection]]"]
key_concepts: ["[[Blackbody Radiation]]", "[[Absorptance and Emittance]]", "[[Spacecraft Thermal Balance Equation]]", "[[Passive vs Active Thermal Control]]"]
tutorial_sheets: ["[[SESA2024 Workbook Ch10 - Thermal Control Solutions]]"]
sources: ["02 - Sources/Lectures/Chapter 10/2025 WEEK 8 - Chapter 10 - Thermal Control - Lecture slides - complete.pdf"]
---

# SESA2024 10 - Thermal Control

> [!abstract] Summary
> In orbit the only effective heat-transfer mechanism is **radiation**. The spacecraft's equilibrium temperature comes from balancing:
> - **inputs**: direct Sun + Earth albedo + Earth IR + internal dissipation;
> - **output**: $\varepsilon\sigma T^4A_{surf}$.
>
> When sunlight dominates, $T$ depends on the **ratio $\alpha_S/\varepsilon$**, so passive control means choosing surface finishes (white paint, SSMs, MLI) and sizing radiators and heaters. Industry avoids active control (fluid loops) wherever possible.

## Key Concepts
- [[Blackbody Radiation]] · [[Absorptance and Emittance]] · [[Spacecraft Thermal Balance Equation]] · [[Passive vs Active Thermal Control]]

---

## 1. Why thermal control?
- **Equipment reliability**: components must stay within their limits (batteries, propellant, mechanisms are the most sensitive).
- **Payload requirements**:
  - radiate the dissipated power;
  - sensor cooling (IR observatories);
  - very small thermal gradients and no thermal shock (Hubble's pointing).

## 2. Heat transfer in space
- **Conduction**: molecular excitation. Works only inside the spacecraft.
- **Convection**: fluid mixing. Must be *forced* in µg.
- **Radiation**: IR emission from surfaces. Needs no medium, so it **dominates between spacecraft and environment**.
- In LEO the particle mean free path is long: about 250 m at 200 km and about 15 km at 400 km. The thin gas has a kinetic temperature of about 1000 K but carries negligible heat.

## 3. Absorption of radiation
See [[Absorptance and Emittance]]. Incident spectral intensity $q_i(\lambda)$:

$$
\alpha_\lambda = \frac{q_a}{q_i},\quad \rho_\lambda = \frac{q_r}{q_i},\quad \tau_\lambda = \frac{q_t}{q_i},\qquad \alpha_\lambda+\rho_\lambda+\tau_\lambda = 1
$$

- Spacecraft surfaces are **opaque** ($\tau = 0$), so $\alpha+\rho = 1$.
- A **blackbody** absorbs all incident radiation and emits the maximum possible at any temperature: $\alpha_\lambda = 1$ and $\rho_\lambda = 0$ for all $\lambda$ (2016/17 Q3(i)).
- Real materials have $\lambda$-dependent $\alpha_\lambda$, which is **colour**.
- **Total absorptance** depends on the material *and* the source spectrum:

$$
\alpha_S = \frac{\int\alpha_\lambda q_S\,d\lambda}{\int q_S\,d\lambda}\approx\frac{\int_{0.3}^{2.0}\alpha_\lambda q_S\,d\lambda}{\int_{0.3}^{2.0}q_S\,d\lambda}
$$

About 97 % of solar energy lies within 0.3–2.0 µm.

## 4. Emission of radiation
See [[Blackbody Radiation]].
- **Planck**: $q_\lambda = \dfrac{2\pi hc^2}{\lambda^5[\exp(ch/k\lambda T)-1]}$, with $h$ = 6.625 × 10⁻³⁴ J s, $k$ = 1.380 × 10⁻²³ J/K, $c$ = 3 × 10⁸ m/s.
- **Wien**: $\lambda_{max}T = 2.898\times10^{-3}$ m K. The Sun (5800 K) peaks at about 0.5 µm; the Earth (290 K) at about **10 µm**.
- **Stefan–Boltzmann**: $q_{BB} = \sigma T^4$, with $\sigma$ = 5.669 × 10⁻⁸ W m⁻² K⁻⁴.
- **Emittance**: $\varepsilon = q(T)/q_{BB}(T)\le1$, so $q = \varepsilon\sigma T^4$.

## 5. The spacecraft thermal balance
See [[Spacecraft Thermal Balance Equation]].

| Term | Expression | Notes |
|---|---|---|
| Direct Sun | $Q_S = q_S\alpha_SA_S^{proj}$ | $q_S\approx1350$ W/m² at 1 AU; 0 in eclipse |
| Earth albedo | $Q_a = aq_S\alpha_SA_E^{proj}\cos\phi\,\beta F$ | $a\approx0.34$; $\phi$ is the Earth-centred angle between the spacecraft and the Sun; $\beta = 1$ for $-90^\circ<\phi<90^\circ$, otherwise 0 |
| Earth IR | $Q_E = q_E\varepsilon A_E^{proj}F$ | $q_E\approx240$ W/m²; uses $\varepsilon$ as the IR absorptance (**Kirchhoff**: $\alpha = \varepsilon$ at equal temperature, about 290 K) |
| Dissipation | $Q_{dis} = P$ | electrical power ends up as heat |
| **Output** | $\varepsilon\sigma T^4A_{surf}$ | total surface area |

Distance factor: $F = (R_E/R_{orb})^2$.

$$
\boxed{q_S\alpha_SA_S^{proj}+aq_S\alpha_SA_E^{proj}\cos\phi\,\beta\Big(\frac{R_E}{R_{orb}}\Big)^2+q_E\varepsilon A_E^{proj}\Big(\frac{R_E}{R_{orb}}\Big)^2+P = \varepsilon\sigma T^4A_{surf}}
$$

**Assumptions**:
- isothermal body;
- **effective** (area-weighted) $\alpha_S$ and $\varepsilon$, for example $\bar\alpha_S = 0.9\alpha_S^{(1)}+0.1\alpha_S^{(2)}$ for 90 %/10 % coverage;
- albedo and IR simplified with the $F$ factor;
- steady state.

**Albedo varies** with surface type (ocean, cloud, ice), season and latitude. 0.34 is a mean (2017/18 Q1(vi)).

## 6. Passive control via $\alpha_S/\varepsilon$
Divide the balance by $\varepsilon A_{surf}$:

$$
T^4 = \frac{q_S}{\sigma}\frac{\alpha_S}{\varepsilon}\left[\frac{A_S^{proj}}{A_{surf}}+a\frac{A_E^{proj}}{A_{surf}}\cos\phi\,\beta F\right]+\frac{q_EA_E^{proj}F}{\sigma A_{surf}}+\frac{P}{\varepsilon\sigma A_{surf}}
$$

If $q_S\gg q_E, P$, then **$T = f(\alpha_S/\varepsilon)$**.
- **Cool it**: lower $\alpha_S/\varepsilon$, with white paint or **second-surface mirrors** (SSM: transparent sheet, aluminised behind).
- **Warm it**: raise $\alpha_S/\varepsilon$, with polished metal, copper or black nickel.
- **UV and atomic oxygen degrade surfaces** and raise $\alpha_S$, so $T$ **rises over the mission**.

![[ast_thermal_alpha_eps.png|600]]

> [!example] In eclipse with $P = 0$, $\varepsilon$ cancels (2023/24 A5, 2024/25 A8)
> Only Earth IR remains: $q_E\varepsilon A_E^{proj}F = \varepsilon\sigma T^4A_{surf}$, so
>
> $$T = \left(\frac{q_EA_E^{proj}F}{\sigma A_{surf}}\right)^{1/4}$$
>
> This is independent of both $\varepsilon$ and $\alpha_S$. A derelict spacecraft in shadow reaches the same temperature whatever its paint.

## 7. Passive design guidelines
- Balance: environmental input + dissipation = thermal emission.
- Insulate non-radiating surfaces with **MLI**.
- Size **radiators** for the hot case (upper limits).
- Size **heaters** for the cold case (eclipse, low power).

| Passive (coatings, MLI, heat pipes) | Active (pumped fluid loops, louvres, heaters, coolers) |
|---|---|
| no power, no moving parts | needs power, has mechanisms (a reliability risk) |
| simple, reliable, cheap | heavier, costlier |
| less flexible | adapts to variable environments; higher heat-transfer rates |

Industry uses **passive whenever possible**. The thermal engineer is involved in nearly every onboard system.

## 8. Typical exam calculations
- **Isothermal body at noon / terminator / eclipse**: GEO cylinder spinner (2013/14 Q3), GEO cube with radiator (2016/17 Q3), Meteosat (2021/22 B2).
- **Thermally decoupled array**: front/back faces with different $\alpha$ and $\varepsilon$ (2019/20 B2, 2022/23 B2, workbook Ch10 Q7). Output $= \sigma T^4(\varepsilon_f+\varepsilon_b)A$.
- **Material selection against a temperature window**: 2023/24 B3 (Jupiter cube) and 2024/25 B3 (LEO cylinder). Compute $T_{eclipse}$ (with the heater) and $T_{sunlit}$ for each candidate: black paint, white paint, SiO-Al dark mirror, MLI.

## Links
- Parent: [[SESA2024 Astronautics Hub]] · Previous: [[SESA2024 09 - Communications]] · Next: [[SESA2024 11 - Payload and Orbit Selection]]
- Solutions: [[SESA2024 Workbook Ch10 - Thermal Control Solutions]]

## Sources
- Chapter 10 lecture (H. Sykulska-Lawrence), equations 10.1–10.9; Fortescue, Stark & Swinerd, Ch. 11

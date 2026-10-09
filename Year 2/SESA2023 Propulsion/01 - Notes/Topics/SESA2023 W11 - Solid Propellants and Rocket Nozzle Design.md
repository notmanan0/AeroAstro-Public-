---
title: "SESA2023 W11 - Solid Propellants and Rocket Nozzle Design"
module: "SESA2023 Propulsion"
type: topic
stream: "Section 5: Rockets"
order: 11
tags:
  - sesa2023
  - rockets
  - solid-propellant
  - burning-rate
  - nozzle-design
aliases: ["Rockets II", "Solid rocket motors"]
date: 2026-09-24
status: complete
parent: ["[[SESA2023 Propulsion Hub]]"]
prerequisites: ["[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
next_topics: []
key_concepts: ["[[Solid Propellant Burning Rate]]", "[[Rocket Nozzle Geometry]]", "[[Rocket Performance Parameters]]", "[[Converging-Diverging Nozzle Operating Regimes]]"]
tutorial_sheets: []
sources: ["02 - Sources/Lectures/Week 11 - Rockets.pdf", "02 - Sources/Lectures/Week 11 - Rockets - Lecture Slides.pdf"]
---

# SESA2023 W11 - Solid Propellants and Rocket Nozzle Design

> [!abstract] Summary
> **Solid rocket motors** are simple, reliable and storable for 5–20 years, but they cannot be relit.
> - Their thrust follows the **burning rate** $r$ (surface regression speed), which obeys **Saint-Robert's law** $r = aP_c^n$. The **burning index** $n$ controls stability: $0.2<n<0.8$ in practice, and $n\ge1$ is unstable.
> - $r$ also rises with the initial propellant temperature, gas cross-flow (**erosive burning**, when $A_p/A_t<4$) and acceleration.
> - Propellants are **double-base** (NC/NG, homogeneous) or **composite** (AP crystals in an HTPB binder plus Al powder).
>
> **Real nozzles**: the convergent shape barely matters; the throat curvature sets the effective $A_t$. The divergent section is either **conical** (12–18°, divergence factor $\lambda = (1+\cos\alpha)/2$) or **bell** (shorter, lower loss, but damaged by particles). Advanced concepts (aerospike, dual-bell) adapt to altitude.

## Key Concepts
- [[Solid Propellant Burning Rate]] · [[Rocket Nozzle Geometry]] · [[Rocket Performance Parameters]]

---

## 1. Solid rocket motors
- **Components**: a case (cylindrical or spherical, insulated), the propellant **grain**, an igniter (pyrotechnic charge) and the nozzle.
- **Uses**: from 2 N to 11 MN. Large boosters, upper stages, tactical missiles (AA, SA, anti-tank), and gas generators for starting turbopumps.
- **Pros**: few moving parts, low cost, very reliable, minimal maintenance, ready for immediate use (military).
- **Con**: no restart.

## 2. Propellants
**The requirements conflict**, so every grain is a compromise:
- high energy (high $T_c$ and $I_{sp}$) and a low product molar mass;
- high density;
- a **low burning index**;
- low sensitivity to temperature and to erosive burning;
- easy ignition;
- good mechanical properties, bonding and thermal-expansion match to the case;
- long storage life and safe manufacture;
- opacity to radiation, smokeless exhaust (stealth);
- low cost.

| Type | Make-up | Pros | Cons |
|---|---|---|---|
| **Homogeneous / double-base** (colloidal) | Nitrocellulose dissolved in nitroglycerine, plus additives (carbon black for opacity; AP or Al for performance; a third component gives *triple-base*) | Cheap, smokeless, non-toxic, good mechanical properties, low $n$, good control of $r$ | Low $I_{sp}$ (≈ 220 s at sea level), low density (1.6 g/cm³), **hazardous**. The optimum NG/NC ≈ 8.6 can't be used; mechanical limits keep NG/NC ≤ 1 |
| **Heterogeneous / composite** | Oxidiser crystals (AP, AN, KP, KN, NP) in a rubbery binder (HTPB, PBAN, asphalt), plus up to ~20 % metal powder (Al, B, Be, the last toxic) | Safer, higher performance, slightly fuel-rich optimum (also protects the nozzle) | Oxidiser loading ≤ 80–85 % for processability. The **volume** ratio matters, so dense oxidisers and light fuels are preferred. The burning rate depends strongly on **AP particle size** |

## 3. Burning rate
$r$ is the regression speed of the burning surface, normal to itself, in mm/s. It is measured in strand (Crawford) burners, ballistic evaluation motors or full-scale motors.

$$
\boxed{r = aP_c^{\,n}}\qquad\text{(Saint-Robert's / Vieille's law)}
$$

- The data lie on straight lines in $\ln r$–$\ln P_c$ over wide ranges, sometimes piecewise (e.g. the "plateau" of double-base propellants).
- **$a$** is the *temperature coefficient*: it depends on the composition and the initial temperature.
- **$n$** is the *burning index* (the slope): it depends mainly on the composition.
- **Interpretation of $n$**:
  - $n = 0$ is **flat** burning, with $r$ independent of $P_c$.
  - $n<0$ is rare, but interesting for reignition.
  - $n\to1$ makes small $P_c$ disturbances cause large changes in gas generation.
  - $n>1$ gives **no stable** operating point.
  - Very low $n$ risks extinction.
  - In practice $0.2\lesssim n\lesssim0.8$.
- Why it matters: the thrust is $F = C_FP_cA_t$, so $P_c$ sets the thrust. The mass generated is $\rho_pA_br$, which must balance the nozzle's $P_cA_t/C^*$. Hence **the grain burning area $A_b(t)$ shapes the thrust curve** (progressive, neutral or regressive grains).

![[prop_burning_rate.png|600]]

### Other influences on $r$
- **Initial propellant temperature $T_p$**:
  - Higher $T_p$ means hotter products, more heat flux into the grain, and a higher $r$.
  - That gives a higher thrust and a shorter burn.
  - The **total impulse is roughly unchanged** (slightly higher through the pressure term).
  - The case must survive the hot-day **overpressure**.
  - Non-uniform $T_p$ causes thrust misalignment in large motors.
- **Erosive burning**:
  - Gas flowing *along* the surface raises the heat transfer and hence $r$.
  - It occurs in tubular grains and not in end-burners.
  - It is strongest near the aft end, where the accumulated mass flow is high.
  - It is strongest early in the burn, when the port area is small.
  - It is significant for $A_p/A_t<4$.
- **Vehicle acceleration** normal to the surface (spin, anti-missile manoeuvres) creates micro-cracks, so the burning area and $r$ rise. The effect becomes noticeable around 5–10 g and can double $r$ above 30 g. For example, 25 g occurs at 2 rev/s at 1.5 m radius.

## 4. Nozzle geometry
Quasi-1D theory only needs $A(x)$. A real nozzle needs the whole axisymmetric profile.

- **Convergent section**: the flow is subsonic with a favourable pressure gradient, so no separation and any smooth shape works.
  - The **contraction ratio** is 1.5–4. A higher ratio gives a lower chamber velocity and less $p_0$ loss during heat release.
  - The convergence half-angle is 30–45°, for short and light nozzles.
- **Throat**: two circular arcs (radius up to 2–3 × $r_t$) meet tangentially. A tighter upstream curvature gives a **vena contracta**, which reduces the effective $A_t$ and the mass flow.
- **Divergent section**: the critical part, because the flow is supersonic and a poor contour creates shocks.
  - **Conical**: defined by the half-angle $\alpha$, simple and cheap. The lateral area scales as $1/\sin\alpha$. Only the axial momentum counts, so the thrust is multiplied by the **divergence factor**
    $$\lambda = \frac{1+\cos\alpha}{2}\qquad(\alpha = 15^\circ\Rightarrow\lambda = 0.983)$$
    Use 12–18°: smaller is too long and heavy, larger loses too much.
  - **Bell (contoured)**: a large initial angle (30–60°) turns gradually to 2–8° at the exit. It is designed with 2-D (method-of-characteristics) models to cancel the expansion waves without creating compression waves. It is **shorter** and has **lower divergence loss** than a 15° cone of the same area ratio. It is **not used on solids**, because two-phase Al₂O₃ particles erode concave walls.
  - **Unconventional** designs reduce launch cost and handle the single-design-altitude problem:
    - *altitude-adaptive*: plug/aerospike, expansion–deflection;
    - *multi-mode*: dual-bell, dual-mode;
    - separation control, extendible cones.

**Real-nozzle losses**:
- exit divergence;
- the contraction ratio and $p_0$ loss;
- the boundary layer (0.5–1.5 %);
- two-phase flow (up to 5 %);
- combustion instability, chemical reactions (frozen or shifting), transients and cooling.

## Links
- Parent: [[SESA2023 Propulsion Hub]] · Previous: [[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]
- Nozzle regimes (over- and under-expanded): [[Converging-Diverging Nozzle Operating Regimes]]
- Not yet examined on the current syllabus (no Week 11 questions in the 2021-25 papers). It is still likely descriptive exam material.

**Related (SESA2028 materials):** [[SESA2028 M5 - Metal and Ceramic Matrix Composites and Hybrid Laminates|SESA2028 M5 CMCs]] (C/C nozzles) · [[Thermal Barrier Coatings]]

## Sources
- Week 11 notes (Grenga, Richardson) and Lecture 33 slides

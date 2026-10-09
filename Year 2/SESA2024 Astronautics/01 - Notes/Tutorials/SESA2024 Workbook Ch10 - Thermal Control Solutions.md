---
title: "SESA2024 Workbook Ch10 - Thermal Control Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Spacecraft Subsystems"
tags:
  - sesa2024
  - tutorial-solutions
  - thermal-control
sheet: "Problem Sheet Workbook 2025-26, Chapter 10 (pp. 129-137)"
theory_notes: ["[[SESA2024 10 - Thermal Control]]"]
key_concepts: ["[[Spacecraft Thermal Balance Equation]]", "[[Absorptance and Emittance]]", "[[Blackbody Radiation]]", "[[Passive vs Active Thermal Control]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch10 - Thermal Control Solutions

> [!abstract] Sheet Info
> Seven questions. Q1–6 are definitions; Q7 is the **solar-array temperature profile** at 18 000 km. Q7 reappeared almost word for word as **2022/23 exam B2(i)**, worth 15 marks. All numbers were reproduced in Python ✔.

## Theory Links
- [[SESA2024 10 - Thermal Control]]
- Concepts: [[Spacecraft Thermal Balance Equation]] · [[Absorptance and Emittance]] · [[Blackbody Radiation]] · [[Passive vs Active Thermal Control]]

---

## Q1: Why thermal control?
- For **long-term, reliable performance** of components. Every component has operating and survival limits; batteries, propellant and mechanisms are the most sensitive. Leaving the limits risks failure.
- The payload may have specific needs: **tight temperature limits**, small thermal **gradients**, or thermal **stability**. Examples: IR detector cooling; Hubble's extreme pointing, which is sensitive to thermal distortion.

## Q2: Spectral absorptance

$$
\alpha_\lambda \equiv \frac{q_a(\lambda)}{q_i(\lambda)}
$$

- $q_i$ is the incident intensity at wavelength $\lambda$ (W m⁻² µm⁻¹) and $q_a$ the absorbed part. It lies between 0 and 1 and **varies with $\lambda$**, which is why materials have colour.
- A **blackbody** has $\alpha_\lambda = 1$ at all wavelengths (a perfect absorber).
- With $\alpha+\rho+\tau = 1$ and opaque surfaces ($\tau = 0$), $\alpha = 1-\rho$.

## Q3: Emittance of a real surface

$$
\varepsilon\equiv\frac{q(T)}{q_{BB}(T)}<1\quad\Rightarrow\quad q(T) = \varepsilon\sigma T^4\ \text{(W m}^{-2})
$$

It is the ratio of real emission to blackbody emission at the same temperature.

## Q4: Inputs and outputs
- **Inputs**: direct solar radiation; Earth albedo (sunlight reflected by the Earth); Earth IR emission; internal dissipation $P$.
- **Output**: IR emission from all spacecraft surfaces.

## Q5: Why $T$ depends on $\alpha_S/\varepsilon$
Thermal balance:

$$
q_S\alpha_SA_S^{proj}+aq_S\alpha_SA_E^{proj}\cos\phi\,\beta\Big(\frac{R_E}{R_{orb}}\Big)^2+q_E\varepsilon A_E^{proj}\Big(\frac{R_E}{R_{orb}}\Big)^2+P = \varepsilon\sigma T^4A_{surf}
$$

Divide by $\varepsilon A_{surf}$:

$$
\sigma T^4 = q_S\frac{\alpha_S}{\varepsilon}\left\{\frac{A_S^{proj}}{A_{surf}}+a\frac{A_E^{proj}}{A_{surf}}\cos\phi\,\beta F\right\}+q_E\frac{A_E^{proj}}{A_{surf}}F+\frac{P}{\varepsilon A_{surf}}
$$

If the solar term dominates both the Earth IR and $P$, then **$T = f(\alpha_S/\varepsilon)$**. Pick surface finishes to set the temperature.

![[ast_thermal_alpha_eps.png|600]]

## Q6: When is active control needed?
- When passive methods (coatings, MLI, radiators, heaters) cannot keep components within limits.
- Examples: strict payload requirements (cryogenic sensor cooling) or harsh, highly variable environments.
- **Costs**: power, mechanisms (a reliability risk), more mass and higher cost. Industry prefers passive whenever possible.

---

## Q7: Solar-array temperature profile at 18 000 km (= 2022/23 B2(i))
**Set-up**:
- Circular equatorial orbit, $R_{orb} = 18\,000$ km, at the Northern summer solstice.
- 3-axis stabilised. Two planar panels of 6 m² each, of negligible thickness, rotating about the orbit normal to track the Sun.
- Sun face: $\alpha_{sf} = 0.67$, $\varepsilon_{sf} = 0.80$. Back face: $\alpha_{sb} = \varepsilon_b = 0.70$.
- Data: $\varepsilon_1 = 23.5^\circ$, $q_S = 1400$, $q_E = 240$ W/m², $a = 0.34$.

### Is there an eclipse?
- At solstice the Sun is $\varepsilon_1 = 23.5^\circ$ out of the equatorial (orbit) plane.
- The shadow cylinder's axis is offset from the orbit by $R_0 = R_{orb}\sin\varepsilon_1 = 18\,000\sin23.5^\circ = \mathbf{7177\ km}$.
- $R_0 > R_E = 6378$ km, so the orbit passes "over" the shadow: **no eclipse**.

### Common numbers
- $F = (R_E/R_{orb})^2 = 0.1256$.
- The array normal is tilted by $\varepsilon_1$ from the Sun line (it can only rotate in the orbit plane), so $A_S^{proj} = 6\cos23.5^\circ$.
- Output from both faces: $\varepsilon_{eff}\sigma T^4A_{surf} = \frac{0.8+0.7}{2}(5.67\times10^{-8})(12)T^4 = 5.103\times10^{-7}T^4$.

### Noon (Earth behind the array's back face)

$$
Q_S = 1400(0.67)(6\cos23.5^\circ) = 5161\ \text{W}
$$

$$
Q_a = 0.34(1400)(0.7)(6)\cos23.5^\circ(0.1256) = 230\ \text{W}
$$

$$
Q_E = 240(0.7)(6)(0.1256) = 127\ \text{W}
$$

$$
T^4 = \frac{5161+230+127}{5.103\times10^{-7}}\ \Rightarrow\ T = 322\ \text{K}\approx\mathbf{49\ ^\circ C}
$$

### Midnight (the Earth now faces the Sun-facing front)
- Albedo is about 0 (the night side is below).
- Earth IR is absorbed by the front face: $Q_E = 240(0.8)(6)(0.1256) = 145$ W.

$$
T^4 = \frac{5161+145}{5.103\times10^{-7}}\ \Rightarrow\ T = 319\ \text{K}\approx\mathbf{46\ ^\circ C}
$$

### Terminator (dawn or dusk)
The Earth is edge-on to the array, so albedo and IR are both about 0:

$$
T^4 = \frac{5161}{5.103\times10^{-7}}\ \Rightarrow\ T = 317\ \text{K}\approx\mathbf{44\ ^\circ C}
$$

![[ast_array_temperature_profile.png|620]]

> [!tip] Why only about 5 °C of variation
> At 18 000 km, $F$ = 0.126, so Earth's contribution is small against 5 kW of direct sunlight. Compare LEO, where $F\approx0.8$ and an eclipse happens every orbit, giving swings of more than 100 °C.

> [!warning] Kirchhoff's law
> For Earth IR (about 290 K), use the surface's **emittance** as its IR absorptance: $\alpha_{IR} = \varepsilon$. For sunlight and albedo, use $\alpha_S$.

## Sources
- Workbook 2025-26 Chapter 10 questions (p. 129–130) and solutions (p. 133–137)
- Chapter 10 lecture, equations 10.1–10.9

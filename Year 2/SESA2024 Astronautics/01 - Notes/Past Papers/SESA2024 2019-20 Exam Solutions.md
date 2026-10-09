---
title: "SESA2024 2019-20 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024 Semester 1 Examination 2019-20 (closed book; Section A all, Section B)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-201920-01-SESA2024.pdf"]
---

# SESA2024 2019-20 Exam Solutions

> [!abstract] Paper
> - A1: seven short questions.
> - B1: the GEO radius from first principles, longitude drift, a +100 km Hohmann.
> - B2: solar-array temperatures and power in SSO.
> - B3: the drag-decay derivation, a drag sail, hyperspectral data rate.
>
> This is the first paper in the "A/B" format used since. Numbers verified in Python; not the official scheme.

## Section A (A1)
**(i) Steps to the DRs (3)** ([[Systems Engineering Design Phases]]):
1. **Mission objectives** (from the customer).
2. **Payload definition** (specialists).
3. **Top-level requirements**: mission and system requirements, including orbit, lifetime, launcher and cost.
4. **Design requirements (DRs)** for each subsystem, found by analysis and trade-offs.

**(ii) Environment at 700 km, circular polar (8)**:
- **residual atmosphere**: small drag, and **atomic oxygen** erosion;
- **solar UV** and full solar flux; Earth IR and albedo;
- **thermal cycling** from about 14–15 eclipses per day (unless dawn–dusk);
- **trapped radiation**: inner-belt protons in the **South Atlantic Anomaly**, and outer-belt electrons at the **polar horns** at high latitude;
- **solar particle events** and **galactic cosmic rays**, which reach low altitude near the poles because the magnetic shielding is weaker there;
- **ionospheric and auroral plasma**, so charging;
- **micrometeoroids and debris** (700–900 km is the most congested band);
- the **geomagnetic field** (usable by magnetorquers).

**(iii) Products of inertia (2)**: the off-diagonal $I_{xy}, I_{xz}, I_{yz}$ ($\int xy\,dm$, …). They are zero only when the body axes are principal axes ([[Inertia Matrix]]).

**(iv) Attitude sensor categories (2)** ([[Attitude Sensors and Torquers]]):
- **reference sensors**, which measure direction to an external reference: Sun, Earth horizon, star trackers, magnetometers;
- **inertial sensors**: gyroscopes, which measure rate or angle change.

**(v) EP categories (3)**:
- **electrothermal** (resistojet, arcjet);
- **electrostatic** (gridded ion, Hall-effect);
- **electromagnetic** (MPD, PPT).

See [[Electric Propulsion Sizing]].

**(vi) Kepler's laws (4)**: ellipse with the central body at a focus; equal areas in equal times; $\tau^2\propto a^3$ ([[Kepler's Laws]]).

**(vii) First pass (3)**: $i\approx98^\circ$ (near-polar, Sun-synchronous); $e\approx0$; $a\approx7078$–$7278$ km ($h$ = 700–900 km).

## B1: GEO
**(i) Centripetal acceleration (6)**: $\mathbf v = r\dot\theta\,\hat{\boldsymbol\theta}$ with $r$ and $\dot\theta$ constant. Since $d\hat{\boldsymbol\theta}/dt = -\dot\theta\hat{\mathbf r}$:

$$\mathbf a = r\dot\theta\frac{d\hat{\boldsymbol\theta}}{dt} = -r\dot\theta^2\,\hat{\mathbf r}$$

So its magnitude is $a_c = r\dot\theta^2$ and it points to the centre (consistent with $a_r = \ddot r-r\dot\theta^2$).

**(ii) GEO radius (8)**:
- $m r\dot\theta^2 = \mu m/r^2$, so $r^3 = \mu/\dot\theta^2$.
- $\dot\theta = 2\pi/86\,160$ = 7.2925 × 10⁻⁵ rad/s.
- **$r$ = 42 163 km** ($h$ = 35 785 km).

**(iii) Above GEO (4)**: a larger $r$ gives a **longer period** ($\tau\propto r^{3/2}$) and a lower angular rate than the Earth. The sub-satellite point falls behind the rotating Earth, so the spacecraft **drifts westward** in longitude: about 1.28°/day at +100 km. To return, it descends back to GEO once at the new longitude. (Below GEO, it drifts east.)

**(iv) Hohmann GEO → GEO + 100 km (12)**:
- $r_1$ = 42 163 km, $r_2$ = 42 263 km, $a_T$ = 42 213 km.
- ΔV₁ = $V_{Tp}-V_1$ = 1.820 m/s; ΔV₂ = $V_2-V_{Ta}$ = 1.819 m/s.
- **Total 3.64 m/s**. (Check: the small-boost formula $V\Delta r/2r$ gives 3.65 m/s.)

## B2: SSO solar arrays (830 km, β = 7°)
**(i) Cell performance (8)**: see [[SESA2024 2014-15 Exam Solutions|2014/15 Q3(i)]].
- **Temperature**: efficiency and $V_{oc}$ fall as $T$ rises.
- **Sun angle**: output ∝ cos θ.
- **Radiation**: permanent $I_{sc}$ and $V_{oc}$ loss, so size for EOL ($D_0$).

**(ii) Array temperatures (12)**: each array is a flat, thermally decoupled plate that tracks the Sun.
- **Front**: $\alpha$ = 0.45, $\varepsilon$ = 0.9. **Back**: $\alpha = \varepsilon$ = 0.8.
- Output $= \sigma T^4(\varepsilon_f+\varepsilon_b)A$, so **$A$ cancels**.
- $a$ = 7208 km, $F = (R_E/a)^2$ = 0.783.

| Position | Inputs (W/m²) | $T$ |
|---|---|---|
| (a) Closest to the Sun (noon) | Sun on front: 1365(0.45); albedo on back: 0.34(1365)(0.8)(0.783)cos 7°; IR on back: 240(0.8)(0.783) | **50.2 °C** |
| (b) Terminator | Sun on front only | **9.4 °C** |
| (c) Farthest from the Sun | **Eclipse**: $a\sin\beta$ = 878 km < $R_E$. IR only, on the front (which faces the Earth there): 240(0.9)(0.783) | **−68.5 °C** |

> [!warning] Check for eclipse before computing the "far side" case
> With β = 7° the satellite passes through the shadow. If you wrongly keep the Sun on the array, you get +27 °C. The −68 °C answer is what makes part (iii)'s −70 °C efficiency relevant: that is the array at **eclipse exit**.

**(iii) Array power (3)**: $P = 2A\,S\,\eta\,\eta_p(1-D_0)$ = 2(7.5)(1365)η(0.9)(0.5).

| $T$ | η | EOL power | (BOL, without $D_0$) |
|---|---|---|---|
| 50 °C (steady sunlit, near noon) | 8.5 % | **783 W** | 1566 W |
| −70 °C (just after eclipse exit) | 14 % | **1290 W** | 2580 W |

**(iv) Power subsystem design (7)**:
- **Size the array for the hot, steady-state, EOL case (783 W)**. The cold-array surge at eclipse exit must be handled by the regulator: a **peak-power tracker** or shunt regulation, with the voltage limits of the bus and the battery charger.
- **Battery**: size for the eclipse (about 35 min per orbit, about 5500 cycles per year) at a modest DoD (Li-ion, about 20–30 %).
- **Rotating arrays** (a solar-array drive mechanism) keep the normal on the Sun. There are single-point failures, so use redundant strings and diodes.
- **Margins**: EOL degradation, eclipse heater power, and the temperature swing between −68 and +50 °C, which drives thermal-cycling fatigue of the interconnects.
- A regulated or unregulated bus choice; protection (fuses, fault isolation).

## B3: Drag and data rate
**(i) Why SSO and a repeat ground track (4)**:
- **SSO**: constant illumination (LST), so images are comparable and change detection is valid.
- **Repeat ground track**: the same viewing geometry on every revisit; a regular, known revisit period; simpler mission planning, ground stations and calibration; systematic global coverage.

**(ii) Derivation (6)**:
- Drag power $= -F V = -\tfrac12\rho V^3SC_D$. Specific energy $\varepsilon = -\mu/2r$, so $d\varepsilon = \dfrac{\mu}{2r^2}dr$.
- Over one orbit, $t = 2\pi r/V$:

$$\frac{\mu}{2r^2}\delta r = -\frac{\rho V^3SC_D}{2m}\cdot\frac{2\pi r}{V} = -\frac{\pi\rho V^2SC_Dr}{m}$$

- With $V^2 = \mu/r$:

$$\delta r = -2\pi\rho\frac{SC_D}{m}r^2$$

**(iii) Drag sail (6)**: $r$ = 7078 km, ρ = 10⁻¹⁴, $m$ = 50 kg, $C_D$ = 2.2.
- Without the sail ($S$ = 1 m²): **δr = −0.139 m/orbit**.
- With the sail ($S$ = 9 m²): **δr = −1.25 m/orbit**.
- It is **9× faster** (δr ∝ $S$), so it is effective: at 700 km the natural decay takes decades, and the sail brings it inside the 25-year guideline. It works because δr ∝ $S/m$ and grows as $r$ falls, since the density rises exponentially. But it is passive, so it cannot be steered. See [[Space Debris Mitigation]].

**(iv) Hyperspectral instrument (14)**:
- Elements per detector = 8 km/2 m = **4000**.
- **FOV** = $2\tan^{-1}(4/700)$ = **0.655°**.
- $V$ = 7.504 km/s, $V_g = VR_E/r$ = 6.762 km/s, line time 2/6762 = 0.296 ms.

$$R_b = \frac{4000\times12\times120}{0.296\times10^{-3}} = \mathbf{19.5\ Gbps}$$

- **It cannot stay uncompressed**. That is orders of magnitude above typical X-band downlinks (hundreds of Mbps to a few Gbps), and it would fill any memory in minutes.
- Needed: strong onboard compression (lossless about 2:1, lossy more), **band selection** (downlink only the useful bands), a limited imaging duty cycle (target-only), and possibly optical or Ka-band downlinks.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]

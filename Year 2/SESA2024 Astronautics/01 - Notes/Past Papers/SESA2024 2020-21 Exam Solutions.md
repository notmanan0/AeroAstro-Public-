---
title: "SESA2024 2020-21 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Assessment 2020/21 (24-hour open book, 9 questions on one reference mission)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-202021-01-SESA2024.pdf"]
---

# SESA2024 2020-21 Exam Solutions

> [!abstract] Paper
> A 24-hour paper built around one **reference mission**: a European land-cover imager.
> - 12-year life, $h$ = 750–800 km, complete coverage at the equator.
> - FOV 20.801°, 10 ± 2 m pixels (push-broom).
> - 10:30 LST descending node; thrusters for orbit control.
>
> Numbers verified in Python; not the official scheme.

> [!warning] Missing data set
> Several parts use the Blackboard **"Final Assessment Data Set"**: spacecraft mass, $I_{sp}$, power loads, cell and battery data, comms frequency and ground station, array finishes. **It is not in the vault.**
> - Everything the paper itself fixes is solved numerically below.
> - For data-set parts, the full method is given, with results expressed in terms of the unknowns, or with clearly labelled **illustrative** values.
>
> If you find the data set, drop it into `02 - Sources` and these can be finished.

## Q1: Environment (5)
At 750–800 km, Sun-synchronous (see [[SESA2024 2019-20 Exam Solutions|2019/20 A1(ii)]] for the 700 km list):
| Factor | Design effect |
|---|---|
| Residual atmosphere and **atomic oxygen** | Small drag, so orbit-control propellant (Q3). AO-resistant coatings on arrays and MLI. |
| **Solar UV** | Degrades $\alpha_S$ of surfaces, so size radiators for EOL $\alpha_S/\varepsilon$. |
| **Thermal cycling** (about 14 eclipses per day, about 35 min each) | Batteries sized for 63 000 cycles; heaters; fatigue-tolerant array interconnects. |
| **Trapped radiation**: SAA protons, polar-horn electrons | 12-year total dose, so rad-hard parts, shielding, cover glass, EOL array sizing, EDAC memory. |
| **Solar particle events, cosmic rays** (weak shielding at the poles) | SEU and latch-up protection; safe modes. |
| **Plasma** (auroral) | Charging, so a conductive exterior and grounding. |
| **Debris and micrometeoroids** (the 700–900 km band is the most crowded) | Shielding of critical units; collision-avoidance ΔV; **disposal** within 25 years ([[Space Debris Mitigation]]). |
| **Magnetic field** | A disturbance torque, but also usable by magnetorquers for momentum dumping. |

## Q2: Orbit
**(i) Sun- and Earth-synchronism (2)**:
- **Sun-synchronism** gives the same local solar time on every pass (10:30). Illumination and shadows are consistent, so land-cover **change detection** compares like with like.
- **Earth-synchronism** (a repeat ground track) returns to the same viewing geometry every $m$ days, gives systematic, gap-free coverage, and makes planning, calibration and ground-station scheduling predictable.

**(ii) $(n, m)$ (10)**:
- Swath $d = 2h\tan(20.801^\circ/2)$ = 0.367$h$, i.e. 275–294 km for 750–800 km.
- Complete equatorial coverage needs $nd\ge2\pi R_E$ = 40 074 km, so $n\ge$ 137–146. With about 14.3 orbits/day, that needs $m\ge10$.
- All coprime $(n, m)$ with 750 ≤ $h$ ≤ 800 km and $m\le11$:

| $(n,m)$ | $h$ (km) | $i$ | Swath (km) | Coverage |
|---|---|---|---|---|
| (43, 3) | 780.7 | 98.52° | 286.6 | 31 % ✗ |
| (72, 5) | 758.6 | 98.43° | 278.5 | 50 % ✗ |
| (100, 7) | 796.6 | 98.59° | 292.4 | 73 % ✗ |
| (115, 8) | 766.9 | 98.46° | 281.5 | 81 % ✗ |
| **(143, 10)** | **791.9** | **98.57°** | **290.7** | **104 % ✔** |
| (158, 11) | 770.7 | 98.48° | 282.9 | 112 % ✔ |

**Choose (143, 10)**: the shortest repeat (10 days) giving complete coverage, with 4 % overlap. (158, 11) is also valid and has more overlap, at the cost of a longer repeat.

Resolution check: the pixel is swath/elements. For 10 ± 2 m this needs about 24 000–36 000 elements. (The data set gives the actual CCD count; with 10 m pixels, 29 068 elements.)

**(iii) (2)**:
- $\tau = (10/143)86400$ = 6042.0 s, $a$ = 7169.9 km.
- **$h$ = 791.9 km**, **$i$ = 98.57°**.

**(iv) Ground-track sketch at 12:00 UTC, spring equinox (6)**:
- At 12:00 UTC the subsolar point is at 0°, 0°. The descending node at 10:30 LST is 1.5 h = **22.5° west** of the subsolar meridian, so **DN = (0°, 22.5°W)**.
- The ascending node is at 22:30 LST, i.e. 157.5°E in inertial terms. Because the Earth rotates during the half-orbit, the AN falls at **170.1°E** half an orbit before the DN, and at **144.9°E** half an orbit after. The shift is 25.2° west per orbit ($360^\circ\tau/\tau_E$ minus the regression).
- The track reaches latitudes ±81.4° (180° − $i$). It heads south through the DN in daylight and north through the AN at night.
- **Eclipse** ($t_e$ = 33.8 min; β = 22.2°, so slightly shorter than the 35.2 min worst case):
  - **entry** at about **63°S, 166°E**, before the AN;
  - **exit** at about **56°N, 153°E**, after the AN;
  - i.e. centred on the night-side node.

![[ast_2021_ground_track.png|800]]

## Q3: Orbit control (projected area 20 m²)
**(i) Worst-case cycle (6)**:
- **Worst case** means the table altitude nearest the orbit (800 km) at **high solar activity**: ρ = 2.22 × 10⁻¹⁴ kg/m³.
- $E_0$ = 0.75 km, so $\delta\lambda = 2E_0/R_E$ and $\Delta t_0 = \delta\lambda/\omega_E$ = **3.23 s**.
- $V$ = 7.456 km/s.

$$\delta a = -2\pi\rho\frac{SC_D}{m}a^2,\qquad\delta\tau = \frac{3\pi}{V}\delta a,\qquad k = \sqrt{\frac{2\Delta t_0}{|\delta\tau|}}$$

- The mass and $C_D$ come from the data set. **Illustrative** results with $C_D$ = 2.2:

| $m$ (kg) | δa (m/orbit) | δτ (ms) | $k$ | Cycle ($2k\tau$) | Height lost per cycle |
|---|---|---|---|---|---|
| 500 | −0.63 | −0.80 | 89 | **12.4 d** | 112 m |
| 1000 | −0.32 | −0.40 | 127 | **17.8 d** | 80 m |
| 1500 | −0.21 | −0.27 | 155 | **21.7 d** | 65 m |

- Scaling: $k\propto\sqrt m$, and the height lost per cycle $2k|\delta a|\propto1/\sqrt m$.

**(ii) Lifetime ΔV and propellant (10)**:
- Each boost is a small Hohmann: $\Delta V\approx V\Delta a/2a$. Summed over 12 years (62 900 orbits), the total height restored equals the total decay $N|\delta a|$:

$$\Delta V_{life} = \frac{V}{2a}N|\delta a|\quad(= 10.3\ \text{m/s for }m = 1000\text{ kg})$$

- Propellant: $M_p = m(1-e^{-\Delta V/V_{ex}})\approx m\Delta V/V_{ex}$.
- Because $\Delta V\propto1/m$, **$M_p$ is independent of the spacecraft mass**: about **4.8 kg** for $I_{sp}$ = 220 s (hydrazine), whatever $m$ is. Use the data-set $I_{sp}$.
- Worst case all mission long (solar max throughout) is conservative. Real density averages lower over an 11-year cycle, so add margin rather than extra propellant.

**(iii) One year without boosts (4)**:
- Decay continues, and faster as it proceeds, because density rises as the height falls. The height drops by roughly 1.6 km per year at solar max ($m$ = 1000 kg). That is small in altitude, but the **period shortens**, so the ground track drifts **eastward** well outside the ±0.75 km corridor ($\delta\tau$ accumulates quadratically: the along-track error grows as $t^2$).
- Consequences:
  - the **repeat pattern is lost**, so revisits no longer fall on the reference tracks and change detection must use resampled, non-identical geometry;
  - equatorial **gaps** can open between swaths (the overlap is only 4 %);
  - the node LST also drifts, because the SSO condition depends on $a$, so illumination changes slightly;
  - scale and resolution change very slightly.
- Recovery needs a larger boost (more propellant). The data are still usable, but not the systematic time series the mission promised.

## Q4: Stabilisation choice (4)
- A nadir-pointing imager needing slews about all three axes means **3-axis stabilisation**. A spinner cannot keep a push-broom imager on the ground or slew freely ([[Spacecraft Stabilisation Types]]).
- **Momentum bias** (a pitch momentum wheel along −y, the orbit normal) gives gyroscopic stiffness about roll and yaw and suits nadir pointing. But it resists slewing, because the bias has to be torqued around.
- Required **agility** and fine pointing (10 m pixels mean jitter must be much smaller than 1 pixel) favour **zero-bias 3-axis control with reaction wheels** (4 in a skewed pyramid for redundancy). Magnetorquers dump momentum ([[Reaction Wheels and Momentum Dumping]]).
- Rotating devices (wheels, the solar-array drive) cause **micro-vibration**. Isolate them and balance the wheels; the array drive's rotation about y must be compensated.
- Momentum stored in wheels is not "bias" if the net is zero, but zero-crossing speed disturbances matter for the imager.

## Q5: ACS instrumentation (5)
| Item | Why |
|---|---|
| **Star trackers** (2, cross-strapped) | Arcsec-level absolute attitude for image geolocation |
| **Gyros/IMU** | Rate and propagation between star fixes; slews; safe mode |
| **Sun sensors** (coarse, fine) | Safe-mode Sun acquisition; array pointing |
| **Earth/horizon sensor** | Nadir reference, backup |
| **Magnetometer** | Coarse attitude; magnetorquer commutation |
| **GNSS receiver** | Orbit and time, for pointing and geolocation |
| **Reaction wheels** (4) | Fine pointing and slews (internal torque) |
| **Magnetorquers** | Momentum dumping (external torque, no propellant) |
| **Thrusters** | Orbit control (Q3), backup dumping, safe mode |
| **On-board computer and software** | Estimation (Kalman filter) and closed-loop control laws |

See [[Attitude Sensors and Torquers]].

## Q6: Power (775 km)
**(i) (1)**:
- $a$ = 7153 km, $\tau$ = 100.3 min.
- **$t_e$ = 35.2 min** (worst case, β = 0).
- **62 900 cycles** in 12 years.

**(ii) Sizing method (7)**: the data set gives the load, cell efficiencies, voltages and degradation ([[SESA2024 08 - Electrical Power Subsystem]]).
1. Battery (Li-ion, **DoD 5 %**): $C = Pt_e/(\text{DoD}\,V_B)$ and $M = CV_B/\bar\varepsilon$. The very low DoD is set by the 62 900 cycles, which makes the battery 20× the eclipse energy.
2. Charge: $R = \text{DoD}\,C/t_s$ ($t_s$ = 65.2 min), so $P_{EOL} = P+RV_A$.
3. Array area: $A = P_{EOL}/[S\cos\theta\,\eta\,\eta_p(1-D_0)]$ for **Si** and for **GaAs**. GaAs has about 1.5–2× the efficiency and better radiation and temperature tolerance, so it needs about 40 % less area for the same power.
4. **One wing or two**: the same total area. Two symmetric wings balance the **aerodynamic and solar-pressure torques** and the centre of mass. One wing is simpler and lighter, but its offset centre of pressure creates a secular disturbance torque that the ACS must dump (and a bigger drag moment arm), plus a field-of-view clash on one side.

**(iii) Recommendation (6)**:
- **GaAs** (smaller, lighter array, less drag area, which feeds back into Q3, and better EOL performance over 12 years in a radiation environment), with **two symmetric wings** (torque balance, which eases the ACS and momentum dumping, and imager pointing stability).
- Justify with the mass and area numbers from (ii). A single wing may win on cost only if the disturbance torques are shown to be small.

## Q7: Downlink dish (15 W, 775 km)
**(i) Method (6)** ([[Link Budget Equation]]):
1. **Data rate** from the payload: $V_g = VR_E/a$ = 6.633 km/s, so the line time is $p/V_g$ = 1.51 ms for 10 m pixels. Then $R_b = N_{px}\times\text{bits}\times\text{bands}/t_{line}$. (29 068 pixels × 8 bits × 1 band = 154 Mbps; scale for the data-set bits and bands, and any compression.)
2. $C/N_0 = E_b/N_0+10\log R_b$.
3. Worst-case range: slant range at the minimum elevation ε, $\rho = \sqrt{a^2-R_E^2\cos^2\varepsilon}-R_E\sin\varepsilon$. At ε = 5° this is 2766 km.
4. $EIRP = C/N_0-G_R/T_R+20\log(4\pi\rho/\lambda)+L_A-228.6$.
5. $G_T = EIRP-10\log15$, so $D = \dfrac{\lambda}{\pi}\sqrt{\dfrac{G_T}{\eta}}$.

Sanity check: if $D$ comes out below a few wavelengths, a shaped or patch antenna is the realistic answer. A larger $D$ narrows the beam ($72\lambda/D$), which then needs pointing (a gimbal), because the spacecraft is nadir-locked.

**(ii) Cut to 7 W (3)**:
- $10\log(7/15)$ = **−3.3 dB**. To hold the same data rate the gain must rise 3.3 dB, i.e. **$D$ × 1.46**, which adds mass and a narrower beam.
- Otherwise the rate falls by 2.14× (longer contacts or more ground stations), or the margin is eaten.
- **Recommendation**: accept only if the link margin at 15 W exceeds 3.3 dB plus the required margin (about 3 dB). Otherwise keep 15 W. The power saved is small compared with the array's total, whereas the data volume *is* the mission.

## Q8: Array temperatures (775 km)
**(i) (7)**: for a thin, thermally decoupled plate tracking the Sun, every input and the output scale with the same area $A$:

$$T^4 = \frac{q_S\alpha_f+aq_S\alpha_bF\cos\phi+q_E\varepsilon_bF}{\sigma(\varepsilon_f+\varepsilon_b)}\ \ \text{(closest)},\qquad T^4 = \frac{q_E\varepsilon_fF}{\sigma(\varepsilon_f+\varepsilon_b)}\ \ \text{(farthest: eclipse)}$$

- **$T$ is independent of $A$.** That is the point of asking "as a function of $A$".
- $F = (R_E/a)^2$ = 0.795. With β = 22°, $a\sin\beta$ = 2713 km < $R_E$, so the farthest point **is in eclipse**.
- **Illustrative** finishes (front 0.45/0.9, back 0.8/0.8, as in [[SESA2024 2019-20 Exam Solutions|2019/20 B2]]): **≈ 49 °C** closest and **≈ −68 °C** farthest.
- Assumptions: isothermal plate, decoupled from the bus, no electrical power extracted (conservative for the hot case), $\alpha_{IR} = \varepsilon$, Sun-normal, $F$ as for a sphere.

**(ii) (2)**: the **cold eclipse case** (about −68 °C, cycling to +49 °C 62 900 times). The 117 K swing drives **thermal-cycling fatigue** of cell interconnects and solder joints, and of the adhesive and CTE mismatch. Also, at eclipse exit the cold array produces a high-voltage surge that the regulator must handle.

**(iii) Improvements (5)**:
- Raise the rear emissivity to lower the hot case, or adjust the front $\alpha/\varepsilon$ with coatings.
- Add thermal mass (a thicker substrate) to damp the eclipse swing.
- Use GaAs, which is more temperature-tolerant and better at high $T$.
- Choose CTE-matched interconnects and qualify for the cycle count.
- Tilt off the Sun (feathering) if there is excess power in the hot case.
- Consider a dawn–dusk-like higher β (not possible with 10:30 LST, so accept it and qualify).

Two smaller wings behave the same as one large one, since $T$ is independent of $A$. The area choice is set by power and torque, not temperature.

## Q9: Subsystem interactions (9)
**(i) (7)**:
- **Payload → orbit**: FOV and resolution → swath → $(n, m)$ → $h$ and $i$ (Q2).
- **Orbit → power**: $h$ sets the eclipse (35 min) → battery and cycles → array area (Q6).
- **Orbit → propulsion**: $h$ and area → drag → ΔV and propellant (Q3).
- **Array area → drag → propulsion**; **array symmetry → disturbance torques → ACS**.
- **Payload data rate → comms power and antenna → power budget** (Q7).
- **Power level and array temperature → thermal** (Q8).
- **ACS pointing and jitter → image quality**; wheels → micro-vibration.
- **Lifetime** (12 years) → radiation dose, cycles and propellant everywhere.

**(ii) (2)**: the **payload FOV and resolution, and the 750–800 km band**. Together they fixed the swath and orbit ((143, 10) at 792 km). The **12-year lifetime** then multiplies through cycles, propellant and degradation. Those few inputs cascade into every subsystem's sizing.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Legacy Papers 2013-2021 Key Answers]] · [[SESA2024 Astronautics Hub]]
- Method notes: [[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission]] · [[SESA2024 14 - Orbit Control, Drag and Payload Data Rate]]

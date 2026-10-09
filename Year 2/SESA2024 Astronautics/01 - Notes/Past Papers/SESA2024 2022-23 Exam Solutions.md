---
title: "SESA2024 2022-23 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Final Assessment 2022/23 (file is misnamed SESA2024-202425-01-SESA2024.pdf)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-202425-01-SESA2024.pdf"]
---

# SESA2024 2022-23 Exam Solutions

> [!abstract] Paper
> - B1: Artemis 1 / OMOTENASHI (rocket equation, orbits).
> - B2: array thermal at 18 000 km (= workbook Ch10 Q7) plus an L-band link.
> - B3: Starlink in SSO (inclination, ground track, drag cycle, attitude).
>
> The file `SESA2024-202425-01-SESA2024.pdf` is this **2022/23** paper. Worked solutions verified in Python; not the official scheme.

## Section A
**A1 (4)**: chemical against electric for a lunar mission.
- Chemical: high thrust (kN), so transfers take about 3 days, with impulsive capture and landing burns; low $I_{sp}$ (300–450 s), so a large propellant fraction; no large power demand.
- EP: $I_{sp}$ 1000–5000 s, so much less propellant; mN-level thrust means months-long spiral transfers; needs kW of power (large arrays); cannot land.
- Crewed and landing missions need chemical propulsion. EP suits cargo or orbiters where time is available.

**A2 (4)**: sketch $\mathbf H_0$ and a disturbance impulse $\mathbf T\,dt$ perpendicular to it. The new $\mathbf H_1$ turns by $d\psi = T\,dt/H_0$. A large bias gives a small angle, so the attitude is **gyroscopically stiff**. Without bias, the same impulse produces a rate $T\,dt/I$ that accumulates. See [[Momentum Bias and Gyroscopic Rigidity]].

**A3 (4)**: eclipse = ⅓ of the orbit, so $180-2\rho = 120^\circ$, giving $\rho = 30^\circ$. Then $a = R_E/\cos30^\circ$ = 7365 km and **$h$ ≈ 987 km**.

**A4 (3)**: $P_R\propto P_TG_TG_R/(4\pi\rho/\lambda)^2$. At Saturn, $\rho\approx8$–10 AU (about 1.4 × 10⁹ km), so the free-space loss is about 290 dB. The flux spreads over $4\pi\rho^2$. The spacecraft's power and antenna size are also limited (RTG power).

**A5 (3)**: when solar input dominates, $T\propto(\alpha_S/\varepsilon)^{1/4}$. Choosing surface finishes sets $T$ with no power or mechanisms, which is the basis of passive thermal control. The ratio also degrades as $\alpha_S$ rises with UV and atomic oxygen.

**A6 (5)**: S sits at 570 km, 96 min.
- **A** (ΔV forward): its apogee rises above 570 km and its period is > 96 min. Plot it upper right.
- **B** (ΔV backward): its *apogee* stays at 570 km (the burn point) and its period is < 96 min. Plot it at the same apogee height, to the left of S.

The plot forms the classic "X" of a Gabbard diagram, with perigees going the other way.

**A7 (2)**: descending node with the Sun behind the Earth means midnight, so **00:00 LST**.

## B1: OMOTENASHI
**(i) (7)** $M_b$ = 2.4 kg, $\Delta V$ = 2.5 km/s, $I_{sp}$ = 260 s, so $V_{ex}$ = 2551 m/s.

$$M_0 = 2.4e^{2500/2551} = 6.40\ \text{kg}\Rightarrow M_p = \mathbf{4.0\ kg}$$

$$\dot m = \frac{T}{g_0I_{sp}} = 0.196\ \text{kg/s}\Rightarrow t_b = \mathbf{20.4\ s}$$

**(ii) (4)** Spinning about the thrust axis gives:
- **gyroscopic stiffness** (momentum bias) against disturbance torques;
- **averaging of thrust misalignment and CG offset**, which would otherwise tumble the vehicle.

The small probe has no active thrust-vector control, so spin-stabilising a solid motor burn is the standard solution.

**(iii) (3)** Free fall from rest: $v^2 = 2g_Mh$, so $h = 30^2/(2\times1.62)$ = **278 m** maximum.

**(iv) (8)**:
- Artemis orbit: 516 × 377 200 km altitude, $a_1$ = 195 236 km, $e_1$ = 0.9647.
- New orbit: 521 × 379 650 km, $a_2$ = 196 464 km, $e_2$ = 0.9649.
- At $r$ = 155 000 km: $V_1$ = 1.7611 km/s and $V_2$ = 1.7648 km/s.
- Flight-path angles: $\cos\gamma = h/(rV)$ with $h = \sqrt{\mu a(1-e^2)}$, giving $\gamma_1$ = 74.385° and $\gamma_2$ = 74.411°.

$$\Delta V = \sqrt{V_1^2+V_2^2-2V_1V_2\cos(\gamma_2-\gamma_1)} = \mathbf{3.7\ m/s}$$

(The speed difference alone is 3.6 m/s. The small angle change adds little.)

**(v) (4)** $r$ = 287 378 km on orbit 2:

$$\cos\theta = \frac1{e_2}\left[\frac{a_2(1-e_2^2)}{r}-1\right]\Rightarrow\theta = \mathbf{170.9^\circ}$$

It is outbound, before apogee.

**(vi) (4)** Apogee at the Moon's radius: $a$ = (6894 + 384 400)/2 = 195 647 km.

$$t = \pi\sqrt{a^3/\mu} = \mathbf{4.98\ days}$$

## B2: Array thermal and L-band link
**(i) (15)** This is identical to workbook Ch10 Q7.
- **No eclipse**: $R_0 = 18\,000\sin23.5^\circ$ = 7177 km > $R_E$.
- Noon **49 °C**, midnight **46 °C**, terminator **44 °C**.

Full working in [[SESA2024 Workbook Ch10 - Thermal Control Solutions]].

**(ii) (15)** $\lambda$ = 0.1905 m, $\rho$ = 18 000 − 6378 = 11 622 km.
- $C/N_0$ = 10 + 10 log(240 000) = 63.80 dB-Hz.
- $L_{FS}$ = 177.7 dB.
- **EIRP = 63.80 + 21.7 + 177.7 − 228.6 = 34.6 dBW**.
- Global coverage: $\alpha = \sin^{-1}(6378/18\,000)$ = 20.75°, so $\theta_{3dB}$ = 41.5° and $D$ = 0.33 m.
- With $\eta$ = 0.65, $G_T$ = 12.9 dB, so $P_T$ = 149 W and $P_{elec}$ = 149/0.55 ≈ **271 W ≈ 272 W** ✔.

## B3: Starlink in SSO
**(i) (3)** An SSO passes each latitude at a fixed LST:
- predictable, repeatable **Sun geometry**, which gives stable power (with a dawn–dusk orbit, near-continuous sunlight and little eclipse);
- stable thermal conditions;
- a fixed ground-track and service pattern;
- polar coverage for "near-global" service.

**(ii) (8)** Daily repeat near 567 km: $\tau(567)$ = 5760 s, so $n = 86400/5760$ = **15.00, i.e. $n$ = 15** ($m$ = 1). $a$ = 6945.0 km and **$i$ = 97.66°**.

**(iii) (7)** Ground-track sketch at 18:00 UTC on the spring equinox:
- The **6 pm descending node** is 6 am ascending: a dawn–dusk orbit riding the terminator.
- At 18:00 UTC the local 18:00 meridian is Greenwich. So the **descending node is at about 0° longitude**, and the ascending node is about 180° away (minus a half-orbit westward shift of about 12°).
- Maximum latitude 180° − 97.66° = **82.3°**.
- At the equinox the dawn–dusk plane lies almost along the terminator, so the eclipse is essentially zero. Show a brief shadow crossing near the poles, or none, and say so.

**(iv) (8)** Worst-case area: the array face-on to the velocity, $S = 2.2\times6.6$ = 14.52 m² (the bus edge is negligible).

$$\delta a = -2\pi(1.9\times10^{-13})\frac{14.52(2.2)}{250}(6.945\times10^6)^2 = -7.36\ \text{m/orbit}$$

- A 2 km tolerance allows 2000/7.36 = 272 orbits = 272 × 5760 s = **18.1 days, so 18 days** between boosts.
- (If the bus face, 5.3 m², is also counted: 13 days.)

**(v) (4)** To minimise ΔV, fly the **array edge-on to the velocity vector**:
- the array plane contains the local vertical and the velocity, i.e. it lies in the orbit plane;
- the bus stays flat, Earth-facing, with its thin edge forward.

In a dawn–dusk SSO the Sun is roughly normal to the orbit plane, so this attitude also points the array face at the Sun. Minimum drag and maximum power together.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Astronautics Hub]]

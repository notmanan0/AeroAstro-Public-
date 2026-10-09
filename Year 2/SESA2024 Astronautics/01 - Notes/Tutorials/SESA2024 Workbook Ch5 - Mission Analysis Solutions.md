---
title: "SESA2024 Workbook Ch5 - Mission Analysis Solutions"
module: "SESA2024 Astronautics"
type: tutorial
stream: "Mission Analysis"
tags:
  - sesa2024
  - tutorial-solutions
  - orbital-mechanics
  - hohmann-transfer
sheet: "Problem Sheet Workbook 2025-26, Chapter 5 (pp. 41-51)"
theory_notes: ["[[SESA2024 02 - Kepler's Laws and the Orbit Equation]]", "[[SESA2024 03 - Orbital Elements and Conic Sections]]", "[[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]]", "[[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]"]
key_concepts: ["[[Orbital Angular Momentum]]", "[[Vis-Viva Equation]]", "[[Orbit Equation and Conic Sections]]", "[[Hohmann Transfer]]", "[[Tsiolkovsky Rocket Equation]]"]
status: complete
sources: ["02 - Sources/Lectures/SESA2024 Astronautics PROBLEM SHEET WORKBOOK 2025-26 V1.1.pdf"]
---

# SESA2024 Workbook Ch5 - Mission Analysis Solutions

> [!abstract] Sheet Info
> Eight questions: four derivations (Q1–3, Q5), one orbit classification (Q4), one discussion (Q6) and two transfer calculations (Q7 LEO→GEO with staging; Q8 heliocentric comet intercept). Constants: $R_E = 6378$ km, $\mu_E = 398\,600$ km³/s². Every number was reproduced in Python ✔.

## Theory Links
- [[SESA2024 02 - Kepler's Laws and the Orbit Equation]] · [[SESA2024 04 - Orbital Energy and the Vis-Viva Equation]] · [[SESA2024 05 - Orbital Transfers and the Hohmann Transfer]]
- Concepts: [[Orbital Angular Momentum]] · [[Vis-Viva Equation]] · [[Orbit Equation and Conic Sections]] · [[Hohmann Transfer]] · [[Tsiolkovsky Rocket Equation]]

---

## Q1: Invariant plane and $r_pV_p = r_aV_a$
- $m\mathbf h = \mathbf r\times m\mathbf V$, so $\mathbf h$ is perpendicular to both $\mathbf r$ and $\mathbf V$ (right-hand rule). $\mathbf h$ is therefore the **orbit-plane normal**.
- $\mathbf h$ is conserved (central force, zero torque), so the normal is fixed and **the motion stays in an unchanging plane**.
- At perigee and apogee, $\mathbf r\perp\mathbf V$ (the flight-path angle is zero). So

$$
\mathbf h_p = \mathbf h_a\ \Rightarrow\ r_pV_p\sin90^\circ = r_aV_a\sin90^\circ\ \Rightarrow\ \boxed{r_pV_p = r_aV_a}
$$

## Q2: Show $\varepsilon = -\mu/2a$
From Q1, $V_p/V_a = r_a/r_p$. From energy conservation, $\tfrac12V^2 = \varepsilon+\mu/r$ at both apses. Dividing:

$$
\frac{r_a^2}{r_p^2} = \frac{\varepsilon+\mu/r_p}{\varepsilon+\mu/r_a}\ \Rightarrow\ r_a^2\Big(\varepsilon+\frac{\mu}{r_a}\Big) = r_p^2\Big(\varepsilon+\frac{\mu}{r_p}\Big)\ \Rightarrow\ \varepsilon(r_a^2-r_p^2) = \mu(r_p-r_a)
$$

$$
\varepsilon = \frac{\mu(r_p-r_a)}{(r_a+r_p)(r_a-r_p)} = -\frac{\mu}{r_a+r_p} = -\frac{\mu}{2a}
$$

using $r_a+r_p = 2a$.

## Q3: Hohmann total $\Delta V$ in terms of $x = r_1/r_2$
From the two burns (see [[Hohmann Transfer]]):

$$
\Delta V = \sqrt{\frac{\mu}{r_1}}\left\{\sqrt{\frac{2r_2}{r_1+r_2}}-1\right\}+\sqrt{\frac{\mu}{r_2}}\left\{1-\sqrt{\frac{2r_1}{r_1+r_2}}\right\}
$$

With $V_1 = \sqrt{\mu/r_1}$:

$$
\sqrt{\frac{\mu}{r_2}} = x^{1/2}V_1,\qquad \sqrt{\frac{2r_2}{r_1+r_2}} = \sqrt{\frac{2}{x+1}},\qquad \sqrt{\frac{2r_1}{r_1+r_2}} = \sqrt{\frac{2x}{x+1}}
$$

$$
\Delta V = V_1\Big\{\sqrt{\tfrac{2}{x+1}}-1\Big\}+x^{1/2}V_1\Big\{1-x^{1/2}\sqrt{\tfrac{2}{x+1}}\Big\} = V_1\left[\left(\frac{2}{x+1}\right)^{1/2}(1-x)+x^{1/2}-1\right]\quad\checkmark
$$

![[ast_hohmann_dv_ratio.png|600]]

## Q4: Unidentified object: apogee height 1000 km, speed 5.589 km/s
- An apogee exists (the object is bound), so it is **not an escaping probe**.
- Energy equation with $r_a = 7378$ km: $\dfrac{V^2}{2}-\dfrac{\mu}{r_a} = -\dfrac{\mu}{2a}$ gives $a = 5189$ km.
- $e = r_a/a-1 = 0.4218$, so $r_p = a(1-e) = 3000$ km, which is **less than $R_E$**.
- The orbit intersects the Earth, so the object is most likely a **ballistic missile**.

## Q5: Prove $r_{apoapsis} = a(1+e)$
At apogee $\theta = 180^\circ$:

$$
r = \frac{a(1-e^2)}{1+e\cos180^\circ} = \frac{a(1-e)(1+e)}{1-e} = a(1+e)
$$

## Q6: Hohmann transfer for interplanetary missions
- **Advantage**: it is the minimum-$\Delta V$ two-impulse transfer between coplanar circular orbits, so it uses the least fuel.
- **Disadvantage**: long transfer times to the outer planets. Uranus takes about 16 years and Neptune about 30. Reliable operation after arrival becomes doubtful.
- Other points worth making:
  - It needs a **launch window**, because the planets must have the correct phasing.
  - Real planetary orbits are not exactly coplanar or circular.
  - In practice, faster (higher-energy) or gravity-assist trajectories trade $\Delta V$ against time.

## Q7: 300 km equatorial → GEO; staged masses
$r_1 = 6678$ km and $r_2 = 42\,164$ km.

$$
\Delta V_1 = \sqrt{\frac{\mu}{r_1}}\left\{\sqrt{\frac{2r_2}{r_1+r_2}}-1\right\} = \mathbf{2.426\ km/s},\qquad \Delta V_2 = \sqrt{\frac{\mu}{r_2}}\left\{1-\sqrt{\frac{2r_1}{r_1+r_2}}\right\} = \mathbf{1.467\ km/s}
$$

Total 3.893 km/s. It is slightly less than the 200 km case (3.933 km/s), because the start orbit is higher.

**Masses** ($V_{ex} = 3$ km/s, $M_1 = 2500$ kg):
1. After burn 1: $M_2 = M_1e^{-\Delta V_1/V_{ex}} = 2500e^{-2.426/3} = 1113.6$ kg.
2. Discard the 136 kg dry stage: $M_3 = 977.6$ kg.
3. After burn 2: $M_{final} = 977.6e^{-1.467/3} = 599.5\approx\mathbf{600\ kg}$ in GEO.

Only 24 % of the LEO mass reaches GEO.

## Q8: Comet intercept (heliocentric Hohmann)
**Data**: $r_E = 1.5\times10^8$ km, $\mu_{Sun} = 1.3\times10^{11}$ km³/s². Comet: $a = 30\times10^8$ km, $e = 0.9$, orbit plane at 90° to the ecliptic, crossing it at perihelion.

**Comet at perihelion**:

$$
r_{cp} = a(1-e) = 3\times10^8\ \text{km},\qquad V_{cp} = \sqrt{2\mu\Big(\frac{1}{r_{cp}}-\frac{1}{2a}\Big)} = \mathbf{28.69\ km/s}
$$

**Transfer injection**:
- The probe starts on Earth's circular orbit: $V_{circ} = \sqrt{\mu/r_E} = 29.44$ km/s.
- Transfer orbit: $a_T = \tfrac12(r_E+r_{cp}) = 2.25\times10^8$ km.
- $V_{Tp} = \sqrt{2\mu(1/r_E-1/2a_T)} = 33.99$ km/s, so

$$
\Delta V = 33.99-29.44 = \mathbf{4.55\ km/s}
$$

**Firing time**: half the transfer period before the comet's perihelion:

$$
T_{firing} = \tfrac12\cdot2\pi\sqrt{a_T^3/\mu} = 2.941\times10^7\ \text{s}\approx\mathbf{340\ days}
$$

**Relative speed at fly-by**:
- The probe arrives at transfer aphelion: $V_{Ta} = \sqrt{2\mu(1/r_{cp}-1/2a_T)} = 17.00$ km/s, in the ecliptic.
- The comet's velocity is perpendicular to the ecliptic (orbit plane at 90°) and perpendicular to the radius at perihelion.

The two velocities are orthogonal:

$$
V = \sqrt{V_{Ta}^2+V_{cp}^2} = \sqrt{17.00^2+28.69^2} = \mathbf{33.35\ km/s}
$$

> [!tip] Pattern
> "Relative velocity at encounter" is always a vector subtraction. When the orbits are perpendicular, Pythagoras applies. When they are coplanar and tangential (2024/25 B1 asteroid), it is a straight subtraction.

## Sources
- Workbook 2025-26 Chapter 5 questions (p. 41–43) and solutions (p. 47–51)
- Lecture worked examples: orbital energy (L10), Hohmann transfer (L13)

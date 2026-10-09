---
title: "SESA2024 2023-24 Exam Solutions"
module: "SESA2024 Astronautics"
type: past-paper
tags: [sesa2024, past-papers, solutions]
paper: "SESA2024W1 Semester 1 Final Assessment 2023/24 (online open-book)"
status: complete
sources: ["03 - Exams & Past Papers/SESA2024-202324-01-SESA2024.pdf"]
---

# SESA2024 2023-24 Exam Solutions

> [!abstract] Paper
> - Section A: 7 questions.
> - B1: Starship IFT-2 (orbits and rocket equation).
> - B2: C-band link, dish sizing, GEO batteries.
> - B3: Jupiter Sun-synchronous orbiter (inclination, repeat track, Hohmann maintenance, thermal material).
>
> These are my worked solutions, verified in Python. They are not the official scheme.

## Section A
**A1 (2)**: $V_{ex} = g_0I_{sp} = 9.81\times240$ = **2354 m/s**. (Mars is irrelevant: $g_0$ is a definition constant.)

**A2 (2)**: **C**. A zero-bias 3-axis spacecraft has (nominally) zero angular momentum.

**A3 (6)**: read from Figure A3 (spring equinox, so the Sun line is ♈). The figure shows a highly eccentric orbit:
- perigee low over the southern hemisphere, apogee high over the north;
- the orbit crosses the equator on the Sun line, moving southward.

Best reading (25 % margin):
- **$e\approx0.7$** and **$a\approx26\,000$ km**: a **Molniya-type** orbit;
- **$i\approx63^\circ$**;
- **$\omega\approx270^\circ$** (apogee in the north);
- the crossing on the Sun line is the *descending* node, so **$\Omega\approx180^\circ$**;
- the satellite at that node gives **$\theta\approx270^\circ$**.

> [!warning] These are figure-reading estimates. Check them against your copy of the figure.

**A4 (5)**: $a$ = 7072 km, $\tau$ = 98.6 min.

$$t_e = \frac{180-2\cos^{-1}(6378/7072)}{360}\tau = \mathbf{35.3\ min}$$

At the equinox, a (near-)equatorial or SSO orbit plane containing the Sun line is the worst case.

**A5 (3)**: in eclipse $Q_S = Q_a = 0$ and $P = 0$:

$$q_E\varepsilon A_E^{proj}F = \varepsilon\sigma T^4A_{surf}$$

$\varepsilon$ cancels and $\alpha_S$ never appears, so $T$ is independent of both.

**A6 (5)**: $\tau$ = 86400/15 = 5760 s, $a$ = 6945.0 km, **$h$ = 567 km**.

**A7 (2)**: nodes are 12 h apart in LST. A 06:00 descending node gives an **18:00 ascending node** (a dawn–dusk orbit).

## B1: Starship IFT-2
**(i) (5)** At apogee, $r_a$ = 6378 + 148 = 6526 km and $V$ = 6.760 km/s:

$$\frac1a = \frac{2}{r_a}-\frac{V^2}{\mu}\Rightarrow a = \mathbf{5213\ km},\qquad e = \frac{r_a}{a}-1 = \mathbf{0.252}$$

The perigee radius, 3900 km, is inside the Earth: suborbital.

**(ii) (4)** At 90 km altitude ($r$ = 6468 km):

$$\cos\theta = \frac1e\left[\frac{a(1-e^2)}{r}-1\right]\Rightarrow\theta = 166.7^\circ\text{ or }193.3^\circ$$

The fragments are **descending after apogee**, so **θ ≈ 193°**.

**(iii) (3)** $T = \dot m g_0I_{sp}\times3 = 3(650)(9.81)(333)$ = **6.37 MN**.

**(iv) (11)** $V_{ex}$ = 3267 m/s; $M_0$ = 1 320 000 kg; separation speed 1522 m/s.
- **Planned**: the 250 × 190 km orbit has $a$ = 6598 km. Take insertion at perigee (190 km): $V$ = 7808 m/s.
  - $\Delta V_{plan}$ = 6286 m/s, so $M_{b,plan} = M_0e^{-6286/3267}$ = 192 700 kg.
- **Actual**: $\Delta V$ = 6760 − 1522 = 5238 m/s, so the propellant *used for thrust* left $M_b = M_0e^{-5238/3267}$ = 265 600 kg.
- The tanks were nevertheless depleted early. **Propellant lost to leaks ≈ 265 600 − 192 700 ≈ 73 t**.
- (Taking insertion at the 250 km apogee instead: $V$ = 7737 m/s, giving ≈ 69 t. State your assumption.)

**(v) (2)** Burn time = (1 320 000 − 192 700)/(3 × 650) ≈ **578 s** (9.6 min).

**(vi) (5)** Ground-track sketch from Boca Chica (26°N, 97°W) to the Pacific splashdown, eastward along an inclined arc. Mark:
- the peak latitude of about 26° or more, which sets $i\ge26^\circ$;
- the descending node over the Atlantic or Africa;
- the ascending node near the Indian Ocean or Pacific.

Flight time is less than one orbital period. With $a$ = 6598 km, $\tau$ = 88.9 min, so about 1–1.5 h from launch to splashdown.

## B2: C-band link, dish and batteries
**(i) (12)** $\lambda$ = 0.0732 m.
- $C/N_0$ = 9 + 10 log(1.5 × 10⁸) = **90.76 dB-Hz**.
- $L_{FS} = 20\log(4\pi\cdot3.68\times10^7/0.0732)$ = **196.01 dB**.

$$EIRP = 90.76-(-16)+196.01+6-228.60 = \mathbf{80.2\ dBW}$$

**Significance**: the isotropic-equivalent transmitted power; it fixes the flux delivered to the receiver.

**(ii) (6)** From GEO the Earth's disc has a half-angle $\alpha = \sin^{-1}(1/6.611)$ = 8.7°. The Northern hemisphere spans about $\alpha$ (from the sub-satellite equator to the northern limb).
- 0.6 m: $\theta_{3dB} = 72(0.0732)/0.6$ = **8.8°**, which matches the hemisphere ✔.
- 0.8 m: 6.6°, too narrow.
- **Choose 0.6 m.**

General: a larger dish means higher gain and less power but a smaller footprint and tighter pointing. A smaller dish means wider coverage but needs more $P_T$.

**(iii) (12)** In GEO, $\tau$ = 23.93 h and **$t_e$ = 1.157 h**.
- Cycles in 10 years = **3662**.

| | DoD | $C = Pt_e/(\text{DoD}\,V_B)$ | $\mathcal E$ | Mass |
|---|---|---|---|---|
| NiCd | 40 % | **1052 A·h** | 28 920 W·h | **964 kg** (30 W·h/kg) |
| NiH₂ | 60 % | **701 A·h** | 19 280 W·h | **386 kg** (50 W·h/kg) |

**Volume**: NiCd stores 1.5× more energy per unit volume, but it must store 1.5× more total energy (28 920 against 19 280 W·h). So the **volumes are equal**. **NiH₂ saves about 580 kg at the same volume**, so choose NiH₂ (or Li-ion today).

## B3: Jupiter Sun-synchronous orbiter
Data: $R_J$ = 69 911 km, $\mu_J$ = 1.26687 × 10⁸ km³/s².

**(i) (3)** $a$ = 76 911 km, $\cos i = -3.33758\times10^{-20}a^{3.5} = -0.00421$, so **$i$ = 90.24°**.

**(ii) (9)** $\tau(7000\ \text{km}) = 2\pi\sqrt{a^3/\mu_J}$ = 11 907 s, and $n/m = 35\,733/11\,907$ = 3.001.
- **$(n,m) = (3,1)$**: 3 orbits per Jupiter day, so every target is revisited daily ✔.
- $\tau$ = 35 733/3 = 11 911 s, $a$ = 76 929 km, **$h$ = 7018 km**.
- ($i$ becomes 90.24°.)

**(iii) (9)** Hohmann between $a\mp20$ km, with $V$ = 40.58 km/s:

$$\Delta V\approx V\frac{\Delta r}{2a} = 40.58\times\frac{40}{2(76\,929)} = \mathbf{10.6\ m/s\ per\ cycle}$$

(The full vis-viva calculation gives 10.55 m/s.)

**(iv) (9)** Cube, 1.25 m side ($A$ = 1.5625 m², $A_{surf}$ = 9.375 m²), with one face to the Sun and one to Jupiter. $F = (R_J/a)^2$ = 0.826.
- **Eclipse** (75 W heater): $T^4 = [14\varepsilon A F+75]/(\varepsilon\sigma A_{surf})$.
- **Sunlit** (noon): $T^4 = [50.3\alpha A+0.5(50.3)\alpha AF+14\varepsilon AF]/(\varepsilon\sigma A_{surf})$.

| Finish | Eclipse | Sunlit |
|---|---|---|
| Black paint | −156 °C | −148 °C |
| White paint | −156 °C | −187 °C |
| **SiO-Al dark mirror** | **−11 °C** | **+9 °C** |
| MLI | −11 °C | −113 °C |

- **SiO-Al is the most suitable**: it is closest to the 10–30 °C window in both phases.
- It still falls short. The eclipse case needs about 102 W of heater to reach 10 °C, so recommend **more heater power** (or insulating the radiating area).
- **Why**: at 5.2 AU sunlight is 27× weaker, so the spacecraft must be a high-$\alpha_S$, low-$\varepsilon$ body to stay warm.

## Links
- [[SESA2024 Past Paper Trend Analysis]] · [[SESA2024 Astronautics Hub]]

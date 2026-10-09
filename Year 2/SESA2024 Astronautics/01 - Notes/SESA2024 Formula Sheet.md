---
title: "SESA2024 Formula Sheet"
module: "SESA2024 Astronautics"
type: formula
tags: [sesa2024, formula-sheet, revision]
status: complete
sources: ["02 - Sources/Lectures", "03 - Exams & Past Papers"]
---

# SESA2024 Formula Sheet

> [!info] Constants
> - $R_E$ = 6378 km; $\mu_E$ = 398 600 km³/s²; $g_0$ = 9.81 m/s²
> - $R_{GEO}$ = 42 164 km = 6.611 $R_E$; sidereal day $\tau_E$ = 86 164 s; year $\tau_Y$ = 3.155815 × 10⁷ s
> - $\mu_{Sun}$ = 1.327 × 10¹¹ km³/s²; 1 AU = 1.496 × 10⁸ km
> - $k$ = 1.38 × 10⁻²³ J/K (−228.6 dB); $c$ = 3 × 10⁸ m/s; $\sigma$ = 5.67 × 10⁻⁸ W m⁻² K⁻⁴
> - $q_S$ ≈ 1350–1400 W/m²; $q_E$ = 240 W/m²; albedo $a$ = 0.34
>
> **Given on recent papers**: energy equation, rocket equation, ellipse equation, and sometimes the drag δa. **Everything else must be known.**

## Orbits ([[SESA2024 02 - Kepler's Laws and the Orbit Equation|Ch 5]])
| | |
|---|---|
| Orbit equation | $r = \dfrac{a(1-e^2)}{1+e\cos\theta} = \dfrac{h^2/\mu}{1+e\cos\theta}$ |
| Apses | $r_p = a(1-e)$, $r_a = a(1+e)$, $a = \tfrac12(r_p+r_a)$, $e = \dfrac{r_a-r_p}{r_a+r_p}$ |
| Angular momentum | $h = r^2\dot\theta = rV\cos\gamma = \sqrt{\mu a(1-e^2)}$, $r_pV_p = r_aV_a$ |
| Kepler 3 | $\tau = 2\pi\sqrt{a^3/\mu}$, $a = [\mu(\tau/2\pi)^2]^{1/3}$ |
| **Energy (vis-viva)** | $\dfrac{V^2}{2}-\dfrac{\mu}{r} = -\dfrac{\mu}{2a}$ |
| Circular / escape | $V_c = \sqrt{\mu/r}$, $V_{esc} = \sqrt{2\mu/r}$ |
| True anomaly | $\cos\theta = \dfrac1e\left[\dfrac{a(1-e^2)}{r}-1\right]$ |
| Acceleration (polar) | $a_r = \ddot r-r\dot\theta^2$, $a_\theta = 2\dot r\dot\theta+r\ddot\theta$ |

## Transfers ([[SESA2024 05 - Orbital Transfers and the Hohmann Transfer|Ch 5]])
| | |
|---|---|
| Hohmann | $a_T = \tfrac12(r_1+r_2)$; $\Delta V_1 = V_{Tp}-V_1$; $\Delta V_2 = V_2-V_{Ta}$; $t = \pi\sqrt{a_T^3/\mu}$ |
| Closed form | $\Delta V_1 = \sqrt{\tfrac{\mu}{r_1}}\left(\sqrt{\tfrac{2r_2}{r_1+r_2}}-1\right)$, $\Delta V_2 = \sqrt{\tfrac{\mu}{r_2}}\left(1-\sqrt{\tfrac{2r_1}{r_1+r_2}}\right)$ |
| Small boost | $\Delta V\approx V\Delta r/2r$ |
| Non-tangential | $\Delta V = \sqrt{V_1^2+V_2^2-2V_1V_2\cos\Delta\gamma}$ |

## Propulsion ([[SESA2024 07 - Spacecraft Propulsion|Ch 7]])
| | |
|---|---|
| Thrust | $T = \sigma V_e+(P_e-P_a)A_e = \sigma V_{ex}$ |
| Specific impulse | $I_{sp} = V_{ex}/g_0 = I/(M_eg_0)$, $I = \int T\,dt = V_{ex}M_e$ |
| **Rocket equation** | $\Delta V = V_{ex}\ln(M_0/M_b)$, $M_e = M_0(1-e^{-\Delta V/V_{ex}})$ |
| Burn time | $t_b = M_e/\sigma = M_eg_0I_{sp}/T$ |
| Launcher | $\Delta V = \Delta V_{ideal}-\Delta V_g-\Delta V_D$ |
| EP | $W = \sigma V_{ex}^2/2\eta = TV_{ex}/2\eta$; $\beta = W/M_W$; $V_c = \sqrt{2\eta\beta t_b}$ |
| EP masses | $M_e = \dfrac{M_0-M_p}{1+(V_{ex}/V_c)^2}$, $M_W = (V_{ex}/V_c)^2M_e$ |
| EP ΔV | $\dfrac{\Delta V}{V_c} = x\ln\dfrac{1+x^2}{M_p/M_0+x^2}$, $x = V_{ex}/V_c$; optimum ≈ 0.63–0.65 for $M_p/M_0$ = 0.1 |

## Attitude ([[SESA2024 06 - Attitude Control|Ch 6]])
- $\mathbf H = [\mathbf I]\boldsymbol\omega$
- $d\mathbf H/dt = \sum\mathbf T_{ext}$
- $I_{xx} = \int(y^2+z^2)dm$, $I_{xy} = \int xy\,dm$
- Precession $\dot\psi = T/H_0$

## Power ([[SESA2024 08 - Electrical Power Subsystem|Ch 8]])
| | |
|---|---|
| Eclipse (worst case) | $t_e = \dfrac{180^\circ-2\cos^{-1}(R_E/a)}{360^\circ}\tau$, $t_s = \tau-t_e$ |
| No-eclipse test | $R_0 = a\sin\beta_{Sun} > R_E$ |
| Battery | $C = \dfrac{Pt_e}{\text{DoD}\,V_B}$, $\mathcal E = CV_B$, $M = \mathcal E/\bar\varepsilon$ |
| Charging | $R = \dfrac{\text{DoD}\,C}{t_s}$, $P_{EOL} = P+RV_A$ |
| Array | $A = \dfrac{P_{EOL}}{S\cos\theta\,\eta\,\eta_p(1-D_0)}$ |

## Communications ([[SESA2024 09 - Communications|Ch 9]])
| | |
|---|---|
| dB | $10\log_{10}(P_2/P_1)$ |
| Gain, beamwidth | $G = \eta(\pi D/\lambda)^2$, $\theta_{3dB} = 72\lambda/D$ (deg) |
| Global coverage | $\theta_{3dB} = 2\sin^{-1}(R_E/r)$ (GEO: 17.4°) |
| **Link budget** | $\dfrac{C}{N_0} = EIRP+\dfrac{G_R}{T_R}-20\log\dfrac{4\pi\rho}{\lambda}-L_A-10\log k$ |
| Link quality | $\dfrac{C}{N_0} = \dfrac{E_b}{N_0}+10\log R_b$ (BER 10⁻⁶ PSK ≈ 10.5 dB) |
| Noise, Shannon | $N = kTB$, $R_{max} = B\log_2(1+S/N)$ |
| PCM | $f_s\ge2f_{max}$, $R_b = nf_s$ |

## Thermal ([[SESA2024 10 - Thermal Control|Ch 10]])
$$q_S\alpha_SA_S^{proj}+aq_S\alpha_SA_E^{proj}\cos\phi\,\beta F+q_E\varepsilon A_E^{proj}F+P = \varepsilon\sigma T^4A_{surf},\qquad F = (R_E/R_{orb})^2$$

- Wien: $\lambda_{max}T = 2.898\times10^{-3}$ m K
- Stefan–Boltzmann: $q = \varepsilon\sigma T^4$
- Sunlit and dominated by the Sun: $T\propto(\alpha_S/\varepsilon)^{1/4}$
- Eclipse with $P = 0$: $\varepsilon$ cancels
- Decoupled plate: output $= \sigma T^4(\varepsilon_f+\varepsilon_b)A$

## Remote sensing ([[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission|Ch 11]])
| | |
|---|---|
| **SSO** | $\dot\Omega = -2.0647\times10^{14}a^{-3.5}\cos i = 0.986^\circ$/day ($a$ in km) |
| **Repeat** | $\tau = \dfrac{m}{n}86\,400$ s; $n = 2\pi R_E/d$; $m = n\tau/86400$ |
| Swath | $d = 2h\tan(\beta/2) = N_{px}\,p$ |
| Track shift | $\Delta\lambda = 360^\circ(\tau/\tau_E-\tau/\tau_Y)$ per orbit (West) |
| LST ↔ RAAN | $\phi = \alpha_S-\Omega$; 15° = 1 h; the nodes are 12 h apart |
| Drag | $\delta a = -2\pi\rho\dfrac{SC_D}{m}a^2$, $\delta\tau = \dfrac{3\pi}{V}\delta a$ |
| Control | $\delta\lambda = \dfrac{2E_0}{R_E}\dfrac{180}{\pi}$, $\Delta t_0 = \delta\lambda/\omega_E$ ($\omega_E$ = 0.004178°/s), $k = \sqrt{2\Delta t_0/\lvert\delta\tau\rvert}$, cycle $2k\tau$, $\Delta a = 2k\lvert\delta a\rvert$ |
| Data rate | $V_{gd} = V\,R_E/a$, $t_s = p/V_{gd}$, $R_b = N_{px}\cdot\text{bits}\cdot\text{bands}/t_s$ |

## Links
- [[SESA2024 Astronautics Hub]] · [[SESA2024 Past Paper Trend Analysis]]

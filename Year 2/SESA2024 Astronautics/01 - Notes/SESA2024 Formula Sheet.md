---
title: "SESA2024 Formula Sheet"
module: "SESA2024 Astronautics"
type: formula
aliases: ["SESA2024 formulae", "Astronautics formula sheet"]
tags: [sesa2024, formula-sheet, revision]
status: lectured
coverage: "Topic notes 01–15; notes 14 (orbit control, drag, data rate) and 15 (debris, NewSpace) are written-ahead from the workbook, slides and past papers"
sources: ["01 - Notes/Topics", "01 - Notes/Tutorials", "02 - Sources/Lectures", "03 - Exams & Past Papers"]
---

# SESA2024 Formula Sheet

One section per topic note, in note order; each heading links to its note. Notes 14 and 15 are `written-ahead` (not lectured in 2025-26, or not recorded), so their sections rest on the workbook and the past papers.

> [!info] Constants and given equations
> - $R_E=6378$ km; $\mu_E=398\,600\ \mathrm{km^3/s^2}=3.986\times10^{14}\ \mathrm{m^3/s^2}$; $g_0=9.81\ \mathrm{m/s^2}$; $J_2=1.0826\times10^{-3}$
> - $r_{GEO}=42\,164$ km $=6.611R_E$; sidereal day $T_{sid}=86\,164$ s; solar day 86 400 s; year $T_{yr}=365.25$ d $=3.1558\times10^7$ s; $\omega_E=360^\circ/86\,164\ \mathrm s=0.004178^\circ$/s
> - $\mu_{Sun}=1.327\times10^{11}\ \mathrm{km^3/s^2}$; 1 AU $=1.496\times10^8$ km
> - $k=1.38\times10^{-23}$ J/K ($10\log k=-228.6$ dB); $c=3\times10^8$ m/s; $\sigma=5.67\times10^{-8}\ \mathrm{W\,m^{-2}\,K^{-4}}$
> - $Q_S\approx1350\text{–}1400\ \mathrm{W/m^2}$ at 1 AU; $Q_E=240\ \mathrm{W/m^2}$; albedo $a=0.34$
>
> Recent papers give the energy equation, the rocket equation, the ellipse equation and sometimes the drag $\delta a$. Everything else must be known.

## 01 Systems engineering ([[SESA2024 01 - Systems Engineering and Spacecraft Design|note 01]])

No formulae to learn; the exam asks for the method and the phases.

| | |
|---|---|
| Design steps | mission objectives (customer) → payload definition → top-level requirements (TLRs) → design requirements (DRs, per subsystem) |
| ECSS phases (ECSS-E-ST-10C) | 0 mission analysis / need identification, A feasibility, B preliminary definition (to PDR), C detailed definition, D qualification and production, E operations / utilisation, F disposal |
| Sun distance | $S\propto1/d^2$: at Jupiter (5.2 AU) an array gives $1/5.2^2=0.037$ of its 1 AU power |

## 02 Kepler's laws and the orbit equation ([[SESA2024 02 - Kepler's Laws and the Orbit Equation|note 02]])

Two-body, $\mu=GM$ of the central body only; $r$ measured from the centre of the central body.

| | |
|---|---|
| Kepler's laws | 1 ellipse with the central body at a focus; 2 equal areas in equal times; 3 $\tau^2\propto a^3$ |
| Polar acceleration | $a_r=\ddot r-r\dot\theta^2$, $a_\theta=2\dot r\dot\theta+r\ddot\theta$ (rotating radial and transverse axes) |
| Angular momentum | $h=r^2\dot\theta=\text{constant}$; $h=rV\cos\gamma$ ($\gamma$ = flight-path angle from the local horizontal); $r_pV_p=r_aV_a$ |
| Orbit equation | $\dfrac{d^2u}{d\theta^2}+u=\dfrac{\mu}{h^2}$ with $u=1/r$, so $r=\dfrac{h^2/\mu}{1+e\cos\theta}$ |
| Ellipse (given) | $r=\dfrac{a(1-e^2)}{1+e\cos\theta}$, $\theta$ the true anomaly from periapsis |
| Semi-latus rectum | $p=a(1-e^2)=h^2/\mu$, so $h=\sqrt{\mu a(1-e^2)}$ |
| Second law | $\dot A=\tfrac12r^2\dot\theta=\tfrac12h$ |
| Third law | $\tau=2\pi\sqrt{a^3/\mu}$, $a=\left[\mu(\tau/2\pi)^2\right]^{1/3}$; same body: $a_2/a_1=(\tau_2/\tau_1)^{2/3}$ |
| Mean motion | $n=2\pi/\tau=\sqrt{\mu/a^3}$ (constant; $\dot\theta=h/r^2$ is not, unless $e=0$) |
| Circular orbit | $V_c=\sqrt{\mu/r}$, $\tau=2\pi r/V_c$; GEO from $\tau=T_{sid}$: $r=42\,164$ km, 3.075 km/s |

## 03 Orbital elements and conic sections ([[SESA2024 03 - Orbital Elements and Conic Sections|note 03]])

| | |
|---|---|
| Size and shape | $a=\tfrac12(r_p+r_a)$, $e=\dfrac{r_a-r_p}{r_a+r_p}$, $r_p=a(1-e)$, $r_a=a(1+e)$; altitude $=r-R_E$ |
| Orientation | $i$ orbit plane to equator at the ascending node (prograde $<90^\circ$, retrograde $>90^\circ$); $\Omega$ from the First Point of Aries to the ascending node, eastwards in the equatorial plane; $\omega$ from the ascending node to periapsis, in the orbit plane and the direction of motion |
| Undefined elements | $\Omega$ when $i=0$; $\omega$ (and $\theta$ from periapsis) when $e=0$ |
| True anomaly from $r$ | $\cos\theta=\dfrac1e\left[\dfrac{a(1-e^2)}{r}-1\right]$, two answers $\theta$ and $360^\circ-\theta$ (outbound and inbound) |
| Conics | $e=0$ circle ($a=r$); $0<e<1$ ellipse ($a>0$); $e=1$ parabola ($a\to\infty$); $e>1$ hyperbola ($a<0$, $r_p=a(1-e)>0$, asymptote at $\cos\theta=-1/e$) |
| Launch azimuth | direct launch needs latitude $\lvert L\rvert\le i$ (prograde) or $\le180^\circ-i$ (retrograde); azimuth from north $\sin Az=\cos i/\cos L$ (2014/15 Q4) |
| Operational orbits | LEO equatorial, LEO about 50°, LEO near-polar or SSO 500–900 km, HEO (Molniya $i=63.4^\circ$, $\omega=270^\circ$), semi-synchronous ($\tau\approx12$ h, $a\approx26\,560$ km), GEO |

## 04 Orbital energy and vis-viva ([[SESA2024 04 - Orbital Energy and the Vis-Viva Equation|note 04]])

Two-body, no drag or thrust between the two points; valid for every conic.

| | |
|---|---|
| Specific energy | $\varepsilon=\dfrac{V^2}{2}-\dfrac{\mu}{r}=-\dfrac{\mu}{2a}$ (potential zero at infinity; $\varepsilon<0$ bound, $>0$ hyperbolic) |
| Vis-viva (given) | $V=\sqrt{\mu\left(\dfrac2r-\dfrac1a\right)}$ |
| $a$ from one state | $\dfrac1a=\dfrac2r-\dfrac{V^2}{\mu}$; then $r_p+r_a=2a$, $e=r_a/a-1=1-r_p/a$ |
| Escape | $V_{esc}=\sqrt{2\mu/r}=\sqrt2\,V_c$ (11.01 km/s at 200 km) |
| Apsis speeds | $V_p=\sqrt{\dfrac{\mu}{a}\dfrac{1+e}{1-e}}=\sqrt{\dfrac{2\mu r_a}{r_p(r_p+r_a)}}$, $V_a=\sqrt{\dfrac{2\mu r_p}{r_a(r_p+r_a)}}$ |
| Flight-path angle | $\cos\gamma=\dfrac{h}{rV}$, $h=\sqrt{\mu a(1-e^2)}$; $\gamma=0$ at the apses |
| Satellite or missile? | at apogee, $V<V_c$ means perigee below; $r_p<R_E$ means suborbital |

## 05 Transfers and plane changes ([[SESA2024 05 - Orbital Transfers and the Hohmann Transfer|note 05]])

Impulsive burns (position unchanged), along the velocity at the apses (no gravity loss); Hohmann between coplanar circles.

| | |
|---|---|
| Hohmann | $a_T=\tfrac12(r_1+r_2)$; $\Delta V_{Tp}=V_{Tp}-V_1$, $\Delta V_{Ta}=V_2-V_{Ta}$; time $t_T=\pi\sqrt{a_T^3/\mu}$ (half the transfer period) |
| Closed form | $\Delta V_{Tp}=\sqrt{\dfrac{\mu}{r_1}}\left(\sqrt{\dfrac{2r_2}{r_1+r_2}}-1\right)$, $\Delta V_{Ta}=\sqrt{\dfrac{\mu}{r_2}}\left(1-\sqrt{\dfrac{2r_1}{r_1+r_2}}\right)$ |
| One variable | $\dfrac{\Delta V}{V_1}=\left(\dfrac{2}{1+x}\right)^{1/2}(1-x)+x^{1/2}-1$, $x=r_1/r_2$; maximum $0.536$ at $r_2/r_1=15.58$; 200 km to GEO: 3.932 km/s, 5.26 h |
| Small tangential burn | circular orbit: $\delta a=\dfrac{2a}{V}\delta V$; $\delta\tau=\tfrac32\tau\dfrac{\delta a}{a}$; opposite apsis moves $2\delta a$; along-track drift $3\lvert\delta V\rvert\tau$ per orbit (forward burn: higher, slower, falls behind) |
| Small Hohmann boost | between nearby circles $\Delta a$ apart: $\Delta V\approx\dfrac{V\,\Delta a}{2a}$ (two burns of $V\Delta a/4a$) |
| Burn at a common point | $\Delta V=\sqrt{V_1^2+V_2^2-2V_1V_2\cos(\gamma_2-\gamma_1)}$, $\gamma$ from the local horizontal (2022/23 B1) |
| Plane change | same cosine rule with the angle $\Delta i$ between the planes at the node and $V_1=V_2=V$: $\Delta V=2V\sin(\Delta i/2)\approx V\Delta i$ ($\Delta i$ in rad); expensive, hence $J_2$ in note 12 |
| Propellant | $m_0/m_f=e^{\Delta V/V_{ex}}$, fraction $1-m_f/m_0$ (note 07) |
| Kinetic impactor | perfectly inelastic: $\Delta V_A=\dfrac{m_{sc}V_{rel}}{m_A+m_{sc}}$ (2024/25 B1) |

## 06 Attitude control ([[SESA2024 06 - Attitude Control|note 06]])

Rigid body; momenta and torques about the centre of mass.

$$
[\mathbf I]=\begin{bmatrix}I_{xx}&-I_{xy}&-I_{xz}\\-I_{xy}&I_{yy}&-I_{yz}\\-I_{xz}&-I_{yz}&I_{zz}\end{bmatrix},
\qquad
I_{xx}=\int(y^2+z^2)\,dm,
\qquad
I_{xy}=\int xy\,dm
$$

| | |
|---|---|
| Dynamics | $\mathbf H=[\mathbf I]\boldsymbol\omega$, $\dfrac{d\mathbf H}{dt}=\sum\mathbf T_{ext}$; internal torques move $\mathbf H$ between parts, never change the total |
| Components | $H_x=I_{xx}\omega_x-I_{xy}\omega_y-I_{xz}\omega_z$ (and cyclic); $\mathbf H\parallel\boldsymbol\omega$ only about a principal axis |
| Spinner test | products of inertia zero, $I_{zz}$ the largest, $I_{xx}=I_{yy}$; otherwise three-axis |
| Precession | $\tan\psi=\dfrac{T\,\Delta t}{H_0}\approx\psi$ (rad, $\mathbf T\perp\mathbf H_0$, small angle); rate $\dot\psi=T/H_0$; $\lvert\mathbf H\rvert$ changes only to second order |
| Momentum bias | $H=I\omega$; larger $H$ gives a smaller $\psi$ for the same impulse (gyroscopic rigidity) |
| Torques | thrust misalignment $T=Fd$ (1 kN at 1 mm gives 1 N m); magnetorquer $\mathbf T=\mathbf m\times\mathbf B$ (none about the field line) |
| Earth-pointing on an ellipse | pitch rate $\dot\theta=h/r^2$; wheel absorbs $\Delta H=I(\dot\theta_p-\dot\theta_a)$ per half orbit, periodic, no dumping |
| Stabilisation types | spinner, dual spinner, hybrid (momentum-bias wheel), three-axis (zero bias); secular momentum must be dumped by an external torquer |

## 07 Propulsion ([[SESA2024 07 - Spacecraft Propulsion|note 07]])

$V_{ex}$ is the effective exhaust velocity (pressure thrust lumped in); no gravity or drag losses unless stated.

| | |
|---|---|
| Thrust | $T=\dot mV_{ex}+(p_e-p_a)A_e$; vacuum or ideal expansion: $T=\dot mV_{ex}$ ($\dot m$ is also written $\sigma$) |
| Total impulse | $I=\int_0^{t_b}T\,dt=M_eV_{ex}$, $M_e$ the propellant (expellant) mass |
| Specific impulse | $I_{sp}=\dfrac{I}{M_eg_0}=\dfrac{V_{ex}}{g_0}=\dfrac{T}{\dot mg_0}$, in s (per unit weight, not mass) |
| Rocket equation (given) | $\Delta V=V_{ex}\ln\dfrac{M_0}{M_b}=g_0I_{sp}\ln\dfrac{M_0}{M_0-M_e}$ |
| Propellant | $\dfrac{M_e}{M_0}=1-e^{-\Delta V/V_{ex}}$; burn time $t_b=M_e/\dot m=M_eg_0I_{sp}/T$ |
| Launcher | $\Delta V=V_{ex}\ln(M_0/M_b)-\Delta V_g-\Delta V_D$, $\Delta V_g=\int g\sin\gamma\,dt$, $\Delta V_D=\int (D/M)\,dt$ (2014/15) |
| EP power | $W=\dfrac{TV_{ex}}{2\eta}=\dfrac{Tg_0I_{sp}}{2\eta}$; at fixed thrust, power $\propto I_{sp}$ |
| EP sizing | $M_0=M_e+M_W+M_p$; $\beta=W/M_W$; constant $\dot m=M_e/t_b$; $V_c=\sqrt{2\eta\beta t_b}$; $x=V_{ex}/V_c$, $p=M_p/M_0$ |
| EP masses | $M_e=\dfrac{M_0-M_p}{1+x^2}$, $M_W=x^2M_e=\dfrac{x^2(M_0-M_p)}{1+x^2}$ |
| EP ΔV | $\dfrac{\Delta V}{V_c}=x\ln\dfrac{1+x^2}{x^2+p}$ |
| EP optimum | $\ln\dfrac{1+x^2}{x^2+p}=\dfrac{2x^2(1-p)}{(1+x^2)(x^2+p)}$, solved numerically: |

| $p=M_p/M_0$ | optimum $x=V_{ex}/V_c$ | peak $\Delta V/V_c$ |
|---|---|---|
| 0.1 | 0.633 | 0.651 |
| 0.25 | 0.737 | 0.491 |
| 0.5 | 0.849 | 0.291 |

## 08 Power ([[SESA2024 08 - Electrical Power Subsystem|note 08]])

Circular orbit, Sun in the orbit plane (worst case), cylindrical shadow; constant load; array sized at end of life (EOL).

| | |
|---|---|
| Eclipse angle | $\cos\alpha=\dfrac{R_E}{R_E+h}$, $\alpha$ from the terminator; shadow arc $180^\circ-2\alpha$ |
| Eclipse time | $t_e=\tau\,\dfrac{180^\circ-2\alpha}{360^\circ}$, $t_s=\tau-t_e$; minimum about 35 min near 1400 km, about 69 min at GEO |
| No-eclipse test | $r\sin\beta_S>R_E$, $\beta_S$ the Sun's angle to the orbit plane, $r$ the orbit radius |
| Cells | $\eta=P_{out}/(1370A)$; $P(\theta)\approx P(0)\cos\theta$; Si loses 0.44 %/°C, GaAs 0.16 %/°C |
| Cycles | lifetime$/\tau$, then DoD from the cycle-life curve |
| Battery | $N_c=V_{bus}/V_c$ (whole number), $V_B=N_cV_c$; $C=\dfrac{P_{EOL}t_e}{\mathrm{DoD}\,V_B}$ (A h with $t_e$ in h); $E=CV_B$; $M_{battery}=E/\varepsilon$ ($\varepsilon$ in W h/kg at 100 % discharge) |
| Charging | $R=\dfrac{\mathrm{DoD}\,C}{t_s}$; $V_A\approx1.2V_B$; $P_{array}=P_{load}+RV_A$ |
| Array area | $A_{SA}=\dfrac{P_{array}}{S\cos\theta\;\eta\;\eta_p(1-D)}$, $\theta$ worst off-Sun angle, $\eta_p$ packing, $D$ radiation degradation at EOL |
| Solar flux | $S=1370/d^2\ \mathrm{W/m^2}$, $d$ in AU |

## 09 Communications ([[SESA2024 09 - Communications|note 09]])

Circular parabolic dishes ($\eta=0.65$ unless given); free space over the slant range $\rho$; downlink.

| | |
|---|---|
| Decibels | $x_{dB}=10\log_{10}(P/P_{ref})$, $P=P_{ref}10^{x_{dB}/10}$; dBW for $P_{ref}=1$ W; ×2 is 3.01 dB, ×10 is 10 dB |
| Wavelength | $\lambda=c/f$; usable window about 0.1–30 GHz |
| PCM | $f_s\ge2f_{max}$ (Nyquist), $2^n$ levels, $R_b=nf_s$ (64 kbit/s for 4 kHz speech at 8 bits) |
| Shannon | maximum rate $B\log_2(1+S/N)$ |
| Noise | $N=kTB$, $N_0=kT$ |
| Gain, beamwidth | $G=\eta\left(\dfrac{\pi D}{\lambda}\right)^2=\dfrac{4\pi A_{eff}}{\lambda^2}$, $A_{eff}=\eta\pi D^2/4$; $\theta_{3dB}=72\lambda/D$ degrees |
| Global coverage | $\theta_{3dB}=2\sin^{-1}(R_E/r)$ (GEO: 17.4°) |
| Received power | $P_R=\dfrac{P_TG_TG_R}{L_{FS}}$, $L_{FS}=(4\pi\rho/\lambda)^2$ |
| Link budget (dB) | $\dfrac{C}{N_0}=\mathrm{EIRP}+\dfrac{G_R}{T_R}-20\log\dfrac{4\pi\rho}{\lambda}-L_a+228.6$, with $\mathrm{EIRP}=10\log(P_TG_T)$ dBW |
| Unit trap | $\rho$ and $\lambda$ in the same unit: km against m shifts the free-space loss by exactly 60 dB |
| Bit rate | $\dfrac{C}{N_0}=\dfrac{E_b}{N_0}+10\log R_b$ (dB); BER $10^{-6}$ needs about 10 dB on the course PSK curve (10.5 dB ideal BPSK) |
| Downlink time | data volume $/R_b$ |

## 10 Thermal control ([[SESA2024 10 - Thermal Control|note 10]])

Steady state at one point in the orbit; uniform temperature; Earth infrared absorbed with $\alpha_{IR}=\varepsilon$ (Kirchhoff, both near 290 K); temperatures in K.

| | |
|---|---|
| Surface | $\alpha+\rho+\tau=1$, opaque $\alpha+\rho=1$; $\alpha_S$ is the absorptance averaged over the solar spectrum |
| Wien | $\lambda_{max}T=2898\ \mu\mathrm m\,\mathrm K$ (Earth peaks near 10 μm, about 290 K) |
| Emission | $Q_{BB}=\sigma T^4$, $Q=\varepsilon\sigma T^4$ |
| Height factor | $F=\left(\dfrac{R_E}{R_E+h}\right)^2$; albedo factor $\cos\phi$ ($\phi$ between Earth–Sun and Earth–spacecraft lines), switch $\beta=0$ over the night side |
| Thermal balance | $\alpha_SQ_SA_S+\alpha_SQ_SA_a\,a\,F\cos\phi\,\beta+\varepsilon Q_EA_EF+P=\varepsilon\sigma A_{surf}T^4$ |
| Areas | $A_S$, $A_a$, $A_E$ projected towards the Sun and the Earth; $A_{surf}$ the whole radiating surface |
| Sunlit, Sun dominant | $T=\left(\dfrac{\alpha_S}{\varepsilon}\dfrac{Q_SA_S}{\sigma A_{surf}}\right)^{1/4}\propto(\alpha_S/\varepsilon)^{1/4}$ |
| Eclipse, $P=0$ | $T=\left(\dfrac{Q_EA_EF}{\sigma A_{surf}}\right)^{1/4}$, independent of $\varepsilon$ |
| Mixed finish | area-weighted $\alpha_S$ and $\varepsilon$, e.g. $0.9\alpha_{S1}+0.1\alpha_{S2}$ |
| Two-sided plate | front and back radiate: output $\sigma T^4(\varepsilon_f+\varepsilon_b)A$ (2020/21, 2022/23) |
| Eclipse check | $r\sin\beta_S<R_E$ means the far side of the orbit is in shadow |

## 11 Payload and orbit selection ([[SESA2024 11 - Payload and Orbit Selection|note 11]])

| | |
|---|---|
| Swath | $d=2h\tan(\beta/2)$, nadir pointing, ground flat across the swath; $\beta$ the field of view |
| Maximum latitude | $i$ for $i\le90^\circ$, $180^\circ-i$ for retrograde ($98^\circ$ SSO: $82^\circ$) |
| First pass, 10 m imager | near-polar, $e\approx0$, $h=700\text{–}900$ km ($a=7078\text{–}7278$ km, $\tau\approx6050\pm120$ s) |
| Operational needs | sunlit target at a moderate Sun angle, invariant illumination (Sun-synchronous), repeating geometry (Earth-synchronous) |

## 12 Sun- and Earth-synchronous orbits ([[SESA2024 12 - Sun- and Earth-Synchronous Orbits|note 12]])

Circular orbit; $J_2$ only. $N$ orbits in $M$ days (also written $n$ orbits, $m$ days), integers with no common factor.

| | |
|---|---|
| Sun-synchronism | $\phi=\alpha_S-\Omega=$ constant, so $\dot\Omega=\dot\alpha_S=360^\circ/365.25\ \mathrm d=0.9856^\circ$/day eastwards |
| $J_2$ regression | $\dot\Omega=-\tfrac32J_2\sqrt\mu\,R_E^2\,a^{-7/2}\cos i=-\tfrac32nJ_2(R_E/a)^2\cos i$ (rad/s, consistent units) |
| Exam form | $\dot\Omega=-2.0647\times10^{14}\,a^{-7/2}\cos i$ in deg/day with $a$ in km |
| SSO inclination | $\cos i=\dfrac{0.9856}{-2.0647\times10^{14}a^{-3.5}}$, so $i>90^\circ$ (98.2°–99.0° for 700–900 km) |
| Sign of $\dot\Omega$ | $i<90^\circ$ westward; $i=90^\circ$ none; $i>90^\circ$ eastward |
| Track shift per orbit | $\Delta\lambda=360^\circ\,\tau\left(\dfrac{1}{T_{sid}}-\dfrac{1}{T_{yr}}\right)$ westwards (rotation less SSO regression) |
| Repeat condition | $N\Delta\lambda=M\times360^\circ$ |
| Sun- and Earth-synchronous | $\tau=\dfrac MN\cdot\dfrac{1}{1/T_{sid}-1/T_{yr}}=\dfrac MN\times86\,400$ s (solar day, not sidereal); other planets: use that planet's $T_{sid}$ and $T_{yr}$ (2021/22 Mars, 2023/24 Jupiter) |

## 13 Orbital elements for a remote-sensing mission ([[SESA2024 13 - Calculating Orbital Elements for a Remote Sensing Mission|note 13]])

Circular, Sun- and Earth-synchronous, nadir imager; swaths just touching at the equator.

| | |
|---|---|
| Track spacing | $s(\lambda)\approx\dfrac{2\pi R_E\cos\lambda}{N}$, largest at the equator, so coverage is checked there |
| Coverage | $N=\mathrm{int}\left(\dfrac{2\pi R_E}{2h\tan(\beta/2)}\right)$, $M=\mathrm{int}\left(\dfrac{N\tau}{86\,400}\right)$ |
| Iteration | guess $h$ → $d$, $\tau$ → $N$, $M$ (coprime) → $\tau=(M/N)86\,400$ → if outside range step $N$ (or $M$) → $a$, $h$, $i$ → recheck the swath at the new $h$ |
| Common factor | $(98,7)$ is $(14,1)$: 14 distinct tracks, 2862 km apart |
| LST and RAAN | $\Omega=\alpha_S-\phi$ at launch; $\phi=15^\circ(12-t)$ for a node at $t$ hours LST; $15^\circ=1$ h; the two nodes are 12 h apart |
| Eclipse by LST | noon–midnight about half the orbit; dawn–dusk nearly none (15–20 min in northern winter); 10:30 about a third |
| $e$, $\omega$ | $e\approx0$; $\omega$ undefined, so arbitrary |

## 14 Orbit control, drag and data rate ([[SESA2024 14 - Orbit Control, Drag and Payload Data Rate|note 14]], written-ahead)

Circular orbit; constant density over a cycle (high solar activity value); small decay per orbit; Hohmann boosts; SI units in the drag formula.

| | |
|---|---|
| Drag decay (sometimes given) | $\delta a=-2\pi\rho\dfrac{SC_D}{m}a^2$ per orbit |
| Period change | $\delta\tau=\dfrac{3\pi}{V}\delta a$ per orbit; the spacecraft speeds up as $a$ falls |
| Tolerance window | $\pm E_0$ at the equator: $\delta\lambda=\dfrac{2E_0}{R_E}$ rad $=\dfrac{2E_0}{R_E}\dfrac{180}{\pi}$ deg; $\Delta t_0=\delta\lambda/\omega_E$ |
| Control cycle | $k=\sqrt{\dfrac{2\Delta t_0}{\lvert\delta\tau\rvert}}$ (round down); cycle $2k$ orbits $=2k\tau$; height lost $\Delta a=2k\lvert\delta a\rvert$ |
| Boost per cycle | $\Delta V_{cycle}\approx\dfrac{V\,\Delta a}{2a}$; life total $N_{cycles}\Delta V_{cycle}$; propellant from the rocket equation |
| Drag sail | $\delta a\propto S$: nine times the area, nine times the decay rate |
| ΔV budget | orbit acquisition, drag make-up, inclination (LST) maintenance, end-of-life disposal |
| Ground speed | $V_{gd}=V\dfrac{R_E}{a}$ (Earth rotation ignored) |
| Line time | $t_s=p/V_{gd}$, $p$ the ground pixel |
| Data rate | $R_b=\dfrac{N_{pix}\times b\times N_{bands}}{t_s}$; detector $d=N_{pix}p$, $\beta=2\tan^{-1}(d/2h)$ |

## 15 Debris and NewSpace ([[SESA2024 15 - Space Sustainability, Debris and NewSpace|note 15]], written-ahead)

| | |
|---|---|
| Disposal burn | one retrograde burn at $r_0$ (which becomes apogee) to perigee $r_p$: $\Delta V=\sqrt{\dfrac{\mu}{r_0}}-\sqrt{\mu\left(\dfrac{2}{r_0}-\dfrac{2}{r_0+r_p}\right)}$ |
| Fragment cloud | same break-up point, different $\Delta V$: forward kick raises the far side, lengthens $\tau$ and falls behind; backward kick lowers it, shortens $\tau$ and moves ahead |
| Rules | IADC four measures; UN seven guidelines; post-mission disposal within 25 years (FCC: 5 years in LEO); GEO to a graveyard orbit |

## Links
- [[SESA2024 Astronautics Hub]] · [[SESA2024 Past Paper Trend Analysis]]

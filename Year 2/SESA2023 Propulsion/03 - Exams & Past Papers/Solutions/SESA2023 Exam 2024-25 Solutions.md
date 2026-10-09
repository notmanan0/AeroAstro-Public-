---
title: "SESA2023 Exam 2024-25 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2024-25"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W03 - Compressible Flow, Normal Shocks and Nozzles]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W08 - Turbomachinery Principles - Euler Equation and Velocity Triangles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-202425-02-SESA2023.pdf"]
---

# SESA2023 Exam 2024-25 Solutions

> [!info] Paper
> Answer all four questions, 25 marks each. The Thermofluids Data Book is provided. This is **the most recent paper and the best model for the current exam**.

## Q1: Ramjet at 15 km, M 2

### (i) Diffuser and combustor states, and fuel-air ratio (8)
- **Ambient** (Data Book Table 25, 15 km): $T_a = 0.7519(288.15) = 216.7$ K and $p_a = 0.1195(101.325) = 12.11$ kPa.
- **Flight**: $V = 2\sqrt{1.4(287)(216.7)} = 590.1$ m/s.
- **Diffuser** (ideal, $\Gamma_d = 1$; adiabatic):

$$
T_{02} = T_{01} = 216.7(1.8) = \boxed{390.0\text{ K}},\qquad p_{02} = p_{01} = 12.11(1.8)^{3.5} = \boxed{94.74\text{ kPa}}
$$

- **Combustor** ($\Gamma_c = 1$): $\boxed{T_{03} = 1800\text{ K}}$ and $\boxed{p_{03} = 94.74\text{ kPa}}$.
- **Fuel-air ratio** (SFEE, 298 K reference):

$$
f = \frac{T_{03}-T_{02}}{LCV/c_p-(T_{03}-298)} = \frac{1410.0}{43{,}284-1502} = \boxed{0.0337}
$$

(0.0340 without the reference-temperature term.)

### (ii) Specific thrust and efficiencies with $\Gamma_n = 0.98$ (8)
$p_{04} = 0.98(94.74) = 92.85$ kPa, fully expanded to 12.11 kPa ($p_{04}/p_a = 7.67$):

$$
T_4 = 1800(7.67)^{-0.2857} = 1005.8\text{ K},\qquad V_e = \sqrt{2(1005)(1800-1005.8)} = 1263.5\text{ m/s}\quad(M_e = 1.99)
$$

$$
\frac{F}{\dot m_a} = (1+f)V_e-V = 1.0337(1263.5)-590.1 = \boxed{716\text{ N s/kg}}
$$

| Efficiency | Working | Value |
|---|---|---|
| Propulsive $\eta_P = \dfrac{(F/\dot m)V}{\tfrac12[(1+f)V_e^2-V^2]}$ | $\dfrac{716.0(590.1)}{0.5[1.0337(1263.5^2)-590.1^2]}$ | **0.649** |
| Thermal $\eta_{th} = \dfrac{\tfrac12[(1+f)V_e^2-V^2]}{f\,LCV}$ | $\dfrac{651{,}000}{0.03375(43.5\times10^6)}$ | **0.443** |
| Overall $\eta_O = \eta_P\eta_{th}$ | $\dfrac{716.0(590.1)}{0.03375(43.5\times10^6)}$ | **0.288** |

The 2 % nozzle loss costs only 4 N s/kg (720 ideal). The low $\eta_{th}$ reflects the weak ram compression at M 2 ($p_{01}/p_a = 7.8$). See [[Thermal and Overall Efficiency]].

### (iii) C–D nozzle behaviour as $p_a/p_0$ falls (5)
See [[SESA2023 Exam 2020-21 Solutions]] Q1(i) and [[Converging-Diverging Nozzle Operating Regimes]]:
1. subsonic venturi flow (unchoked);
2. choked, with subsonic diffusion after the throat;
3. a normal shock in the divergent section, moving towards the exit;
4. a shock at the exit;
5. over-expanded (oblique shocks outside);
6. design (fully expanded);
7. under-expanded (expansion fans).

Once the throat is choked, $\dot m$ is fixed.

![[prop_cd_nozzle_regimes.png|640]]

### (iv) Mach number across a normal shock (4)
Upstream $M_1>1$ always, and downstream $M_2<1$. $M_2$ falls monotonically with $M_1$:

$$
M_2^2 = \frac{1+\frac{\gamma-1}2M_1^2}{\gamma M_1^2-\frac{\gamma-1}2}
$$

- $M_2 = 1$ at $M_1 = 1$ (a vanishingly weak wave).
- $M_2\to\sqrt{(\gamma-1)/2\gamma} = 0.378$ as $M_1\to\infty$.

Across the shock $p$, $\rho$ and $T$ rise, $T_0$ is constant, and $p_0$ falls.

![[prop_normal_shock.png|640]]

---

## Q2: Rocket performance

### (i) Tsiolkovsky derivation (6)
Assume a fully expanded nozzle, so $F = \dot mc$ with $c = V_e$ constant, and free space (no gravity or drag).
1. In time $dt$, the rocket of mass $m$ ejects $dm_p = -dm$ at velocity $c$ relative to itself.
2. Momentum conservation, or Newton's second law with $F = \dot mc = -c\,dm/dt$: $m\,dV = -c\,dm$.
3. Integrate from $m_0$ to the burn-out mass $m_{bo}$:

$$
\Delta V = c\ln\frac{m_0}{m_{bo}} = g_0I_{sp}\ln\frac{m_0}{m_{bo}}\;\blacksquare
$$

See [[Tsiolkovsky Rocket Equation]].

### (ii) Single-stage propellant mass (6)
$c = 450(9.81) = 4414.5$ m/s, $\Delta V = 5000$ m/s, $\delta = 0.08$, 2000 kg payload.

$$
\lambda = e^{-5000/4414.5}-0.08 = 0.3222-0.08 = 0.2422,\qquad m_0 = \frac{2000}{0.2422} = 8258\text{ kg}
$$

$$
m_p = m_0(1-\lambda-\delta) = 8258(0.6778) = \boxed{5598\text{ kg}}
$$

The dead weight is 661 kg. (5601 kg with $g_0 = 9.80665$.)

### (iii) Two-stage propellant mass (8)
Each stage gives 2500 m/s:

$$
\lambda_i = e^{-2500/4414.5}-0.08 = 0.4876
$$

Work down from the payload:

$$
m_{02} = \frac{2000}{0.4876} = 4102\text{ kg},\qquad m_{p2} = 4102(1-0.4876-0.08) = 1773\text{ kg}
$$

$$
m_{01} = \frac{4102}{0.4876} = 8412\text{ kg},\qquad m_{p1} = 8412(0.4324) = 3637\text{ kg}
$$

$$
\boxed{m_{p,total} = 5411\text{ kg}}
$$

> [!note] Why staging barely helps here
> Staging saves only **187 kg of propellant (3.3 %)**, and the lift-off mass actually **rises**: 8412 kg against 8258 kg. That is because in this model $\delta$ is a fixed fraction of each stage's *initial* mass, so the dead weight totals 1001 kg against 661 kg.
>
> With $\Delta V/c = 1.13$ the single stage is already feasible. Staging pays off only when $\Delta V/c$ is large. Contrast [[SESA2023 Problem Sheet 10 Rockets Solutions]] Q10.2, where $\Delta V/c = 3.5$ and staging cuts the mass 22×. See [[Rocket Staging]].

### (iv) Altitude and $\dot m$ (5)
**No influence** while the throat is choked, which is always the case in rocket operation:
- $\dot m = \dfrac{A_tp_c}{\sqrt{RT_c}}\sqrt\gamma\left(\dfrac{2}{\gamma+1}\right)^{\frac{\gamma+1}{2(\gamma-1)}}$ depends only on the chamber conditions and $A_t$.
- Information about the back pressure cannot travel upstream through the sonic throat.

Altitude changes only the flow **downstream**: the pressure thrust $(p_e-p_a)A_e$, the shock and plume structure, and possible flow separation in an over-expanded nozzle at sea level. So thrust, $C_F$ and $I_{sp}$ rise with altitude, while $\dot m$ and $C^*$ are unchanged. See [[Critical Conditions and Choked Flow]].

---

## Q3: Turbojet turbine

### (i) Turbine pressure ratio (10)
Compressor $\Delta T_0 = 600$ K with $c_{p,a} = 1020$. Products have $c_{p,g} = 1150$ and $\gamma = 1.32$ ($\gamma/(\gamma-1) = 4.125$). AFR = 50, so $f = 0.02$. $T_{04} = 1500$ K and $\eta_t = 0.91$.

Work balance (the turbine drives the compressor; the turbine flow includes the fuel):

$$
c_{p,a}\Delta T_{0,c} = (1+f)c_{p,g}\Delta T_{0,t}\;\Rightarrow\;\Delta T_{0,t} = \frac{1020(600)}{1.02(1150)} = 521.7\text{ K},\qquad T_{05} = 978.3\text{ K}
$$

$$
T_{05s} = 1500-\frac{521.7}{0.91} = 926.7\text{ K},\qquad \frac{p_{04}}{p_{05}} = \left(\frac{1500}{926.7}\right)^{4.125} = \boxed{7.29}
$$

(7.68 if $f$ is neglected in the work balance.)

### (ii) Pressure ratios against combustor outlet temperature (4)
![[prop_e2425_q3_pressure_ratios.png|680]]

- With a fixed compressor work, the turbine must deliver a fixed $\Delta T_0$.
- A hotter turbine inlet makes that $\Delta T_0$ a **smaller fraction** of $T_{04}$, so a **smaller turbine pressure ratio** is needed: $\pi_t = [T_{04}/(T_{04}-\Delta T_0/\eta_t)]^{\gamma/(\gamma-1)}$, which falls with $T_{04}$.
- The OPR is fixed and $\pi_t\times\pi_{nozzle} = $ OPR (no losses), so the **nozzle pressure ratio rises**. More expansion (and hotter gas) is left for the jet, and hence more thrust.

### (iii) High combustor outlet temperature in a turbofan (≤ 200 words) (7)
- **Advantages**:
  - More **specific work** from the core: smaller, lighter core for the thrust, and a better thrust-to-weight.
  - Higher **thermal efficiency**, because the optimum OPR rises with $T_{04}/T_{02}$.
  - In a turbofan the extra core energy is transferred to a larger bypass flow (a higher bpr at a lower fpr), so the high $\eta_{th}$ is **combined with** a high $\eta_P$ and TSFC falls.
  - Also a smaller core for a given power.
- **Disadvantages**:
  - Turbine blade and vane life: creep, oxidation and thermal fatigue.
  - The need for single-crystal superalloys, **thermal barrier coatings** and **cooling air** (15–25 % bled from the compressor), whose mixing and pumping losses erode the efficiency gain.
  - Higher **NOₓ** (exponential in flame temperature), which conflicts with emissions rules.
  - Higher cost and maintenance.
  - Hot-day take-off sets the limit.

See [[Turbine Entry Temperature and Blade Cooling]].

### (iv) Exhaust velocity and propulsive efficiency (≤ 100 words) (4)
- $\eta_P = 2/(1+V_j/V)$: the closer the jet velocity is to the flight speed, the less kinetic energy is wasted in the wake, and the higher $\eta_P$. But thrust per unit mass flow ($\approx V_j-V$) falls, so more mass flow is needed.
- A **high-bypass turbofan** (or a geared turbofan, open rotor or turboprop) uses the core's power to drive a large fan, accelerating a large mass of air by a small $\Delta V$. That lowers the mean $V_j$ and raises $\eta_P$ to about 0.8.

See [[Propulsive Efficiency]].

---

## Q4: Axial compressor rotor (2 kg/s, 15,000 rpm, $r = 0.2$ m, $V_{\theta2} = 200$ m/s)

### (i) Shaft power (6)

$$
U = \Omega r = \frac{15{,}000(2\pi)}{60}(0.2) = 314.2\text{ m/s}
$$

No inlet swirl, so the Euler equation gives:

$$
w = UV_{\theta2}-UV_{\theta1} = 314.2(200) = 62.83\text{ kJ/kg},\qquad \dot W = \dot mw = \boxed{125.7\text{ kW}}
$$

See [[Euler Work Equation]].

### (ii) Isentropic pressure ratio (8)

$$
T_{02} = 300+\frac{62{,}832}{1005} = 362.5\text{ K},\qquad \frac{p_{02}}{p_{01}} = \left(\frac{362.5}{300}\right)^{3.5} = \boxed{1.94},\qquad p_{02} = 1.94(101.325) = \boxed{196.5\text{ kPa}}
$$

### (iii) Rotor-exit velocity triangle (3)
$V_x = 100$ m/s and $V_\theta = 200$ m/s.
- Absolute: $V_2 = 223.6$ m/s at $\alpha_2 = 63.4^\circ$.
- Relative: $W_\theta = 200-314.2 = -114.2$ m/s, so $W_2 = 151.8$ m/s at $\beta_2 = -48.8^\circ$ (against the rotation).

![[prop_e2425_q4_triangle.png|560]]

### (iv) Static pressure at rotor exit (4)

$$
T_2 = T_{02}-\frac{V_2^2}{2c_p} = 362.5-\frac{223.6^2}{2010} = 337.6\text{ K}
$$

$$
p_2 = p_{02}\left(\frac{T_2}{T_{02}}\right)^{3.5} = 196.5(0.7797) = \boxed{153.2\text{ kPa}}\quad(M_2 = 0.61)
$$

### (v) Raising the static pressure at exit (4)
- The flow leaves the rotor with a large kinetic energy (25 K of $T_0$ is locked in as velocity, 63° swirl). Add a **stator (or outlet guide vane) row** that turns the flow back to axial and **diffuses** it, converting swirl KE into static pressure.
  - Removing the swirl alone ($V$: 224 → 100 m/s) raises $p$ to about **187 kPa** (isentropic).
- Then a **diffuser** (increasing annulus area) slows $V_x$ further before the combustor.
- Alternatives:
  - design the rotor for a higher degree of reaction (more static rise in the rotor itself, e.g. $R = 0.5$);
  - more stages;
  - a higher blade speed or loading within the stall and de Haller limits.

See [[Degree of Reaction]].

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2024-25" and extras)

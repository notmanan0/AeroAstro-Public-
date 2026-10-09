---
title: "SESA2023 Exam 2013-14 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2013-14"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W05 - Combustion, Stoichiometry and Chemical Equilibrium]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201314-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2013-14 Solutions

> [!info] Paper
> 120 min, closed book. Answer Q1 and **any two** of Q2–Q4 (30 marks each). Given: $M = V/\sqrt{\gamma RT}$, $T_0/T = 1+\frac{\gamma-1}2M^2$, isentropic $T_0/T = (p_0/p)^{(\gamma-1)/\gamma}$, air $R = 287$, $\gamma = 1.4$, so $c_p = 1004.5\approx1005$.

> [!tip] Conventions used throughout
> - Fuel-air ratio from $(1+f)c_pT_{04} = c_pT_{03}+f\,LCV$ (no reference temperature, as in the pre-2020 papers; see the warning in [[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat|W06]]).
> - The fuel mass is carried through the turbine and nozzle. The simpler $f\approx c_p\Delta T/LCV$ changes answers by only about 3 %.

## Q1: Turbojet cycle

### (i) Block diagram (5)
Intake (1–2) → compressor (2–3) → combustor (3–4) → turbine (4–5) → propelling nozzle (5–6), with the turbine driving the compressor through a shaft.
- **Intake**: decelerates the flow with minimum loss of $p_0$ (ram compression) and delivers uniform flow at M ≈ 0.5 to the compressor.
- **Compressor**: raises $p_0$ (the cycle pressure ratio sets $\eta_{th}$). Its work comes from the turbine.
- **Combustor**: adds heat at nearly constant pressure by burning fuel, raising $T_0$ to the turbine entry limit.
- **Turbine**: extracts just enough work to drive the compressor ($w_t = w_c$). The remaining $p_0$ and $T_0$ are available for the jet.
- **Nozzle**: accelerates the gas to a high jet velocity $V_j$. The thrust is $\dot m[(1+f)V_j-V]$.

See [[Turbojet]].

### (ii) Ideal and real $T$–$s$ diagrams (5)
![[prop_turbojet_Ts.png|620]]
- **Ideal**: the compression 1–3 and expansion 4–6 are vertical (isentropic), and heat is added along one isobar $p_{03} = p_{04}$.
- **Real**:
  - $\eta_c<1$ means the compressor exit is hotter than isentropic, so more work is needed.
  - $\eta_t<1$ means the turbine exit is hotter than isentropic, and a larger pressure ratio is needed for the same work.
  - Stagnation-pressure losses in the intake, combustor and nozzle mean the isobars do not coincide.
  - $c_p$ of the products is higher than for air.
  - All irreversibilities move the states to the right (entropy rises), leaving less expansion for the jet.

### (iii) Compressor entry state (5)
$M = 0.9$, $p_a = 22$ kPa, $T_a = 230$ K, ideal intake ($T_{02} = T_{01}$, $p_{02} = p_{01}$):

$$
T_{02} = 230(1+0.2\times0.81) = \boxed{267.3\text{ K}},\qquad p_{02} = 22(1.162)^{3.5} = \boxed{37.21\text{ kPa}}
$$

### (iv) Fuel-air ratio (5)
Compressor with $r_c = 30$ and $\eta_c = 0.9$:

$$
T_{03s} = 267.3(30)^{0.2857} = 706.3\text{ K},\qquad T_{03} = 267.3+\frac{706.3-267.3}{0.9} = 755.1\text{ K},\qquad p_{03} = 1116\text{ kPa}
$$

Combustor to $T_{04} = 1800$ K:

$$
f = \frac{c_p(T_{04}-T_{03})}{LCV-c_pT_{04}} = \frac{1005(1044.9)}{41\times10^6-1.809\times10^6} = \boxed{0.0268}
$$

### (v) Turbine pressure ratio (5)
Work balance: $c_p(T_{03}-T_{02}) = (1+f)c_p(T_{04}-T_{05})$.

$$
T_{05} = 1800-\frac{487.8}{1.0268} = 1324.9\text{ K},\qquad T_{05s} = 1800-\frac{475.1}{0.85} = 1241.1\text{ K}
$$

$$
\frac{p_{04}}{p_{05}} = \left(\frac{1800}{1241.1}\right)^{3.5} = \boxed{3.67}
$$

This is 3.83 if the fuel mass is neglected in the work balance.

### (vi) Specific thrust (5)
With no combustor loss, $p_{05} = 1116/3.674 = 303.8$ kPa. The ideal nozzle expands fully to 22 kPa:

$$
V_j = \sqrt{2c_pT_{05}\left[1-\left(\frac{p_a}{p_{05}}\right)^{0.2857}\right]} = \sqrt{2(1005)(1324.9)(1-0.4723)} = 1185.5\text{ m/s},\qquad V = 0.9\sqrt{1.4(287)(230)} = 273.6\text{ m/s}
$$

$$
\frac{F}{\dot m_a} = (1+f)V_j-V = 1.0268(1185.5)-273.6 = \boxed{944\text{ N s/kg}}
$$

This is 912 if $(1+f)$ is dropped. TSFC = $f/(F/\dot m_a)$ = 28.4 g kN⁻¹ s⁻¹.

---

## Q2: Ideal ramjet

### (i) Applications and issues (5)
- **Use**: supersonic missiles and target drones (M 2–4), and the ramjet mode of turbo-ramjets such as the SR-71's J58. A ramjet produces **no static thrust**, so it needs a rocket boost or a turbojet to reach operating speed.
- **Aerodynamics**:
  - The intake must decelerate supersonic flow through oblique shocks and a terminal normal shock with minimum $p_0$ loss. See [[Intake Pressure Recovery]].
  - Shock position must be controlled (intake **unstart**), with variable geometry and bleed.
  - Wave drag is high, so slender bodies are needed.
- **Materials**:
  - Kinetic heating: $T_0\approx T_a(1+0.2M^2)$ is about 600 K at M 3, which needs titanium, Inconel or high-temperature composites.
  - The combustor and nozzle see the full cycle temperature with **no turbine limit**, so they need cooling and liners.
  - Thermal expansion of the whole airframe must be accommodated.

See [[Ramjet]].

### (ii) Effect of flight Mach number at fixed $T_{03}$ (5)
![[prop_ramjet_performance.png|700]]
- Raising $M$ raises $T_{02} = T_a(1+0.2M^2)$ and the ram pressure ratio.
- **Thermal efficiency** $\eta_{th} = 1-T_a/T_{02}$ rises: compression is higher.
- The heat added, $c_p(T_{03}-T_{02})$, shrinks, so the $T$–$s$ "loop" becomes tall and thin.
- **Specific thrust** first rises, then falls to zero when $T_{02}\to T_{03}$ (no heat can be added).
- There is therefore an upper Mach limit, and a best Mach number for thrust below it.

### (iii) Flight speed and Mach number (5)
Energy balance on the burner (ideal, $T_{03} = 2750$ K, $f = 0.03$):

$$
(1+f)c_pT_{03} = c_pT_{02}+f\,LCV\;\Rightarrow\;T_{02} = 1.03(2750)-0.03\frac{41\times10^6}{1005} = 1608.6\text{ K}
$$

$$
M = \sqrt{\frac{T_{02}/T_a-1}{0.2}} = \sqrt{\frac{7.413-1}{0.2}} = \boxed{5.66},\qquad V = 5.66\sqrt{1.4(287)(217)} = \boxed{1672\text{ m/s}}
$$

### (iv) Exhaust Mach number and speed (5)
In an ideal ramjet $p_{04} = p_{01}$ and $p_4 = p_a$, so $p_{04}/p_4 = p_{01}/p_a$ and **$M_e = M = 5.66$**.

$$
T_e = \frac{T_{03}}{1+0.2M^2} = \frac{2750}{7.413} = 371.0\text{ K},\qquad V_e = 5.66\sqrt{1.4(287)(371.0)} = \boxed{2186\text{ m/s}}
$$

### (v) Efficiencies (10)
Assumptions: ideal and fully expanded; air properties throughout; $f$ from (iii).

$$
\frac{F}{\dot m_a} = (1+f)V_e-V = 1.03(2186)-1672 = 579.7\text{ N s/kg}
$$

| Efficiency | Definition | Value |
|---|---|---|
| Overall | $\eta_O = \dfrac{FV}{\dot m_fLCV}$ = thrust power / fuel power | $\dfrac{579.7(1672)}{0.03(41\times10^6)} = \mathbf{0.788}$ |
| Propulsive | $\eta_P = \dfrac{FV}{\tfrac12\dot m_a[(1+f)V_e^2-V^2]}$ = thrust power / jet KE increase | $\mathbf{0.911}$ (0.867 from $2/(1+V_e/V)$) |
| Thermal | $\eta_{th} = \dfrac{\tfrac12[(1+f)V_e^2-V^2]}{f\,LCV}$ = jet KE increase / fuel power | $\mathbf{0.865} = 1-T_a/T_{02}$ ✓ |

$\eta_O = \eta_P\eta_{th}$. Such high values reflect the ideal components and the very high Mach number. See [[Thermal and Overall Efficiency]] and [[Propulsive Efficiency]].

---

## Q3: Two-shaft M 2 turbofan (bpr 0.5, 20 kg/s)

### (i) Cold-nozzle exhaust velocity (10)
$V = 2\sqrt{1.4(287)(216)} = 589.2$ m/s, and $T_{01} = T_{02} = 216(1.8) = 388.8$ K.

**Intake**, 95 % isentropic efficiency ($T_{02s}$ is the temperature that would reach the actual $p_{02}$ isentropically):

$$
T_{02s} = T_a+0.95(T_{01}-T_a) = 380.2\text{ K},\qquad p_{02} = 22\left(\frac{380.2}{216}\right)^{3.5} = 159.1\text{ kPa}\;(\Gamma_d = 0.924)
$$

**Fan**, pressure ratio 1.4 and $\eta_f = 0.9$:

$$
T_{013} = 388.8\left[1+\frac{1.4^{0.2857}-1}{0.9}\right] = 432.4\text{ K},\qquad p_{013} = 222.8\text{ kPa}
$$

**Cold nozzle**, ideal and expanding to 22 kPa:

$$
V_{jc} = \sqrt{2(1005)(432.4)\left[1-\left(\frac{22}{222.8}\right)^{0.2857}\right]} = \boxed{648.5\text{ m/s}}
$$

### (ii) Turbine pressure ratios (10)
Core compressor from the fan exit, $r_c = 30$ and $\eta_c = 0.9$:

$$
T_{03} = 432.4\left[1+\frac{30^{0.2857}-1}{0.9}\right] = 1221.6\text{ K},\qquad p_{03} = 6683\text{ kPa}
$$

$$
f = \frac{1005(1750-1221.6)}{41\times10^6-1005(1750)} = 0.01353
$$

**HP turbine** drives the core compressor (core flow only):

$$
\Delta T_{HPT} = \frac{1221.6-432.4}{1.01353} = 778.6\text{ K}\Rightarrow T_{045} = 971.4\text{ K},\quad T_{045s} = 1750-\frac{778.6}{0.85}
$$

$$
\boxed{\frac{p_{04}}{p_{045}} = 13.39}
$$

**LP turbine** drives the fan, which handles $(1+bpr) = 1.5$ kg per kg of core:

$$
\Delta T_{LPT} = \frac{1.5(432.4-388.8)}{1.01353} = 64.5\text{ K}\Rightarrow T_{05} = 906.8\text{ K},\quad T_{05s} = 971.4-\frac{64.5}{0.9}
$$

$$
\boxed{\frac{p_{045}}{p_{05}} = 1.31}
$$

### (iii) Total thrust (10)
$p_{05} = 6683/(13.39\times1.308) = 381.8$ kPa.

$$
V_{jh} = \sqrt{2(1005)(906.8)\left[1-\left(\frac{22}{381.8}\right)^{0.2857}\right]} = 1008.1\text{ m/s}
$$

With $\dot m_c = 20/1.5 = 13.33$ kg/s and $\dot m_b = 6.67$ kg/s:

$$
F = \dot m_c[(1+f)V_{jh}-V]+\dot m_b(V_{jc}-V) = 13.33(1021.7-589.2)+6.67(648.5-589.2) = \boxed{6.16\text{ kN}}
$$

At M 2 the ram drag ($\dot mV = 11.8$ kN) almost cancels the gross thrust. The bypass stream contributes only 0.4 kN because its jet is barely faster than flight. A low bpr (or a pure turbojet with reheat) is used at supersonic speed for this reason. See [[Bypass Ratio and Fan Pressure Ratio]].

---

## Q4: Rocket performance and H₂/O₂ equilibrium

### (i) Definitions (5)
- **Specific impulse**: impulse per unit *weight* of propellant, $I_{sp} = F/(\dot mg_0)$ (s).
- **Equivalent (effective) exhaust velocity**: $c = F/\dot m = V_e+(p_e-p_a)A_e/\dot m = g_0I_{sp}$.
- **Characteristic exhaust velocity**: $C^* = p_cA_t/\dot m$. A measure of combustion and propellant performance, independent of the nozzle.

See [[Rocket Performance Parameters]].

### (ii) $I_{sp}$ for ideal full expansion (5)
Assumptions: steady, adiabatic, isentropic nozzle flow of a perfect gas with constant $c_p$ and $\gamma$; negligible chamber velocity ($T_{02} = T_c$); fully expanded ($p_e = p_a$, so $c = V_e$).

The SFEE across the nozzle gives $V_e^2/2 = c_p(T_{02}-T_e)$, and the isentropic relation gives $T_e = T_{02}(p_e/p_{02})^{(\gamma-1)/\gamma}$. So:

$$
V_e = \sqrt{2c_pT_{02}\left[1-\left(\frac{p_e}{p_{02}}\right)^{\frac{\gamma-1}{\gamma}}\right]},\qquad I_{sp} = \frac{F}{\dot mg} = \frac{V_e}{g} = \frac1g\sqrt{2c_pT_{02}\left[1-\left(\frac{p_e}{p_{02}}\right)^{\frac{\gamma-1}{\gamma}}\right]}\;\blacksquare
$$

### (iii) Equilibrium composition (10)
$\mathrm{H_2+\tfrac12O_2\to aH_2O+bH_2+cOH}$. Atom balances:
- O: $1 = a+c$, so $a = 1-c$.
- H: $2 = 2a+2b+c$, so $b = c/2$.

Total moles $n = a+b+c = 1+c/2 = (2+c)/2$.

Partial pressures are $p_i = (n_i/n)P$, so:

$$
K = \frac{p_{OH}\sqrt{p_{H_2}}}{p_{H_2O}} = \frac{c}{1-c}\sqrt{\frac{(c/2)P}{(2+c)/2}} = \frac{c}{1-c}\sqrt{\frac{cP}{2+c}}
$$

Squaring: $K^2(1-c)^2(2+c) = c^3P$. Since $(1-c)^2(2+c) = 2-3c+c^3$:

$$
c^3(P-K^2)+3K^2c-2K^2 = 0\;\xrightarrow{\;\div(-2K^2)\;}\;\boxed{\left(\frac12-\frac{P}{2K^2}\right)c^3-1.5c+1 = 0}\;\blacksquare
$$

See [[Chemical Equilibrium and Dissociation]].

### (iv) $p_{H_2}$ at 3000 K and 40 bar (10)
From the table, $\ln K = -2.937$ at 3000 K, so $K = 0.05302$ bar$^{1/2}$ and $K^2 = 0.002812$ bar. Then:

$$
A = \frac12-\frac{40}{2(0.002812)} = -7112.9
$$

Iterate in the stable form $c = [(1-1.5c)/7112.9]^{1/3}$ from $c_0 = 0.06$:

| Iteration | $c$ |
|---|---|
| 0 | 0.06 |
| 1 | 0.05039 |
| 2 | 0.05065 |
| 3 | 0.05065 |

> [!warning] Choose a convergent form
> The rearrangement $c = (1+Ac^3)/1.5$ **diverges** (it gives $c = -0.36$ on the first step), because its slope is about 50.

With $c = 0.0506$: $a = 0.9494$, $b = 0.0253$ and $n = 1.0253$.

$$
p_{H_2} = \frac{b}{n}P = \frac{0.0253}{1.0253}(40) = \boxed{0.99\text{ bar}}
$$

Also $p_{OH} = 1.98$ bar and $p_{H_2O} = 37.0$ bar. Check: $K = 1.976\sqrt{0.988}/37.04 = 0.0530$ ✓.

Only about 5 % of the water dissociates at 40 bar. High chamber pressure suppresses dissociation (Le Chatelier: the dissociation increases the number of moles), which keeps more of the chemical energy as sensible heat. That is one reason rocket engines run at high $p_c$.

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2013-14")

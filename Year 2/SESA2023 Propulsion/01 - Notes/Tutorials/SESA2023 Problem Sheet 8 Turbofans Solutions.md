---
title: "SESA2023 Problem Sheet 8 Turbofans Solutions"
module: "SESA2023 Propulsion"
type: tutorial
stream: "Section 3: Ramjets, Gas Turbines, Turbojets and Turbofans"
tags:
  - sesa2023
  - tutorial-solutions
  - turbofan
  - fan-pressure-ratio
sheet: "Exercises Week 8 (turbofans)"
theory_notes: ["[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]"]
key_concepts: ["[[Bypass Ratio and Fan Pressure Ratio]]", "[[Propulsive Efficiency]]", "[[Turbojet]]", "[[Isentropic Efficiency]]"]
status: complete
sources: ["02 - Sources/Tutorial Sheets/Problem Sheet Week 08 - Turbofans.pdf"]
---

# SESA2023 Problem Sheet 8 Turbofans Solutions

> [!abstract] Sheet Info
> One engine core (OPR 45, TET 1500 K, M 0.78 at 35,000 ft, 90 % components, cold air) is used three ways:
> 1. as a pure turbojet;
> 2. as turbofans with fpr 1.4, 1.5 and 1.6;
> 3. with nacelle drag included.
>
> All the printed answers are reproduced ✔, to within the rounding of inputs (the sfc values differ by at most 0.02 g/s/kN).

## Theory Links
- [[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]
- [[Bypass Ratio and Fan Pressure Ratio]] · [[Propulsive Efficiency]] · [[Turbojet]]

Ambient at 35,000 ft: $T_a = 218.81$ K, $p_a = 23.8$ kPa, $V = 0.78\sqrt{\gamma RT_a} = 231.3$ m/s. At the fan face, $T_{02} = 245.4$ K and $p_{02} = 35.6$ kPa, which are consistent with M 0.78 ✔.

---

## Q8.1: Core temperatures
### (a) Fan, booster and HPC

$$
T_{013}-T_{02} = \frac{245.4(1.5^{0.2857}-1)}{0.9} = \boxed{33.5\text{ K}},\qquad T_{023}-T_{02} = \frac{245.4(2.5^{0.2857}-1)}{0.9} = \boxed{81.6\text{ K}}
$$

$$
T_{023} = \boxed{327.0\text{ K}},\qquad T_{03} = 327.0\Big(1+\frac{18^{0.2857}-1}{0.9}\Big) = \boxed{793.5\text{ K}},\qquad\Delta T_{HPC} = \boxed{466.5\text{ K}}\;✔
$$

### (b) HP turbine
The HPT drives the HPC (same $c_p$, fuel mass neglected):

$$
T_{045} = 1500-466.5 = \boxed{1033.5\text{ K}},\qquad T_{045s} = 1500-\frac{466.5}{0.9} = 981.7\text{ K}
$$

$$
p_{03} = 35.6(2.5)(18) = 1602\text{ kPa} = p_{04},\qquad p_{045} = 1602\Big(\frac{981.7}{1500}\Big)^{3.5} = \boxed{363.5\text{ kPa}}\;✔
$$

### (c) Remove the LP work for the core stream (81.6 K)

$$
T = 1033.5-81.6 = \boxed{951.9\text{ K}},\qquad T_s = 1033.5-\frac{81.6}{0.9} = 942.8\text{ K},\qquad p = 363.5\Big(\frac{942.8}{1033.5}\Big)^{3.5} = \boxed{263.6\text{ kPa}}\;✔
$$

## Q8.2: Pure turbojet using the gas generator exit (951.9 K, 263.6 kPa)

$$
V_j = \sqrt{2c_p(951.9)\big[1-(23.8/263.6)^{0.2857}\big]} = \boxed{975\text{ m/s}}\;✔
$$

| Quantity | Value |
|---|---|
| (b) $\eta_P = 2V/(V+V_j)$ | **0.383** ✔ |
| (c) $F_G/\dot m_c = V_j$ | **975** N s/kg ✔ |
| (c) $F_N/\dot m_c = V_j-V$ | **744** N s/kg ✔ |
| (d) $\eta_O = F_NV/[c_p(T_{04}-T_{03})]$ | $\dfrac{744(231.3)}{1005(706.5)}$ = **0.242** ✔ |
| (e) sfc, with $f = c_p(T_{04}-T_{03})/LCV = 0.01651$ | $f/(F_N/\dot m)$ = **22.2 g s⁻¹ kN⁻¹** ✔ |

$\eta_{th} = \eta_O/\eta_P = 0.63$. That is a good cycle wasted by a jet that is far too fast.

## Q8.3: Turbofan with the same core, $V_{jc} = V_{jb}$
**Method**:
1. **Bypass**: $T_{013} = T_{02}\big(1+(fpr^{0.2857}-1)/0.9\big)$, $p_{013} = fpr\cdot p_{02}$, then $V_{jb}$ from isentropic expansion to $p_a$.
2. **LPT** from 1033.5 K and 363.5 kPa: iterate the LPT pressure ratio $\pi$ until $V_{jc}(T_{05},p_{045}/\pi) = V_{jb}$. Here $T_{05} = T_{045}-0.9T_{045}(1-\pi^{-0.2857})$.
3. **BPR**: the LP work balance $(T_{045}-T_{05}) = (T_{023}-T_{02})+BPR(T_{013}-T_{02})$.
4. **Thrust**: $F_N/\dot m_c = (1+BPR)(V_j-V)$ and $F_G/\dot m_c = (1+BPR)V_j$. Specific thrust $X = F_N/\dot m_a = V_j-V$.
5. **Efficiency and sfc**: $\eta_O = F_NV/[\dot m_cc_p(T_{04}-T_{03})]$; $f$ is the same as in Q8.2.

| fpr | $V_j$ (m/s) | $\eta_P$ | $p_{045}/p_{05}$ | $T_{045}/T_{05}$ | bpr | $F_G/\dot m_c$ (kN s/kg) | $F_N/\dot m_c$ (kN s/kg) | $F_N/\dot m_a$ (N s/kg) | $\eta_O$ | sfc (g/s/kN) |
|---|---|---|---|---|---|---|---|---|---|---|
| 1.4 | **323** | **0.834** | **10.95** | **1.804** | **13.8** | **4.78** | **1.358** | **91.9** | **0.442** | **12.16** |
| 1.5 | **340** | **0.810** | **10.58** | **1.790** | **11.2** | **4.14** | **1.324** | **108.7** | **0.431** | **12.47** |
| 1.6 | **355** | **0.789** | **10.24** | **1.776** | **9.4** | **3.71** | **1.295** | **124.0** | **0.422** | **12.75** |

All agree with the sheet ✔ (its sfc values are 12.18, 12.49 and 12.77).

**Interpretation**:
- The **same core** produces 1.8× the net thrust of the turbojet ($F_N/\dot m_c$ = 1.32 against 0.744 kN s/kg) at **56 % of its sfc**.
- Lowering fpr improves bare-engine sfc, but specific thrust falls. For a given thrust the fan and nacelle must grow.

![[prop_turbofan_fpr.png|700]]

## Q8.4: Installed sfc with $F_{N,eff} = F_{N,bare}(1-9.25/X)$
The core and fuel flow are unchanged, so $\text{sfc}_{eff} = \text{sfc}_{bare}/(1-9.25/X)$:

| fpr | $X$ | factor $1-9.25/X$ | sfc$_{eff}$ (g/s/kN) |
|---|---|---|---|
| 1.4 | 91.9 | 0.899 | **13.52** (sheet 13.55) ✔ |
| 1.5 | 108.7 | 0.915 | **13.63** (13.65) ✔ |
| 1.6 | 124.0 | 0.925 | **13.78** (13.8) ✔ |

Nacelle drag penalises low fpr most, and nearly flattens the advantage. Once engine **weight** is added (W07 §4), a true optimum appears near fpr ≈ 1.5.

## Sources
- `02 - Sources/Tutorial Sheets/Problem Sheet Week 08 - Turbofans.pdf`. Solved numerically (root-finding on the LPT pressure ratio).

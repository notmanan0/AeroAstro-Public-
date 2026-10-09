---
title: "SESA2023 Exam 2016-17 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2016-17"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W07 - Turbofan Architectures and Fan Pressure Ratio Selection]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]", "[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201617-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2016-17 Solutions

> [!info] Paper
> Closed book, with the Calvert & Farrar data book. Four questions of 25 marks, titled *Pure Afterburning Turbojets*, *Spacecraft Propulsion*, *Turbofans* and *High Speed Flight*. Air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$.

## Q1: Pure afterburning turbojet (OPR 15, M 2, TET 1850 K, 22 kPa, 216 K)

### (i) $T$–$s$ diagrams, ideal and real (5)
![[prop_e2021_q3_reheat_Ts.png|640]]

*(The figure is the 2020-21 engine; the shape is identical.)*
- **Ideal**: isentropic 1–3; isobaric burner 3–4; isentropic turbine 4–5; isobaric afterburner 5–6 at the **lower** pressure $p_{05}$; isentropic nozzle 6–7 to $p_a$.
- **Real**:
  - compressor and turbine lines lean to the right ($\eta<1$), so a hotter compressor exit and a hotter turbine exit;
  - $p_0$ drops in the intake, burner, afterburner (flame holders and heat addition, the Rayleigh loss) and nozzle;
  - combustion efficiency < 1;
  - product $c_p$ > air $c_p$.
- The afterburner isobar lies **below** the main burner isobar. Heat added at a lower pressure is converted less efficiently, which is why TSFC rises.

### (ii) Combustor entry temperature (5)
Ideal intake and $\eta_c = 0.9$:

$$
T_{02} = 216(1.8) = 388.8\text{ K},\quad p_{02} = 22(1.8)^{3.5} = 172.1\text{ kPa};\qquad T_{03s} = 388.8(15)^{0.2857} = 842.9\text{ K}
$$

$$
T_{03} = 388.8+\frac{454.1}{0.9} = \boxed{893.3\text{ K}}
$$

### (iii) Fuel-air ratio with $\eta_b = 0.95$ (5)
Only 95 % of the fuel energy is released:

$$
(1+f)c_pT_{04} = c_pT_{03}+f\eta_bLCV\;\Rightarrow\;f = \frac{1005(1850-893.3)}{0.95(41\times10^6)-1005(1850)} = \boxed{0.0259}
$$

This is 0.0247 with the simple $c_p\Delta T/(\eta_bLCV)$.

### (iv) Turbine pressure ratio and exit temperature, $\eta_t = 0.92$ (5)

$$
T_{05} = 1850-\frac{893.3-388.8}{1.0259} = \boxed{1358.2\text{ K}},\qquad T_{05s} = 1850-\frac{491.8}{0.92} = 1315.5\text{ K}
$$

$$
\frac{p_{04}}{p_{05}} = \left(\frac{1850}{1315.5}\right)^{3.5} = \boxed{3.30}
$$

So $p_{05} = 15(172.1)/3.298 = 782.8$ kPa.

### (v) Afterburner to $T_{06} = 2500$ K (5)
Isobaric ($p_{06} = p_{05}$), ideal combustion of extra fuel $f_{ab}$ (per kg of air):

$$
(1+f)c_pT_{05}+f_{ab}LCV = (1+f+f_{ab})c_pT_{06}\;\Rightarrow\;f_{ab} = \frac{1.0259(1005)(2500-1358.2)}{41\times10^6-1005(2500)} = 0.0306,\qquad f_{tot} = 0.0565
$$

The ideal nozzle expands fully to 22 kPa:

$$
T_7 = 2500\left(\frac{22}{782.8}\right)^{0.2857} = \boxed{901\text{ K}},\qquad V_j = \sqrt{2(1005)(2500-901)} = \boxed{1793\text{ m/s}}
$$

With $V = 2\sqrt{1.4(287)(216)} = 589.2$ m/s:

$$
\frac{F}{\dot m_a} = (1+f_{tot})V_j-V = 1.0565(1792.8)-589.2 = \boxed{1305\text{ N s/kg}}
$$

Dry, the same engine gives $V_j = 1321$ m/s and 766 N s/kg. Reheat gives **+70 % thrust** for **+118 % fuel**, so TSFC rises from 33.8 to 43.3 g kN⁻¹ s⁻¹.

---

## Q2: Spacecraft propulsion

### (i) Ion vs chemical: what sets thrust and $I_{sp}$ (5)
- **Chemical**: the energy comes from the propellant itself (about 13 MJ/kg for H₂/O₂), so $c\le\sqrt{2\Delta h_{chem}}\approx4.5$ km/s. $I_{sp}$ is **energy-limited** (≤ 460 s). The thrust is **power-unlimited**: huge mass flows through a small nozzle give MN of thrust at high thrust-to-weight.
- **Electrostatic**:
  - The energy comes from an external electrical source.
  - Ions of charge $q$ accelerated through potential $V_b$ reach $v = \sqrt{2qV_b/m_i}$, typically 30–50 km/s, so **$I_{sp}$ ≈ 3000–5000 s**.
  - Thrust is **power-limited**: $F = 2\eta P/v$. The jet power grows as $v^2$ per unit thrust, so a few kW gives only about 0.1 N.
  - Thrust is also **space-charge-limited**: the Child–Langmuir law gives $j\propto V^{3/2}/d^2$ across the grids, so thrust per unit area is at most a few N/m².
  - Grid erosion limits life.
- The result: very high $\Delta V$ capability (low propellant mass) but very low accelerations, requiring **long burns**.

See [[Electric (Ion) Propulsion]].

### (ii) Thrust of two xenon ion thrusters (5)
Singly charged, $m_i = 131.3(1.66\times10^{-27}) = 2.180\times10^{-25}$ kg:

$$
v = \sqrt{\frac{2eV_b}{m_i}} = \sqrt{\frac{2(1.6\times10^{-19})(1800)}{2.180\times10^{-25}}} = 51{,}410\text{ m/s},\qquad \dot m = \frac{Im_i}{e} = \frac{21(2.180\times10^{-25})}{1.6\times10^{-19}} = 2.861\times10^{-5}\text{ kg/s}
$$

Divergence correction $\cos15^\circ = 0.966$:

$$
F_1 = \dot mv\cos\theta = 1.42\text{ N},\qquad F_{total} = \boxed{2.84\text{ N}}
$$

$I_{sp} = v/g_0 \approx 5240$ s. (Using $(1+\cos\theta)/2$ for a uniformly filled conical plume gives 2.89 N.)

### (iii) SSTO is not energetically achievable (5)
Assume the best chemical propellant, $I_{sp} = 450$ s ($c = 4415$ m/s). Tankage structural efficiency $\epsilon = m_s/(m_s+m_p) = 0.10$ with zero payload means the burn-out mass is $m_s$, so:

$$
MR = \frac{m_0}{m_{bo}} = \frac{m_s+m_p}{m_s} = \frac1\epsilon = 10
$$

$$
\Delta V_{ideal} = 4415\ln10 = 10{,}165\text{ m/s},\qquad \Delta V_{net} = (1-0.32-0.08)\times10{,}165 = 6099\text{ m/s}
$$

Circular orbital speed at 200 km:

$$
V_{orb} = \sqrt{\frac{\mu}{R_E+h}} = \sqrt{\frac{3.986\times10^{14}}{6.571\times10^6}} = 7788\text{ m/s}
$$

$6.1<7.8$ km/s **even with zero payload**, so SSTO is impossible. (Earth rotation adds at most 0.46 km/s.) Reaching orbit would need $MR = e^{7788/(0.6\times4415)} = 18.9$, i.e. $\epsilon = 5.3\%$, which is not structurally feasible. **Staging** discards spent structure so that each stage has a good mass ratio. See [[Tsiolkovsky Rocket Equation]] and [[Rocket Staging]].

### (iv) Five power cycles (10)
See [[SESA2023 Exam 2014-15 Solutions]] Q4(iv) and [[Rocket Engine Power Cycles]]. Name and sketch: pressure-fed, gas generator, expander, staged combustion, and full-flow staged combustion (or tap-off).

---

## Q3: Turbofans

### (i) Design philosophy (10)
See [[SESA2023 Exam 2015-16 Solutions]] Q1(v). Include the $\eta_P$ curve against $V_j/V$ and the $\eta_O = \eta_P\eta_{th}$ argument.

### (ii) Breguet range (10)
> [!warning] Mass labels in the paper
> This paper says "$w_1$ is the initial mass, $w_2$ the final" but writes $\ln(w_2/w_1)$, which would give a negative range. The correct form is $\ln(\text{initial}/\text{final})$.

Derivation: see [[SESA2023 Exam 2014-15 Solutions]] Q1(iii) and [[Breguet Range Equation]].

$$
s = \frac LD\frac{\eta_OLCV}{g_0}\ln\frac{w_{initial}}{w_{final}}
$$

High-bypass turbofans raise $\eta_O$ through $\eta_P$, and so raise range directly.

### (iii) Specific thrust of an ideal turbofan (5)
Assumptions:
- separate, fully expanded hot and cold nozzles ($p_j = p_a$, no pressure thrust);
- steady flow;
- fuel added to the core only;
- core air flow $\dot m_{aC}$ and bypass flow $\dot m_{aB} = BPR\,\dot m_{aC}$;
- both streams enter at the flight speed $V$.

Momentum balance on each stream:

$$
F = \underbrace{\dot m_{aC}[(1+f)V_{jHOT}-V]}_{\text{core}}+\underbrace{BPR\,\dot m_{aC}[V_{jCOLD}-V]}_{\text{bypass}}
$$

$$
\boxed{\frac{F}{\dot m_{aC}} = (1+f)V_{jHOT}+BPR\,V_{jCOLD}-V(1+BPR)}\;\blacksquare
$$

See [[Thrust Equation]].

---

## Q4: High-speed flight

### (i) Profiles through a reheat turbojet (5)
Stations: intake 1–2, compressor 2–3, combustor 3–4, turbine 4–5, afterburner 5–6, nozzle 6–7.

| Quantity | Intake | Compressor | Combustor | Turbine | Afterburner (on / off) | Nozzle |
|---|---|---|---|---|---|---|
| $V$ | falls (M 2 → ~0.5) | ≈ constant | small rise | rises slightly | low (≈ constant); a little higher with reheat | rises sharply to $V_j$ (higher with reheat) |
| $p_0$ | constant (ideal) or small drop | rises strongly | slight drop | falls strongly | slight drop (more when lit) | constant |
| $p$ | rises (ram) | rises | ≈ constant | falls | ≈ constant | falls to $p_a$ |
| $T_0$ | constant | rises | jumps to TET | falls | **jumps** to $T_{06}$ when lit; constant when off | constant |
| $T$ | rises | rises | jumps | falls | jumps when lit | falls (exit $T$ higher with reheat) |

The nozzle throat opens when the reheat is lit, so the upstream $p_0$ is unchanged. See [[Afterburning (Reheat)]].

### (ii) Ideal ramjet cruise missile (5)
$T_a = 230$ K, $f = 0.05$, $T_{03} = 2800$ K:

$$
T_{02} = 1.05(2800)-0.05(40{,}796) = 900.2\text{ K},\qquad M = \sqrt{\frac{900.2/230-1}{0.2}} = \boxed{3.82},\qquad V = \boxed{1160\text{ m/s}}
$$

### (iii) Exhaust (5)
$M_e = 3.82$, $T_e = 2800/3.914 = 715.4$ K and $V_e = \boxed{2046\text{ m/s}}$. $F/\dot m = 988$ N s/kg.

### (iv) SR-71 runaway acceleration (5)
- In ramjet-type operation the thrust is $F = \dot m_a[(1+f)V_e-V]$ with $\dot m_a = \rho_aA_{capture}V$.
- A small **fuel increase** raises $T_{04}$ and hence $V_e$, so the aircraft accelerates.
- As $M$ rises:
  1. the captured mass flow $\dot m_a\propto V$ rises;
  2. the ram pressure ratio $(1+0.2M^2)^{3.5}$ rises steeply (by about 35 % from M 3.2 to 3.4), so the nozzle pressure ratio and the jet velocity rise;
  3. at a **fixed fuel-air ratio** the fuel flow scales with $\dot m_a$, so heat release grows too;
  4. $\eta_{th} = 1-T_a/T_{02}$ improves.
- So thrust grows **faster** than drag: positive feedback, and ever greater acceleration.
- $T_{04}$ is not being held (the pilot increased fuel, and as $T_{02}$ rises the same $f$ gives an even higher $T_{04}$). Only throttling back (reducing $f$) restores equilibrium. Otherwise inlet, compressor-inlet and airframe temperature limits would be exceeded (at M 3.2 in a 217 K stratosphere, $T_0 = 661$ K ≈ 390 °C already), or the inlet shock system would unstart.

See [[Ramjet]] and `prop_ramjet_performance.png`.

### (v) Why a Mach 2 airliner? (5)
See [[SESA2023 Exam 2015-16 Solutions]] Q4(v):
- $\eta_O$ rises with $M$ for a turbojet ($\eta_P = 2/(1+V_j/V)$ and ram compression), partly offsetting the poor supersonic $L/D$ in Breguet.
- $T_0 = 390$ K at M 2 is the limit for aluminium airframes.
- Doubling the speed halves the block time.

Diagram: $\eta_P$ against $V_j/V$ ([[Propulsive Efficiency]]) and $T_0$ against $M$.

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2016-17")

---
title: "SESA2023 Exam 2017-18 Solutions"
module: "SESA2023 Propulsion"
type: exam-solution
year: "2017-18"
tags: [sesa2023, exam-solutions, past-papers, closed-book]
topics: ["[[SESA2023 W01 - Thrust, Efficiency, Range and the ISA]]", "[[SESA2023 W06 - Jet Engine Cycle Analysis - Brayton, Ramjet, Turbojet and Reheat]]", "[[SESA2023 W10 - Rocket Performance, Staging and Power Cycles]]"]
status: complete
sources: ["03 - Exams & Past Papers/SESA2023-201718-02-SESA2023W1.pdf"]
---

# SESA2023 Exam 2017-18 Solutions

> [!info] Paper
> Closed book with a data book and formula sheet. Four questions of 25 marks: *General Propulsion Performance*, *Turbojet Cycle Analysis*, *Spacecraft Propulsion*, *Supersonic Flight*. Air: $R = 287$, $\gamma = 1.4$, $c_p = 1005$.

## Q1: General propulsion performance

### (i) Military vs civil design drivers (5)
See [[SESA2023 Exam 2014-15 Solutions]] Q1(v) and [[SESA2023 Exam 2015-16 Solutions]] Q1(v).

### (ii) Overall efficiency derivation (20)
**Definitions** (control volume around the engine; air $\dot m_a$ in at $V$, fuel $f\dot m_a$ with no axial momentum, jet out at $V_j$ and $P_j$ over $A_j$):
- Thrust: $F = \dot m_a[(1+f)V_j-V]+(P_j-P_{atm})A_j$ (momentum balance).
- Thrust power (useful): $FV$.
- Jet kinetic-energy production: $\dot W_{KE} = \tfrac12\dot m_a[(1+f)V_j^2-V^2]$.
- Fuel power (input): $\dot m_fLCV = f\dot m_aLCV$.

**Overall efficiency** is useful power divided by fuel power. Factorise by multiplying and dividing by $\dot W_{KE}$:

$$
\eta_O = \frac{FV}{f\dot m_aLCV} = \underbrace{\frac{FV}{\dot W_{KE}}}_{\eta_P}\times\underbrace{\frac{\dot W_{KE}}{f\dot m_aLCV}}_{\eta_{th}}
$$

$$
\eta_O = \frac{V\{\dot m_a[(1+f)V_j-V]+(P_j-P_{atm})A_j\}}{\tfrac12\dot m_a[(1+f)V_j^2-V^2]}\times\frac{\tfrac12(1+f)V_j^2-\tfrac12V^2}{f\,LCV}\;\blacksquare
$$

(The paper writes the second factor as $\frac{(1+f)V_j^2-V^2}{2fLCV}$, which is the same thing.)

- **First numerator**: thrust power, the rate of useful work on the aircraft.
- **First denominator** (= second numerator): the rate of kinetic-energy increase of the working fluid. This is the "output" of the gas generator and the "input" to the propulsor.
- **Second denominator**: the rate of chemical energy supplied.

$\eta_{th}$ measures the conversion of heat to jet KE (set by OPR, TET and component efficiencies). $\eta_P$ measures how much of that KE becomes thrust work, with the rest lost as wake KE $\tfrac12\dot m(V_j-V)^2$. Hence $\eta_O = \eta_P\eta_{th}$, and range ∝ $\eta_O$ ([[Breguet Range Equation]]). See [[Thermal and Overall Efficiency]].

---

## Q2: Turbojet cycle analysis

### (i) Afterburning $T$–$s$ diagrams (5)
See [[SESA2023 Exam 2016-17 Solutions]] Q1(i) and `prop_e2021_q3_reheat_Ts.png`.

### (ii) Compressor entry state (5)
> [!warning] Misprint in the paper
> The paper gives "$p_a$ = 7165 kPa", which is impossible at 44,000 ft (≈ 71 atm). The ISA value at 44,000 ft (13.41 km) is **15.5 kPa** (Data Book Table 25 interpolation). This is used below.
>
> Only the absolute pressures depend on it: **every ratio, $f$, $\pi_t$, $V_j$ and the specific thrust are independent of $p_a$**.

$$
T_{02} = 218(1+0.2\times0.64) = \boxed{245.9\text{ K}},\qquad \frac{p_{02}}{p_a} = (1.128)^{3.5} = 1.524\;\Rightarrow\;p_{02} = \boxed{23.7\text{ kPa}}
$$

### (iii) Fuel-air ratio (5)
$r_c = 30$, $\eta_c = 0.9$:

$$
T_{03s} = 245.9(30)^{0.2857} = 649.8\text{ K},\qquad T_{03} = 245.9+\frac{403.9}{0.9} = 694.7\text{ K},\qquad p_{03} = 711\text{ kPa}
$$

$$
f = \frac{1005(1900-694.7)}{41\times10^6-1005(1900)} = \boxed{0.0310}
$$

### (iv) Turbine pressure ratio, $\eta_t = 0.88$ (5)

$$
T_{05} = 1900-\frac{448.8}{1.031} = 1464.7\text{ K},\qquad T_{05s} = 1900-\frac{435.3}{0.88} = 1405.3\text{ K}
$$

$$
\frac{p_{04}}{p_{05}} = \left(\frac{1900}{1405.3}\right)^{3.5} = \boxed{2.87}
$$

### (v) Specific thrust (5)
$p_{05}/p_a = 30(1.524)/2.874 = 15.91$ (so $p_{05} = 247$ kPa) and $V = 0.8\sqrt{1.4(287)(218)} = 236.8$ m/s.

$$
V_j = \sqrt{2(1005)(1464.7)\left[1-15.91^{-0.2857}\right]} = 1268.4\text{ m/s}\quad(T_6 = 664\text{ K})
$$

$$
\frac{F}{\dot m_a} = 1.031(1268.4)-236.8 = \boxed{1071\text{ N s/kg}}
$$

TSFC = 28.9 g kN⁻¹ s⁻¹.

---

## Q3: Spacecraft propulsion

### (i) Ion vs chemical (5)
See [[SESA2023 Exam 2016-17 Solutions]] Q2(i). Chemical propulsion is energy-limited in $I_{sp}$ but not in thrust. Electric propulsion is power-limited ($F = 2\eta P/v$) and space-charge limited in thrust, with $I_{sp}$ set by the accelerating voltage.

### (ii) SSTO impossible; staging (5)
With $\epsilon = 0.10$ and no payload: $MR = 10$. With $I_{sp}\le450$ s, $\Delta V_{ideal} = 10.2$ km/s, and after 40 % losses **6.1 km/s < 7.79 km/s** needed at 200 km. See [[SESA2023 Exam 2016-17 Solutions]] Q2(iii) for the working.

**Staging**:
- Each stage carries the rest of the vehicle as payload, $\lambda_i = e^{-\Delta V_i/c}-\delta_i$.
- Discarding empty tanks and engines means that later stages do not accelerate dead mass. The overall payload fraction $\prod\lambda_i$ then stays positive, whereas a single stage has $\lambda<0$.
- Two to three stages suffice for LEO.

See [[Rocket Staging]] and [[SESA2023 Problem Sheet 10 Rockets Solutions]] Q10.2.

### (iii) Why high chamber temperature and large expansion ratio? (5)

$$
c = \sqrt{\frac{2\gamma}{\gamma-1}\frac{\bar RT_c}{\mathcal M}\left[1-\left(\frac{p_e}{p_c}\right)^{\frac{\gamma-1}{\gamma}}\right]}
$$

- **$T_c$ high** (and $\mathcal M$ low): more enthalpy per kg, so the jet is faster ($c\propto\sqrt{T_c/\mathcal M}$).
- **Large expansion ratio** $\epsilon = A_e/A_t$: $\epsilon$ fixes $M_e$ and so $p_e/p_c$ (area–Mach relation). A larger $\epsilon$ gives a lower $p_e/p_c$, so the bracket approaches 1 and more thermal energy is converted to kinetic. $C_F$ rises (≈ 1.3 at sea level towards 1.9+ in vacuum).
  - A main engine climbs through a falling $p_a$, so it uses a large $\epsilon$ (SSME ≈ 69), with a high $p_c$ to avoid gross over-expansion and separation at sea level.
- Both raise $I_{sp}$, so less propellant for the same $\Delta V$ (Tsiolkovsky), which is why main engines use high $T_c$, high $p_c$ and large $\epsilon$.

See [[Rocket Nozzle Geometry]].

### (iv) RD-253 (5)
See [[SESA2023 Exam 2015-16 Solutions]] Q2(v).

### (v) RD-253 vs RD-270 (5)
See [[SESA2023 Exam 2015-16 Solutions]] Q2(vi).
- RD-253: **one** oxidiser-rich pre-burner; a single turbine drives both pumps; part of the fuel bypasses the pre-burner.
- RD-270: **two** pre-burners (fuel-rich and oxidiser-rich) and two turbopumps; **all** of both propellants are gasified before the chamber.
- The RD-270's advantages: lower turbine temperatures for the same power; no inter-propellant seal; gas–gas combustion; higher $p_c$ (≈ 26 MPa) and $I_{sp}$.

---

## Q4: Supersonic flight

### (i) Ramjet modules (3)
See [[SESA2023 Exam 2014-15 Solutions]] Q2(i).

### (ii) The J58 and scramjets (7)
See [[SESA2023 Exam 2014-15 Solutions]] Q2(vi).
- **Scramjet challenges**: millisecond residence times for mixing and ignition; ignition delay at low static $T$; thermal protection (stagnation temperatures above 2000 K at M 8); a strong airframe–engine coupling (the forebody is the intake, the afterbody the nozzle); no thrust below about M 4, so a rocket or combined-cycle booster is needed; hard to ground-test.

### (iii) Peak temperature limited, accelerating towards M 6 (5)
- With $T_{03}$ capped, the ram compression raises $T_{02} = T_a(1+0.2M^2)$ towards the cap. The heat that can be added, $c_p(T_{03}-T_{02})$, shrinks.
- The ideal specific thrust is $F/\dot m = M\sqrt{\gamma RT_a}\left[\sqrt{T_{03}/T_{02}}-1\right]$, which falls with $M$ at high Mach.
- Illustration with $T_{03} = 2200$ K and $T_a = 215$ K:

| $M$ | 3 | 4 | 5 | 6 |
|---|---|---|---|---|
| $T_{02}$ (K) | 602 | 903 | 1290 | 1763 |
| $F/\dot m$ (N s/kg) | 804 | 659 | 450 | **206** |

- Thrust vanishes at $M = 6.8$, where $T_{02} = T_{03}$. Meanwhile the captured mass flow cannot rise fast enough to compensate, and drag rises roughly as $\rho V^2$. The **maximum achievable velocity** is where thrust equals drag, well below M 6. It rises with the permitted $T_{03}$ (materials, cooling).
- Dissociation near 2000+ K makes this worse: heat goes into breaking bonds rather than into temperature. Hence scramjets beyond about M 5–6.

### (iv) Flight speed and Mach number (5)
$T_a = 215$ K, $f = 0.05$, $T_{03} = 2800$ K:

$$
T_{02} = 1.05(2800)-0.05(40{,}796) = 900.2\text{ K},\qquad M = \sqrt{\frac{900.2/215-1}{0.2}} = \boxed{3.99},\qquad V = \boxed{1173\text{ m/s}}
$$

### (v) Exhaust (5)
$M_e = 3.99$ and $T_e = 2800/4.187 = 668.7$ K:

$$
V_e = 3.99\sqrt{1.4(287)(668.7)} = \boxed{2069\text{ m/s}}
$$

$F/\dot m = 1.05(2069)-1173 = 999$ N s/kg. ($\eta_P = 0.752$, $\eta_{th} = 0.761$ and $\eta_O = 0.572$, if asked.)

## Related
- [[SESA2023 Past Paper Map]] · [[SESA2023 Propulsion Hub]] · [[SESA2023 Formula Sheet]]
- Script: `04 - Scripts/verify_past_papers.py` (section "2017-18")
